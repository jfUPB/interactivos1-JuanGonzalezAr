# 🧠 Actividad 4 – Análisis de Comunicación con micro:bit y uso de SVG

## 🖼️ ¿Para qué se usan las imágenes SVG?

Las imágenes SVG (Scalable Vector Graphics) se utilizan para construir patrones o diseños en el lienzo. Representan gráficos vectoriales que pueden escalarse sin perder calidad, lo que las hace ideales para interfaces visuales dinámicas.

---

## 🔌 ¿Se pueden leer datos si el puerto está cerrado?

No. Si el puerto serial está cerrado, no es posible recibir datos del micro:bit, ya que no existe un canal activo de comunicación.

---

## 📤 ¿Qué pasa si el micro:bit envía datos con el puerto cerrado?

- Los datos enviados se pierden.
- Al abrir el puerto más tarde, los datos anteriores no pueden recuperarse.
- No hay almacenamiento en búfer automático entre transmisiones.

---

## ❗ ¿Qué pasa si el micro:bit no envía `\n`?

- El separador `\n` es necesario para delimitar cada conjunto de datos.
- Sin él, la lectura de datos con `readUntil('\n')` no funcionará correctamente.
- La línea de datos no se considerará completa, lo que podría causar errores en el análisis.

---

## 🧭 Posición central del objeto en pantalla

Al sumar `windowWidth / 2` y `windowHeight / 2`, el punto de referencia se traslada al centro del lienzo.  
Cuando `xValue = 0` e `yValue = 0`, el objeto se dibuja en el centro de la pantalla.

---

## ⌨️ Verificación de eventos `keyPressed` y `keyReleased`

- Se puede imprimir un mensaje en consola (`print("A pressed")`) para confirmar que el evento ocurrió.
- También se puede hacer que el lienzo cambie de color, muestre texto o cambie un diseño al presionar o soltar una tecla.

---

## 🔄 Análisis de `updateButtonStates()`

### ¿Qué hace?
- Detecta transiciones en el estado de los botones del micro:bit.
- Específicamente, detecta:
  - Botón A: de **no presionado** a **presionado**.
  - Botón B: de **presionado** a **no presionado**.

### ¿Por qué guardar el estado anterior?
- Permite detectar la transición y no repetir acciones mientras el botón sigue presionado.

### ¿Qué pasa si no se guarda el estado anterior?
- La función ejecutará la acción muchas veces por segundo durante cada ciclo de `draw()`.
- Esto causará un comportamiento repetitivo y no deseado.

---

## 📊 Diferencias entre el código anterior y el nuevo

### 1. Interacción con micro:bit
- El nuevo código recibe datos desde el micro:bit (inclinación y botones).
- El anterior dependía de teclado y mouse como entrada principal.

### 2. Eventos del mouse
- En el original, se usaban funciones como `mousePressed()` para dibujar.
- En el nuevo código, esas funciones se eliminan o se reemplazan por señales del micro:bit.

---

## ⚠️ Mensaje: “No se están recibiendo 4 datos del micro:bit”

### ¿Qué significa?
- El programa espera 4 valores separados por comas (x, y, a, b).
- Este mensaje aparece si:
  - Se reciben menos de 4 valores.
  - Los valores están mal formateados.
  - El micro:bit no ha enviado la línea completa.

### ¿Es constante o intermitente?
- Ocurre ocasionalmente. Esto sugiere que algunos datos se están perdiendo en la transmisión o se están leyendo de forma incompleta.

---

## ✅ Soluciones posibles

### 1. Validación de datos en p5.js
- Usar `port.availableBytes()` antes de leer.
- Verificar que `data.split(",").length === 4` antes de procesar.

### 2. Revisión del código del micro:bit
- Confirmar que los datos se envían en el formato correcto:  
  `"{},{},{},{}\n".format(x, y, a, b)`
- Asegurarse de que cada línea termina con un salto de línea `\n`.



