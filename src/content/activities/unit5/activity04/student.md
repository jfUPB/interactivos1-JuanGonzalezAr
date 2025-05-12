### Codigo sin editar:
https://editor.p5js.org/JuanGonzalezAr/sketches/HJxW7ljK6 
```js
let x = 360;
let port, reader;
let buffer = [];
let textInfo = "Haz clic en 'Conectar Microbit'";
let connectButton;

function setup() {
  createCanvas(720, 400);
  textSize(20);
  colorMode(RGB);

  // Crear botón y asignar función
  connectButton = createButton("Conectar Microbit");
  connectButton.position(20, 420);
  connectButton.mousePressed(connectMicrobit);

  noLoop(); // Solo se redibuja cuando llegan datos
}

function draw() {
  background(0);
  fill(200, 90, 90);
  circle(x, height / 2, 50);
  fill(255);
  text(textInfo, 20, 30);
}

async function connectMicrobit() {
  try {
    port = await navigator.serial.requestPort();
    await port.open({ baudRate: 115200 });
    textInfo = "Microbit conectado";
    reader = port.readable.getReader();
    readSerialData();
  } catch (err) {
    textInfo = "Error de conexión: " + err.message;
    console.error(err);
    redraw();
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
          let a = data[4];
          let b = data[5];

          // Mueve solo con botones
          if (a === 1) x -= 10;
          if (b === 1) x += 10;
          x = constrain(x, 25, width - 25);
        }

        buffer = [];
        redraw();
      } else if (buffer.length > 20) {
        buffer.shift();
      }
    }
  }
}

```
### Enlace a p5
- https://editor.p5js.org/JuanGonzalezAr/sketches/Gpeaa8iK4 
- https://drive.google.com/file/d/1_fSIQVNgkg-woiBFMw0F8WBLR2nQffQ5/view?usp=drivesdk 
