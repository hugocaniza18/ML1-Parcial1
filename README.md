# Primer Parcial - Machine Learning 1

## Objetivo

Este trabajo analiza el rendimiento académico de estudiantes de la asignatura **Métodos Numéricos** con el objetivo de estimar la probabilidad de que un estudiante alcance una firma final de **71 puntos o más**.

La pregunta principal planteada fue:

**¿Qué factores académicos disponibles después del primer parcial permiten estimar la probabilidad de que un estudiante alcance una firma final de 71 puntos o más?**

El problema fue abordado como una tarea de **clasificación binaria**, donde la variable objetivo `exonera` toma los siguientes valores:

- `1`: el estudiante alcanza una firma mayor o igual a 71.
- `0`: el estudiante no alcanza dicho puntaje.
---
## Estructura del proyecto

```text
ML1-Parcial1/
├── README.md
├── data/
│   ├── dataset_metodos_numericos_completo.csv
│   ├── dataset_metodos_numericos_modelo.csv
│   ├── rendimiento_año_2025_ciclo_1_anon.xlsx
│   └── rendimiento_año_2025_ciclo_2_anon.xlsx
└── notebooks/
    ├── 01_preprocesamiento.ipynb
    ├── 02_EDA.ipynb
    └── 03_modelo.ipynb
```
---
## Notebooks

### `01_preprocesamiento.ipynb`

Este notebook contiene la preparación y construcción del dataset utilizado posteriormente en el análisis y modelado.

Incluye:

- carga y revisión inicial de los datos;
- selección de la cohorte de estudiantes de Métodos Numéricos;
- construcción de la firma previa;
- construcción de variables relacionadas con la carga académica;
- cálculo del rendimiento académico del ciclo anterior;
- agrupación de los códigos según la carrera;
- construcción de la variable objetivo `exonera`;
- revisión de valores faltantes, duplicados e inconsistencias;
- generación de los datasets procesados.

---

### `02_EDA.ipynb`

Este notebook contiene el análisis exploratorio de los datos con el objetivo de identificar patrones y relaciones entre las variables y la posibilidad de exonerar.

Se analizan:

- distribución de la variable objetivo;
- relación entre el primer parcial y la exoneración;
- relación entre la firma previa y la exoneración;
- rendimiento académico del ciclo anterior;
- carga académica;
- diferencias entre carreras;
- correlación entre variables;
- comportamiento de los estudiantes con primer parcial igual a cero.

---

### `03_modelo.ipynb`

Este notebook contiene la construcción, evaluación e interpretación de los modelos de clasificación.

Se utilizó **Regresión Logística** y se compararon dos enfoques:

- **Modelo base:** utiliza únicamente el puntaje del primer parcial.
- **Modelo completo:** incorpora además la firma previa, la carga académica, el rendimiento del ciclo anterior y la carrera.

Para la preparación de las variables se utilizaron:

- `StandardScaler` para las variables numéricas;
- `OneHotEncoder` para la variable categórica `carrera`;
- `Pipeline` y `ColumnTransformer` para integrar el preprocesamiento y el modelo.

---

## Evaluación de los modelos

Los modelos fueron evaluados utilizando:

- Accuracy;
- Precision;
- Recall;
- F1-score;
- ROC-AUC;
- matriz de confusión;
- validación cruzada estratificada de 5 folds.

Debido al desbalance presente en la variable objetivo, no se utilizó únicamente **Accuracy** para evaluar el rendimiento de los modelos.

---

## Resultados principales

El **primer parcial** resultó ser la variable con mayor influencia en la estimación de la posibilidad de alcanzar una firma de 71 puntos o más.

El rendimiento académico del ciclo anterior, especialmente la **tasa de aprobación**, también aportó información relevante.

El modelo completo presentó un rendimiento más estable que el modelo que utiliza únicamente el primer parcial.

En la validación cruzada estratificada, el modelo completo obtuvo aproximadamente:

- **F1-score promedio:** 0.81
- **ROC-AUC promedio:** 0.98

---

## Conclusión

Los resultados indican que el desempeño obtenido en el primer parcial es el principal factor para anticipar si un estudiante alcanzará una firma de 71 puntos o más.

Sin embargo, incorporar información sobre el rendimiento académico previo, la carga académica y la carrera permite mejorar la estabilidad y el desempeño del modelo.

Los resultados deben interpretarse considerando las limitaciones asociadas al tamaño de la muestra y al reducido número de estudiantes que alcanzaron el umbral de exoneración.
