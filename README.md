## 1. Definición de Negocio, Objetivos y KPIs

### Problema de negocio
La alta tasa de cancelación (*churn*) de clientes en la industria de telecomunicaciones genera pérdidas recurrentes de ingresos y debilita la posición competitiva de la empresa. En este sector, se ha demostrado que captar un cliente nuevo es considerablemente más costoso (en términos de marketing, ventas y costos de incorporación) que retener a uno actual. 

El problema principal radica en que la empresa suele detectar la marcha del cliente tarde (cuando ya ha solicitado la baja del servicio), lo que imposibilita cualquier acción de contraoferta o retención oportuna.

### Objetivo del proyecto
El objetivo del proyecto es desarrollar, evaluar e implementar un modelo predictivo de Machine Learning capaz de identificar con antelación a los clientes con alta probabilidad de abandonar el servicio. Esto permitirá al departamento comercial y de atención al cliente anticiparse y desplegar campañas de retención preventivas y focalizadas (tales como descuentos segmentados, mejoras de planes o soporte técnico prioritario).

### KPIs (Indicadores Clave de Desempeño)
Para medir el éxito tanto técnico como financiero de la solución, se han definido los siguientes indicadores:

* **Tasa de Churn Global (Negocio):** 
  * *Definición:* Porcentaje actual de clientes que cancelan el servicio en un periodo determinado. 
  * *Propósito:* Establecer la baseline del problema antes de aplicar el modelo.
* **Recall y Precision / F1-Score (Técnico):** 
  * *Definición:* Métricas de evaluación del modelo de clasificación.
  * *Propósito:* Equilibrar los falsos positivos frente a los falsos negativos. Se priorizará el recall para asegurar la mayor captura posible de clientes en riesgo.
* **ROI de la Campaña de Retención (Financiero):** 
  * *Definición:* Retorno de inversión estimado al comparar el costo de las ofertas de retención aplicadas mediante el modelo frente a las campañas masivas a ciegas o la pérdida directa de ingresos por cada cliente fugado.
 
### Descripción Fuentes de Datos utilizadas
Para este proyecto se usó el Dataset Telco Customer Churn, este consta de una lista de 7043 clientes de una empresa de telecomunicaciones, este cuenta con la variable objetivo churn, la cual es nuestro trabajo predecir mediante una solución de Machine Learning.

## 2. Preparación y Análisis Exploratorio de Datos (EDA)

### Auditoría de Calidad y Limpieza de Datos
* **Transformación de Variables:** La variable objetivo `Churn` fue mapeada a valores binarios, y se aplicó codificación *One-Hot Encoding* para transformar las variables categóricas en estructuras numéricas aptas para los algoritmos de Machine Learning, además la columna  `TotalCharges` fue transformada de objeto a integer.
* **Valores Nulos y Duplicados:** Se verificó la presencia de nulos y duplicados, ambos tipos de datos fueron eliminados del Dataset.

### Hallazgos del Análisis Exploratorio (EDA)
* **Desbalance de Clases:** El análisis de la distribución de la variable objetivo muestra una proporción menor de clientes que cancelan el servicio frente a los que se quedan, lo que justifica el uso de métricas orientadas a la matriz de confusión (como el Recall) por encima del Accuracy global.
* **Variables Relevantes:** Los gráficos bivariados evidencian que los clientes con contratos a corto plazo y cargos mensuales elevados presentan una propensión significativamente mayor al abandono en comparación con aquellos bajo contratos anuales o bianuales, por esto contrato es uno de los predictores más potentes del modelo.
* **Servicio de Internet**: Los clientes que utilizan fibra óptica muestran una proporción de cancelación inusualmente alta en comparación con los usuarios de DSL o aquellos sin servicio de internet, lo que sugiere posibles problemas de satisfacción con este tipo de conexión o tarifas competitivas en el mercado.
* **Servicios de Seguridad y Soporte**: Los clientes que no cuentan con servicios adicionales de seguridad o soporte técnico presentan una tasa de cancelación significativamente mayor. Esto indica que un ecosistema de servicios más integrado reduce el abandono.
* **Método de Pago**: El método de pago cheque electrónico concentra la mayor cantidad de clientes que deciden abandonar el servicio frente a transferencias bancarias o tarjetas de crédito automáticas.

## Metodología Utilizada (CRISP-DM)

El desarrollo de este proyecto se estructuró bajo la metodología estandarizada CRISP-DM (Cross-Industry Standard Process for Data Science), la cual garantiza un enfoque iterativo y orientado a la resolución de problemas de negocio:

1. **Comprensión del Negocio:** Definición del problema de alta tasa de cancelación, establecimiento de objetivos orientados a la retención y selección de KPIs (como *Recall* y *ROI*).
2. **Comprensión y Preparación de los Datos:** Carga del dataset de Telco Customer Churn, validación de tipos de datos (conversión de `TotalCharges`), detección y tratamiento de nulos y codificación de variables categóricas.
3. **Análisis Exploratorio de Datos (EDA):** Visualización de la distribución de la variable objetivo, análisis de correlaciones numéricas y evaluación del impacto de variables clave (como el tipo de contrato) sobre la cancelación.
4. **Modelamiento:** Entrenamiento y comparación de modelos de clasificación supervisada (Regresión Logística y Random Forest).
5. **Evaluación:** Análisis de matrices de confusión, métricas de rendimiento y selección del modelo óptimo para el negocio.
6. **Despliegue / Conclusiones:** Reflexión sobre el impacto ético, mitigación de sesgos y potencial aplicación de las predicciones en campañas de marketing preventivas.

## 3. Modelamiento y Comparación de Algoritmos
Se entrenaron dos modelos de clasificación supervisada para predecir la variable objetivo churn: una Regresión Logística y un Random Forest.
| Métrica / Modelo | Regresión Logística | Random Forest |

| **Accuracy** | **0.80** | 0.78 |

| **Precision** | **0.65** | 0.62 |

| **Recall** | **0.56** | 0.50 |

| **F1-Score** | **0.60** | 0.55 |

#### Justificación y Selección del Modelo
Para este problema de negocio la Regresión Logística resulta ser superior porque obtiene un mayor Recall (56% frente al 50% de Random Forest). En el contexto de retención de clientes de telecomunicaciones,minimizar los falsos negativos es prioritario frente a los falsos positivos, ya que el costo de perder un cliente de forma definitiva supera ampliamente el costo de una campaña preventiva de retención.
