# 🎮 Actividad 1: Comunicación entre micro:bit y p5.js

## 🔌 Conexión serial
El micro:bit se comunica con p5.js mediante una conexión serial utilizando la librería `p5.webserial.js`.  
Envía datos a través de `uart.write()`, que son leídos en el sketch de p5.js para generar visuales interactivos.

---

## 📤 Datos enviados por el micro:bit

Formato de los datos enviados (en ASCII, separados por comas y terminados en `\n`):
```
<xValue>,<yValue>,<aState>,<bState>\n
```


- `xValue`, `yValue`: valores del acelerómetro (enteros).
- `aState`, `bState`: estados de los botones A y B (booleanos `true` o `false`).

---

## 🔁 Lectura en p5.js

La lectura de datos ocurre dentro de la función `draw()` en p5.js:

```javascript
if (port.availableBytes() > 0) {
  let data = port.readUntil("\n");
  if (data) {
    data = data.trim();
    let values = data.split(",");
    if (values.length == 4) {
      microBitX = int(values[0]) + windowWidth / 2;
      microBitY = int(values[1]) + windowHeight / 2;
      microBitAState = values[2].toLowerCase() === "true";
      microBitBState = values[3].toLowerCase() === "true";
      updateButtonStates(microBitAState, microBitBState);
    } else {
      print("No se están recibiendo 4 datos del micro:bit");
    }
  }
}
```
- microBitX, microBitY: se usan para posicionar elementos según el acelerómetro.

- Estados de botones se comparan para generar eventos.

### 🟢 Eventos en p5.js
La función updateButtonStates() detecta eventos al comparar los estados actuales y anteriores de los botones:

```javascript
function updateButtonStates(newAState, newBState) {
  if (newAState === true && prevmicroBitAState === false) {
    lineModuleSize = random(50, 160);
    clickPosX = microBitX;
    clickPosY = microBitY;
    print("A pressed");
  }

  if (newBState === false && prevmicroBitBState === true) {
    c = color(random(255), random(255), random(255), random(80, 100));
    print("B released");
  }

  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}
```

### 🎯 ¿Qué hacen los eventos?
1. "A pressed": se detecta cuando el botón A pasa de false a true. Se guarda la posición y se genera un tamaño aleatorio.

2. "B released": se detecta cuando el botón B pasa de true a false. Se asigna un color aleatorio.
- microBitX, microBitY: se usan para posicionar elementos según el acelerómetro.


