# Anexo A: Transparencia en el Uso de Inteligencia Artificial (IA)

De acuerdo con las bases y lineamientos del Reto AgroCebada 2026, este documento detalla el uso de Modelos de Lenguaje Grande (LLMs) durante el ciclo de vida del desarrollo del proyecto. 

## Herramientas Utilizadas
El desarrollo analítico, la revisión de código y la corrección de estilo fueron asistidos por los siguientes modelos:
1. **Claude (Anthropic)**
2. **ChatGPT (OpenAI)**
3. **Gemini (Google)**

## Naturaleza de la Asistencia
La IA **no** se utilizó para inventar datos, generar bases de datos sintéticas, ni alterar los resultados métricos. Su uso se restringió estrictamente a las siguientes labores como "asistente de programación y redacción":

### 1. Refactorización Geoespacial y de Scikit-Learn
Se utilizó IA para optimizar la estructura del código y construir *Pipelines* de Machine Learning que evitaran la fuga de datos. 
* **Ejemplo de Prompt:** *"Tengo un GeoDataFrame con las parcelas y necesito extraer el valor promedio de varios rasters CHIRPS (precipitación) para cada polígono asegurándome de manejar correctamente los valores NoData (-9999). ¿Cómo puedo optimizar esto usando rasterstats y geopandas en Python?"*

### 2. Implementación de Geoestadística
Se solicitó asistencia matemática para traducir fórmulas geoestadísticas a código vectorizado en Python (numpy/pandas).
* **Ejemplo de Prompt:** *"Necesito calcular un semivariograma empírico para evaluar la autocorrelación espacial del rendimiento. Escribe una función eficiente usando pairwise_distances de scikit-learn que agrupe las distancias en bins finos (0-250m, 250-500m) y calcule la semivarianza estricta (1/2N * suma de diferencias al cuadrado)."*

### 3. Edición de Estilo Científico (Reporte Metodológico)
Se emplearon LLMs para corregir el tono del reporte final, garantizando que el lenguaje fuera científicamente riguroso, prudente y evitara afirmaciones causales no probadas.
* **Ejemplo de Prompt:** *"Revisa este párrafo de resultados. Por favor, elimina cualquier verbo que denote certeza absoluta como 'demuestra' o 'comprueba', y reemplázalo por lenguaje estadísticamente prudente como 'es consistente con' o 'no se detectó diferencia estadísticamente significativa'."*
