## ACTIVIDAD 3

### Función de `express.static('public')` en el servidor
Sirve para que el servidor entregue archivos estáticos (HTML, CSS, JS) desde la carpeta `public`.

### Comparación con `app.get('/ruta', …)`
`app.get()` requiere definir manualmente cada ruta; `express.static()` lo hace automático para archivos públicos.

---

### Flujo de un mensaje táctil

**Envío desde el móvil:**  
La función `touchMoved()` recopila las coordenadas y las envía con `socket.emit('message', data)`.

**Recepción en el servidor:**  
El servidor escucha con `socket.on('message', ...)` y recibe los datos.

**Acción del servidor:**  
El servidor reenvía los datos a otros clientes con `socket.broadcast.emit('message', message)`.

**Recepción en el escritorio:**  
El mensaje llega a los clientes de escritorio gracias al `broadcast.emit`.

---

### ¿Por qué `socket.broadcast.emit`?
Porque así se excluye al emisor.  
- `socket.emit`: solo al emisor.  
- `io.emit`: a todos.  
- `broadcast.emit`: a todos menos al emisor.

---

### ¿Quién recibe el mensaje retransmitido?
Todos los clientes conectados, excepto quien lo envió (por ejemplo, los escritorios si lo envió un móvil).

---

### Mensajes `console.log` en el servidor
Muestran información útil:  
- Nuevo cliente conectado  
- Mensaje recibido  
- Cliente desconectado
