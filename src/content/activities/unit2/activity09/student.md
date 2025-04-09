```js
from microbit import *
import utime

class Semaforo:
    def __init__(self):
        self.state = "ROJO"  
        self.startTime = running_time()  
        self.tiempos = {"ROJO": 3000, "AMARILLO": 1000, "VERDE": 2000}  
        
    def update(self):

        if running_time() - self.startTime > self.tiempos[self.state]:
            self.startTime = running_time()  
            if self.state == "ROJO":
                self.state = "VERDE"
            elif self.state == "VERDE":
                self.state = "AMARILLO"
            elif self.state == "AMARILLO":
                self.state = "ROJO"

    def mostrarSemaforo(self):
        display.clear()  
        if self.state == "ROJO":
            display.set_pixel(2, 0, 9) 
        elif self.state == "AMARILLO":
            display.set_pixel(2, 2, 9) 
        elif self.state == "VERDE":
            display.set_pixel(2, 4, 9)  


semaforo = Semaforo()

while True:
    semaforo.update() 
    semaforo.mostrarSemaforo()  
    utime.sleep(0.1)  
```
