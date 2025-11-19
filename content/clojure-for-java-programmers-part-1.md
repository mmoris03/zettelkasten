# Fundamentos

> [!important] Clojure es un lenguaje de programación dinámico
> En particular tiene tipado dinámico.

> [!important] Clojure es un lenguaje de programación funcional
> Clojure estoy muy enfocado en la inmutabilidad, con lo cual los programas se escriben primordialmente con estructuras de datos inmutables

> [!info] JVM
> Está alojado en la **J**ava **V**irtual **M**achine, de hecho fue escrito para la JVM.

> [!info] Concurrencia
> A diferencia de otros lenguajes como C# que usan el modelo de concurrencia basado en locks, estructuras de datos compartidas entre hilos... Clojure resuelve esta problemática de manera automática.

## ¿Por qué usar un lenguaje de programación dinámica?

Existen una serie de razones por las cuales muchos programadores prefieren utilizar lenguajes de programación con tipado dinámico (Python, Ruby...) frente a lenguajes con tipado estático (Java...).

> [!info] Productividad
> Los lenguajes con tipado estáticos son inherentemente más lentos porque requieren mayor interacción del programador con el lenguaje.

> [!info] Interactividad
> Sientes que estás más en contacto con el entorno de ejecución en lugar de sentir que le estás enchufando texto a un compilador que lo interpreta por ti.

> [!info] Conciso
> Java por ejemplo es un claro ejemplo de un lenguaje que no es conciso.
> Los lenguajes de programación dinámicos son mejores para la experimentación y la exploración. En pocas palabras, te permiten centrarte en el problema que estás resolviendo.

## Clojure vs otros lenguajes aptos para la JVM

Existen otros lenguajes dinámicos que también son opciones que funcionan en la JVM como JRuby, Jython, Groovy...

Es importante preguntarse antes de elegir si estos lenguajes fueron escritos para la JVM o son adaptaciones, puesto que estos últimos tienen más problemas.

Los lenguajes nativos de la JVM ofrecen, naturalmente, mejor integración con la JVM.

## ¿Por qué Clojure?

> [!info] Ventajas de Clojure frente a Java
> Uno de los propósitos detrás de aprender Clojure si ya sabes Java es darse cuenta de qué estabas haciendo mal en Java.
> 

> [!info] Acceso directo a Java
> A diferencia de otros lenguajes que se ven obligados a usar adaptadores para lograr la interoperabilidad con Java, Clojure fue diseñado para proporcionar acceso directo a Java.

## Clojure es un dialecto de LISP

- Dinámico
	- Tiene un REPL
	- Permite hacer modificaciones del código en ejecución
- Código como datos
	El código se representa como datos.
- Lector
	Existe un lector que es una entidad en medio del texto y el evaluador
- Núcleo pequeño
	Tiene muchísima menos sintaxis que otros lenguajes como Python por ejemplo.
- Secuencias
	No está tan centrado en las listas como otros dialectos de Lisp.
	Ofrece más estructuras de datos que la mayoría de los demás dialectos.
- Abstracciones sintácticas
	Ofrece mecanismos que permiten extraer aún más código duplicado cuando no es posible hacerlo con una función.
## Desarrollo dinámico

> [!important] **R**ead **E**valuate **P**rint **L**oop
> Utilizaremos el REPL para escribir código, darle a ENTER y "ver qué pasa".

Con Clojure podemos:
- Definir funciones
- Arreglar bugs
**en tiempo de ejecución**, y en consecuencia, en producción.

Es posible acceder al programa que ejecuta nuestro programa.
## Tipos de datos atómicos

> [!important] En Clojure todo son objetos

> [!info] Enteros
> Tienen una precisión arbitraria que será tan grande como tu memoria pueda soportar.
> Promoción automática de tipos enteros pequeños a grandes.
> > [!example] Ejemplo
> > `87236492092`

> [!info] Doubles
> Son los `Double` (que no `double`) de Java.
> > [!example] Ejemplo
> > `3.215`

> [!info] Ratios
> Representan números **sin perder información** ya que no lo convierten a un formato de coma flotante.
> > [!example] Ejemplo
> > `22/7`

> [!info] Strings
> Son los `String` de Java. Son inmutables.
> > [!example] Ejemplo
> > `"fred"`
> 

> [!info] Caracteres
> Son los `Char` de Java.
> > [!example] Ejemplos
> > `\a` `\b` `\c`

> [!info] Símbolos
> Son identificadores que no pueden contener espacios en blancos y se usan principalmente a nivel de código aunque, dado que con objetos de primera clase (en Java no lo son).
> > [!example] Ejemplos
> > `fred` `ethel` 
 
> [!important] Uso de símbolos como claves de diccionarios
> Son muy útiles para las claves de diccionarios porque son muy rápidos a la hora de hacer comparaciones y se imprimen y leen como sí mismos.

> [!info] Palabras reservadas
> Las palabras reservadas siempre se designan a sí mismas, con lo cual en ningún caso se asocian a un valor, no se evalúan.
> > [!example] Ejemplos
> > `:fred` `:ethel` 

> [!WARNING] Diferencia clave con las palabras reservadas
> Mientras que es posible usar un símbolo `fred` como variable y hacer que sea equivalente a 5 pero nunca podrías hacer que `:fred` sea equivalente a `5`
> `:fred` siempre va a ser equivalente a `:fred` cuando se evalúa.

> [!NOTE] Null
> `nil` significa nada y es el mismo valor que `null` de Java.
> `nil` es `false`.

> [!NOTE] Regex
> Se emplea la misma sintaxis que en Java.
> > [!EXAMPLE]
> > `#"a\*b"`

## Estructuras de datos

> [!important] Las estructuras de datos son inmutables

> [!important] Las estructuras de datos son persistentes

> [!important] Todas las colecciones pueden ser hetereogéneas

> [!important] Igualdad
> El operador que evalúa la igualdad es `=`.
> Cabe destacar que en Clojure la igualdad siempre es igualdad de valores, no de identidad. 

> [!info] Lista
> Son listas simplemente enlazadas en las que los elementos se añaden al principio.
> - Buscar el elemento en la posición n-ésima: O(n)
> - Añadir un elemento al principio: O(1)
> - Eliminar un elemento al principio: O(1)
> > [!example] Ejemplo
> > `(1 2 3 4 5)` `(fred ethel lucy)` `(list 1 2 3)`

> [!info] Vectores
> Son arrays que soportan acceso eficiente mediante índices. Son similares a los `ArrayList` de Java.
> - Buscar el elemento en la posición n-ésima: O(1)
> > [!example] Ejemplos
> > `[1 2 3 4 5]` `[fred ethel lucy]`

> [!info] Mapas/Diccionarios (pares clave-valor)
> Ofrecen una asociación entre claves y valores, con la restricción de que las claves son únicas. Son similares a los `Map` de Java, concretamente un `HashMap`.
> - Buscar el valor asociado a una clave: O(1)
> > [!example] Ejemplo
> > `{:a 1 :b 2 :c 3}` `(1 "ethel" 2 "fred")`

> [!info] Mapas/Diccionarios ordenados
> También existen mapas ordenados en los que la búsqueda a partir de la clave es `O(log n)`.

> [!info] Sets
> Son conjuntos de elementos únicos.
> Son similares a los `Set` de Java, concretamente `HashSet`. 
> > [!example] Ejemplo
> > `#{fred ethel lucy)`

> [!important] Todas estas estructuras de datos son *anidables*

> [!important] En un programa concurrente no son necesarios bloquos para trabajar con estas estructuras de datos.
# Sintaxis y modelo de evaluación

## Sintaxis de Clojure

> [!important] Las estructuras de datos son el código
> Esta es la naturaleza de Lisp, y tiene muchísimas implicaciones.
> > [!important] La sintaxis es la interpretación de las estructuras de datos
> 
> > [!info] Homoiconicidad
> > Es una propiedad de algunos lenguajes de programación, Clojure entre ellos.
> > 
> > Significa que la representación del programa en memoria, el árbol de sintaxis abstracta, se realiza a partir de las propias estructuras de datos centrales del programa.
> > Esto significa que los programas pueden ser procesados por otros programas porque son estructuras de datos.

> [!callout] Sintaxis a la hora de interpretación del código
> Los elementos que aparecen al principio indican el significado del resto

## Modelo evaluación de Clojure

- Modelo de evaluación de Java
	1. Escribimos nuestro programa en un fichero de texto.
	2. Lo almacenamos.
	3. Enviamos los caracteres del fichero de texto al compilador.
	4. El compilador procesa el texto genera un AST a partir del analizador léxico y analizador sintáctico, asumiendo que el programa es correcto sintácticamente.
	5. Genera código Bytecode que es ejecutable por la JVM y lo mete en archivos .class/.jar
	6. La JVM ejecuta el código.
	![[modelo-evaluacion-java.png]]
- Modelo de evaluación de Clojure
	![[modelo-evaluacion-clojure.png]]
	1. Escribimos nuestro programa en un fichero de texto.
	2. Lo almacenamos.
	3. Enviamos los caracteres del fichero de texto al lector.
		Su función es procesar los caracteres y convertirlos en estructuras de datos.
		Lo que le llega al compilador ya son estructuras de datos, nunca trabaja con texto.
	4. El compilador/evaluador genera Bytecode a partir de esas estructuras de datos (no interpreta) que es ejecutable por la JVM.
	5. Al tratarse de un entorno interactivo, la JVM ejecuta directamente el código Bytecode.

> [!NOTE] El código no tiene por qué proceder de un fichero, se pueden evaluar expresiones enviándoselas al lector.

> [!note] Es posible incluso no utilizar texto
> Podemos escribir un programa que genera las estructuras de datos que el compilador necesita y se las envíe para que este las evalúe.
> 
> > [!note] Un uso común de Clojure es precisamente escribir programas que generan programas.
> 

## Expresiones

> [!important] En Clojure todo son expresiones
> En Java se distinguen declaraciones, sentencias y expresiones, en Clojure no existe esa distinción.
> El trabajo del compilador es evaluar todas las estructuras de datos (mapas, conjuntos, vectores...) para representar a sí mismos.

Sin embargo, existen dos excepciones que el compilador no va a devolver directamente representándose a sí mismos:

> [!warning] Los símbolos son tratados de manera especial por defecto.
> El compilador va a intentar mapearlos a valores, como si fueran variables.  
> Cuando nosotros utilicemos un símbolo en una estructura de datos, Clojure va a intentar averiguar qué valor tiene asociado ese símbolo haciendo una búsqueda primero local, y después global.  
> Se puede asociar un valor a un símbolo mediante dos construcciones:
> - Símbolo local
> `(let [name value-expr] expr1 expr2 ... exprN)`
> Recibe una serie de pares símbolo-valor, los asocia, y después ejecuta todas las expresiones que vienen detrás, siendo la última de ellas el valor retornado.
> > [!important] Es inmutable
> - Símbolo global 
> `(def name value-expr)`
> > [!important] Aquello que se define con `def` es mutable, en el fondo.
> > Es probablemente "la única vía de escape" para lograr la mutabilidad en Clojure.

> [!warning] Las listas son tratadas de manera especial por defecto.
> Cuando el compilador recibe una lista de símbolos va a intentar interpretarlos como una operación en la que el primer elemento de la lista es el operador `op`, que determina lo que se va a hacer

## Operadores

> [!iinfo] Operadores `(op ...)`
> Los operadores pueden ser:
> - Operadores especiales
> Pueden tener una evaluación anormal de sus argumentos, es decir, pueden no evaluarlos.
> 	- `if`
> > [!example] Condicional
> > `(if test-expr then-expr else-expr)`
> > En caso de intentar que `if` fuese una función, tendríamos el problema de que `if` solo debe evaluar la expresión `test-expr`, y las funciones evalúan todos sus argumentos, con lo cual debe ser una función especial.
> > - Si `test-expr` es `nil` o `false` -> `else-expr`
> > - Si `test-expr` es cualquier otra cosa -> `then-expr`
> > > [!note] Se puede omitir `else-expr`
> 	- `let`
> 	- `def`
> 	- `fn`
> 	- `loop`
> 	- `recur`
> 	- `do`
> 	- `new`
> 	- `throw`
> 	- `try`
> 	- `set!`
> 	- `quote`
> 	- `var`
> 	- ...
> - Macros
> > [!important] Son definidas por el usuario y permiten extender el lenguaje Clojure.
> 
> La idea es decirle al compilador que, en lugar de intentar interpretar una determinada estructura de datos que no conoce, utilice un programa nuestro.
> Nuestro programa recibe esa estructura de datos desconocida para el compilador, pues no conoce el `op`, pero como nosotros hemos marcado ese símbolo como una *macro*, se ejecuta una función (asociada a esa *macro*) que espera recibir el resto de cosas que están entre paréntesis, y después se le envía al compilador la estructura de datos resultado de esta función.
> 
> > [!important] Este programa *auxiliar* se llama *macro* y permite la abstracción sintáctica y la extensión de la sintaxis del lenguaje.
> 
> > [!quote] Es un proceso de transformación en el que se le envían los datos que están entre paréntesis como argumentos a la *macro*, que ejecutará un programa arbitrario que dada la estructura de datos, devuelve la estructura de datos *sustituta* que interpretará el compilador.
> 
> > [!important] Proceso recursivo
> > Las macros pueden devolver una macro que devuelve otra macro que devuelve otra macro... y así sucesivamente hasta devolver algo que el compilador entiende y continúa la compilación hasta generar el Bytecode.
> 
> > [!example] Ejemplos de macros de Clojure
> > - `(or x y)`
> > El operador `or` no es primitivo, sino que se construye con `if`.
> > Al igual que el operador `||` en Java, `or` funciona de manera que, si la primera parte se evalúa a verdadero, la segunda parte no se evalúa. Este comportamiento extraño que es diferente a las funciones normales, es el mismo que realiza `if`: evaluación condicional de una de dos expresiones.
> > `(or x y)` se expande a
> > ```clojure
> > (let [or__158 x]
> > 	if or__158 or__158 y))
> > ```
> > [!important] Esta tranformación supone una optimización respecto de `if (x x y)` porque se evita evaluar `x` dos veces, algo que es interesante cuando `x` no es un símbolo sino una expresión costosa de evaluar.
> - Expresiones que devuelve algo que sea *invocable*
> > [!warning] Aunque normalmente serán funciones, existen otras construcciones del lenguaje *invocables* además de las funciones.

# Secuencias
# Integración con Java
# Concurrencia
# Q&A
