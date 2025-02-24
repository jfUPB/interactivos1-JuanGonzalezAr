## Salidas visuales:
```js
# Imports go at the top
from microbit import *

# Definir las imágenes a mostrar

while True:
   display.show("Bof")
   sleep(1000)

   display.show(Image.DUCK)
   sleep(1000)

   display.show(Image.ARROW_NE)
   sleep(1000)
```
- El display.show es para mostrar una imagen en el LED y el sleep 1000 permite pausar la ejecución del programa 1 segundo
