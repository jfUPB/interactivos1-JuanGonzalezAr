### Codigo sin editar:
https://editor.p5js.org/JuanGonzalezAr/sketches/HJxW7ljK6 
```js
let x = 25;
let port, reader;
let buffer = [];
let textInfo = "Conectando...";

function setup() {
  createCanvas(720, 400);
  colorMode(RGB);
  textSize(20);
  noLoop();
  connectMicrobit();
}

function draw() {
  background(0);
  fill(x / 3, 90, 90);
  circle(x, height / 2, 50);

  x += 5;
  if (x > width + 25) {
    x = -25;
  }

  fill(255);
  text(textInfo, 20, 30);
}

function mousePressed() {
  if (isLooping()) {
    noLoop();
  } else {
    loop();
  }
}

async function connectMicrobit() {
  try {
    port = await navigator.serial.requestPort();
    await port.open({ baudRate: 115200 });
    textInfo = "Microbit conectado";
    reader = port.readable.getReader();
    readSerialData();
  } catch (err) {
    textInfo = "Error de conexión: " + err;
    console.error(err);
  }
}

async function readSerialData() {
  while (true) {
    const { value, done } = await reader.read();
    if (done) break;
    for (let byte of value) {
      buffer.push(byte);

      if (buffer.length >= 8 && buffer[0] === 0xAA) {
        let data = buffer.slice(1, 7);
        let receivedChecksum = buffer[7];
        let computedChecksum = data.reduce((a, b) => a + b, 0) % 256;

        if (computedChecksum === receivedChecksum) {
          let xVal = (data[0] << 8) | data[1];
          let a = data[4];
          let b = data[5];

          if (xVal > 32767) xVal -= 65536;

          if (a === 1) x -= 10;
          if (b === 1) x += 10;

          x = constrain(x, 25, width - 25);
        } else {
          console.warn("Paquete con checksum incorrecto");
        }

        buffer = [];
      } else if (buffer.length > 20) {
        buffer.shift();
      }
    }
  }
}
```
### Enlace a p5
- https://editor.p5js.org/JuanGonzalezAr/sketches/Gpeaa8iK4 
