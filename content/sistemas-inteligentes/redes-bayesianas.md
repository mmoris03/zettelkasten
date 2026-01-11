# Redes bayesianas
## Introducción
### Noción de incertidumbre

> [!important] En muchos dominios de interés para la IA es necesario trabajar con **incertidumbre**.

> [!example] Ejemplo
> Voy a un restaurante y la comida es buena, pero hay una mosca en la sopa y el servicio es mediocre.
> - ¿Qué propina debo dejar?
> - ¿Debo presentar una reclamación?
> Ahora viene el encargado y me pide disculpas y me invita a café.
> - ¿Debo cambiar mis decisiones?

> [!example] Ejemplo
> Un paciente presenta tos, fiebre y dificultad para respirar.
> - ¿Cuál es la probabilidad de que tenga gripe?
> - ¿Cuál es la probabilidad de que tenga neumonía?
> Le hacemos una radiografía y aparecen manchas en el pulmón.
> - ¿Cuál es ahora la probabilidad de que tenga gripe?
> - ¿Cuál es ahora la probabilidad de que tenga neumonía?

> [!NOTE] Aspectos relevantes de los sistemas de razonamiento con incertidumbre
> - Es el tipo de razonamiento que se hace en la mayoría de las situaciones reales.
> - El razonamiento no suele ser monótono.
> 	El grado de convicción sobre ciertos hechos puede variar a lo largo del proceso de razonamiento.
> - Se trata de utilizar el conocimiento disponible de la mejor manera posible.
> 	Si el conocimiento aumenta, debería mejorar la calidad de las inferencias.
> - Los modelos clásicos como la lógica o las reglas de producción no sirven.
> 	Son necesarios nuevos modelos que permitan representar y razonar con conocimiento incierto, impreciso, vago, contradictorio...

## Modelos de razonamiento con incertidumbre

> [!NOTE] Reglas difusas (estilo Mandani)
> Relacionan hechos que son ciertos en un determinado grado.
> ![[Pasted image 20251208183647.png]]

> [!NOTE] Redes bayesianas
> Expresan probabilidades de algunos hechos y relaciones de dependencia e independencia entre otros representados por variables aleatorias.
> Los hechos solo pueden ser ciertos o falsos.
> ![[Pasted image 20251208183909.png]]

> [!imporant] Las redes bayesianas son el modelo dominante en IA
> Las redes bayesianas, propuestas por Judea Pearl (premio Turing en 2012) en el año 1988, son consideradas como una de las contribuciones más importantes de la inteligencia artificial en las últimas décadas.
## Teoría de la probabilidad
### Resultados de un experimento

> [!NOTE] Espacio muestral $U$
> Es el conjunto que contiene **todos** los resultados posibles de un experimento, sucesos elementales.

> [!NOTE] Suceso aleatorio $A$
> Es un subconjunto del espacio muestral $A \subseteq U$
> - Si $A = U$, se llama **suceso seguro** (va a ocurrir sí o sí).
> - Si $A = \emptyset$ (conjunto vacío), se llama **suceso imposible**.

### Probabilidad de sucesos aleatorios

> [!NOTE] Función de probabilidad $P: 2^U \rightarrow \mathbb{R}$
> Se define la probabilidad $P$ como una función que asigna un número real a cada suceso posible.
> Matemáticamente se expresa como $P: 2^U \rightarrow \mathbb{R}$, lo que significa que toma cualquier subconjunto posible de $U$ y le asigna un valor real.

### Axiomas de la probabilidad
Estos son las tres reglas inquebrantables sobre los que se construye toda la teoría:

> [!NOTE] Normalización
> $$P(U)=1$$
> La probabilidad del espacio muestral completo es 1 ($P(U)=1$), lo que significa que la suma de las probabilidades de todas las opciones posibles es el 100%.

> [!NOTE] No negatividad
> $$\forall A \subseteq U, P(A) \ge 0$$
> La probabilidad de cualquier suceso $A$ es mayor o igual a cero ($P(A) \ge 0$), lo que significa que no existen probabilidades negativas.

> [!NOTE] Aditividad
> $$\forall A,B \subseteq U, A \cap B = \emptyset, P(A \cup B) = P(A) + P(B)$$
> Si dos sucesos $A$ y $B$ son **disjuntos** (su intersección es vacía, $A \cap B = \emptyset$, es decir, no pueden ocurrir a la vez), la probabilidad de su unión es la suma de sus probabilidades individuales: $P(A \cup B) = P(A) + P(B)$
> ![[Pasted image 20251208190006.png]]
### Deducciones de los axiomas de la probabilidad

> [!NOTE] Suceso imposible
> $$P(\emptyset) = 0$$

> [!NOTE] Límite superior
> $$\forall A \subseteq U, P(A) \le 1$$

> [!NOTE] Probabilidad del complemento
> $$\forall A \subseteq U, P(U \setminus A) = 1 - P(A)$$

> [!NOTE] Probabilidad de la unión
> $$\forall A,B \subseteq U, P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

> [!NOTE] Unión finita de sucesos disjuntos
> $$\forall A_1, ..., A_n \subseteq U, A_1 \cap ... \cap A_n = \emptyset, P(A_1 \cup ... \cup A_n) = P(A_1) + ... + P(A_n)$$

### Interpretaciones de la probabilidad

> [!NOTE] Interpretación bayesiana de la probabilidad
> Grado de creencia en que se va a producir un suceso.

> [!NOTE] Interpretación frecuentista de la probabilidad
> Frecuencia relativa con la que se produce un suceso.
### Variable aleatoria y distribuciones de probabilidad

> [!NOTE] Definición de variable aleatoria $X$ (discreta)
> Una **variable aleatoria** es una función matemática que asocia un valor numérico a cada posible resultado de un experimento o suceso aleatorio.
> Una **variable aleatoria** $X$ (discreta) en un espacio $(U, P)$ es una función
> $$X: U \to \Omega_X$$
> - $\Omega_X$ es el espacio de $X$

> [!example] Ejemplos de variables aleatorias discretas
> - $U = \{1, 2, 3, 4, 5, 6\}$
> - $X$ = **Paridad**: $\Omega_X = \{\text{par, impar}\}$
> - $Y$ = **Intervalo**: $\Omega_Y = \{\text{menor\_que\_tres, entre\_tres\_cuatro, mayor\_que\_tres}\}$

> [!NOTE] Función de distribución de probabilidad $P$ de una variable aleatoria $X$
> $$P: \Omega_X \to \mathbb{R}$$
> - $P(x_i) = P(X = x_i) = P(\{e \in U | X(e) = x_i\})$
> - **Notación**: $P(X)$ es una distribución de probabilidad sobre $X$

> [!example] Ejemplos
> - $\Omega_X$: $P(\text{par}) = P(\{2, 4, 6\}) = P(\{2\}) + P(\{4\}) + P(\{6\}) = 1/2$
> - $\Omega_Y$: $P(\text{mayor\_que\_cuatro}) = P(\{5, 6\}) = 1/3$

> [!important] Definición informal
> Una **variable aleatoria** $X$ es una variable que puede tomar valores en un dominio $\Omega_X$.
> Cada valor $x_i$ tiene una determinada **probabilidad** $P(x_i)$

### Probabilidad conjunta y marginal

> [!NOTE] **Probabilidad conjunta** $P$ de un conjunto de variables $X = \{X_1, \dots, X_n\}$
> $$P: \Omega_1 \times \dots \times \Omega_n \to [0, 1]$$
> - **Notación**: $P(x_1, \dots, x_n) = P(X_1 = x_1, \dots, X_n = x_n)$
> Debe cumplir: 
> $$\sum_{x_1, \dots, x_n} P(x_1, \dots, x_n) = 1$$
> - **Notación**: $P(X_1, \dots, X_n)$ es la tabla de distribución conjunta
> > [!NOTE] Si las variables son booleanas, entonces hay $2^n$ conjuntos de valores $x_1, \dots, x_n$ en la tabla.

> [!NOTE] **Probabilidad marginal**
> - $P(x_1, \dots, x_i) = \sum_{x_{i+1}, \dots, x_n} P(x_1, \dots, x_i, x_{i+1}, \dots, x_n)$
> - $P(x_1, \dots, x_i, x_{i+1}) = \sum_{x_{i+2}, \dots, x_n} P(x_1, \dots, x_i, x_{i+1}, x_{i+2}, \dots, x_n)$

> [!example] Ejemplo con 3 variable booleanas $A, B, C$
> ![[Pasted image 20251208194614.png]]
> A partir de la distribución conjunta podemos calcular probabilidades marginales:
> - $P(a) = P(a, \neg b, \neg c) + P(a, \neg b, c) + P(a, b, \neg c) + P(a, b, c)$
> - $P(a, \neg b) = P(a, \neg b, c) + P(a, \neg b, \neg c) = 0.1 + 0.3$

Seguir desde la página 12 hasta la 20
### Probabilidad condicionada
## Redes bayesianas

> [!important] Utilidad de las redes bayesianas
> Permiten representar relaciones de dependencia e independencia entre variables aleatorias.
> - Muchos menos valores de probabilidad que las tablas de valores de distribución conjunta.
> - Mayor eficiencia para el cálculo de probabilidades conjuntas o marginales.

> [!NOTE] Aplicaciones de las redes bayesianas
> Tienen muchas aplicaciones en las que el conocimiento que se maneja es incierto.
> - Filtrado de correo
> - Reconocimiento de voz
> - Robótica
> - Diagnóstico médico
> - ...

### Estructura (DAG)

> [!NOTE] ¿Qué es una red bayesiana?
> ![[Pasted image 20251208195619.png]]
> Una red bayesiana es un modelo gráfico que representa relaciones de dependencia condicional entre un conjunto de variables aleatorias mediante un **grafo dirigido acíclico (DAG)** en el que:
> - Cada nodo del grafo es una variable aleatoria.
> - Un arco de X a Y indica que estas variables son **dependientes**.
> 	En un grafo causal: **X es una causa de Y**
> - La **ausencia de arcos** entre dos nodos **no** significa **independencia**
> 	C y D no son independientes, pero son **condicionalmente independientes dado B**
### Tabla de probabilidad condicional (CPT)

![[Pasted image 20251208202531.png]]

> [!NOTE] Tabla de probabilidad condicional (CPT)
> Cada nodo contiene una **tabla de probabilidad condicional (CPT)**.
> Expresa la distribución de probabilidad condicional $P(X_i | Padres(X_i))$ que cuantifica el efecto de los padres sobre el nodo.

> [!important] La suma de las probabilidades del nodo debe dar 1 para cada una de las combinaciones de valores de los padres.
> Esto reduce **a la mitad** el número de valores que necesitamos conocer para cada tabla, si las variables son booleanas, porque solo necesitamos conocer la probabilidad de **uno** de los estados del nodo para **inferir el otro**.
> Si todas las variables son booleanas, para un nodo con $k$ padres se requieren **$2^k$ valores** en cada nodo en lugar de $2^{k+1}$.
> 
> ![[Pasted image 20251208200833.png]]

### Cálculo de la probabilidad conjunta

> [!NOTE] Teorema de factorización
> Podemos calcular la distribución conjunta de todas las variables de la red $\{X_1, \dots, X_n\}$ usando la fórmula:
> $$P(x_1, \dots, x_n) = \prod_{i=1}^n P(X_i = x_i | Padres(X_i))$$
> Donde $Padres(X_i)$ son los valores de los padres del nodo $X_i$.
> > [!NOTE] Es menos costoso que aplicar la regla de la cadena
> > Requiere conocer menos probabilidades condicionadas:
> > $$P(x_1, \dots, x_n) = \prod_{i=1}^n P(X_i = x_i | X_{i+1} = x_{i+1}, \dots, X_n = x_n)$$

> [!example] Ejemplo: **¿qué valor tiene** $P(C, \neg D, B, \neg A)$**?**
> ![[Pasted image 20251208202600.png]]
> - Teorema de factorización
> $$P(C, \neg D, B, \neg A)$$
> $$= P(C | Padres(C)) P(\neg D | Padres(D)) P(B | Padres(B)) P(\neg A | Padres(A))$$
> $$= P(C | B) P(\neg D | B) P(B | \neg A) P(\neg A) = 0.1 \cdot 0.05 \cdot 0.99 \cdot 0.6$$
> - Regla de la cadena
> $$P(C, \neg D, B, \neg A)$$
> $$= P(C | \neg D, B, \neg A) P(\neg D | B, \neg A) P(B | \neg A) P(\neg A)$$

### Agentes inteligentes con RBs para representación del conocimiento.

![[Pasted image 20251208202251.png]]

### Construcción de una RB
Leer de la 27 a la 31
### Independencia en redes bayesianas

![[Pasted image 20251209105828.png]]

> [!NOTE] **(a)** Independencia Condicional Local de un nodo $X$
> Un nodo $X$ es **condicionalmente independiente** de sus **no descendientes** (por ejemplo, los $Z_{ij}$s) dados sus **padres** (los $U_i$s mostrados en el área lila).
> 
> Esto significa que, si ya conoces el estado de los **padres** de $X$ ($U_1, \dots, U_m$), la información sobre cualquier otro nodo que no sea un descendiente de $X$ ($Z_{11}, \dots, Z_{nj}$) es **irrelevante** para determinar la probabilidad de $X$.
> **En otras palabras, la única información que influye a $X$ proviene de sus padres.**

> [!NOTE] **(b)** Manto de Markov
> Un nodo $X$ es **condicionalmente independiente** de **todos los otros nodos de la red** dado su **Manto de Markov** (el área lila).
> 
> El **Manto de Markov** es el conjunto de nodos que aísla completamente a $X$ de cualquier otro nodo en la red. Está formado por tres grupos:
> - Los **Padres** de $X$ ($U_i$s).
> - Los **Hijos** de $X$ ($Y_j$s).
> - Los **Otros Padres** de los Hijos de $X$ ($Z_{ij}$s).
> 	Estos $Z_{ij}$s ahora se incluyen porque son co-padres de los hijos de $X$).
> 
> Si conoces el estado de **todos los nodos que componen el Manto de Markov de $X$**, cualquier otro nodo fuera de esa área (la red restante) no te dará ninguna información adicional sobre la probabilidad de $X$.

### Criterio de separación por D
![[Pasted image 20251209111359.png]]
La pregunta de independencia condicional más general que se puede plantear en una red bayesiana es si un conjunto de nodos $\mathbf{X}$ es condicionalmente independiente de otro conjunto $\mathbf{Y}$, dado un tercer conjunto $\mathbf{Z}$.
Esto se puede determinar eficientemente examinando la Red Bayesiana para ver si $\mathbf{Z}$ **separa-d** a $\mathbf{X}$ y $\mathbf{Y}$. 
El proceso funciona de la siguiente manera:
1. Considerar solo el **subgrafo ancestral** que consiste en $\mathbf{X}$, $\mathbf{Y}$, $\mathbf{Z}$ y sus ancestros.
2. Añadir enlaces entre cualquier par de nodos no enlazados que comparten un **hijo común**; ahora tenemos el llamado **grafo moral**.
3. Reemplazar todos los enlaces dirigidos por **enlaces no dirigidos**.
4. Si $\mathbf{Z}$ **bloquea todos los caminos** entre $\mathbf{X}$ e $\mathbf{Y}$ en el grafo resultante, entonces $\mathbf{Z}$ **separa-d** a $\mathbf{X}$ y $\mathbf{Y}$.
	En ese caso, $\mathbf{X}$ es condicionalmente independiente de $\mathbf{Y}$, dado $\mathbf{Z}$.
	De lo contrario, la Red Bayesiana original **no** requiere independencia condicional.
### Inferencia en redes bayesianas

> [!NOTE] Inferencia en redes bayesianas
> La inferencia consiste en utilizar la red bayesiana para calcular la probabilidad de uno o varios eventos.

## Ejercicios