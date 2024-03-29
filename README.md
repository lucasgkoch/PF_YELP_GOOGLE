# Yelp - Google Maps
 
## Menú de Navegación

- [Objetivos del Proyecto](#objetivos-del-proyecto)
- [Alcance del Proyecto](#alcance-del-proyecto)
- [Stack Tecnológico](#stack-tecnológico)
- [Dashboard](#dashboard)
- [Metodología](#metodología)
- [Cloud - Guía General](#cloud---guía-general)
- [Deploy en Streamlit](#deploy-en-streamlit)
- [Análisis Exploratorio de Datos (EDA)](#análisis-exploratorio-de-datos-eda)
- [Diagrama de Entidad-Relación (ERD)](#diagrama-de-entidad-relación-erd)
- [Diccionario de Datos](#diccionario-de-datos)
- [Archivos Complementarios](#archivos-complementarios)
- [Modelo de Recomendación de Machine Learning](#modelo-de-recomendación-de-machine-learning)
- [Sistema de Retroalimentación de Sugerencias](#sistema-de-retroalimentación-de-sugerencias)
- [Video](#video)

## Objetivos del Proyecto
La Asociación de Restaurantes y Afines de Pennsylvania ha encomendado a Prometheus Data Solutions la tarea de evaluar la percepción de los clientes sobre los establecimientos afiliados, mediante el análisis de reseñas en Yelp y Google Maps. Nuestros objetivos principales incluyen medir la satisfacción de los clientes, identificar preferencias, señalar áreas de mejora, destacar sectores con oportunidades de crecimiento y anticipar aquellos que podrían enfrentar disminuciones en las ventas. Además, se busca diseñar un sistema de recomendación mediante Machine Learning que ofrezca sugerencias personalizadas a los usuarios, basándose en sus gustos y preferencias específicas.

## Alcance del Proyecto
El proyecto abarcará el proceso ETL y el Análisis Exploratorio de Datos (EDA), considerando la integración de información proveniente de Yelp y Google Maps. Se utilizarán herramientas como PySpark y Streamlit. El modelo de recomendación de Machine Learning incorporará análisis de sentimientos, técnicas de procesamiento de lenguaje natural (NLP) y considerará restaurantes de grandes cadenas en otros estados para mejorar la percepción en Pensilvania.

## Stack Tecnológico
### Lenguaje de Programación
- Python

### Bibliotecas
- Pandas, Matplotlib, Seaborn, NLTK

### Frameworks
- PySpark, Streamlit

### Plataforma de Cloud
- Google Cloud Platform (GCP)

### Servicios y Herramientas de GCP
- Cloud Storage (Almacenamiento de objetos)
- Dataproc (Procesamiento de datos en clústeres Apache Spark)
- BigQuery (Data Warehouse)
- Vertex AI (Entrenamiento de modelos de ML)
- Cloud Functions(Ejecución de tareas automatizadas)

### Endpoints
- Deployment Streamlit

## Dashboard

### Inspiración de Diseño

El diseño del dashboard se basará en la estética de Yelp para proporcionar al receptor un contexto visual coherente. Esto incluirá el uso de paletas de colores y tipografías inspiradas en Yelp.

Además, se prestará especial atención a aspectos de accesibilidad, llevando a cabo pruebas de daltonismo para elegir colores amigables y asegurando etiquetados adecuados para mejorar la experiencia de usuarios con diversas necesidades.

### Estructura del Dashboard

El dashboard constará de varias secciones:

1. **Home**
   - Página de inicio con un menú que facilitará la navegación por las diferentes secciones del dashboard.

2. **Contexto Geográfico**
   - Tablero que mostrará un mapa de la región en análisis (Pensilvania), proporcionando un contexto geográfico para las evaluaciones de los restaurantes.

3. **Tablero principal**
   - Tablero principal que presentará la información más relevante del análisis general.
   - Incluirá filtros para facilitar la exploración de datos, permitiendo al usuario seleccionar datos por año y plataforma (Yelp o Google Maps).

4. **KPI 1 y KPI 2**
   - Tablero dedicado a los primeros dos Key Performance Indicators (KPI).
   - Mostrará si se lograron o no los objetivos planteados y proporcionará gráficos para respaldar y profundizar en la comprensión de estos KPI.

5. **KPI 3 y KPI 4**
   - Tablero similar al anterior, pero enfocado en los KPI 3 y 4.

![tablero principal](assets/dashboard_principal.png)

### Implementación del Dashboard

El dashboard se implementará utilizando PowerBI, aprovechando sus capacidades de visualización de datos y facilidades de interactividad.

Para garantizar una experiencia óptima, se recomienda utilizar el dashboard en navegadores modernos y asegurarse de tener una conexión estable a Internet.

### [Link al dashboard](https://app.powerbi.com/view?r=eyJrIjoiNmNhZDM1OWQtMGY1Yi00ZTljLTk4ZmYtMmU5NGE0N2QxZWM1IiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9)
### [Informe del dashboard]('Informe_dashboard.pdf')



## Metodología
![banner equipo](assets/equipo.png)

El proyecto seguirá la metodología Scrum para la gestión y desarrollo. El equipo está compuesto por:

- [Davidsson Gonzales](https://www.linkedin.com/in/davidsson-gonzalez-usma-6a7486295/) - Data Engineer
- [Francisco Mejia](https://github.com/pachomejia26) - Data Engineer
- [Diego Gamarra Rivera](https://www.linkedin.com/in/diegogamarrarivera/) - Data Scientist
- [Juan Ochoa](https://www.linkedin.com/in/juan-gabriel-ochoa-g/) - Data Scientist
- [Lucas Koch](https://www.linkedin.com/in/lucas-gkoch/) - Data Analyst

## Cloud - Guía General
![Pipeline](assets/pipeline.png)

1. Registrarse en Google Cloud Platform. 
2. Activar facturación y regalo de 300 créditos gratis. (Sólo para quien va a trabajar montando el ecosistema, ya que este beneficio tiene una duración limitada de 3 meses).
    - [Cómo usar Google Cloud Storage](https://www.youtube.com/watch?v=HSIyOin5paQ)
3. Se establece un presupuesto para el proyecto.
4. Asignación de roles y permisos para los demás miembros.
    - [Gestión de Identidades y Accesos de Google Cloud (IAM)](https://www.youtube.com/watch?v=ZS3qyD_cveY)
5. Se crea un bucket en gcp con la herramienta Google Cloud Storage.
    - Se crea el bucket.
    - Se crean las respectivas carpetas de los datasets dentro del bucket.
    - Se suben los archivos en la carpeta datasets.
    - [Cómo usar Google Cloud Storage](https://www.youtube.com/watch?v=HSIyOin5paQ)
6. Se crea un clúster de Apache Spark con la herramienta Dataproc.
    - Se habilitan las API’s de Cloud Resource Manager API y Cloud Dataproc API.
    - Se crea el clúster con Compute Engine.
    - Se suben los scripts de python a la carpeta de un bucket que contienen el código pyspark del ETL.
7. Se crea un conjunto de Datos en BigQuery.
    - Se habilitan API’s Google BigQuery
    - Se crea un conjunto de datos
    - Se crea una consulta que crea las tablas de los datos a entrar del ETL
8. Se crean las Cloud Functions.
    - Se crea una cloud function que detecta la carga de archivo en el bucket de entrada de datos y procede a ejecutar los diferentes trabajos en Dataproc dependiendo del nombre del archivo subido
    - Se crea una cloud function para que llene las tablas creadas en BigQuery con los archivos parquet que llegan a un bucket en particular. Esta cloud function se activa con cualquier evento de carga de archivos al bucket
9. Se ejecutan los trabajos en Dataproc.
    - Se realizan los trabajos en el clúster de Dataproc de manera automática gracias a la Cloud Function
    - La ejecución del ETL guarda los  DataFrames en archivos parquet en un bucket de salida
10. Se cargan las tablas en BIgQuery de manera automática.
    - Al detectar los archivos en el bucket de salida se activa la Cloud Function que los utiliza para llenar las tablas de BigQuery con sus respectivos nombres asignados
11. Se crean nuevas tablas a partir de las recién cargadas.
    - Al completarse los registros desde los archivos parquet del bucket se completan nuevas tablas que contiene información específica de diferentes tablas ya que estas tendrán diversas funcionalidades
    - Se crea la tabla en BigQuery necesaria para el análisis de sentimiento
12. Se realiza un modelo en Vertex AI.
    - Se crea una instancia en Vertex AI donde se ejecuta jupyter y se trabaja en un Notebook
    - Se utiliza la información de las diversas tablas de BigQuery para realizar un modelo de similitud de coseno dentro del archivo notebook pudiendo éste exportar la información adquirida en el modelo a una nueva tabla de BigQuery necesaria para el proceso de Deployment

    - [Video demostracion del pipeline](https://drive.google.com/file/d/1VsG5ham_mw_jRBkHIp2sgj0uhnzB_MZQ/view)

## Deploy en Streamlit
El proyecto contará con una aplicacion desplegada en streamlit, la cual le brindará al usuario una recomendación de restaurantes basada en su ubicación y preferencias.
[Esta aplicación](streamlit_app.py) está programada en python y realiza un request con el metodo POST a una cloud function de GCP enviandole un diccionario con la informacion necesaria. La cloud function, mediante un modelo de machine learning basado en similitud del coseno y tecnicas de NLP, recomienda los 5 restaurantes más apropiados y devuelve a la aplicación un JSON con la informacion necesaria, el cual será procesado y mostrado al usuario en forma tabular y también en un mapa.

### [Link a la api](https://parecommends.streamlit.app/)

![Vistazo API](assets/API_view.png)

## Análisis Exploratorio de Datos (EDA)
- Yelp: 5 tablas (3 hechos, 2 dimensionales). Datos detallados.
- Google Maps: 2 tablas relacionadas. Menos detallado y con datos faltantes.
- Yelp como fuente principal; Google Maps, complementario según utilidad.

## Diagrama de Entidad-Relación (ERD)

Para visualizar la estructura de la base de datos utilizada en este proyecto, se creó un Diagrama de Entidad-Relación (DER).diagrama en formato PDF: [Diagrama entidad-relación](DER_yelp_google.pdf).


## Diccionario de Datos

[Diccionario de Datos](diccionario_de_datos.pdf).



## Archivos complementarios
Ser obtuvo un archivo GeoJson del estado de Pensilvania y sus condados. Este archivo fue descargado del sitio Pennsylvania Spatial Data Access (https://www.pasda.psu.edu/)

## Modelo de Recomendación de Machine Learning
En nuestro enfoque de machine learning, hemos diseñado un sistema de recomendación para restaurantes que utiliza análisis de reseñas, información de ubicación y atributos clave para ofrecer recomendaciones personalizadas y precisas.

1. Análisis de Reseñas:

    Implementaremos un modelo de machine learning para analizar cada reseña y clasificarlas en categorías de positivas, negativas y neutras. Este análisis profundo permitirá una comprensión más precisa de las experiencias compartidas por los usuarios.

2. Identificación de Atributos Clave:

Cada establecimiento será evaluado en función de atributos clave que influyen significativamente en la experiencia del usuario:

- Ubicación: La proximidad y accesibilidad del restaurante.
- Tipo de Comida: Identificación de la especialidad culinaria del restaurante.
- Tipo de Restaurante: Clasificación del ambiente, ya sea casual, formal o informal.
- Aceptación de Tarjetas de Crédito: Información relevante sobre las opciones de pago.

3. Diseño del Sistema de Recomendación:

    Integraremos las clasificaciones de reseñas y los atributos clave para diseñar un sistema de recomendación personalizado. Este sistema tomará en cuenta las preferencias individuales del usuario y proporcionará sugerencias adaptadas a sus gustos específicos.

4. Ordenamiento basado en Índice de Satisfacción:

    Las recomendaciones generadas se organizarán en base a un índice de satisfacción (reseñas positivas/reseñas negativas). Este índice reflejará la opinión de los usuarios con respecto al lugar.


## Sistema de retroalimentación de sugerencias
El proceso de consulta de recomendación guarda los datos sobre las recomendaciones entregadas a los usuarios las cuales cada cierto periodo de tiempo se utilizaran para alimentar al mismo modelo y entregar nuevos insight a los restaurantes.

## Video 

Hemos desarrollado un video que vende nuestra idea mostrando la funcionalidad de nuestros productos. 

### [Link al video](https://www.youtube.com/watch?v=DVFc8fxR0yw)
