# 📌 Análisis detallado del código

Este código en **MicroPython** para la **BBC micro:bit** define una clase `Pixel`, que gestiona el parpadeo de un píxel en la pantalla LED de la micro:bit. Cada instancia de `Pixel` alterna entre encenderse y apagarse después de un intervalo de tiempo específico.

---

## **📌 Descripción del código**

### **Clase `Pixel`**
- **Propiedades:**
  - `state`: controla el estado en el que se encuentra el píxel.
  - `startTime`: almacena el tiempo de referencia para medir el intervalo.
  - `interval`: define cuánto tiempo espera el píxel antes de cambiar de estado.
  - `pixelX` y `pixelY`: posición del píxel en la matriz de LEDs.
  - `pixelState`: define si el píxel está encendido (`9`) o apagado (`0`).

- **Método `update()`**:
  - **Estado `"Init"`**:
    - Se establece `startTime` con el tiempo actual.
    - Se cambia al estado `"WaitTimeout"`.
    - Se enciende o apaga el píxel dependiendo del valor inicial.
  - **Estado `"WaitTimeout"`**:
    - Si ha pasado el tiempo definido en `interval`, alterna el estado del píxel (`9` para encendido, `0` para apagado).
    - Se actualiza `startTime` para medir el próximo intervalo.

### **Bucle principal (`while True`)**
- Se crean dos píxeles en posiciones diferentes:
  - `pixel1` en `(0,0)`, con un parpadeo cada 1000 ms.
  - `pixel2` en `(4,4)`, con un parpadeo más rápido (cada 500 ms).
- En cada iteración del bucle, se llama `update()` en ambos píxeles, permitiendo que cambien su estado según el tiempo transcurrido.

---

## **📌 Identificación de Estados, Eventos y Acciones**

### **📍 Estados**
- `"Init"`: El píxel se inicializa, se fija el tiempo de referencia y se enciende en pantalla.
- `"WaitTimeout"`: El programa espera a que pase el `interval` para cambiar el estado del píxel.

### **📍 Eventos**
- `utime.ticks_diff(utime.ticks_ms(), self.startTime) > self.interval`: Pregunta si ha pasado el tiempo definido (`interval`).

### **📍 Acciones**
- `display.set_pixel(self.pixelX, self.pixelY, self.pixelState)`: Cambia el estado del píxel en la pantalla LED.
- `self.startTime = utime.ticks_ms()`: Reinicia el temporizador.
- `self.pixelState = 9 if self.pixelState == 0 else 0`: Alterna el estado del píxel entre encendido y apagado.

