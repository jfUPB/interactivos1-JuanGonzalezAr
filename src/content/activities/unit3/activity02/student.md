```js
from microbit import *
import utime

class Bomba:
    def __init__(self, tiempo_limite):
        self.tiempo_inicio = utime.ticks_ms()
        self.tiempo_limite = tiempo_limite
        self.estado = "Activada"
        self.contador = self.tiempo_limite
        self.secuencia = []

    def actualizar(self):
        if self.estado == "Activada":
            # Contar el tiempo y verificar si el tiempo se acabó
            if utime.ticks_diff(utime.ticks_ms(), self.tiempo_inicio) >= self.tiempo_limite:
                display.show(Image.SAD)  # La bomba explota
                self.estado = "Explota"
            else:
                display.show(str((self.tiempo_limite - utime.ticks_diff(utime.ticks_ms(), self.tiempo_inicio)) // 1000))  # Mostrar tiempo restante en segundos

    def desactivar(self):
        self.estado = "Desactivada"
        display.show(Image.NO)  # Bomba desactivada

    def verificar_secuencia(self):
        # Si la secuencia es correcta, desactivar la bomba
        if self.secuencia == ["A", "B", "A", "shake"]:
            self.desactivar()
            self.secuencia = []

    def registrar_entrada(self):
        if button_a.is_pressed():
            self.secuencia.append("A")
            utime.sleep(0.5)  # Evitar entradas múltiples
        elif button_b.is_pressed():
            self.secuencia.append("B")
            utime.sleep(0.5)
        elif accelerometer.is_gesture("shake"):
            self.secuencia.append("shake")
            utime.sleep(0.5)
        
        self.verificar_secuencia()

# Crear la bomba con un tiempo límite de 10 segundos
bomba = Bomba(10000)

while True:
    bomba.actualizar()
    bomba.registrar_entrada()
    utime.sleep(0.1)  # Evitar que el bucle corra demasiado rápido
```
