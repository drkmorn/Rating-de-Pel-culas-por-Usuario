# Predicción de Rating de Películas por Usuario
En este proyecto se requiere realizar un modelo de Machine Learning el cual sirva para predecir cómo un usuario (con características como edad, sexo, ocupación, zip-code y un historial de películas calificadas) calificará una película que no ha visto.

Este proyecto se realizó en Google Colab, para compilarlo los archivos se subieron de manera local al almacenamiento de la sesión. Las bases de datos se encuentran en la carpeta "Bases de Datos" junto con un README que explica cada uno de los datos.

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Predicción de Rating de Películas por Usuarios</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }
        h1, h2, h3 {
            color: #0056b3;
        }
        h1 {
            text-align: center;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
        }
        h2 {
            border-bottom: 1px solid #eee;
            padding-bottom: 5px;
            margin-top: 30px;
        }
        ul {
            list-style-type: disc;
            margin-left: 20px;
        }
        code {
            background-color: #f4f4f4;
            padding: 2px 4px;
            border-radius: 4px;
        }
        pre {
            background-color: #f4f4f4;
            padding: 10px;
            border-radius: 5px;
            overflow-x: auto;
        }
        .author {
            text-align: center;
            font-style: italic;
            margin-top: 20px;
        }
        .highlight {
            background-color: #fffacd;
            padding: 1px 5px;
            border-radius: 3px;
        }
    </style>
</head>
<body>
    <h1>Predicción de Rating de Películas por Usuarios</h1>
    <div class="author">
        Autor: Morán Pérez Derek Saúl
    </div>

    <h2>Descripción del Proyecto</h2>
    <p>
        Este proyecto tiene como objetivo desarrollar un modelo de Machine Learning capaz de predecir la calificación que un usuario le otorgará a una película que aún no ha visto. La predicción se basa en las características del usuario (edad, sexo, ocupación, código postal) y su historial de calificaciones previas, así como en las características de las películas.
    </p>

    <h2>Problema a Resolver</h2>
    <p>
        En el vasto mundo del entretenimiento, la cantidad de películas disponibles es abrumadora. Los sistemas de recomendación son clave para ayudar a los usuarios a descubrir contenido relevante. Este proyecto contribuye a este objetivo prediciendo la preferencia de un usuario por una película específica, lo que puede ser la base para un sistema de recomendación personalizado.
    </p>

    <h2>Fuentes de Datos</h2>
    <p>
        Los datos utilizados provienen de tres conjuntos de datos interrelacionados, probablemente derivados de un dataset de MovieLens (comúnmente usado para este tipo de problemas):
    </p>
    <ul>
        <li><code>movies.dat</code>: Contiene información sobre las películas (ID, Título, Géneros).</li>
        <li><code>users.dat</code>: Contiene información demográfica de los usuarios (ID, Sexo, Edad, Ocupación, Código Postal).</li>
        <li><code>ratings.dat</code>: Contiene las calificaciones otorgadas por los usuarios a las películas, junto con una marca de tiempo (ID de Usuario, ID de Película, Calificación, Timestamp).</li>
    </ul>

    <h2>Metodología y Enfoque</h2>

    <h3>1. Importación y Exploración Inicial de Datos</h3>
    <p>
        Los datos se importaron utilizando la librería Pandas, prestando especial atención a la codificación (`ISO-8859-1`) y el separador de columnas (`::`). Se asignaron nombres descriptivos a las columnas basándose en la documentación original de los datos (archivo README externo).
    </p>
    <p>
        Se realizó una inspección inicial para identificar valores nulos y duplicados en cada uno de los datasets. Se verificó que no hubiera duplicados en los IDs únicos de películas y usuarios, y en el caso de las calificaciones, se aseguró que la combinación de <code>UserID</code> y <code>MovieID</code> fuera única, garantizando la integridad de los datos.
    </p>

    <h3>2. Limpieza de Datos (Mención de OpenRefine)</h3>
    <p>
        Se identificó la necesidad de tratar posibles inconsistencias en los títulos de las películas. Se planteó el uso de una herramienta externa como OpenRefine para estandarizar y limpiar estos datos textuales. Aunque el proceso completo de re-importación y fusión de los datos limpios no se muestra explícitamente en el script actual, se reconoce la importancia de este paso.
    </p>

    <h3>3. Ingeniería de Características (Oportunidades Futuras)</h3>
    <p>
        El script actual importa características como el sexo, la edad, la ocupación de los usuarios y los géneros de las películas. Para un futuro desarrollo, estas características categóricas necesitarán ser transformadas (ej., mediante <span class="highlight">One-Hot Encoding</span>) para ser utilizadas eficazmente por los modelos de Machine Learning. La columna <code>Timestamp</code> también ofrece potencial para crear características relacionadas con la temporalidad.
    </p>

    <h3>4. Modelo de Machine Learning</h3>
    <p>
        El proyecto utiliza un modelo de clasificación para predecir las calificaciones. Aunque el código principal utiliza un modelo ya definido (<code>modelo</code>), una sección comentada indica la intención de usar un <span class="highlight">RandomForestClassifier</span> y realizar una búsqueda de hiperparámetros con <span class="highlight">GridSearchCV</span>. Sin embargo, esta última parte no pudo ser ejecutada debido a limitaciones de recursos computacionales.
    </p>

    <h3>5. Evaluación del Modelo</h3>
    <p>
        El rendimiento del modelo se evaluó utilizando la métrica de <span class="highlight">Accuracy Score</span> tanto para el conjunto de entrenamiento como para el de prueba.
    </p>
    <ul>
        <li>Accuracy en entrenamiento: ~0.256</li>
        <li>Accuracy en prueba: ~0.256</li>
    </ul>
    <p>
        La similitud en la exactitud entre ambos conjuntos sugiere que el modelo no presenta un sobreajuste significativo en las características actuales.
    </p>

    <h2>Resultados y Limitaciones</h2>
    <p>
        El modelo actual alcanza una exactitud de aproximadamente 0.25 en la predicción de ratings. Si bien este valor es bajo para una predicción directa de calificación, indica un punto de partida para futuras optimizaciones.
    </p>
    <p>
        La principal limitación identificada fue la falta de recursos computacionales para realizar una búsqueda exhaustiva de hiperparámetros (GridSearchCV), lo que impidió optimizar el rendimiento del modelo más allá de su configuración inicial.
    </p>

    <h2>Futuro Trabajo y Mejoras</h2>
    <p>
        Para mejorar este proyecto, se recomiendan los siguientes pasos:
    </p>
    <ul>
        <li><strong>Completar el Preprocesamiento:</strong> Re-importar y fusionar los datos de películas limpios de OpenRefine. Implementar la unión de los tres datasets (`movies`, `users`, `ratings`).</li>
        <li><strong>Ingeniería de Características Avanzada:</strong> Transformar todas las variables categóricas a formatos numéricos adecuados. Explorar la creación de características adicionales a partir de la columna `Timestamp`.</li>
        <li><strong>Optimización de Hiperparámetros:</strong> Utilizar técnicas como <span class="highlight">RandomizedSearchCV</span> o buscar entornos con mayores recursos para llevar a cabo una sintonización de hiperparámetros y mejorar el rendimiento del modelo.</li>
        <li><strong>Evaluación con Métricas Adecuadas:</strong> Para la predicción de ratings, considerar métricas como <span class="highlight">RMSE (Root Mean Squared Error)</span> o <span class="highlight">MAE (Mean Absolute Error)</span>, que son más apropiadas para problemas de regresión o cuando se valora la proximidad de la predicción. Si se mantiene como clasificación, usar el <span class="highlight">Classification Report</span> para obtener precisión, recall y F1-score.</li>
        <li><strong>Exploración de Modelos:</strong> Investigar otros algoritmos de Machine Learning o enfoques específicos para sistemas de recomendación que puedan ser más adecuados para la tarea.</li>
        <li><strong>Visualización de Datos:</strong> Incluir análisis exploratorio de datos (EDA) con visualizaciones para comprender mejor la distribución de los datos y los resultados del modelo.</li>
        <li><strong>Modularización del Código:</strong> Organizar el script en funciones para mejorar la legibilidad y la mantenibilidad del código.</li>
        <li><strong>Persistencia del Modelo:</strong> Implementar la funcionalidad para guardar y cargar el modelo entrenado.</li>
    </ul>

    <h2>Cómo Ejecutar el Proyecto (Configuración)</h2>
    <p>
        Para ejecutar este proyecto, necesitarás Python y las siguientes librerías (pueden instalarse vía pip):
    </p>
    <pre><code>pip install pandas scikit-learn</code></pre>
    <p>
        Asegúrate de colocar los archivos <code>movies.dat</code>, <code>users.dat</code> y <code>ratings.dat</code> en el mismo directorio que el script Python, o ajustar las rutas de carga en el código.
    </p>

    <p>Este README se generó basándose en el análisis del archivo <code>untitled1.py</code>.</p>
</body>
</html>
