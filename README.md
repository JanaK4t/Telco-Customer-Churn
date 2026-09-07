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
