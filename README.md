# Predicción de Rating de Películas por Usuario
En este proyecto se requiere realizar un modelo de Machine Learning el cual sirva para predecir cómo un usuario (con características como edad, sexo, ocupación, zip-code y un historial de películas calificadas) calificará una película que no ha visto.

Este proyecto se realizó en Google Colab, para compilarlo los archivos se subieron de manera local al almacenamiento de la sesión. Las bases de datos se encuentran en la carpeta "Bases de Datos" junto con un README que explica cada uno de los datos.

# Predicción de Rating de Películas por Usuarios

## Descripción del Proyecto

Este proyecto tiene como objetivo desarrollar un modelo de Machine Learning capaz de predecir la calificación que un usuario daría a una película que aún no ha visto. La predicción se basa en las características demográficas del usuario (como edad, sexo, ocupación, código postal) y su historial de calificaciones previas, así como en las características de las películas.

El objetivo principal es construir un sistema que pueda anticipar las preferencias de los usuarios, lo que podría ser útil en sistemas de recomendación de películas.

## Datos

Se utilizan tres conjuntos de datos principales, proporcionados en formato `.dat`, que incluyen información sobre:

* **`movies.dat`**: Información sobre las películas (ID de película, título, géneros).
* **`users.dat`**: Información sobre los usuarios (ID de usuario, sexo, edad, ocupación, código postal).
* **`ratings.dat`**: Calificaciones dadas por los usuarios a las películas (ID de usuario, ID de película, calificación, marca de tiempo).

Se realizó un proceso de importación cuidadoso, manejando la codificación (`ISO-8859-1`) y definiendo los nombres de las columnas según la documentación externa.

## Metodología

El enfoque inicial del proyecto abarca las siguientes etapas:

1.  **Importación y Carga de Datos:** Lectura de los archivos `.dat` en DataFrames de pandas.
2.  **Inspección de Datos:**
    * Verificación exhaustiva de valores nulos y duplicados en cada conjunto de datos. Se prestó especial atención a la combinación `UserID` y `MovieID` en el conjunto de `ratings` para asegurar la unicidad.
3.  **Limpieza de Datos:** Identificación de posibles inconsistencias en los títulos de las películas y planificación del uso de herramientas externas como OpenRefine para su estandarización.
4.  **Modelado (Inicio):**
    * Se exploró un enfoque de clasificación para la predicción de ratings.
    * El código incluye el cálculo de la `accuracy_score` para los conjuntos de entrenamiento y prueba.

## Estado Actual y Resultados Preliminares

El modelo inicial muestra una `accuracy` similar tanto en el conjunto de entrenamiento como en el de prueba (aproximadamente `0.25`). Esto sugiere que el modelo no está sobreajustando los datos, pero su rendimiento es bajo, lo que indica la necesidad de una mejora significativa en las etapas de preprocesamiento, ingeniería de características y selección/optimización del modelo.

## Próximos Pasos y Mejoras Futuras

Para mejorar la robustez y el rendimiento de este proyecto, se planean las siguientes mejoras:

1.  **Completar el Pipeline de Preprocesamiento:**
    * Integrar los datos limpios de OpenRefine de vuelta al flujo de trabajo.
    * Realizar la fusión completa de las tres bases de datos (`movies`, `users`, `ratings`).
2.  **Ingeniería de Características Avanzada:**
    * Transformar características categóricas (como `Gender`, `Occupation`, `Genres`) utilizando técnicas como `one-hot encoding`.
    * Explorar el uso de la columna `Timestamp` para generar características relacionadas con el tiempo (ej. recencia).
3.  **Selección y Optimización del Modelo:**
    * Evaluar y justificar la elección de un modelo (ej. `RandomForestClassifier`) o considerar alternativas más adecuadas para problemas de regresión si los ratings se tratan como valores continuos.
    * Implementar una estrategia de **sintonización de hiperparámetros** (ej. `GridSearchCV` o `RandomizedSearchCV`), incluso con muestreo de datos, para encontrar la mejor configuración del modelo (actualmente limitada por recursos computacionales).
4.  **Métricas de Evaluación Robustas:**
    * Utilizar métricas más apropiadas para la predicción de ratings, como el Error Cuadrático Medio (RMSE) o el Error Absoluto Medio (MAE), además del `accuracy_score`.
    * Generar un `classification_report` completo para entender la precisión, recall y F1-score por clase si se mantiene el enfoque de clasificación.
5.  **Exploración de Datos (EDA) y Visualizaciones:**
    * Realizar un análisis exploratorio de datos más profundo con visualizaciones para entender las distribuciones de datos y relaciones entre variables.
    * Visualizar los resultados del modelo y los errores de predicción.
6.  **Modularización del Código:**
    * Organizar el código en funciones y módulos para mejorar la legibilidad, mantenibilidad y reutilización.
7.  **Persistencia del Modelo:**
    * Implementar la funcionalidad para guardar y cargar el modelo entrenado.
8.  **Funcionalidad de Predicción:**
    * Crear una función clara para realizar predicciones sobre nuevos datos de usuario-película.

## Autor

**Morán Pérez Derek Saúl**

---
