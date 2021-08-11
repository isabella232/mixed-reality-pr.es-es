---
title: Controladores de movimiento
description: Aprenda a configurar, emparejar y administrador las interacciones de entrada mediante Mixed Reality de movimiento en las aplicaciones.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Controladores de 6dof, controladores de movimiento, emparejamiento, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, HoloLens, desplazamiento, control, estado
ms.openlocfilehash: bced0115eee5e753ef01d129ae10910acdca2b7b91020117f53b2ebf8833a130
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224923"
---
# <a name="motion-controllers"></a>Controladores de movimiento

:::row:::
    :::column:::
        Los controladores de movimiento [son accesorios de hardware](../discover/hardware-accessories.md) que permiten a los usuarios tomar medidas en realidad mixta. Una ventaja de los controladores de movimiento sobre los [gestos](gaze-and-commit.md#composite-gestures) es que los controladores tienen una posición precisa en el espacio, lo que permite una interacción más precisa con objetos digitales. Para Windows Mixed Reality cascos envolventes, los controladores de movimiento son la forma principal de que los usuarios tomen medidas en su mundo.<br>
        <br>
        *Imagen: un controlador Windows Mixed Reality movimiento*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality controladores de movimiento](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Característica</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Controladores de movimiento</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Detalles del hardware

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality de movimiento ofrecen un seguimiento preciso y dinámico del movimiento en el campo de visión mediante los sensores del casco envolvente. No es necesario instalar hardware en las paredes del espacio. Estos controladores de movimiento ofrecen la misma facilidad de configuración y portabilidad que Windows Mixed Reality cascos envolventes. Nuestros asociados de dispositivos planean comercializar y vender estos controladores en tiendas minoristas esta semana.

![Conocer el controlador](images/controllerimage-750px.png)<br>
*Conocer el controlador*

**Características**
* Seguimiento óptico
* Desencadenador
* Botón Desgarr
* Stick
* Panel táctil

## <a name="setup"></a>Configurar

### <a name="before-you-begin"></a>Antes de empezar

**Necesitará:**
* Un conjunto de dos controladores de movimiento.
* Cuatro baterías AA.
* Un equipo con compatibilidad Bluetooth 4.0.

**Comprobación de Windows, Unity y actualizaciones de controladores**
* Visite [Instalación de las herramientas](../develop/install-the-tools.md) para las versiones preferidas de Windows, Unity, entre otras, para el desarrollo de realidad mixta.
* Asegúrese de que tiene los controladores de controladores de movimiento y casco más [actualizados.](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)

### <a name="pairing-controllers"></a>Emparejamiento de controladores

Los controladores de movimiento se pueden unir con el equipo host mediante Windows configuración como cualquier otro Bluetooth dispositivo.

1. Inserte dos baterías AA en la parte posterior del controlador. Deje la cubierta de la batería apagada por ahora.
2. Si usa un adaptador de Bluetooth USB externo en lugar de una radio Bluetooth [](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) integrada, revise los procedimientos recomendados de Bluetooth antes de continuar. Para la configuración de escritorio con radio integrada, asegúrese de que la antena está conectada.
3. Abra **Windows Configuración** dispositivos agregar Bluetooth u otros dispositivos Bluetooth y quite las instancias anteriores de "Controlador de movimiento – Derecha" y "Controlador de movimiento  ->    ->    ->   – Izquierda". Compruebe también la categoría Otros dispositivos en la parte inferior de la lista.
4. Seleccione **Agregar Bluetooth u otro dispositivo y** vea que empieza a detectar Bluetooth dispositivos.
5. Mantenga presionado el botón de Windows del controlador para activar el controlador y suéltelo cuando suba el timbre.
6. Mantenga presionado el botón de emparejamiento (tabulación en el compartimiento de la batería) hasta que los LED empiecen a pulsar.

:::row:::
    :::column:::
7. Espere "Controlador de movimiento - Izquierda" o "Controlador de movimiento - Derecha" para aparecer en la parte inferior de la lista. Seleccione esta opción para emparejar. El controlador se vibración una vez cuando se conecta.<br>
        <br>
        *Imagen: seleccione "Controlador de movimiento" para emparejar; si hay varias instancias, seleccione una en la parte inferior de la lista.*
    :::column-end:::
        :::column:::
       ![Seleccione Controlador de movimiento para emparejar, si varias instancias seleccionan una de las que aparecen en la parte inferior de la lista.](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. Verá que el controlador aparece en la configuración de Bluetooth en la categoría **"Mouse, teclado, & lápiz"** como **Conectado.** En este momento, puede obtener una actualización de firmware; consulte [la sección siguiente.](motion-controllers.md#updating-controller-firmware)
9. Vuelva a conectar la cubierta de la batería.
10. Repita los pasos del 1 al 9 para el segundo controlador.

<br>

:::row:::
    :::column:::
        Después de emparejar correctamente ambos controladores, la configuración debe ser como la siguiente, en la categoría **"Mouse, teclado, & lápiz".** <br>
        <br>
        *Imagen: Controladores de movimiento conectados*
    :::column-end:::
        :::column:::
       ![Controladores de movimiento conectados](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

Si los controladores se apagan después del emparejamiento, su estado se mostrará como Emparejado. En el caso de los controladores de forma permanente en la categoría "Otros dispositivos", es posible que el emparejamiento solo se haya completado parcialmente. En este caso, vuelva a ejecutar los pasos de emparejamiento para que el controlador funcione.

### <a name="updating-controller-firmware"></a>Actualización del firmware del controlador

* Si hay disponible un casco envolvente conectado al equipo con el nuevo firmware del controlador, el firmware se insertará automáticamente en los controladores de movimiento la próxima vez que los active. Las actualizaciones de firmware del controlador se indican mediante un patrón de iluminación de cuadrantes LED en un movimiento circular y pueden tardar entre 1 y 2 minutos.


:::row:::
    :::column:::
* Una vez completada la actualización del firmware, los controladores se reiniciarán y se volverán a conectar. Ambos controladores deben estar conectados ahora. <br>
        <br>
        *Imagen: Controladores conectados en Bluetooth configuración*
    :::column-end:::
        :::column:::
       ![Controladores conectados](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* Compruebe que los controladores funcionan correctamente:
    1. Inicie **Portal de realidad mixta** y escriba su Mixed Reality Inicio.
    2. Mueva los controladores y compruebe que el seguimiento, los botones de prueba y comprueben que [la teleportación](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) funciona. Si no lo hacen, consulte la solución de problemas [del controlador de movimiento.](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)

## <a name="gazing-and-pointing"></a>Gazing and pointing

Windows Mixed Reality admite dos modelos clave para la interacción; **mirar y confirmar y** **apuntar y confirmar**:
* Con la mirada y **la confirmación,** los usuarios tienen como destino un objeto con su mirada y, a continuación, seleccionan objetos con pulsaciones de aire a mano, un mando de juegos, un clicker o su voz. [](gaze-and-commit.md)
* Con **el punto y la confirmación,** un usuario puede apuntar a un controlador de movimiento con capacidad de apuntar al objeto de destino y, a continuación, seleccionar objetos con el desencadenador del controlador.

Las aplicaciones que admiten apuntar con controladores de movimiento también deben habilitar interacciones controladas por mirada siempre que sea posible, para ofrecer a los usuarios la opción de qué dispositivos de entrada usan.

### <a name="managing-recoil-when-pointing"></a>Administración del retroceso al apuntar

Al usar controladores de movimiento para apuntar y confirmar, los usuarios usarán el controlador para dirigirse e interactuar mediante la extracción de su desencadenador. Los usuarios que extraigan el desencadenador de forma productiva pueden acabar apuntando al controlador más arriba al final de su extracción del desencadenador de lo previsto.

Para administrar cualquier retroceso que pueda producirse cuando los usuarios extraigan el desencadenador, la aplicación puede ajustar su rayo de destino cuando el valor del eje análogo del desencadenador suba por encima de 0,0. A continuación, puede tomar medidas con ese rayo de destino unos fotogramas más adelante una vez que el valor del desencadenador alcance 1,0, siempre que la última pulsación se produzca en un breve período de tiempo. Al usar el gesto de pulsar compuesto de nivel [superior,](gaze-and-commit.md#composite-gestures)Windows administrará esta captura de rayos de destino y el tiempo de espera.

## <a name="grip-pose-vs-pointing-pose"></a>Posición de control frente a posición de apuntar

Windows Mixed Reality admite controladores de movimiento en diferentes factores de forma, y el diseño de cada controlador difiere en su relación entre la posición de la mano del usuario y la dirección "hacia delante" natural que las aplicaciones deben usar para señalar al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de poses que puede investigar para cada origen de interacción. la **posición del control** y la posición del **puntero.**

### <a name="grip-pose"></a>Posición de control

La **posición del control** representa la ubicación de la mano detectada por un HoloLens o la mano que mantiene un controlador de movimiento.

En los cascos envolventes, la  posición del control se usa mejor para representar la mano del usuario o un objeto que se mantiene en la mano del **usuario,** como un revólver o un revólver. La posición de control también se usa al  visualizar un controlador de movimiento, ya que el modelo procesable proporcionado por Windows para un controlador de movimiento usa la posición del control como su origen y centro de rotación.

La posición de control se define específicamente de la siguiente manera:
* Posición **del control:** centroide de mano al mantener el controlador de forma natural, ajustado a la izquierda o derecha para centrar la posición dentro del control. En el Windows Mixed Reality de movimiento, esta posición se alinea generalmente con el botón Desajegar.
* Eje **derecho** de la orientación del control: cuando se abre completamente la mano para formar una posición plana de cinco dedos, el rayo que es normal para la mano (hacia delante desde la mano izquierda, hacia atrás desde la mano derecha).
* Eje **hacia** delante de la orientación del control: cuando cierra la mano parcialmente (como si sostendía el controlador), el rayo que señala "hacia delante" a través del metro formado por los dedos no thumb.
* Eje **Up de la orientación del control:** eje Up implícito en las definiciones Right y Forward.

### <a name="pointer-pose"></a>Posición de puntero

La **posición del puntero** representa la punta del controlador que apunta hacia delante.

La posición de puntero proporcionada por el sistema se usa mejor para la difusión por rayos cuando se representa **el propio modelo de controlador.** Si va a representar algún otro objeto virtual en lugar del controlador, como un revólver virtual, debe apuntar con un rayo que sea más natural para ese objeto virtual, como un rayo que viaja a lo largo del vuelo del modelo de revólver definido por la aplicación. Dado que los usuarios pueden ver el objeto virtual y no el controlador físico, es probable que apuntar con el objeto virtual sea más natural para aquellos que usan la aplicación.

## <a name="controller-tracking-state"></a>Estado de seguimiento del controlador

Al igual que los cascos, el Windows Mixed Reality de movimiento no requiere ninguna configuración de sensores de seguimiento externos. En su lugar, los sensores del casco son los que realiza el seguimiento de los controladores.

Si el usuario mueve los controladores fuera del campo de visión del casco, en la mayoría de los casos Windows seguirá inferiendo las posiciones del controlador y las proporcionará a la aplicación. Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se colocarán en posiciones de precisión aproximada.

En este punto, el sistema bloqueará el controlador con el cuerpo del usuario, haciendo un seguimiento de la posición del usuario a medida que se mueve, a la vez que expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan controladores para apuntar y activar elementos de la interfaz de usuario pueden funcionar con normalidad con una precisión aproximada sin que el usuario lo haga.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>Razonamiento sobre el seguimiento del estado explícitamente

Las aplicaciones que desean tratar las posiciones de forma diferente en función del estado de seguimiento pueden ir más allá e inspeccionar las propiedades en el estado del controlador, como SourceLossRisk y PositionAccuracy:

<table>
<tr>
<th> Estado de seguimiento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisión</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Alta precisión (en riesgo de pérdida)</b> </td><td style="background-color: orange"> == 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Precisión aproximada</b> </td><td style="background-color: orange"> == 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Sin posición</b> </td><td style="background-color: orange"> == 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> false</td>
</tr>
</table>

Estos estados de seguimiento del controlador de movimiento se definen de la siguiente manera:
* **Alta precisión:** Aunque el controlador de movimiento está dentro del campo de visión del casco, generalmente proporcionará posiciones de alta precisión, en función del seguimiento visual. Un controlador en movimiento que abandona momentáneamente el campo de vista o se oculta momentáneamente de los sensores de casco (por ejemplo, por la otra mano del usuario) seguirá devolviendo poses de alta precisión durante un breve período de tiempo, en función del seguimiento inerte del propio controlador.
* **Alta precisión (en riesgo de perder):** Cuando el usuario mueve el controlador de movimiento más allá del borde del campo de vista del casco, el casco pronto no podrá realizar un seguimiento visual de la posición del controlador. La aplicación sabe cuándo el controlador ha alcanzado este límite de FOV al ver que **SourceLossRisk** alcanza la versión 1.0. En ese momento, la aplicación puede optar por pausar los gestos del controlador que requieren un flujo estable de poses de alta calidad.
* **Precisión aproximada:** Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se colocarán en posiciones de precisión aproximada. En este punto, el sistema bloqueará el controlador con el cuerpo del usuario, haciendo un seguimiento de la posición del usuario a medida que se mueve, a la vez que expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan controladores para apuntar y activar elementos de la interfaz de usuario pueden funcionar con normalidad con una precisión aproximada sin que el usuario se de cuenta. Las aplicaciones con requisitos de entrada  más elevados pueden optar por entender esta caída de Alta precisión a Precisión aproximada inspeccionando la propiedad **PositionAccuracy,** por ejemplo, para proporcionar al usuario un cuadro de acceso más práctico en los destinos fuera de la pantalla durante este tiempo. 
* **Sin posición:** Aunque el controlador puede funcionar con precisión aproximada durante mucho tiempo, a veces el sistema sabe que incluso una posición bloqueada por el cuerpo no es significativa en este momento. Por ejemplo, es posible que un controlador que se ha activado nunca se haya observado visualmente, o bien que un usuario pueda colocar un controlador que otra persona haya seleccionado a continuación. En ese momento, el sistema no proporcionará ninguna posición a la aplicación y **TryGetPosition** devolverá false.

## <a name="interactions-low-level-spatial-input"></a>Interacciones: entrada espacial de bajo nivel

Las interacciones principales entre las manos y los controladores de movimiento son **Select**, **Menu**, **Hands**, **Touchpad,** **Thumbstick** y **Home.**
* **Select** es la interacción principal para activar un holograma, que consta de una pulsación seguida de una versión. En el caso de los controladores de movimiento, se realiza una pulsación Seleccionar mediante el desencadenador del controlador. Otras maneras de realizar una selección son mediante el uso del comando [de voz](voice-input.md) "Seleccionar". La misma interacción de selección se puede usar dentro de cualquier aplicación. Piense en Seleccionar como el equivalente de un clic del mouse; una acción universal que se aprende una vez y, a continuación, se aplica en todas las aplicaciones.
* **Menu** es la interacción secundaria para actuar en un objeto, que se usa para extraer un menú contextual o realizar alguna otra acción secundaria. Con los controladores de movimiento, puede realizar una acción de menú mediante el botón de *menú del* controlador. (es decir, el botón con el icono de "menú" de hamburguesa)
* **Comprender** es cómo los usuarios pueden tomar medidas directamente en los objetos que tienen a su mano para manipularlos. Con los controladores de movimiento, puede realizar una acción de comprensión apreando fuertemente la malla. Un controlador de movimiento puede detectar una comprensión con un botón de agarrar, un desencadenador de mano u otro sensor.
* **Touchpad permite** al usuario ajustar una acción en dos dimensiones a lo largo de la superficie del panel táctil de un controlador de movimiento, confirmando la acción haciendo clic hacia abajo en el panel táctil. Los touchpad proporcionan un estado presionado, un estado tocado y coordenadas XY normalizadas. X e Y van de -1 a 1 en el intervalo del panel táctil circular, con un centro en (0, 0). Para X, -1 está a la izquierda y 1 a la derecha. Para Y, -1 está en la parte inferior y 1 en la parte superior.
* **Thumbstick** permite al usuario ajustar una acción en dos dimensiones moviendo el control de posición de un controlador de movimiento dentro de su intervalo circular, confirmando la acción haciendo clic hacia abajo en el control de posición. Las huellas digitales también proporcionan un estado presionado y coordenadas XY normalizadas. X e Y van de -1 a 1 en el intervalo del panel táctil circular, con un centro en (0, 0). Para X, -1 está a la izquierda y 1 a la derecha. Para Y, -1 está en la parte inferior y 1 en la parte superior.
* **Inicio** es una acción especial del sistema que se usa para volver al menú Inicio. Es similar a presionar la tecla Windows en un teclado o el botón Xbox en un controlador de Xbox. Puede ir a Inicio presionando el botón Windows en un controlador de movimiento. Tenga en cuenta que siempre puede volver a Empezar si dice "Hey Cortana, Go Home". Las aplicaciones no pueden reaccionar específicamente a las acciones de Inicio, ya que las controla el sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Gestos compuestos: entrada espacial de alto nivel

Tanto [los gestos con las](gaze-and-commit.md#composite-gestures) manos como los controladores de movimiento se pueden realizar con el tiempo para detectar un conjunto común de **[gestos compuestos de alto nivel.](gaze-and-commit.md#composite-gestures)** Esto permite que la aplicación detecte  gestos  de pulsación,  **retención,** manipulación y navegación de alto nivel, tanto si los usuarios terminan usando las manos como los controladores.

## <a name="rendering-the-motion-controller-model"></a>Representación del modelo de controlador de movimiento

**Los modelos de controlador 3D** Windows pone a disposición de las aplicaciones un modelo que se puede representar de cada controlador de movimiento actualmente activo en el sistema. Al hacer que la aplicación cargue y articule dinámicamente estos modelos de controlador proporcionados por el sistema en tiempo de ejecución, puede asegurarse de que la aplicación sea compatible con el futuro para cualquier diseño de controlador futuro.

Se recomienda representar todos los modelos que se pueden representar en la **posición** de control del controlador, ya que el origen del modelo está alineado con este punto del mundo físico. Si va a representar modelos de controlador, es posible que desee pasar a la escena desde la posición del puntero **,** que representa el rayo a lo largo del cual los usuarios esperarán apuntar de forma natural, dado el diseño físico del controlador.

Para obtener más información sobre cómo cargar modelos de controlador dinámicamente en Unity, consulte la sección Representación del [modelo de controlador de movimiento en Unity.](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity)

**Arte de línea del controlador 2D** Aunque se recomienda adjuntar sugerencias y comandos del controlador en la aplicación a los propios modelos de controlador en la aplicación, es posible que algunos desarrolladores quieran usar representaciones de arte de línea 2D de los controladores de movimiento en la interfaz de usuario plana de "tutorial" o "cómo hacerlo". Para esos desarrolladores, hemos hecho que los archivos .png de línea del controlador de movimiento estén disponibles en blanco y negro a continuación (haga clic con el botón derecho para guardar).

![Vista previa de la técnica de línea de controladores de movimiento](images/motioncontrollers-black-preview-300px.png)

[Arte de línea de controladores de movimiento de resolución completa en "''white'''](images/motioncontrollers-white.png)
 
[Diseño de línea de controladores de movimiento de resolución completa en "''black''"](images/motioncontrollers-black.png)

## <a name="faq"></a>Preguntas más frecuentes

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>¿Puedo emparejar controladores de movimiento con varios equipos?

Los controladores de movimiento admiten el emparejamiento con un solo equipo. Siga las instrucciones sobre [la configuración del controlador de movimiento](motion-controllers.md#setup) para emparejar los controladores.

### <a name="how-do-i-update-motion-controller-firmware"></a>Cómo actualizar el firmware del controlador de movimiento?

El firmware del controlador de movimiento forma parte del controlador del casco y se actualizará automáticamente en la conexión, si es necesario. Las actualizaciones de firmware suelen tardar entre 1 y 2 minutos, dependiendo Bluetooth de radio y de vínculo. En raras ocasiones, las actualizaciones de firmware del controlador pueden tardar hasta 10 minutos, lo que puede indicar una conectividad Bluetooth o interferencias de radio. Consulte [Bluetooth recomendados en la Guía para aficionados para](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) solucionar problemas de conectividad. Después de una actualización de firmware, los controladores se reiniciarán y volverán a conectarse al equipo host (es posible que observe que los LED son brillantes para el seguimiento). Si se interrumpe una actualización de firmware (por ejemplo, los controladores pierden energía), se volverá a intentar la próxima vez que se enciendan los controladores.

### <a name="how-i-can-check-battery-level"></a>¿Cómo puedo comprobar el nivel de batería?

En la [Windows Mixed Reality inicio,](../discover/navigating-the-windows-mixed-reality-home.md)puede girar el controlador para ver su nivel de batería en el lado inverso del modelo virtual. No hay ningún indicador físico de nivel de batería.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>¿Puede usar estos controladores sin casco? ¿Solo para la entrada de desencadenador/etc?.

No para aplicaciones de Windows universales.

## <a name="troubleshooting"></a>Solución de problemas

Consulte [solución de problemas del controlador de movimiento](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) en la Guía para aficionados.

## <a name="filing-motion-controller-feedbackbugs"></a>Presentación de comentarios o errores del controlador de movimiento

[Enviarnos comentarios](/hololens/hololens-feedback) en Centro de opiniones, mediante la categoría "Mixed Reality -> Entrada".

## <a name="see-also"></a>Consulte también

* [Controladores de movimiento en Unity](../develop/unity/motion-controllers-in-unity.md)
* [Manos y controladores de movimiento en DirectX](../develop/native/hands-and-motion-controllers-in-directx.md)
* [Gestos](gaze-and-commit.md#composite-gestures)
* [Guía del entusiasta: Su Windows Mixed Reality hogar](/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guía del entusiasta: Uso de juegos & aplicaciones en Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Funcionamiento del seguimiento de la interacción directa](/windows/mixed-reality/enthusiast-guide/tracking-system)