---
title: Selección de destino de seguimiento de los ojos
description: Acceso a datos de mirada con los ojos y eventos específicos de mirada con los ojos para seleccionar destinos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144198"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="63401-104">Selección de destino compatible con los ojos</span><span class="sxs-lookup"><span data-stu-id="63401-104">Eye-supported target selection</span></span>

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="63401-106">En esta página se de abordan diferentes opciones para acceder a los datos de mirada con los ojos y a eventos específicos de mirada con los ojos para seleccionar destinos en MRTK.</span><span class="sxs-lookup"><span data-stu-id="63401-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="63401-107">El seguimiento de los ojos permite realizar selecciones de destino rápidas y sin  esfuerzo mediante una combinación de información sobre lo que un usuario está viendo con entradas adicionales, como el seguimiento de manos y los comandos _de voz:_</span><span class="sxs-lookup"><span data-stu-id="63401-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="63401-108">Busque & _"Seleccionar"_ (comando de voz predeterminado)</span><span class="sxs-lookup"><span data-stu-id="63401-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="63401-109">Busque & _"Explode"_ o _"Pop"_ (comandos de voz personalizados)</span><span class="sxs-lookup"><span data-stu-id="63401-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="63401-110">Buscar & de Bluetooth</span><span class="sxs-lookup"><span data-stu-id="63401-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="63401-111">Busque & acercar (es decir, mantener la mano delante de usted y reunir el dedo índice y el dedo)</span><span class="sxs-lookup"><span data-stu-id="63401-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="63401-112">Tenga en cuenta que para que esto funcione, es necesario deshabilitar los rayos [de las manos.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="63401-112">Please note that for this to work, the [hand rays need to be disabled](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="63401-113">Para seleccionar contenido holográfico mediante la mirada con los ojos, hay varias opciones:</span><span class="sxs-lookup"><span data-stu-id="63401-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="63401-114">**1. Use el puntero de foco principal:**</span><span class="sxs-lookup"><span data-stu-id="63401-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="63401-115">Esto se puede entender como el cursor priorizado.</span><span class="sxs-lookup"><span data-stu-id="63401-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="63401-116">De forma predeterminada, si las manos están a la vista, serían rayos de mano.</span><span class="sxs-lookup"><span data-stu-id="63401-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="63401-117">Si no hay manos a la vista, el puntero con prioridad sería la mirada con la cabeza o los ojos.</span><span class="sxs-lookup"><span data-stu-id="63401-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="63401-118">Por lo tanto, tenga en cuenta que, en función del diseño actual, la mirada con la cabeza o los ojos se suprime como entrada de cursor si se usan rayos de mano.</span><span class="sxs-lookup"><span data-stu-id="63401-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="63401-119">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="63401-119">For example:</span></span>

<span data-ttu-id="63401-120">Un usuario quiere seleccionar un botón holográfico lejano.</span><span class="sxs-lookup"><span data-stu-id="63401-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="63401-121">Como desarrollador, quiere proporcionar una solución flexible que permita al usuario realizar estas tareas en varias condiciones:</span><span class="sxs-lookup"><span data-stu-id="63401-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="63401-122">Subir hasta el botón y descándalo.</span><span class="sxs-lookup"><span data-stu-id="63401-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="63401-123">Míralo desde una distancia y diga "seleccionar"</span><span class="sxs-lookup"><span data-stu-id="63401-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="63401-124">Dirigir el botón mediante un rayo de mano y realizar una acción de acercamiento. En este caso, la solución más flexible es usar el controlador de foco principal, ya que le notificará cada vez que el puntero de foco principal con prioridad actual desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="63401-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="63401-125">Tenga en cuenta que si los rayos de las manos están habilitados, el puntero de foco de mirada con la cabeza o los ojos se deshabilita en cuanto las manos se ven.</span><span class="sxs-lookup"><span data-stu-id="63401-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63401-126">Tenga en cuenta que si los rayos de las manos están habilitados, el puntero de foco de mirada con la cabeza o los ojos se deshabilita en cuanto las manos se ven.</span><span class="sxs-lookup"><span data-stu-id="63401-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="63401-127">Si desea admitir una interacción [ _de "buscar_](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)y acercar", debe deshabilitar el rayo de mano .</span><span class="sxs-lookup"><span data-stu-id="63401-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="63401-128">En nuestras escenas de ejemplo de seguimiento de los ojos, hemos deshabilitado el rayo de la mano para permitir que se muestren interacciones más enriquecciones con los ojos y los movimientos de las manos; vea por ejemplo Posición compatible con los [ojos.](eye-tracking-eyes-and-hands.md)</span><span class="sxs-lookup"><span data-stu-id="63401-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span></span>

[<span data-ttu-id="63401-129">**2. Use el foco de los ojos y los rayos de las manos al mismo tiempo:**</span><span class="sxs-lookup"><span data-stu-id="63401-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="63401-130">Puede haber instancias en las que quiera ser más específico qué tipo de punteros de foco pueden desencadenar determinados eventos y permitir el uso simultáneo de varias técnicas de interacción lejana.</span><span class="sxs-lookup"><span data-stu-id="63401-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="63401-131">Por ejemplo: en la aplicación, un usuario puede usar rayos de mano lejanos para manipular algunas configuraciones mecánicas holográficas, por ejemplo, agarrar y retener algunas partes lejanas del motor holográfico y mantenerlas en su lugar.</span><span class="sxs-lookup"><span data-stu-id="63401-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="63401-132">Al hacerlo, el usuario tiene que seguir una serie de instrucciones y registrar su progreso marcando algunas casillas.</span><span class="sxs-lookup"><span data-stu-id="63401-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="63401-133">Si el usuario no tiene las manos ocupadas, sería instintivo simplemente tocar la casilla o seleccionarla con un rayo de mano.</span><span class="sxs-lookup"><span data-stu-id="63401-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="63401-134">Sin embargo, si el usuario tiene las manos ocupadas, como en nuestro caso, con algunas partes del motor holográfico en su lugar, quiere permitir que el usuario se desplace sin problemas por las instrucciones con la mirada con los ojos y simplemente mire una casilla y diga "comprobarlo".</span><span class="sxs-lookup"><span data-stu-id="63401-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="63401-135">Para habilitar esto, debe usar un script EyeTrackingTarget específico de los ojos que sea independiente de los principales focusHandlers de MRTK y que se analizará más adelante.</span><span class="sxs-lookup"><span data-stu-id="63401-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="63401-136">1. Usar controladores genéricos de puntero y foco</span><span class="sxs-lookup"><span data-stu-id="63401-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="63401-137">Si el seguimiento de los ojos está configurado correctamente (consulte Configuración básica de [MRTK](eye-tracking-basic-setup.md)para usar el seguimiento de los ojos), permitir a los usuarios seleccionar hologramas con sus ojos es lo mismo que para cualquier otra entrada de foco (por ejemplo, mirada con la cabeza o rayo de la mano). Esto proporciona la gran ventaja de una manera flexible de interactuar con los hologramas mediante la definición del tipo de foco principal en el perfil de puntero de entrada de MRTK en función de las necesidades del usuario, a la vez que deja el código intacto.</span><span class="sxs-lookup"><span data-stu-id="63401-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="63401-138">Esto permite cambiar entre la mirada con la cabeza o los ojos sin cambiar una línea de código ni reemplazar los rayos de las manos por el objetivo de los ojos para interacciones lejanas.</span><span class="sxs-lookup"><span data-stu-id="63401-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="63401-139">Centrarse en un holograma</span><span class="sxs-lookup"><span data-stu-id="63401-139">Focusing on a hologram</span></span>

<span data-ttu-id="63401-140">Para detectar cuándo se centra un holograma, use la interfaz _"IMixedRealityFocusHandler",_ que proporciona dos miembros de interfaz: _OnFocusEnter_ y _OnFocusExit._</span><span class="sxs-lookup"><span data-stu-id="63401-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="63401-141">Este es un ejemplo sencillo de [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) para cambiar el color de un holograma cuando se mira.</span><span class="sxs-lookup"><span data-stu-id="63401-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="63401-142">Selección de un holograma centrado</span><span class="sxs-lookup"><span data-stu-id="63401-142">Selecting a focused hologram</span></span>

<span data-ttu-id="63401-143">Para seleccionar un holograma centrado, use _PointerHandler_ para escuchar eventos de entrada y confirmar una selección.</span><span class="sxs-lookup"><span data-stu-id="63401-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="63401-144">Por ejemplo, agregar _IMixedRealityPointerHandler_ hará que reaccionen a una entrada de puntero simple.</span><span class="sxs-lookup"><span data-stu-id="63401-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="63401-145">La _interfaz IMixedRealityPointerHandler_ requiere la implementación de los tres miembros de interfaz siguientes: _OnPointerUp_, _OnPointerDown_ y _OnPointerClicked._</span><span class="sxs-lookup"><span data-stu-id="63401-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="63401-146">En el ejemplo siguiente, cambiamos el color de un holograma; para ello, lo miramos y nos acercamos o indicamos "seleccionar".</span><span class="sxs-lookup"><span data-stu-id="63401-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="63401-147">La acción necesaria para desencadenar el evento se define mediante la cual podemos establecer el tipo de en el Editor de Unity: de forma predeterminada, es la `eventData.MixedRealityInputAction == selectAction` `selectAction` acción "Seleccionar".</span><span class="sxs-lookup"><span data-stu-id="63401-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="63401-148">Los tipos de [MixedRealityInputActions](../input-actions.md) disponibles se pueden configurar en el perfil de MRTK mediante acciones de entrada de entrada del perfil de configuración de _MRTK._  ->    ->  </span><span class="sxs-lookup"><span data-stu-id="63401-148">The types of available [MixedRealityInputActions](../input-actions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="63401-149">BaseEyeFocusHandler específico de la mirada con los ojos</span><span class="sxs-lookup"><span data-stu-id="63401-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="63401-150">Dado que la mirada con los ojos puede ser muy diferente a otras entradas de  puntero, es posible que quiera asegurarse de reaccionar solo a la entrada de foco si es la mirada con los ojos y actualmente es el puntero de entrada principal.</span><span class="sxs-lookup"><span data-stu-id="63401-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="63401-151">Para este propósito, usaría el que es específico del seguimiento de [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) los ojos y que deriva de [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .</span><span class="sxs-lookup"><span data-stu-id="63401-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="63401-152">Como se mencionó anteriormente, solo se desencadenará si el objetivo de la mirada con los ojos es actualmente la entrada del puntero principal (es decir, no hay ningún rayo de mano activo).</span><span class="sxs-lookup"><span data-stu-id="63401-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="63401-153">Para obtener más información, [consulte Compatibilidad con la mirada con los ojos y los gestos de la mano.](eye-tracking-eyes-and-hands.md)</span><span class="sxs-lookup"><span data-stu-id="63401-153">For more information, see [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).</span></span>

<span data-ttu-id="63401-154">Este es un ejemplo de `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span><span class="sxs-lookup"><span data-stu-id="63401-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="63401-155">En esta demostración, hay dos hologramas 3D que se activarán en función de la parte del objeto que se examina: si el usuario mira el lado izquierdo del holograma, esa parte se moverá lentamente hacia la parte frontal orientada al usuario.</span><span class="sxs-lookup"><span data-stu-id="63401-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="63401-156">Si se mira el lado derecho, esa parte se moverá lentamente al frente.</span><span class="sxs-lookup"><span data-stu-id="63401-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="63401-157">Se trata de un comportamiento que es posible que no quiera tener activo en todo momento y también algo que es posible que no quiera desencadenar accidentalmente mediante un rayo de mano o la mirada con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="63401-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="63401-158">Si se [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) adjunta, un Objeto GameObject gira mientras se mira.</span><span class="sxs-lookup"><span data-stu-id="63401-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

<span data-ttu-id="63401-159">Consulte la documentación de la API para obtener una lista completa de los eventos disponibles de [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :</span><span class="sxs-lookup"><span data-stu-id="63401-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="63401-160">**OnEyeFocusStart:** Se desencadena una vez que el rayo de mirada *con los ojos* comienza a formar una intersección con el colisionador de este objetivo.</span><span class="sxs-lookup"><span data-stu-id="63401-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="63401-161">**OnEyeFocusFocus:** Se *desencadena mientras* el rayo de mirada con los ojos forma una intersección con el colisionador de este objetivo.</span><span class="sxs-lookup"><span data-stu-id="63401-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="63401-162">**OnEyeFocusStop:** Se desencadena una vez que el rayo de *mirada con los ojos deja* de formar intersección con el colisionador de este objetivo.</span><span class="sxs-lookup"><span data-stu-id="63401-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="63401-163">**OnEyeFocusDwell:** Se desencadena una vez que el rayo de mirada con los ojos se ha intersecado con el colisionador de este objetivo durante un período de tiempo especificado.</span><span class="sxs-lookup"><span data-stu-id="63401-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="63401-164">2. EyeTrackingTarget específico de la mirada con los ojos independiente</span><span class="sxs-lookup"><span data-stu-id="63401-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="63401-165">Por último, le proporcionamos una solución que le permite tratar la entrada basada en los ojos completamente independiente de otros punteros de foco a través del [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span><span class="sxs-lookup"><span data-stu-id="63401-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="63401-166">Esto tiene tres _ventajas:_</span><span class="sxs-lookup"><span data-stu-id="63401-166">This has three _advantages_:</span></span>

- <span data-ttu-id="63401-167">Puede asegurarse de que el holograma solo reacciona a la mirada con los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="63401-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="63401-168">Esto es independiente de la entrada principal activa actualmente.</span><span class="sxs-lookup"><span data-stu-id="63401-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="63401-169">Por lo tanto, puede procesar varias entradas a la vez, por ejemplo, combinando el objetivo rápido de los ojos con los gestos de la mano.</span><span class="sxs-lookup"><span data-stu-id="63401-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="63401-170">Ya se han configurado varios eventos de Unity para que sea rápido y cómodo controlar y reutilizar los comportamientos existentes desde el Editor de Unity o a través del código.</span><span class="sxs-lookup"><span data-stu-id="63401-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="63401-171">También hay algunas _desventajas:_</span><span class="sxs-lookup"><span data-stu-id="63401-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="63401-172">Más esfuerzo para controlar entradas independientes individualmente.</span><span class="sxs-lookup"><span data-stu-id="63401-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="63401-173">Sin degradación elegante: solo admite la orientación con los ojos.</span><span class="sxs-lookup"><span data-stu-id="63401-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="63401-174">Si el seguimiento de los ojos no funciona, necesita alguna reserva adicional.</span><span class="sxs-lookup"><span data-stu-id="63401-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="63401-175">De forma similar a _BaseFocusHandler,_ _EyeTrackingTarget_ viene listo con varios eventos de Unity específicos de la mirada con los ojos que puede escuchar cómodamente a través del Editor de Unity (vea el ejemplo siguiente) o mediante _AddListener()_ en el código:</span><span class="sxs-lookup"><span data-stu-id="63401-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="63401-176">OnLookAtStart()</span><span class="sxs-lookup"><span data-stu-id="63401-176">OnLookAtStart()</span></span>
- <span data-ttu-id="63401-177">WhileLookingAtTarget()</span><span class="sxs-lookup"><span data-stu-id="63401-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="63401-178">OnLookAway()</span><span class="sxs-lookup"><span data-stu-id="63401-178">OnLookAway()</span></span>
- <span data-ttu-id="63401-179">OnDwell()</span><span class="sxs-lookup"><span data-stu-id="63401-179">OnDwell()</span></span>
- <span data-ttu-id="63401-180">OnSelected()</span><span class="sxs-lookup"><span data-stu-id="63401-180">OnSelected()</span></span>

<span data-ttu-id="63401-181">A continuación, le llevamos a través de algunos ejemplos sobre cómo usar _EyeTrackingTarget._</span><span class="sxs-lookup"><span data-stu-id="63401-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="63401-182">Ejemplo #1: notificaciones inteligentes compatibles con los ojos</span><span class="sxs-lookup"><span data-stu-id="63401-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="63401-183">En `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), puede encontrar un ejemplo de _"notificaciones inteligentes_ de notificación" que reaccionan a la mirada con los ojos.</span><span class="sxs-lookup"><span data-stu-id="63401-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="63401-184">Se trata de cuadros de texto 3D que se pueden colocar en la escena y que se ampliarán sin problemas y se volverán hacia el usuario cuando se les mira para facilitar la legibilidad.</span><span class="sxs-lookup"><span data-stu-id="63401-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="63401-185">Mientras el usuario lee la notificación, la información se muestra clara y clara.</span><span class="sxs-lookup"><span data-stu-id="63401-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="63401-186">Después de leerla y alejarse de la notificación, la notificación se descartará automáticamente y se atenuará. Para lograr todo esto, hay algunos scripts de comportamiento genéricos que no son específicos del seguimiento ocular, como:</span><span class="sxs-lookup"><span data-stu-id="63401-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="63401-187">La ventaja de este enfoque es que varios eventos pueden reutilizar los mismos scripts.</span><span class="sxs-lookup"><span data-stu-id="63401-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="63401-188">Por ejemplo, un holograma puede empezar a enfrentarse al usuario en función de los comandos de voz o después de presionar un botón virtual.</span><span class="sxs-lookup"><span data-stu-id="63401-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="63401-189">Para desencadenar estos eventos, simplemente puede hacer referencia a los métodos que se deben ejecutar en el [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script que está asociado a GameObject.</span><span class="sxs-lookup"><span data-stu-id="63401-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="63401-190">Para el ejemplo de las _"notificaciones inteligentes de notificación",_ ocurre lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="63401-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="63401-191">**OnLookAtStart():** la notificación comienza a...</span><span class="sxs-lookup"><span data-stu-id="63401-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="63401-192">*FaceUser.Engage:* ... se dirige al usuario.</span><span class="sxs-lookup"><span data-stu-id="63401-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="63401-193">*ChangeSize.Engage:* ... aumentar el tamaño _(hasta una escala máxima especificada)._</span><span class="sxs-lookup"><span data-stu-id="63401-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="63401-194">*BlendOut.Engage:* ... comienza a combinarse en más _(después de estar en un estado de inactividad más sutil)._</span><span class="sxs-lookup"><span data-stu-id="63401-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="63401-195">**OnDwell():** informa al script _BlendOut_ de que la notificación se ha visto lo suficiente.</span><span class="sxs-lookup"><span data-stu-id="63401-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="63401-196">**OnLookAway():** la notificación comienza a...</span><span class="sxs-lookup"><span data-stu-id="63401-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="63401-197">*FaceUser.Disengage:* ... volver a su orientación original.</span><span class="sxs-lookup"><span data-stu-id="63401-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="63401-198">*ChangeSize.Disengage:* ... reducir a su tamaño original.</span><span class="sxs-lookup"><span data-stu-id="63401-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="63401-199">*BlendOut.Disengage:* ... comienza a combinarse: si _se desencadenó OnDwell(),_ se mezcla completamente y se destruye; de lo contrario, vuelve a su estado de inactividad.</span><span class="sxs-lookup"><span data-stu-id="63401-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="63401-200">**Consideración de diseño:** La clave de una experiencia divertida aquí es ajustar cuidadosamente la velocidad de cualquiera de estos comportamientos para evitar causar molestias al reaccionar a la mirada del usuario demasiado rápido todo el tiempo.</span><span class="sxs-lookup"><span data-stu-id="63401-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="63401-201">De lo contrario, esto puede parecer muy abrumador.</span><span class="sxs-lookup"><span data-stu-id="63401-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="63401-202">Ejemplo #2: la gema holográfica gira lentamente al mirarla</span><span class="sxs-lookup"><span data-stu-id="63401-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="63401-203">Al igual que en el ejemplo #1, podemos crear fácilmente un comentario de mantener el puntero para nuestras gemas holográficas en la escena (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) que girará lentamente en una dirección constante y a una velocidad constante (a diferencia del ejemplo de rotación anterior) cuando se `EyeTrackingDemo-02-TargetSelection` mira.</span><span class="sxs-lookup"><span data-stu-id="63401-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="63401-204">Todo lo que necesita es desencadenar la rotación de la gema holográfica desde el evento _WhileLookingAtTarget()_ de _EyeTrackingTarget._</span><span class="sxs-lookup"><span data-stu-id="63401-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="63401-205">A continuación se incluyen algunos detalles más:</span><span class="sxs-lookup"><span data-stu-id="63401-205">Here are a few more details:</span></span>

1. <span data-ttu-id="63401-206">Cree un script genérico que incluya una función pública para rotar el GameObject al que está asociado.</span><span class="sxs-lookup"><span data-stu-id="63401-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="63401-207">A continuación se muestra un ejemplo de _RotateWithConstSpeedDir.cs,_ donde podemos ajustar la dirección y la velocidad de rotación desde el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="63401-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. <span data-ttu-id="63401-208">Agregue el script al GameObject de destino y haga referencia a la [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) _función RotateTarget()_ en el desencadenador UnityEvent, como se muestra en la captura de pantalla siguiente:</span><span class="sxs-lookup"><span data-stu-id="63401-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![Ejemplo de EyeTrackingTarget](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="63401-210">Ejemplo #3: Selección de destino compatible  con la mirada con los ojos multimodal</span><span class="sxs-lookup"><span data-stu-id="63401-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="63401-211">En el ejemplo anterior, hemos mostrado lo fácil que es detectar si se busca un destino y cómo desencadenar una reacción a eso.</span><span class="sxs-lookup"><span data-stu-id="63401-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="63401-212">A continuación, vamos a hacer que las gemas se desenlomen con el _evento OnSelected()_ de [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) .</span><span class="sxs-lookup"><span data-stu-id="63401-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="63401-213">La parte interesante es *cómo se* desencadena la selección.</span><span class="sxs-lookup"><span data-stu-id="63401-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="63401-214">permite [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) asignar rápidamente distintas formas de invocar una selección:</span><span class="sxs-lookup"><span data-stu-id="63401-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="63401-215">_Gesto de acercar:_ al establecer la opción "Seleccionar acción" en "Seleccionar", se usa el gesto de mano predeterminado para desencadenar la selección.</span><span class="sxs-lookup"><span data-stu-id="63401-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="63401-216">Esto significa que el usuario puede simplemente elevar la mano y acercar el dedo índice y el dedo para confirmar la selección.</span><span class="sxs-lookup"><span data-stu-id="63401-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="63401-217">Diga _"Seleccionar":_ use el comando de voz _predeterminado "Seleccionar"_ para seleccionar un holograma.</span><span class="sxs-lookup"><span data-stu-id="63401-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="63401-218">Diga _"Explode"_ o _"Pop":_ para usar comandos de voz personalizados, debe seguir dos pasos:</span><span class="sxs-lookup"><span data-stu-id="63401-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="63401-219">Configuración de una acción personalizada como _"DestroyTarget"_</span><span class="sxs-lookup"><span data-stu-id="63401-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="63401-220">Vaya a _MRTK -> Input -> Input Actions_</span><span class="sxs-lookup"><span data-stu-id="63401-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="63401-221">Haga clic en "Agregar una nueva acción".</span><span class="sxs-lookup"><span data-stu-id="63401-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="63401-222">Configure los comandos de voz que desencadenan esta acción, como _"Explode"_ o _"Pop"._</span><span class="sxs-lookup"><span data-stu-id="63401-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="63401-223">Vaya a _MRTK -> Input -> Speech_</span><span class="sxs-lookup"><span data-stu-id="63401-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="63401-224">Haga clic en "Agregar un nuevo comando de voz".</span><span class="sxs-lookup"><span data-stu-id="63401-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="63401-225">Asociación de la acción que acaba de crear</span><span class="sxs-lookup"><span data-stu-id="63401-225">Associate the action you just created</span></span>
            - <span data-ttu-id="63401-226">Asignación de _un código de_ clave para permitir desencadenar la acción mediante una pulsación de botón</span><span class="sxs-lookup"><span data-stu-id="63401-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![Ejemplo eyeTrackingTarget de comandos de voz](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="63401-228">Cuando se selecciona una gema, se expande, se hace un sonido y desaparece.</span><span class="sxs-lookup"><span data-stu-id="63401-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="63401-229">Esto se controla mediante el [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span><span class="sxs-lookup"><span data-stu-id="63401-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="63401-230">Tiene dos opciones:</span><span class="sxs-lookup"><span data-stu-id="63401-230">You have two options:</span></span>

- <span data-ttu-id="63401-231">**En el Editor de Unity:** Simplemente puede vincular el script que está asociado a cada una de nuestras plantillas de gema al evento De Unity OnSelected() en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="63401-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="63401-232">**En el código:** Si no desea arrastrar y colocar GameObjects, también puede simplemente agregar un agente de escucha de eventos directamente al script.</span><span class="sxs-lookup"><span data-stu-id="63401-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="63401-233">Este es un ejemplo de cómo lo hicimos en el [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span><span class="sxs-lookup"><span data-stu-id="63401-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="63401-234">Ejemplo #4: Uso de los rayos de las manos y la entrada de mirada con los ojos juntos</span><span class="sxs-lookup"><span data-stu-id="63401-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="63401-235">Los rayos de las manos tienen prioridad sobre el objetivo de la mirada con la cabeza y los ojos.</span><span class="sxs-lookup"><span data-stu-id="63401-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="63401-236">Esto significa que, si se habilitan los rayos de mano, en el momento en que las manos se ven, el rayo de la mano actuará como puntero principal.</span><span class="sxs-lookup"><span data-stu-id="63401-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="63401-237">Sin embargo, puede haber situaciones en las que quiera usar rayos de mano mientras sigue detectando si un usuario está mirando un determinado holograma.</span><span class="sxs-lookup"><span data-stu-id="63401-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="63401-238">Fácil.</span><span class="sxs-lookup"><span data-stu-id="63401-238">Easy!</span></span> <span data-ttu-id="63401-239">Básicamente, necesita dos pasos:</span><span class="sxs-lookup"><span data-stu-id="63401-239">Essentially you require two steps:</span></span>

<span data-ttu-id="63401-240">**1. Habilitar el** rayo de mano: para habilitar el rayo de mano, vaya a _Mixed Reality Toolkit -> Input -> Pointers_.</span><span class="sxs-lookup"><span data-stu-id="63401-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="63401-241">En _EyeTrackingDemo-00-RootScene,_ donde el kit de herramientas de Mixed Reality se configura una vez para todas las escenas de demostración de seguimiento de los ojos, debería ver _EyeTrackingDemoPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="63401-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="63401-242">Puede crear un nuevo perfil de _entrada desde_ cero o adaptar el actual:</span><span class="sxs-lookup"><span data-stu-id="63401-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="63401-243">**Desde cero:** En la _pestaña Punteros,_ seleccione _DefaultMixedRealityInputPointerProfile_ en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="63401-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="63401-244">Este es el perfil de puntero predeterminado que ya tiene habilitado el rayo de mano.</span><span class="sxs-lookup"><span data-stu-id="63401-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="63401-245">Para cambiar el cursor predeterminado (un punto blanco opaco), basta con clonar el perfil y crear su propio perfil de puntero personalizado.</span><span class="sxs-lookup"><span data-stu-id="63401-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="63401-246">A continuación, reemplace _DefaultCursor_ por _EyeGazeCursor en_ _Gaze Cursor Prefab_.</span><span class="sxs-lookup"><span data-stu-id="63401-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="63401-247">**En función del _elemento EyeTrackingDemoPointerProfile_ existente:** haga doble clic en _EyeTrackingDemoPointerProfile_ y agregue la siguiente entrada en _Opciones de puntero_:</span><span class="sxs-lookup"><span data-stu-id="63401-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="63401-248">**Tipo de controlador:** "Mano articulada", "Windows Mixed Reality"</span><span class="sxs-lookup"><span data-stu-id="63401-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="63401-249">**Entrega:** Cualquier</span><span class="sxs-lookup"><span data-stu-id="63401-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="63401-250">**Prefab de puntero:** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="63401-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="63401-251">**2. Detectar que se** busca un holograma: use el script para habilitar la detección de que un holograma se ha visto como se [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) describió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="63401-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="63401-252">También puede echar un vistazo al script de ejemplo para obtener inspiración, ya que muestra un holograma después de la mirada con los ojos (por ejemplo, un cursor) independientemente de si los rayos de las manos están habilitados `FollowEyeGaze` o no.</span><span class="sxs-lookup"><span data-stu-id="63401-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="63401-253">Ahora, al iniciar las escenas de demostración de seguimiento ocular, debería ver un rayo procedente de las manos.</span><span class="sxs-lookup"><span data-stu-id="63401-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="63401-254">Por ejemplo, en la demostración de selección de destino de seguimiento de los ojos, el círculo semitransparente sigue con la mirada con los ojos y las gemas responden a si se miran o no, mientras que los botones del menú de la escena superior usan el puntero de entrada principal (las manos) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="63401-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="63401-255">Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit).</span><span class="sxs-lookup"><span data-stu-id="63401-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
