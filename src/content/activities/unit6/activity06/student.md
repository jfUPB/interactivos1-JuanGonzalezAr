## ACTIVIDAD 6

### Función del servidor Node.js
El servidor Node.js centraliza la comunicación entre los clientes, gestionando los datos y evitando que los clientes se comuniquen directamente entre sí.

---

### Diferencia entre `socket.emit()` y `socket.broadcast.emit()`
- `socket.emit()`: Envía un mensaje **solo al cliente que emite**.
- `socket.broadcast.emit()`: Envía el mensaje a **todos los demás clientes**, excepto al emisor.

---

### Comparación con comunicación serial

**Ventajas de Node.js / Socket.IO:**
- Comunicación **bidireccional** y **en tiempo real**.

**Desventajas de Node.js / Socket.IO:**
- Requiere **infraestructura** y **conexión a Internet**.

**Ventajas de la comunicación serial:**
- **Simplicidad**.
- No depende de una red.

**Desventajas de la comunicación serial:**
- **Alcance limitado**.
- Solo sirve para **aplicaciones simples**.

---

### Rol del protocolo HTTP y Socket.IO
- **HTTP**: Maneja las **solicitudes iniciales** del cliente (por ejemplo, al cargar la página).
- **Socket.IO**: Mantiene la **conexión activa** para la comunicación en tiempo real entre el servidor y los clientes.

---

### Lo más sorprendente sobre la comunicación en red
La **simplicidad y eficiencia** de **Socket.IO** para gestionar eventos en tiempo real entre múltiples clientes, sin necesidad de lidiar con las complejidades de WebSockets o protocolos de bajo nivel.
