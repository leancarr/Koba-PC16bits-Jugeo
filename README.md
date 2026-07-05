# Koba-PC16bits-Juego

## Minijuego: Donkey Kong

**Integrantes:** Leandro Caraballo, Antonio Gomez, Facundo Naveira, Luca Mamani

El juego es un clásico de plataformas de pantallas fijas donde todo el reto pasa por la precisión, el ritmo y el cálculo de tiempos.

### ¿Cómo se juega y cuáles son las mecánicas?

Controlás a un personaje bastante limitado en sus movimientos: solo podés moverte de izquierda a derecha, subir o bajar escaleras, y saltar. El gran desafío es el diseño de los niveles, que están llenos de plataformas inclinadas y rampas.

A medida que intentás subir, te caen un montón de barriles desde arriba. Algunos bajan rodando en línea recta y otros caen de golpe por las escaleras, por lo que tenés que calcular muy bien el tiempo para saltarlos en el momento justo o esperarlos en una zona segura.

Además de los barriles, hay otros peligros móviles, como unas pequeñas llamas de fuego que aparecen de repente y te empiezan a perseguir de forma bastante impredecible por todo el mapa. Para defenderte, en algunas pantallas hay martillos flotando. Si saltás y agarrás uno, tu personaje empieza a golpear automáticamente hacia adelante durante unos segundos; esto te permite destruir cualquier barril o fuego que se te cruce, pero tiene una desventaja: mientras tenés el martillo, no podés saltar ni subir escaleras, quedando atrapado en esa plataforma hasta que se le termine el efecto.

---

## Escenarios o pantallas del juego

### Escenario 1: Los Barriles (Ramps / 25m)

Transcurre en la base de la construcción.

* **Dinámica:** Al principio de la pantalla, Donkey Kong pisa fuerte, rompe la estructura (por eso las vigas quedan inclinadas) y empieza a tirar barriles desde arriba hacia abajo.
* **El tacho de aceite:** Está abajo a la izquierda. Si un barril azul de DK cae ahí, se prende fuego y genera el primer enemigo "fueguito", que empieza a subir las escaleras para perseguir al jugador.
* **El martillo:** Hay dos martillos que se pueden agarrar para destruir barriles y fueguitos por unos segundos.
* **Objetivo:** Subir esquivando o saltando barriles y usar las escaleras hasta llegar a la plataforma superior donde está Pauline.

### Escenario 2: La Fábrica de Cemento (Conveyor Belts / 50m)

Transcurre en una planta de procesamiento.

* **Dinámica:** Hay tres pisos con cintas transportadoras móviles. Dos van hacia una dirección y la del medio va al revés. Sobre las cintas se mueven unas "cajas de cemento" que te matan si te tocan.
* **Invasión de fueguitos:** En esta pantalla no hay barriles. El peligro principal son múltiples fueguitos que salen constantemente de los dos hornos/tachos de aceite que están en el centro del mapa. Se mueven por todos lados subiendo y bajando escaleras.
* **Escaleras móviles:** Hay escaleras que suben y bajan o se cortan a la mitad de forma intermitente, obligándote a calcular el tiempo justo para subir.
* **Objetivo:** Llegar a la cima sorteando el cemento y la intensa presión de los fueguitos.

### Escenario 3: Los Ascensores (Elevators / 75m)

Una pantalla que requiere muchísima precisión y cálculo de saltos.

* **Dinámica:** El mapa está dividido en varias columnas. La principal atracción son dos líneas de ascensores verticales que se mueven sin parar (una sube y la otra baja).
* **Los rebotadores (Bouncers):** Desde arriba, Donkey Kong tira unas vigas o resortes mecánicos que rebotan por la parte superior de la pantalla y caen al vacío justo por donde pasan los ascensores.
* **Los fueguitos:** Hay un par controlando las plataformas fijas para complicarte la subida inmediatamente después de salir del ascensor.
* **Objetivo:** Subir usando los ascensores en movimiento, esquivar los rebotadores calculando su parábola de caída y trepar por las escaleras del lado derecho hasta arriba de todo.

### Escenario 4: Los Remaches (Rivets / 100m)

La batalla final de cada nivel. Acá no tenés que "llegar hasta Donkey Kong", sino ganarle por ingenio desarmando la estructura.

* **Estrategia de desarme:** El escenario está sostenido por 8 remaches amarillos brillantes en el suelo. El jugador tiene que caminar o saltar sobre ellos; al pasar por arriba, el remache desaparece.
* **Presión constante:** Mientras intentás sacar los remaches, varios fueguitos te persiguen de cerca. Como el mapa se va desarmando a medida que sacás los remaches, los caminos se vuelven callejones sin salida tanto para vos como para ellos.
* **Objetivo:** Quitar los 8 remaches. Cuando sacás el último, toda la estructura de vigas se desploma, Donkey Kong cae de cabeza quedando desmayado y se rescata a Pauline.

### Del nivel 2 en adelante (El Loop de Dificultad Infinito)

Al terminar la pantalla 4, el juego vuelve a la pantalla 1 avanzando de nivel de forma matemáticamente infinita. Para honrar el comportamiento de los arcades de los años 80, no existe un límite de niveles programado en el flujo de la CPU. 

La dificultad escala de manera orgánica e imperceptible entre niveles utilizando aritmética de punto fijo de 32 bits. En cada cambio de nivel, el sistema aplica un incremento fraccionario a las siguientes variables físicas del juego:
* **Aceleración Fraccionaria de Sprites:** La velocidad de los barriles, rebotadores y fueguitos aumenta en un delta de píxel sutil por nivel. Esto genera una curva de aceleración suave donde el juego se siente cómodo al principio, pero acumula una velocidad frenética a medida que se encadenan los loops.
* **Reducción de Ventanas de Spawn:** El temporizador de la CPU encargado de generar nuevos enemigos disminuye su ciclo de espera remanente, provocando que los tachos de aceite y Donkey Kong saturen los escenarios con mayor densidad de peligros en niveles avanzados.
* **Presión del Temporizador:** El contador de *Bonus* de tiempo inicial se reduce levemente en cada nivel, obligando al jugador a ejecutar rutas perfectas sin margen de duda.

---

### ¿Cómo se gana?

Al tratarse de un sistema arcade genuino, **no existe una condición de victoria absoluta ni una pantalla de fin de juego exitoso**. El juego está diseñado bajo el concepto de la **superación de puntaje y el desafío biológico**. 

El software correrá de forma indefinida loops de las 4 pantallas principales. El verdadero objetivo del jugador es la optimización de sus movimientos para alcanzar el "High Score" más alto posible y poner a prueba sus reflejos en la curva de dificultad matemática, la cual eventualmente superará la velocidad de respuesta humana (convirtiéndose en un desafío prácticamente imposible alrededor del nivel 10 o 12). La victoria es la superación del propio récord.

### ¿Cómo se pierde?

Disponés de un número limitado de vidas (3 por defecto). Perdés una vida instantáneamente si:

* Te toca un barril, un fueguito o cualquier caja de cemento.
* Te caés desde una plataforma que esté demasiado alta (el personaje no soporta caídas de gran altura y muere al impactar).
* Se te termina el tiempo. Hay un contador de *Bonus* en la esquina de la pantalla que baja constantemente; si llega a cero antes de cumplir el objetivo de la pantalla, se pierde la vida de inmediato.

Si te quedás sin vidas en reserva, la partida se termina de manera definitiva (*Game Over*).

### El sistema de puntos

Prácticamente todas las acciones recompensan al jugador para incentivar la competencia por el récord:

* **El bonus de tiempo:** Al terminar una pantalla, todo el valor restante en el contador de tiempo se transforma directamente en puntos netos para el marcador.
* **Saltar obstáculos:** Cada salto exitoso por encima de un barril o de un fueguito premia al jugador con puntos extra en tiempo real.
* **Destruir enemigos:** Al recolectar el martillo, cada barril o llama machacada suma una gran cantidad de puntos.
* **Agarrar objetos perdidos:** Dispersos por los escenarios se encuentran los accesorios de Pauline (carteras, sombreros, paraguas) que otorgan un fuerte empuje al puntaje al ser recolectados.
* **Vida extra:** Al alcanzar un umbral de puntuación alto determinado (ej. 7000 puntos), el sistema recompensa al jugador otorgándole una vida adicional para extender su partida.

### Sprites Base

<img width="600" height="320" alt="spritesGeneral" src="https://github.com/user-attachments/assets/86006d83-bc70-4d55-9ecf-84ee5723bb20" />

### Mapa de Sprites Fueguito:

<img width="256" height="128" alt="New Piskel" src="https://github.com/user-attachments/assets/7fb60c23-7f1b-4bdb-bd77-491d7538f71d" />

### Sprites Barriles:

<img alt="Sprites Barriles" src="./Sprites/Sprites%20barriles%20juntos.png" />
