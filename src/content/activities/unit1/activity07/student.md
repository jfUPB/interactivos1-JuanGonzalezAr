# Assassin's Creed: Caso de estudio
Assassin's Creed, desarrollado por Ubisoft, es conocido por sus vastos y detallados entornos urbanos, 
los cuales están basados en ciudades históricas como Jerusalén, Venecia, y París. 
El uso del diseño generativo en la creación de estos mundos no es tan obvio como en los juegos procedurales, 
pero se aplica en ciertos aspectos clave,
como la creación de edificios, calles, y la generación dinámica de actividades dentro de las ciudades.
## Como se aplico el diseño generativo:
1. Input (Entradas):
- Datos históricos: En Assassin's Creed, las ciudades están basadas en representaciones históricas reales, por lo que se recogen datos de arquitectura, distribución urbana, y eventos importantes.
- Reglas de navegación y rutas: Los algoritmos generan calles y rutas de navegación optimizadas para el desplazamiento de los personajes (por ejemplo, las techumbres y los edificios a los que el protagonista puede saltar).
- Comportamiento y poblaciones: Parámetros de IA como el comportamiento de los ciudadanos, patrones de tráfico, y las interacciones con los jugadores.
2. Procesamiento:
- Generación del terreno y las calles: Aunque la ciudad en sí no es completamente generada proceduralmente, las reglas de diseño generativo se utilizan para crear la disposición de edificios, calles, y áreas clave de la ciudad.
- Población dinámica: La IA controla el comportamiento de los NPCs en las calles (marcha, interacciones, reacciones a eventos). Los algoritmos generativos ayudan a decidir la distribución de estos NPCs, así como las interacciones que ocurren entre ellos y el jugador.
- Simulación de actividades: Se simulan eventos generados dinámicamente, como festivales, protestas o persecuciones, que pueden cambiar según el contexto de la misión o el estado de la ciudad en el juego.
3. Output:
- Ciudades vibrantes y dinámicas: Las ciudades dentro de Assassin's Creed tienen un aspecto único en cada partida, con personas, mercados, y lugares de interés que varían en cada entorno.
- Eventos procedurales: Los NPCs no siguen una ruta fija; su comportamiento y actividad dentro de la ciudad se adaptan de acuerdo con el contexto del jugador (por ejemplo, reaccionan a las acciones del protagonista o al entorno).
- Interacciones en tiempo real: La IA de la ciudad permite que las calles cambien y respondan de manera interactiva al jugador, como el aumento de la vigilancia o la evasión de guardias según el nivel de notoriedad del jugador.
## Impacto en la experiencia de usuario:
1.Inmersión y Realismo:
- La ciudad generada dinámicamente responde a las acciones del jugador, creando una experiencia inmersiva donde cada ciudad parece viva y cambiante. Esto no solo refleja el mundo real, sino que hace que el jugador se sienta más involucrado y conectado con el entorno.
2. Rejugabilidad:
- La variabilidad de las interacciones con los NPCs y el comportamiento dinámico de la ciudad aseguran que no haya dos visitas iguales a la misma ciudad. Las situaciones, las interacciones y los eventos cambiarán con cada nueva partida, lo que aumenta la rejugabilidad.
3. Libertad de exploración:
- El diseño generativo también facilita la navegación en el mundo abierto. Los edificios, las rutas de escape y las oportunidades de saltar entre los tejados generan una experiencia fluida de exploración, permitiendo que el jugador se mueva con libertad a través de entornos urbanos complejos.
4. Desafíos en el diseño:
- El desafío de generar una ciudad abierta de manera convincente no solo depende de los algoritmos generativos, sino también de equilibrar la fidelidad histórica con la jugabilidad. Es necesario un equilibrio entre crear un entorno inmersivo y ofrecer un mundo accesible para la experiencia de juego.
