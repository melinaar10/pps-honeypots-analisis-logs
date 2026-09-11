# Demo: Análisis Exploratorio de Logs de Honeypots (T-Pot / Cowrie)

Este repositorio contiene una Prueba de Concepto (PoC) desarrollada en Python (Jupyter Notebook, Pandas, Matplotlib) orientada al análisis avanzado de eventos de ciberseguridad.

## Objetivo
El objetivo de esta demostración es procesar eventos simulados (manteniendo la estructura de los registros que genera el honeypot **Cowrie** dentro del ecosistema **T-Pot**) para extraer inteligencia procesable. Se busca superar las limitaciones de los dashboards estáticos mediante la manipulación programática de los datos, enfocándose en evaluar la efectividad de las tácticas de *Cyber Deception* (engaño cibernético).

## Contenido del Notebook (`demo_analisis_honeypot.ipynb`)
1. **Generación de datos:** Simulación de un dataset de eventos y sesiones completas de atacantes, aplicando distribuciones estadísticas reales (Poisson y Exponencial) para diferenciar el comportamiento automatizado (bots) de la exploración humana.
2. **Análisis Exploratorio (EDA):** Identificación de IPs atacantes más frecuentes, picos de actividad temporal y distribución geográfica análoga a la ingesta de Elasticsearch/Kibana.
3. **Métrica Personalizada ("Índice de Profundidad de Engaño"):** Desarrollo de un algoritmo basado en agrupaciones temporales (`groupby`) que analiza sesiones completas para calcular el promedio de comandos ejecutados y la duración de la sesión por ventana de 6 horas. 

## Aplicación Práctica
Medir únicamente el volumen de ataques no responde qué tan bien está funcionando el engaño. Sesiones cada vez más "profundas" (mayor duración y cantidad de comandos) indican que el honeypot resulta convincente o que está atrayendo actores más sofisticados. Conectando este script a la API de Elasticsearch/OpenSearch en un entorno de producción, este análisis sienta las bases para aplicar modelos de detección de anomalías y *Machine Learning* sobre datos históricos, distinguiendo automáticamente el ruido superficial de intentos de explotación elaborados.
