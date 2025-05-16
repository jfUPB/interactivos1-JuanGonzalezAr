## Reflexión Unidad: Comunicación Serial y p5.js con micro:bit
---
### 1. ¿Qué es un protocolo de comunicación y por qué es importante en la comunicación serial?
Es un conjunto de reglas para que dos dispositivos se entiendan. Sin él, los datos podrían llegar mal interpretados.

### 2. ¿Por qué se separan los datos con comas en el protocolo ASCII que exploramos?
Porque permite dividir fácilmente los valores al recibirlos con `split(",")`.

### 3. ¿Por qué es necesario terminar los datos con un carácter que marque el fin del mensaje?
Para saber cuándo terminó un paquete. Usamos `\n` para que `readUntil("\n")` sepa dónde parar.

### 4. ¿Por qué fue necesario usar una máquina de estados en la aplicación modificada de p5.js?
Para manejar correctamente los cambios de estado: conectar, leer datos y mover el círculo solo si hay datos.

### 5. ¿Cómo se formatean los datos en el micro:bit para ser enviados por el puerto serial?
Se usa:  
```python
uart.write("{},{},{},{}\n".format(x, y, a, b))
```

### 6. ¿Qué significa que los datos enviados por el micro:bit están codificados en ASCII?
Que los números y valores se convierten en texto legible, no en binario puro.

### 7. ¿Por qué es necesario en la aplicación de p5.js preguntar si hay bytes disponibles en el puerto serial antes de leerlos?
Porque si se intenta leer sin datos disponibles, puede generar errores o undefined.

### 8. ¿Cómo se elimina el retorno de carro o salto de línea de un string en p5.js?
Con .trim().

### 9. Si una cadena tiene información separada por espacios y quieres dividir dicha información en varias cadenas individuales ¿Qué función de p5.js usarías?
Usaría split(" ").

### 10. ¿Por qué es necesario en la aplicación del caso de estudio convertir las cadenas a números enteros antes de usarlas en el sketch de p5.js?
Porque al recibir los datos por serial son strings, y no se pueden usar directamente para mover objetos o hacer cálculos.

### 11. Si el micro:bit tiene los siguientes datos xValue: 123, yValue: 756, aState: False, bState: True ¿Qué bytes se enviarían por el puerto serial
Se enviaría:
123,756,0,1\n
### 12. ¿Qué aprendiste nuevo del micro:bit que no sabías antes?
Aprendí cómo enviar datos por UART y cómo acceder al acelerómetro y botones desde código.

### 13. ¿Qué aprendiste nuevo de p5.js que no sabías antes?
Cómo usar Web Serial para leer datos en tiempo real desde otro dispositivo.

