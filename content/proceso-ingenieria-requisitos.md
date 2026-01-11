# Proceso de la ingeniería de requisitos
## Introducción

En este tema vamos a identificar y definir las actividades o subprocesos que implica la práctica de la Ingeniería de Requisitos y también veremos el proceso general que las integra y cómo se relacionan entre sí.

> [!NOTE] Actividades principales que conforman la Ingeniería de Requisitos
> - Educción u obtención de requisitos
> - Análisis de requisitos
> - Especificación de requisitos
> - Validación de requisitos
> - Gestión de requisitos

## Definición de las actividades principales

### Educción u obtención de requisitos

### Análisis de requisitos

> [!NOTE] Definición de IREB: Análisis de requisitos
> Análisis de los requisitos educidos (obtenidos) con el fin de entenderlos y documentarlos.

> [!NOTE] Definición informal: Análisis de requisitos
> Consiste en obtener los requisitos "en bruto" de los *stakeholders* y estudiarlos en detalle.

> [!NOTE] Objetivos del análisis de requisitos
> - Detectar lagunas o conflictos entre requisitos que habrá que resolver.
> - Precisar mejor el alcance de los requisitos
> - Completar información asociada a ellos
> - Clasificarlos u organizarlos
> - ...
> En definitiva, ir moviendo el foco o perspectiva desde los *stakeholders* hacia el *software*.
> Para ello, suele recurrirse a técnicas de modelado que faciliten describir los requisitos de manera más precisa y formal.
### Especificación de requisitos

> [!NOTE] Especificación de requisitos
> Plasmar los resultados de la educción y el análisis en un documento de especificación de requisitos (SRS).

> [!NOTE] Aspectos a tener en cuenta
> - Habrá que terminar de organizar o clasificar los requisitos.
> - El documento de especificación de requisitos tendrá que seguir algún tipo de norma formal.
> - Tanto los requisitos de forma individual como el SRS en conjunto deberán de tener una serie de características deseables.
### Validación de requisitos

> [!NOTE] Definición de IREB: Validación de requisitos
> Es el proceso de confirmación de que los requisitos documentados son correctos, o en otras palabras, que coinciden con las necesidades de los *stakeholders*.

> [!important] Los requisitos deberán ser validados, al menos, por los *stakeholders* designados.
> - Hay que ayudar a los *stakeholders* no técnicos a comprender el SRS para que la validación sea efectiva.
> 	Hay diferentes técnicas para ayudara validar los requisitos.
> - En ocasiones, también debe ser validado por miembros del equipo de desarrollo.
### Gestión de requisitos

> [!NOTE] Gestión de requisitos
> Los requisitos, aunque ya hayan sido educidos, especificados, o incluso validados, pueden evolucionar o cambiar (lo raro sería que no fuese así).
> La gestión de requisitos se encarga, básicamente, de afrontar esos cambios en los requisitos a lo largo de todo el ciclo de vida del software.
## Flujo real del proceso

Aunque el orden "lógico" es el expuesto (la gestión puede requerirse en cualquier momento):
1. Educción u obtención de requisitos
2. Análisis de requisitos
3. Especificación de requisitos
4. Validación de requisitos
en la realidad las actividades descritas **no se realizan una sola vez**.

> [!important] El flujo real es más bien una espiral
> Vamos realizando iteraciones de los 4 pasos hasta alcanzar los resultados finales, de manera incremental.
> ![[Pasted image 20251216174130.png]]
> El resultado final, el SRS, se va construyendo igualmente de forma iterativa e incremental.

> [!NOTE] Proceso ideal
> En cada iteración nos ocupamos de requisitos de un cierto nivel, de mayor abstracción a mayor detalle.
> > [!example] Ejemplo canónico
> > - Iteración 1: requisitos de negocio o dominio (los de más alto nivel).
> > - Iteración 2: requisitos de *stakeholder* más concretos.
> > - Iteración 1: requisitos de *software*.
> 
> > [!NOTE] Según la complejidad del sistema, podría haber más o menos iteraciones.

> [!warning] En realidad, lo anterior puede no ser factible
> El proceso real es más complejo: en una iteración pueden coexistir requisitos de distinto nivel de abstracción.

> [!NOTE] ¿Por qué lo habitual es no poder seguir una espiral perfecta?
> - Los *stakeholders* no siempre están disponibles cuando los necesitamos.
> 	Tendremos que avanzar con la información disponible.
> - Necesidad de dar "marcha atrás" con parte de los requisitos mientras se avanza con el resto:
> 	- Los *stakeholders* suelen cambiar de opinión o dar información relevante a última hora.
> 	- Los conflictos detectados y su resolución también pueden provocar "daños colaterales" y obligar a rehacer trabajo hecho.
## Otras actividades
### Negociación de requisitos

> [!NOTE] Negociación de requisitos
> Tarea que consiste en resolver conflictos.
> 

Cabe destacar que:
- Siempre requiere la participación de los *stakeholders* afectados.
- Aunque algunos autores lo ubican como parte de una única actividad (análisis o validación), los conflictos pueden detectarse en cualquier momento.
	Conviene afrontarlos en cuanto se identifican.
### Verificación de requisitos

> [!NOTE] Verificación de requisitos
> Tarea que consiste en confirmar que los requisitos están bien construidos o especificados, es decir, que individualmente y como conjunto tienen las características formales deseadas.

Cabe destacar que:
- Se focaliza entre la especificación y la validación.
- En la práctica, deberíamos de tenerlo en cuenta en todo el proceso.
	Por ejemplo, siguiendo buenas prácticas de documentación desde el inicio, lo cual es muy importante durante el mantenimiento evolutivo del software (gestión de requisitos).
- No se debe confundir con verificar que el software construido satisface los requisitos previamente especificados (parte de las pruebas de software).
## Conclusiones

- En la ingeniería de requisitos pueden identificarse varias actividades principales:
	1. Educción: obtener los requisitos de los *stakeholders*
	2. Análisis: completarlos, subsanar conflictos y desarrollarlos para llegar a requisitos de *software*.
	3. Especificación: plasmar lo anterior en un SRS.
	4. Validación: validar con los *stakeholders* que el SRS expresa correctamente todas sus necesidades.
- Estas actividades se realizan de forma iterativa e incremental (modelo de espiral).
- La gestión de requisitos se encarga de lidiar con los cambios o evolución de los requisitos, durante el proceso de desarrollo y en el mantenimiento del *software*.
- Otras tareas, como la negociación y verificación de requisitos, ocurren como parte de las anteriores.
## Bibliografía
• Glinz, Martin. CPRE. RequirementsEngineeringGlossary(versión 2.1.0). International RequirementsEngineeringBoardIREB. https://cpre.ireb.org/en/concept/knowledge-and-resources/glossary
• International Organization for Standardization, International Electrotechnical Commission, & Institute of Electrical and Electronics Engineers.(2018).Systems and software engineering —Life cycle processes —Requirements engineering (ISO/IEC/IEEE 29148:2018)
• Real Academia Española. Diccionario de la lengua española(24.ª ed., 2025). https://dle.rae.es