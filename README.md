# Segmentación de clientes de Costanera Andina

**Equipo 2 · Diego Améstica, Agustín Cáceres y Gino Andrades**  
**Asignatura:** Gestión de Proyectos de Datos · **Sección:** 001D  
**Profesor:** Ricardo Alfonso Pino

Este proyecto desarrolla una prueba de concepto para explorar cómo la segmentación de clientes podría apoyar las campañas de fidelización y las decisiones sobre la oferta comercial de Costanera Andina. El notebook aplica K-Means a **200 registros de referencia** y encuentra cinco grupos según el ingreso anual y el puntaje de gasto.

Los resultados permiten formular hipótesis para revisar con Marketing y Administración. La muestra utilizada es externa y no corresponde a datos acreditados de clientes de Costanera Andina, así que los perfiles deben validarse antes de usarlos para decisiones reales.

[Notebook de segmentación](notebooks/Clustering_CostaneraAndina_Equipo2.ipynb) · [Informe de avance EP5](reports/Informe_Avance_EP5_PRY01_Equipo02.pdf) · [Informe gerencial](reports/Informe_Gerencial_Costanera_Andina.docx) · [Contexto del negocio](reports/Contexto%20del%20Negocio/03_Segmentacion_Clientes_Centro_Comercial.docx)

![Infografía de los segmentos y propuestas para Marketing](images/extras/Infografia_Segmentacion_Costanera_Andina.png)

## 1. Problema y propósito

El caso plantea que Costanera Andina busca comprender mejor a sus visitantes para personalizar campañas y fundamentar decisiones sobre su oferta de tiendas. El proyecto explora si el ingreso anual y el puntaje de gasto permiten identificar perfiles diferentes y propone ideas que Marketing podría evaluar.

## 2. Datos y alcance del análisis

El notebook utiliza `Mall Customers.xlsx`, una muestra externa de referencia con 200 registros. No corresponde a datos acreditados de clientes de Costanera Andina.

Para formar los grupos se utilizan dos variables:

- **Ingreso anual**, expresado en miles de dólares.
- **Spending Score**, un índice de gasto entre 1 y 100.

El identificador `CustomerID` no entra al modelo. Edad, género, educación y estado civil se mantienen como variables descriptivas para revisar los grupos.

Durante la exploración se encontraron categorías `Unknown` en educación (13 %) y estado civil (7,5 %). También se detectaron dos valores atípicos de ingreso, que se conservaron. El preprocesamiento contempla imputación por mediana y estandarización de las variables numéricas. El notebook verifica la integridad del archivo de referencia mediante SHA-256.

## 3. Método y resultados

Se utilizó **K-Means** para agrupar registros con valores de ingreso y puntaje de gasto similares. El equipo comparó soluciones de uno a diez grupos. El método del codo y el mayor coeficiente de silueta favorecieron **K = 5**, con una silueta de **0,5547**.

La silueta resume qué tan cohesionados están los registros de un mismo grupo y qué tan separados quedan de los demás en esta muestra. Este resultado no demuestra por sí solo que los grupos sean estables o representativos de los clientes reales del centro comercial.

| Grupo | Registros | Muestra | Ingreso medio anual (miles de USD) | Puntaje medio | Perfil |
| --- | ---: | ---: | ---: | ---: | --- |
| 0 | 81 | 40,5 % | 55,3 | 49,5 | Ingreso y puntaje medios |
| 1 | 39 | 19,5 % | 86,5 | 82,1 | Ingreso y puntaje altos |
| 2 | 22 | 11,0 % | 25,7 | 79,4 | Ingreso bajo y puntaje alto |
| 3 | 35 | 17,5 % | 88,2 | 17,1 | Ingreso alto y puntaje bajo |
| 4 | 23 | 11,5 % | 26,3 | 20,9 | Ingreso y puntaje bajos |

Los grupos 1 y 3 tienen ingresos medios parecidos, pero sus puntajes de gasto difieren en aproximadamente 65 puntos. Esto sugiere que, en la muestra, un ingreso similar puede acompañarse de comportamientos de gasto distintos.

El informe gerencial propone ideas como beneficios preferentes, campañas de entretenimiento y descuentos. Son propuestas para evaluar, no campañas ejecutadas ni resultados comerciales medidos.

## 4. Avance del proyecto al corte EP5

El **Informe de Avance EP5** documenta la situación del proyecto al **22 de noviembre de 2026**. Presenta el trabajo técnico y el seguimiento académico en curso. Distingue las actividades registradas, las validaciones pendientes y las proyecciones preventivas.

### Trabajo técnico documentado

Al corte, el equipo contaba con un notebook de análisis exploratorio y segmentación, una solución K-Means con cinco grupos, la evaluación con el método del codo y silueta, y perfiles cuantitativos de los segmentos. El prototipo se desarrolló sobre la muestra externa de 200 registros.

El informe identifica como pendientes la prueba reproducible de estabilidad mediante ARI y la revisión técnica y comercial de los perfiles. También indica que el dashboard todavía no había comenzado y que no se acreditaba una aceptación formal del proyecto.

### Estado de las actividades de Trello

La planilla `PRY01_Trello_Control.xlsx` registra **27 actividades** con este estado al corte:

| Estado en Trello | Actividades |
| --- | ---: |
| Finalizadas | 20 |
| En proceso | 4 |
| En revisión | 2 |
| Por revisar | 1 |
| **Total** | **27** |

Las veinte tareas marcadas como finalizadas se relacionan principalmente con la comprensión del negocio y de los datos, la preparación y limpieza, el análisis exploratorio, el entrenamiento del modelo, la preparación de recomendaciones y el planteamiento de controles y riesgos.

Las siete actividades que todavía no figuraban como finalizadas eran:

| Código | Actividad | Estado al corte |
| --- | --- | --- |
| ACT-16 | Construcción y prueba del dashboard | Por revisar, sin checklist completado |
| ACT-19 | Informe de cierre y balance de recursos | En proceso |
| ACT-20 | Recepción y acta de cierre formal | En proceso |
| ACT-24 | Revisión de equidad en las recomendaciones | En proceso |
| ACT-25 | Seguimiento de mitigaciones de riesgos | En revisión |
| ACT-26 | Conciliación de presupuestos y reservas | En revisión |
| ACT-27 | Validación de riesgos de reidentificación | En proceso |

El estado de Trello sirve para seguir el trabajo académico. No equivale a la aceptación formal de un entregable por parte de un cliente o aprobador.

### Estado de los hitos

La pestaña de hitos de la planilla Trello registra H01 a H04 como finalizados en el tablero académico. H05, H06 y H07 seguían pendientes al corte:

- **H05 · Aprobación de los modelos de segmentación.** Requiere completar la evaluación de estabilidad y la revisión técnica y comercial.
- **H06 · Entrega y demostración del dashboard.** La actividad ACT-16 aún no había comenzado.
- **H07 · Cierre administrativo y contractual.** El informe de cierre y el acta de recepción seguían en proceso.

El informe advierte que un hito finalizado en el tablero académico no acredita aprobación institucional ni recepción formal.

## 5. Escenarios preventivos de plazo y presupuesto

El Informe EP5 y `PRY01_Control_Contingencias_y_Recuperacion.xlsm` incluyen ejercicios de planificación preventiva. El informe utiliza un T0 ilustrativo del **28 de agosto de 2026**, un plazo de 16 semanas y un cierre previsto del **17 de diciembre de 2026**. Estas fechas son supuestos académicos para el ejercicio y no acreditan un compromiso contractual ejecutado.

La planilla parte de un presupuesto base de **CLP $40.080.000**, reservas por **CLP $6.212.400** y un presupuesto con reservas de **CLP $46.292.400**. El límite del caso es **CLP $50.000.000**.

| Escenario simulado | Costo proyectado | Saldo respecto del límite |
| --- | ---: | ---: |
| Sin extensión, después de incidencias simuladas | CLP $45.860.000 | CLP $4.140.000 bajo el límite |
| Extensión de una semana con todos los recursos | CLP $48.365.000 | CLP $1.635.000 bajo el límite |
| Extensión de dos semanas con todos los recursos | CLP $50.870.000 | CLP $870.000 sobre el límite |
| Una semana con recursos selectivos | CLP $47.497.500 | CLP $2.502.500 bajo el límite |

Las incidencias, extensiones, costos y ahorros de esta sección son **supuestos de simulación**. No representan gastos realizados, retrasos confirmados, contratos renovados ni autorizaciones aprobadas.

## 6. Próximos pasos señalados en el seguimiento

1. Probar la estabilidad del agrupamiento con distintas inicializaciones o remuestreos, calcular ARI y documentar la decisión técnica.
2. Contrastar los perfiles con datos autorizados del centro y revisarlos con Marketing, Administración y TI.
3. Definir el alcance mínimo del dashboard, estimar su esfuerzo y probar sus funciones.
4. Completar las revisiones de equidad, privacidad y riesgo de reidentificación.
5. Reunir evidencias para los hitos pendientes y completar el cierre formal.
6. Revisar los escenarios de plazo y presupuesto antes de proponer cambios o extensiones.

## 7. Estructura del repositorio

```text
Proyecto Gestion/
├── README.md
├── data/
│   ├── raw/                                      Archivo original de referencia
│   ├── processed/                                Base preparada en CSV
│   └── segmentation/                             Asignaciones, perfiles, centroides y métricas
├── images/
│   ├── extras/                                   Infografía para presentar
│   └── modelo_segmentacion/                      Gráficos de evaluación y visualización de grupos
├── models/
│   └── Segmentacion_modelo/                      K-Means, preprocesador, PCA y metadatos
├── notebooks/
│   └── Clustering_CostaneraAndina_Equipo2.ipynb
└── reports/
    ├── Archivos Complementarios de esta Evaluacion/
    │   ├── Planilla_Costanera_Andina.excalidraw
    │   ├── PRY01_Control_Contingencias_y_Recuperacion.xlsm
    │   └── PRY01_Trello_Control.xlsx
    ├── Contexto del Negocio/
    │   └── 03_Segmentacion_Clientes_Centro_Comercial.docx
    ├── Informe_Avance_EP5_PRY01_Equipo02.pdf
    ├── Informe_Gerencial_Costanera_Andina.docx
    └── Presentacion_EP6_Costanera_Andina.pptx
```

### Contenido de las carpetas principales

- **`data/segmentation/`** contiene las asignaciones de grupo, centroides originales y estandarizados, métricas de K-Means, perfiles descriptivos, proyecciones PCA y archivos de prueba sintética.
- **`images/modelo_segmentacion/`** reúne los gráficos del método del codo, la silueta, los centroides, la varianza explicada y la visualización de los grupos.
- **`models/Segmentacion_modelo/`** guarda el modelo K-Means, el preprocesador, los transformadores PCA y los metadatos de configuración.
- **`notebooks/`** contiene el cuaderno que desarrolla el análisis, el modelado y la exportación de resultados.

### Informes y materiales de apoyo

- **`Informe_Avance_EP5_PRY01_Equipo02.pdf`** resume el prototipo técnico, el estado de las actividades e hitos, los asuntos pendientes y los escenarios preventivos.
- **`Informe_Gerencial_Costanera_Andina.docx`** explica los perfiles de la muestra y propone acciones que Marketing podría evaluar.
- **`Presentacion_EP6_Costanera_Andina.pptx`** sirve como apoyo visual para la exposición del proyecto.
- **`03_Segmentacion_Clientes_Centro_Comercial.docx`** describe el caso de negocio, sus objetivos y las necesidades del centro comercial.
- **`PRY01_Trello_Control.xlsx`** reúne el inventario de actividades, el estado de Trello, el seguimiento de hitos, la relación con CRISP-DM y los entregables con sus responsables.
- **`PRY01_Control_Contingencias_y_Recuperacion.xlsm`** incluye incidencias observadas, supuestos de riesgo, escenarios de costo y plazo, reservas y acciones de recuperación.
- **`Planilla_Costanera_Andina.excalidraw`** contiene un esquema visual de la planificación del equipo.

## 8. Reproducir el notebook

El análisis utiliza Python, pandas, NumPy, scikit-learn, Matplotlib, Seaborn y joblib. Para preparar un entorno local se pueden instalar las dependencias principales con:

```bash
python -m pip install jupyter pandas numpy openpyxl requests scikit-learn matplotlib seaborn joblib
```

Abre el notebook en Jupyter o Google Colab y ejecuta las celdas en orden. La descarga y verificación del archivo de referencia requieren conexión a internet.

Las celdas de exportación pueden crear una carpeta `archivos_segmentacion/` y un archivo ZIP en el directorio de trabajo. Los resultados organizados en este repositorio están en `data/segmentation/`, `models/Segmentacion_modelo/` e `images/modelo_segmentacion/`.
