---
title: Controladores de movimiento en Unity
description: Obtenga información sobre cómo realizar acciones en la mirada en Unity con la entrada del controlador de movimiento mediante XR y las API comunes de botón y eje.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: controladores de movimiento, unity, entrada, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d8f9ce292c0ab1cfa89faf58f0e5b90322192b35
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394519"
---
# <a name="motion-controllers-in-unity"></a>Controladores de movimiento en Unity

Hay dos maneras clave de tomar medidas en [](../../design/motion-controllers.md) la mirada en [Unity,](gaze-in-unity.md) [gestos](../../design/gaze-and-commit.md#composite-gestures) de mano y controladores de movimiento en HoloLens y HMD inmersivo. Puede acceder a los datos de ambos orígenes de entrada espacial a través de las mismas API en Unity.

Unity proporciona dos formas principales de acceder a los datos de entrada espacial para Windows Mixed Reality. Las API *Input.GetButton/Input.GetAxis* comunes funcionan en varios SDK XR de Unity, mientras que la API *InteractionManager/GestureRecognizer* específica de Windows Mixed Reality expone el conjunto completo de datos de entrada espacial.

## <a name="unity-xr-input-apis"></a>API de entrada XR de Unity

Para los proyectos nuevos, se recomienda usar las nuevas API de entrada XR desde el principio. 

Puede encontrar más información sobre las [API de XR aquí.](https://docs.unity3d.com/Manual/xr_input.html)

## <a name="unity-buttonaxis-mapping-table"></a>Tabla de asignación de botones y ejes de Unity

El Administrador de entrada de Unity para Windows Mixed Reality de movimiento admite los valores de botón y de eje que se enumeran a continuación a través de las API *Input.GetButton/GetAxis.* La columna "Específico de Mr. de Windows" hace referencia a las propiedades disponibles fuera del *tipo InteractionSourceState.* Cada una de estas API se describe en detalle en las secciones siguientes.

Las asignaciones de identificadores de botón o eje Windows Mixed Reality suelen coincidir con los identificadores de botón o eje de Oculus.

Las asignaciones de identificadores de botón o eje Windows Mixed Reality de las asignaciones de OpenVR de dos maneras:
1. La asignación usa los IDs del panel táctil que son distintos de la huella digital, para admitir controladores con los controladores tanto con los controladores como con los controladores táctiles.
2. La asignación evita sobrecargar los ID de los botones A y X de los botones Menú para dejarlos disponibles para los botones FÍSICOS ABXY.

<table>
<tr>
<th rowspan="2">Entrada </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API comunes de Unity</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">API de entrada específica de MR de Windows</a><br />(XR. Wsa. Entrada)</th>
</tr><tr>
<th> Mano izquierda </th><th> Mano derecha</th>
</tr><tr>
<td> Selección del desencadenador presionado </td><td> Eje 9 = 1,0 </td><td> Eje 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Selección del valor análogo del desencadenador </td><td> Eje 9 </td><td> Eje 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Seleccionar desencadenador presionado parcialmente </td><td> Botón 14 <i>(compatibilidad con el gamepad)</i> </td><td> Botón 15 <i>(compatibilidad con el gamepad)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> Botón menú presionado </td><td> Botón 6* </td><td> Botón 7* </td><td> menuPressed</td>
</tr><tr>
<td> Botón De control presionado </td><td> Eje 11 = 1,0 (sin valores análogos)<br />Botón 4 <i>(compatibilidad con el gamepad)</i> </td><td> Eje 12 = 1,0 (sin valores análogos)<br />Botón 5 <i>(compatibilidad con el gamepad)</i> </td><td> Agarró</td>
</tr><tr>
<td> Thumbstick X <i>(left: -1.0, right: 1.0)</i> </td><td> Eje 1 </td><td> Eje 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </td><td> Eje 2 </td><td> Eje 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Thumbstick pressed </td><td> Botón 8 </td><td> Botón 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(izquierda: -1.0, derecha: 1.0)</i> </td><td> Eje 17* </td><td> Eje 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Touchpad Y <i>(superior: -1.0, inferior: 1.0)</i> </td><td> Eje 18* </td><td> Eje 20* </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Touchpad tocado </td><td> Botón 18* </td><td> Botón 19* </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad presionado </td><td> Botón 16* </td><td> Botón 17* </td><td> touchpadPressed</td>
</tr><tr>
<td> 6 Posición de control o posición de puntero de DoF </td><td colspan="2"> <i>Solo</i> posición de control: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></td><td> Pasar <i>control</i> o <i>puntero</i> como argumento: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Estado de seguimiento </td><td colspan="2"> <i>La precisión de la posición y el riesgo de pérdida de origen solo están disponibles a través de la API específica de MR.</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Estos IDs de botón o eje difieren de los que usa Unity para OpenVR debido a colisiones en las asignaciones que usan los gamepads, Oculus Touch y OpenVR.

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->

### <a name="openxr"></a>OpenXR

Para conocer los conceptos básicos sobre las interacciones de realidad mixta en Unity, visite el Manual de [Unity para la entrada XR de Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) En esta documentación de Unity se tratan las asignaciones de entradas específicas del controlador a entradas **más generalizablesFeatureUsage,** cómo se pueden identificar y clasificar las entradas XR disponibles, cómo leer datos de estas entradas y mucho más.

El Mixed Reality complemento OpenXR proporciona perfiles de interacción de entrada adicionales, asignados a **inputFeatureUsage** estándar, como se detalla a continuación:

| InputFeatureUsage | Controlador HP Reverb G2 (OpenXR) | HoloLens Hand (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Interruptor: haga clic en | |
| desencadenador | Desencadenador  | |
| Agarre | Agarre | Pulsación o presión en el aire |
| primaryButton | [X/A] - Press | Pulsar en el aire |
| secondaryButton | [Y/B] - Press | |
| gripButton | Control: presione | |
| triggerButton | Desencadenador: presionar | |
| menuButton | Menú | |

## <a name="grip-pose-vs-pointing-pose"></a>Posición de control frente a posición de apuntar

Windows Mixed Reality admite controladores de movimiento en una variedad de factores de forma. El diseño de cada controlador difiere en su relación entre la posición de la mano del usuario y la dirección "hacia delante" natural que las aplicaciones deben usar para señalar al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de poses que puede investigar para cada origen de interacción: la posición del **control** y la **posición del puntero**. Las coordenadas de posición de control y posición de puntero se expresan mediante todas las API de Unity en coordenadas globales del mundo de Unity.

### <a name="grip-pose"></a>Posición de control

La **posición de control** representa la ubicación de la mano de los usuarios, ya sea detectada por un HoloLens o que mantiene un controlador de movimiento.

En los cascos envolventes, la  posición de control se usa mejor para representar la mano del usuario o un objeto que se **mantiene en la mano del usuario.** La posición de control también se usa al visualizar un controlador de movimiento. El **modelo procesable proporcionado** por Windows para un controlador de movimiento usa la posición de control como su origen y centro de rotación.

La posición de control se define específicamente de la siguiente manera:
* Posición **del control:** centroide de la mano al mantener el controlador de forma natural, ajustado a la izquierda o a la derecha para centrar la posición dentro del control. En el Windows Mixed Reality de movimiento, esta posición se alinea generalmente con el botón Desajegar.
* Eje **derecho** de la orientación del control: cuando se abre completamente la mano para formar una posición plana de 5 dedos, el rayo que es normal para la mano (hacia delante desde la mano izquierda, hacia atrás desde la mano derecha).
* Eje **hacia** delante de la orientación del control: al cerrar la mano parcialmente (como si sostendes el controlador), el rayo que apunta "hacia delante" a través del rayo formado por los dedos que no son de los dedos.
* Eje **Up de la orientación del control:** eje Up implícito en las definiciones Right y Forward.

Puede acceder a la posición de control a través de la API de entrada entre proveedores *[(XR) de Unity. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o a través de la API específica de Mr. de Windows *(sourceState.sourcePose.TryGetPosition/Rotation,* que solicita datos de posición para el **nodo Control).**

### <a name="pointer-pose"></a>Posición de puntero

La **posición del puntero** representa la punta del controlador que apunta hacia delante.

La posición de puntero proporcionada por el sistema se usa mejor para la difusión por rayos cuando se representa **el propio modelo de controlador.** Si va a representar algún otro objeto virtual en lugar del controlador, como un revólver virtual, debe apuntar con un rayo que sea más natural para ese objeto virtual, como un rayo que viaja a lo largo del vuelo del modelo de revólver definido por la aplicación. Dado que los usuarios pueden ver el objeto virtual y no el controlador físico, es probable que apuntar con el objeto virtual sea más natural para aquellos que usan la aplicación.

Actualmente, la posición del puntero solo está disponible en Unity a través de la API específica de Mr. de Windows, *sourceState.sourcePose.TryGetPosition/Rotation,* pasando *InteractionSourceNode.Pointer* como argumento.

### <a name="openxr"></a>OpenXR 

Tiene acceso a dos conjuntos de poses a través de interacciones de entrada de OpenXR:

* El control posa para representar objetos en la mano
* El objetivo es apuntar al mundo.

Puede encontrar más información sobre este diseño y las diferencias entre las dos posturas en [Especificación de OpenXR: subpaths de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Las poses proporcionadas por InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** y **DeviceAngularVelocity** representan la posición de control de OpenXR.  InputFeatureUsages relacionados con las poses de control se definen en [CommonUsages de](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.

Las poses proporcionadas por InputFeatureUsages **PointerPosition**, **PointerRotation,** **PointerVelocity** y **PointerAngularVelocity** representan la posición de objetivo de OpenXR.  Estos inputFeatureUsages no se definen en los archivos de C# incluidos, por lo que deberá definir sus propios inputFeatureUsages como se muestra a continuación:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a>Haptics

Para obtener información sobre el uso de hápticos en el sistema de entrada XR de Unity, puede encontrar documentación en el Manual de Unity para la entrada XR de [Unity: haptics.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)

## <a name="controller-tracking-state"></a>Estado de seguimiento del controlador

Al igual que los cascos, el Windows Mixed Reality de movimiento no requiere ninguna configuración de sensores de seguimiento externos. En su lugar, los sensores del casco son los que realiza el seguimiento de los controladores.

Si el usuario mueve los controladores fuera del campo de visión del casco, Windows sigue inferiendo posiciones del controlador en la mayoría de los casos. Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se colocarán en posiciones de precisión aproximada.

En este punto, el sistema bloqueará el controlador con el cuerpo del usuario, haciendo un seguimiento de la posición del usuario a medida que se mueve, a la vez que expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan controladores para apuntar y activar elementos de la interfaz de usuario pueden funcionar con normalidad con una precisión aproximada sin que el usuario lo haga.

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>Razonamiento sobre el seguimiento del estado explícitamente

Las aplicaciones que desean tratar las posiciones de forma diferente en función del estado de seguimiento pueden ir más allá e inspeccionar las propiedades en el estado del controlador, como *SourceLossRisk* y *PositionAccuracy*:

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
* **Alta precisión:** Aunque el controlador de movimiento está dentro del campo de visión del casco, generalmente proporcionará posiciones de alta precisión, en función del seguimiento visual. Un controlador en movimiento que abandona momentáneamente el campo de visión o se oculta momentáneamente de los sensores de casco (por ejemplo, por la otra mano del usuario) seguirá devolviendo poses de alta precisión durante un breve período de tiempo, en función del seguimiento inerte del propio controlador.
* **Alta precisión (en riesgo de perder):** Cuando el usuario mueve el controlador de movimiento más allá del borde del campo de vista del casco, el casco pronto no podrá realizar un seguimiento visual de la posición del controlador. La aplicación sabe cuándo el controlador ha alcanzado este límite de FOV al ver que **SourceLossRisk** alcanza la versión 1.0. En ese momento, la aplicación puede optar por pausar los gestos del controlador que requieren un flujo estable de poses de alta calidad.
* **Precisión aproximada:** Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se colocarán en posiciones de precisión aproximada. En este punto, el sistema bloqueará el controlador con el cuerpo del usuario, haciendo un seguimiento de la posición del usuario a medida que se mueve, a la vez que expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan controladores para apuntar y activar elementos de la interfaz de usuario pueden funcionar con normalidad con una precisión aproximada sin que el usuario se de cuenta. Las aplicaciones con requisitos de entrada  más elevados pueden optar por entender esta caída de Alta precisión a Precisión aproximada inspeccionando la propiedad **PositionAccuracy,** por ejemplo, para proporcionar al usuario un cuadro de acceso más práctico en los destinos fuera de la pantalla durante este tiempo. 
* **Sin posición:** Aunque el controlador puede funcionar con precisión aproximada durante mucho tiempo, a veces el sistema sabe que incluso una posición bloqueada por el cuerpo no es significativa en este momento. Por ejemplo, es posible que un controlador que se ha activado nunca se haya observado visualmente, o bien que un usuario pueda colocar un controlador que otra persona haya seleccionado a continuación. En ese momento, el sistema no proporcionará ninguna posición a la aplicación y *TryGetPosition* devolverá false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>API comunes de Unity (Input.GetButton/GetAxis)

**Espacio de nombres:** *UnityEngine*, *UnityEngine.XR*<br>
**Tipos:** *entrada,* *XR. InputTracking*

Actualmente, Unity usa sus API *input.GetButton/Input.GetAxis* generales para exponer la entrada del SDK de [Oculus,](https://docs.unity3d.com/Manual/OculusControllers.html)el SDK de [OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html) y Windows Mixed Reality, incluidos los controladores de manos y movimiento. Si la aplicación usa estas API para la entrada, puede admitir fácilmente controladores de movimiento en varios SDK de XR, incluidos Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Obtención del estado presionado de un botón lógico

Para usar las API de entrada generales de Unity, normalmente empezarás por conectar botones y ejes a nombres lógicos en el Administrador de entrada de [Unity,](https://docs.unity3d.com/Manual/ConventionalGameInput.html)enlazando un botón o los iDs de eje a cada nombre. A continuación, puede escribir código que haga referencia a ese nombre de eje o botón lógico.

Por ejemplo, para asignar el botón de desencadenador del controlador de movimiento izquierdo a la acción Enviar, vaya a Edit **> Project Settings > Input** within Unity (Editar configuración del proyecto > Entrada dentro de Unity) y expanda las propiedades de la sección Submit (Enviar) en Axes (Ejes). Cambie la **propiedad Botón positivo** o Botón Alt **positivo** para leer el **botón 14**, de la siguiente manera:

![InputManager de Unity](images/unity-input-manager.png)<br>
*Unity InputManager*

A continuación, el script puede comprobar la acción Submit *mediante Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Puede agregar más botones lógicos cambiando la **propiedad Tamaño** en **Ejes**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Obtener el estado presionado de un botón físico directamente

También puede acceder a los botones manualmente por su nombre completo, mediante *Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Obtención de la posición de una mano o un controlador de movimiento

Puede acceder a la posición y rotación del controlador mediante *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> El código anterior representa la posición de control del controlador (donde el usuario contiene el controlador), lo que resulta útil para representar un revólver o un revólver en la mano del usuario o un modelo del propio controlador.
> 
> La relación entre esta posición de control y la posición del puntero (donde apunta la punta del controlador) puede diferir entre los controladores. En este momento, el acceso a la posición de puntero del controlador solo es posible a través de la API de entrada específica de MR, que se describe en las secciones siguientes.

## <a name="windows-specific-apis-xrwsainput"></a>API específicas de Windows (XR. Wsa. Entrada)

> [!CAUTION]
> Si el proyecto usa cualquiera de las XR. Las API de WSA se están eliminando gradualmente en favor del SDK de XR en futuras versiones de Unity. Para los proyectos nuevos, se recomienda usar el SDK de XR desde el principio. Puede encontrar más información sobre el sistema [de entrada XR y las API aquí.](https://docs.unity3d.com/Manual/xr_input.html)

**Espacio de nombres:** *UnityEngine.XR.WSA.Input*<br>
**Tipos:** *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Para obtener información más detallada sobre la entrada Windows Mixed Reality mano (para HoloLens) y los controladores de movimiento, puede elegir usar las API de entrada espacial específicas de Windows en el espacio de nombres *UnityEngine.XR.WSA.Input.* Esto le permite acceder a información adicional, como la precisión de la posición o el tipo de origen, lo que le permite diferenciar las manos y los controladores.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Sondeo para el estado de las manos y los controladores de movimiento

Puede sondear el estado de este fotograma para cada origen de interacción (controlador de mano o movimiento) mediante el *método GetCurrentReading.*

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Cada *InteractionSourceState que* se obtiene representa un origen de interacción en el momento actual en el tiempo. *InteractionSourceState expone* información como:
* Qué [tipos de presiones](../../design/motion-controllers.md) se producen (Select/Menu/Thumbstick/Touchpad/Thumbstick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Otros datos específicos de los controladores de movimiento, como las coordenadas XY del panel táctil o el control de posición y el estado tocado

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* InteractionSourceKind para saber si el origen es una mano o un controlador de movimiento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Sondeo de las representaciones predichos hacia delante

* Al sondear los datos de origen de interacción de manos y controladores, las poses que obtiene son poses predichos hacia delante por el momento en que los fotones de este fotograma llegarán a los ojos del usuario.  Las poses predichos hacia delante se usan mejor para **representar** el controlador o un objeto mantenido en cada fotograma.  Si tiene como destino una determinada presión o una versión con el controlador, será más preciso si usa las API de eventos históricos que se describen a continuación.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* También puede obtener la posición de la cabeza predicho hacia delante para este fotograma actual.  Al igual que con la  posición de origen, esto es útil para representar un cursor, aunque el destino de una determinada presión o versión será más preciso si usa las API de eventos históricos que se describen a continuación.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Control de eventos de origen de interacción

Para controlar los eventos de entrada a medida que se suceden con sus datos de posición históricos precisos, puede controlar los eventos de origen de interacción en lugar de sondear.

Para controlar los eventos de origen de interacción:
* Regístrese para un *evento de entrada de InteractionManager.* Para cada tipo de evento de interacción que le interese, debe suscribirse a él.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Controle el evento. Una vez que se haya suscrito a un evento de interacción, recibirá la devolución de llamada cuando corresponda. En el *ejemplo SourcePressed,* será después de que se detecte el origen y antes de que se libera o se pierde.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Cómo detener el control de un evento

Debe dejar de controlar un evento cuando ya no esté interesado en el evento o esté destruyendo el objeto que se ha suscrito al evento. Para dejar de controlar el evento, cancele la suscripción al evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Lista de eventos de origen de interacción

Los eventos de origen de interacción disponibles son:
* *InteractionSourceDetected* (el origen se activa)
* *InteractionSourceLost* (queda inactivo)
* *InteractionSourcePressed* (pulsar, presionar el botón o "Seleccionar" se ha dicho)
* *InteractionSourceReleased* (final de una pulsación, un botón publicado o el final de la expresión "Select")
* *InteractionSourceUpdated* (mueve o cambia algún estado)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Los eventos de destino históricos suponen que coinciden con mayor precisión con una publicación o una pulsación

Las API de sondeo descritas anteriormente dan a la aplicación poses predichos para el futuro.  Aunque las poses predichos son mejores para representar el controlador o un objeto de mano virtual, las poses futuras no son óptimas para el destino, por dos razones clave:
* Cuando el usuario presiona un botón en un controlador, puede haber unos 20 ms de latencia inalámbrica a través de Bluetooth antes de que el sistema reciba la presión.
* A continuación, si usa una posición predicho hacia delante, se aplicarían otros 10-20 ms de predicción hacia delante para dirigirse al momento en que los fotones del fotograma actual lleguen a los ojos del usuario.

Esto significa que el sondeo proporciona una posición de origen o de cabeza que está entre 30 y 40 ms hacia delante desde donde la cabeza y las manos del usuario estaban realmente de vuelta cuando se produjo la presión o la liberación.  En el caso de la entrada de mano de HoloLens, aunque no hay ningún retraso de transmisión inalámbrica, hay un retraso de procesamiento similar para detectar la presión.

Para dirigirse con precisión en función de la intención original del usuario para una pulsación de mano o controlador, debe usar la posición histórica de origen o la posición de la cabeza de ese evento de entrada *InteractionSourcePressed* o *InteractionSourceReleased.*

Puede seleccionar como destino una presión o una versión con datos de posición históricos de la cabeza del usuario o su controlador:
* La posición de la cabeza en el momento en el que  se produjo un gesto o una presión del controlador, que se puede usar para dirigirse a para determinar a qué estaba mirando el [usuario:](../../design/gaze-and-commit.md)

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* La posición de origen en el momento en que se  produjo una presión del controlador de movimiento, que se puede usar para establecer como destino para determinar a qué apuntaba el controlador el usuario.  Este será el estado del controlador que experimentó la presión.  Si va a representar el propio controlador, puede solicitar la posición del puntero en lugar de la posición de control para que el rayo de destino se base en lo que el usuario considerará la sugerencia natural de ese controlador representado:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Ejemplo de controladores de eventos

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a>Controladores de movimiento en MRTK

Puede acceder al [gesto y al controlador de movimiento](/windows/mixed-reality/mrtk-unity/features/input/controllers) desde el Administrador de entrada.

## <a name="follow-along-with-tutorials"></a>Seguimiento de tutoriales

Los tutoriales paso a paso, con ejemplos de personalización más detallados, están disponibles en Mixed Reality Academy:

- [MR Input 211: gesto](tutorials/holograms-211.md)
- [MR Input 213: controladores de movimiento](../../deprecated/mixed-reality-213.md)

[![Entrada de MR 213: controlador de movimiento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Entrada de MR 213: controlador de movimiento*

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, está en medio de la exploración de los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Seguimiento de manos y ocular](./hand-eye-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también

* [Mirada-cabeza y confirmación](../../design/gaze-and-commit.md)
* [Controladores de movimiento](../../design/motion-controllers.md)