# Conceptos generales de Calidad, Validación y Verificación del Software

> [!important] ¿Por qué son necesarias las pruebas?
> Porque todos cometemos errores.
## Historias de fallos

- https://it.slashdot.org/story/07/02/25/2038217/software-bug-halts-f-22-flight
- http://www.f-22raptor.com/news_view.php?nid=267
- https://tech.slashdot.org/story/09/07/22/1813236/f-22-raptorcancelled?sdsrc=rel
## Problemática general

![[problematica-general-errores-software.png]]
## Causas de los defectos en el software

> [!NOTE] Los defectos en el software se deben a múltiples causas
> - Falta de experiencia
> 	- Proyecto
> 	- Tecnologías
> 	- Herramientas
> - Falta de información
> 	- Requisitos mal documentados
> - La presión y las prisas durante el desarrollo
> - Recortes en los esfuerzos en testing y calidad.
> - Descuidos

> [!NOTE] Los defectos en el software se dan en múltiples lugares
> - Especificación
> - Diseño
> - Implementación

> [!note] Deberíamos garantizar
> - Qué hace lo que debe hacer
> 	Comportamiento esperado
> - Que no hace lo que no debe hacer
> 	Comportamiento no esperado
> 
> > [!warning] ¿Para todas las combinaciones de factores?
> > **¡¡¡Infinito!!!**
## Error, defecto y fallo

![[error-efecto-fallo.png]]

> [!NOTE] Error
> Acción humana que produce un resultado incorrecto.

> [!NOTE] Defecto
> Es la manifestación de un error. 
> Es un *desperfecto* en un componente/sistema que puede causar que el software no realice su función requerida

> [!NOTE] Failure
> Desviación en un componente o sistema respecto de su comportamiento esperado.
## Contexto

![[Pasted image 20251203105500.png]]

> [!important] Conseguir calidad implica:
> - Hemos hecho las cosas correctamente:
> 	El producto satisface los requisitos funcionales, de rendimiento (explícitos) y de calidad (implícitos).
> - Hemos hecho el sistema correcto:
> 	Los requisitos corresponden a las necesidades del usuario.

> [!important] ¿Para quién?
> - Usuario
> - Cliente
> - Desarrollador
> - Tester

## Definición de calidad

Algunas definiciones de calidad podrían ser las siguientes:
- Ability of a product, service, system, component, or process to meet customer or user needs, expectations, or requirements (ISO/IEC 24765:2009 Systems and software engineering vocabulary).
- The totality of characteristics of an entity that bear on its ability to satisfy stated and implied needs (ISO/IEC 9126-1:2001 Software engineering -- Product quality -- Part 1: Quality model).
- Definición informal (empresa de automoción): Filosofía, éxito de negocio, satisfacción del cliente (interno y externo), involucrar a todos, mejora continua (procesos, productos y servicios), y por tanto, coste.

> [!NOTE] Calidad del producto
> Grado en el que el producto software cumple los requisitos y necesidades.

> [!NOTE] Calidad del proceso
> En qué medida se sigue el proceso y si se cumplen los estándares.

## Algunas cifras

![[Pasted image 20251203105853.png]]

![[Pasted image 20251203105908.png]]
[^1]
[^2]![[Pasted image 20251203110039.png]]

![[Pasted image 20251203110242.png]]

![[Pasted image 20251203110246.png]]

![[Pasted image 20251203110309.png]]

## Verificación y Validación

> [!info] Verificación
> Confirmación a través de evidencias objetivas de que los requisitos han sido satisfechos. 

> [!info] Validación
> Confirmación a través de evidencias objetivas de que los requisitos para un uso específico o de una aplicación han sido satisfechos.
> En el contexto del ciclo de vida del software, consiste en una serie de actividades que tienen como objetivo asegurar que el sistema es capaz de satisfacer su uso esperado y los objetivos.

![[Pasted image 20251203110820.png]]








































[^1]: World Quality Report 12th edition, 2020-2021. Capgemini, Sogeti, Micro Focus
[^2]: World Quality Report 10th edition, 2018-2019. Capgemini, Sogeti, HP
