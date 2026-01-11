# Casos de uso

> [!NOTE] ¿Qué es un caso de uso?
> Un caso de uso es la **descripción** de una **funcionalidad** del sistema, y cómo interactúa dicho sistema con actores externos o actores.
> Un caso de uso se compone de varios escenarios.

> [!NOTE] ¿Qué es un escenario?
> Cada secuencia de interacciones posible de un caso de uso es un escenario.
> Un caso de uso, por tanto, contiene todos los escenarios posibles para que el actor primario consiga su objetivo.
> En definitiva, un escenario es una secuencia específica y completa de acciones que se ejecutan cuando un actor interactúa con el sistema para lograr un objetivo.
> - Es concreto, no genérico.
> - Muestra cada paso del camino (desde la condición inicial hasta la postcondición).
> - No mezcla variantes: cada escenario representa un único flujo completo.
> Si puedes leer el escenario como una "historia" que empieza, se desarrolla y termina, estás documentando un escenario correctamente.

> [!NOTE] Caso de uso VS Escenario
> 

| Concepto    | Qué es                                                                           | Contiene                                                   |
| ----------- | -------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Caso de uso | Describe todo el comportamiento del sistema para alcanzar un objetivo del actor. | Varios escenarios (básico, alternativos, excepciones).     |
| Escenario   | Es una ejecución concreta (una “historia” específica) de ese caso de uso.        | Una única secuencia de pasos desde el inicio hasta el fin. |

> [!NOTE] ¿Qué es un actor?
> Una persona, grupo de personas o incluso otro sistema. Cada caso de uso está asociado con el objetivo de un actor, que es el actor primario.

> [!NOTE] ¿Stakeholders vs actores?
> Todos los actores son stakeholders, pero no todos los stakeholders interactúan con el sistema y no son, por tanto, actores.
> > [!important] Actor != usuario.
## Diagrama de casos de uso: Biblioteca
## Formato tabular casos de uso

| Campo               | Qué representa                                                                     | Ejemplos                                                                                                                                                                                                                                  |
| ------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Nombre              | Identificar de forma única y representativa el caso de uso.                        | Usa un verbo + objeto, por ejemplo: *Comprar producto*, *Registrar usuario*, *Reservar cita médica*.                                                                                                                                      |
| Descripción         | Resumen breve del propósito del caso o escenario. Explica **qué se busca lograr**. | *Permite al cliente adquirir un producto y recibir confirmación de<br>pedido.*                                                                                                                                                            |
| Actores             | Roles que interactúan con el sistema (actores, otros sistemas,…).                  | *Cliente, Sistema de pasarela de pagos.*                                                                                                                                                                                                  |
| Condición de inicio | Evento o acción que dispara el caso de uso (el “trigger”).                         | *El cliente hace clic en el botón ´Pagar´.*                                                                                                                                                                                               |
| Precondiciones      | Estado previo que debe cumplirse antes de ejecutar el<br>escenario.                | *El cliente tiene sesión iniciada y un carrito con productos disponibles.*                                                                                                                                                                |
| Postcondiciones     | Estado final que se espera tras la ejecución (éxito o fallo).                      | *Pedido creado y pago validado.* / *No se crea pedido si el pago falla.*                                                                                                                                                                  |
| Flujo normal        | Secuencia paso a paso que describe la *ruta principal* del<br>escenario.           | Numera los pasos alternando actor y sistema, por ejemplo:<br>*1. El cliente selecciona “Pagar”.*<br>*2. El sistema muestra resumen del pedido.*<br>*3. El cliente introduce datos de pago.*<br>*4. El sistema valida el pago y confirma.* |
| Flujos alternativos | Variaciones del flujo normal donde la meta se cumple por<br>otro camino.           | *(3') El cliente elige PayPal en lugar de tarjeta.*                                                                                                                                                                                       |
| Excepciones         | Desviaciones por errores o condiciones anómalas que<br>impiden completar la meta.  | *(4’) El sistema muestra mensaje y ofrece reintentar..*                                                                                                                                                                                   |
## Formato tabular escenarios

| Campo               | Qué representa                                                                              | Cómo complementarlo correctamente                                                                                                      | Ejemplo (Reservar mesa)                                                                                            |
| ------------------- | ------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Nombre              | Identificar de forma única y representativa el escenario.                                   | Usa un verbo + objeto, por ejemplo:                                                                                                    | *Compra producto anulada*, *Registrar<br>usuario fallido*, *Cambiar fecha de cita médica anteriormente reservada*. |
| Descripción         | Breve resumen del propósito del escenario. Explica qué sucede en esta secuencia particular. | Resume la situación concreta sin detallar los pasos. Indica si es flujo normal, alternativo o excepción.                               | *El sistema no encuentra disponibilidad en la fecha solicitada y propone una fecha alternativa.*                   |
| Actores             | Roles que intervienen en el escenario<br>(personas, sistemas o dispositivos).               | Menciona el actor primario y, si aplica, actores secundarios que participan en la secuencia.                                           | *Cliente (primario)*, *Sistema de reservas*                                                                        |
| Condición de inicio | Evento o acción que dispara el inicio del escenario.                                        | Describe qué hace el actor o qué evento ocurre para que comience este flujo.                                                           | *El cliente selecciona la opción ‘Reservar mesa’*.                                                                 |
| Precondiciones      | Situaciones o requisitos que deben cumplirse antes de ejecutar el escenario.                | Define el estado previo necesario para que el flujo pueda iniciarse correctamente.                                                     | *El sistema tiene conexión al calendario de disponibilidad*.                                                       |
| Postcondiciones     | Estado del sistema y de los actores una vez finalizado el escenario.                        | Explica el resultado final del escenario (éxito o fracaso).                                                                            | *Reserva creada y confirmación enviada al cliente*.                                                                |
| Secuencia           | Secuencia de acciones que muestran la interacción entre actor(es) y sistema.                | Redacta los pasos en orden cronológico, alternando acciones del actor y respuestas del sistema. Cada paso debe ser claro y observable. | *1) El cliente solicita una reserva. 2) El sistema verifica disponibilidad. 3) El cliente confirma la reserva.*    |
