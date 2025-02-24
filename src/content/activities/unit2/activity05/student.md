## Leyendo datos seriales :
1. Codigo de p5:
``` js
let port;
let connectBtn;
let sendBtnA, sendBtnB;

function setup() {
  createCanvas(400, 400);
  background(199);
  
  port = createSerial(); // inicializa la conexión serial
  
  connectBtn = createButton('Conectar a micro:bit');
  connectBtn.position(80, 300);
  connectBtn.mousePressed(connectBtnClick); // Define la acción del botón de conexión
  
  sendBtnA = createButton('Enviar A');
  sendBtnA.position(220, 300);
  sendBtnA.mousePressed(() => sendBtnClick('A')); // Envía "A" cuando se presiona este botón
  
  sendBtnB = createButton('Enviar B');
  sendBtnB.position(295, 300);
  sendBtnB.mousePressed(() => sendBtnClick('B')); // Envía "B" cuando se presiona este botón
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open('MicroPython', 115200); // Abre el puerto serial con la tasa de baudios
    console.log("Conectado al micro:bit");
  } else {
    port.close();
    console.log("Desconectado del micro:bit");
  }
}

function sendBtnClick(data) {
  if (port.opened()) {
    port.write(data); // Envía los datos al micro:bit
    console.log(`Enviado: ${data}`);
  } else {
    console.log("Micro:bit no conectado");
  }
}
```
- Aca estan comentados para que sirven cada cosa que hice en codigo
2. Codigo de microPython
``` js
# Imports go at the top
from microbit import *

# Definir las imágenes a mostrar
image_A = Image.HEART
image_B = Image.HAPPY

while True:
    if uart.any():  # Si hay datos disponibles en el puerto serial
        data = uart.read()  # Leer los datos recibidos
        if data == b'A':  # Si los datos recibidos son 'A'
            display.show(image_A)  # Muestra la imagen de corazón
        elif data == b'B':  # Si los datos recibidos son 'B'
            display.show(image_B)  # Muestra la cara feliz
```
