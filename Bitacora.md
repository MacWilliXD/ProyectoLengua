# Bitacora "Proyecto Lengua"

## Día: 21 de enero del 2024
**BP_Jugador**

Movimiento Axis:
* Inputs (Axis Mappings) de movimientos de caminar del personaje.

    * **FrenteInput**: Movimiento hacia adelante y hacia atrás.
        * Verificación si la variable "CanMoveP?" está activa para agregar movimiento al input.

    * **LadosInput**: Movimiento hacia la derecha y hacia la izquierda.
        * Verificación si la variable "CanMoveP?" está activa para agregar movimiento al input.

Input (Axis Mappings)**CameraHorz**: movimiento de camara para el personaje. (Vista tercera persona)
* Condicionamiento provisional por si se necesita posteriormente.
* Agrega movimiento al controlador de Yaw.

Input (Action Mappings) **SaltoInput**: salto del jugador.
* Función por default de UE5 "Jump".
* Función por default de UE5 "Stop Jump".

Input (Action Mappings) **AgacharInput**: sistema de agachado del jugador.
* Condición para evitar cambiar de estado si ya se encuentra en uno.
        * IsCorriendo?
    * Presionar:

        * Velocidad de caminado a 125.0.

        * Variable "IsAgachado?" activada.

    * Soltar: 

        * Velocidad de caminado a 500 (Velocidad base).

        * Variable "IsAgachado?" desactivada.

Input (Action Mappings) **CorrerInput**: sistema de correr del jugador.
* Condición para evitar cambiar de estado si ya se encuentra en uno.
        * IsAgachado?
    
    * Presionar:

        * Velocidad de caminado a 1000.0.

        * Variable "IsCorriendo?" activada.

    * Soltar:

        * Velocidad de caminado a 500.0(Velocidad base).

        * Variable "IsCorriendo?" desactivada.


Input (Action Mappings) **GanchoInput**: sistema para lanzar un gancho que al impactar una superficie física lanzará al jugador hacia dicha dirección. Se mantendría presionado para poder apuntar mejor y al soltar lanzaría el proyectil.

* Presionar: 

    * Variable "CanMoveP?" desactivada.

* Soltar:

    * Line Trace By Channel
            
        * Lanza una linea de reconocimiento desde el punto de acople "Gancho Inicio".

        * Su punto de acople final es: "World Location" de "Gancho Inicio" sumado a la multiplicación del "Forward Vector" por la distancia máxima que se desee.

        * Se comprueba si la Line Trace chocó con una superficie para llamar al evento "Gancho".

Evento Gancho: Recibirá el punto de impacto del Line Trace para envíar al personaje o viceversa.
* Se va cambiando la posición del personaje mediante un "Set Actor Location".

* Timer Line que mediante una gráfica cosenoidal la cual irá desde la posición inicial hasta la final sin ir linealmente.

## Día: 27 de enero del 2024

Mejora en el impacto del Line Trace
* Usa el "Out Hit Location" para enviarselo al evento "Gancho".

* Envía el tipo de objeto al que impactó el Line Trace.

**Blender Models:**
* Personaje del jugador:
    * personaje completado en su modelo (Faltan los huesos y animaciones).


## Día: 30 de enero del 2024

Agregados los huesos y pintado el peso dentro de los meshes

## Día: 3 de febrero del 2024

**Animaciones**
(Se deben mejorar)

* [x] Idle
* [x] Walk
* [x] Run (Posible mejora)


**Outliners**

Agregado al proyecto para que se vea una linea negra alrededor de los modelos de los personajes y estruturas. Puro estilo cartoon.


## Día: 5 de febrero del 2024
**Los agregados son placeholders**

Agregado el modelo y las animaciones a unreal engine

Añadido un blueprint de animación

Añadido un blendspace de animación para obtener la velocidad del jugador y cambiar de animación de Idle -> Walk -> Run


## Día: 08 de febrero del 2024

Añadido sistema de cambio de animaciones y mejorado para que pudiera cambiar entre diferentes animaciones (fuera de la caminata)

Añadido animación de agachado