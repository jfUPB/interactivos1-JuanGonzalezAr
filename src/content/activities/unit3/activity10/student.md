## 🧩 Consolidación – Análisis sobre máquinas de estado y pruebas
### 🧠 ¿Por qué es poderosa la técnica de máquina de estados para la escalabilidad y el manejo de eventos?
La técnica de máquina de estados es muy poderosa porque permite organizar el comportamiento de una aplicación en secciones claras, donde cada estado representa una situación específica del sistema. Esto facilita que la aplicación:

1. Escale mejor, ya que se pueden añadir nuevos estados sin romper el código existente.

2. Maneje eventos concurrentes, porque cada entrada o estímulo (como presionar un botón o recibir datos) puede redirigir al sistema a otro estado, permitiendo respuestas rápidas y organizadas.

3. Sea más fácil de mantener y depurar, ya que el flujo de ejecución es más predecible y está claramente definido.

4. En aplicaciones como la bomba o un semáforo digital, donde hay eventos constantes y cambios en el tiempo, este enfoque permite tener un control preciso y modular.

### ✅ Ventajas y desventajas del tipo de pruebas realizadas
#### Ventajas:
- Permiten detectar errores funcionales básicos rápidamente.

- Ayudan a verificar si los estados se están activando correctamente.

- Son útiles para validar la interacción entre p5.js y el micro:bit (entrada/salida de datos, visualización de cambios, etc.).

#### Desventajas:
- Las pruebas fueron mayormente manuales, lo que puede llevar a pasar por alto errores intermitentes o sutiles.

- No siempre se prueba todo el sistema en conjunto, lo que deja algunas dependencias sin verificar.

- Falta de automatización y documentación en las pruebas limita su reutilización.

### 🔁 Importancia de las pruebas de regresión
Las pruebas de regresión son esenciales porque aseguran que los cambios en el código no afecten funcionalidades que ya estaban funcionando correctamente. Si no se realizan estas pruebas:

1. Se pueden introducir errores ocultos que no son visibles de inmediato.

2. Se pierde la confianza en la estabilidad del sistema, ya que no se tiene certeza de qué sigue funcionando y qué no.

3. El mantenimiento del código se vuelve más riesgoso, sobre todo en proyectos grandes o en colaboración con otros.

- En resumen, las pruebas de regresión son una herramienta clave para construir aplicaciones confiables y escalables, especialmente cuando se trabaja con múltiples estados, entradas y salidas como en el caso de los microcontroladores.
