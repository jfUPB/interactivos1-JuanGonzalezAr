# Framing y protocolo binario

## ¿Por qué se necesita framing?

Cuando enviamos datos como texto, usamos comas y saltos de línea para separar los valores.  
En binario, no hay separadores visibles, así que el receptor no sabe dónde empieza o termina un paquete.  
Por eso usamos un byte especial (0xAA) al inicio de cada paquete para marcar el comienzo.

## ¿Cómo funciona el framing?

El paquete binario tiene esta estructura:

- 1 byte: header (0xAA)
- 6 bytes: datos (x, y, aState, bState)
- 1 byte: checksum

El receptor busca el header y luego lee los siguientes 7 bytes como un paquete.

## ¿Qué es un carácter de sincronización?

Es un byte que indica el inicio de un paquete.  
En este caso usamos 0xAA (170 en decimal).

## ¿Qué es el checksum?

Es un número que ayuda a verificar que los datos no se dañaron.  
Se calcula sumando todos los bytes del paquete (excepto el header) y tomando el resultado módulo 256.

## ¿Por qué se usa concat?

Porque los datos pueden llegar por partes.  
Se necesita unirlos para tener el paquete completo.

## ¿Por qué el bucle se ejecuta solo si serialBuffer.length >= 8?

Porque cada paquete tiene exactamente 8 bytes.  
Si hay menos, no se puede procesar un paquete completo.

## ¿Qué hace serialBuffer.shift()?

Quita el primer byte del arreglo.  
Se usa para descartar datos hasta encontrar el header (0xAA).

## ¿Qué hace continue?

Salta al siguiente ciclo del bucle.  
Se usa para evitar procesar datos incompletos o inválidos.

## ¿Qué hace break?

Sale del bucle.  
Se usa si no hay suficientes bytes para continuar.

## ¿Qué hacen slice() y splice()?

- slice(): copia una parte del arreglo sin modificarlo.
- splice(): elimina parte del arreglo.

Se usan para copiar y luego quitar el paquete procesado del buffer.

## ¿Qué hace reduce()?

Suma los valores de un arreglo.  
Se usa para calcular el checksum.

## ¿Por qué se comparan los checksums?

Para verificar que los datos llegaron bien.  
Si no coinciden, el paquete se descarta.

## ¿Qué es un DataView?

Es una herramienta de JavaScript que permite leer datos binarios como enteros, flotantes, etc.  
Sirve para interpretar los bytes que vienen del micro:bit.

## ¿Por qué no se pueden leer los datos binarios directamente?

Porque los datos binarios no son texto.  
Se necesita saber cómo están organizados (tipo de dato, tamaño, orden de bytes) para poder interpretarlos.
