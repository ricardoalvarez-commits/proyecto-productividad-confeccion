# ¿Por qué los equipos no cumplen su meta? — Productividad en una planta de confección

Proyecto del curso **Data Analytics en Gestión Industrial** (Universidad de Ibagué).
Analizamos y predecimos si los equipos de una planta de confección cumplen su meta de productividad, usando datos abiertos.

**Integrantes:**
- Ricardo Alvarez Zapata — cód. 2320221005
- Juan David Díaz Riaño — cód. 2320221023
- Andres Urueña — cód. 2320212016

## Resultados principales
- **Incumplimiento de la meta:** el **27 %** de las jornadas (323 de 1 197) no cumple la meta. En **acabado** no la cumple el 40 % y en **costura** el 17 %.
- **Incentivo en costura:** las jornadas **sin incentivo** no cumplen el 65 % de las veces; **con incentivo**, solo el 8 %.
- **Clustering (K-Means, k = 3):** separa tres tipos de jornada: costura estable, acabado inestable y costura con cambio de estilo.
- **Clasificación:** el mejor modelo es **Random Forest** (F1 0.69, ROC-AUC 0.84; en validación cruzada, 0.86 ± 0.03). Con umbral 0.35 detecta el 79 % de las jornadas que no cumplen.
- **Regresión:** Random Forest predice la productividad con un error promedio de 0.07 (R² 0.52).
- **PCA y LDA:** **PCA** sirve para visualizar, pero empeora la clasificación. **LDA** mejora a kNN (F1 pasa de 0.35 a 0.49).

## Contenido de esta carpeta
```text
├── Proyecto/
│   └── project.ipynb                      ← código: ETL, EDA y modelado (Fases 1 a 4)
├── datasets/
│   ├── garments_worker_productivity.csv   ← datos originales (zona RAW)
│   ├── garments_limpio.csv                ← datos limpios (zona procesada)
│   └── modelo_datos/                      ← modelo estrella: hechos_produccion, dim_fecha, dim_equipo
├── requirements.txt                       ← librerías y versiones
└── README.md
```

## Cómo reproducirlo
1. Instalar Python 3.12.
2. Instalar las librerías:
   ```
   pip install -r requirements.txt
   ```
3. Abrir `Proyecto/project.ipynb` en VS Code o Jupyter y ejecutar **Run All**. Tarda unos 4 minutos.

La semilla aleatoria está fija (`RANDOM_STATE = 42`), así que cada ejecución da los mismos resultados.

## Datos
Imran, A. A., Rahim, M. S., & Ahmed, T. (2021). *Productivity Prediction of Garment Employees* [Dataset].
UCI Machine Learning Repository. https://doi.org/10.24432/C51S6D — Licencia **CC BY 4.0**.
Son 1 197 registros × 15 variables de una planta en Bangladesh (enero a marzo de 2015).

## Uso de inteligencia artificial
- **Para qué la usamos:** un asistente de IA (Claude, de Anthropic) nos ayudó a depurar errores del código y nos ayudo en algunas interpretaciones.
.
- **Datos y costos:** Los costos del plan de acción son estimaciones, y sus supuestos están explicados en el informe.
