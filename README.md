# FASHION-MNIST
Clasificación del conjunto de datos Fashion MNIST utilizando la función load_data de Keras

Carga datos

Se cargó el conjunto de datos Fashion MNIST utilizando la función load_data de Keras. Fashion MNIST es un conjunto de datos que se utiliza comúnmente para prácticas de clasificación de imágenes y es similar al conjunto de datos MNIST, pero en lugar de dígitos escritos a mano, contiene imágenes de prendas de vestir

Reorganización y Normalización

En esta sección se preparó los conjuntos de datos de imágenes (X_train y X_test) para ser utilizados en un modelo de aprendizaje profundo. La transformación incluye cambiar la forma de las imágenes, convertir los valores de píxeles a punto flotante y normalizar los valores de píxeles. Estos pasos son comunes en el preprocesamiento de datos para entrenar modelos de redes neuronales convolucionales (CNN).
Adicional se preparó las etiquetas para ser utilizadas en un modelo de clasificación de Keras, transformando las etiquetas enteras originales en una representación one-hot antes de entrenar o evaluar el modelo.

Visualización imagen random

Para la visualización las imágenes se codifican como matrices. Particularmente en escala de grises en una matriz de dos dimensiones, donde cada número representa la intensidad de un pixel. Tomamos una de las imágenes del dataset para observarla su impresión.para visualizar imágenes, usamos el módulo pyplot de la librería matplotlib.

Modelamiento

•	Creación modelo CNN
Para el modelo se crearon las siguientes capas: 
Conv2D: Primera capa convolucional con 32 filtros de 3x3.
De esta manera se calcula la salida de las neuronas que están conectadas localmente en la entrada, midiendo el peso y la región de la red a la que están conectadas y en que magnitud.
MaxPolling2D: Esta capa reduce dimensionalidad espacial de la salida convolucional.
La funcionalidad de esta red convolucional es el reconocimiento de imágenes aplicando un filtro que reducirá la dimensionalidad.
Conv2D: Segunda capa con 64 filtros de 3x3.
MaxPolling2D: Esta capa reduce la dimensionalidad espacial después segunda convolución.
Flatten: Esta capa aplana la salida de la última capa en un vector unidimensional.
Dropout: Esta capa previene el sobreajuste apagando el 50 % de las neuronas aleatoriamente.
Dense: Esta capa esta conectada con 64 neuronas.
Salida Dense: Esta capa tiene la salida con 10 neuronas (las 10 clases del dataset)
La sección final muestra el número total de parámetros de la red neuronal, así como el número de parámetros entrenables. En este caso, hay un total de 121930 parámetros y todos son entrenables. El tamaño total de los parámetros es de aproximadamente 476.29 KB.

•	Compilación modelo

Para la compilación se ajustó los pesos del modelo para minimizar la pérdida utilizando el optimizador Adam, la función de pérdida de entropía cruzada categórica y medirá la precisión como métrica durante el entrenamiento.
•	Entrenamiento Modelo
Para el entrenamiento se utilizó los datos de entrenamiento y las etiquetas proporcionadas. Los pesos del modelo se actualizarán iterativamente para minimizar la función de pérdida especificada durante el proceso de entrenamiento. El conjunto de validación se utilizará para evaluar el rendimiento del modelo en cada época.

Evaluación

•	Validación resultados
Para la validación se proporcionó información sobre el rendimiento del modelo en el conjunto de datos de prueba, permitiéndote entender qué tan bien generaliza el modelo a datos no vistos. La pérdida y la precisión son métricas comunes utilizadas para evaluar modelos de clasificación. Un valor bajo de pérdida y una alta precisión son indicativos de un buen rendimiento del modelo.


 TEST
•	Test loss: En este conjunto de prueba es aproximadamente 25%. La pérdida es una medida de qué tan bien el modelo está realizando las predicciones. Cuanto más cercano a cero sea el valor, mejor será el rendimiento del modelo.
•	Test accuracy: En este conjunto de prueba es aproximadamente 92%. La precisión es la proporción de predicciones correctas realizadas por el modelo en el conjunto de prueba. Una precisión más alta indica que el modelo está haciendo predicciones más precisas sobre los datos de prueba.

TRAIN
•	Train loss: La pérdida aproximadamente es 5.75%. Una pérdida más baja en el conjunto de entrenamiento indica que el modelo está haciendo buenas predicciones en los datos de entrenamiento.
•	Train accuracy: La precisión aproximadamente es del 98%. Indica que el modelo está realizando predicciones acertadas.

•	Matriz confusión
 
TRAIN

•	Indica qué tan preciso es el modelo al predecir la clase correspondiente. Por ejemplo, para la clase 0, el modelo tiene una precisión del 97%, lo que significa que el 97% de las muestras que el modelo predice como clase 0 son realmente de esa clase. Recall indica que el 98% de todas las muestras de la clase 0 fueron identificadas correctamente por el modelo. F1-score alto indica un buen equilibrio entre precisión y recall. 600 el número de muestras de cada clase en el conjunto de datos de entrenamiento

TEST

•	Indica qué tan preciso es el modelo al predecir la clase correspondiente. Por ejemplo, para la clase 0, el modelo tiene una precisión del 97%, lo que significa que el 88% de las muestras que el modelo predice como clase 0 son realmente de esa clase. Recall indica que el 89% de todas las muestras de la clase 0 fueron identificadas correctamente por el modelo. F1-score alto indica un buen equilibrio entre precisión y recall. 1000 el número de muestras de cada clase en el conjunto de datos de la prueba.


Las métricas son altas en general, podemos observar algunas diferencias entre las métricas en el conjunto de datos de entrenamiento y prueba. Por ejemplo, la precisión, recall y F1-score pueden ser ligeramente más altos en el conjunto de datos de entrenamiento en comparación con el conjunto de datos de prueba. Esto puede indicar que el modelo está sobreajustando ligeramente los datos de entrenamiento, lo cual es común en muchos modelos de aprendizaje automático.

Al observar las métricas para cada clase individual, podemos identificar si hay clases específicas para las cuales el modelo tiene un rendimiento inferior. Esto puede ayudar a identificar áreas de mejora para el modelo
