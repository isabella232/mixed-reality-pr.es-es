---
title: Controladores de movimiento en Unity
description: Obtenga información sobre cómo realizar una acción en Unity en Unity con la entrada del controlador de movimiento mediante XR y las API del eje y del botón común.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Controladores de movimiento, Unity, entrada, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: bf9aad0ee67a406280cefedec8b55fb1de130b8b
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192975"
---
# <a name="motion-controllers-in-unity"></a>Controladores de movimiento en Unity

Hay dos formas clave de tomar medidas en su [mirada en Unity](gaze-in-unity.md), [gestos de mano](../../design/gaze-and-commit.md#composite-gestures) y [controladores de movimiento](../../design/motion-controllers.md) en HoloLens y HMDs envolventes. Puede tener acceso a los datos de los dos orígenes de entrada espacial a través de las mismas API en Unity.

Unity proporciona dos maneras principales de tener acceso a los datos de entrada espacial para Windows Mixed Reality. Las API de *Input. GetButton/Input. GetAxis* comunes funcionan en varios SDK de Unity XR, mientras que la API *InteractionManager/GestureRecognizer* específica de Windows Mixed Reality expone el conjunto completo de datos de entrada espacial.

## <a name="unity-xr-input-apis"></a>API de entrada de Unity XR

En el caso de los proyectos nuevos, se recomienda usar las nuevas API de entrada de XR desde el principio. 

Puede encontrar más información sobre las [API de XR aquí](https://docs.unity3d.com/Manual/xr_input.html).

## <a name="unity-buttonaxis-mapping-table"></a>Tabla de asignación de ejes y botones de Unity

El administrador de entrada de Unity para los controladores de movimiento de Windows Mixed Reality es compatible con los identificadores de botón y de eje que se enumeran a continuación a través de las API *Input. GetButton/GetAxis* . La columna "específico de Windows MR" hace referencia a las propiedades disponibles fuera del tipo *InteractionSourceState* . Cada una de estas API se describe en detalle en las secciones siguientes.

Las asignaciones de identificador de botón/eje para Windows Mixed Reality suelen coincidir con los identificadores del botón o del eje Oculus.

Las asignaciones de identificador de botón/eje para Windows Mixed Reality difieren de las asignaciones de OpenVR de dos maneras:
1. La asignación usa identificadores de Touchpad distintos del stick analógico para admitir controladores con thumbsticks y Touchpad.
2. La asignación evita la sobrecarga de los identificadores de botón A y X de los botones de menú para dejarlos a disposición de los botones de ABXY físicos.

<table>
<tr>
<th rowspan="2">Entrada </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API comunes de Unity</a><br />(Input. GetButton/GetAxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">API de entrada específica de Windows MR</a><br />XR. WSA. Entradas</th>
</tr><tr>
<th> Mano izquierda </th><th> Mano derecha</th>
</tr><tr>
<td> Seleccionar desencadenador presionado </td><td> Eje 9 = 1,0 </td><td> Eje 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Seleccionar desencadenador de valor analógico </td><td> Eje 9 </td><td> Eje 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Seleccionar desencadenador parcialmente presionado </td><td> Botón 14 <i>(compatibilidad con el controlador de juegos)</i> </td><td> Botón 15 <i>(compatibilidad con el controlador de juegos)</i> </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Botón de menú presionado </td><td> Botón 6 * </td><td> Botón 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Botón de control presionado </td><td> Eje 11 = 1,0 (sin valores analógicos)<br />Botón 4 <i>(compatibilidad con el controlador de juegos)</i> </td><td> Eje 12 = 1,0 (sin valores analógicos)<br />Botón 5 <i>(compatibilidad con el controlador de juegos)</i> </td><td> entendido</td>
</tr><tr>
<td> Stick analógico X <i>(izquierda:-1,0, derecha: 1,0)</i> </td><td> Eje 1 </td><td> Eje 4 </td><td> thumbstickPosition. x</td>
</tr><tr>
<td> Stick analógico Y <i>(superior:-1,0, inferior: 1,0)</i> </td><td> Eje 2 </td><td> Eje 5 </td><td> thumbstickPosition. y</td>
</tr><tr>
<td> Stick analógico presionado </td><td> Botón 8 </td><td> Botón 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(izquierda:-1,0, derecha: 1,0)</i> </td><td> Eje 17 * </td><td> Eje 19 * </td><td> touchpadPosition. x</td>
</tr><tr>
<td> Touchpad Y <i>(superior:-1,0, inferior: 1,0)</i> </td><td> Eje 18 * </td><td> Eje 20 * </td><td> touchpadPosition. y</td>
</tr><tr>
<td> Touchpad tocado </td><td> Botón 18 * </td><td> Botón 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad presionado </td><td> Botón 16 * </td><td> Botón 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> replanteamiento de control de 6DoF o de puntero </td><td colspan="2"> El <i>puño</i> solo representa: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></td><td> Pase el <i>control</i> o el <i>puntero</i> como argumento: SourceState. sourcePose. TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Estado de seguimiento </td><td colspan="2"> <i>Riesgo de pérdida y precisión de la posición solo disponible a través de la API específica de MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. properties. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Estos ID. de botón o eje difieren de los identificadores que usa Unity para OpenVR debido a colisiones en las asignaciones que usan los controladores de juegos, Oculus Touch y OpenVR.

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


## <a name="grip-pose-vs-pointing-pose"></a>Replanteamiento de control frente a pose de puntero

Windows Mixed Reality admite controladores de movimiento en diversos factores de forma. El diseño de cada controlador difiere en su relación entre la posición del usuario y la dirección de "avance" natural que las aplicaciones deben usar para apuntar al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de supuestos que puede investigar para cada origen de interacción, la representación del **control** y la representación del **puntero**. Las coordenadas de reposición de control y de posición de puntero se expresan en todas las API de Unity en coordenadas globales de Unity.

### <a name="grip-pose"></a>Replanteamiento de control

El **puño** representa la ubicación de la palma de los usuarios, detectada por HoloLens o manteniendo un controlador de movimiento.

En los auriculares envolventes, la representación del puño es la que mejor se usa para representar **la mano del usuario** o **un objeto mantenido en la mano del usuario**. El replanteamiento de control también se usa al visualizar un controlador de movimiento. El **modelo representable** proporcionado por Windows para un controlador de movimiento utiliza la representación del puño como su origen y centro de rotación.

La pose de control se define específicamente de la siguiente manera:
* La **posición del puño**: Palm centroide cuando mantiene el controlador de forma natural, se ajusta hacia la izquierda o derecha para centrar la posición dentro del control. En el controlador de movimiento de Windows Mixed Reality, esta posición generalmente se alinea con el botón de agarre.
* **Eje derecho de la orientación del puño**: cuando se abre por completo la mano para formar una postura plana de 5 dedos, el rayo perpendicular a la palma (hacia delante de la mano izquierda y hacia atrás desde la mano derecha)
* El **eje hacia delante de la orientación del puño**: al cerrar la mano (como si contiene el controlador), el rayo que señala "reenviar" a través del tubo formado por los dedos no Thumb.
* **Eje hacia arriba de la orientación del puño**: el eje hacia arriba implícito por las definiciones derecha y hacia delante.

Puede acceder a la representación del puño a través de la API de entrada entre proveedores (XR) de Unity *[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o a través de la API específica de Windows Mr (*SourceState. SourcePose. TryGetPosition/Rotation*, que solicita los datos de pose para el nodo de **control** ).

### <a name="pointer-pose"></a>Representar puntero

La **pose de puntero** representa la punta del controlador que señala hacia delante.

La representación de puntero proporcionada por el sistema se usa mejor para Raycast cuando se **representa el propio modelo de controlador**. Si está representando algún otro objeto virtual en lugar del controlador, como un cañón virtual, debe apuntar con un rayo que sea más natural para ese objeto virtual, como un rayo que viaja a lo largo del barril del modelo de pistola definido por la aplicación. Dado que los usuarios pueden ver el objeto virtual y no el controlador físico, es probable que apunte con el objeto virtual sea más natural para los que usan su aplicación.

Actualmente, la pose de puntero solo está disponible en Unity a través de la API específica de Windows MR, *sourceState. sourcePose. TryGetPosition/Rotation*, pasando *InteractionSourceNode. Pointer* como argumento.

## <a name="controller-tracking-state"></a>Estado de seguimiento del controlador

Al igual que los auriculares, el controlador de movimiento de Windows Mixed Reality no requiere la configuración de sensores de seguimiento externos. En su lugar, el seguimiento de los controladores se realiza mediante sensores en el propio casco.

Si el usuario mueve los controladores fuera del campo de vista del casco, Windows continúa inferencia de las posiciones del controlador en la mayoría de los casos. Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se quitarán de las posiciones de precisión aproximada.

En este punto, el sistema bloqueará el controlador al usuario, realizará un seguimiento de la posición del usuario a medida que se mueven, mientras se expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan Controladores para apuntar a los elementos de la interfaz de usuario y activarlos pueden funcionar con normalidad mientras tienen una precisión aproximada sin que el usuario lo note.

La mejor manera de hacerse una idea es probarlo. Consulte este vídeo con ejemplos de contenido envolvente que funciona con controladores de movimiento en varios Estados de seguimiento:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Razonamiento sobre el estado de seguimiento explícitamente

Las aplicaciones que quieren tratar las posiciones de manera diferente según el estado de seguimiento pueden ir más allá e inspeccionar las propiedades en el estado del controlador, como *SourceLossRisk* y *PositionAccuracy*:

<table>
<tr>
<th> Estado de seguimiento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisión</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Alta precisión (riesgo de pérdida)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Precisión aproximada</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ninguna posición</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> false</td>
</tr>
</table>

Estos Estados de seguimiento del controlador de movimiento se definen de la siguiente manera:
* **Alta precisión:** Aunque el controlador de movimiento está en el campo de vista del casco, normalmente proporcionará posiciones de alta precisión en función del seguimiento visual. Un controlador de movimiento que deja momentáneamente el campo de vista o que se oculta momentáneamente de los sensores de auriculares (por ejemplo, por la otra mano del usuario) seguirá devolviendo resultados de alta precisión durante un breve período de tiempo, en función del seguimiento inerte del propio controlador.
* **Alta precisión (riesgo de pérdida):** Cuando el usuario mueve el controlador de movimiento más allá del borde del campo de vista del casco, el casco pronto no podrá realizar un seguimiento visual de la posición del controlador. La aplicación sabe cuándo el controlador ha alcanzado este límite de hiperapartados; para ello, vea el **SourceLossRisk** Reach 1,0. En ese momento, la aplicación puede optar por pausar los gestos del controlador que requieren un flujo estable de planteamientos de alta calidad.
* **Precisión aproximada:** Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se quitarán de las posiciones de precisión aproximada. En este punto, el sistema bloqueará el controlador al usuario, realizará un seguimiento de la posición del usuario a medida que se mueven, mientras se expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan Controladores para apuntar a los elementos de la interfaz de usuario y activarlos pueden funcionar de la manera normal, pero con una precisión aproximada sin que los usuarios lo noten. Las aplicaciones con requisitos de entrada más pesados pueden optar por detectar este descenso de **alta** precisión a una precisión **aproximada** mediante la inspección de la propiedad **PositionAccuracy** , por ejemplo, para proporcionar al usuario una hitbox más amplia en los destinos de la pantalla durante este tiempo.
* **Ninguna posición:** Aunque el controlador puede funcionar con una precisión aproximada durante mucho tiempo, a veces el sistema sabe que incluso una posición bloqueada por el cuerpo no es significativa en este momento. Por ejemplo, un controlador que se ha activado puede que nunca se haya observado visualmente, o que un usuario pueda poner un controlador que recoja otro usuario. En ese momento, el sistema no proporcionará ninguna posición a la aplicación y *TryGetPosition* devolverá FALSE.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>API de Unity comunes (Input. GetButton/GetAxis)

**Espacio de nombres:** *UnityEngine*, *UnityEngine. XR*<br>
**Types**: *Input*, *XR. InputTracking*

Unity usa actualmente sus API de *entrada general. GetButton/Input. GetAxis* para exponer la entrada para [el SDK de Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [el SDK de OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html) y Windows Mixed Reality, incluidas las manos y los controladores de movimiento. Si la aplicación usa estas API para la entrada, puede admitir fácilmente controladores de movimiento en varios SDK de XR, incluido Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Obtener el estado presionado de un botón lógico

Para usar las API de entrada de Unity generales, normalmente se empieza por conectar botones y ejes a nombres lógicos en el [Administrador de entrada de Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), enlazando un botón o ID. de eje a cada nombre. Después, puede escribir código que haga referencia a ese botón o nombre de eje lógico.

Por ejemplo, para asignar el botón de desencadenador del controlador de movimiento izquierdo a la acción de envío, vaya a **editar > configuración del proyecto > entrada** en Unity y expanda las propiedades de la sección enviar en ejes. Cambie el botón **positivo** o la propiedad del **botón positivo alternativo** para leer el **botón 14 del joystick**, de la siguiente manera:

![InputManager de Unity](images/unity-input-manager.png)<br>
*InputManager de Unity*

Después, el script puede comprobar la acción de envío mediante *Input. GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Puede agregar más botones lógicos cambiando la propiedad **tamaño** en **ejes**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Obtener el estado presionado del botón físico directamente

También puede tener acceso a los botones manualmente por su nombre completo, mediante *Input. GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Obtención de un controlador de movimiento o mando a mano

Puede tener acceso a la posición y la rotación del controlador mediante *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> El código anterior representa la representación del puño del controlador (donde el usuario contiene el controlador), que es útil para representar un arma o un cañón en la mano del usuario, o un modelo del propio controlador.
> 
> La relación entre esta postura de control y el representador de puntero (donde está señalando la punta del controlador) puede diferir entre los controladores. En este momento, el acceso a la pose de puntero del controlador solo es posible a través de la API de entrada específica de MR, que se describe en las secciones siguientes.

## <a name="windows-specific-apis-xrwsainput"></a>API específicas de Windows (XR. WSA. Entradas

> [!CAUTION]
> Si el proyecto usa cualquiera de las de XR. Las API de WSA, se están desinstalando en favor del SDK de XR en futuras versiones de Unity. En el caso de los proyectos nuevos, se recomienda usar el SDK de XR desde el principio. Puede encontrar más información sobre el [sistema de entrada de XR y las API aquí](https://docs.unity3d.com/Manual/xr_input.html).

**Espacio de nombres:** *UnityEngine. XR. WSA. Input*<br>
**Tipos**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Para obtener información más detallada sobre la entrada de mano de Windows Mixed Reality (para HoloLens) y los controladores de movimiento, puede optar por usar las API de entrada espacial específicas de Windows en el espacio de nombres *UnityEngine. XR. WSA. Input* . Esto le permite tener acceso a información adicional, como la precisión de la posición o el tipo de origen, lo que permite indicar a las manos y los controladores.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Sondeo del estado de los controladores de manos y de movimiento

Puede sondear el estado de este fotograma para cada origen de interacción (controlador de movimiento o mano) mediante el método *GetCurrentReading* .

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Cada *InteractionSourceState* que recibe representa un origen de interacción en el momento actual. *InteractionSourceState* expone información como:
* Qué [tipos de pulsaciones](../../design/motion-controllers.md) se están produciendo (Select/menu/agarre/Touchpad/Stick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Otros datos específicos de los controladores de movimiento, tales como las coordenadas XY y/o el estado de tocado del Stick.

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

### <a name="polling-for-forward-predicted-rendering-poses"></a>Sondeo de representación de representación de predicción de reenvío

* Cuando se realiza un sondeo de los datos de origen de interacción de las manos y los controladores, las supuestos que obtiene son supuestos predichos en el momento en que las fotos de este fotograma llegarán a los ojos del usuario.  Los planteamientos de predicción se usan mejor para **representar** el controlador o un objeto mantenido en cada fotograma.  Si el destino es una determinada pulsación o versión con el controlador, será más preciso si usa las API de eventos históricos que se describen a continuación.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* También puede obtener el representa el encabezado de predicción hacia delante para este marco actual.  Al igual que en el caso de la representación de origen, esto resulta útil para **representar** un cursor, aunque el destino de una determinada pulsación o versión será más preciso si usa las API de eventos históricos que se describen a continuación.

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

Para controlar los eventos de entrada a medida que se producen con sus datos de pose históricos precisos, puede controlar los eventos de origen de interacción en lugar de realizar un sondeo.

Para controlar los eventos de origen de interacción:
* Regístrese para un evento de entrada *InteractionManager* . Para cada tipo de evento de interacción que le interese, necesita suscribirse a él.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Controle el evento. Una vez que se haya suscrito a un evento de interacción, recibirá la devolución de llamada cuando sea necesario. En el ejemplo *SourcePressed* , será una vez detectado el origen y antes de que se libere o se pierda.

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

Debe dejar de controlar un evento cuando ya no le interese en el evento o si está destruyendo el objeto que se ha suscrito al evento. Para dejar de controlar el evento, cancele la suscripción del evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Lista de eventos de origen de interacción

Los eventos de origen de interacción disponibles son:
* *InteractionSourceDetected* (el origen se activa)
* *InteractionSourceLost* (se convierte en inactivo)
* *InteractionSourcePressed* (TAP, presionar botón o "seleccionar")
* *InteractionSourceReleased* (final de una pulsación, botón liberado o final de "Select")
* *InteractionSourceUpdated* (se mueve o cambia cualquier estado)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Los eventos de destinatarios históricos suponen que coinciden con más precisión con una prensa o una versión

Las API de sondeo descritas anteriormente proporcionan a la aplicación las supuestos predecidas.  Aunque los planteamientos predichos son idóneos para representar el controlador o un objeto de dispositivo de mano virtual, los planteamientos futuros no son óptimos para el destino, por dos motivos clave:
* Cuando el usuario presiona un botón en un controlador, puede haber aproximadamente 20 ms de latencia inalámbrica a través de Bluetooth antes de que el sistema reciba la prensa.
* A continuación, si usa una pose de predicción, se aplicará otro 10-20 ms de predicción hacia delante para dirigirse a la hora en que las fotos del fotograma actual llegarán a los ojos del usuario.

Esto significa que el sondeo le proporciona una pose de origen o un representador de cabeza que es 30-40 ms hacia delante desde donde el encabezado del usuario y las manecillas se han vuelto realmente cuando se produjo la prensa o la versión.  Para la entrada de la mano de HoloLens, aunque no hay ningún retraso de la transmisión inalámbrica, hay un retraso de procesamiento similar para detectar la prensa.

Para establecer como destino con precisión en función de la intención original del usuario de una mano o de un controlador, debe usar la representación de origen histórica o la representación del encabezado de ese evento de entrada *InteractionSourcePressed* o *InteractionSourceReleased* .

Puede tener como destino una imprenta o una versión con datos de pose históricos del encabezado del usuario o del controlador:
* El encabezado se representa en el momento en que se produjo un gesto o un pulsador del controlador, que se puede usar para determinar el **destino** en el que se [Gazing](../../design/gaze-and-commit.md) el usuario:

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

* La suposición de origen en el momento en que se produce una acción del controlador de movimiento, que se puede usar para determinar el **destino** del controlador.  Este será el estado del controlador que experimentó la pulsación.  Si está representando el propio controlador, puede solicitar la representación del puntero en lugar de la representación del control para captar el rayo de destino de lo que el usuario considerará la punta natural de ese controlador representado:

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

## <a name="motion-controllers-in-mrtk-v2"></a>Controladores de movimiento en MRTK V2

Puede tener acceso al [gesto y al controlador de movimiento](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) desde el administrador de entrada.

## <a name="follow-along-with-tutorials"></a>Seguimiento de tutoriales

Los tutoriales paso a paso, con ejemplos de personalización más detallados, están disponibles en la Academia de realidad mixta:

- [MR Input 211: gesto](tutorials/holograms-211.md)
- [MR Input 213: controladores de movimiento](../../deprecated/mixed-reality-213.md)

[![Entrada MR 213-controlador de movimiento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Entrada MR 213-controlador de movimiento*

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Seguimiento de manos y ocular](hand-eye-in-unit.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también

* [Mirada-cabeza y confirmación](../../design/gaze-and-commit.md)
* [Controladores de movimiento](../../design/motion-controllers.md)
