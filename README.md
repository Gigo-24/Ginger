
# ⏱️ Análisis Temporal de Reclamos de Seguros  

### Proyecto SafeClaim — Propuesta 1

Este repositorio contiene el análisis exploratorio, de calidad de datos y análisis temporal aplicado al dataset PFDA_fraud_car.csv, con el objetivo de identificar patrones de fraude en reclamos de seguros de autos.
El análisis fue desarrollado en el notebook:

![Descripción de la imagen](fraude_vehiculos_-removebg-preview.png)


## 🎯 Objetivo del Proyecto

El objetivo principal es entender el comportamiento temporal del fraude, usando variables como:

- Día del accidente

- Día de la reclamación

- Mes del accidente

- Mes de la reclamación

- Diferencia temporal entre accidente → reclamación

- Patrones por tipo de vehículo

- Datos históricos presentes en la póliza

## El análisis incluye:

- Exploración inicial
- Calidad de datos
- Outliers
- Distribuciones
- Patrones de fraude
- 5 preguntas temporales clave
- Construcción del Índice de Riesgo Temporal (IRT)
- Reglas de negocio basadas en evidencia

## 📝 Dataset Utilizado

El dataset contiene características relacionadas con:

------------

- Edad del asegurado

- Edad del vehículo

- Tipo de vehículo

- Historial de reclamos

- Días entre póliza–accidente

- Meses y días de accidente y reclamación

- Información del reporte policial

- Variable objetivo: FraudFound (1 = fraude, 0 = legítimo)

------------
# 🔍 Metodología del Análisis

1. Importación y exploración inicial

## Incluye:
------------
- Visualización de primeras filas

- Tipos de datos

- Conteo de filas y columnas

- Identificación de columnas numéricas

- Estadísticas descriptivas
------------
## 2. Evaluación de calidad de datos
------------

- Registros duplicados

- Valores nulos

- Detección de outliers usando el método IQR

- Columnas con inconsistencias (especialmente edades = 0)

------------


## 3. Análisis de distribución

- Se evaluaron las variables más relevantes:

- Distribución de casos de fraude

- Edad de asegurados

- Categoría de vehículo

- Diferencias entre casos legítimos y fraudulentos

- Ejemplos incluidos en el notebook:

- Gráfico de distribución del fraude

- Histogramas de edad

- Boxplots por tipo de fraude

- Barras por categoría de vehículo

## 4.  Análisis de patrones temporales

El corazón del análisis responde 5 preguntas clave:

# 🧠 PREGUNTA 1:
##  ¿Hay meses del año con mayor incidencia de fraude?

## Se analizan:
------------
-  Mes del accidente
  
-  Distribución de fraude por mes

![Descripción de la imagen](fraude_vehiculos_-removebg-preview.png)

**Interpretacion:**

Los datos revelan un patron estacional de fraude:

- **Primer semestre (Ene-Jun):** Concentra el 87% de los fraudes
  - Marzo pico maximo: 12.56% de tasa de fraude
  - Q1 y Q2 tienen tasas >10%

- **Segundo semestre (Jul-Dic):** Casi libre de fraude
  - Q3 solo 0.44% de fraude (24 veces MENOR que Q1)
  - Septiembre y Octubre: 0% de fraude

- **Patron de reclamacion:** Los defraudadores reclaman inmediatamente
  - El heatmap muestra concentracion en la diagonal (mismo mes)
  - No esperan para reclamar, actuan rapido

**Implicacion de Negocio:**
Este patron NO puede ser coincidencia. Sugiere comportamiento deliberado
y planificado. Se recomienda reforzar controles en el primer semestre
del año, especialmente en marzo-mayo.

## Hallazgos clave:

- Meses con mayor fraude: enero, abril y mayo.

- Meses con menor fraude: julio y noviembre.

- Las reclamaciones fraudulentas tienden a concentrarse al inicio del año.

------------

# 🧠 PREGUNTA 2:

## ¿Existen patrones por DÍA DE LA SEMANA?

##Se examinan:

------------
- Día del accidente

- Día de la reclamación

- 

## Hallazgos clave:

- Martes y jueves muestran tasas de fraude anormalmente altas.

- Viernes presenta incremento también.

- Sábados y domingos presentan menor incidencia.

------------



# 🧠 PREGUNTA 3:
## ¿Cuál es la diferencia temporal entre accidente y reclamación?

## Se analiza:

- Meses transcurridos entre accidente → reporte

- Comparación entre casos fraudulentos y legítimos

## Conclusiones:

- El fraude suele tardarse más en reportarse.

- La ventana "mes siguiente" concentra el 25% del fraude, más del doble que el mismo mes del accidente.

- Los reclamos inmediatos (mismo día) rara vez son fraudulentos.
- 
# 🧠 PREGUNTA 4:
## ¿Podemos construir un Índice de Riesgo Temporal (IRT)?

Se desarrolla un índice que combina:

- Mes del accidente

- Mes de la reclamación

- Diferencia temporal

- Días de la semana

- Meses críticos

## Resultados del IRT:

- Se identifican combinaciones específicas de fecha → reclamación con mayor probabilidad de fraude.

- Mejora el recall del análisis con 47% de identificación de fraude.

# 🧠 PREGUNTA 5:
## ¿El tipo de vehículo influye en los patrones temporales?

## Hallazgos:

- Los vehículos tipo Sport presentan mayor tasa de fraude temporal.

- Las categorías Utility presentan menor riesgo.

- El IRT combinado con categoría es un predictor robusto.

# 📊 Conclusiones Generales

- El dataset está altamente desbalanceado (94% no fraude vs 6% fraude).

- Las variables temporales sí muestran patrones significativos.

- Los modelos futuros deben incluir mes, día, y diferencia entre fechas.

- Se identificaron 5 reglas temporales claras que funcionan como alertas tempranas.

- El IRT es un buen punto de partida para integrar en un modelo de ML o motor de reglas.


