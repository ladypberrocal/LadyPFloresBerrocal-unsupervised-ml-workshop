# 🧠 Informe del Taller de Aprendizaje Automático No Supervisado y Supervisado – Dataset de Setas

## 1️⃣ Descripción General

El presente trabajo tiene como objetivo aplicar técnicas de **aprendizaje automático supervisado y no supervisado** sobre el dataset de **setas (Mushrooms)** del repositorio **UCI Machine Learning Repository**.  
Este conjunto de datos contiene información sobre diferentes características físicas y químicas de los hongos, con la finalidad de determinar si son **comestibles (edible)** o **venenosos (poisonous)**.

El proyecto combina dos enfoques complementarios:

- **Aprendizaje no supervisado:** PCA y K-Means, para explorar la estructura interna de los datos y descubrir posibles patrones.
- **Aprendizaje supervisado:** Random Forest, para construir un modelo predictivo capaz de clasificar correctamente los hongos según sus características.

---

## 2️⃣ Flujo de Trabajo del Proyecto

El desarrollo del proyecto siguió una secuencia lógica y estructurada conformada por las siguientes etapas:

1. **Carga y exploración del dataset:**  
   Se revisaron los valores nulos, el balance entre clases y la estructura de los datos.

2. **Preprocesamiento:**  
   - Se codificaron las variables categóricas mediante *One-Hot Encoding*.  
   - Se normalizaron los valores con *StandardScaler* para optimizar el rendimiento de los modelos.  
   - Se generó un dataset limpio y preparado para el modelado.

3. **Análisis de Componentes Principales (PCA):**  
   Se redujo la dimensionalidad a dos componentes para visualizar la estructura general de los datos en un plano 2D.

4. **Clustering con K-Means:**  
   Se aplicó para identificar agrupamientos naturales sin usar etiquetas reales, comparando los clusters con las clases verdaderas.

5. **Clasificación Supervisada con Random Forest:**  
   Se entrenó un modelo para predecir si un hongo es comestible o venenoso, evaluando métricas de rendimiento y overfitting.

6. **Evaluación Final:**  
   Se analizaron los resultados de cada técnica y se extrajeron conclusiones generales del comportamiento de los datos.

---

## 3️⃣ Resultados Principales

### 🔹 PCA – Análisis de Componentes Principales

El PCA permitió reducir la dimensionalidad del dataset a 2 componentes principales, capturando la mayor parte de la varianza.  
Sin embargo, los puntos (hongos comestibles y venenosos) se mostraban mezclados, sin una frontera clara entre ambos grupos.  

📘 **Interpretación:**  
El PCA no clasifica, solo resume la información y proyecta los datos en un espacio reducido para facilitar su visualización.  
Fue útil para observar la estructura general antes de aplicar K-Means.

---

### 🔹 K-Means – Agrupamiento No Supervisado

El **método del codo** indicó que el número óptimo de clusters se encuentra entre **K = 2 y K = 3**, coincidiendo con las dos clases principales del dataset.

Con **K = 2**, el algoritmo separó los datos en dos grupos visualmente distinguibles (puntos amarillos y morados).  

📊 **Métricas de agrupamiento:**

| Métrica | Valor | Interpretación |
|----------|--------|----------------|
| Adjusted Rand Index (ARI) | 0.6182 | Buena concordancia entre clusters y clases reales |
| Normalized Mutual Information (NMI) | 0.5707 | Correlación moderada entre los agrupamientos y las etiquetas verdaderas |

💡 **Conclusión PCA vs K-Means:**  
La diferencia entre ambas visualizaciones no proviene de un cambio en los datos, sino en cómo se interpretan y agrupan.  
Mientras **PCA** solo reduce dimensiones, **K-Means** detecta patrones de similitud y logra distinguir grupos más evidentes en ese mismo espacio reducido.

✅ **Interpretación complementaria:**  
Estos valores están por encima de **0.5**, lo que indica una **buena concordancia** entre los grupos creados por K-Means y las etiquetas verdaderas (comestible vs venenoso).  
El **gráfico del codo** te dice **cuántos clusters formar**,  
y los valores de **ARI y NMI** te confirman **qué tan bien se formaron esos clusters**.  
En este análisis, ambos indicadores muestran que **K-Means logró una separación bastante buena** entre hongos comestibles y venenosos.

---

## 4️⃣ Clasificación Supervisada – Random Forest

El modelo Random Forest se entrenó con una división del 70% de los datos para entrenamiento y 30% para prueba.

### 📈 Métricas de Rendimiento

| Métrica | Valor |
|----------|--------|
| Accuracy global | 1.0000 |
| Precision (ambas clases) | 1.00 |
| Recall (ambas clases) | 1.00 |
| F1-score | 1.00 |

📊 **Matriz de Confusión:**

[[1263 0]
[ 0 1175]]

yaml
Copiar código

✅ El modelo clasificó correctamente todas las observaciones, sin cometer errores.

📘 **Interpretación:**  
El modelo alcanzó una precisión perfecta (100%), demostrando una excelente capacidad para distinguir hongos comestibles de venenosos.

---

## 5️⃣ Evaluación del Overfitting

| Tipo de Accuracy | Valor |
|-------------------|--------|
| Entrenamiento | 1.0000 |
| Prueba | 1.0000 |
| Overfitting (train - test) | 0.0000 |

✅ **Conclusión:**  
No se detecta overfitting significativo.  
El modelo generaliza correctamente, manteniendo el mismo rendimiento en entrenamiento y prueba.  
Esto significa que **no memorizó los datos**, sino que aprendió los **patrones reales** del dataset.

---

## 6️⃣ Conclusiones Generales

- El dataset fue correctamente preprocesado: sin valores nulos, balanceado y con variables bien codificadas.  
- **PCA** reveló que los datos no son fácilmente separables visualmente.  
- **K-Means** confirmó la existencia de **dos grupos naturales**, alineados con las clases comestible y venenosa.  
- **Random Forest** logró una **clasificación perfecta (100%)**, sin errores ni sobreajuste.  
- **ARI y NMI** demostraron que los clusters descubiertos tienen una buena relación con las etiquetas verdaderas.  

📊 En conjunto, los resultados evidencian que las características del dataset contienen **información suficiente y representativa** para distinguir ambas clases con total precisión.

---

## 7️⃣ Reflexión Final

Este trabajo demuestra cómo el uso combinado de **técnicas no supervisadas (PCA, K-Means)** y **supervisadas (Random Forest)** permite obtener una comprensión profunda de los datos:  
desde su estructura interna hasta su comportamiento predictivo.

El modelo desarrollado es **robusto, interpretable y eficiente**, representando una solución óptima para  la clasificación de hongos según sus propiedades físicas y químicas.

### 🔄 Flujo de Trabajo del Proyecto

```text
┌────────────────────────────┐
│     1️⃣ Carga del Dataset   │
│ (UCI Machine Learning Repo)│
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│     2️⃣ Exploración de Datos │
│ - Verificación de nulos     │
│ - Balance de clases         │
│ - Variables categóricas     │
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│     3️⃣ Preprocesamiento     │
│ - One-Hot Encoding          │
│ - Escalado (StandardScaler) │
│ - Exportación CSV limpio    │
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│       4️⃣ PCA (2D)           │
│ - Reducción de dimensional. │
│ - Visualización de clases   │
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│     5️⃣ K-Means Clustering  │
│ - Método del codo (K óptimo)│
│ - ARI / NMI                 │
│ - Visualización 2D grupos   │
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│  6️⃣ Random Forest (RF)     │
│ - Entrenamiento/Test split │
│ - Accuracy y OOB Score     │
│ - Overfitting (0.00)       │
│ - Importancia variables    │
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│    7️⃣ Interpretación Final  │
│ - PCA vs K-Means conclusión│
│ - Modelo RF sin sobreajuste│
│ - Insights clave del dataset│
└────────────────────────────┘

