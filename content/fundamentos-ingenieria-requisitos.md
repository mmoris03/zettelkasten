# Fundamentos de la ingeniería de requisitos
## Introducción

### Definiciones de la RAE

> [!NOTE] Requisito
> Circunstancia o condición necesaria para algo.

> [!important] requisito ≠ requerimiento (requirement ≠ request)
> Esta confusión se debe a traducir mal “requirement” del inglés.
### Interpretación en el ámbito de la ingeniería de software

Dentro del ámbito de la ingeniería de software, el "algo" de la definición de la RAE se refiere a un sistema o *software* concreto.

> [!NOTE] Definición informal de requisito en el ámbito de la ingeniería de software
> Los requisitos de un *software* concreto serán las **necesidades que debe satisfacer** ese *software* y en qué **condiciones específicas** debe hacerlo.
> En definitiva, los requisitos representan lo que se supone que tiene que hacer el software.

> [!NOTE] Ingeniería de requisitos
> Es la parte de la ingeniería del software que se encarga de gestionar esos requisitos a lo largo de todo el ciclo de vida del *software*.

> [!important] Los requisitos son importantes a lo largo de todo el ciclo de vida del software
> Hoy en día los requisitos no solo son:
> - El punto de partida: *¿Qué hay que hacer?*
> sino también
> - El punto final: *¿Lo que hemos construido hace lo que se supone que debe hacer?*
> 
> Además, no son algo estático porque pueden aparecer nuevos requisitos o modificarse los existentes en cualquier momento, lo cual requiere de una gestión.

> [!important] La ingeniería de requisitos es parte de la ingeniería del software
> - Sus actividades tienen lugar en momentos concretos del ciclo de vida del *software*.
> - Sus resultados o productos son usados o tienen relación con el resto de actividades que conforman ese ciclo de vida.

El siguiente gráfico relaciona el ciclo de vida del software (tomando como referencia las fases o etapas clásicas del ciclo de vida del software) con las asignaturas obligatorias del grado, incluyendo IR.

![[Pasted image 20251214105811.png]]

> [!NOTE] Relación de la ingeniería de requisitos con el desarrollo de software práctico
> La ingeniería de requisitos tiene una relación directa con el desarrollo, puesto que hay que expresar de manera clara qué debe hacer el *software* y en qué condiciones.
> Sin embargo, también tiene un componente "humano" o social, ya que hace de "puente" entre:
> - Perfiles no técnicos
> 	Aquellos que encargan, necesitan, o tienen algún interés en el *software*.
> - Equipo de desarrollo
## Propósito de la ingeniería de requisitos

En resumen, la ingeniería de requisitos trata de afrontar mediante técnicas y métodos:
- La **identificación, descubrimiento u obtención de los requisitos** de un sistema o *software* que se va a construir:
	- ¿Qué debe hacer?
	- ¿Qué necesidades debe satisfacer?
	- ¿Qué condiciones debe cumplir?
	- ¿Qué problemas debe resolver?
- La **documentación de esos requisitos de una forma clara**, de modo que:
	- Pueda ser entendida y validada por los usuarios o clientes.
	- Sirva de base al equipo de desarrollo para el diseño y la construcción del *software*.
	- Facilite verificar que el *software* cumple con esos requisitos.
- La **gestión del ciclo de vida de los requisitos.**
	- Los requisitos pueden cambiar o evolucionar en el tiempo.

Ojo, también existe una Ingeniería de Requisitos asociada a otros sistemas que no tienen que ver con el *software*. Comparte con la "nuestra" algunos procedimientos, métodos y técnicas, aunque es diferente.
## Desarrollo de la ingeniería de requisitos

En el pasado:
- O yo me hacía los programas que necesitaba para mi trabajo.
- O estaba claro a quién preguntar qué había que hacer.

En los años 60 apareció la **crisis del software**, y junto con ella empezó a surgir tanto la ingeniería del software como la ingeniería de requisitos:
- Aparece el **perfil del analista** y la **dicotomía analista-programador**.
	Más que de ingeniería de requisitos se hablaba de análisis de requisitos o sistemas.
- Se empieza a sistematizar la tarea de obtener y especificar requisitos:
	Al principio, se utilizaban técnicas sencillas para problemas sencillos (IN-PROC-OUT).

> [!important] Evolución de la ingeniería de requisitos
> Debido al avance de la tecnología, cada vez el software que se construye es más complejo:
> - Sistemas más grandes
> - Dominios funcionales más complejos
> - Más integraciones con otros sistemas
> - Más usuarios potenciales
> - Necesidad de mantenimiento evolutivo continuo
> - ...
> 
> Por ello, cada vez es más difícil saber qué hay que hacer y mantener ese conocimiento.
> La ingeniería de requisitos va desarrollándose para afrontar esa complejidad.
### Puntos principales del desarrollo de la ingeniería de requisitos

1. **Pasar del "cliente" o usuario al concepto de *stakeholder*.**

> [!NOTE] *¿Quién tiene la información de "qué" hay que hacer?*
> Cuando el *software* crece en complejidad, ya no basta con preguntar por los requisitos al cliente directo o a un usuario de referencia.

> [!NOTE] Stakeholder
> Un *stakeholder* o parte interesada es cualquier persona u organización que tiene algo que decir o tiene algún interés o relación sobre el *software* a construir y sus requisitos.

> [!warning] Identificar a todos los *stakeholders* es una tarea compleja
> > [!example] Ejemplos de *stakeholders*
> > - Clientes.
> > - Distintos usuarios finales.
> > - Administradores y operadores.
> > - Organismos que regulan la actividad a la que da soporte el *software*.

> [!NOTE] Puede haber inconsistencias entre los distintos stakeholders... o con el mismo
> En estos casos habrá que "negociar" una solución.

> [!important] Es necesario relacionarse con los stakeholders
> Esto le da un carácter "humano" a la ingeniería de requisitos y no solo técnico.

2. **Constatación de la relevancia de la ingeniería de requisitos.**

> [!important] Principio de incremento creciente de coste en el ciclo de vida del *software*
> **El coste de corregir un error en la especificación de requisitos aumenta exponencialmente según avanza el proyecto.**
> > [!quote] Los errores cometidos durante la fase de requisitos pueden ser hasta 100 veces más costosos de corregir si se detectan en la fase de mantenimiento.
> > \[Sommerville, 2011\]
> 
> En otras palabras, **el coste de arreglar un error a la hora de construir software es mayor cuanto más tiempo pase desde que se comete el error hasta que nos damos cuenta del mismo.**

> [!NOTE] Los errores en los requisitos son difíciles de detectar por el equipo de desarrollo
> Un error en la especificación de requisitos se puede arrastrar hasta que el *software* esté diseñado, construido y probado y se entregue al *cliente*.
> Esto sucede debido a que suelen ser **difíciles de detectar por el equipo de desarrollo**, porque **no conocen el contexto** y puede que **no tengan contacto con el cliente**.
> > [!warning] Consecuencias de la detección tardía de errores en los requisitos.
> > - Que el cliente rechace el *software* terminado.
> > - Que los usuarios no lo usen.
> > - Retrasos en la implementación.
> > - Sobrecostes.
> > - ...
> >
> > Por todo ello, es necesario establecer mecanismos que minimicen esos errores.

3. **Afrontar explícitamente el mantenimiento de los requisitos.**

> [!NOTE] Mantenimiento evolutivo del *software* en producción.
> Actualmente, es uno de los problemas principales de la industria del *software*.
> La ingeniería de requisitos ha ido desarrollándose para facilitar el mantenimiento y evolución posterior de los requisitos.

4. **Formalizar y sistematizar todas las actividades y documentos asociados a los requisitos.**
	Existen algunas herramientas que dan soporte a la gestión de los requisitos.
5. **Adaptación de la ingeniería de requisitos a las metodologías ágiles de desarrollo.**
	Una de las motivaciones de las metodologías ágiles es adaptarse a entornos donde los requisitos son cambiantes o se van descubriendo sobre la marcha.
6. **Uso de las IA generativas como herramienta para distintas actividades.**
## Definiciones formales

### Definiciones de la ISO/IEC/IEEE 29148

> [!NOTE] Restricción (constraint)
> Limitación impuesta externamente al *software*, su diseño o implementación, o al proceso utilizado para desarrollar o modificar un *software*.
> > [!NOTE] Nota
> > Una restricción es un factor que se impone a la solución por fuerza u obligación, y puede limitar o modificar el diseño.

> [!NOTE] Condición
> Atributo cualitativo o cuantitativo medible que se estipula para un requisito y que indica una circunstancia o evento bajo el cual se aplica dicho requisito.
### Aspectos a tener en cuenta de la ingeniería de requisitos

> [!important] El proceso es **iterativo y cooperativo**.

> [!important] Importancia del **mantenimiento evolutivo** del software.
> El trabajo con los requisitos no termina cuando se entrega el software al cliente.
> Los requisitos irán evolucionando: hay que gestionar esa evolución.

> [!important] Importancia de la **comunicación**.
> El ingeniero de requisitos es, muchas veces, el principal interlocutor entre los *stakeholders* y el equipo de desarrollo.
## Tipología de los requisitos
### Lo que no son requisitos

> [!example] Cosas que, aunque lo parezcan, no son requisitos
> - **Decisiones de diseño, arquitectura o implementación**.
> 	Los requisitos deben versar sobre las necesidades que el *software* debe satisfacer, no sobre cómo implementarlas, por lo que no deberían incluir elementos de diseño como:
> 	- División del *software* en módulos y sus flujos de información y control
> 	- Detalles sobre las estructuras de datos a usar, tecnologías o algoritmos concretos
> 	- …
> 	
> 	Sólo deben incluirse cuando realmente sean impuestos por el *stakeholder* como de obligado cumplimiento (estándares que cumplir, normativas o restricciones internas del cliente…).
> - **Restricciones o requisitos de proyecto**.
> 	Plazos de ejecución, presupuesto, criterios de aceptación, metodología de gestión….
> 	Estos requisitos no son del *software*, por lo que se indicarán en otros documentos.
> - **Necesidades del *stakeholder* que el *software* no puede satisfacer como tal, aunque tenga alguna relación**.
> 	Puede expresar una necesidad que quede parcialmente fuera del alcance del software.
> 	En ese caso, habrá que aclarar qué se puede hacer y qué no.
### Clasificación de los requisitos

Los requisitos son de muy diversos tipos, tratan de distintos aspectos del software a construir, pueden tener distinto nivel de detalle, etc.
Vamos a clasificar los requisitos en función de:
- Su **objeto**:
	- Requisitos **funcionales**.
	- Requisitos **no funcionales**.
- Su **perspectiva** y **nivel de detalle** y **abstracción**:
	- Requisitos **de usuario o stakeholder**.
	- Requisitos de ***software***.
### Requisitos funcionales

> [!NOTE] Requisito funcional
> Un requisito funcional describe las **funciones, servicios o comportamientos** que el sistema debe realizar o proporcionar.
> Dicho de un modo más simple, define *qué* debe hacer el software desde una perspectiva externa sin entrar en el *cómo* hacerlo internamente o bajo qué condiciones externas.
> > [!NOTE] A veces se les denominan capacidades.
> 
> > [!NOTE] Formato de los requisitos funcionales según IEEE 830.
> > Generalmente, se enumeran como declaraciones comenzando con "El sistema deberá..."

> [!warning] Son los que primero suelen aparecer cuando se habla con los primeros stakeholders, pero no son los únicos requisitos…

> [!NOTE] Organización de los requisitos funcionales:
> Para facilitar su gestión, suelen estructurarse en grupos o jerarquía:
> - Agrupando funciones relacionadas.
> - Por tipo de usuario.
> - ...
### Requisitos no funcionales

> [!NOTE] Requisito no funcional
> Definición simple: Todos los demás.
> > [!NOTE] A veces se les denomina **restricciones**
> > Esto se debe a que suelen ser restricciones o limitaciones sobre los requisitos funcionales o sobre el sistema general a construir.

> [!important] Diferencias entre requisitos funcionales y no funcionales.
>  Los funcionales expresan los servicios que ofrece el *software*, mientras que los no funcionales añaden **condiciones** que debe cumplir ese *software*.
>  Pueden ser más críticos que los funcionales y condicionar mucho más la arquitectura y el diseño.
>  > [!warning] La diferencia no siempre es clara
>  > Depende del dominio del proyecto.

> [!example] Ejemplos de requisitos no funcionales
> Suelen referirse a propiedades generales del software.
> - Cumplimiento de normativas o estándares
> - Requisitos de rendimiento
> - Seguridad
> - Capacidad
> - Compatibilidad
> - ...

> [!important] Diferencia entre un requisito no funcional y una decisión de diseño
> La diferencia es que el requisito no funcional **lo impone el *stakeholder*** como algo necesario.

### Clasificación de requisitos no funcionales

No existe una única clasificación, así que habrá que elegir la más adecuada según el proyecto.
- Clasificación según IEEE 830:
	- Requisitos de rendimiento (*performance*).
	- Requisitos lógicos de base de datos.
	- Restricciones de diseño:
		- Cumplimiento normativo
		- Hardware
	- Atributos del software: 
		- Fiabilidad
		- Disponibilidad
		- Seguridad
		- Mantenibilidad
		- Portabilidad.
- Clasificación según MEGEPA/GADEPA 2023):
	- De compatibilidad tecnológica:
		- Tecnologías de desarrollo
		- Tecnologías de despliegue
		- SGBD
		- SO
		- cliente
		- ...
	- De integración (con otros sistemas existentes, como los de autenticación o firma electrónica).
	- De capacidad:
		- Usuarios
		- Transacciones
		- Volumen de datos
		- Ancho de banda
		- Disponibilidad
	- De seguridad:
		- Política de seguridad
		- Normativa
		- Legislación.
- Clasificación según nivel de abstracción o detalle y desde la perspectiva que toman:
	- Requisitos de usuario (o *stakeholder*).
	- Requisitos de software.
### Requisitos de usuario (o stakeholder)

> [!NOTE] Requisitos de usuario o stakeholder
> Los stakeholders no suelen "dictar" requisitos como tal, sino más bien, una mezcla desorganizada de deseos, necesidades, suposiciones… a menudo con lagunas, ambigüedades e incoherencias.
> Estos requisitos, que suelen ser de alto nivel, usar el lenguaje o asunciones de los *stakeholders* etc., se les conoce como requisitos de usuario y expresan las necesidades de los stakeholders desde su perspectiva o punto de vista.

> [!important] Hay que tomar toda esa información, depurarla, integrarla...
### Requisitos de software

> [!NOTE] Requisitos de software
> Los requisitos de usuario no suelen ser lo suficientemente detallados para el equipo de desarrollo, por lo que conviene refinarlos y desarrollarlos, desplazando el punto de vista desde el del *stakeholder* al del *software* a construir.
> Los requisitos de software son precisamente el resultado de ese proceso.
> Por todo ello, los requisitos de software:
> - Son mucho más detallados y concretos que los de usuario:
> 	Se orientan a describir el *software* a construir, no simplemente las necesidades a satisfacer.
> - Están pensados para ser usados directamente por el equipo de desarrollo:
> 	- Añaden información que puede ser obvia para el *stakeholder* pero no para el equipo de desarrollo
> 	- Explicitan condiciones o restricciones
> 	- ...

> [!NOTE] Distinción entre requisitos de usuario o stakeholder y de software.
> Suele relacionarse con la existencia de diferentes "niveles" donde ubicar los requisitos según su nivel de abstracción y detalle.

> [!NOTE] Formas de gestionar la diferencia entre requisitos de usuario/*stakeholder* y de *software*.
> - Opción 1
> 	Ir convirtiendo los requisitos de usuario en requisitos de software, que serán los que documentaremos.
> - Opción 2
> 	Documentar los requisitos de usuario y los de software en documentos separados.
> 	- Más complejo de mantener
> 	- Puede ser necesario si el software es parte de un sistema mayor:
> 	(ISO/IEC/IEEE 29148: BRS $\rightarrow$ StRS $\rightarrow$ SyRS $\rightarrow$ SRS)
> - Opción 3 (la más habitual)
> 	Mantener la perspectiva del usuario en requisitos de alto nivel, que se "explotan" en requisitos de bajo nivel con una perspectiva software.
> > [!example] Ejemplo
> > Se puede crear una jerarquía de requisitos tan desarrollada como haga falta:
> > - RQ1: ...
> > 	- RQ1.1: ...
> > 		- RQ1.1.1: ...
> > 		- RQ1.1.2: ...
> > - RQ2: ...
## La especificación de requisitos de software SRS o ERS

> [!NOTE] Especificación de requisitos de software (**SRS** o **ERS**)
> El objetivo final de la Ingeniería de Requisitos es producir una **especificación de requisitos de *software* (SRS o ERS)**, que es el documento que servirá de base para continuar con el proyecto.

> [!NOTE] **Creación** de la especificación de requisitos de software (**SRS** o **ERS**)
> Aunque el responsable último es el ingeniero de requisitos, han participado en su creación los *stakeholders*.

> [!NOTE] **Aprobación** de la especificación de requisitos de software (**SRS** o **ERS**)
>  El SRS debe de ser **aprobado explícitamente por los *stakeholders* designados**.

> [!NOTE] **Importancia** de la especificación de requisitos de software (**SRS** o **ERS**)
> - Fundamental para el equipo de desarrollo (diseño, arquitectura, codificación, pruebas…).
> - Puede ser parte de un **contrato**: implica obligaciones legales en ambos sentidos.
> - Suele ser la base para calcular el **presupuesto** del software.

> [!NOTE] **Formato** de la especificación de requisitos de software (**SRS** o **ERS**)
> Los requisitos pueden expresarse de diferentes formas:
> - Lenguaje natural (la más común).
> - Lenguajes semiformales o plantillas.
> - **Diagramas** (p. ej., UML, normalmente acompañados de descripciones textuales).
> 
> Además suele añadirse a cada uno información útil como:
> - Prioridad (¿obligatorio, recomendable…?).
> - Estabilidad (¿se espera que se mantenga o que vaya cambiando con el tiempo?, ¿es una necesidad transitoria?).
> - Un **Identificador único** (para hacer el seguimiento).
> - Origen del requisito (¿qué stakeholder aportó la información?).
> - ...
> 
> Por último, el SRS suele tener una estructura determinada, con información general sobre el software o sistema a construir.

> [!warning] A veces el SRS está integrado en documentos de más alto nivel de gestión de proyectos.
### Características de un buen SRS (tomado de IEEE 830)

El SRS, además de un formato determinado, debe de cumplir con una serie de características o propiedades:

- **Correcto:**
	Cada requisito que se indica en él es uno que el software debe cumplir.
- **No ambiguo:**
	Cada requisito indicado en él tiene una única interpretación.
- **Completo:**
	Incluye todos los requisitos y es completo formalmente.
- **Consistente:**
	Ningún subconjunto de requisitos individuales descritos en él entra en conflicto.
- **Clasificado por importancia y/o estabilidad:**
	Esenciales, deseables u opcionales, si se esperan cambios…
- **Verificable:**
	Se puede comprobar de forma objetiva si el software satisface cada requerimiento.
- **Modificable:**
	Si puede evolucionar de manera sencilla.
- **Trazable:**
	Documentar el origen de cada requisito y mantener un id único para los siguientes documentos.
- Otras:
	- no incluir diseño o arquitectura
	- conciso
	- claro
	- ...
## El rol del ingeniero de requisitos

> [!NOTE] "Ingeniero de requisitos" normalmente no es un puesto de trabajo como tal
> Es más bien un **rol** dentro de la Ingeniería del Software que suele realizar un perfil **sénior**, cercano a los de dirección y gestión de proyectos.
> Es uno de los perfiles con **mayor proyección y recorrido profesional**.

> [!NOTE] Características de un buen ingeniero de requisitos
> - Capacidad de análisis y síntesis (detectar incoherencias o lagunas…)
> - Empatía
> - Buena expresión escrita
> - Capacidad de diálogo y negociación
> - …
### Donde y cómo trabaja el ingeniero de requisitos

*   **Modelo tradicional:**
	El ingeniero de requisitos es parte del equipo de desarrollo del software:
	- **Miembro del departamento de informática** de la organización que necesita el software para ella:
		Alternativa: crear software genérico para vender a terceros.
	- **Miembro de una organización externa** contratada para construir el software.
*   **Modelo cada vez más común:**

> [!NOTE] Organización donde trabaja el ingeniero de requisitos
> La organización realiza la Ingeniería de Requisitos (al menos básica) y recurre a una contratación externa para construir el *software*.
> > [!important] La especificación de requisitos es parte de las cláusulas de un contrato
> > Esta especificación de requisitos contractual puede ser de alto nivel y el contratista la refinará como primera tarea.
> > > [!warning] Un desacuerdo puede acabar en un juicio.

*   **Otros modelos:**
	*   Oficina técnica: empresa externa que hace el análisis de requisitos (entre otras cosas) para un cliente que luego contrata el desarrollo a otra empresa.
	*   Consultoría: detectar las necesidades reales de un cliente y orientarle.
	*   Ingeniero preventa/comercial, integrador…: identificar necesidades de clientes, mostrarles pruebas de concepto, construir soluciones con módulos estándar.