## Experimento 1:
1. ¿Qué querías comprobar?
- Queria ver que pasaba si presionaba el boton A y le mandaba una imagen 
2. ¿Cuál fue tu hipótesis
- Si presiono el boton A el LED mostrara una imagen que es Angry
3. Los códigos involucrados en el experimento
```
while True:
    if button_a.is_pressed():
        display.show(Image.ANGRY)
    else:
        display.clear()
```
4. Descripción de lo resultados
- El LED mostro la imagen que le mande unicamente si el boton A se dejaba presionado
## Experimento 2:
1. ¿Qué querías comprobar?
- Queria ver si al presionar el boton B me mostraba algun numero del 1 al 6
2. ¿Cuál fue tu hipótesis?
- Si presiono el boton B mostrara un numero random del 1 al 6 
3. Los códigos involucrados en el experimento
```
# Imports go at the top
from microbit import *
import random 

# Code in a 'while True:' loop repeats forever
while True:
    if button_b.is_pressed():
        display.show(random.randint(1,6))
```
4. Descripción de lo resultados
- El led mostro un numero random del 1 al 6 cada vez que se presionaba el boton B
## Experimento 3:
1. ¿Qué querías comprobar?
- Queria comprobar si al tocar el touch mostraba una imagen que era un corazon y que cada un segundo se borrara, pero al volver a tocarlo se volviera a mostar y despues del segundo se borrara de nuevo
2. ¿Cuál fue tu hipótesis?
- Al tocar el touch mostrara una imagen 
3. Los códigos involucrados en el experimento
```
while True:
    if pin_logo.is_touched():
        def heart_wait():
            display.show(Image.HEART)
            sleep(1000)
        
        heart_wait()
        display.clear()
```
4. Descripción de lo resultados
- El led mostro el corazon por un segundo 
