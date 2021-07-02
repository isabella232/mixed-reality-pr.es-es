---
title: Servicio de simulación de entrada
description: Documentación sobre el servicio de simulación de entrada en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 66b79c14bbd0ea8c188aba684b9bd1034de31bf9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176962"
---
# <a name="input-simulation-service"></a>Servicio de simulación de entrada

![Simulación de entrada de MRTK](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

Con la simulación de entrada de MRTK, puede probar varios tipos de interacciones en el editor de Unity sin necesidad de compilar e implementar en un dispositivo. Esto le permite iterar rápidamente sus ideas en el proceso de diseño y desarrollo. Use combinaciones de teclado y mouse para controlar entradas simuladas.

El servicio de simulación de entrada emula el comportamiento de los dispositivos y plataformas que pueden no estar disponibles en el editor de Unity. Algunos ejemplos son:

* HoloLens o seguimiento de la cabeza del dispositivo vr
* HoloLens gestos de mano
* HoloLens 2 de mano articulado
* HoloLens 2 seguimiento de los ojos
* Controladores de dispositivo vr

> [!WARNING]
> Esto no funciona cuando se usa la emulación holográfica XR de Unity > modo de emulación = "Simular en el editor". La simulación en el editor de Unity quitará el control de la simulación de entrada de MRTK. Para usar el servicio de simulación de entrada DE MRTK, deberá establecer emulación holográfica XR en Modo de emulación = *"None"*

## <a name="how-to-use-mrtk-input-simulation"></a>Uso de la simulación de entrada de MRTK 

La simulación de entrada está habilitada de forma predeterminada en los perfiles que se envían con MRTK. Simplemente puede hacer clic en **el botón Reproducir** para ejecutar la escena con compatibilidad con la simulación de entrada.

* Presione **las teclas W, A, S, D, Q, E** para mover la cámara.
* Mantenga presionado **el botón derecho del mouse** y mueva el mouse para mirar alrededor.
* Para abrir las manos simuladas, presione **Barra espaciador (mano derecha)** o Tecla **Mayús izquierda (mano izquierda)**
* Para mantener las manos simuladas en la vista, presione **la tecla T** o **Y.**
* Para girar las manos simuladas, mantenga presionada la **tecla Ctrl y** mueva el mouse.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a>En la hoja de datos de simulación de entrada del editor

Presione **Ctrl+ H a** la izquierda en la escena HandInteractionExamples para abrir una hoja de trucos con controles de simulación de entrada.

> ![Hoja de datos de simulación de entrada de MRTK](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a>Habilitación del servicio de simulación de entrada

En la configuración del proveedor de datos del sistema de entrada, el servicio Simulación de entrada se puede configurar con lo siguiente.

* **El** tipo debe *ser Microsoft.MixedReality.Toolkit. Input > InputSimulationService*.
* **Las plataformas admitidas de** forma predeterminada incluyen todas las *plataformas del editor,* ya que el servicio usa la entrada del teclado y del mouse.

> [!NOTE]
> El servicio Simulación de entrada se puede usar en otros puntos de conexión de la plataforma, como independiente, cambiando la propiedad **Plataformas admitidas** para incluir los destinos deseados.
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a>Control de cámara

El servicio de simulación de entrada puede emular el movimiento de la cabeza.

### <a name="rotating-the-camera"></a>Rotación de la cámara

1. Mantenga el puntero sobre la ventana del editor de ventanilla.
    *Es posible que tenga que hacer clic en la ventana para darle el foco de entrada si las pulsaciones de botón no funcionan.*
1. Mantenga presionado el Botón **de vista del mouse (valor** predeterminado: botón derecho del mouse).
1. Mueva el mouse en la ventana de la ventanilla para girar la cámara.
1. Use la rueda de desplazamiento para enrollar la cámara alrededor de la dirección de la vista.

La velocidad de rotación de la cámara se puede configurar cambiando el valor de Velocidad de apariencia del **mouse** en el perfil de simulación de entrada.

Como alternativa, use los ejes **Look Horizontal** Look Vertical (Look Horizontal Look Vertical) para girar la cámara (valor predeterminado: el control de posición derecho del /  controlador de juegos).

### <a name="moving-the-camera"></a>Movimiento de la cámara

Use los **ejes Mover horizontalmente** verticalmente para mover la cámara (valor predeterminado: teclas WASD o el control de posición izquierdo /  del controlador de juego).

Los ángulos de posición y rotación de la cámara también se pueden establecer explícitamente en la ventana de herramientas. La cámara se puede restablecer a su valor predeterminado mediante el **botón Restablecer.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>Simulación de controlador

La simulación de entrada admite dispositivos de controlador emulados (es decir, controladores de movimiento y manos). Estos controladores virtuales pueden interactuar con cualquier objeto que admita controladores normales, como botones u objetos que se pueden agarrar.

### <a name="controller-simulation-mode"></a>Modo de simulación de controlador

En la ventana [de herramientas de simulación de entrada,](#input-simulation-tools-window) la opción **Default Controller Simulation Mode** (Modo de simulación de controlador predeterminado) cambia entre tres modelos de entrada distintos. Este modo predeterminado también se puede establecer en el perfil de simulación de entrada.

* *Manos articuladas:* simula un dispositivo de mano totalmente articulado con datos de posición conjunta.

   Emula HoloLens 2 de interacción.

   Las interacciones basadas en el posicionamiento preciso de la mano o el uso de tocar se pueden simular en este modo.

* *Gestos con la* mano: simula un modelo de mano simplificado con pulsación de aire y gestos básicos.

   Emula HoloLens [de interacción .](/windows/mixed-reality/gestures)

   El foco se controla mediante el puntero Mirada. El *gesto De pulsación* en el aire se usa para interactuar con botones.

* *Controlador de movimiento:* simula un controlador de movimiento que se usa con cascos vr que funciona de forma similar a las interacciones lejanas con las manos articuladas.

   Emula el casco vr con el modelo de interacción de controladores.

   Las teclas de desencadenador, toma y menú se simulan mediante la entrada del teclado y del mouse.

### <a name="simulating-controller-movement"></a>Simulación del movimiento del controlador

Mantenga presionada la tecla **de** manipulación del controlador izquierdo/derecho (valor *predeterminado:* Desplazamiento a la izquierda para el controlador izquierdo y Espacio para el controlador derecho) para obtener el control de cualquiera de los controladores.  Mientras se presiona la tecla de manipulación, el controlador aparecerá en la ventanilla. Una vez que se libera la clave de manipulación, los controladores desaparecerán después de un breve **tiempo de espera de ocultación del controlador.**

Los controladores se pueden activar y inmovilizar [](#input-simulation-tools-window) con respecto a la cámara en la ventana de herramientas de simulación de entrada o presionando alternar la tecla del controlador **izquierdo/derecho** (valor predeterminado: *T* para la izquierda e *Y* para la derecha). Presione de nuevo la tecla de alternancia para ocultar los controladores de nuevo. Para manipular los controladores, es necesario mantener la clave **de** manipulación del controlador izquierdo/derecho. Pulsar dos veces la **tecla de manipulación del controlador izquierdo/derecho** también puede activar o desactivar los controladores.

El movimiento del mouse moverá el controlador en el plano de vista. Los controladores se pueden mover más o más cerca de la cámara mediante la **rueda del mouse.**

Para girar los controladores con el mouse, mantenga presionada la  tecla de manipulación del controlador izquierdo/derecho **(mayús** a la izquierda o *espacio)* y el botón de rotación del controlador **(valor** predeterminado: botón *Ctrl* izquierdo) y, a continuación, mueva el mouse para girar el controlador. La velocidad de rotación del controlador se puede configurar cambiando el valor de Velocidad de rotación del controlador del **mouse** en el perfil de simulación de entrada.

Toda la colocación de las manos también puede cambiar en la ventana de herramientas de [simulación de entrada,](#input-simulation-tools-window)incluido el restablecimiento de las manos al valor predeterminado.

### <a name="additional-profile-settings"></a>Configuración de perfil adicional

* **El multiplicador de profundidad del controlador** controla la sensibilidad del movimiento de profundidad de la rueda de desplazamiento del mouse. Un número mayor acelerará el zoom del controlador.
* **Distancia predeterminada del controlador** es la distancia inicial de los controladores desde la cámara. Al hacer clic **en los controladores** del botón Restablecer también se colocarán los controladores a esta distancia.
* **Cantidad de vibración del controlador** agrega movimiento aleatorio a los controladores. Esta característica se puede usar para simular un seguimiento incorrecto del controlador en el dispositivo y asegurarse de que las interacciones funcionan bien con entrada ruidosa.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>Gestos con la mano

También se pueden simular gestos con la mano, como el gesto de acercamiento, la captura, el movimiento de los dedos, etc.

1. Habilitar el control de mano mediante la **tecla de manipulación del controlador izquierdo/derecho** *(desplazamiento a la* izquierda o *espacio)*

2. Durante la manipulación, mantenga presionado un botón del mouse para realizar un gesto con la mano.

Cada uno de los botones del mouse se puede asignar para transformar la forma de la mano en un gesto diferente mediante la configuración gesto de la mano *izquierda, media/derecha.* El *gesto de mano predeterminado* es la forma de la mano cuando no se presiona ningún botón.

> [!NOTE]
> El *gesto* Desenlazador es el único gesto que realiza la acción "Seleccionar" en este momento.

### <a name="one-hand-manipulation"></a>Manipulación con una mano

1. Mantenga presionada la **tecla de manipulación del controlador izquierdo/derecho** *(desplazamiento a la* izquierda o *espacio)*
2. Apuntar al objeto
3. Mantener presionado el botón del mouse para acercar
4. Uso del mouse para mover el objeto
5. Suelte el botón del mouse para detener la interacción.

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>Manipulación a dos manos

Para manipular objetos con dos manos al mismo tiempo, se recomienda el modo de mano persistente.

1. Para alternar en ambas manos, presione las teclas de alternancia *(T/Y).*
1. Manipular una mano a la vez:
    1. Mantener **presionado el** espacio para controlar la mano derecha
    1. Mover la mano a donde desea agarrar el objeto
    1. Presione el **botón izquierdo del mouse** para activar el gesto *Desenlazador.*
    1. Espacio **de liberación** para detener el control de la mano derecha. La mano se inmovilizará en su  lugar y se bloqueará en el gesto Desenlazador, ya que ya no se está manipulando.
1. Repita el proceso con la otra mano, agarrándose el mismo objeto en un segundo lugar.
1. Ahora que ambas manos están tomando el mismo objeto, puede mover cualquiera de ellos para realizar la manipulación con dos manos.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>Interacción de GGV (mirada, gesto y voz)

De forma predeterminada, la interacción de GGV está habilitada en el editor, mientras que no hay manos articuladas presentes en la escena.

1. Girar la cámara para apuntar el cursor de mirada al objeto interactuable (botón derecho del mouse)
1. Haga clic y mantenga presionado **el botón izquierdo del mouse** para interactuar.
1. Girar la cámara de nuevo para manipular el objeto

Puede desactivar esta opción si desactiva la opción *Is Hand Free Input Enabled* (Está habilitada la entrada disponible a mano) dentro del perfil de simulación de entrada.

Además, puede usar manos simuladas para la interacción con GGV.

1. Para habilitar la simulación de GGV, cambie **el modo de simulación de mano** a *Gestos* en el perfil [de simulación de entrada.](#enabling-the-input-simulation-service)
1. Girar la cámara para apuntar el cursor de mirada al objeto interactuable (botón derecho del mouse)
1. Mantener **presionado el** espacio para controlar la mano derecha
1. Haga clic y mantenga presionado **el botón izquierdo del mouse** para interactuar.
1. Uso del mouse para mover el objeto
1. Suelte el botón del mouse para detener la interacción.

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>Generar eventos de teleport

Para generar el evento de teleport en la simulación de entrada, configure el  gesto de mano Configuración en  el perfil de simulación de entrada para que uno realice el gesto de inicio de teleportar mientras que el otro realiza el gesto de fin de teleportar. El **gesto Teleport Start** (Inicio de Teleport) mostrará el puntero **teleport,** mientras que la gesure Teleport End completará la acción de teleportar y moverá al usuario.

La posición y del teleportador resultante depende del desplazamiento de la cámara a lo largo del eje Y. En el editor, es 0 de forma predeterminada, así que use las teclas **Q** y **E** para ajustarlo al alto adecuado.

![Teleportador de simulación de entrada Configuración](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>Interacción del controlador de movimiento

Los controladores de movimiento simulados se pueden manipular de la misma manera que las manos articuladas. El modelo de interacción es similar a la interacción lejana de la mano articulada, mientras que el desencadenador, las teclas de agarre y de menú se asignan al botón izquierdo del *mouse,* las teclas *G* y *M,* respectivamente.

### <a name="eye-tracking"></a>Seguimiento de los ojos

[La simulación de seguimiento](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) de los ojos se puede habilitar activando la **opción Simular posición** de los ojos en el perfil de [simulación de entrada](#enabling-the-input-simulation-service). Esto no debe usarse con interacciones de estilo GGV o de controlador de movimiento (así que asegúrese de que el modo de simulación de controlador predeterminado está establecido en *Mano articulada).* 

## <a name="input-simulation-tools-window"></a>Ventana Herramientas de simulación de entrada

Habilite la ventana de herramientas de simulación de entrada **desde el Mixed Reality** Toolkit Simulación de entrada  >    >    >  **de** utilidades. Esta ventana proporciona acceso al estado de la simulación de entrada durante el modo de reproducción.

## <a name="viewport-buttons-optional"></a>Botones de ventanilla (opcional)

Se puede especificar un elemento prefab para los botones en el editor para controlar la colocación de la mano básica en el perfil de simulación de entrada en **Indicadores prefab**. Se trata de una utilidad opcional, se puede acceder a las mismas características en la ventana de herramientas [de simulación de entrada](#input-simulation-tools-window).

> [!NOTE]
> Los indicadores de ventanilla están deshabilitados de forma predeterminada, ya que actualmente pueden interferir con las interacciones de la interfaz de usuario de Unity. Vea el problema [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106). Para habilitarlo, agregue el prefab InputSimulationIndicators a **Indicators Prefab**.

Los iconos de mano muestran el estado de las manos simuladas:

* ![Icono de mano sin seguimiento](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) La mano no está en el seguimiento. Haga clic para habilitar la mano.
* ![Icono de mano con seguimiento](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Icono de mano con seguimiento") El usuario realiza el seguimiento de la mano, pero no la controla. Haga clic para ocultar la mano.
* ![Icono de la mano controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Icono de la mano controlada") El usuario realiza el seguimiento y el control de la mano. Haga clic para ocultar la mano.
* ![Icono de restablecimiento de la mano](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Icono de restablecimiento de la mano") Haga clic para restablecer la mano a la posición predeterminada.


## <a name="see-also"></a>Consulte también

* [Perfil del sistema de entrada](../input/input-providers.md).
