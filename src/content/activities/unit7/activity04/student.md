## ACTIVIDAD 4

### ¿Por qué es útil enviar los datos como objeto JSON?
Es claro, estructurado y fácil de extender con más propiedades.

### ¿Qué pasaría sin la comprobación del `threshold`?
Se enviarían demasiados datos, saturando la red y causando retrasos.

### ¿Cómo adaptar el código para clic de ratón?
Usar `mouseMoved()` y `mousePressed()` en lugar de `touchMoved()`.

### ¿Por qué usar `JSON.parse()` en `try…catch`?
Para evitar que errores al convertir datos detengan el programa.

### ¿Canvas con tamaños distintos? ¿Cómo adaptar?
Usar `map()` para escalar las coordenadas del móvil al tamaño del escritorio.

### ¿Qué cambiar si el servidor emite ‘updateDesktop’?
Cambiar el nombre del evento en `socket.on()` del escritorio a `'updateDesktop'`.

---

### Propósito de `mobile/sketch.js`:
Captura el toque y envía datos al servidor solo si hay cambio significativo.

### Propósito de `desktop/sketch.js`:
Recibe datos del servidor y actualiza la posición del círculo según el toque.

### Función `touchMoved` en móvil:
Detecta movimiento; si supera el umbral, envía coordenadas como JSON al servidor.

### Recepción en escritorio:
Convierte JSON a objeto y actualiza la posición del círculo si el tipo es ‘touch’.
