

# 🧪 Actividad 3 – Análisis del envío de datos por UART desde el micro:bit

## 🔍 ¿Qué información se está enviando?
- `xValue`: Aceleración en el eje X (rango aproximado: -1024 a 1024).
- `yValue`: Aceleración en el eje Y (rango aproximado: -1024 a 1024).
- `aState`: Estado del botón A (`True` si está presionado).
- `bState`: Estado del botón B (`True` si está presionado).

---

## 📤 ¿Cómo se envía esta información?
Se envía como texto por UART, con el siguiente formato:

- xValue,yValue,aState,bState\n


- Los valores están **separados por comas (`,`)**.
- Cada línea termina con un **salto de línea (`\n`)**.

### Ejemplo:

969,652,True,False\n

---

## 🧠 ¿Qué significan las partes del código?

```python
"{} , {} , {} , {}\n".format(xValue, yValue, aState, bState)
```
{}: Espacios reservados para los valores.

.format(...): Inserta los valores correspondientes.

\n: Finaliza la línea, indicando el fin del paquete de datos.

### ❓ ¿Por qué usar comas y salto de línea?
Comas (,): Separan los datos, facilitando su lectura por otros programas (como p5.js o Python).

### Salto de línea (\n): Marca el final de un paquete de datos, útil para leer línea por línea.

### ⚠️ ¿Qué pasa si no se usan?
1. Sin comas: Los números se mezclan (969652TrueFalse) y son difíciles de separar correctamente.

2. Sin salto de línea: Todos los datos se envían como un bloque continuo, muy difícil de procesar.

### ⏱️ ¿Para qué sirve sleep(100)?
1. Pausa de 100 milisegundos entre cada envío.

2. Limita la frecuencia a 10 datos por segundo (10 Hz).

3. Evita saturar el puerto serial con datos excesivos e ilegibles.

### 📈 ¿Cómo cambian xValue y yValue al inclinar el micro:bit?
- Izquierda: xValue negativo, yValue positivo.

- Derecha: xValue positivo, yValue negativo.

- Adelante: xValue negativo, yValue positivo.

- Atrás: xValue positivo, yValue negativo.

### 🔄 ¿Qué diferencia hay entre is_pressed() y was_pressed()?
- is_pressed(): Devuelve True mientras el botón está presionado.

- was_pressed(): Devuelve True si el botón fue presionado, aunque ya se haya soltado.

### 📦 Ejemplo de salida:
- 969,652,True,False
- 39 36 39 2C 36 35 32 2C 54 72 75 65 2C 46 61 6C 73 65 0A
