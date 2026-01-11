# Técnicas de obtención de requisitos
## Introducción

> [!NOTE] Educción u obtención de requisitos
> Actividad de obtener de las fuentes de información apropiadas (por ejemplo distintos *stakeholders*) la información básica que necesitamos de ellas para identificar y documentar los requisitos de los *stakeholders*.

> [!NOTE] Nota sobre la traducción
> "Educir" significa según la RAE: "sacar algo de otra cosa, deducir"
> Es la traducción más literal del inglés "elicit" ("requirements elicitation").
> Como es una palabra poco conocida, suele utilizarse en su lugar "obtener" u otro sinónimo.
> > [!warning] "Elicitar" no es una palabra que exista en español, no deberíamos utilizarla.

> [!important] Normalmente es el proceso más crítico y difícil de realizar
> La razón de su dificultad es que es una actividad más "humana" que técnica.
> Además, los *stakeholders*:
> - Tienen perfiles muy variados.
> - Pueden ser difíciles de identificar o ser muchísimos.
> - Pueden ser más o menos colaborativos.
> - A veces nos redirigirán a otras fuentes.
> - ...
> 

> [!NOTE] Pasos lógicos del proceso de educción u obtención de requisitos.
> 1. Identificar las fuentes de información de donde obtener los requisitos.
> 2. Seleccionar una técnica adecuada para cada fuente.
> 3. Preparar y planificar la obtención de información de las diferentes fuentes.
> 4. Ejecutar la planificación anterior.

> [!NOTE] Técnicas de obtención de requisitos.
> Existen técnicas específicas para realizar esta actividad que tienen poco que ver con la práctica habitual del desarrollo de software (muchas vienen de las ciencias sociales).
> Requieren preparación y planificación, ejecutarlas es el último paso.
## Fuentes de requisitos

> [!NOTE] Categorías principales de fuentes de requisitos
> - *Stakeholders*
> - Documentos
> - Sistemas o software existente

> [!NOTE] Proceso habitual de identificación de posibles fuentes de requisitos
> Identificar las fuentes de información de donde obtener los requisitos es la primera tarea de la educción de requisitos, pero no basta con hacerlo una sola vez puesto que, según vayamos avanzando con la obtención de requisitos, pueden ir apareciendo nuevas fuentes de requisitos que habrá que incorporar.
> Por todo ello, el proceso habitual es:
> 1. Se identifican las fuentes más evidentes, con las que se comienza.
> 2. Se van buscando otras fuentes de requisitos adicionales de manera sistemática a partir de las anteriores.
> 	Uno de los posibles objetivos "indirectos" de la obtención de requisitos es identificar esas fuentes adicionales de información.
### Stakeholders

> [!NOTE] Identificación y selección de *stakeholders*
> En primer lugar, solemos identificar roles o grupos (usuarios del departamento X, clientes, administradores) de *stakeholders*, pero es necesario ponerles "nombre y apellidos" para poder trabajar con ellos porque, al final, tratamos con personas concretas, no grupos abstractos.
> Este proceso consta de 3 pasos:
> 1. Identificación de grupos, roles e individuos "obvios".
> 	Aquellos que se identifican de manera sencilla por experiencia previa, primer contacto con el proyecto etc.
> 2. Búsqueda sistemática de más grupos o roles de *stakeholders*.
> 	- Revisar listas de grupos/roles de *stakeholders* habituales.
> 	> [!example] Grupos/roles de stakeholders habituales
> 	> - IREB: usuarios directos del sistema, gestores/directivos, clientes, personal TIC relacionado, entidades reguladoras, la competencia...
> 	> - ISO/IEC/IEEE 29148: usuarios, adquirientes (compradores), personal TIC relacionado, entidades reguladoras...
> 	- Revisar el organigrama de la empresa u organización (departamentos, responsables...)
> 	- Revisar la documentación corporativa sobre los procesos relacionados con el *software* y su ciclo de vida.
> 	- Preguntar explícitamente a los *stakeholders* ya identificados.
> 	- ...
> 3. Identificación de *stakeholders* concretos
> 	Como no es posible tratar con cientos de *stakeholders*, habrá que identificar personas concretas de cada grupo/rol con las que tratar (idealmente los más colaborativos e informados).
> > [!important] Lista de *stakeholders*
> > Una vez identificados y seleccionados, hay que documentar la lista de *stakeholders*.
> > Cabe destacar que:
> > - Es muy útil agrupar a los *stakeholders* por tipo (por ejemplo internos/externos).
> > - Se debe incluir la información mínima:
> > 	- id
> > 	- nombre
> > 	- rol
> > 	- contacto
> > 	- disponibilidad
> > 	- relevancia
> > 	- área de experiencia
> > 	- interés en el proyecto
> > - Hay un tipo especial de *stakeholder*: el *usuario final* (que usará el *software*).
> > 	- Pueden ser internos o externos (pueden documentarse aparte).
> > 	- No siempre pueden ser incluidos como *stakeholders* concretos (especialmente los externos).
> > 		Habrá que buscar formas alternativas de identificar sus necesidades (por ejemplo a través de otros *stakeholders* que sí están disponibles se identifican sus necesidades y se documentan como propias).
### Documentos

> [!NOTE] Ejemplos de documentos que son posibles fuentes de requisitos
> - Legislación, normativa interna o estándares de obligado cumplimiento.
> - Planes estratégicos del adquiriente o estrategia TIC.
> - Documentación del anteproyecto: estudios de necesidad, viabilidad, PoC...
> - Especificaciones de requisitos de sistemas previos.
> - Manuales de usuario de sistemas previos o de la competencia.
> - Documentación sobre el proceso de negocio relacionado.
> - Documentación de interfaces con otros sistemas.
> - Documentos generados en el proceso de negocio relacionado.

> [!NOTE] Consideraciones sobre los documentos
> - Pueden ser internos o externos, públicos o confidenciales.
> - Hay que tener en cuenta que no todos tendrán la misma relevancia, fiabilidad o vigencia.
> - Es habitual comenzar la educción de requisitos leyendo documentos.
> 	Aportan contexto, requisitos de alto nivel, dan información sobre otras fuentes de requisitos...
> 	En general, ayudan a preparar la obtención de requisitos de otras fuentes.

> [!NOTE] Gestión de los documentos
> Hay que registrar todos los documentos de manera similar a lo visto para los *stakeholders*:
> - id
> - nombre
> - descripcion
> - *stakeholder* asociado (normalmente)
### Sistemas o software existente

> [!NOTE] Consideraciones sobre los sistemas o software existentes
> - Analizar *software* existente (o su documentación) puede ser más rápido y preciso que obtener la misma información de los *stakeholders*.
> - Hay que documentar adecuadamente el *software* usado como fuente de requisitos.
> 	Posiblemente, el software estará asociado a algún *stakeholder* o documento previamente identificado, lo cual debe ser documentado.

> [!example] Ejemplos de sistemas o software existente que son posibles fuentes de requisitos
> - *Software* con el que el nuevo sistema debe interaccionar.
> 	Sobre todo la especificación de sus interfaces.
> - Plataformas o ecosistemas en los que debe integrarse.
> 	- Restricciones técnicas
> 	- Usabilidad/UX
> 	- Facilidades disponibles
> 	- ...
> - *Software* que va a ser reemplazado por el nuevo sistema.
> 	No solo funcionalidad: migración de datos, fase de transición...
> - *Software* de la competencia o con funciones similares.
## Técnicas de análisis de documentos y de software
### Análisis de documentación para educir requisitos

> [!NOTE] Lectura basada en perspectiva
> No conviene ponerse a leer sin más (excepto documentos muy genéricos, para conocer el contexto).
> Es más útil una lectura basada en perspectiva:
> 1. Antes de empezar a leer, identificamos desde qué perspectiva vamos a realizar la lectura:
> 	- Identificar requisitos funcionales de un usuario particular o de una función concreta.
> 	- Buscar requisitos no funcionales de algún tipo (seguridad, rendimiento...).
> 	En definitiva, tener claro qué información estamos buscando.
> 2. Leemos el documento atendiendo a la perspectiva elegida.
> 	Anotamos la información relevante que encontremos.
> 	> [!NOTE] El proceso puede repetirse para distintas perspectivas.
> 	> Si hay varios analistas, cada uno puede tomar una perspectiva diferente.
> 	> En todo caso, es más eficiente hacer varias lecturas con perspectiva que una "general".
> 3. El resultado será un documento de notas (o similar).
> 	Las notas serán requisitos obtenidos u otra información relevante.
> 	Se registrará para cada nota su origen (por ejemplo, la página del documento donde se halló la información).

> [!warning] Riesgo de documentación obsoleta o errónea.
> En algunos casos habrá que contrastar los requisitos obtenidos.
### Reutilización de requisitos

> [!important] Es un caso especial de análisis de documentación.

> [!NOTE] Especificaciones de requisitos de otros sistemas
> Puede ser útil investigar si hay disponibles especificaciones de sistemas previos o similares que nos sirvan para encontrar listas de requisitos potencialmente reutilizables para nuestro sistema:
> - Pliegos de preescripciones técnicas para licitaciones (PPT).
> 	Son básicamente especificaciones de requisitos.
> - Otros SRS de la misma organización.
> 	Aunque sean para sistemas diferentes, pueden incluir requisitos comunes (por ejemplo requisitos no funcionales que aplican a cualquier *software* de esa organización).
> 
> > [!warning] El resultado serán requisitos potenciales
> > Habrá que utilizar solo los que realmente nos sirvan o adaptarlos a nuestro contexto.
### Análisis de *software* existente

> [!important] Suele hacerse con el *software legacy* al que debe reemplazar el nuevo sistema.

> [!NOTE] El primer paso es determinar el objetivo del análisis
> - Funcionalidades no identificadas previamente.
> - Aspectos a cambiar o fallos.
> - Roles o tipos de usuario actuales.
> - Estilo de IU cómodo para los usuarios
> - ...

> [!NOTE] Objetos a analizar
> - Documentación del software (manuales, especificaciones...)
> - El *software* en un entorno de pruebas
> - El código fuente
> 	Si lo anterior no es suficiente para obtener cierta información.

> [!NOTE] Resultados del análisis de *software* existente
> - Requisitos potenciales.
> - Información útil para obtener requisitos:
> 	- Tipología de usuarios.
> 	- Secuencia de interacción.
> 	- Estructura de la información a gestionar.
> 	- Requisitos o funcionalidades ignoradas hasta ese momento.
> 	- ...
## Técnicas para pedir información

Se basan en hacer preguntas a algún *stakeholder*:
- Preguntas **cerradas**
	Con respuestas predefinidas (SI/NO, lista donde elegir, valor cuantitativo limitado...).
- Preguntas **abiertas**
	Requieren un análisis cognitivo.

> [!important] En ingeniería de requisitos las más habituales son las preguntas abiertas.

Hay dos técnicas principales:
- Entrevistas
- Cuestionarios
### Entrevistas

> [!important] Es la técnica más usada en la educción de requisitos.

> [!NOTE] Preparación de las entrevistas
> - Identificar al *stakeholder* objeto de la entrevista.
> - Definir los objetivos de la entrevista y sus criterios de calidad (permiten verificar si la entrevista fue un éxito o no).
> - Preparar una guía para la entrevista
> 	- Puntos a tratar
> 	- Preguntas a realizar
> - Organizar la entrevista
> 	- Lugar
> 	- Hora
> 	- Duración máxima
> 	- Si se va a grabar o se tomarán las notas (¿quién las toma?)
> 	- ...

> [!NOTE] Resultados de la entrevista
> Una vez analizada la información obtenida:
> - Requisitos de cualquier tipo.
> - Información adicional a los ya identificados.
> - Nuevas fuentes o atributos de las conocidas, etc.

> [!NOTE] Consideraciones generales:
> - Lo ideal es entrevistar a un solo *stakeholder*, no a muchos a la vez.
> - El ingeniero de requisitos es quien dirige la entrevista:
> 	- Debe ser educado y claro, buscando la empatía con el *stakeholder*.
> 	- Debe verificar que se ha entendido la respuesta.
> 	- Debe fijarse no solo en lo que responde el *stakeholder*, sino en cómo lo hace.
> - 20-40 minutos es lo recomendado, nunca más de una hora.
> 	El lugar es importante para evitar interrupciones (presencialidad > videoconferencia).
> - Opcionalmente, se puede dar un guión o pregunta abiertas previamente al entrevistado.
> 	Para que vaya preparado o tenga documentación relevante a mano.
> - Pasar un "acta" al *stakeholder* para que lo valide, confirmando así la información obtenida.
### Cuestionarios

> [!NOTE] Formato de los cuestionarios
> Lista de preguntas que se envían a los *stakeholders* para que contesten y devuelvan la información.

> [!NOTE] Consideraciones sobre los cuestionarios
> - Pueden ser formularios web, email, papel...
> - Pueden hacerse a muchos *stakeholders* a la vez, aunque no es habitual en la práctica.
> - Las preguntas pueden ser:
> 	- Cerradas:
> 		Útiles para verificar hipótesis, requisitos previamente educidos o potenciales.
> 	- Abiertas:
> 		- Son las más habituales
> 		- Se requiere más tiempo para procesar las respuestas.
> 		- Alternativa a la entrevista cuando no hay acceso directo a los *stakeholders* o solo necesitamos información muy concreta.
> > [!important] Es importante preparar bien las preguntas
> > - Seguir un orden lógico
> > - Cubrir todas las posibilidades
> > - Ser claros
> > - ...
> > No hay margen para la ambiguedad porque no estaremos presentes cuando contesten.
## Técnicas de observación

Se basan en observar a los *stakeholders* (normalmente usuarios) realizar su trabajo habitual, relacionado con el *software* a construir.

> [!important] Antes de observar, hay que conocer algo el contexto o dominio.
> Si no, no se entenderá lo que se observe o se tenderá a simplificarlo.

> [!NOTE] Técnicas principales
> Hay tres técnicas principales que diferen en la posición y actitud del observador (el ingeniero de requisitos) y pueden incluso combinarse.
> - Trabajo/observación de campo.
> - Inmersión como aprendiz.
> - Indagación contextual.

> [!important] Hay que preparar la observación
> Hay que tener clara la técnica o técnicas, los objetivos... así como documentar los resultados.

> [!NOTE] Resultados de la observación
> Los requisitos obtenidos deben ser validados por otros medios.

### Trabajo/observación de campo

> [!NOTE] Trabajo/observación de campo
> Consiste en observar a los *stakeholders* realizar su trabajo habitual **sin interferir en él**.

> [!NOTE] Consideraciones
> - Puede que ni sepan que les estamos observando.
> - La observación puede ser presencial o no.

> [!NOTE] Utilidad principal del trabajo/observación de campo
> Descubrir requisitos o aspectos de los mismos implícitos u ocultos consecuencia de que:
> - Hay información que a los *stakeholders* les resultan tan obvia que no la verbalizan si no se les pregunta.
> 	Esta información puede ser crucial para el éxito del proyecto porque hay requisitos que no se verbalizan expresamente pero que si faltan en el nuevo sistema los usuarios lo considerarán un fallo.
> - Muchas veces, la norma o la teoría estipula algo, pero la práctica va por otro lado.
> 
> También sirve para descubrir la "cultura de la empresa", normalmente inconscientes para los implicados.
### Inmersión como aprendiz

> [!NOTE] Inmersión como aprendiz
> El ingeniero de requisitos toma el rol de "aprendiz":
> - El *stakeholder* le introduce en el trabajo y le forma como si fuera un nuevo empleado.
> - El ingeniero de requisitos no se limita a observar o preguntar:
> 	Realiza el trabajo, lo que le da una comprensión diferente.

> [!NOTE] Preparación de la inmersión como aprendiz
> - Identificar qué rol o tipo de usuario va a asumirse.
> - Seleccionar el maestro.
> - Definir los objetivos.
> - Planificar el tiempo de la inmersión.

> [!NOTE] Utilidad de la inmersión como aprendiz
> - Es una buena forma de conocer el contexto.
> - Permite identificar las dificultades y problemas actuales que el *software* a construir debe resolver.
> - Como el trabajo de campo, facilita identificar información o prácticas inconscientes o implícitas.
### Indagación contextual

> [!NOTE] Indagación contextual
> Combina la observación y la entrevista y consiste en que el ingeniero de requisitos observe a un usuario (o varios) desarrollar algún aspecto de su trabajo mientras dialoga con él (o ellos) para profundizar en los detalles del trabajo.

> [!NOTE] Preparación de la indagación contextual
> - Identificar objetivos
> - Seleccionar usuarios
> - Planificar cómo recoger la información (lista de puntos, grabación...)
> Normalmente, hay que haber hecho previamente entrevistas, observación... antes de poder identificar usuarios y objetivos de una indagación contextual.

> [!NOTE] Ventajas
> - El diálogo con los usuarios permite obtener más información y más precisa que la simple observación.
> - La observación evita al usuario tener que explicarse prolijamente en una entrevista, lo que le puede resultar difícil por la ausencia de contexto.

> [!NOTE] Desventajas
> - No siempre es posible de realizar.
> - Hay riesgo de que el usuario nos dé información incorrecta (consciente o inconscientemente).
## Técnicas de trabajo colaborativo

Se basan en la colaboración de varios *stakeholders* en la tarea de educir requisitos.

> [!important] La técnica más común en ingeniería de requisitos es el taller.
### Taller

> [!NOTE] Taller
> Reunión de varios *stakeholders* o expertos que trabajan juntos para definir, crear o refinar requisitos de usuario.

> [!NOTE] El ingeniero de requisitos asume el rol de **facilitador** 
> - **Preparación**
> 	- Seleccionar participantes.
> 	- Lugar y horario.
> 	- Marcar los objetivos del taller y el plan de trabajo.
> 	- ...
> - **Inicio**
> 	- Dar la bienvenida.
> 	- Explicar los objetivos y el plan de trabajo.
> 	- Marcar reglas.
> 	- ...
> - **Dirección**
> 	- Animar a la participación.
> 	- Vigilar el cumplimiento de objetivos y reglas.
> 	- ...
> - **Cierre**
> 	- Agradecer la participación.
> 	- Explicar los siguientes pasos o cómo se van a tratar los resultados.
> 	- ...

> [!NOTE] Utilidad de los talleres
> - Cuando los requisitos no están claramente prefijados y hay que tomar decisiones sobre ellos en base a la experiencia de los *stakeholders*.
> - Facilita que lleguen a acuerdos en el mismo taller, lo que le ahorra trabajo al ingeniero de requisitos.

> [!NOTE] Dificultades de los talleres
> Implican muchos recursos (tiempo, personas, dinero...), por lo que requieren un patrocinador que lo impulse.

> [!NOTE] Otras técnicas de trabajo colaborativo
> - Grupos focales
> 	Orientados a obtener opiniones, percepciones, actitudes y sugerencias sobre productos o servicios relacionados con el *software* a construir.
> - Uso de redes sociales o *software ad hoc* para que un gran número de personas aporte opiniones, ideas, soluciones... relacionadas con el *software* a construir.
## Pautas de uso

Seleccionar las técnicas adecuadas de educción de requisitos y en qué orden aplicarlas depende de muchos factores:
- Disponibilidad de los *stakeholders* o fuentes.
	No siempre están disponibles cuando mejor conviene.
- Limitaciones de tiempo o recursos.
	Puede limitar el número de entrevistas.
- El propio contexto o dominio.
	Puede ser inviable hacer observación u organizar talleres.

> [!NOTE] Pautas generales para seleccionar las técnicas de educción
> - Reunión de arranque del proyecto (*kick-off meeting*).
> 	Sirve para conocer el contexto general y el alcance y también para identificar fuentes de requisitos.
> 	No es una entrevista como tal pero algo se saca...
> - ¿Qué hacer en primer lugar?
> 	Si hay, comenzar por el análisis de:
> 	- Documentación
> 	- *Software legacy* que debe ser reemplazado.
> 	- *Software* de la competencia que debe ser imitado.
> - ¿Cuándo recurrir a cuestionarios frente a entrevistas?
> 	- Si no podemos hacer una entrevista.
> 	- Para confirmar requisitos potenciales.
> 	- Para pedir información específica y precisa.
> 	- Para obtener opiniones concretas de muchos *stakeholders* a la vez
> 	...
> 	**No es normal empezar por ellos porque requieren conocimiento previos del contexto o dominio.**
> - ¿Cuándo recurrir a técnicas de observación?
> 	- Vemos que nos falta información que nadie nos da.
> 	- Detectamos incoherencias entre documentos y práctica real o entre jefes y trabajadores...
> 		La observación es la mejor forma de descubrir conocimiento implícito.
> 	- No es posible "sacar" alos stakeholders de su lugar de trabajo.
> 		La indagación textual puede sustituir a la entrevista.
> 	- Si la usabilidad es muy importante.
> 	- Cuando los *stakeholders* tienen dificultades para explicar su trabajo o aportar información de manera precisa.
> - ¿Cuando recurrir a técnicas colaborativas?
> 	- Cuando no está muy claro qué se necesita, porque es algo nuevo.
> 	- Cuando las necesidades son subjetivas, para ayudar a alcanzar consensos.