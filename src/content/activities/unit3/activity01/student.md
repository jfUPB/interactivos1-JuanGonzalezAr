```js
from microbit import *
import utime

class Semaforo:
    def __init__(self, x, y, intervalos):
        self.estado = "Rojo"
        self.tiempo_inicio = utime.ticks_ms()
        self.intervalos = intervalos  # Diccionario con duración de cada estado
        self.x = x
        self.y = y
        self.actualizar_display()

    def actualizar_display(self):
        if self.estado == "Rojo":
            display.set_pixel(self.x, self.y, 9)
        elif self.estado == "Amarillo":
            display.set_pixel(self.x, self.y + 1, 5)
        elif self.estado == "Verde":
            display.set_pixel(self.x, self.y + 2, 9)

    def apagarPixel(self):
        if self.estado == "Rojo":
            display.set_pixel(self.x, self.y, 0)
        elif self.estado == "Amarillo":
            display.set_pixel(self.x, self.y + 1, 0)
        elif self.estado == "Verde":
            display.set_pixel(self.x, self.y + 2, 0)

    def actualizar(self):
        tiempo_actual = utime.ticks_ms()
        if utime.ticks_diff(tiempo_actual, self.tiempo_inicio) > self.intervalos[self.estado]:
            self.tiempo_inicio = tiempo_actual
            self.apagarPixel()
            self.transicionar_estado()
            self.actualizar_display()

    def transicionar_estado(self):
        if self.estado == "Rojo":
            self.estado = "Verde"
        elif self.estado == "Verde":
            self.estado = "Amarillo"
        elif self.estado == "Amarillo":
            self.estado = "Rojo"

# Configuración del semáforo con tiempos de duración en cada estado
intervalos1 = {"Rojo": 5000, "Amarillo": 2000, "Verde": 3000}
intervalos2 = {"Rojo": 3000, "Amarillo": 1000, "Verde": 2000}
intervalos3 = {"Rojo": 4000, "Amarillo": 3000, "Verde": 2000}
semaforo1 = Semaforo(2, 0, intervalos1)
semaforo2 = Semaforo(3, 0, intervalos2)
semaforo3 = Semaforo(4, 0, intervalos3)

while True:
    semaforo1.actualizar()
    semaforo2.actualizar()
    semaforo3.actualizar()
```


## Ventajas de usar una clase para el semáforo
1. Organización: La clase encapsula todo lo relacionado con el semáforo, lo que facilita su comprensión y mantenimiento.

2. Reusabilidad: Permite crear múltiples semáforos con distintas configuraciones sin repetir código.

3. Manejo de Estado: Facilita las transiciones entre los estados del semáforo y la actualización de la visualización.

4. Escalabilidad: Se pueden agregar más semáforos fácilmente sin modificar el código existente.

5. Claridad: El código es más limpio y modular, lo que facilita la depuración y mantenimiento.

## Técnica de máquinas de estado
El enfoque de máquina de estado es ideal para semáforos, ya que tiene un ciclo claro de estados (Rojo, Amarillo, Verde) y transiciones bien definidas. Esto facilita la programación y asegura que el semáforo siga un ciclo preciso.
