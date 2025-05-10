## Solucion:
### Vectores de prueba
#### Estado: CONFIGURACIÓN (STATE_CONFIG)
- Incrementar tiempo al presionar A [X]
- Disminuir tiempo al presionar B [X]
- Pasar a estado ARMADO al agitar el micro:bit [X]
- No cambiar estado al presionar el logo táctil [X]
- Incrementar tiempo al recibir ‘A’ por UART [X]
- Disminuir tiempo al recibir ‘B’ por UART [X]
#### Estado: ARMADO (STATE_ARMED)
- Pasar a EXPLOSIÓN cuando el tiempo llegue a 0 [X]
- Añadir ‘A’ a la secuencia de desactivación al presionar A [X]
- Añadir ‘B’ a la secuencia de desactivación al presionar B [X]
- Desactivar la bomba al ingresar la secuencia correcta A-B-A-B [X]
- Mantener el estado ARMADO si la secuencia de desactivación es incorrecta [X]
- Añadir caracteres a la secuencia al recibir ‘A’ o ‘B’ por UART [X]
#### Estado: EXPLOSIÓN (STATE_EXPLOSION)
- Reiniciar el juego al presionar el logo táctil [X]
- No responder a A o B en estado EXPLOSIÓN [X]
- No responder a agitación en estado EXPLOSIÓN [X]
