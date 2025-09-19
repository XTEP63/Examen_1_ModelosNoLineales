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

###  FIX (Tipo de Cambio FIX)

 Es un *tipo de cambio oficial* publicado por el *Banco de México*.  

 Representa cuántos *pesos mexicanos equivalen a 1 dólar estadounidense (MXN/USD)*.  

 Se calcula con base en operaciones del mercado cambiario en México y se publica *una vez al día*.  

 *Se usa para:*  
•⁠  ⁠Facturación oficial.  
•⁠  ⁠Operaciones contables.  
•⁠  ⁠Liquidaciones de comercio exterior.  
•⁠  ⁠Referencia legal en contratos.  

 Es un *dato regulado y único*, que sirve como referencia oficial en México.  

---

<p align="center">
  <img src="https://monitorfinanciero.com.mx/wp-content/uploads/2024/07/Captura-de-pantalla-2024-07-11-a-las-3.41.37%E2%80%AFp.m.png" alt="" width=300/>
</p>


---


##  Objetivo del Proyecto

Desarrollar un **modelo SARIMA (Seasonal ARIMA)** que:  
1. Analice el comportamiento histórico del FIX .  
2. Identifique tendencias, estacionalidad y patrones relevantes.  
3. Genere proyecciones confiables a corto y mediano plazo.  

Los datos se obtienen directamente desde la **API de Banxico**, garantizando **fuentes oficiales y actualizadas**.

---

##  Metodología
1. **Obtención de datos**  
   - Conexión a la API de Banxico.  
   - Limpieza y preparación de la serie temporal.
  
    #### Ejemplo de datos (head)

| Fecha       | Tipo de Cambio |
|-------------|----------------|
|    1991-11-12    | 3.0735         |
|    1991-11-13    | 3.0712         |
|    1991-11-14    | 3.0718         |
|    1991-11-15    | 3.0684         |
|    1991-11-18    | 3.0673         |

2. **Análisis exploratorio (EDA)**  
   - Visualización de tendencias y estacionalidad.  
   - Pruebas de estacionariedad (ADF Test).
   - Selección de los datos que se utilizarán para el modelo.
     
        •⁠  ⁠Se obtuvieron los registros históricos del *Tipo de Cambio FIX* directamente de la API de Banxico.  
        •⁠  ⁠El dataset original contiene información desde *1991* hasta la fecha actual.  
        •⁠  ⁠Para fines de modelado y evaluación, se aplicó un *filtro temporal* considerando únicamente los *últimos 5 años de observaciones*.

3. **Construcción del modelo SARIMA**  
   - Identificación de parámetros (p, d, q, P, D, Q, s).  
   - Ajuste del modelo con ``.  

4. **Evaluación del modelo**  
   - Métricas: AIC, BIC, MAE, MAPE.  
   - Validación sobre datos de prueba.  

5. **Proyección**  
   - Forecast del FIX en el horizonte seleccionado.  
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

---
##AQUIII
---

# Examen_1_ModelosNoLineales
Repositorio colaborativo para el Examen 1 de **Modelos No Lineales**.

---

## 👥 Integrantes del Equipo
- **Esteban Javier Verumen Nieto**  
- **Mariana Salomé García González**  
- **Remi Heredia Pérez**  
- **Ivanna Camerota Curiel**  
- **Juan Pablo Echeverría Villaseñor**

---

![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellow.svg?logo=pandas&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-SARIMA-green.svg?logo=statsmodels&logoColor=white)
![Banxico](https://img.shields.io/badge/Data-Banxico-orange.svg?logo=google-scholar&logoColor=white)

---

## 📌 Contexto: FIX (Tipo de Cambio FIX)
El **FIX** es el *tipo de cambio oficial* publicado por el **Banco de México**. Indica **cuántos pesos mexicanos equivalen a 1 dólar estadounidense (MXN/USD)**.  
Se calcula con base en operaciones del mercado cambiario y se **publica una vez al día**.

**Usos principales**
- Facturación oficial  
- Operaciones contables  
- Liquidaciones de comercio exterior  
- Referencia legal en contratos  

> Es un dato **regulado y único** que funciona como referencia oficial en México.

---

## 📈 Histórico de la Serie
**Head de la serie original:**

| Fecha       | Tipo de Cambio |
|------------:|---------------:|
| 1991-11-12  | 3.0735 |
| 1991-11-13  | 3.0712 |
| 1991-11-14  | 3.0718 |
| 1991-11-15  | 3.0684 |
| 1991-11-18  | 3.0673 |

![Histórico](./html_files/Imagen%201.png)

**Corte 2021–Actualidad:**  
![Corte 2021](./html_files/Imagen%202.png)

---

## 🧹 Sustitución de días festivos y fines de semana
Se imputaron valores de días no hábiles con el valor del día hábil anterior para evitar saltos en la serie.

| Fecha       | Tipo de Cambio |
|------------:|---------------:|
| 1991-11-12  | 3.0735 |
| 1991-11-13  | 3.0712 |
| 1991-11-14  | 3.0718 |
| ...         | ... |
| 2025-09-15  | 18.3635 |
| 2025-09-16  | 18.3635 |
| 2025-09-17  | 18.3257 |

![Serie imputada](./html_files/Imagen%203.png)

---

## 🔀 División Train/Test
Se realizó un split temporal dejando el tramo final para validación.

| Fecha       | Tipo de Cambio |
|------------:|---------------:|
| 2021-01-01  | 19.9087 |
| 2021-01-02  | 19.9087 |
| 2021-01-03  | 19.9087 |
| ...         | ... |
| 2025-09-15  | 18.3635 |
| 2025-09-16  | 18.3635 |
| 2025-09-17  | 18.3257 |

![Train/Test](./html_files/Imagen%204.png)

---

## 📊 Pruebas de Estacionariedad
Se aplicaron pruebas **ADF** y **KPSS**:

- **ADF:** Statistic = `-1.4536`, p-value = `0.5563`  
- **KPSS:** Statistic = `2.0326`, p-value = `0.0100`  
**Conclusión:** La serie **NO** es estacionaria → aplicar diferenciación.

**Tras diferenciación (d=1):**
- **ADF:** Statistic = `-12.9547`, p-value = `0.0000`  
- **KPSS:** Statistic = `0.0706`, p-value = `0.1000`  
**Conclusión:** La serie es **estacionaria** después de 1 diferenciación.

---

## 🪓 Descomposición STL
![STL](./html_files/Imagen%205.png)

---

## 🔎 ACF y PACF
Se usaron para identificar p, q y componentes estacionales.

![ACF/PACF](./html_files/Imagen%206.png)

---

## 🔧 Modelo SARIMA
Parámetros seleccionados:  
\[
(p,d,q) = (1,1,1), \quad (P,D,Q,m) = (1,1,1,5)
\]

**Resultados de error:**
- **RAW:** RMSE = 0.1914, MAE = 0.1512  
- **LOG:** RMSE = 0.1892, MAE = 0.1503  
- **BOXCOX:** RMSE = 0.1805, MAE = 0.1446  

![Modelo](./html_files/Imagen%207.png)
![Diagnóstico 1](./html_files/Imagen%208.png)
![Diagnóstico 2](./html_files/Imagen%209.png)
![Forecast](./html_files/Imagen%2010.png)

---

## 📑 Métricas Finales

| Transformación | MAPE | Accuracy | RMSE | SMAPE |
|---------------:|-----:|--------:|-----:|------:|
| **Sin transformación** | 0.82% | 99.18% | 0.19 | 0.82% |
| **Logarítmica**        | 0.82% | 99.18% | 0.19 | 0.81% |
| **Box-Cox**           | 0.79% | 99.21% | 0.18 | 0.78% |

> La transformación **Box-Cox** obtuvo el mejor desempeño, con el menor error y mayor precisión.

---


