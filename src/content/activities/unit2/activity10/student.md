# Explicación del Código de Micro:bit - Cambios de Estado

Este código en Micro:bit utiliza una máquina de estados para cambiar entre diferentes imágenes en la pantalla de la micro:bit. El código maneja cuatro estados: **HAPPY** (feliz), **SMILE** (sonriente), **SAD** (triste), y **INIT** (inicial), y cada uno tiene un intervalo de tiempo específico.

## Definición de los Estados

1. **`STATE_INIT`**: El estado inicial.
2. **`STATE_HAPPY`**: Muestra una cara feliz en la pantalla.
3. **`STATE_SMILE`**: Muestra una cara sonriente en la pantalla.
4. **`STATE_SAD`**: Muestra una cara triste en la pantalla.

## Variables

- **`HAPPY_INTERVAL`**: Define el tiempo en milisegundos (1500 ms o 1.5 segundos) que el micro:bit debe permanecer en el estado de "feliz".
- **`SMILE_INTERVAL`**: Define el tiempo (1000 ms o 1 segundo) para el estado de "sonriente".
- **`SAD_INTERVAL`**: Define el tiempo (2000 ms o 2 segundos) para el estado de "triste".
- **`current_state`**: Variable que almacena el estado actual. Se inicia en `STATE_INIT`.
- **`start_time`**: Guarda el tiempo en el que comenzó el estado actual.
- **`interval`**: Define cuánto tiempo debe durar el estado actual.

## Flujo del Código

### 1. **Estado `STATE_INIT`**
   - Cuando el estado es `STATE_INIT`, el micro:bit muestra la cara feliz en la pantalla (`display.show(Image.HAPPY)`).
   - Se actualiza el `start_time` con el tiempo actual.
   - Se establece el intervalo (`interval = HAPPY_INTERVAL`).
   - Luego, cambia al siguiente estado `STATE_HAPPY`.

### 2. **Estado `STATE_HAPPY`**
   - El micro:bit permanece en el estado de "feliz" (`display.show(Image.HAPPY)`) durante el tiempo definido en `HAPPY_INTERVAL` (1500ms).
   - **Evento del botón A**: Si el botón A es presionado, cambia al estado `STATE_SAD` y muestra la imagen triste (`display.show(Image.SAD)`).
   - Si el tiempo transcurrido es mayor que el intervalo, cambia al estado `STATE_SMILE` y muestra la imagen sonriente (`display.show(Image.SMILE)`).

### 3. **Estado `STATE_SMILE`**
   - El micro:bit permanece en el estado de "sonriente" (`display.show(Image.SMILE)`) durante el tiempo definido en `SMILE_INTERVAL` (1000ms).
   - **Evento del botón A**: Si el botón A es presionado, cambia al estado `STATE_HAPPY` y muestra la imagen feliz.
   - Si el tiempo transcurrido es mayor que el intervalo, cambia al estado `STATE_SAD` y muestra la imagen triste.

### 4. **Estado `STATE_SAD`**
   - El micro:bit permanece en el estado de "triste" (`display.show(Image.SAD)`) durante el tiempo definido en `SAD_INTERVAL` (2000ms).
   - **Evento del botón A**: Si el botón A es presionado, cambia al estado `STATE_SMILE` y muestra la imagen sonriente.
   - Si el tiempo transcurrido es mayor que el intervalo, cambia al estado `STATE_HAPPY` y muestra la imagen feliz.

### Transiciones de Estado
Las transiciones entre estados son gestionadas por dos factores:
1. El **tiempo transcurrido**: Cuando el micro:bit ha estado en un estado por el tiempo correspondiente (`HAPPY_INTERVAL`, `SMILE_INTERVAL`, `SAD_INTERVAL`), el estado cambia automáticamente.
2. La **presión del botón A**: Si se presiona el botón A, el micro:bit cambia directamente al siguiente estado correspondiente, independientemente del tiempo.

