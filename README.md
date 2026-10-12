# AgroCebada 2026: Predicción de Rendimiento mediante Modelado Espacial 

Este repositorio contiene la solución completa para el reto AgroCebada 2026 (FIRA), enfocada en la predicción del rendimiento de cebada (t/ha) en la región centro de México utilizando datos climáticos, topográficos y series temporales de satélite (Sentinel-2, Landsat, Planet NICFI).

A diferencia de los enfoques tradicionales de *Machine Learning* que asumen independencia entre las observaciones, este proyecto se fundamenta en la **Geoestadística y la Honestidad Algorítmica**. 

## Enfoque Analítico
El análisis de semivarianza demostró que el rendimiento agrícola en este conjunto de datos presenta una fuerte autocorrelación espacial (un efecto "pepita" a menos de 250m y tendencias macroclimáticas a >25km). Para evitar que los modelos de caja negra "memoricen" coordenadas mediante *proxies* (fuga de datos espaciales), implementamos:
1. **Validación Espacial Estricta (LOGO por Municipio):** Para medir la capacidad real de extrapolación del modelo a zonas sin parcelas de referencia.
2. **Ingeniería Fenológica:** Transición de promedios mensuales crudos a variables físicas (Integrales de dosel, cocientes térmicos de estrés).
3. **Ablación y Análisis de Residuos:** Demostrando estadísticamente el peso relativo de la ubicación frente a la señal agronómica de percepción remota.

## Resultados Principales
El modelo final de entrega es un **Ensamble Promedio (VotingRegressor)** que combina un interpolador K-Nearest Neighbors (KNN) espacial con un modelo HistGradientBoosting (HGB) basado en variables físicas y satelitales.

| Métrica (Repeated K-Fold) | Resultado |
| :--- | :--- |
| **MAE (Error Absoluto Medio)** | ~ 0.38 t/ha |
| **RMSE** | ~ 0.52 t/ha |
| **R²** | ~ 0.60 |
| **Intervalo Empírico (80%)** | ± 0.56 t/ha (en interpolación) |

## Estructura del Repositorio
El código está diseñado para ser modular y reproducible, dividido en 4 libretas principales:
* `01_Calidad_y_Contexto_Agronomico.ipynb`: Análisis de nube, cobertura y limpieza.
* `02_Ingenieria_Fenologica_y_Espacial.ipynb`: Extracción raster (CHIRPS/CHIRTS/INEGI) e integrales de dosel.
* `03_Validacion_Robusta_y_Ablacion.ipynb`: Evaluación LOGO, diferencias pareadas y prueba de residuos.
* `04_Interpretabilidad_y_Preguntas_Guia.ipynb`: Valores SHAP, dependencia parcial (ICE) e importancia por permutación.
* `/docs/uso_de_ia.md`: Bitácora de uso de Modelos de Lenguaje (IA) en el desarrollo.

## 💡 Inclusión Financiera
En lugar de forzar el modelo para fijar primas de seguros ciegos, el algoritmo se propone como una **herramienta de tamizaje y verificación con incertidumbre explícita**. Utilizando el cálculo de distancia a vecinos conocidos, las instituciones financieras pueden validar de forma remota los rendimientos esperados, disminuyendo los costos de inspección en campo para pequeños productores.
