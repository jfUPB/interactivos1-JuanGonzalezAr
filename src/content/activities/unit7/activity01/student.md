## ACTIVIDAD 1

### ¿Por qué necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local del computador para que el celular se conecte?
Porque `localhost` solo funciona en el mismo dispositivo. La URL de Dev Tunnels es pública y permite que el celular se conecte desde otra red o dispositivo.

### ¿Qué hace `npm install` y `npm start`?
- `npm install`: Instala las dependencias del proyecto (como express y socket.io).
- `npm start`: Inicia el servidor Node.js.

### ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil?
Mensajes similares pero con diferentes IDs. Ej:  
`New client connected`,  
`Received message => {"type":"touch","x":128.49,"y":326.80}`,  
`Client disconnected`.

### Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?
Sí, funcionó bien. El círculo en la pantalla del computador seguía el toque del celular en tiempo real. La latencia fue baja.

### ¿Cerraste el puerto? ¿Por qué es importante hacerlo?
Sí. Es importante para liberar recursos y evitar posibles conexiones no deseadas.
