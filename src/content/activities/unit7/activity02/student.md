## ACTIVIDAD 2

### ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?
Porque permite acceder al servidor local desde otro dispositivo. Dev Tunnels crea una URL pública que redirige al puerto local (3000) de la máquina.

### ¿Por qué usamos JSON.stringify() en el emisor (móvil) y JSON.parse() en el receptor (escritorio)? ¿Qué problema resuelve JSON aquí?
Convierte objetos en texto para enviarlos (stringify) y los convierte de nuevo en objetos al recibirlos (parse). JSON hace que los datos sean claros y estructurados.

### ¿Cuál es la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil?
touchMoved() detecta movimiento del dedo. El threshold evita enviar datos cuando el cambio es muy pequeño, reduciendo mensajes innecesarios.

### ¿Qué otros eventos táctiles existen en p5.js y para qué tipo de interacciones podrían ser útiles?
- `touchStarted()`: cuando se toca la pantalla. Útil para iniciar acciones.
- `touchEnded()`: cuando se levanta el dedo. Útil para finalizar acciones o confirmar selecciones.
