# 🔋 Proyecto SMART ENERGY: Pronóstico de Demanda Eléctrica en Perú  

## 📌 Objetivo del Proyecto 
El presente proyecto busca predecir la demanda eléctrica en el Perú utilizando técnicas de Machine Learning aplicadas a series temporales.
Para ello se emplea la librería *skforecast*, que permite entrenar modelos de regresión para pronóstico autoregresivo.

El proyecto se desarrolla sobre la base de datos de Consumo Eléctrico en el Perú en un periodo que abarca los años 2023 y 2024. Cada registro de consumo eléctrico está dado en intervalos de 30 minutos.
La finalidad es construir un modelo capaz de anticipar el consumo eléctrico con un horizonte de predicción de una semana.

## 🛠️ Metodología y Estructura del Proyecto  

El desarrollo del proyecto siguió las siguientes etapas:  

1. **Preparación del entorno de trabajo**  
   - Instalación y configuración de librerías necesarias (`skforecast`, `xgboost`).  
   - Importación de librerías de análisis y visualización (Pandas, Matplotlib, Seaborn).  

2. **Carga y exploración de los datos**  
   - Dataset: registros históricos de consumo eléctrico en Perú (2023–2024), frecuencia de **30 minutos**.  
   - Conversión de la columna de fechas a formato datetime y establecimiento como índice de la serie.  
   - Verificación de calidad de datos (sin nulos, consistencia en la frecuencia).  

3. **Análisis exploratorio (EDA)**  
   - Visualización de la serie temporal para identificar tendencias y patrones de estacionalidad.  
   - Aplicación de **medias móviles** (24h y 7 días) para suavizar la serie y detectar variaciones.  

4. **Transformación de los datos**  
   - Definición de la variable objetivo: **Demanda eléctrica**.  
   - Generación de variables exógenas.  

5. **Modelado predictivo con skforecast**  
   - Entrenamiento de modelos autoregresivos mediante `ForecasterRecursive`.  
   - Regresor aplicado: **XGBRegressor**.  
   - Optimización de hiperparámetros con `grid_search_forecaster`.
   - Comparativa de modelos. Univariado: lags de la serie + XGBoost. Multivariado: lags + exógenas.

6. **Validación y evaluación**  
   - Predicciones sobre la última semana.   
   - Métricas empleadas: **MAE (Mean Absolute Error)** y **MSE (Mean Squared Error)**.  

---

## 📊 Resultados  

- El modelo logró capturar adecuadamente los **patrones diarios y semanales** de la demanda eléctrica.  
- Se observó que la inclusión de lags representando un **día completo (48 pasos)** y hasta **una semana (336 pasos)** mejora la capacidad de predicción.  
- Las métricas de evaluación empleadas presentaron mejores resultados en el modelo multivariado (con variables exógenas), reflejando el efecto positivo y la mejora en la eficiencia del modelo al emplear este tipo de variables.  

---

## ✅ Conclusiones  

- La librería **skforecast** permite simplificar la implementación de modelos autoregresivos, integrando técnicas de ML modernas.  
- El pronóstico de la demanda eléctrica mostró ser factible y confiable en periodos de **una semana**, lo cual es útil para la planificación energética.  
- El proyecto demuestra el potencial de **combinar series temporales con algoritmos de boosting** para resolver problemas del mundo real.  

---
