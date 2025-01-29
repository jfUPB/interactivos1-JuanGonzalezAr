## Interaccion con micro:bit
``` js
let port;
let connectBtn;

function setup() {
    createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton('Connect to micro:bit');
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
    fill('white');
    square(50,50,50);
}

function draw() {

    if(port.availableBytes() > 0){
        let dataRx = port.read(1);
        if(dataRx == 'A'){
            fill('pink');
        }

        
        background(220);
        fill('white')
        square(50,50,50)
      
    }


    if (!port.opened()) {
        connectBtn.html('Connect to micro:bit');
    }
    else {
        connectBtn.html('Disconnect');
    }
}

function connectBtnClick() {
    if (!port.opened()) {
        port.open('MicroPython', 115200);
    } else {
        port.close();
    }
}

function sendBtnClick() {
    port.write('h');
}
```

```js
from microbit import *

uart.init(baudrate=115200)
display.show(Image.BUTTERFLY)

while True:
    if button_a.is_pressed():
        uart.write('A')
        sleep(500)
    if button_b.is_pressed():
        uart.write('B')
        sleep(500)
    if accelerometer.was_gesture('shake'):
        uart.write('C')
        sleep(500)
    if uart.any():
        data = uart.read(1)
        if data:
            if data[0] == ord('h'):
                display.show(Image.HEART)
                sleep(500)
                display.show(Image.HAPPY)
```
# **Conexión y Comunicación entre p5.js y micro:bit**

## **Conexión:**
1. El usuario presiona **"Connect to micro:bit"**.
2. Se abre la conexión serial con el micro:bit.

## **Recepción de Datos:**
1. Si el micro:bit envía `'A'`, p5.js cambia el color del cuadrado.

## **Envío de Datos (Opcional):**
1. p5.js puede enviar datos al micro:bit usando `port.write()`, aunque esta función no se usa activamente en el código.
