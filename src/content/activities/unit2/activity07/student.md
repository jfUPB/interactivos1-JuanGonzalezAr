## Reproduciendo musica
```js
# Imports go at the top
from microbit import *
import music

# Code in a 'while True:' loop repeats forever
while True:
    if button_a.was_pressed():  //Cuando el boton a se presiona reproduce un sonido
        music.play(music.DADADADUM)
        sleep(1000)

    if button_b.was_pressed():  //Cuando el boton b se presiona se reproduce un sonido
        music.play(music.PYTHON)
        sleep(1000)
```
