---
title: Cómo agregar una interactividad casi
description: Documentación sobre la interacción próxima en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, interacción cercana,
ms.openlocfilehash: fc0d6d4013392db74e5c8637574c258bee857865
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144188"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a>Cómo agregar una interacción cercana en MRTK

Las interacciones cercanas tienen la forma de toques y agarres. Los eventos touch y grab se elevan como eventos de puntero por [parte de Los objetos Depointer](pointers.md#pokepointer) y [SpherePointer,](pointers.md#spherepointer)respectivamente.

Se requieren tres pasos clave para escuchar eventos de entrada táctiles o de entrada en un GameObject determinado.

1. Asegúrese de que el puntero correspondiente está registrado en el perfil de configuración de [MRTK principal.](../../configuration/mixed-reality-configuration-guide.md)
1. Asegúrese de que el Elemento GameObject deseado tiene el componente de script [táctil](#add-grab-interactions) [o](#add-touch-interactions) de agarre adecuado y [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. Implemente una interfaz de controlador de entrada en un script adjunto al GameObject deseado para escuchar los [eventos de entrada](#grab-code-example) [táctil.](#touch-code-example)

## <a name="add-grab-interactions"></a>Adición de interacciones de agarre

1. Asegúrese de [que spherepointer](pointers.md#spherepointer) está registrado en el *perfil de puntero MRTK*.

    El perfil de MRTK predeterminado y el HoloLens 2 predeterminado ya contienen *un spherepointer*. Para confirmar que se creará spherepointer, seleccione el perfil de configuración de MRTK y vaya a **Input**  >  **Pointers** Pointer Options (Opciones de puntero de puntero de  >  **entrada).** El `GrabPointer` objeto prefab predeterminado (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers)  debe aparecer con un tipo de controlador *de mano articulada.* Se puede usar un prefab personalizado siempre que implemente la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) clase .

    ![Ejemplo de perfil de puntero de captura](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    El puntero de toma predeterminado consulta objetos cercanos en un cono alrededor del punto de toma para que coincida con la interfaz predeterminada de Hololens 2.

    ![Puntero de toma cónica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. En el Elemento GameObject que se debe poder agarrar, agregue [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) un elemento , así como un colisionador.

    Asegúrese de que la capa de GameObject está en una capa que se puede agarrar. De forma predeterminada, se pueden capturar todas las *capas excepto Reconocimiento* espacial e Ignorar *raycasts.* Vea qué capas se pueden agarrar inspeccionando las *máscaras* de capa de captura en el prefab *de GrabPointer.*

1. En GameObject o en uno de sus antecesores, agregue un componente de script que implemente la [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interfaz . Cualquier antecesor del objeto con [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) también podrá recibir eventos de puntero.

### <a name="grab-code-example"></a>Ejemplo de código de captura

A continuación se muestra un script que se imprimirá si un evento es un toque o una toma. En la función de *interfaz IMixedRealityPointerHandler* pertinente, se puede ver el tipo de puntero que desencadena ese evento a través de [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . Si el puntero es *spherepointer,* la interacción es una toma.

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a>Adición de interacciones táctiles

El proceso para agregar interacciones táctiles en elementos UnityUI es diferente al de gameObjects 3D de la vaina. Puede ir directamente a la sección siguiente, Interfaz de usuario *de Unity,* para habilitar los componentes de la interfaz de usuario de Unity.

Sin **embargo,** para ambos tipos de elementos de la experiencia del usuario, asegúrese de que Se haya registrado [Un elemento Depointer](pointers.md#pokepointer) en el perfil de puntero de *MRTK*.

El perfil de MRTK predeterminado y el HoloLens 2 predeterminado ya contienen *un valor de Tipo Depointer*. Se puede confirmar que se creará un elemento PointerePointer seleccionando el perfil de configuración de MRTK y navegando a Input  >  **Pointers** Pointer Options (Opciones de puntero de puntero de  >  **entrada).** El `PokePointer` objeto prefab predeterminado (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers)  debe aparecer con un tipo de controlador *de mano articulada.* Un objeto prefab personalizado se puede usar siempre que implemente la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) clase .

![Ejemplo de perfil de puntero de puntero de puntero de puntero](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>GameObjects 3D

Hay dos maneras diferentes de agregar interacciones táctiles a objetos GameObject 3D, en función de si el objeto 3d solo debe tener un solo plano táctil, o de si debe ser táctil en función de todo su colisionador.
La primera forma suele ser en objetos con BoxColliders, donde solo se desea que una sola cara del colisionador reaccione a eventos táctiles. La otra es para objetos que deben ser táctiles desde cualquier dirección en función de su colisionador.

### <a name="single-face-touch"></a>Single face touch

Esto es útil para habilitar situaciones en las que solo una cara debe ser táctil. Esta opción supone que el objeto de juego tiene boxcollider. es posible usar esto con objetos que no son BoxCollider, en cuyo caso las propiedades "Bounds" y "Local Center" se establecen de forma manual para configurar el plano táctil (es decir, los límites deben establecerse en un valor distinto de cero-cero).

1. En el Elemento GameObject que debe ser táctil, agregue un componente BoxCollider y [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable).

    1. Establezca **Eventos en Recibir** en *Táctil* si usa la interfaz [ ] `IMixedRealityTouchHandler` (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) en el siguiente script de componente.

    1. Haga clic **en Fix bounds (Límites de** corrección) y fix center **(Centro de corrección).**

    ![Instalación de NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. En ese objeto o en uno de sus antecesores, agregue un componente de script que implemente el [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Interfaz. Cualquier antecesor del objeto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) también podrá recibir eventos de puntero.

> [!NOTE]
> En la vista de escena del editor con *el elemento GameObject NearInteractionTouchable* seleccionado, observe un cuadrado y una flecha de contorno blanco. La flecha apunta a la "parte frontal" del control táctil. El que se puede colisionar solo será táctil desde esa dirección. Para que un colisionador sea táctil desde todas las direcciones, consulte la sección sobre [la función táctil arbitraria del colisionador.](#arbitrary-collider-touch)
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Toque de colisionador arbitrario

Esto es útil para habilitar situaciones en las que el objeto de juego debe ser táctil a lo largo de toda la cara del colisionador. Por ejemplo, esto se puede usar para habilitar interacciones táctiles para un objeto con spherecollider, donde todo el colisionador debe ser táctil.

1. En el Elemento GameObject que debe ser táctil, agregue un colisionador y un componente [ `NearInteractionTouchableVolume` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume).

    1. Establezca **Eventos en Recibir** en *Táctil* si usa la interfaz [ ] `IMixedRealityTouchHandler` (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) en el siguiente script de componente.

1. En ese objeto o uno de sus antecesores, agregue un componente de script que implemente el [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Interfaz. Cualquier antecesor del objeto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) también podrá recibir eventos de puntero.

### <a name="unity-ui"></a>Interfaz de usuario de Unity

1. Agregue o asegúrese de que hay un [lienzo de UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) en la escena.

1. En el Elemento GameObject que debe ser táctil, agregue un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.  

    1. Establezca **Eventos en Recibir en** *Táctil* si usa la interfaz en el siguiente script [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) de componente.

1. En ese objeto o uno de sus antecesores, agregue un componente de script que implemente la [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interfaz . Cualquier antecesor del objeto con [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) también podrá recibir eventos de puntero.

> [!IMPORTANT]
> Es posible que los objetos no se comporten según lo previsto si se encuentran en objetos de lienzo superpuestos. Para garantizar un comportamiento coherente, nunca superponga los objetos de lienzo en la escena.

> [!IMPORTANT]
> En el `NearInteractionTouchable` componente de script, para la propiedad *Eventos que se van a recibir* hay dos opciones: *Puntero* y *Táctil.* Establezca *Events (Eventos)* en Receive (Recibir) en *Pointer* (Puntero) si usa la interfaz y establezca en Touch si usa la interfaz del script de componente que [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) responde o controla los eventos de  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) entrada.

#### <a name="touch-code-example"></a>Ejemplo de código táctil

El código siguiente muestra un MonoBehaviour que se puede adjuntar a un Elemento GameObject con un componente variante y responder a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) eventos de entrada táctiles.

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a>Ejemplos de script de interacción cercana

### <a name="touch-events"></a>Eventos de función táctil

En este ejemplo se crea un cubo, se puede tocar y se cambia el color al tocar.

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a>Eventos de captura

En el ejemplo siguiente se muestra cómo hacer que un Objeto GameObject se puede arrastrar. Supone que el objeto de juego tiene un colisionador.

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a>API útiles

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>Consulte también

* [Información general sobre acciones del usuario](overview.md)
* [Punteros](pointers.md)
* [Eventos de entrada](input-events.md)
