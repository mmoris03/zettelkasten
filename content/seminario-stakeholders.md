# Stakeholders

> [!NOTE] ¿Qué son los stakeholders?
> Personas interesadas o implicadas en el proyecto, y en la especificación de requisitos.

> [!important] Es importante conocer las necesidades de los stakeholders para definir qué se debe construir.

> [!NOTE] Tipos de stakeholders
> - Internos
> > [!example] Ejemplos de stakeholders internos
> > - Empresa cliente
> > - Equipo de desarrollo
> > - ...
> - Externos
> > [!example] Ejemplos de stakeholders externos
> > - Clientes finales
> > - Inversores
> > - Competidores
> > - ...

> [!NOTE] ¿Por que es importante identificar stakeholders para la especificación de requisitos?
> Porque nos proporcionan diferentes puntos de vista.

> [!warning] Consecuencias de no identificar correctamente a los stakeholders
> No identificarlos correctamente podría implicar:
> - Insatisfacción
> - Errores en la identificación de requisitos
> 	Estos resultarán en errores en fases posteriores del proyecto.
> 	> [!example] Ejemplo de fase posterior del proyecto afectada
> 	> Diseño
## Documentación de los stakeholders

| ID  | Stakeholder | Descripción |
| --- | ----------- | ----------- |
| S1  |             |             |
| S2  |             |             |
| ... |             |             |
| SN  |             |             |

| ID  | Usuario | Descripción |
| --- | ------- | ----------- |
| U1  |         |             |
| U2  |         |             |
| ... |         |             |
| UN  |         |             |
## Ejercicio (1): Identifica los stakeholders

Eres el analista de un proyecto software en Asturias (IRMed) que tiene como objetivo es desarrollar un sistema de apoyo para la gestión de citas médicas en centros de salud. Se pretende que este proyecto sirva de apoyo para el personal de administración con el fin de reducir la carga de llamadas telefónicas y agilizar la respuesta.
Este software lo utilizarán tanto los usuarios como el personal de administración de los centros de salud, quienes se encargarán de confirmar las reservas o anularlas en caso de que surjan imprevistos. El software tendrá un usuario administrador, que se encargará de añadir los roles a los administrativos de los centros de salud, y de darles permisos en caso de que haya nuevas incorporaciones a dicho puesto de trabajo. El personal médico del centro (medicina, enfermería, etc.) tendrán acceso al calendario de reservas, pero no podrán hacer modificaciones. Todos usuarios podrán acceder al calendario de reservas, pero solo los que entren a la web con su número de la tarjeta sanitaria podrán realizar reservas.
El cliente indica que la página web debe ser fácil de usar para todas las personas, y deberá estar disponible tanto en español como en inglés.
### Tabla stakeholders

| ID  | Stakeholder                    | Descripción                                                                      |
| --- | ------------------------------ | -------------------------------------------------------------------------------- |
| S1  | Analista proyecto              | Encargado de realizar las tareas de planificación análisis y diseño del proyecto |
| S2  | Equipo desarrollo              | Encargado de programar, testear, desplegar y mantener la aplicación              |
| S3  | Administrador                  | Administrador del sistema                                                        |
| S4  | Personal médico                | Personal sanitario de los centros de salud                                       |
| S5  | Personal administrativo        | Personal de administración del centro de salud                                   |
| S6  | Conserjería de salud           | Cliente                                                                          |
| S7  | Proveedor de hosting           | Proveedor de hosting                                                             |
| S8  | Proveedor de nombre de dominio | Proveedor de nombres de dominio                                                  |
### Tabla usuarios

| ID  | Usuario                         | Descripción                                      |
| --- | ------------------------------- | ------------------------------------------------ |
| U1  | Usuario no registrado           | Usuario no registrado                            |
| U2  | Usuario administrador           | Usuario con funciones de gestión de roles        |
| U3  | Usuario personal administrativo | Usuario utilizado por el personal administrativo |
| U4  | Usuario personal médico         | Usuario utilizado por el personal médico         |
### Otras fuentes de información

> [!example] Ejemplo de leyes y normas
> RGPD

> [!example] Ejemplos de estándares
> Estándares de calidad ISO 9000

 > [!example] Ejemplos de documentación técnica, metodologías, etc...
 > - Pautas de accesibilidad
 > - WCAG
 > - Métrica V3