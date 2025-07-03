Este proyecto fue realizado en Google Colab subiendo los datos que se encuentran en la carpeta "Bases de Datos" al almacenamiento de la sesión. 

# Predicción de Rating de Películas por Usuarios

## Descripción del Proyecto

Este proyecto tiene como objetivo desarrollar un modelo de Machine Learning capaz de predecir la calificación que un usuario daría a una película que aún no ha visto. La predicción se basa en las características demográficas del usuario (como edad, sexo, ocupación, código postal) y su historial de calificaciones previas, así como en las características de las películas.

El objetivo principal es construir un sistema que pueda anticipar las preferencias de los usuarios, lo que podría ser útil en sistemas de recomendación de películas.

## Datos

Se utilizan tres conjuntos de datos principales, proporcionados en formato `.dat`, que incluyen información sobre:

* **`movies.dat`**: Información sobre las películas (ID de película, título, géneros).
* **`users.dat`**: Información sobre los usuarios (ID de usuario, sexo, edad, ocupación, código postal).
* **`ratings.dat`**: Calificaciones dadas por los usuarios a las películas (ID de usuario, ID de película, calificación, marca de tiempo).

Se realizó un proceso de importación cuidadoso, obteniendo la codificación el archivo, ya que no era UTF-8 y definiendo los nombres de las columnas según la documentación externa.

## Metodología

El enfoque inicial del proyecto abarca las siguientes etapas:

1.  **Importación y Carga de Datos:** Lectura de los archivos `.dat` en DataFrames de pandas.
2.  **Inspección de Datos:**
    * Verificación exhaustiva de valores nulos y duplicados en cada conjunto de datos. Se prestó especial atención a la combinación `UserID` y `MovieID` en el conjunto de `ratings` para asegurar la unicidad.
3.  **Limpieza de Datos:** Identificación de posibles inconsistencias en los títulos de las películas y planificación del uso de herramientas externas como OpenRefine para su estandarización.
4.  **Modelado (Inicio):**
    * Se exploró un enfoque de clasificación y uno de regresión mediante RandomForest para la predicción de ratings. Mostrando un pobre desempeño en los resultados de ambos modelos, pero obteniendo resultados mejores según las métricas para el modelo de Clasificación.
    * Se intentó hacer una búsqueda de hiperparámetros mediante GridSearchCV, pero debido al costo computacional esto no se pudo lograr.

## Estado Actual y Resultados Preliminares

El modelo inicial muestra una `accuracy` similar tanto en el conjunto de entrenamiento como en el de prueba (aproximadamente `0.25`). Esto sugiere que el modelo no está sobreajustando los datos, pero su rendimiento es bajo, lo que indica la necesidad de una mejora significativa en las etapas de preprocesamiento, ingeniería de características y selección/optimización del modelo.

## Próximos Pasos y Mejoras Futuras

Para mejorar la robustez y el rendimiento de este proyecto, se planetea conseguir un poder computacional mayor para hacer la búsqueda de mejores hiperparámetros

## Autor

**Morán Pérez Derek Saúl**

---
