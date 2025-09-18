# Examen_1_ModelosNoLineales
Un repositorio colaborativo para el examen 1 de modelos no lineales 

##  Contexto

La **Tasa de Interés Interbancaria de Equilibrio (TIIE)** es un indicador financiero clave publicado diariamente por el **Banco de México (Banxico)**.  
Sirve como referencia en **créditos, derivados, bonos e instrumentos financieros**, y refleja las condiciones de liquidez y expectativas de política monetaria en México.  

El pronóstico de la TIIE es crucial porque permite:  
- Estimar costos de financiamiento futuros.  
- Evaluar riesgos en inversiones y créditos.  
- Apoyar la planeación estratégica de empresas y bancos.  

---

##  Objetivo del Proyecto

Desarrollar un **modelo SARIMA (Seasonal ARIMA)** que:  
1. Analice el comportamiento histórico de la TIIE (28 días).  
2. Identifique tendencias, estacionalidad y patrones relevantes.  
3. Genere proyecciones confiables a corto y mediano plazo.  

Los datos se obtienen directamente desde la **API de Banxico**, garantizando **fuentes oficiales y actualizadas**.

---

##  Metodología
1. **Obtención de datos**  
   - Conexión a la API de Banxico.  
   - Limpieza y preparación de la serie temporal.  

2. **Análisis exploratorio (EDA)**  
   - Visualización de tendencias y estacionalidad.  
   - Pruebas de estacionariedad (ADF Test).  

3. **Construcción del modelo SARIMA**  
   - Identificación de parámetros (p, d, q, P, D, Q, s).  
   - Ajuste del modelo con ``.  

4. **Evaluación del modelo**  
   - Métricas: AIC, BIC, MAE, MAPE.  
   - Validación sobre datos de prueba.  

5. **Proyección**  
   - Forecast de la TIIE en el horizonte seleccionado.  
   - Visualización con intervalos de confianza.  
