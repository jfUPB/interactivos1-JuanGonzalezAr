# Actividad 3 – Comparación de Formatos de Comunicación

## 🧩 ¿Por qué antes necesitábamos delimitadores y ahora no?

### Antes (Formato ASCII):
- **Datos en texto:** `"x,y,a,b\n"`
- **Necesario usar:**
  - **Comas (,):** Para separar los valores.
  - **Salto de línea (\n):** Para indicar el final de un paquete.
- **Tamaño variable:** Cada valor podía ocupar diferente número de caracteres.

### Ahora (Formato Binario):
- **Datos en binario con `struct.pack('>2h2B')`.**
- **Tamaño fijo:** Siempre 6 bytes por paquete.
- **No se necesitan separadores** porque se conoce la estructura y el tamaño exacto de cada dato.

---

## 🔄 Cambio en el Envío y Recepción de Datos

### Envío desde el micro:bit:

| Unidad Anterior             | Unidad Actual                   |
|----------------------------|----------------------------------|
| Texto ASCII con separadores | Binario con estructura fija     |
| `"x,y,a,b\n"`              | `struct.pack('>2h2B', x, y, a, b)` |
| Tamaño variable            | Tamaño fijo: 6 bytes            |

### Recepción en p5.js / Processing:

| Antes                      | Ahora                           |
|---------------------------|----------------------------------|
| Se leía texto (`readLine()`) | Se leen exactamente 6 bytes     |
| Se usaba `split(',')`     | Se decodifica usando `DataView` |

---

## 🐛 ¿Qué pasa si hay errores?

### Ejemplo en consola:
microBitX: 32767 microBitY: -1 microBitAState: false microBitBState: true


### Causas posibles:
- ❌ **Lectura desincronizada:** Se leyó a mitad de un paquete.
- ❌ **Bytes perdidos:** El mensaje quedó incompleto.
- ❌ **Lecturas desfasadas:** Se desalineó toda la secuencia.

**Resultado:** Se muestran datos corruptos o absurdos.

---

## ⚙️ Cambios en los programas

### Código del micro:bit:
- **Acelerómetro real:** `accelerometer.get_x()` y `get_y()` en lugar de valores fijos.
- **Botones reales:** `button_a.is_pressed()` y `button_b.is_pressed()`.

### Código en p5.js:
- **Consola más limpia:** Se quitó `console.log()` para evitar saturación.
- **Mensajes observados:**
  - `Microbit ready to draw`
  - `A pressed`, `B released`
  - `Checksum error in packet` (cuando los datos llegan mal)


