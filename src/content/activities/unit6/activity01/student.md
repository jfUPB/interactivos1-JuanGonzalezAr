## Actividad 1

### ¿Qué ocurrió en la terminal cuando ejecutaste `npm install`? ¿Cuál crees que es su propósito?

Cuando ejecuté `npm install`, la terminal comenzó a descargar e instalar paquetes. Este comando sirve para instalar las dependencias que el proyecto necesita, que están definidas en el archivo `package.json`.

---

### ¿Qué mensaje específico apareció en la terminal después de ejecutar `npm start`? ¿Qué indica este mensaje?

Después de ejecutar `npm start`, apareció el mensaje:

Server listening on http://localhost:3000
User connected


Esto indica que el servidor se inició correctamente y está listo para recibir conexiones en el puerto 3000.

---

### Describe lo que ves inicialmente en page1 y page2 en tu navegador

- En http://localhost:3000/page1, vi una página con fondo claro y un círculo que se podía mover.
- En http://localhost:3000/page2, vi una página similar, sincronizada con la primera. Mostraba una línea conectando elementos que cambiaba según la posición del círculo de page1.

---

### ¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?

Aparecieron mensajes como:
Client connected



---

### Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador y en la terminal del servidor?

- Cuando moví el círculo en una de las páginas, también se actualizó en la otra. Las dos páginas están sincronizadas en tiempo real.
- En la consola del navegador apareció:
Object height: 671 width: 395 x: -16 y: 55

- En la terminal del servidor seguían apareciendo mensajes indicando que los clientes estaban conectados.


