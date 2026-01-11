# Glosario de conceptos de Aprendizaje Automático

## Evaluación de lo aprendido
### Fundamentos de la evaluación y métricas

- **Objetivo de entrenamiento (Función de coste)**:
	Medida que se utiliza durante el aprendizaje para guiar al modelo.
	No siempre coincide exactamente con los objetivos finales del mundo real.
    
- **Métricas**:
	Herramientas cuantitativas que permiten capturar un objetivo de negocio y convertirlo en una meta medible.
	Ayudan a organizar el esfuerzo del equipo de ML y a medir el progreso en el conjunto de desarrollo (*dev set*).
    
- **Brecha (Gap) de rendimiento**:
	Diferencia cuantificable que existe entre:
	 - El rendimiento actual del modelo.
	 - Nivel de referencia (*baseline*) o el rendimiento deseado.
    
- **Sesgo (Bias) vs. Varianza (Variance)**:
	Conceptos clave para el diagnóstico y depuración de modelos.
	Ayudan a identificar si el modelo está fallando por:
	- Falta de ajuste (sesgo).
	- Exceso de ajuste a los datos de entrenamiento (varianza).
    
- **Error de entrenamiento (Training error)**:
	Tasa de error obtenida utilizando los mismos datos con los que se entrenó el modelo.
    
- **Optimismo del error de entrenamiento**:
	Fenómeno por el cual el error de entrenamiento suele ser mucho más bajo que el error real, lo que lo convierte en un mal indicador del rendimiento del modelo ante datos futuros.
    
- **Capacidad predictiva**:
	Medida que indica qué tan bien se comportará el modelo al enfrentarse a datos nuevos que no ha visto previamente.
### Clasificadores binarios y tipos de modelos

- **Entrada ($x$)**:
	Conjunto de datos o características que se introducen en el modelo para realizar una predicción.
    
- **Salida binaria ($y$)**:
	El resultado real u objetivo que queremos predecir, que en clasificación binaria toma valores discretos como $0$ o $1$.
    
- **Modelo de clasificación ($\hat{y}=h(x)$)**:
	Función o hipótesis aprendida que intenta predecir el valor de la salida para una entrada.
    
- **Modelos de salida categórica directa**:
	Clasificadores que asignan directamente una etiqueta de clase a la entrada.

> [!example] Ejemplos
> - Algoritmo de K-vecinos más cercanos (K-NN).
> - Árboles de Decisión.

- **Modelos de salida de valor real (Score-based)**:
	Clasificadores que, en lugar de una clase, devuelven una puntuación numérica (score).

> [!example] Ejemplos
> - Regresión Logística.
> - Máquinas de Vector de Soporte (SVM).
    
- **Puntuación (Score)**:
	Valor numérico generado por un modelo que indica la confianza o probabilidad de que una instancia pertenezca a una clase.
	Puede ser una probabilidad (en Regresión Logística) o un margen (en SVM).
    
- **Umbral (*Threshold*)**:
	Valor crítico que se selecciona para convertir la puntuación continua del modelo en una decisión categórica (clase $0$ o $1$).

- ***Thresholding***:
	El proceso de aplicar un umbral a las puntuaciones de un modelo para obtener predicciones de clase finales.
    
- **Visión de Ranking (Rank view)**:
	Perspectiva de evaluación de clasificadores que se centra en la capacidad del modelo para ordenar las instancias según su puntuación, más que en la predicción de una clase concreta.
### Metodologías de partición de datos

- **Conjunto de entrenamiento (Training set)**:
	Parte de los datos utilizada para que el modelo aprenda y construya su estructura básica.
    
- **Conjunto de test (Test set)**:
	Conjunto de instancias independientes que no han participado en absoluto en el entrenamiento del modelo.
	Se utiliza para estimar de forma realista cómo funcionará el modelo con datos nuevos.
    
- **Conjunto de validación (Validation data)**:
	Un tercer conjunto de datos necesario cuando el aprendizaje tiene dos etapas.
	Se utiliza específicamente para optimizar los parámetros del modelo sin contaminar el conjunto de test.
    
- **Método Holdout**:
	Metodología de partición de datos sencilla que consiste en dividir los datos originales en dos bloques:
	- entrenamiento.
	- test.
	Generalmente se reserva un tercio para test y el resto para entrenamiento.
    
- **Estratificación (Stratification)**:
	Metodología de partición de datos avanzada que asegura que cada clase esté representada en proporciones aproximadamente iguales tanto en el conjunto de entrenamiento como en el de test.
	Es crucial para evitar que una clase falte en alguna de las particiones.
    
- **Holdout repetido (Repeated holdout)**:
	Metodología de partición de datos que consiste en repetir el proceso de holdout varias veces con diferentes submuestras aleatorias y promediar los errores obtenidos para obtener una estimación más fiable.
    
- **Validación Cruzada (Cross Validation)**:
	Metodología de partición de datos que busca evitar el solapamiento de los conjuntos de test dividiendo los datos en varios "pliegues" (folds) para que cada dato se use tanto para entrenar como para testear en diferentes iteraciones.

- **Fold (Pliegue)**:
	Cada una de las particiones en las que se divide el conjunto de datos total en una validación cruzada.
    
- **Leave-One-Out (LOO)**:
	Metodología de partición de datos y forma particular de validación cruzada donde el número de pliegues es igual al número de instancias de entrenamiento ($n$).
	En cada paso, el modelo se entrena con $n-1$ ejemplos y se prueba con el único que quedó fuera.
### Técnicas de estimación de error

- **Validación Cruzada de K-pliegues (K-fold Cross Validation)**:
	Técnica donde los datos se dividen en $K$ subconjuntos o pliegues de igual tamaño.
	El modelo se entrena $K$ veces, usando cada vez un pliegue distinto como test y los $K-1$ restantes como entrenamiento.
    
- **Estimación de error por CV**:
	Es la media aritmética de los errores obtenidos en cada una de las $K$ iteraciones de la validación cruzada.
	Proporciona una medida más robusta que un único holdout.
    
- **Leave-One-Out (LOO)**:
	Caso extremo de validación cruzada donde el número de pliegues $K$ es igual al número total de ejemplos $n$.
	Es el método que mejor aprovecha los datos, pero es computacionalmente muy costoso.
    
- **Coste computacional de LOO**:
	Desventaja principal de este método, ya que requiere entrenar el modelo $n$ veces (una por cada instancia).
    
- **Inestabilidad de LOO con Zero R**:
	Concepto que explica que, en datasets equilibrados (ej. 50/50), el método LOO puede dar un error del 100% mientras que el error esperado real sería del 50%, debido a que al sacar un ejemplo de una clase, la mayoría "gana" siempre por la otra.
    
- **No estratificación en LOO**:
	A diferencia de otras técnicas, en Leave-One-Out no es posible realizar una versión estratificada, ya que el conjunto de test solo tiene un elemento.
### Métricas de rendimiento puntuales

- **Matriz de Confusión**:
	Es una tabla que permite visualizar el desempeño de un algoritmo de aprendizaje supervisado.
	En ella se comparan las predicciones del modelo con los valores reales, permitiendo identificar qué clases están siendo confundidas entre sí.
    
- **Verdaderos Positivos (TP - True Positives)**:
	Casos en los que el modelo predijo la clase positiva y la instancia realmente pertenecía a la clase positiva.
    
- **Verdaderos Negativos (TN - True Negatives)**:
	Casos en los que el modelo predijo la clase negativa y la instancia realmente pertenecía a la clase negativa.
    
- **Falsos Positivos (FP - False Positives)**:
	Casos en los que el modelo predijo la clase positiva y la instancia realmente pertenecía a la clase negativa.
	También conocido como "Error de Tipo I".
    
- **Falsos Negativos (FN - False Negatives)**:
	Casos en los que el modelo predijo la clase negativa y la instancia realmente pertenecía a la clase positiva.
	También conocido como "Error de Tipo I".
    
- **Accuracy (Exactitud)**:
	Representa la proporción total de predicciones correctas (tanto positivas como negativas) sobre el total de casos.
	$$\text{Accuracy} = \frac{TP + TN}{TP + FP + FN + TN}$$
- **Precision (Precisión)**:
	Representa la proporción de instancias que realmente son positivas entre todas las que el modelo clasificó como tales.
	Mide la calidad de las predicciones positivas.
	$$\text{Precision} = \frac{TP}{TP + FP}$$
- **Recall o Sensibilidad (Sensitivity)**:
	Representa la proporción de casos positivos reales que fueron identificados correctamente por el modelo.
	Mide la capacidad del modelo para encontrar todos los casos positivos.
    $$\text{Recall} = \frac{TP}{TP + FN}$$
- **Especificidad (Specificity)**:
	Representa la proporción de casos negativos reales que fueron clasificados como negativos.
	Mide la capacidad del modelo para identificar correctamente los casos negativos.
	$$\text{Specificity} = \frac{TN}{TN + FP}$$
- **F-score (o F1-score)**:
	Es una métrica de rendimiento puntual que combina la Precisión y el Recall en un solo valor (generalmente mediante su media armónica) para proporcionar un balance entre ambas que sirve para evaluar el rendimiento global del modelo.
### Métricas de resumen y evaluación de puntuaciones

- **Métricas de Resumen (Summary Metrics)**:
	Conjunto de medidas que evalúan el rendimiento global de un modelo que devuelve puntuaciones reales (scores) en lugar de etiquetas fijas, considerando todos los umbrales posibles.

- **Curva ROC (Receiver Operating Characteristic)**:
	Gráfico que representa la relación entre la Tasa de Verdaderos Positivos (Sensibilidad) y la Tasa de Falsos Positivos (1 - Especificidad) para todos los umbrales de clasificación posibles.

- **AU-ROC (Area Under the ROC Curve)**:
	Es el área bajo la curva ROC.
	Proporciona un valor entre 0 y 1 que indica la probabilidad de que el modelo clasifique una instancia positiva elegida al azar por encima de una negativa elegida al azar.
	Es una medida de la capacidad de **ranking** del modelo.

- **Curva PRC (Precision-Recall Curve)**:
	Gráfico que representa la relación entre la Precisión y el Recall para diferentes umbrales.
	Es especialmente útil cuando las clases están muy desbalanceadas (cuando hay muy pocos casos positivos).

- **AU-PRC (Area Under the Precision-Recall Curve)**:
	El área bajo la curva Precision-Recall.
	A diferencia del AU-ROC, se centra más en el rendimiento del modelo respecto a la clase positiva (la clase de interés).

- **Log-loss (Pérdida Logarítmica)**:
	Métrica que evalúa la calidad de las probabilidades predichas por el modelo.
	Penaliza fuertemente las predicciones que son seguras pero incorrectas (por ejemplo, predecir un 90% de probabilidad para una clase que resulta ser la incorrecta).

- **Calibración**:
	Propiedad de un modelo de puntuación real en la que las probabilidades predichas reflejan la frecuencia real de los eventos en la naturaleza (por ejemplo, si el modelo dice 0.7, el evento debería ocurrir el 70% de las veces).

- **Softmax**: (Relacionado con Log-loss)
	Función utilizada frecuentemente para convertir las salidas de un modelo en una distribución de probabilidad que suma 1.
## Regresión Lineal y Descenso del Gradiente

### Fundamentos y Formulación de la Regresión Lineal

- **Aprendizaje Supervisado (Supervised Learning):**
	Tipo de aprendizaje automático que se caracteriza por disponer de un conjunto de datos de entrenamiento donde, para cada entrada, conocemos de antemano la respuesta correcta o etiqueta.
	Es el contexto en el que se encuadra la regresión lineal. 

- **Variable de Entrada / Características (Features):**
	Denotadas habitualmente como $x^{(i)}$.
	Son las variables independientes o atributos que utilizamos para realizar una predicción.

> [!example] Ejemplos
> - Metros cuadrados de una casa.
> - Número de habitaciones.

- **Variable de Salida / "Target" (Objetivo):**
	Denotada habitualmente como $y^{(i)}$.
	Es la variable dependiente que el modelo intenta predecir.

> [!example] Ejemplos
> - El precio de la vivienda.

- **Ejemplo de Entrenamiento (Training Example):**
	Es un par $(x^{(i)}, y^{(i)})$ que representa una única observación dentro de nuestro conjunto de datos.
    
- **Conjunto de Entrenamiento (Training Set):**
	La lista de $n$ ejemplos de entrenamiento $\{(x^{(i)}, y^{(i)}); i = 1, \dots, n\}$ que el algoritmo utiliza para aprender.
    
- Hipótesis ($h$ o $h_\theta$):
	Es la función que el algoritmo de aprendizaje devuelve. Toma una entrada $x$ y trata de predecir el valor de $y$ correspondiente. En regresión lineal simple, se expresa como:
    $$h_\theta(x) = \theta_0 + \theta_1 x_1 + \theta_2 x_2 + \dots$$
- **Término de Intercepción (Intercept Term):** Es el parámetro $\theta_0$. Representa el valor de la predicción cuando todas las características de entrada son cero.
    
- **Variable Auxiliar $x_0$:** Convención de notación donde se define $x_0 = 1$ para todos los ejemplos. Esto permite escribir la función de hipótesis de forma compacta como un sumatorio o un producto escalar de vectores.
    
- Notación Vectorial: Forma simplificada de expresar la hipótesis utilizando el producto traspuesto de los vectores de parámetros y características:
	$$h(x) = \sum_{i=0}^{d} \theta_i x_i = \theta^T x$$
- **Espacio de Hipótesis:** El conjunto de todas las funciones posibles que se pueden formar variando los parámetros $\theta$. En este caso, estamos limitados a funciones que sean combinaciones lineales de las entradas.
### Función de Coste (Mínimos Cuadrados)

- **Función de Coste (Cost Function):** Denotada como $J(\theta)$. Es una función matemática que mide la discrepancia entre las predicciones del modelo ($h_\theta(x)$) y los valores reales ($y$) de todo el conjunto de entrenamiento. Nuestro objetivo es encontrar los parámetros $\theta$ que **minimicen** esta función.
    
- **Mínimos Cuadrados Ordinarios (Ordinary Least Squares - OLS):** Es el método que define la función de coste como la suma de los cuadrados de las diferencias entre las predicciones y los valores reales.
    
- **Error Cuadrático (Squared Error):** Es el término $(h_\theta(x^{(i)}) - y^{(i)})^2$. Se eleva al cuadrado por dos razones principales: para que todos los errores sean positivos y para penalizar con mayor fuerza las predicciones que están muy alejadas del valor real.
    
- Fórmula de la Función de Coste $J(\theta)$: Según el material de Stanford, se define formalmente como:
	$$J(\theta) = \frac{1}{2} \sum_{i=1}^{n} (h_\theta(x^{(i)}) - y^{(i)})^2$$
    (Nota: El factor $1/2$ se incluye por conveniencia matemática para que se cancele al derivar durante el proceso de optimización).
    
- **Superficie de Coste:** Representación geométrica de $J(\theta)$ en función de los parámetros. Si tenemos dos parámetros ($\theta_0$ y $\theta_1$), esta superficie suele tener forma de "cuenco" o parábola (en modelos lineales simples).
    
- **Mínimo Global:** El punto más bajo de la función de coste. Los valores de $\theta$ en este punto representan la "mejor" línea posible que se ajusta a los datos según el criterio de mínimos cuadrados.
    
- **Contornos de la Función de Coste (Contour Plots):** Una forma de visualizar $J(\theta)$ mediante elipses. Cada elipse representa puntos donde el valor de la función de coste es el mismo. El centro de las elipses corresponde al valor mínimo de $J$.
### Algoritmos de Optimización (Descenso del Gradiente)

- **Descenso del Gradiente (Gradient Descent):** Algoritmo de optimización iterativo utilizado para encontrar el mínimo de la función de coste $J(\theta)$. Funciona empezando con unos valores iniciales de $\theta$ y dando pasos en la dirección de máxima pendiente negativa.
    
- Regla de Actualización (Update Rule): Es la fórmula matemática que cambia los parámetros en cada paso:
	$$\theta_j := \theta_j - \alpha \frac{\partial}{\partial \theta_j} J(\theta)$$
- **Ratio de Aprendizaje / Tasa de Aprendizaje (Learning Rate - $\alpha$):** Un parámetro (hiperparámetro) que determina el tamaño de los pasos que damos hacia el mínimo.
    
    - Si $\alpha$ es muy **pequeño**, el algoritmo será muy lento.
        
    - Si $\alpha$ es muy **grande**, el algoritmo puede oscilar o incluso divergir (alejarse del mínimo).
        
- **Derivada Parcial ($\frac{\partial}{\partial \theta_j} J(\theta)$):** Término que indica la dirección y la magnitud de la pendiente de la función de coste respecto a un parámetro específico. Nos dice hacia dónde "bajar".
    
- **Actualización Simultánea (Simultaneous Update):** Técnica crucial en la implementación donde todos los $\theta_j$ se calculan primero usando los valores antiguos y luego se actualizan todos a la vez. No se debe actualizar uno y usar ese nuevo valor para calcular el siguiente en la misma iteración.
    
- LMS (Least Mean Squares) / Regla de Widrow-Hoff: Es la regla de actualización específica para la regresión lineal derivada de la función de coste de mínimos cuadrados:
    $$\theta_j := \theta_j + \alpha (y^{(i)} - h_\theta(x^{(i)})) x_j^{(i)}$$
    
- **Batch Gradient Descent (Descenso del Gradiente por Lotes):** Versión del algoritmo que utiliza **todo el conjunto de entrenamiento** en cada paso de actualización. Es preciso pero puede ser lento si el dataset es gigantesco.
    
- **Stochastic Gradient Descent (Descenso del Gradiente Estocástico - SGD):** Versión que actualiza los parámetros basándose en **un solo ejemplo de entrenamiento** cada vez. Es mucho más rápido y permite trabajar con datasets que no caben en memoria, aunque su trayectoria hacia el mínimo es más "errática".
    
- **Convergencia:** El estado en el que el algoritmo ha llegado al mínimo (o está lo suficientemente cerca) y los parámetros $\theta$ dejan de cambiar significativamente entre iteraciones.
### Interpretación Probabilística y Casos Particulares

- **Término de Error ($\epsilon$):** Variable que captura todo lo que el modelo no puede explicar (características no incluidas, ruido aleatorio, etc.). Se define como $y^{(i)} = \theta^T x^{(i)} + \epsilon^{(i)}$.
    
- **Distribución Gaussiana (Normal):** Suposición fundamental en la que se asume que los errores $\epsilon^{(i)}$ son variables aleatorias independientes e idénticamente distribuidas (IID) que siguen una campana de Gauss con media 0 y varianza $\sigma^2$.
    
- **Verosimilitud (Likelihood - $L(\theta)$):** Función que mide qué tan probable es observar los datos de entrenamiento para unos valores específicos de los parámetros $\theta$. A diferencia de la probabilidad (que predice datos dado $\theta$), la verosimilitud busca el $\theta$ dado los datos.
    
- **Log-Verosimilitud (Log-Likelihood - $\ell(\theta)$):** Es el logaritmo natural de la función de verosimilitud. Se utiliza porque es más fácil de derivar matemáticamente y permite transformar productos de probabilidades en sumas sin cambiar el punto donde se encuentra el máximo.
    
- **Estimación de Máxima Verosimilitud (Maximum Likelihood Estimation - MLE):** Principio estadístico que establece que debemos elegir los parámetros $\theta$ que maximicen la probabilidad de haber observado los datos que realmente tenemos. En el caso de errores Gaussianos, maximizar la verosimilitud es equivalente a minimizar la suma de los errores al cuadrado.
    
- **Underfitting (Subajuste):** Problema que ocurre cuando el modelo es demasiado sencillo para capturar la estructura de los datos (por ejemplo, intentar ajustar una recta a datos que claramente siguen una curva). El modelo tiene un "sesgo" (bias) alto.
    
- **Overfitting (Sobreajuste):** Problema que ocurre cuando el modelo es demasiado complejo (por ejemplo, un polinomio de grado muy alto) y se ajusta demasiado a los datos específicos de entrenamiento, incluyendo el ruido. Esto hace que el modelo no generalice bien ante datos nuevos.
    
- **Generalización:** La capacidad de un modelo de aprendizaje automático para realizar predicciones precisas sobre datos nuevos que no fueron utilizados durante el entrenamiento.
## Regresión Logística
### Fundamentos de la Clasificación y el Modelo Logístico

- **Clasificación Binaria:** Tipo de problema de aprendizaje supervisado donde la variable de salida $y$ solo puede tomar dos valores discretos (normalmente 0 y 1).
    
- **Etiqueta (Label):** Es el valor $y^{(i)}$ correspondiente a un ejemplo de entrenamiento. En clasificación binaria, identifica a qué clase pertenece el dato.
    
- **Clase Positiva vs. Negativa:** Por convención, al valor $1$ se le denomina clase positiva (frecuentemente denotada con el símbolo "+") y al valor $0$ clase negativa (denotada con "-"). Un ejemplo típico es: 1 para "spam" y 0 para "correo legítimo".
    
- **Hipótesis ($h_\theta(x)$):** En regresión logística, la hipótesis representa la probabilidad estimada de que, dada una entrada $x$, la salida sea la clase positiva ($y=1$). Se expresa como $h_\theta(x) = P(y=1 | x; \theta)$.
    
- **Función Logística (o Sigmoide):** Función denotada como $g(z) = \frac{1}{1 + e^{-z}}$. Se utiliza para "aplastar" cualquier valor real en el intervalo $(0, 1)$, lo cual es ideal para representar probabilidades.
    

	![Imagen de Logistic function sigmoid curve](https://encrypted-tbn2.gstatic.com/licensed-image?q=tbn:ANd9GcSE2Rke8GsNHC60xdZWGaLPcg_3ZKubLi_GsR8les52R3DjSao7IUsekHUIpDj8aRe1PyEwWY-NW4ba2V82GE6Dgqv9-JbtvJEiUPqq0l0ABCMM2ho)

- **Argumento de la función ($z$):** En nuestro modelo, $z = \theta^T x$. Es el producto escalar entre el vector de parámetros y el vector de características de la entrada.
    
- **Propiedades de la Sigmoide:**
    
    - Cuando $z \to \infty$, $g(z) \to 1$.
        
    - Cuando $z \to -\infty$, $g(z) \to 0$.
        
    - $g(0) = 0.5$.
        
    - Su derivada tiene una forma muy conveniente para el cálculo: $g'(z) = g(z)(1 - g(z))$.
        
- **Regresión Lineal vs. Logística (Limitación):** Los textos destacan que usar regresión lineal para clasificación es inadecuado porque la salida de una función lineal puede ser mucho mayor que 1 o menor que 0, lo cual no tiene sentido cuando buscamos clasificar etiquetas discretas.
### Estimación Probabilística y Máxima Verosimilitud

- **Suposición Probabilística:** Es la base del modelo donde asumimos que las etiquetas siguen una distribución de Bernoulli. Se define como:
    
    - $P(y=1 | x; \theta) = h_\theta(x)$
        
    - $P(y=0 | x; \theta) = 1 - h_\theta(x)$
        
- **Forma Compacta de la Probabilidad:** Una manera matemática de escribir las dos ecuaciones anteriores en una sola expresión: $p(y|x; \theta) = (h_\theta(x))^y (1 - h_\theta(x))^{1-y}$. Si $y=1$ se anula el segundo término, y si $y=0$ se anula el primero.
    
- Función de Verosimilitud ($L(\theta)$): Función que mide qué tan probable es observar el conjunto de etiquetas de nuestro entrenamiento dado un conjunto de parámetros $\theta$. Se define (asumiendo que los ejemplos son independientes) como el producto de las probabilidades de cada ejemplo:
    
    $L(\theta) = \prod_{i=1}^{n} p(y^{(i)} | x^{(i)}; \theta)$
    
- Log-verosimilitud ($l(\theta)$): Es el logaritmo natural de la función de verosimilitud. Se utiliza porque es más fácil de maximizar (convierte productos en sumas) y evita problemas de precisión numérica. Su fórmula es:
    
    $l(\theta) = \sum_{i=1}^{n} y^{(i)} \log h(x^{(i)}) + (1 - y^{(i)}) \log (1 - h(x^{(i)}))$
    
- **Máxima Verosimilitud (Maximum Likelihood Estimation - MLE):** Principio estadístico que consiste en elegir los parámetros $\theta$ que maximicen la probabilidad de haber observado los datos que realmente tenemos en el conjunto de entrenamiento. En lugar de minimizar el error (como en regresión lineal), aquí buscamos "maximizar el acuerdo" del modelo con los datos.
    
- **Independencia (IID):** Suposición necesaria para que la verosimilitud total sea el producto de las probabilidades individuales. Consideramos que cada ejemplo de entrenamiento ha sido generado de forma independiente y siguiendo la misma distribución.
### Aprendizaje del Modelo (Optimización)

- **Ascenso del Gradiente (Gradient Ascent):** Algoritmo de optimización que busca el máximo de una función. A diferencia del descenso del gradiente (que busca mínimos), aquí sumamos el gradiente a los parámetros: $\theta := \theta + \alpha \nabla_\theta l(\theta)$. Lo usamos porque queremos **maximizar** la verosimilitud.
    
- **Derivada de la Sigmoide:** Propiedad matemática clave que facilita los cálculos. Se define como $g'(z) = g(z)(1 - g(z))$. Esta forma compacta permite que la regla de actualización final sea muy elegante.
    
- **Vector de Parámetros ($\theta$):** Conjunto de pesos que el algoritmo aprende. Cada $\theta_j$ determina la influencia de una característica $x_j$ en la probabilidad final.
    
- **Tasa de Aprendizaje ($\alpha$):** Parámetro que controla el tamaño del paso que damos en cada iteración del ascenso del gradiente. Si es muy grande, podemos sobrepasar el máximo; si es muy pequeño, el aprendizaje será muy lento.
    
- Regla de Actualización (Update Rule): La fórmula final para ajustar los pesos después de derivar la log-verosimilitud:
    $$\theta_j := \theta_j + \alpha \sum_{i=1}^{n} (y^{(i)} - h_\theta(x^{(i)})) x_j^{(i)}$$
    
- **Error de Predicción ($y - h_\theta(x)$):** En la regla de actualización, es la diferencia entre el valor real y la probabilidad predicha. Si la predicción es perfecta, el ajuste es cero.
    
- **Similitud con LMS (Least Mean Squares):** Un concepto muy preguntable en examen. Aunque la regresión logística y la regresión lineal son modelos distintos (uno usa una sigmoide y el otro no), la regla de actualización del gradiente tiene **la misma forma estética**, lo cual es un resultado notable del diseño de estos algoritmos.
    
- **Algoritmo Batch (por lotes):** Cuando la actualización de los parámetros se realiza sumando el error de **todos** los ejemplos del conjunto de entrenamiento antes de dar un paso.
### Reglas de Decisión y Clasificación Multi-clase

- **Regla de Separación (Separation Rule):** Es el criterio que aplicamos para asignar una clase definitiva a una observación. La regla estándar es:
    
    - Predecimos $y=1$ si $h_\theta(x) \geq 0.5$.
        
    - Predecimos $y=0$ si $h_\theta(x) < 0.5$.
        
- **Frontera de Decisión (Decision Boundary):** Es la línea (o hiperplano en dimensiones superiores) que separa las regiones donde el modelo predice una clase de la otra. Matemáticamente, corresponde a los puntos donde $\theta^T x = 0$, ya que $g(0) = 0.5$.
    
- **Clasificación Multi-clase:** Extensión del problema donde la variable $y$ puede tomar $k$ valores discretos (por ejemplo, clasificar tipos de plantas o dígitos del 0 al 9).
    
- **Distribución Multinomial:** Es la generalización de la distribución de Bernoulli para cuando hay más de dos resultados posibles. En este contexto, cada una de las $k$ salidas tiene una probabilidad asociada $\phi_i$.
    
- Función Softmax: Es la generalización de la función logística para problemas multi-clase. Calcula la probabilidad de cada clase $i$ asegurándose de que la suma de todas las probabilidades sea 1. Se define como:
    $$P(y=i | x; \theta) = \frac{e^{\theta_i^T x}}{\sum_{j=1}^{k} e^{\theta_j^T x}}$$
    
- **Vector de Parámetros Multi-clase:** A diferencia de la binaria, en multi-clase (Softmax) tenemos un vector de parámetros $\theta_i$ diferente para cada una de las $k$ clases.
    
- **Función de Pérdida de Entropía Cruzada (Cross-Entropy Loss):** Es la función que se minimiza en modelos multi-clase (equivalente a maximizar la verosimilitud). Mide la "distancia" entre la distribución de probabilidad real (la etiqueta) y la predicha por el Softmax.
    
- **Indicador Identidad ($1\{condition\}$):** Notación matemática utilizada en las fórmulas multi-clase que vale 1 si la condición es verdadera y 0 si es falsa. Por ejemplo, $1\{y=i\}$ sirve para seleccionar solo el término de la clase correcta en la suma de verosimilitud.
## Deep Learning
### Fundamentos y Conceptos Iniciales
#### Conceptos Generales de Representación

- **Deep Learning (Aprendizaje Profundo):** Tipo de aprendizaje automático que busca resolver la dificultad de extraer características mediante el aprendizaje de representaciones que se expresan en términos de otras representaciones más simples y abstractas.
    
- **Representación de Datos:** Forma en la que se codifica la información. El éxito de un algoritmo de aprendizaje depende críticamente de cómo se representen los datos (por ejemplo, el paso de coordenadas cartesianas a polares puede simplificar drásticamente un problema de clasificación).
    
- **Jerarquía de Conceptos:** Estructura que permite a la computadora aprender conceptos complejos (como la imagen de una persona) mediante la combinación de conceptos más simples (bordes, esquinas, contornos).
#### Arquitecturas y Flujo de Información

- **Capas Ocultas (Hidden Layers):** Capas de una red neuronal situadas entre la entrada y la salida. Su función es extraer características de niveles de abstracción cada vez más altos que no están presentes directamente en los datos de entrada.
    
- **Deep Feedforward Networks (Redes de Alimentación hacia Adelante):** También llamadas Multilayer Perceptrons (MLP). Son modelos donde la información fluye solo hacia adelante, desde la entrada $x$, a través de las capas intermedias, hasta la salida $y$. No existen retroalimentaciones (ciclos).
    
- **Modelo Quintilla (Housing Price Example):** Ejemplo clásico donde variables de entrada (tamaño, nº habitaciones, código postal) se combinan en nodos intermedios para representar conceptos abstractos (calidad de la zona, tamaño familiar) antes de predecir el precio final.
#### Componentes de la Red Neuronal

- **Unidad de Cómputo (Neurona):** Elemento básico que recibe entradas, aplica una transformación y produce una salida. Se inspira vagamente en el funcionamiento de las neuronas biológicas.
    
- **Parámetros ($\theta$):** Conjunto de valores internos de la red que el algoritmo debe aprender. Incluyen:
    
    - **Pesos ($w$):** Coeficientes que determinan la importancia de una entrada sobre una unidad.
        
    - **Bias ($b$):** Término de sesgo que permite desplazar la función de activación.
        
- **Función de Activación:** Función no lineal aplicada a la salida de una unidad para que la red pueda aprender relaciones complejas que no sean simples combinaciones lineales de la entrada.
#### El Proceso de Aprendizaje

- **Aproximación de Funciones:** El objetivo principal del Deep Learning es aproximar una función desconocida $f^*(x)$. La red define un mapeo $y = f(x; \theta)$ y aprende los parámetros $\theta$ que mejor aproximan esa función.
    
- **Optimization (Optimización):** El proceso de encontrar los parámetros $\theta$ que minimizan una función de coste. A diferencia de la optimización pura, en Machine Learning nos interesa que el rendimiento mejore en datos nuevos (generalización), no solo en el entrenamiento.
    
- **Función de Coste / Pérdida (Loss Function):** Medida que cuantifica la diferencia entre la salida predicha por la red y el valor real esperado.
### No Linealidad y Arquitectura

#### Funciones de Activación

- **Función de Activación:** Transformación no lineal que se aplica a la suma ponderada de las entradas de una neurona. Sin ella, una red neuronal de muchas capas se comportaría como una simple regresión lineal, sin importar cuántas capas tenga.
    
- **ReLU (Rectified Linear Unit):** Es la función de activación por defecto en el Deep Learning moderno. Se define como $f(z) = \max(0, z)$.
    
    - _Ventaja:_ Es fácil de optimizar porque su gradiente es 1 para valores positivos y no se "satura" (no se aplana) tanto como las funciones clásicas.
        
- **Sigmoide ($\sigma$):** Función que "aplasta" los valores al rango $(0, 1)$. Definida como $\sigma(z) = 1 / (1 + \exp(-z))$. Era muy común antiguamente, pero tiende a saturarse, haciendo que el gradiente sea casi cero y el aprendizaje se detenga.
    
- **Tangente Hiperbólica ($\tanh$):** Función similar a la sigmoide pero con un rango de $(-1, 1)$. También sufre problemas de saturación en los extremos.
#### Capacidad y Teoremas

- **Teorema del Aproximador Universal:** Establece que una red neuronal _feedforward_ con una sola capa oculta que contenga un número suficiente de neuronas y una activación no lineal puede aproximar cualquier función continua con el nivel de precisión que se desee.
    
    - _Nota importante:_ El teorema dice que es **posible**, pero no garantiza que el algoritmo de aprendizaje sea capaz de encontrar esos parámetros o que la red no sea demasiado grande para ser práctica.
        
- **Arquitectura de la Red:** Se refiere a la estructura de la red: cuántas capas tiene (profundidad) y cuántas unidades hay en cada capa (ancho). Las redes más profundas suelen necesitar menos unidades para aproximar funciones complejas y generalizan mejor.
#### El Gradiente y la Optimización

- **Gradiente ($\nabla$):** Vector de derivadas parciales que indica la dirección de máximo crecimiento de una función. En el entrenamiento, nos movemos en la dirección opuesta al gradiente para minimizar el error.
    
- **Cost Surface (Superficie de Coste):** Representación geométrica de la función de pérdida en relación con los parámetros. En modelos lineales es una "u" perfecta (convexa), pero en Deep Learning es una superficie muy irregular con muchos valles y picos.
    
- **Dificultad de la No Linealidad:** Debido a las funciones de activación y la profundidad, la función de coste de las redes neuronales no es convexa. Esto significa que el algoritmo de optimización puede quedarse atrapado en mínimos locales o puntos de silla, aunque en la práctica esto se gestiona bien con los algoritmos actuales.
### Algoritmos de Aprendizaje y Entrenamiento

#### El Marco de Aprendizaje

- **Maximum Likelihood (Máxima Verosimilitud):** Es el principio estadístico que se utiliza para derivar algoritmos de aprendizaje. La mayoría de las redes neuronales se entrenan bajo este criterio, lo cual equivale a minimizar la discrepancia entre la distribución de datos real y la distribución predicha por el modelo.
    
- **Negative Log-Likelihood (NLL):** Es la función de coste específica que surge al aplicar Máxima Verosimilitud. Minimizar el NLL es equivalente a maximizar la probabilidad de que el modelo acierte los datos de entrenamiento.
    
- **Función de Pérdida (Loss Function / Cost Function):** Función que mide el error del modelo. El objetivo del entrenamiento es encontrar los parámetros $\theta$ que minimicen este valor.
#### Descenso de Gradiente (Gradient Descent)

- **Gradient Descent (GD):** Algoritmo de optimización que actualiza los parámetros moviéndose en la dirección opuesta al gradiente de la función de coste.
    
- **Stochastic Gradient Descent (SGD - Descenso de Gradiente Estocástico):** Variante del algoritmo que, en lugar de usar todo el conjunto de datos para cada paso (lo cual sería muy lento), utiliza un solo ejemplo o un pequeño grupo (minibatch). Es la base del entrenamiento en Deep Learning.
    
- **Learning Rate (Tasa de Aprendizaje, $\epsilon$):** Un hiperparámetro crítico que determina el tamaño del paso que damos en cada iteración hacia el mínimo. Si es muy grande, podemos saltarnos el mínimo; si es muy pequeño, el entrenamiento será eterno.
#### El Algoritmo de Back-propagation

- **Forward Propagation (Propagación hacia adelante):** Proceso de introducir los datos de entrada en la red y calcular la salida y el valor de la función de coste.
    
- **Back-propagation (Propagación hacia atrás):** Algoritmo clave que permite calcular de forma eficiente el gradiente de la función de coste con respecto a cada peso de la red. Utiliza la **regla de la cadena** del cálculo para propagar el error desde la salida hacia atrás hasta la entrada.
    
- **Regla de la Cadena (Chain Rule):** Operación matemática fundamental en la que se basa el back-propagation para calcular derivadas de funciones compuestas (como lo es una red neuronal de muchas capas).
    
- **Grafo de Computación:** Representación visual de las operaciones matemáticas de la red donde los nodos son variables y las aristas son operaciones. Se utiliza para organizar el cálculo de los gradientes durante el back-propagation.

#### Flujo de Entrenamiento

- **Iteración:** Una única actualización de los pesos de la red usando un minibatch de datos.
    
- **Epoch (Época):** Un paso completo por todo el conjunto de datos de entrenamiento.
    
- **Convergencia:** Estado en el que la función de coste ha llegado a un mínimo (local o global) y los parámetros dejan de cambiar significativamente, indicando que el modelo ha "aprendido" lo suficiente.
### Arquitecturas y Tareas Específicas
#### Tipos de Arquitecturas Principales

- **Multilayer Perceptrons (MLP):** También llamadas Redes Feedforward. Es la arquitectura básica donde las unidades se organizan en capas y la información viaja en una sola dirección. Se usan para datos tabulares generales.
    
- **Convolutional Neural Networks (CNN - Redes Convolucionales):** Redes especializadas en procesar datos con estructura de rejilla, como las **imágenes**. Utilizan la operación de convolución para extraer características espaciales automáticamente.
    
- **Recurrent Neural Networks (RNN - Redes Recurrentes):** Diseñadas para procesar **secuencias** de datos (texto, audio, series temporales). Tienen conexiones que retroalimentan la información, permitiendo "recordar" elementos anteriores de la secuencia.
#### Tareas de Salida y Funciones de Activación

- **Regresión:** Tarea que consiste en predecir un valor numérico continuo (ej. el precio de una casa).
    
    - _Unidad de salida:_ Lineal (sin activación limitante).
        
- **Clasificación Binaria:** Problema de decidir entre dos categorías (Sí/No, 0/1).
    
    - _Unidad de salida:_ **Sigmoide** (proporciona una probabilidad entre 0 y 1).
        
- **Clasificación Multiclase:** Problema de elegir una categoría entre $n$ opciones posibles (ej. clasificar un animal como "perro", "gato" o "pájaro").
    
    - _Unidad de salida:_ **Softmax**. Esta función asegura que todas las salidas sumen 1, interpretándose como una distribución de probabilidad sobre las clases.
        

#### Unidades de Salida y Distribuciones

- **Distribución de Bernoulli:** Modelo estadístico utilizado en las unidades de salida para clasificación binaria.
    
- **Distribución Multinoulli (Categorical):** Modelo estadístico utilizado para la clasificación multiclase.
    
- **Distribución Gaussiana:** Modelo que se asume típicamente para las unidades de salida en tareas de regresión cuando queremos predecir la media de una distribución.
#### Conceptos de Diseño

- **Unidades Lineales:** Unidades de salida sin función de activación no lineal. Se usan a menudo para predecir la media de una distribución condicional gaussiana.
    
- **Cross-Entropy (Entropía Cruzada):** Es la función de coste más común para tareas de clasificación. Mide la distancia entre la distribución de probabilidad real y la predicha por la red.
### Regularización

#### Concepto Fundamental

- **Regularización:** Cualquier modificación que se realiza a un algoritmo de aprendizaje con el objetivo de reducir su **error de generalización** (test), aunque no necesariamente reduzca su error de entrenamiento. Su meta es evitar el _overfitting_ (sobreajuste).
#### Penalización de Normas de Parámetros (Norm Penalties)

Consiste en añadir una penalización $\Omega(\theta)$ a la función de coste original para limitar la capacidad del modelo restringiendo el tamaño de los pesos.

- **L2 Parameter Regularization (Squared L2):** También conocida como _Weight Decay_, _Ridge Regression_ o _Tikhonov_.
    
    - _Efecto:_ Obliga a los pesos a ser pequeños (cercanos a cero) de forma suave.
        
    - _Interpretación estadística:_ Equivale a una estimación Bayesiana MAP con un _prior_ Gaussiano.
        
- **L1 Parameter Regularization:** También conocida como _LASSO_.
    
    - _Efecto:_ Induce **dispersión (sparsity)**, es decir, hace que muchos pesos sean exactamente cero.
        
    - _Uso:_ Se utiliza mucho como un mecanismo de selección de características (_feature selection_).
        
    - _Interpretación estadística:_ Equivale a una estimación Bayesiana MAP con un _prior_ de Laplace.
        
#### Técnicas de Entrenamiento

- **Early Stopping (Parada Temprana):** Probablemente la forma más común de regularización en Deep Learning. Consiste en monitorizar el error en un **conjunto de validación** y detener el entrenamiento en el momento en que este error empieza a subir, aunque el error de entrenamiento siga bajando.
    
    - _Procedimiento:_ Tras encontrar el punto óptimo, a veces se realiza un segundo entrenamiento con todos los datos (entrenamiento + validación) usando los hiperparámetros obtenidos.
        
- **Dropout:** Técnica muy potente que consiste en "apagar" aleatoriamente unidades (neuronas) de la red durante cada paso del entrenamiento.
    
    - _Funcionamiento:_ Se entrena un "ensamble" de todas las sub-redes posibles.
        
    - _Probabilidades típicas:_ Normalmente, se mantiene un nodo de entrada con probabilidad $0.8$ y un nodo oculto con probabilidad $0.5$.
        
    - _Efecto:_ Evita que las neuronas co-dependan demasiado unas de otras, forzándolas a aprender características más robustas.
        

	![Imagen de Dropout neural network before and after](https://encrypted-tbn3.gstatic.com/licensed-image?q=tbn:ANd9GcQJNGJwPOoZ6eIp2FVEPkMafvVbov6ObU8sosWF2YU2kfHNiKYfM0BxKu0i5vCHBp9JTyJLdr2WG4ALNhfhHjrsuVWNJjNpotwtKwoEYMASQE43S2o)

#### Datos y Validación

- **Conjunto de Validación (Validation Set):** Conjunto de datos distinto al de entrenamiento y test que se utiliza exclusivamente para tomar decisiones sobre los hiperparámetros (como cuándo parar el entrenamiento o qué valor de penalización usar).
    
- **Generalización:** Capacidad de la red neuronal para realizar predicciones correctas sobre datos nuevos que no ha visto nunca durante el entrenamiento.
## Detección de anomalías

### Fundamentos de las Anomalías

- **Anomalía (u Outlier):** Es una observación que se desvía significativamente del patrón general de los datos. Se considera un punto de datos generado por un proceso diferente al que genera los puntos "nominales" o normales.
    
- **Detección de Anomalías (Outlier Detection):** Es el proceso cuyo objetivo principal es identificar todas las instancias que se desvían de la normalidad.
    
- **Anomalía Puntual (One-off):** Se refiere a un único dato individual que se desvía significativamente del resto del conjunto. Un ejemplo típico es una transacción de tarjeta de crédito con un valor inusualmente alto.
    
- **Anomalía Contextual:** Es un dato que se considera anómalo solo dentro de un contexto específico, pero que sería normal en otro. Por ejemplo, registrar una temperatura de 30°C en Oviedo durante el invierno.
    
- **Anomalía Colectiva:** Ocurre cuando un grupo de datos, que individualmente podrían parecer normales, resultan anómalos al presentarse juntos como una secuencia o conjunto. Un ejemplo es una secuencia inusual de peticiones a un servidor.
    
- **Puntos Nominales:** Son los puntos de datos que siguen el comportamiento o proceso esperado y estándar dentro del conjunto de datos.
    
- **Mecanismo Diferente:** Concepto que explica que las anomalías a veces no son simples errores, sino indicadores de un nuevo proceso subyacente previamente desconocido.
#### Aplicaciones Principales

- **Detección de Fraude:** Identificación de patrones de transacciones inusuales.
    
- **Ciberseguridad:** Detección de intrusiones y comportamientos anómalos en redes.
    
- **Mantenimiento Predictivo:** Uso de sensores para identificar lecturas que indiquen posibles fallos en maquinaria.
    
- **Calidad de Datos:** Limpieza de datos e identificación de errores o inconsistencias.
    
- **Salud:** Detección de enfermedades noveles o anomalías médicas.
    
- **Video Vigilancia:** Identificación de comportamientos extraños en grabaciones de seguridad.
### Desafíos y Evaluación

- **Datos Desbalanceados (Unbalanced Data):** Situación en la que existe una gran escasez de ejemplos anómalos en comparación con los ejemplos normales1. Es uno de los retos principales, ya que los algoritmos tienden a aprender mejor la clase mayoritaria.
    
- **Escasez de Etiquetas (Little/No Labeled Data):** La dificultad de disponer de pocos o ningún dato etiquetado como "anomalía" para entrenar o validar los modelos2.
    
- **Ruido (Noise):** Datos irrelevantes o errores aleatorios en el conjunto de datos que pueden ser confundidos erroneamente con anomalías por el algoritmo3.
    
- **Novedad Molesta (Nuisance Novelty):** Se refiere a anomalías que, aunque son estadísticamente diferentes, no son relevantes para la tarea o el caso de uso específico4. Por ejemplo, cambios en el fondo de una imagen que no representan una amenaza o fallo5.
    
- **Evolución de las Anomalías:** El desafío de que la naturaleza o el patrón de lo que se considera una anomalía cambie con el tiempo6.
    
- **Verdadero Positivo (True Positive):** Instancia anómala que el modelo identifica correctamente como anomalía7.
    
- **Falso Positivo (False Positive):** Instancia normal que el modelo identifica erróneamente como anomalía.
    
- **Falso Negativo (False Negative):** Instancia anómala que el modelo identifica erróneamente como normal9
    
- **Verdadero Negativo (True Negative):** Instancia normal que el modelo identifica correctamente como normal.
    
- **Precisión (Precision):** Métrica que mide qué porcentaje de las anomalías detectadas por el modelo son realmente anomalías.
    
- **Exhaustividad (Recall):** Métrica que mide qué porcentaje del total de anomalías reales fue capaz de detectar el modelo.
    
- **F1-score:** Una métrica que combina la Precisión y el Recall en un solo valor para evaluar el rendimiento global, siendo muy útil cuando hay clases desbalanceadas.
    
- **Umbral (Threshold / ε):** Valor límite utilizado para decidir si un punto es anómalo o no (por ejemplo, si la probabilidad $p(x) < \epsilon$ ). Se suele ajustar utilizando un conjunto de validación que contenga algunos ejemplos anómalos.
### Métodos Estadísticos (Gaussianos e IQR)

- **Distribución Gaussiana (Normal):**
	Modelo estadístico que asume que los datos se agrupan en torno a una media ($\mu$) con una cierta dispersión o desviación típica ($\sigma$). Se representa con la campana de Gauss.
    
- **Media ($\mu$):** Es el valor promedio de los datos. En un modelo gaussiano, es el punto de máxima probabilidad.
    
- **Varianza ($\sigma^2$) / Desviación Típica ($\sigma$):** Medidas que indican cuánto se alejan los datos de la media. Una varianza alta indica datos muy dispersos.
    
- Algoritmo Gaussiano (1-dimensión): Método que estima la probabilidad de un dato basándose en la media y varianza de una sola característica. Si la probabilidad $p(x)$ es menor que un umbral $\epsilon$, el dato se marca como anomalía.
    $$p(x; \mu, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$
    
- **Algoritmo Gaussiano Multidimensional:** Extensión del método para $n$ características. Asume que la probabilidad total es el producto de las probabilidades de cada característica individual: $p(x) = p(x_1) \cdot p(x_2) \cdot ... \cdot p(x_n)$.
    
- **Independencia de Características:** Suposición necesaria para el modelo gaussiano multidimensional simple, donde se asume que las variables no están correlacionadas entre sí.
    
- Rango Intercuartílico (IQR): Medida de dispersión estadística que se calcula como la diferencia entre el tercer cuartil ($Q_3$) y el primer cuartil ($Q_1$). Representa el 50% central de los datos.
    $$IQR = Q_3 - Q_1$$
    
- Criterio de Outlier (Regla de Tukey): Regla basada en el IQR para detectar anomalías sin asumir una distribución normal. Un punto se considera anomalía si está fuera del rango:
    $$[Q_1 - 1.5 \cdot IQR, Q_3 + 1.5 \cdot IQR]$$
    
- **Cuartiles ($Q_1, Q_2, Q_3$):** Valores que dividen los datos ordenados en cuatro partes iguales. $Q_2$ coincide con la mediana.

	![Imagen de boxplot showing IQR and outliers](https://encrypted-tbn3.gstatic.com/licensed-image?q=tbn:ANd9GcT_E33zdGDg1VmJhsffdR3oVrn6e9nWVXp5SNyvD_CZnevmmYiR6RDSEqi5FibH0fJ1V-vPyKoAqDNSQuKUVZUjinxfBmx_lCvWdREMH4Veqzbcgl4)
### Algoritmos de Proximidad y Aislamiento

- **Local Outlier Factor (LOF):** Algoritmo que detecta puntos anómalos comparando su densidad local con la de sus vecinos más cercanos. A diferencia de otros métodos, busca "outliers" locales en lugar de globales.
    
- **Densidad Local:** Concepto central en LOF que mide qué tan "apretados" están los puntos en una región pequeña del espacio de datos. Las anomalías suelen tener una densidad significativamente menor que sus vecinos.
    
- **Distancia de Alcanzabilidad (Reachability Distance):** Medida utilizada por LOF para suavizar las fluctuaciones estadísticas entre puntos cercanos, definida como el máximo entre la distancia real entre dos puntos y la distancia al k-ésimo vecino más cercano.
    
- **Factor de Outlier Local (LOF Score):** Valor numérico que indica la "rareza" de un punto.
    
    - Si **LOF ≈ 1**, el punto es normal (densidad similar a sus vecinos).
        
    - Si **LOF > 1**, el punto tiene menor densidad que sus vecinos y es un posible outlier.
        
- **Isolation Forest:** Algoritmo basado en la idea de que las anomalías son "pocas y diferentes", lo que las hace más fáciles de aislar que los puntos normales.
    
- **Bosque de Aislamiento (Ensemble):** Conjunto de muchos árboles de decisión aleatorios (por ejemplo, 100) construidos para promediar los resultados y mejorar la precisión.
    
- **Árbol de Aislamiento (iTree):** Estructura binaria construida seleccionando una característica al azar y un valor de corte aleatorio para dividir los datos sucesivamente.
    
- **Aislamiento (Isolation):** Proceso de separar un punto de datos del resto mediante cortes aleatorios. Los puntos anómalos se aislan con **pocos cortes** (poca profundidad en el árbol).
    
- **Profundidad del Nodo (Depth):** Número de cortes necesarios para aislar un punto.
    
    - **Menor profundidad:** Indica una anomalía (fácil de aislar).
        
    - **Mayor profundidad:** Indica un punto normal (difícil de aislar entre la multitud).
        
- **Submuestreo (Subsampling):** Técnica de Isolation Forest que consiste en usar solo una pequeña muestra aleatoria (ej. 256 puntos) para construir cada árbol, reduciendo el coste computacional y evitando problemas de enmascaramiento.
### Detección de Anomalías en Imágenes

- **Autoencoder:** Un tipo de red neuronal diseñada para copiar sus entradas a sus salidas. Se compone de dos partes principales (codificador y decodificador) y se entrena solo con datos normales para que aprenda a reconstruirlos perfectamente.
    
- **Codificador (Encoder):** La primera parte del Autoencoder que comprime la imagen de entrada en una representación mucho más pequeña y compacta.
    
- **Decodificador (Decoder):** La segunda parte del Autoencoder que toma la representación comprimida e intenta reconstruir la imagen original lo más fielmente posible.
    
- **Representación Latente (Latent Representation):** También llamada **"Bottle neck"** (cuello de botella). Es la versión comprimida de los datos en el centro del Autoencoder. Contiene solo la información esencial de la imagen.
    
- **Error de Reconstrucción (Reconstruction Error):** Es la diferencia entre la imagen de entrada y la imagen que el Autoencoder genera a la salida.
    
    - Si el error es **bajo**, la imagen es similar a lo que el modelo vio en el entrenamiento (normal).
        
    - Si el error es **alto**, la imagen contiene patrones que el modelo no conoce (anomalía).
        
- **Denoising (Reducción de Ruido):** Una de las utilidades de los Autoencoders, donde aprenden a eliminar distorsiones de una imagen para recuperar la versión limpia.
    
- **Reducción de Dimensionalidad:** Capacidad del Autoencoder para resumir una imagen compleja (muchos píxeles) en unos pocos valores esenciales en el espacio latente.