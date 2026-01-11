# ¿Por qué son importantes las métricas?

El objetivo de entrenamiento o función de coste es solo una **aproximación (proxy)** de los objetivos del mundo real.

Las métricas son fundamentales porque:

> [!NOTE] Capturan un objetivo de negocio
> Transforman un objetivo de negocio en una meta cuantitiva.
> > [!important] Esto es crucial porque no todos los errores son iguales en una aplicación práctica.

> [!NOTE] Ayudan a organizar el esfuerzo del equipo de ML
> Generalmente la meta del equipo de ML será mejorar esa métrica en el conjunto de desarrollo (*dev set*).
> 

> [!NOTE] Son útiles para cuantificar "brechas"
> - Rendimiento deseado VS línea base (*baseline*) para estimar el esfuerzo.
> - Rendimiento deseado VS Rendimiento actual.
> Permiten medir el progreso a lo largo del tiempo

> [!NOTE] Son valiosas para tareas de bajo nivel y para la **depuración**
> Por ejemplo, para diagnosticar problemas de sesgo (*bias*) frente a varianza (*variance*).

En resumen, podemos afirmar que:

> [!important] El **objetivo de entrenamiento** debería ser la **métrica**
> Y **si no es posible**, las **métricas** siguen siendo **útiles e importantes**.

# Clasificación binaria

La clasificación binaria se ocupa de los problemas donde la entrada $x$ se clasifica en una de dos categorías, representadas como una salida binaria:
$y = 0$ ó $y = 1$

El modelo de clasificación se denota como $\hat{y}=h(x)$.
## Tipos de modelos en la clasificación binaria

Existen dos tipos principales de modelos en la clasificación binaria:

> [!NOTE] Modelos que dan una clase categórica directamente
> Estos modelos **predicen** la **clase de salida** de forma inmediata, sin un valor de puntuación intermedio.
> > [!example] Ejemplos
> > - K-Nearest Neighbor (K-NN)
> > - Árboles de Decisión (_Decision Tree_)

> [!important] Modelos que generan una puntuación de valor real (*real valued score*)
> Estos modelos primero **calculan** un **valor numérico continuo** que se encuentra en algún **rango real** (normalmente entre 0 y 1).
> > [!example] Ejemplos de modelos basados en puntuación
> > - Máquinas de Vectores de Soporte (SVM)
> > 	La **puntuación** podría ser el **margen**.
> > - Árboles de Decisión (_Decision Tree_)
> > 	La **puntuación** podría ser la **probabilidad**.

## Vista de _Ranking_ (Modelos basados en Puntuación)

> [!NOTE] Vista de *Ranking*
> Se refiere a cómo se ordenan los ejemplos en el conjunto de datos **basándose únicamente en la puntuación** que el modelo les asignó.
> > [!example] Ordenar de mayor a menor puntuación
> > Si hacemos eso, estamos creando un ***ranking***. 

> [!NOTE] Clasificación u ordenación
> En la mayoría de las métricas de resumen (como AU-ROC), solo importa la **clasificación u ordenación (_ranking_)**, es decir, si un ejemplo positivo tiene una puntuación más alta que un ejemplo negativo, el _ranking_ es correcto.

> [!NOTE] Prevalencia en un conjunto de datos
> $$\text{Prevalencia} = \frac{\text{\# ejemplos positivos}}{\text{\# ejemplos positivos} + \text{\# ejemplos negativos}}$$

## Umbralización (_Thresholding_)

> [!NOTE] Convertir puntuación real en predicción binaria
> Para los modelos que dan una puntuación, es necesario **seleccionar un umbral (_threshold_)** para convertir esa puntuación continua (el *score*) en una clase categórica (0 o 1):
> 
> - Si $\text{Puntuación} \ge Th$, se **predice** la **clase positiva** (1)
> - Si $\text{Puntuación} \lt Th$, se **predice** la **clase negativa** (0)
> 
> > [!example] Ejemplo
> > Al elegir un umbral $Th$ (por ejemplo, $Th=0.5$), se divide el conjunto de datos clasificado en dos regiones.
> 
> > [!important] Importancia de la elección del umbral
> > La elección del umbral es crítica porque define qué tan agresivo será el clasificador al predecir la clase positiva.
> > Afecta directamente la clasificación final y, por lo tanto, a la Matriz de Confusión y a las métricas puntuales (como *Accuracy*, *Precision* y *Recall*).

# Matriz de confusión

> [!NOTE] Matriz de confusión
> Es una herramienta fundamental para visualizar el rendimiento de un algoritmo de clasificación.

> [!NOTE] ¿Cuándo se construye la matriz de confusión?
> Después de seleccionar un umbral ($Th$) y clasificar el conjunto de datos.

## Componentes detallados de la matriz de confusión

| Componentes matriz de confusión | **Etiqueta Positiva**     | **Etiqueta Negativa**     |
| ------------------------------- | ------------------------- | ------------------------- |
| **Predicción Positiva**         | *True Positive* (**TP**)  | *False Positive* (**FP**) |
| **Predicción Negativa**         | *False Negative* (**FN**) | *True Negative* (**TN**)  |
## Propiedades de la matriz de confusión

- La suma total de todos los valores ($TP + TN + FP + FN$) es fija.
- La suma de las columnas es fija.
- La calidad del modelo y el umbral $Th$ elegido deciden cómo se dividen las columnas en las filas de predicción.

> [!important] Objetivo de la matriz de la confusión
> Idealmente, buscamos que las diagonales sean "pesadas" y que las **casillas fuera de la diagonal** sean **"ligeras"**, es decir:
> -  $TP$ y $TN$ grandes
> - $FP$ y $FN$ pequeños

# Métricas puntuales

Las Métricas Puntuales son valores únicos calculados a partir de la Matriz de Confusión, y dependen, por lo tanto, del umbral ($Th$) seleccionado.

> [!NOTE] Accuracy
> Mide la proporción de clasificaciones correctas sobre el total de casos.
> $$Accuracy = \frac{TP + TN}{TP + FP + FN + TN}$$
> > [!NOTE] Es equivalente a la función de Coste 0-1 (*0-1 Loss*).

> [!NOTE] Precision
> Mide la proporción de predicciones positivas correctas (_True Positives_) de todas las predicciones positivas realizadas.
> $$Precision = \frac{TP}{TP + FP}$$

> [!NOTE] Recall (Sensibilidad)
> Mide la proporción de casos positivos que fueron correctamente identificados.
> $$Recall = \frac{TP}{TP + FN}$$

> [!NOTE] Especificidad (_Specificity_ o _Negative Recall_)
> Mide la proporción de casos negativos que fueron correctamente identificados (_True Negatives_).
> $$Specificity = \frac{TN}{TN + FP}$$

> [!NOTE] Puntuación F1 (_F1-score_)
> Es la media armónica de _Precision_ y _Recall_, ofreciendo una forma de medir el equilibrio entre ambas métricas:
> $$F_1 = \left( \frac{2}{\text{recall}^{-1} + \text{precision}^{-1}} \right) = 2 \cdot \frac{\text{precision} \cdot \text{recall}}{\text{precision} + \text{recall}}$$

## _Precision_ vs. _Recall_ y la Modificación del Umbral

> [!important] _Precision_ y _Recall_ a menudo representan un compromiso mutuo (*trade-off*)
> Por lo general, mejorar una implica sacrificar la otra, especialmente cuando se trabaja con un clasificador basado en puntuaciones.

> [!NOTE] ¿Cuál es el objetivo de un buen clasificador?
> El objetivo de un buen clasificador es **separar los ejemplos positivos y negativos en el ranking** de puntuaciones lo mejor posible.

> [!NOTE] Búsqueda de 100% *Recall*
> La estrategia trivial es **colocar a todo el mundo por encima del umbral**.
> Si predecimos que todo es positivo, $FN$ será 0, por lo que:
> $$Recall = TP / (TP + 0) = 1$$

> [!NOTE] Búsqueda de 100% *Precision*
> La estrategia trivial es **colocar a todo el mundo por debajo del umbral**, excepto quizás un positivo en la parte superior.
> En otras palabras, solo hacemos una **predicción positiva** cuando estamos **extremadamente** **seguros**, minimizando $FP$:
> $$Precision = TP / (TP + 0) = 1$$

> [!important] Estrategias de optimización
> - Para obtener un **buen _Precision_** con un **100% _Recall_**, debemos empujar el verde más bajo lo más alto posible en el _ranking_.
> - Para obtener un **buen _Recall_** con un **100% _Precision_**, debemos empujar el gris superior lo más bajo posible en el _ranking_.

## Escaneo de umbrales (Threshold Scanning)

Dado que las métricas puntuales dependen directamente del umbral, es fundamental entender cómo se comportan al cambiar este valor.

Al mover el umbral ($Th$), estamos **cambiando la partición de la matriz de confusión** y, por lo tanto, recalculando $TP$, $TN$, $FP$ y $FN$.

> [!NOTE] ¿Cuál es el **número de umbrales efectivos** a evaluar?
> **Número de ejemplos + 1.**
> Si movemos el umbral de una puntuación a otra donde no hay ejemplos, las métricas no cambiarán.

### Ejemplo de escaneo de umbrales

|**Umbral**|**TP**|**FN**|**FP**|**TN**|**Accuracy**|**Precision**|**Recall**|**Specificity**|**F1**|
|---|---|---|---|---|---|---|---|---|---|
|**1.00**|0|10|0|10|0.50|1|0|1|0|
|**0.50**|9|1|2|8|0.85|0.818|0.9|0.8|0.857|
|**0.00**|10|0|10|0|0.50|0.500|1|0|0.667|
Este escaneo nos permite ver que, a medida que disminuye el umbral (nos volvemos más propensos a predecir positivo):

- _Recall_ generalmente aumenta (pasamos de 0 a 1).
	
- _Specificity_ generalmente disminuye (pasamos de 1 a 0).
	
- _Accuracy_, _Precision_ y _F1_ varían y típicamente tienen un punto óptimo en algún lugar intermedio.

# Métricas resumen

> [!NOTE] ¿Para qué sirven las métricas resumen?
> Estas métricas son fundamentales porque evalúan la capacidad de **ranking** del modelo en todo el rango de posibles umbrales, y no solo en un punto fijo, como hacen las métricas puntuales.
> > [!example] Ejemplos de métricas resumen:
> > - AU-ROC
> > - AU-PRC
> > - Log-loss

## Curva ROC (*Receiver Operating Characteristic*)

> [!important] ¿Cómo se construye la curva ROC?
> La Curva ROC se construye trazando el rendimiento del clasificador a medida que se varía el umbral de decisión, desde 1.0 hasta 0.0:
> - Eje Y: *Recall*
> 	$$\text{Sensibilidad} = \frac{TP}{TP + FN}$$
> - Eje X: 1 - Especificidad (*Specificity*).
> 	$$\text{Especificidad} = \frac{TN}{TN + FP}$$
> > [!important] Por qué 1 - Especificidad
> > El valor de 1 - Especificidad (o Tasa de Falsos Positivos, _False Positive Rate_) representa la proporción de negativos reales que fueron clasificados incorrectamente como positivos.

> [!NOTE] ¿Cómo se interpreta AU-ROC?
> El **AU-ROC** es el área que queda bajo esta curva y su valor tiene varias interpretaciones clave:
> > [!NOTE] Valor global de rendimiento
> > Un valor de AU-ROC de 1.0 representa un clasificado perfecto, mientras que una valor de 0.5 representa un rendimiento aleatorio (*Random Guessing*).
> 
> > [!NOTE] Probabilidad de Ranking
> > El AU-ROC se interpreta como la **probabilidad de que un ejemplo positivo elegido al azar sea clasificado (puntuado) más alto que un ejemplo negativo elegido al azar**.
> 
> > [!NOTE] AU-ROC es una métrica **agnóstica a la prevalencia**
> > Esto significa que su valor no se ve afectado por la proporción de ejemplos positivos y negativos en el conjunto de datos, lo cual lo convierte en una excelente medida de la calidad intrínseca del _ranking_ del modelo.

# Evaluación de modelos

Si queremos obtener una estimación precisa del rendimiento de un clasificador, es esencial dividir el conjunto de datos disponibles, para lo cual podemos utilizar varias técnicas.

## Holdout (Conjunto de retención)

La técnica de Holdout consiste en dividir el conjunto de datos original en dos o tres subconjuntos disjuntos (sin ejemplos compartidos):

- **Conjunto de Entrenamiento (_Training Set_)**: Se utiliza para entrenar el modelo (ajustar los parámetros).
    
- **Conjunto de Validación (_Validation Set_ o _Dev Set_)**: Se utiliza para ajustar los hiperparámetros (parámetros que no se aprenden en el entrenamiento, como el _learning rate_ o el número de capas de una red neuronal) y para seleccionar el mejor modelo.
    
- **Conjunto de Prueba (_Test Set_)**: Se utiliza **solo una vez** al final del proceso para obtener la estimación final y no sesgada del rendimiento del modelo.

**Desventaja Principal:**

- Al dividir los datos, se reduce la cantidad de información disponible para el entrenamiento, lo que puede ser un problema si el conjunto de datos original es pequeño.

## Cross-validation (_Validación Cruzada_)

La _Cross-validation_ es una técnica que permite utilizar todos los datos tanto para entrenamiento como para prueba, generando una estimación del rendimiento mucho más robusta y fiable que el Holdout simple.

La forma más común es la **Validación Cruzada K-Fold**:

1. **División en K-Folds:** El conjunto de datos se divide en $K$ subconjuntos o "folds" de igual tamaño. (Por ejemplo, si K=10, el conjunto se divide en 10 partes).
    
2. **Iteración:** El proceso se repite $K$ veces (o $K$ iteraciones).
    
3. **Entrenamiento y Evaluación:**
    
    - En cada iteración $k$, el fold $k$ se utiliza como el **Conjunto de Prueba**.
        
    - Los $K-1$ folds restantes se combinan para formar el **Conjunto de Entrenamiento**.
        
4. **Estimación Final:** El rendimiento final del modelo es la **media** de las $K$ evaluaciones de rendimiento obtenidas en cada iteración.

**Ventajas de la _Cross-validation_**:

- Se aprovechan mejor los datos, ya que cada ejemplo se usa para entrenar $K-1$ veces y para probar exactamente una vez.
    
- La estimación de la métrica de rendimiento es menos sensible a cómo se haya dividido inicialmente el conjunto de datos.

## Leave-One-Out Cross-validation (LOO)

_Leave-One-Out_ es una forma particular y extrema de _Cross-validation_:

- **Número de _Folds_**: El número de _folds_ ($K$) se establece igual al número de instancias de entrenamiento ($n$).
    
- **Proceso:** Para $n$ instancias de entrenamiento, se construye el clasificador $n$ veces. En cada iteración, solo se deja **una** instancia para el conjunto de prueba, y las $n-1$ restantes se usan para entrenar.
    
- **Ventaja:** Hace el mejor uso posible de los datos para entrenamiento.
    

**Desventajas de LOO:**

- **Muy costoso computacionalmente:**
	Requiere entrenar el modelo $n$ veces, lo que es inmanejable para grandes conjuntos de datos (excepto para modelos muy simples como K-NN).
- **No es posible hacer una versión estratificada:** Esto es una desventaja crítica. 
	Si un conjunto de datos tiene, por ejemplo, 50 ejemplos de la clase A y 50 de la clase B (50% de error esperado para un clasificador _Zero-R_ o aleatorio), la estimación LOO puede devolver un error del 100% debido a la falta de estratificación.