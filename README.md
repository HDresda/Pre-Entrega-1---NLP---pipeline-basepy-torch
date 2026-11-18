# Pipeline base de clasificación con PyTorch
Proyecto integrador · Data Science III · Módulo 1. Preparado para Hans.

## Objetivo y datos
Clasificar las tres especies de Iris usando cuatro mediciones, con un MLP 4 → 16 → 16 → 3 y ReLU.
120 ejemplos de entrenamiento y 30 de validación; división estratificada y StandardScaler ajustado solo con entrenamiento.

## Configuración
- Semilla: 42
- Adam, learning_rate: 0.01
- Épocas: 50; batch_size: 16
- Pérdida: CrossEntropyLoss sobre logits, sin Softmax previo.
- Datos: float32; etiquetas: long.

## Resultados reales de esta ejecución
La pérdida antes de entrenar fue 1.0924 en entrenamiento y 1.0948 en validación. En la época 50 fue 0.0239 y 0.1122, respectivamente. La pérdida mínima observada de validación fue 0.0825 en la época 48. Hubo 19 incrementos entre épocas consecutivas de validación (de 49 comparaciones). El accuracy final fue 96.67%, equivalente a 29/30 aciertos. Estas métricas corresponden a una partición pequeña y no prueban ausencia de sobreajuste.

![Curvas](reports/curvas_entrenamiento.png)
![Matriz de confusión](reports/matriz_confusion.png)

## Validaciones incorporadas
Dimensiones, conjuntos separados, gradientes finitos, actualización de pesos, métricas finitas y evaluación sin cambios en el modelo.
Las métricas de entrenamiento se acumulan durante las actualizaciones; validación se calcula al final de cada época.
No se utiliza un conjunto de test independiente ni se guarda/restaura un modelo de la mejor época.

## Estructura
- data/README.md: descripción del origen de los datos.
- notebooks/01_pipeline_base.ipynb: desarrollo autónomo y comentado.
- reports/: métricas, resumen con configuración e índices y figuras.
- requirements.txt: versiones del entorno verificado.

## Fuentes
Material adjunto: presentación Módulo 1 Data Science III, diapositivas 30–39, y notebook de clase, Parte 4.
- https://docs.pytorch.org/tutorials/beginner/basics/optimization_tutorial.html
- https://docs.pytorch.org/docs/stable/generated/torch.nn.CrossEntropyLoss.html
- https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_iris.html
- https://scikit-learn.org/stable/common_pitfalls.html

## Alcance
Pre-entrega técnica: pipeline funcional y comprensible. Las 30 muestras de validación no permiten asegurar rendimiento en producción.
Un checkpoint de pesos es opcional y no forma parte de esta versión.

### Interpretación del experimento:
La pérdida (*loss*) descendió de manera consistente a lo largo de las 50 épocas tanto en el conjunto de entrenamiento como en el de validación. Ambas curvas convergen de forma pareja sin que la pérdida de validación se dispare hacia arriba, lo que demuestra que el clasificador base aprende patrones generalizables y no presenta *overfitting* severo.

