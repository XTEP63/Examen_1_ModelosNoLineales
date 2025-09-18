# Examen_1_ModelosNoLineales
Un repositorio colaborativo para el examen 1 de modelos no lineales 

---
## Integrantes del Equipo

- **Esteban Javier Verumen Nieto**  
- **Mariana Salomé García González**  
- **Remi Heredia Pérez**  
- **Ivanna Camerota Curiel**  
- **Juan Pablo Echeverría Villaseñor**

---

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellow.svg?logo=pandas&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-SARIMA-green.svg?logo=statsmodels&logoColor=white)
![Banxico](https://img.shields.io/badge/Data-Banxico-orange.svg?logo=google-scholar&logoColor=white)

---

##  Contexto

El tipo de cambio **FIX** es determinado por el **Banco de México** con base en un promedio de cotizaciones del mercado de cambios al mayoreo para operaciones liquidables el segundo día hábil bancario siguiente y que son obtenidas de plataformas de transacción cambiaria y otros medios electrónicos con representatividad en el mercado de cambios.
  

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/6/6e/Logobm.svg" alt="" width=300/>
</p>


---


##  Objetivo del Proyecto

Desarrollar un **modelo SARIMA (Seasonal ARIMA)** que:  
1. Analice el comportamiento histórico de la TIIE .  
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
  
## Selección del Modelo SARIMA

### 1. Elección de los órdenes (p, d, q)

-   **d (diferenciación no estacional):**  
    Se aplicaron pruebas de estacionariedad (ADF, KPSS) y análisis visual de la serie. El tipo de cambio FIX mostró tendencia en ciertos periodos, por lo que se aplicó una diferenciación para estabilizar la media.
    
-   **p y q (orden autorregresivo y de medias móviles):**  
    Se utilizaron las gráficas de **Autocorrelation Function (ACF)** y **Partial Autocorrelation Function (PACF)**:
    
    -   Un corte significativo en el PACF sugirió un orden **p** inicial.
        
    -   Un corte en el ACF sugirió un orden **q** inicial.
        
    -   Se probaron distintas combinaciones y se seleccionó la que minimizó el criterio AIC/BIC.
        

### 2. Elección de los órdenes estacionales (P, D, Q, s)

-   **s (periodicidad estacional):**  
    Se determinó con base en la frecuencia de los datos (diarios hábiles) y en el análisis exploratorio, donde se observan patrones semanales. Se estableció `s = 5` para capturar estacionalidad semanal de días hábiles.
    
-   **D (diferenciación estacional):**  
    Evaluada a partir de estacionalidad visible en la descomposición de la serie. Se aplicó diferenciación estacional solo si la serie no resultaba estacionaria tras el primer paso.
    
-   **P y Q (órdenes AR y MA estacionales):**  
    Identificados mediante picos en la ACF y PACF en los rezagos múltiplos de `s`.
    

### 3. Justificación del uso de SARIMA

-   El tipo de cambio FIX presenta **tendencias de largo plazo** con fluctuaciones de corto plazo.
    
-   Los datos muestran **patrones recurrentes de estacionalidad semanal** (ligeros cambios entre inicio y fin de semana).
    
-   El modelo SARIMA permite capturar:
    
    -   Tendencia → con diferenciación no estacional.
        
    -   Estacionalidad → con componentes estacionales (P, D, Q, s).
        
    -   Ruido y fluctuaciones → con los términos AR y MA.
        

En comparación con un ARIMA simple, SARIMA fue más adecuado porque incorporó la estacionalidad semanal, lo que redujo los errores de pronóstico y mejoró el ajuste en la validación.

