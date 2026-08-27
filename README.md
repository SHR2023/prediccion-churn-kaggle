# Predicción de Churn en un Operador de Telecomunicaciones Móviles

Proyecto grupal — Caso de analítica de datos, Ciencia de Datos, Pontificia Universidad Javeriana.
1er lugar en la competencia de Kaggle del curso, con un AUC-ROC de 0.8881.

Autores: Sharid M. Rodríguez Wilches, Laura C. Ariza Ortiz, Juan D. Manosalva Duarte, Juan C. García Diaz.

## Problema de negocio

Un operador de telecomunicaciones móviles compite en un mercado saturado, sin espacio real para crecer con clientes nuevos, donde retener cuesta 5 veces menos que adquirir. Con una tasa de churn mensual cercana al 2%, el objetivo del proyecto fue anticipar qué clientes están en riesgo de abandonar el servicio para poder actuar antes de que se vayan, y priorizar esas intervenciones según el valor económico de cada cliente (CLTV).

## Metodología

El proyecto siguió la metodología **CRISP-DM** de principio a fin:

- **Business & Data Understanding:** análisis PESTLE, Fuerzas de Porter y SWOT del sector; definición de objetivos de negocio y de minería de datos; exploración de las variables disponibles (facturación, minutos, mora, antigüedad, tipo de cliente, entre otras).
- **Data Preparation:** ingeniería de variables (razones, transformaciones logarítmicas para variables con cola derecha, interacciones y términos polinómicos) y one-hot encoding de variables categóricas.
- **Modeling:** ensamble ponderado de dos modelos **XGBoost** con configuraciones complementarias de hiperparámetros, combinados como `0.7 × XGBoost A + 0.3 × XGBoost B`.
- **Evaluation:** validación cruzada estratificada de 5 particiones, con AUC-ROC como métrica principal (alineada con el criterio de la competencia).
- **Deployment:** propuesta de estrategias de retención focalizadas por nivel de riesgo y por valor del cliente (CLTV), e integración del modelo en un CRM predictivo.

## Resultados

| Métrica | Valor |
|---|---|
| AUC-ROC (validación cruzada) | ~0.8765 |
| AUC-ROC (Kaggle, modelo final) | **0.8881** |
| Resultado en la competencia | **1er lugar** |

El control de sobreajuste se manejó con validación cruzada estratificada, early stopping, subsampling y regularización (`gamma`, `min_child_weight`) dentro de cada modelo XGBoost.

## Contenido del repositorio

- `caso_churn.pdf` — reporte completo con la metodología CRISP-DM.
- Notebook con el desarrollo del modelo (ingeniería de variables, entrenamiento, ensamble).

## Herramientas

R · XGBoost · caret · validación cruzada estratificada
