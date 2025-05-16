## Entradas del micro:bit 
1. Botones:
- El micro:bit tiene dos botones en la parte frontal que se pueden usar por separado o juntos para hacer que sucedan cosas.
2. Logotipo tactil
- El nuevo micro:bit tiene una entrada adicional. El logo dorado también funciona como sensor táctil. Puedes usarlo como un botón adicional en tus programas, además de los botones A y B.
3. Acelerometro:
- El acelerómetro del micro:bit mide fuerzas en tres dimensiones, incluida la gravedad, para que tus proyectos puedan saber en qué posición se encuentra tu micro:bit. Puedes usarlo para experimentos científicos, agregar entradas de movimiento a los juegos o crear alarmas simples que te avisen cuando alguien mueva tus cosas
4. Boton de reinicio y encendido
- Al presionar este botón en el nuevo micro:bit, se reiniciará el micro:bit y se ejecutará el programa nuevamente desde el principio. Si lo mantiene presionado, el LED de encendido rojo se apagará. Cuando el LED de encendido se apague, suelte el botón y su micro:bit estará en modo de suspensión de ahorro de energía. Use esto para hacer que las baterías duren más. Presione el botón nuevamente para reactivar su micro:bit
## Salidas:
1. Led de encendido rojo
- El LED rojo en la parte posterior del nuevo micro:bit muestra cuando su micro:bit tiene energía, ya sea de baterías o de un cable USB.
2. LED usb amarillo:
- En el nuevo micro:bit, una luz LED amarilla parpadea cuando su computadora se está comunicando con el micro:bit a través de USB, por ejemplo, cuando flashea un archivo de programa.
3. Altavoz
- El nuevo micro:bit con sonido tiene un altavoz incorporado para que puedas añadir música y nuevos sonidos a tus proyectos aún más fácilmente
4. Procesador
- El procesador del micro:bit es su cerebro, que obtiene, decodifica y ejecuta sus instrucciones.
 ## Funciopnes de micropython
 ## Entradas:
 1. Botones: 
``` 
while True:
    if button_a.was_pressed():
        display.scroll('A')
```
- Verifica si el boton A fue presionado
2. Touch logo:
```
while True:
    if pin_logo.is_touched():
        display.show(Image.HAPPY)
```
- Si se toca el touch muestra una imagen 
3. Microfono
```
while True:
    if microphone.current_event() == SoundEvent.LOUD:
        display.show(Image.HAPPY)
    elif microphone.current_event() == SoundEvent.QUIET:
        display.show(Image.ASLEEP)
```
- Si el microfono recibe sonido muestra una imagen y si no muestra otra imagen
## Salidas 
1. Imagen
```
display.show(Image.HEART)
sleep(400)
```
- Muestra una imagen por medio de los LED
2. Led
```
display.clear()
```
- Cuando se manda una imagen esta funcion ayuda a que si no se esta cumpliendo la funcion para mostrar la imagen, se apaguen los led
3. Sonido:
```
import music

music.play(music.BA_DING)
```
- Importa musica y la hace sonar
