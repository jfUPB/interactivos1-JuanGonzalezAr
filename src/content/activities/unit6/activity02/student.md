## Actividad 2

### Pausa activa 1: Mi rampa de acceso a Internet

En mi casa me conecto a Internet por Wi-Fi, que viene de un módem conectado al proveedor. En la universidad también uso Wi-Fi, pero a veces uso cable Ethernet si quiero mejor conexión. Si se cae el Wi-Fi o se desconecta el cable, pierdo acceso a Internet. Eso significa que no puedo cargar páginas, usar apps en línea o enviar/recibir datos. Es como si el carro se quedara en el garaje sin poder salir.

---

### Pausa activa 2: Relación Cliente-Servidor en la vida diaria

Un ejemplo es un restaurante:

- **Cliente:** Yo, cuando voy a pedir comida.
- **Servidor:** El mesero.
- **Petición:** “Quiero una hamburguesa con papas.”
- **Respuesta:** El mesero trae la comida.

---

### Pausa activa 3: Analizando una URL

URL: `https://www.youtube.com/watch?v=dQw4w9WgXcQ`

- **Protocolo:** `https://`
- **Dominio:** `www.youtube.com`
- **Ruta:** `/watch`
- **Parámetro:** `?v=dQw4w9WgXcQ` (dice qué video ver)

Si solo pongo el dominio `www.youtube.com`, me carga la página principal de YouTube.

---

### Pausa activa 4: HTTP vs protocolos seriales

- **Similitudes:** Ambos definen cómo enviar y recibir mensajes.
- **Diferencias:** HTTP es más complejo, tiene tipos de contenido, métodos (como GET), códigos de estado. Los seriales son más simples y cercanos al hardware.

**¿Por qué HTTP es más complejo?**
Porque maneja muchos tipos de contenido y funciona entre dispositivos diferentes a través de Internet.

---

### Pausa activa 5: Analizando una página de login

**HTML:**
- Campos de usuario y contraseña.
- Botón de “Iniciar sesión”.
- Textos y títulos.

**CSS:**
- Colores, tipo y tamaño de letra.
- Estilo del botón.

**JavaScript:**
- Validación de campos.
- Mostrar errores sin recargar.
- Redirigir si el login es correcto.

---

### Pausa activa 7: draw() vs eventos

**Ventajas de los eventos:**
- Más eficiente: solo se ejecuta cuando pasa algo.
- Ahorra recursos y batería.
- Facilita el diseño modular.

**¿draw() sería eficiente?**
No. Redibujar 60 veces por segundo sin cambios es un gasto innecesario. Los eventos son mejores cuando los cambios son pocos.

---

### Pausa activa 8: JavaScript en cliente y servidor

**Ventajas:**
- Solo se necesita un lenguaje.
- Se puede reutilizar código.
- Mejora la productividad.
- Más rápido desarrollar.

---

### Pausa activa final: HTTP vs WebSockets / Socket.IO

**HTTP:**
- Una petición para cada
