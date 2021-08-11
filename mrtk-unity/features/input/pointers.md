---
title: Punteros
description: Documentación sobre punteros en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, punteros,
ms.openlocfilehash: 9fec02e7866aaf867c7145491bfd84f727e039cdd7a4323ace9c65f74e49480a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191020"
---
# <a name="pointers"></a>Punteros

![Puntero](../images/pointers/MRTK_Pointer_Main.png)

En este artículo se explica cómo configurar y responder a la entrada de puntero en la práctica, en comparación con [la arquitectura de puntero.](../../architecture/controllers-pointers-and-focus.md)

Los punteros se crean automáticamente en tiempo de ejecución cuando se detecta un nuevo controlador. Se puede adjuntar más de un puntero a un controlador. Por ejemplo, con el perfil de puntero predeterminado, los controladores Windows Mixed Reality obtienen una línea y un puntero parabólico para la selección normal y la teleportación respectivamente.

## <a name="pointer-configuration"></a>Configuración de puntero

Los punteros se configuran como parte del sistema de entrada de MRTK a través de [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) . Este tipo de perfil se asigna a en [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) el inspector de configuración de MRTK. El perfil de puntero determina el cursor, los tipos de punteros disponibles en tiempo de ejecución y cómo esos punteros se comunican entre sí para decidir cuál está activo.

- *Extensión apuntando:* define la distancia máxima para la que un puntero puede interactuar con un GameObject.

- *Apuntar máscaras de* capa de rayas: se trata de una matriz prioritaria de máscaras de capa para determinar con qué objetos GameObject posibles puede interactuar un puntero determinado y el orden de interacción que se va a intentar. Esto puede ser útil para asegurarse de que los punteros interactúan primero con los elementos de la interfaz de usuario antes que otros objetos de escena.
![Ejemplo de perfil de puntero](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>Configuración de opciones de puntero

La configuración predeterminada del perfil de puntero MRTK incluye las siguientes clases de puntero y los elementos prefabs asociados de fábrica. La lista de punteros disponibles para el sistema en tiempo de ejecución se define en *Opciones de puntero* en el perfil de puntero. Los desarrolladores pueden usar esta lista para volver a configurar los punteros existentes, agregar nuevos punteros o eliminar uno.

![Ejemplo de perfil de opciones de puntero](../images/input/pointers/PointerOptionsProfile.PNG)

Cada entrada pointer se define mediante el siguiente conjunto de datos:

- *Tipo de* controlador: el conjunto de controladores para los que un puntero es válido.
  - Por ejemplo, El contrapunto *es* responsable de "deslizar" objetos con un dedo y, de forma predeterminada, está marcado como solo compatible con el tipo de controlador de mano articulado. Solo se crean instancias de los punteros cuando  un controlador está disponible y, en concreto, el tipo de controlador define con qué controladores se puede crear este objeto prefab de puntero.

- *Entrega:* permite que solo se cree una instancia de un puntero para una mano específica (izquierda/derecha)

> [!NOTE]
> Si se *establece la propiedad Handedness* de una entrada pointer en *None,* se deshabilitará de forma eficaz desde el sistema como alternativa a quitar ese puntero de la lista.

- *Prefab de puntero:* se crea una instancia de este recurso prefab cuando se inicia el seguimiento de un controlador que coincide con el tipo de controlador y la entrega especificados.

Es posible tener varios punteros asociados a un controlador. Por ejemplo, en `DefaultHoloLens2InputSystemProfile` (Assets/MRTK/SDK/Profiles/HoloLens2/) el controlador de mano articulado está asociado con El controlador de mano articulado, *GrabPointer* y *DefaultControllerPointer* (es decir, rayos de mano).

> [!NOTE]
> MRTK proporciona un conjunto de elementos prefabs de puntero en *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers*. Se puede crear un nuevo objeto prefab personalizado siempre que contenga uno de los scripts de puntero de *Assets/MRTK/SDK/Features/UX/Scripts/Pointers* o cualquier otro script que implemente [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) .

### <a name="default-pointer-classes"></a>Clases de puntero predeterminadas

Las clases siguientes son los punteros MRTK de fábrica disponibles y definidos en el perfil de *puntero MRTK* predeterminado descrito anteriormente. Cada elemento prefab de puntero proporcionado en *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers* contiene uno de los componentes de puntero adjuntos.

![Punteros predeterminados de MRTK](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>Punteros lejanos

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *LinePointer*, una clase de puntero base, dibuja una línea del origen de la entrada (es decir, el controlador) en la dirección del puntero y admite una sola conversión de rayo en esta dirección. Por lo general, se crea una instancia de las clases secundarios, como y los punteros teleport, y se usan (que también dibujan líneas para indicar dónde terminará la teleportación) en lugar de esta clase que proporciona principalmente funcionalidad [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) común.

En el caso de los controladores de movimiento como Oculus, Vive y Windows Mixed Reality, la rotación coincidirá con la rotación del controlador. Para otros controladores como HoloLens 2 manos articuladas, la rotación coincide con la posición de apuntamiento de la mano proporcionada por el sistema.

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer* amplía la clase *LinePointer* al permitir la conversión de rayos de varios pasos a lo largo de una curva. Esta clase de puntero base es útil para las instancias curvas, como los punteros de teleportación, donde la línea se inclina constantemente en una parabola.

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

La implementación de *ShellHandRayPointer*, que se extiende desde , se usa como valor predeterminado [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) para el perfil de puntero *MRTK*. El *objeto prefab DefaultControllerPointer* implementa la [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) clase .

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

También conocido como el puntero De mirada, gesto y voz *(GGV),* el GGVPointer potencia HoloLens las interacciones de pulsación y apariencia de estilo 1, principalmente a través de La mirada y pulsación en el aire o la interacción de selección de mirada y voz. La posición y la dirección del puntero GGV están controladas por la posición y rotación de la cabeza.

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

*TouchPointer es* responsable de trabajar con la entrada de Unity Touch (es decir, pantalla táctil). Se trata de "interacciones lejanas" porque el acto de tocar la pantalla proyectará un rayo desde la cámara a una ubicación potencialmente lejana de la escena.

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

*MousePointer impulsa* una pantalla a la transmisión por rayos del mundo para interacciones lejanas, pero para el mouse en lugar de táctil.

![Puntero](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> La compatibilidad con el mouse no está disponible de forma  predeterminada en MRTK, pero se puede habilitar agregando un nuevo proveedor de datos de entrada de tipo al perfil de entrada de MRTK y asignando al proveedor [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) de [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) datos.

#### <a name="near-pointers"></a>Punteros cercanos

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[El objeto Detepointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* se usa para interactuar con objetos de juego que admiten "interacción cercana táctil". que son objetos GameObject que tienen un [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) script adjunto. En el caso de UnityUI, este puntero busca NearInteractionTouchableUnityUIs.  El elemento DePointer usa SphereCast para determinar el elemento táctil más cercano y se usa para encender elementos como los botones que se pueden presionar.

 Al configurar GameObject con el componente , asegúrese de configurar el parámetro localForward para que apunte a la parte delantera del botón u otro objeto que se debe poder [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) tocar.  Asegúrese también de que los *límites* del objeto táctil coincidan con los límites del objeto táctil.

Propiedades útiles del puntero de puntero de puntero:

- *TouchableDistance:* distancia máxima con la que se puede interactuar con una superficie táctil
- *Objetos visuales:* objeto de juego que se usa para representar el objeto visual de la punta del dedo (el anillo en el dedo, de forma predeterminada).
- *Línea:* línea opcional para dibujar desde el dedo a la superficie de entrada activa.
- *Máscaras de capa de máscaras* de capa: matriz prioritaria de máscaras de capas para determinar con qué objetos GameObject posibles puede interactuar el puntero y el orden de interacción que se va a intentar. Tenga en cuenta que un Elemento GameObject también debe tener `NearInteractionTouchable` un componente para interactuar con un puntero de puntero.

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* usa [UnityEngine.Physics.OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) con el fin de identificar el objeto más cercano para la interacción, lo que resulta útil para la entrada [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) "capturable" como `ManipulationHandler` . De forma similar al par funcional, para poder interactuar con el puntero sphere, el objeto de juego debe contener un [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) componente que sea el [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) script.

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

Propiedades útiles del puntero sphere:

- *Radio de conversión de esfera:* el radio de la esfera que se usa para consultar objetos que se pueden agarrar.
- *Margen de objeto* cercano: distancia en la parte superior del radio de conversión de esfera que se va a consultar para detectar si un objeto está cerca del puntero. El radio total de detección de objetos cercanos es Radio de conversión de esfera + Margen de objeto cercano
- *Ángulo del sector de objetos cercanos:* ángulo alrededor del eje hacia delante del puntero para consultar objetos cercanos. Hace que `IsNearObject` la función de consulta sea como un cono. Se establece en 66 grados de forma predeterminada para que coincida con el comportamiento de Hololens 2.

![Puntero de Sphere modificado para consultar únicamente objetos en dirección hacia delante](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *Near Object Smoothing Factor*: factor de suavizado para la detección de objetos cercanos. Si se detecta un objeto en el radio de objeto cercano, el radio consultado se convierte en Radio de objeto cercano * (1 + Factor de suavizado de objetos cercanos) para reducir la sensibilidad y dificultar que un objeto salga del intervalo de detección.
- *Obtener máscaras de capa:* matriz prioritaria de máscaras de capa para determinar con qué objetos GameObject posibles puede interactuar el puntero y el orden de interacción que se va a intentar. Tenga en cuenta que un Elemento GameObject también debe tener `NearInteractionGrabbable` un elemento para interactuar con spherepointer.
    > [!NOTE]
    > La capa de reconocimiento espacial está deshabilitada en el objeto prefab grabPointer predeterminado proporcionado por MRTK. Esto se hace para reducir el impacto en el rendimiento de realizar una consulta de superposición de esfera con la malla espacial. Puede habilitarlo modificando el prefab grabPointer.
- *Ignore Colliders Not in FOV* (Omitir colisiondores no en FOV) : indica si se deben omitir los colisiondores que pueden estar cerca del puntero, pero que no están realmente en el FOV visual.
Esto puede evitar las toma accidentales y permitirá que los rayos de las manos se activen cuando pueda estar cerca de un control grabable, pero no pueda verlo. La *fov visual* se define a través de un cono en lugar del frustum típico por motivos de rendimiento. Este cono está centrado y orientado igual que el frusto de la cámara con un radio igual a la altura de la pantalla media (o FOV vertical).

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>Teleportar punteros

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) genera una solicitud de teleporto cuando se toma una acción (es decir, se presiona el botón teleportar) para mover al usuario.
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) genera una solicitud de teleporto cuando se toma una acción (es decir, se presiona el botón teleportar) con un raycast de línea parabólica para mover al usuario.

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>Compatibilidad con punteros para plataformas de realidad mixta

En la tabla siguiente se detallan los tipos de puntero que se usan normalmente para las plataformas comunes de MRTK. NOTA: Es posible agregar diferentes tipos de puntero a estas plataformas. Por ejemplo, podría agregar un puntero Desagregar o un puntero sphere a VR. Además, los dispositivos vr con un gamepad podrían usar el puntero GGV.

|       Puntero              | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | Válido   | Válido                 |            | Válido      |
| TeleportPointer     | Válido   | Válido                 |            |            |
| GGVPointer          |         |                       | Válido      |            |
| SpherePointer       |         |                       |            | Válido      |
| Contrapunto         |         |                       |            | Válido      |

## <a name="pointer-interactions-via-code"></a>Interacciones de puntero a través de código

### <a name="pointer-event-interfaces"></a>Interfaces de eventos de puntero

MonoBehaviours que implementan una o varias de las interfaces siguientes y se asignan a un GameObject con un recibirá eventos de interacciones de puntero tal como se define en la `Collider` interfaz asociada.

| Evento | Descripción | Controlador |
| --- | --- | --- |
| Antes de cambiar el foco/ Cambiar el foco | Se genera tanto en el objeto de juego que pierde el foco como en el que lo obtiene cada vez que un puntero cambia el foco. | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
Entrar y salir del foco | Se genera en el objeto de juego que obtiene el foco cuando el primer puntero lo entra y en el que pierde el foco cuando el último puntero lo deja. | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
Puntero hacia abajo/ arrastrado / arriba / hecho clic | Se genera para que el puntero de informe presione, arrastre y suelte. | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Touch Started/ Updated/Completed | Se genera mediante punteros táctiles como para [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) notificar la actividad táctil. | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) y [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) deben controlarse en los objetos en los que se elevan. Es posible recibir eventos de foco globalmente, pero, a diferencia de otros eventos de entrada, el controlador de eventos global no bloqueará la recepción de eventos en función del foco (el evento lo recibirá el controlador global y un objeto correspondiente en el foco).

#### <a name="pointer-input-events-in-action"></a>Eventos de entrada de puntero en acción

El sistema de entrada de MRTK reconoce y controla los eventos de entrada de puntero de forma similar a los [eventos de entrada normales.](input-events.md#input-events-in-action) La diferencia es que los eventos de entrada de puntero solo los controla gameObject en el foco por el puntero que ha desencadenado el evento de entrada, así como cualquier controlador de entrada global. GameObjects controla los eventos de entrada normales en el foco para todos los punteros activos.

1. El sistema de entrada MRTK reconoce que se ha producido un evento de entrada
1. El sistema de entrada MRTK desaconse la función de interfaz pertinente para el evento de entrada a todos los controladores de entrada globales registrados
1. El sistema de entrada determina qué GameObject está en el foco para el puntero que ha desencadenado el evento.
    1. El sistema de entrada utiliza el sistema de eventos de [Unity](https://docs.unity3d.com/Manual/EventSystem.html) para usar la función de interfaz pertinente para todos los componentes correspondientes en el GameObject centrado.
    1. Si en algún momento se ha marcado un evento de entrada como [usado,](input-events.md#how-to-stop-input-events)el proceso finalizará y ningún gameObject más recibirá devoluciones de llamada.
        - Ejemplo: Los componentes que implementan la interfaz buscarán si gameObject gana [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) o pierde el foco.
        - Nota: El sistema de eventos de Unity se burbujas para buscar el Elemento GameObject primario si no se encuentra ningún componente que coincida con la interfaz deseada en el GameObject actual.
1. Si no se registra ningún controlador de entrada global y no se encuentra gameObject con un componente o interfaz que coincida, el sistema de entrada llamará a cada controlador de entrada registrado de reserva.

#### <a name="example"></a>Ejemplo

A continuación se muestra un script de ejemplo que cambia el color del representador adjunto cuando un puntero toma o deja el foco o cuando un puntero selecciona el objeto.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>Punteros de consulta

Es posible recopilar todos los punteros actualmente activos si se recorren en bucle los orígenes de entrada disponibles (es decir, controladores y entradas disponibles) para detectar qué punteros están asociados a ellos.

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>Puntero principal

Los desarrolladores pueden suscribirse al evento FocusProviders PrimaryPointerChanged para recibir una notificación cuando el puntero principal en el foco haya cambiado. Esto puede ser muy útil para identificar si el usuario está interactuando actualmente con una escena a través de la mirada, un rayo de la mano u otro origen de entrada.

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

La `PrimaryPointerExample` escena (Assets/MRTK/Examples/Demos/Input/Scenes/PrimaryPointer) muestra cómo usar para eventos para responder a un [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) nuevo puntero principal.

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>Resultado del puntero

La propiedad [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) pointer contiene el resultado actual de la consulta de escena utilizada para determinar el objeto con el foco. En el caso de un puntero de difusión por rayos, como los creados de forma predeterminada para los controladores de movimiento, la entrada de mirada y los rayos de las manos, contendrá la ubicación y la normalidad de la transmisión por rayos.

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

La `PointerResultExample` escena (Assets/MRTK/Examples/Demos/Input/Scenes/PointerResult/PointerResultExample.unity) muestra cómo usar el puntero para generar un objeto en la ubicación de [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) acceso.

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>Deshabilitar punteros

Para activar y deshabilitar punteros (por ejemplo, para deshabilitar el rayo de mano), establezca para un tipo [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) de puntero determinado a través de [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) .

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

Vea [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) y para obtener más [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) ejemplos.

## <a name="pointer-interactions-via-editor"></a>Interacciones de puntero a través del editor

Para los eventos de puntero administrados por , MRTK proporciona mayor comodidad en forma del componente, lo que permite que los eventos de puntero se controle directamente a través [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) de eventos de Unity.

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>Extensión de puntero

Los punteros lejanos tienen configuraciones que limitan hasta qué punto se van a convertir en rayos e interactuar con otros objetos de la escena.
De forma predeterminada, este valor se establece en 10 metros. Este valor se ha elegido para mantener la coherencia con el comportamiento del HoloLens shell.

Esto se puede cambiar actualizando los campos del componente del `DefaultControllerPointer` [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) prefab:

*Extensión del* puntero: controla la distancia máxima con la que interactuarán los punteros.

*Extensión de puntero predeterminada:* controla la longitud del rayo o línea de puntero que se representará cuando el puntero no interactúe con nada.

## <a name="see-also"></a>Consulte también

- [Arquitectura de puntero](../../architecture/controllers-pointers-and-focus.md)
- [Eventos de entrada](input-events.md)
