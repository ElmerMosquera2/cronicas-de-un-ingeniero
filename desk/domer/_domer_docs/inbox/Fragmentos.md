Documento de producto, fase.

La idea es representar componentes de valor llamamos fragmentos `<fragment>` en un formato extricto predefinido resumido.

- La adr puede expresarse en una frase, el porque ya esta en la adr.

Por lo tanto un <fragmento> es un conjunto de requisitos funcionales, no funcionales o de información. Que representan una característica del sistema.

Ejemplo:

El flujo de la app es:

inicio -> login/registro -> tablero (estudiante, instructor, soporte, biblioteca)

Los dominios propios del fragmento son:

1. Modelo de acceso de interfases cliente.
2. Acceso segun rol.
3. Denegacion de acceso sin rol correspondiente.

No implica adr micro tales como "gestor de autenticacion"  que si bien hace parte del sistema es delegable, el fragmento representa el comportameniento macro (en este caso) de navegar entre ventanas, que las ventanas enten bien construidas con el metodo de autenticacion correspondiente no es de dominio del fragmento.

Los fragmentos son lineales segun el flujo del sistema, aunque segun modelo el desarrollo puede paralizarse. 