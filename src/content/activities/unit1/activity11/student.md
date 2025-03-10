```js
let port;
let connectBtn;

let x;

function setup() {
    createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton('Connect to micro:bit');
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
    fill('white');
    circle(50,50,50);
  
    x = 20
}

function draw() {

    if(port.availableBytes() > 0){
        let dataRx = port.read(1);
        if(dataRx == 'A'){
            x = x+20
            translate(x, 0);
        }
        else if(dataRx == 'B'){
            x = x - 20
            translate(x, 0);
        }
      background(220);
      fill('white');
      circle(50,50,50);
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
Se logra mediante comunicacion serial, se define una variable x que sera la posicion del circulo en esa coordenada, ahora se hace una condicion
para cuando se presione el boton `A` el circulo se desplaze la posicion en x que definimos mas los 20 que le estamos sumando y cuando presionesmos
el boton `B` se hace la mismo cambiando que ahora se va desplazar a la izquierda restando 20 a su posicion 
