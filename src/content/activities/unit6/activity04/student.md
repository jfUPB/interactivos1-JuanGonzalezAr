## Actividad 4

### Error al detener el servidor

Abrí `page2.html` en el navegador con el servidor corriendo y accedí a la consola de desarrollador (F12).  
Luego, detuve el servidor de Node.js con `Ctrl + C`.

Al refrescar la página, apareció el error: **"localhost rechazó la conexión"**, ya que la conexión con **Socket.IO no se pudo establecer** porque el servidor estaba apagado.

Después, volví a iniciar el servidor y recargué la página. Los errores desaparecieron y la conexión se restableció correctamente.

---

### Estado inicial de page2 comentado

Comenté la línea que envía el estado inicial de `page2` al servidor.  
Al reiniciar y mover la ventana de `page2`, noté que `page1` **no mostraba la información correcta** hasta que `page2` actualizaba su estado manualmente.

Cuando descomenté la línea, `page1` recibió el estado inicial de `page2` al conectarse.  
Esto permite que la información esté sincronizada desde el principio y mejora la comunicación entre las páginas.

---

### Comunicación entre páginas

Abrí ambas páginas (`page1` y `page2`) al mismo tiempo:

- Al mover la ventana de `page1`, en la consola de `page2` apareció el mensaje:
#### Page 2 received data about the other window: {x: 241, y: 54, width: 743, height: 664}

#### Esto ocurrió porque el servidor transmitió los datos de `page1` a `page2` mediante `broadcast.emit`.

- Al mover la ventana de `page2`, **no apareció ningún mensaje** en su consola.  
Esto se debe a que `page2` no estaba enviando nada al servidor que activara el evento `getdata`.

Esto demuestra que la sincronización entre páginas depende de qué datos cada una envía al servidor.

---

### Detección eficiente de cambios en page2
Cuando moví la ventana de `page2` muy lentamente, apareció en la consola el mensaje:
- Page 2 detected change…

### Este mensaje solo se mostró cuando había un **cambio real** en la posición o tamaño de la ventana.

Si la ventana no se movía, el mensaje no aparecía.

Este método compara el estado actual con el anterior antes de enviar datos.  
Es eficiente porque:

- Solo se envía información si realmente hay un cambio.
- Se reducen las actualizaciones innecesarias.
- Se optimiza el uso de recursos y mejora el rendimiento.

