# Proyecto de Normalización de Datos y Despliegue con FastAPI

Este proyecto tiene como objetivo principal la normalización y transforamción de los archivos de datos `movies_data.csv` y `credits.csv`, para seguido de la creación de una API utilizando FastAPI y el despliegue del proyecto en Render.

## Transformación de Datos

1. Se inició con los archivos `movies_dataset.csv` y `credits.csv` que contenían información sobre películas y créditos asociados.
2. Se realizó una exploración inicial de los datos para comprender su estructura y contenido.
3. Se identificaron los problemas de calidad de los datos, como valores faltantes, duplicados o inconsistencias.
4. Se procedió a realizar la normalización de los datos para facilitar su procesamiento y análisis.
    - En el caso del archivo `movies_data.csv`, se realizaron las siguientes transformaciones:
        ## movies_dataset.csv: Instanciar clase y ejecutar métodos
        ### Parámetros
        path_in_movies = '/Users/negro/Library/CloudStorage/OneDrive-Personal/Documentos/00 Fran/01 - Personales/02-Learn/0. Data Science/0. Data Science/2_projects/d_moviesML/Data Set/movies_dataset.csv'

        ### Instanciar clase DataGuru
        DataGuru = DataGuru(path_in_movies)

        ### Leer archivo CSV y crear DataFrame
        DataGuru.read_csv()

        ### Lista de columnas a normalizar (Dtype: dict, Dtype: list of dict)
        (dict_columns, dict_list_columns) = (['belongs_to_collection'], ['genres', 'production_companies', 'production_countries', 'spoken_languages'])
        ### Normalizar columnas con dict o list de dict
        DataGuru.normalize_data(dict_columns, dict_list_columns)

        ### Limpiar espacios antes y después de caracteres
        DataGuru.trim_spaces()

        ### Lista de columnas a convertir a int
        num_columns = ['id', 'runtime', 'vote_count', 'budget', 'popularity', 'revenue', 'vote_average']
        ### Asignar DTypes a columnas int, float y date
        DataGuru.assign_dtypes_num(num_columns)

        ### Lista de columnas a convertir a YYYY-MM-DD
        date_columns = ['release_date']
        ### Asignar DTypes a columnas int, float y date
        DataGuru.assign_dtypes_date(date_columns)

        ### Eliminar columnas innecesarias
        drop_columns = ['video', 'imdb_id', 'adult', 'original_title', 'poster_path', 'homepage', 'original_language', 'runtime', 'status',
                        'tagline', 'belongs_to_collection_backdrop_path', 'belongs_to_collection_name', 'belongs_to_collection_id', 'belongs_to_collection_poster_path',
                        'genres_id', 'production_companies_id', 'production_countries_iso_3166_1', 'spoken_languages_name', 'spoken_languages_iso_639_1']
        DataGuru.drop_columns(drop_columns)

        ### Reemplazar valores nulos a str='', num='0'
        DataGuru.replace_null_values()

        ### Eliminar filas con valores nulos en 'release_date'
        drop_na = ['release_date']
        DataGuru.drop_na(drop_na)

        ### Redondear columnas float a 4 decimales
        round_float = ['popularity']
        DataGuru.redondear_decimales(round_float, 4)

        ### Redondear columnas int a 0 decimales
        round_int = ['id', 'budget', 'revenue', 'vote_count']
        DataGuru.redondear_decimales(round_int, 0)

        ### Agregar columna 'release_year'
        DataGuru.add_release_year_column()

        ### Crear columna 'return' usando a/b = c
        (a, b, c) = ('revenue', 'budget', 'return')
        DataGuru.create_return_column(a, b, c)

        ### Revisar nulos e infinitos en columnas específicas
        check_null_inf = ['id', 'budget', 'revenue', 'vote_count', 'return']
        DataGuru.check_null_and_inf_values(check_null_inf)

        ### Guardar DataFrame normalizado
        df_movies = DataGuru.get_data()
        df_movies_norm = df_movies  # Copia normalizada


    - En el caso del archivo `credits.csv`, se realizaron las siguientes transformaciones:
        ## credits.csv: Instanciar clase y ejecutar métodos

        ### Ruta del archivo credits.csv
        path_in_credits = '/Users/negro/Library/CloudStorage/OneDrive-Personal/Documentos/00 Fran/01 - Personales/02-Learn/0. Data Science/0. Data Science/2_projects/d_moviesML/Data Set/credits.csv'

        ### Instanciar la clase DataGuru2 y pasar la ruta del archivo como argumento
        DataGuru2 = DataGuru2(path_in_credits)

        ### Renombrar la columna 'id' a 'credits_id' en el DataFrame
        DataGuru2.rename_id_column()

        ### Desanidar la columna 'cast' del DataFrame y agregar la columna 'job' cuando 'character' no es nulo
        DataGuru2.desanidar_cast_and_agregar_job()

        ### Desanidar la columna 'crew' del DataFrame
        DataGuru2.desanidar_crew()

        ### Crear el DataFrame 'df_credits_norm' unificando las columnas 'job', 'name' y 'credits_id'
        df_credits_norm = DataGuru2.crear_dataframe_credits_norm()


## Desarrollo de la API con FastAPI

1. Se utilizó el framework FastAPI para desarrollar una API que permitiera acceder a los datos normalizados.
2. Se crearon las rutas y controladores correspondientes para manejar las solicitudes de los usuarios.
3. Se implementaron las operaciones básicas de consulta y búsqueda de películas, así como también la obtención de información detallada de una película específica.
4. Se realizaron pruebas locales para asegurarse de que la API funcionara correctamente.

## Despliegue del Proyecto en Render

1. Se configuró el entorno de despliegue utilizando Render, un servicio de alojamiento y despliegue de aplicaciones web.
    - Parametros utilizados:
    -![Render_settings_1](2_projects/d_moviesML_API_1.1/Movies_API/src/Render_settings_1.png)
    -![Render_settings_2](2_projects/d_moviesML_API_1.1/Movies_API/src/Render_settings_2.png)
    -![Render_settings_3](2_projects/d_moviesML_API_1.1/Movies_API/src/Render_settings_3.png)

2. Se creó un archivo de configuración `requirements.txt` con las dependencias necesarias para el proyecto.
4. Se realizó el despliegue del proyecto en Render, asegurando que la API estuviera disponible en línea.

![Texto alternativo](2_projects/d_moviesML_API_1.1/Movies_API/src/Render_deploy_config.png)

## Uso de la API
Una vez desplegado, se pueden realizar las siguientes solicitudes a la API:

- Consultar la cantidad de filmaciones en un mes específico: `https://fastapi-1koe.onrender.com/filmaciones/mes/{mes}`
- Consultar la cantidad de filmaciones en un día específico: `https://fastapi-1koe.onrender.com/filmaciones/dia/{dia}`
- Consultar el score de una película por título: `https://fastapi-1koe.onrender.com/peliculas/score/{titulo}`
- Consultar la cantidad de votos de una película por título: `https://fastapi-1koe.onrender.com/peliculas/votos/{titulo}`
- Consultar información sobre un actor específico: `https://fastapi-1koe.onrender.com/actores/{nombre_actor}`
- Consultar información sobre un director específico: `https://fastapi-1koe.onrender.com/directores/{nombre_director}`
- Recomendar películas similares a una película de entrada: `https://fastapi-1koe.onrender.com/recomendar/{pelicula_entrada}`
- Documentación de la API: https://fastapi-1koe.onrender.com/docs
![Render_deploy_API_1](https://raw.githubusercontent.com/Fran-AS/Movies_API/src/Render_deploy_API_1.png)

![Render_deploy_API_2](2_projects/d_moviesML_API_1.1/Movies_API/src/Render_deploy_API_2.png)


## Recursos Adicionales

- [Documentación de FastAPI](https://fastapi.tiangolo.com/)
- [Render - Plataforma de despliegue](https://render.com/)
- [Entorno virtual y despliegue local de fastAPI](https://youtu.be/J0y2tjBz2Ao)
- [Despliegue web de fastAPI con Render](https://youtu.be/920XxI2-MJ0)
