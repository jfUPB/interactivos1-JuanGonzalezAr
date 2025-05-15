## Actividad 3

### Pausa activa: ¿Por qué es útil usar módulos o librerías?

Usar módulos como `express`, `http`, `socket.io` y `path` es útil porque:

- Ahorra tiempo.
- Evita escribir todo desde cero.
- Son herramientas probadas y confiables.
- Hacen el código más limpio y fácil de mantener.
- Aseguran compatibilidad entre sistemas operativos.
- Tienen comunidades grandes con soporte y recursos.

---

### Experimento: Cambiar carpeta de archivos estáticos

Cuando cambié la línea a:

- app.use(express.static(path.join(__dirname, 'archivos_cliente')));
- Y luego abrí http://localhost:3000/page1.html, apareció un error 404 (Not Found). Esto fue porque la carpeta archivos_cliente no existe.

- En la consola del navegador también apareció un error indicando que no se pudo cargar el recurso.

- Cuando volví a poner la carpeta views, todo funcionó bien porque esa sí existe y contiene los archivos
----.
## Experimento: Cambiar la ruta del servidor
### Acceder a:

- http://localhost:3000/page1 → No funciona (error 404).

- http://localhost:3000/pagina_uno → Sí funciona, el servidor devuelve page1.html.

- Esto ocurre porque cambié la ruta que el servidor reconoce.
---
## Experimento: Conexión y desconexión con Socket.IO
- Al abrir http://localhost:3000/page1, en la terminal del servidor aparece:Experimento: Cambiar la ruta del servidor
### Acceder a:

- http://localhost:3000/page1 → No funciona (error 404).

- http://localhost:3000/pagina_uno → Sí funciona, el servidor devuelve page1.html.

- Esto ocurre porque cambié la ruta que el servidor reconoce.
----
## Experimento: Conexión y desconexión con Socket.IO
#### Al abrir http://localhost:3000/page1, en la terminal del servidor aparece:
- A user connected - ID: BT5F2CyEbUYD6ypRAAAB
#### Al abrir http://localhost:3000/page2, aparece otro ID:
- A user connected - ID: xPU5OwouV64xD0RHAAAD
#### Al cerrar page2, aparece:
- User disconnected - ID: xPU5OwouV64xD0RHAAAD
---- 
### Experimento: Observando datos enviados
#### En page1, se ve:
- Data: { x: 100, y: 150, width: 200, height: 300 }
#### En page2, se ve:
- Received win2update from ID: 2n3gh92w10 Data: { x: 50, y: 75, width: 150, height: 250 }

### Prueba clave: Cambio en socket.emit
#### Cambié esta línea:

- socket.broadcast.emit('getdata', page1);
#### por esta otra:


- socket.emit('getdata', page1);
- Después de reiniciar el servidor, al mover la ventana en page1 no se actualizaba page2. Esto mostró que broadcast es necesario para enviar datos a los demás clientes, no al mismo.
--- 
### Experimento: Cambio de puerto del servidor
Cambié el puerto de 3000 a 3001 y reinicié el servidor. En la consola apareció:

- Server is listening on http://localhost:3001
- Al abrir http://localhost:3000/page1, no funcionaba. Pero http://localhost:3001/page1 sí cargó bien.

- Esto demuestra que el servidor solo responde en el puerto donde fue configurado con listen.

- Finalmente, volví a dejar el puerto en 3000 para seguir trabajando normalmente.
