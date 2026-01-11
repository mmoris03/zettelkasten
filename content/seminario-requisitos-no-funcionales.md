
> [!NOTE] ¿Qué son los requisitos no funcionales?
> Los requisitos no funcionales en ingeniería de requisitos de software describen los **criterios de calidad y restricciones del sistema que no están directamente relacionados con funcionalidades específicas que el software debe realizar**, sino con cómo debe comportarse o las condiciones en las que debe operar.

> [!example] Ejemplos de requisitos no funcionales
> Estos requisitos suelen definir atributos de calidad del sistema como:
> - Rendimiento
> - Seguridad
> - Usabilidad
> - Fiabilidad
> - Escalabilidad
> - Mantenibilidad
> - ...

> [!NOTE] ¿Por qué son importantes?
> **Ignorar los requisitos no funcionales** en esta fase, supone identificar el error y remediarlo en fases posteriores, donde será mucho **más costoso**.

> [!important] Se deben definir en términos **precisos** y **cuantificables**
> > [!example] Ejemplo de requisito mal definido
> > *RNF1. El sistema debe tener un tiempo de respuesta aceptable.*
> > 
> > Al definirlo de forma **imprecisa**, el sistema tiene un tiempo de respuesta de 15 segundos en la fase de desarrollo, pero el sistema necesitaba que fuera de 5 segundos para que no se formasen colas.
> > - Resultado
> > El usuario final decide no utilizar el sistema y el proyecto.
> > - Posible corrección
> > *RNF1. El sistema debe tener un tiempo de respuesta de un máximo de 5 segundos.*
## Clasificación según Kotonya-Sommerville
![[Pasted image 20251204204127.png]]

## Tipos de requisitos no funcionales

> [!NOTE] Requisitos de producto
> Estos requisitos especifican cómo debe comportarse el software.
> - Requisitos de **usabilidad**.
> - Requisitos de **eficencia**.
> - Requisitos de **fiabilidad**.
> - Requisitos de **portabilidad**.

## Ejercicio: Clasificar requisitos de producto

| Requisito no funcional de producto                                                                                                 | Tipo         |
| ---------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| RNF1. La tasa de errores cometidos por el usuario deberá ser menor del 1% de las transacciones totales ejecutadas en el sistema.   | Usabilidad   |
| RNF2. El sistema será compatible con Windows 10, Mac y Linux.                                                                      | Portabilidad |
| RNF3. El sistema debe tener una probabilidad de no disponibilidad del 0,01% de las veces en que un usuario intente accederlo.      | Fiabilidad   |
| RNF4. El sistema debe ser capaz de operar adecuadamente con hasta 100.000 usuarios con sesiones concurrentes.                      | Eficiencia   |
| RNF5. El tiempo para iniciar o reiniciar el sistema no podrá ser mayor a 5 minutos.                                                | Eficiencia   |
| RNF6. La probabilidad de fallo del sistema no podrá ser mayor a 0,05%.                                                             | Fiabilidad   |
| RNF7. Los datos modificados en la base de datos deben ser actualizados para todos los usuarios que acceden en menos de 2 segundos. | Eficiencia   |
| RNF8. El tiempo de aprendizaje del sistema por un usuario deberá ser menor a 4 horas.                                              | Usabilidad   |
> [!NOTE] Requisitos de organizacionales
> Estos requisitos derivan de políticas de la empresa cliente y de la empresa desarrolladora.
> - Requisitos de **entrega**.
> - Requisitos de **implementación**.
> - Requisitos de **estándar**.

> [!NOTE] Requisitos externos
> Requisitos derivados de factores externos al sistema, por ejemplo, requisitos necesarios para que el sistema sea aprobado por un organismo regulador.
> - Requisitos de **interoperabilidad**.
> - Requisitos de **éticos**.
> - Requisitos de **legales**.

| ¿Requisito no funcional organizacional o externo?                                  | Tipo           |
| ---------------------------------------------------------------------------------- | -------------- |
| RNF9. El sistema debe cumplir el estándar ISO 27001.                               | Organizacional |
| RNF10. El sistema mostrará a los usuarios información anonimizada de los clientes. | Externo        |
| RNF11. El sistema debe emplear Wikidata para construir las preguntas.              | Organizacional |
## Atributos de calidad

> [!NOTE] ¿Cuáles de estas categorías se corresponderían con atributos de calidad?
> 

## Ejercicio: Identificar requisitos no funcionales

Perteneces al equipo de análisis de requisitos de un sistema de mensajería instantánea. En dicho software, se deben permitir tener chats entre 2 usuarios, chats en grupos y difusiones.
Objetivos de la aplicación:
- Mensajería en tiempo real.
- Autenticación y autorización de los usuarios.
- Seguridad y privacidad de los datos.
- Recuperación de los datos perdidos
- Amigable para los usuarios.

**Identifica requisitos no funcionales que creas que debe tener el software descrito.**