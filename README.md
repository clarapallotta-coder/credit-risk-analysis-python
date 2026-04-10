# credit-risk-analysis-python
Credit Risk Analysis - python
Autor: Clara Pallotta

## Overview

Este proyecto analiza un dataset de riesgo crediticio con el objetivo de entender cómo se está asignando el riesgo y si esa asignación refleja el comportamiento real de default.

El análisis inicial (power bi) mostró una inconsistencia: los niveles de riesgo definidos no estaban alineados con las tasas de incumplimiento observadas.

A partir de esto, el proyecto se enfoca en reconstruir una lógica de riesgo más coherente basada en los datos.

---

## Objetivo

- Identificar los principales drivers del default  
- Evaluar la consistencia de la segmentación de riesgo original  
- Construir una segmentación basada en datos  
- Validar si la nueva lógica explica mejor el comportamiento del default  

---

## Dataset

- Fuente: Kaggle — Credit Risk Dataset  
- Observaciones: 45.000 préstamos  
- Variable objetivo: `loan_status` (default vs no default)

---

## Proceso

### 1. Entendimiento de los datos
- Revisión de la estructura del dataset  
- Identificación de variables relevantes (ingresos, características del préstamo, historial crediticio)  

### 2. Selección de variable clave
- Se utiliza `loan_percent_income` como proxy de debt-to-income ratio (DTI)  
- Esta variable representa la carga financiera del cliente  

### 3. Validación exploratoria
- Análisis de correlación entre:
  - default (`loan_status`)
  - ingresos
  - DTI  

- Primer hallazgo:  
  El DTI muestra una relación más fuerte con el default que el ingreso  

### 4. Segmentación basada en datos
- Aplicación de segmentación por cuantiles (`qcut`)  
- Creación de grupos según niveles de DTI  
- Cálculo del default rate por grupo  

### 5. Insights de la segmentación
- El default aumenta con el DTI  
- La relación no es lineal  
- En niveles altos de DTI, el default se incrementa de forma significativa  

Esto sugiere la existencia de un umbral de riesgo.

### 6. Reconstrucción del riesgo
- Se construye un nuevo score combinando:
  - DTI (mayor peso)
  - ingreso (menor peso)

- Se agrupan los clientes en niveles de riesgo  

### 7. Validación
- Se analiza el default por grupo de riesgo reconstruido  
- Se observa una relación monotónica clara:

A mayor riesgo, mayor default.

Esto confirma que la nueva lógica captura mejor el comportamiento real.

---

## Insights clave

- El DTI es el principal driver del default  
- El riesgo no es lineal y se intensifica en niveles altos de carga financiera  
- El ingreso por sí solo no explica el default  
- La segmentación basada en datos mejora la asignación de riesgo  
- El problema no estaba en los datos, sino en la definición del riesgo  

---

## Contexto del proyecto

Este análisis forma parte de un trabajo más amplio sobre el mismo dataset:

- Power BI: detección de inconsistencias en la asignación de riesgo  
- SQL: análisis y reconstrucción de la lógica  
- Python (este repositorio): validación del comportamiento  

---

## Herramientas utilizadas

- Python  
- Pandas  
- Seaborn  
- Matplotlib  

---

## Resultado

Se obtiene una segmentación de riesgo donde:

- Los niveles de riesgo están alineados con el default  
- Se captura la relación entre carga financiera y probabilidad de incumplimiento  

---
