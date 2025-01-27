```
function setup() {
  createCanvas(400, 400);
  background(70);
}

function draw() {
  let c = color(255,40,255);
  fill(c);
  triangle (100,100,100,40,random(98,250),78);
}
```
## Cambios:
- El `let c `es para cambiar el color y el fill es para rellenar el objeto o dibujo que seria el triangulo, y el triangulo tiene todos sus componentes que son (x1,y1,x2,y2,x3,y3) los cuales le dan las caracteristicas al triangulo, tambien tiene unos componentes de random que hace que tome valores entre 98 y 250
- **Falta insertar imagenes**
