---
title: Manipulador de objetos
description: Uso del manipulador de objetos en MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, manipulación de objetos,
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176652"
---
# <a name="object-manipulator"></a><span data-ttu-id="75db8-104">Manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="75db8-104">Object manipulator</span></span>

![Manipulador de objetos](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="75db8-106">*ObjectManipulator es el* nuevo componente para el comportamiento de manipulación, que se encontró anteriormente en *ManipulationHandler*.</span><span class="sxs-lookup"><span data-stu-id="75db8-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="75db8-107">El manipulador de objetos realiza una serie de mejoras y simplificaciones.</span><span class="sxs-lookup"><span data-stu-id="75db8-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="75db8-108">Este componente es un reemplazo del controlador de manipulación, que estará en desuso.</span><span class="sxs-lookup"><span data-stu-id="75db8-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="75db8-109">El script *ObjectManipulator* hace que un objeto sea móvil, escalable y rotable con una o dos manos.</span><span class="sxs-lookup"><span data-stu-id="75db8-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="75db8-110">El manipulador de objetos se puede configurar para controlar cómo responderá el objeto a varias entradas.</span><span class="sxs-lookup"><span data-stu-id="75db8-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="75db8-111">El script debe funcionar con la mayoría de las formas de interacción HoloLens 2, como una mano articulada, un HoloLens 2 de mano, una mirada y gestos de HoloLens y una entrada de controlador de movimiento de casco envolvente.</span><span class="sxs-lookup"><span data-stu-id="75db8-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="75db8-112">Uso del manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="75db8-112">How to use the object manipulator</span></span>

<span data-ttu-id="75db8-113">Para usar el manipulador de objetos, agregue primero el `ObjectManipulator` componente de script a un Objeto GameObject.</span><span class="sxs-lookup"><span data-stu-id="75db8-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="75db8-114">Asegúrese de agregar también un colisionador al objeto, que coincida con sus límites que se pueden agarrar.</span><span class="sxs-lookup"><span data-stu-id="75db8-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="75db8-115">Para que el objeto responda a una entrada de mano casi articulada, agregue también `NearInteractionGrabbable` el script.</span><span class="sxs-lookup"><span data-stu-id="75db8-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="75db8-116">El comportamiento físico se puede habilitar para el manipulador de objetos agregando un componente rigidbody al objeto.</span><span class="sxs-lookup"><span data-stu-id="75db8-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="75db8-117">El comportamiento físico habilitado mediante la adición de este componente se describe con más detalle en [*Física y colisiones.*](#physics-and-collisions)</span><span class="sxs-lookup"><span data-stu-id="75db8-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="75db8-118">Además de esto, la manipulación se puede restringir agregando componentes de [restricción de manipulación](constraint-manager.md#transform-constraints) al objeto .</span><span class="sxs-lookup"><span data-stu-id="75db8-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="75db8-119">Se trata de componentes especiales que funcionan con la manipulación y cambian el comportamiento de la manipulación de alguna manera.</span><span class="sxs-lookup"><span data-stu-id="75db8-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Uso del controlador de manipulación en el editor de Unity](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="75db8-121">Propiedades y campos del inspector</span><span class="sxs-lookup"><span data-stu-id="75db8-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="75db8-122">Propiedades generales</span><span class="sxs-lookup"><span data-stu-id="75db8-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="75db8-123">Transformación de host</span><span class="sxs-lookup"><span data-stu-id="75db8-123">Host transform</span></span>

<span data-ttu-id="75db8-124">Transformación de objeto que se va a manipular.</span><span class="sxs-lookup"><span data-stu-id="75db8-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="75db8-125">El valor predeterminado es el objeto del componente.</span><span class="sxs-lookup"><span data-stu-id="75db8-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="75db8-126">Tipo de manipulación</span><span class="sxs-lookup"><span data-stu-id="75db8-126">Manipulation type</span></span>

<span data-ttu-id="75db8-127">Especifica si el objeto se puede manipular con una o dos manos.</span><span class="sxs-lookup"><span data-stu-id="75db8-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="75db8-128">Dado que esta propiedad es una marca, se pueden seleccionar ambas opciones.</span><span class="sxs-lookup"><span data-stu-id="75db8-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="75db8-129">*Con una mano:* habilita la manipulación con una mano si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="75db8-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="75db8-130">*Dos manos:* habilita la manipulación con dos manos si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="75db8-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="75db8-131">Permitir manipulación lejana</span><span class="sxs-lookup"><span data-stu-id="75db8-131">Allow far manipulation</span></span>

<span data-ttu-id="75db8-132">Especifica si se puede realizar la manipulación mediante la interacción lejana con punteros.</span><span class="sxs-lookup"><span data-stu-id="75db8-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="75db8-133">Propiedades de manipulación con una mano</span><span class="sxs-lookup"><span data-stu-id="75db8-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="75db8-134">Modo de rotación de una mano cerca</span><span class="sxs-lookup"><span data-stu-id="75db8-134">One hand rotation mode near</span></span>

<span data-ttu-id="75db8-135">Especifica cómo se comportará el objeto cuando se esté capturando con una mano cerca.</span><span class="sxs-lookup"><span data-stu-id="75db8-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="75db8-136">Estas opciones solo funcionan para las manos articuladas.</span><span class="sxs-lookup"><span data-stu-id="75db8-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="75db8-137">*Girar sobre el centro de* objetos: el objeto gira mediante la rotación de la mano, pero sobre el punto central del objeto.</span><span class="sxs-lookup"><span data-stu-id="75db8-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="75db8-138">Parecerá que el objeto se mueve menos a medida que gira, pero puede haber una sensación de desconexión entre la mano y el objeto.</span><span class="sxs-lookup"><span data-stu-id="75db8-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="75db8-139">Más útil para la interacción lejana.</span><span class="sxs-lookup"><span data-stu-id="75db8-139">More useful for far interaction.</span></span>
- <span data-ttu-id="75db8-140">*Girar sobre el punto de agarre:* gira el objeto con la mano sobre el punto de agarre entre el dedo índice y el dedo índice.</span><span class="sxs-lookup"><span data-stu-id="75db8-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="75db8-141">Debería ser como si el objeto se hubiera mantenido con la mano.</span><span class="sxs-lookup"><span data-stu-id="75db8-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="75db8-142">Modo de rotación de una mano lejos</span><span class="sxs-lookup"><span data-stu-id="75db8-142">One hand rotation mode far</span></span>

<span data-ttu-id="75db8-143">Especifica cómo se comportará el objeto cuando se esté tomando con una mano a distancia.</span><span class="sxs-lookup"><span data-stu-id="75db8-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="75db8-144">Estas opciones solo funcionan para las manos articuladas.</span><span class="sxs-lookup"><span data-stu-id="75db8-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="75db8-145">*Girar sobre el centro de* objetos: gira el objeto mediante la rotación de la mano, pero sobre el punto central del objeto.</span><span class="sxs-lookup"><span data-stu-id="75db8-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="75db8-146">Resulta útil para inspeccionar a una distancia sin que el centro de objetos se mueva a medida que el objeto gira.</span><span class="sxs-lookup"><span data-stu-id="75db8-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="75db8-147">*Girar sobre el punto de agarre:* gira el objeto mediante la rotación de la mano, pero sobre el punto de impacto del rayo del puntero.</span><span class="sxs-lookup"><span data-stu-id="75db8-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="75db8-148">Útil para la inspección.</span><span class="sxs-lookup"><span data-stu-id="75db8-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="75db8-149">Dos propiedades de manipulación con manos</span><span class="sxs-lookup"><span data-stu-id="75db8-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="75db8-150">Tipo de manipulación con dos manos</span><span class="sxs-lookup"><span data-stu-id="75db8-150">Two handed manipulation type</span></span>

<span data-ttu-id="75db8-151">Especifica cómo la manipulación de dos manos puede transformar un objeto.</span><span class="sxs-lookup"><span data-stu-id="75db8-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="75db8-152">Dado que esta propiedad es una marca, se puede seleccionar cualquier número de opciones.</span><span class="sxs-lookup"><span data-stu-id="75db8-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="75db8-153">*Mover:* se permite el movimiento si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="75db8-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="75db8-154">*Escala:* se permite el escalado si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="75db8-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="75db8-155">*Girar:* se permite la rotación si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="75db8-155">*Rotate*: Rotation is allowed if selected.</span></span>

![Controlador de manipulación](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="75db8-157">Restricciones</span><span class="sxs-lookup"><span data-stu-id="75db8-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="75db8-158">Habilitar restricciones</span><span class="sxs-lookup"><span data-stu-id="75db8-158">Enable constraints</span></span>

<span data-ttu-id="75db8-159">Esta configuración habilitará el administrador de [restricciones vinculadas.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="75db8-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="75db8-160">Los cambios de transformación se procesarán mediante restricciones registradas en el administrador [de restricciones seleccionado.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="75db8-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="75db8-161">Administrador de restricciones</span><span class="sxs-lookup"><span data-stu-id="75db8-161">Constraint manager</span></span>

<span data-ttu-id="75db8-162">La lista desplegable permite seleccionar cualquiera de los administradores de [restricciones asociados.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="75db8-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="75db8-163">El manipulador de objetos garantiza que haya un administrador [de restricciones](constraint-manager.md) asociado en todo momento.</span><span class="sxs-lookup"><span data-stu-id="75db8-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="75db8-164">Tenga en cuenta que varios componentes del mismo tipo se mostrarán con el mismo nombre en Unity.</span><span class="sxs-lookup"><span data-stu-id="75db8-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="75db8-165">Para facilitar la distinción entre varios administradores de restricciones en el mismo objeto, las opciones disponibles mostrarán una sugerencia sobre la configuración del administrador de restricciones seleccionado (selección manual o automática de restricciones).</span><span class="sxs-lookup"><span data-stu-id="75db8-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="75db8-166">Ir al componente</span><span class="sxs-lookup"><span data-stu-id="75db8-166">Go to component</span></span>

<span data-ttu-id="75db8-167">La selección del administrador de restricciones incluye un *botón Ir al* componente.</span><span class="sxs-lookup"><span data-stu-id="75db8-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="75db8-168">Este botón hará que el inspector se desplace al componente seleccionado para que se pueda configurar.</span><span class="sxs-lookup"><span data-stu-id="75db8-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="75db8-169">Física</span><span class="sxs-lookup"><span data-stu-id="75db8-169">Physics</span></span>

<span data-ttu-id="75db8-170">Configuración en esta sección solo aparecen cuando el objeto tiene un componente RigidBody.</span><span class="sxs-lookup"><span data-stu-id="75db8-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="75db8-171">Comportamiento de la versión</span><span class="sxs-lookup"><span data-stu-id="75db8-171">Release behavior</span></span>

<span data-ttu-id="75db8-172">Especifique las propiedades físicas que un objeto manipulado debe conservar al liberarse.</span><span class="sxs-lookup"><span data-stu-id="75db8-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="75db8-173">Dado que esta propiedad es una marca, se pueden seleccionar ambas opciones.</span><span class="sxs-lookup"><span data-stu-id="75db8-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="75db8-174">*Mantener velocidad:* cuando se libera el objeto, si se selecciona esta opción, mantendrá su velocidad lineal.</span><span class="sxs-lookup"><span data-stu-id="75db8-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="75db8-175">*Mantener Angular velocidad:* cuando se libera el objeto, si se selecciona esta opción, mantendrá su velocidad angular.</span><span class="sxs-lookup"><span data-stu-id="75db8-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="75db8-176">Uso de fuerzas para la manipulación próxima</span><span class="sxs-lookup"><span data-stu-id="75db8-176">Use forces for near manipulation</span></span>

<span data-ttu-id="75db8-177">Si se usan fuerzas físicas para mover el objeto al realizar manipulaciones cercanas.</span><span class="sxs-lookup"><span data-stu-id="75db8-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="75db8-178">Si se establece en *false,* el objeto se verá más conectado directamente a la mano de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="75db8-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="75db8-179">Si se establece en *true,* se respetará la masa y la inercia del objeto, pero puede parecer que el objeto está conectado a través de un spring.</span><span class="sxs-lookup"><span data-stu-id="75db8-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="75db8-180">El valor predeterminado es *false*.</span><span class="sxs-lookup"><span data-stu-id="75db8-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="75db8-181">Suavizado</span><span class="sxs-lookup"><span data-stu-id="75db8-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="75db8-182">Suavizado lejos</span><span class="sxs-lookup"><span data-stu-id="75db8-182">Smoothing far</span></span>

<span data-ttu-id="75db8-183">Si el suavizado independiente de velocidad de fotogramas está habilitado para interacciones lejanas.</span><span class="sxs-lookup"><span data-stu-id="75db8-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="75db8-184">El suavizado lejano está habilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="75db8-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="75db8-185">Suavizado cerca de</span><span class="sxs-lookup"><span data-stu-id="75db8-185">Smoothing near</span></span>

<span data-ttu-id="75db8-186">Si el suavizado independiente de velocidad de fotogramas está habilitado para interacciones cercanas.</span><span class="sxs-lookup"><span data-stu-id="75db8-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="75db8-187">El suavizado casi está deshabilitado de forma predeterminada porque el efecto se puede percibir como "desconectado" de la mano.</span><span class="sxs-lookup"><span data-stu-id="75db8-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="75db8-188">Suavizado activo</span><span class="sxs-lookup"><span data-stu-id="75db8-188">Smoothing active</span></span>

<span data-ttu-id="75db8-189">Obsoleto y se quitará en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="75db8-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="75db8-190">Las aplicaciones deben usar SmoothingFar, SmoothingNear o una combinación de los dos.</span><span class="sxs-lookup"><span data-stu-id="75db8-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="75db8-191">Mover el tiempo de lerp</span><span class="sxs-lookup"><span data-stu-id="75db8-191">Move lerp time</span></span>

<span data-ttu-id="75db8-192">Cantidad de suavizado que se aplicará al movimiento.</span><span class="sxs-lookup"><span data-stu-id="75db8-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="75db8-193">Suavizado de 0 significa que no hay suavizado.</span><span class="sxs-lookup"><span data-stu-id="75db8-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="75db8-194">El valor máximo significa que no hay ningún cambio en el valor.</span><span class="sxs-lookup"><span data-stu-id="75db8-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="75db8-195">Rotación del tiempo de lerp</span><span class="sxs-lookup"><span data-stu-id="75db8-195">Rotate lerp time</span></span>

<span data-ttu-id="75db8-196">Cantidad de suavizado que se aplicará a la rotación.</span><span class="sxs-lookup"><span data-stu-id="75db8-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="75db8-197">Suavizado de 0 significa que no hay suavizado.</span><span class="sxs-lookup"><span data-stu-id="75db8-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="75db8-198">El valor máximo significa que no hay ningún cambio en el valor.</span><span class="sxs-lookup"><span data-stu-id="75db8-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="75db8-199">Escalado del tiempo de lerp</span><span class="sxs-lookup"><span data-stu-id="75db8-199">Scale lerp time</span></span>

<span data-ttu-id="75db8-200">Cantidad de suavizado que se aplicará a la escala.</span><span class="sxs-lookup"><span data-stu-id="75db8-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="75db8-201">Suavizado de 0 significa que no hay suavizado.</span><span class="sxs-lookup"><span data-stu-id="75db8-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="75db8-202">El valor máximo significa que no hay ningún cambio en el valor.</span><span class="sxs-lookup"><span data-stu-id="75db8-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="75db8-203">Eventos de manipulación</span><span class="sxs-lookup"><span data-stu-id="75db8-203">Manipulation events</span></span>

<span data-ttu-id="75db8-204">El controlador de manipulación proporciona los siguientes eventos:</span><span class="sxs-lookup"><span data-stu-id="75db8-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="75db8-205">*OnManipulationStarted:* se desencadena cuando se inicia la manipulación.</span><span class="sxs-lookup"><span data-stu-id="75db8-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="75db8-206">*OnManipulationEnded:* se ejecuta cuando finaliza la manipulación.</span><span class="sxs-lookup"><span data-stu-id="75db8-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="75db8-207">*OnHoverStarted:* se activa cuando una mano o un controlador mantiene el puntero sobre el manipulable, cerca o lejos.</span><span class="sxs-lookup"><span data-stu-id="75db8-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="75db8-208">*OnHoverEnded:* se activa cuando una mano o un controlador mantiene el puntero sobre el manipulable, cerca o lejos.</span><span class="sxs-lookup"><span data-stu-id="75db8-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="75db8-209">El orden de la manipulación de la manipulación del evento es:</span><span class="sxs-lookup"><span data-stu-id="75db8-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="75db8-210">*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="75db8-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="75db8-211">Si no hay ninguna manipulación, seguirá teniendo eventos de mantener el puntero con el siguiente orden de incendio:</span><span class="sxs-lookup"><span data-stu-id="75db8-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="75db8-212">*OnHoverStarted*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="75db8-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="75db8-213">Física y colisiones</span><span class="sxs-lookup"><span data-stu-id="75db8-213">Physics and collisions</span></span>

<span data-ttu-id="75db8-214">El comportamiento físico se puede habilitar agregando un componente rigidbody al mismo objeto que un manipulador de objetos.</span><span class="sxs-lookup"><span data-stu-id="75db8-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="75db8-215">Esto no solo habilita la configuración del comportamiento [de la versión](#release-behavior) anterior, sino que también permite colisiones.</span><span class="sxs-lookup"><span data-stu-id="75db8-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="75db8-216">Sin un componente rigidbody, las colisiones no se comportan correctamente durante la manipulación:</span><span class="sxs-lookup"><span data-stu-id="75db8-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="75db8-217">Las colisiones entre un objeto manipulado y un colisionador estático (es decir, un objeto con un colisionador pero no un elemento rígido) no funcionan, el objeto manipulado pasa directamente a través del colisionador estático sin que se ve afectado.</span><span class="sxs-lookup"><span data-stu-id="75db8-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="75db8-218">Colisiones entre un objeto manipulado y un rígido (es decir,</span><span class="sxs-lookup"><span data-stu-id="75db8-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="75db8-219">Un objeto con un colisionador y un elemento rigidbody) hace que el elemento rigidbody tenga una respuesta de colisión, pero la respuesta es rápida y no natural.</span><span class="sxs-lookup"><span data-stu-id="75db8-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="75db8-220">Tampoco hay ninguna respuesta de colisión en el objeto manipulado.</span><span class="sxs-lookup"><span data-stu-id="75db8-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="75db8-221">Cuando se agrega un rigidbody, las colisiones deben funcionar correctamente.</span><span class="sxs-lookup"><span data-stu-id="75db8-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="75db8-222">Sin rigidbody</span><span class="sxs-lookup"><span data-stu-id="75db8-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="75db8-223">Con rigidbody</span><span class="sxs-lookup"><span data-stu-id="75db8-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="75db8-224">Elásticos (experimentales)</span><span class="sxs-lookup"><span data-stu-id="75db8-224">Elastics (Experimental)</span></span>

<span data-ttu-id="75db8-225">Los elásticos se pueden usar al manipular objetos a través del manipulador de objetos.</span><span class="sxs-lookup"><span data-stu-id="75db8-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="75db8-226">Tenga en cuenta que [el sistema elástico](../experimental/elastic-system.md) sigue en estado experimental.</span><span class="sxs-lookup"><span data-stu-id="75db8-226">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="75db8-227">Para habilitar los elásticos, vincule un componente existente del administrador de elásticos o cree y vincule un nuevo administrador de elásticos mediante el `Add Elastics Manager` botón .</span><span class="sxs-lookup"><span data-stu-id="75db8-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="75db8-228">Consulte también</span><span class="sxs-lookup"><span data-stu-id="75db8-228">See also</span></span>

- [<span data-ttu-id="75db8-229">Control Bounds</span><span class="sxs-lookup"><span data-stu-id="75db8-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="75db8-230">Administrador de restricciones</span><span class="sxs-lookup"><span data-stu-id="75db8-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="75db8-231">El plazo de migración</span><span class="sxs-lookup"><span data-stu-id="75db8-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="75db8-232">Sistema elástico (experimental)</span><span class="sxs-lookup"><span data-stu-id="75db8-232">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
