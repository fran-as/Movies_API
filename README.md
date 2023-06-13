# Proyecto de Normalización de Datos, creacion de API con FastAPI y disponibilización con Render

Este proyecto tiene como objetivo principal la normalización y transforamción de los archivos de datos `movies_data.csv` y `credits.csv`, para seguido de la creación de una API utilizando FastAPI y el despliegue del proyecto en Render.

Toda la docmuntacion pueda accederce atraves del siguiente repositorio
[Frans-AS Repo](https://github.com/fran-as/Movies_API/tree/deploy)
## 1. Transformación de Datos

1. Se inició con los archivos `movies_dataset.csv` y `credits.csv` que contenían información sobre películas y créditos asociados.
2. Se realizó una exploración inicial de los datos para comprender su estructura y contenido.
3. Se identificaron los problemas de calidad de los datos, como valores faltantes, duplicados o inconsistencias.
4. Se procedió a realizar la normalización de los datos para facilitar su procesamiento y análisis a través de archivo main.ipynb:
    ### En el caso del archivo `movies_data.csv`, se realizaron las transformaciones con la clase DataGuru y se exportó a df_movies_norm.csv:
- [Archivo df_movies_norm](https://github.com/fran-as/Movies_API/blob/ed016e275c15bd006cb4c4876bf040249804b195/Data%20Set/df_movies_norm.csv)
    ### En el caso del archivo `credits.csv`, se realizaron las transformaciones con la clase DataGuru2 y se exportó a df_credits_norm.csv:
- [Archivo df_movies_norm](https://github.com/fran-as/Movies_API/blob/ed016e275c15bd006cb4c4876bf040249804b195/Data%20Set/df_credits_norm.csv)


## 2. Desarrollo de la API con FastAPI

1. Se utilizó el framework FastAPI para desarrollar una API que permitiera acceder a los datos normalizados.
2. Se crearon las rutas y controladores correspondientes para manejar las solicitudes de los usuarios.
3. Se implementaron las operaciones básicas de consulta y búsqueda de películas, así como también la obtención de información detallada de una película específica.
4. Se realizaron pruebas locales para asegurarse de que la API funcionara correctamente.

## 3. Despliegue del Proyecto en Render

1. Se configuró el entorno de despliegue utilizando Render, un servicio de alojamiento y despliegue de aplicaciones web, Parametros utilizados:

<img src="./src/Render_settings_1.png" alt="Render_settings_1" width="800" height="350">

<img src="./src/Render_settings_2.png" alt="Render_settings_2" width="800" height="350">

<img src="./src/Render_settings_3.png" alt="Render_settings_3" width="800" height="350">

2. Se creó un archivo de configuración `requirements.txt` con las dependencias necesarias para el proyecto.
4. Se realizó el despliegue del proyecto en Render, asegurando que la API estuviera disponible en línea.

<img src="./src/Render_deploy_config.png" alt="Render_settings_3" width="800" height="350">


## 4. Uso de la API
### Una vez desplegado, se pueden realizar las siguientes solicitudes a la API:
- [1. Consultar la cantidad de filmaciones en un mes específico](https://fastapi-deploy-w4h0.onrender.com/filmaciones/mes/)
- [2. Consultar la cantidad de filmaciones en un día específico](https://fastapi-deploy-w4h0.onrender.com/filmaciones/dia/)
- [3. Consultar el score de una película por título](https://fastapi-deploy-w4h0.onrender.com/peliculas/score/)
- [4. Consultar la cantidad de votos de una película por título](https://fastapi-deploy-w4h0.onrender.com//peliculas/votos/)
- [5. Consultar información sobre un actor específico](https://fastapi-deploy-w4h0.onrender.com/actores/)
- [6. Consultar información sobre un director específico](https://fastapi-deploy-w4h0.onrender.com/directores/)
- [7. Recomendar películas similares a una película de entrada](https://fastapi-deploy-w4h0.onrender.com/recomendar/)

<img src="https://raw.githubusercontent.com/fran-as/Movies_API/deploy/src/Render_deploy_API_1.png" alt="Render_deploy_API_2" width="800" height="350">

<img src="https://raw.githubusercontent.com/fran-as/Movies_API/deploy/src/Render_deploy_API_2.png" alt="Render_deploy_API_2" width="800" height="350">

<iframe width="560" height="315" src="https://youtu.be/UXflgTJhOsk" frameborder="0" allowfullscreen></iframe>


- [Documentación de la API](https://fastapi-deploy-w4h0.onrender.com/docs)
## Recursos Adicionales

- [Documentación de FastAPI](https://fastapi.tiangolo.com/)
- [Render - Plataforma de despliegue](https://render.com/)
- [Entorno virtual y despliegue local de fastAPI](https://youtu.be/J0y2tjBz2Ao)
- [Despliegue web de fastAPI con Render](https://youtu.be/920XxI2-MJ0)

