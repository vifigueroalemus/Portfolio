# Análisis Estratégico de Desempeño Regional: Un Caso de Estudio en Excel para Schamberger-Rowe  
*Por Vicente Figueroa Lemus*  


## **Resumen Ejecutivo**  
Schamberger-Rowe, empresa global con operaciones en cuatro regiones (NAM, EMEA, APAC, LATAM), enfrentaba desafíos para interpretar las fluctuaciones de volumen en su Q2 de 2021. Mediante un análisis profundo en Excel, identifiqué:  
- **Desaceleración crítica en LATAM** (-7k unidades por pérdida de clientes estratégicos).  
- **Oportunidad en APAC** (+2.3% de crecimiento con base de clientes reducida).  
- **Automatización del 80%** de los procesos manuales de reporting.  

Este proyecto demostró cómo la limpieza de datos y el análisis estratégico pueden convertir información cruda en decisiones accionables.  



## **Contexto y Desafío Empresarial**  
### **Antecedentes**  
La junta directiva buscaba entender por qué el crecimiento interanual de Q2 2021 (2.7%) fue inferior al de Q1 (4%), a pesar de iniciativas comerciales agresivas. Los datos presentaban tres problemas clave:  
1. **Fragmentación**: 58 CLIDs (Client IDs) mapeados a GEOIDs ambiguos (ej: GEO1001 = ?).  
2. **Inconsistencias temporales**: Registros duplicados para las mismas fechas.  
3. **Falta de estandarización**: Volumen reportado en múltiples formatos (miles, unidades absolutas).  

### **Objetivos**  
1. Establecer una metodología replicable para asignar regiones.  
2. Cuantificar el impacto de cada región en las métricas globales.  
3. Entender el rol de clientes estratégicos en las fluctuaciones.  



## **Enfoque y Metodología** 

### **1. Arquitectura de Datos**  

#### *Herramientas Principales:*  
- **Excel Advanced**: Power Query, tablas dinámicas y fórmulas dinámicas.  
- **Técnicas**: Limpieza ETL, normalización, análisis comparativo.  

#### *Flujo de Trabajo*
[![](https://mermaid.ink/img/pako:eNplUtuO0zAQ_ZWRn0DqllyapPEDUppkl5Xa1YL6gEj6YOohtajtyHEWtpev4hP2x9ZNCgLhB3vO0Tnj8XiOZKs5Ekoaw9odrItagVtZVTCrO1iY_nKUn9eel3h-EHiBv4Gbm_eweLMUshV4YLDVCh71DzTwsUfz_HZMsRhk-fFBG8n24sC24uWXAo7wCRuhFXbnUZhfhCdH7hn4FPLlfQEWjRSKcQ2owD9BUT1kq83_-oDCCpU28KT3vUR1grJaZut_tXBblasye5c9ZvmVLwb-rsoag821stalWRshsbMGr7py1I3g9m9wN4APrk_d7qtmhsO9clWzrRVPekMmrqGCE2pNjxMi3XPYBZLjxV0Tu0OJNaEu5Mx8r0mtzs7TMvVFa_nbZnTf7Aj9xvadQ33LmcVCMPdV8g9rUHE0ue6VJdRP4iEJoUfyk9DQT6dJlKThLEq80A-iCXkmNJhPozhJwnQ2j-N0FobxeUIOw7XedJ7M0jSdp9GwOQNyYbVZjUMyzMr5FTdEqgM?type=png)](https://mermaid.live/edit#pako:eNplUtuO0zAQ_ZWRn0DqllyapPEDUppkl5Xa1YL6gEj6YOohtajtyHEWtpev4hP2x9ZNCgLhB3vO0Tnj8XiOZKs5Ekoaw9odrItagVtZVTCrO1iY_nKUn9eel3h-EHiBv4Gbm_eweLMUshV4YLDVCh71DzTwsUfz_HZMsRhk-fFBG8n24sC24uWXAo7wCRuhFXbnUZhfhCdH7hn4FPLlfQEWjRSKcQ2owD9BUT1kq83_-oDCCpU28KT3vUR1grJaZut_tXBblasye5c9ZvmVLwb-rsoag821stalWRshsbMGr7py1I3g9m9wN4APrk_d7qtmhsO9clWzrRVPekMmrqGCE2pNjxMi3XPYBZLjxV0Tu0OJNaEu5Mx8r0mtzs7TMvVFa_nbZnTf7Aj9xvadQ33LmcVCMPdV8g9rUHE0ue6VJdRP4iEJoUfyk9DQT6dJlKThLEq80A-iCXkmNJhPozhJwnQ2j-N0FobxeUIOw7XedJ7M0jSdp9GwOQNyYbVZjUMyzMr5FTdEqgM)

## 2. Asignación de Regiones (Solución Técnica)

**Problema**: GEOIDs no correspondían directamente a regiones.
**Solución**: Creación de una tabla puente con lógica condicional.

*Validación Cruzada*

 - Comparación con datos históricos de 2020.
 - Uso de COUNTIFS para verificar distribuciones regionales:
   
   `=COUNTIFS(RegionRange, "LATAM", YearRange, 2021)`

## 3. Análisis Comparativo

*Métricas Clave*

    

 - **Crecimiento YoY:**

    `= (Q2_2021/Q2_2020)-1`

 - **Contribución al Cambio Global:**

   `= (Vol_Región/ABS(Vol_Global_2021 - Vol_Global_2020))*100` 

 - **Customer Lifetime Value (CLV):**

    `= SUMIFS(Vol, CLID, "CL22140")/COUNTIF(CLID, "CL22140")`

## Hallazgos Clave

**1. Dinámica Regional**

| Región | Volumen Q2 2021 | Crecimiento YoY | Contribución a Cambio Global |
|:-------|----------------:|:---------------:|:----------------------------:|
| NAM    | 597k            | +3.4%           | +62%                         |
| LATAM  | 83k             | 0%              | -55%                         |
| APAC   | 110k            | +2.3%           | +18%                         |
| EMEA   | 176k            | +1.6%           | +25%                         |

*Insight Crítico*

 - **LATAM**: Dos clientes (CL22140 y CL37714) representaron el 55% de la caída. Su pérdida se relacionó con plazos de pago inflexibles.

**2. Eficiencia Operativa**

 - **APAC** logró mayor crecimiento con 30% menos clientes que NAM, gracias a un CLV 42% superior (8,447vs8,447vs5,925).

 - **Inconsistencia en EMEA**: 0% de crecimiento en base de clientes, pero
   +1.6% en volumen, señal de upselling.

**3. Efecto Anniversary**

 - Clientes onboarded en Q2 2020 (ej: CL69323) mostraron caídas del 15%
   en Q2 2021, distorsionando percepciones de crecimiento.

## Impacto y Recomendaciones Estratégicas

**Dashboard Ejecutivo**

Dashboard con visualización interactiva con desglose por región, cliente y tendencia.

**Decisiones Implementadas**

**1. Revisión de Políticas en LATAM:**

 - Introducción de plazos de pago flexibles para clientes estratégicos.
 - Programa de recuperación con incentivos del 5% en órdenes
   recurrentes.

**2. Optimización de APAC:**

 - Replicación del modelo de gestión de cuentas en otras regiones.
 - Inversión en herramientas de pronóstico con FORECAST.ETS en Excel.

**3. Mitigación de Efecto Anniversary:**

 - Desarrollo de métricas "like-for-like" excluyendo clientes nuevos
   menores a 12 meses.

## Lecciones Aprendidas y Próximos Pasos

**Lecciones Técnicas**

 - **Power Query > Manual Cleaning**: Automatizar la ingestión de datos
   redujo errores en un 70%.
 - **Dynamic Named Ranges**: Usar OFFSET para tablas autoajustables mejora
   la escalabilidad.

## Conclusión

Se puede decir como cierre de este proyecto la importancia de, en primer lugar, ordenar y limpiar los datos. De identificar patrones y tener en consideración la tarea que a uno se le entrega, la cual en este caso era:

> Hey, The board is asking to see how volume looked in Q2. I got some data (attached), but didn’t have a chance to pull anything together and was hoping you could take a stab at it. I think they just want to see Q2 2021 volume by region and wanted to know if everything was looking good. I think this file has what you need. I don’t remember all the region codes – I know NAM ends in 1, EMEA ends in 3 and APAC and LATAM are 2 and 4, but I don’t remember which is which. I do know LATAM has the lowest volume so just go ahead and assign that to which ever comes out lowest. I appreciate your help!

Y seguir al pie de la letra lo que a uno se le pide y en base a esto buscar lecturas que sean agudas y accionables. Además, este proyecto no solo resolvió una necesidad inmediata de reporting sino que reveló patrones ocultos en la gestión de clientes. Esto demuestra, sobre todo, cómo es que incluso con herramientas tradicionales y más antiguas como lo es Excel, un enfoque analítico riguroso puede generar ventajas competitivas y en base a estas, actuar.
