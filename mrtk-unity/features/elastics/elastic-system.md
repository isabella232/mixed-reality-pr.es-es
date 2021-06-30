---
title: Sistema elástico
description: Documentación relacionada con la simulación de elásticos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, ElasticsSystem,
ms.openlocfilehash: 1f90864ee6d3b6756b863de600ade8423a44cacc
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121243"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="16c32-104">Sistema elástico (experimental)</span><span class="sxs-lookup"><span data-stu-id="16c32-104">Elastic system (experimental)</span></span>

![Sistema elástico](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="16c32-106">MRTK incluye un sistema de simulación elástica que incluye una amplia variedad de subclases extensibles y flexibles, que ofrece enlaces para cuaternión de cuaternión de 4 dimensiones, sonidos de volumen tridimensionales y sistemas de spring lineales simples.</span><span class="sxs-lookup"><span data-stu-id="16c32-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="16c32-107">Actualmente, los siguientes componentes de MRTK que [admiten el administrador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) pueden aprovechar la funcionalidad de los elásticos:</span><span class="sxs-lookup"><span data-stu-id="16c32-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="16c32-108">Control Bounds</span><span class="sxs-lookup"><span data-stu-id="16c32-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="16c32-109">Manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="16c32-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="16c32-110">Administrador de elastics</span><span class="sxs-lookup"><span data-stu-id="16c32-110">Elastics manager</span></span>

![Elastic System2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="16c32-112">Los procesos del administrador de elásticos pasan transformaciones y las alimentan en el sistema elástico.</span><span class="sxs-lookup"><span data-stu-id="16c32-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="16c32-113">La habilitación de elásticos para componentes personalizados se puede lograr mediante dos pasos:</span><span class="sxs-lookup"><span data-stu-id="16c32-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="16c32-114">Llamar al método Initialize al iniciar la manipulación, actualizando el sistema con la transformación de host actual.</span><span class="sxs-lookup"><span data-stu-id="16c32-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="16c32-115">Consultar ApplyHostTransform siempre que se deba realizar un cálculo elástico en la transformación de destino actualizada.</span><span class="sxs-lookup"><span data-stu-id="16c32-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="16c32-116">Tenga en cuenta que los elásticos seguirán simulando una vez que finalice la manipulación (a través del bucle de actualización del administrador de elásticos).</span><span class="sxs-lookup"><span data-stu-id="16c32-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="16c32-117">Para bloquear el comportamiento, la actualización automática de [los elásticos EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) se puede establecer en false.</span><span class="sxs-lookup"><span data-stu-id="16c32-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="16c32-118">De forma predeterminada, el componente de administrador de elásticos, cuando se agrega a un objeto de juego, no tendrá elásticos habilitados para ningún tipo de transformación.</span><span class="sxs-lookup"><span data-stu-id="16c32-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="16c32-119">El campo `Manipulation types using elastic feedback` debe habilitarse para tipos de transformación específicos para crear configuraciones elásticas y extensiones para el tipo seleccionado.</span><span class="sxs-lookup"><span data-stu-id="16c32-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="16c32-120">Configuraciones elásticas</span><span class="sxs-lookup"><span data-stu-id="16c32-120">Elastics configurations</span></span>

<span data-ttu-id="16c32-121">De forma similar a las configuraciones de [control de límites,](../ux-building-blocks/bounds-control.md#configuration-objects)Elastic Manager incluye un conjunto de objetos de configuración que se pueden almacenar como objetos que pueden incluirse en scripts y compartirse entre instancias o elementos prefab diferentes.</span><span class="sxs-lookup"><span data-stu-id="16c32-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="16c32-122">Las configuraciones se pueden compartir y vincular como archivos de recursos individuales que pueden incluirse en scripts o recursos anidados que se pueden incluir en scripts dentro de objetos prefab.</span><span class="sxs-lookup"><span data-stu-id="16c32-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="16c32-123">También se pueden definir otras configuraciones directamente en la instancia sin vincular a un recurso que permite scripts externo o anidado.</span><span class="sxs-lookup"><span data-stu-id="16c32-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="16c32-124">El inspector del administrador elástico indicará si una configuración se comparte o se inline como parte de la instancia actual mostrando un mensaje en el inspector de propiedades.</span><span class="sxs-lookup"><span data-stu-id="16c32-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="16c32-125">Además, las instancias compartidas no se podrán editar directamente en la propia ventana de propiedades del administrador de elásticos, sino que el recurso al que está vinculando debe modificarse directamente para evitar cambios accidentales en las configuraciones compartidas.</span><span class="sxs-lookup"><span data-stu-id="16c32-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="16c32-126">Elastics Manager ofrece opciones de objetos de configuración para los siguientes tipos de transformación, cada uno de ellos representado por un [objeto de configuración elástica](#elastic-configuration-object):</span><span class="sxs-lookup"><span data-stu-id="16c32-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="16c32-127">Traducción elástica</span><span class="sxs-lookup"><span data-stu-id="16c32-127">Translation Elastic</span></span>
- <span data-ttu-id="16c32-128">Rotación elástica</span><span class="sxs-lookup"><span data-stu-id="16c32-128">Rotation Elastic</span></span>
- <span data-ttu-id="16c32-129">Escalado elástico</span><span class="sxs-lookup"><span data-stu-id="16c32-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="16c32-130">Objeto de configuración elástica</span><span class="sxs-lookup"><span data-stu-id="16c32-130">Elastic configuration object</span></span>

<span data-ttu-id="16c32-131">Una configuración de elásticos define las propiedades de un sistema diferencial de diferenciales de diferenciales armónicos.</span><span class="sxs-lookup"><span data-stu-id="16c32-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="16c32-132">Las siguientes propiedades se pueden ajustar, pero ya vienen con un conjunto de valores predeterminados en MRTK:</span><span class="sxs-lookup"><span data-stu-id="16c32-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="16c32-133">**Masa:** masa del elemento de oscilador simulado.</span><span class="sxs-lookup"><span data-stu-id="16c32-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="16c32-134">**HandK:** constante de spring de mano.</span><span class="sxs-lookup"><span data-stu-id="16c32-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="16c32-135">**EndK:** end cap spring constant.</span><span class="sxs-lookup"><span data-stu-id="16c32-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="16c32-136">**SnapK:** constante de spring de punto de instantánea.</span><span class="sxs-lookup"><span data-stu-id="16c32-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="16c32-137">**Arrastre**: factor de arrastre/desastrador, proporcional a la velocidad.</span><span class="sxs-lookup"><span data-stu-id="16c32-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="16c32-138">Extensiones elásticas</span><span class="sxs-lookup"><span data-stu-id="16c32-138">Elastics extents</span></span>

<span data-ttu-id="16c32-139">La configuración de extensiones elásticas varía en función del tipo de manipulación.</span><span class="sxs-lookup"><span data-stu-id="16c32-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="16c32-140">La traducción y la escala se representan [mediante extensiones elásticas de volumen](#volume-elastic-extent) y la rotación se representa mediante una extensión elástica de [cuaternión](#quaternion-elastic-extent).</span><span class="sxs-lookup"><span data-stu-id="16c32-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="16c32-141">Extensión elástica del volumen</span><span class="sxs-lookup"><span data-stu-id="16c32-141">Volume elastic extent</span></span>

<span data-ttu-id="16c32-142">Las extensiones de volumen definen un espacio tridimensional en el que el oscilador del armónico desasistido es libre de moverse.</span><span class="sxs-lookup"><span data-stu-id="16c32-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Límites elásticos de stretch de volumen](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="16c32-144">**StretchBounds:** representa los límites inferiores del espacio elástico.</span><span class="sxs-lookup"><span data-stu-id="16c32-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="16c32-145">**UseBounds:** indica si el sistema debe respetar los límites de extensión.</span><span class="sxs-lookup"><span data-stu-id="16c32-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="16c32-146">Si es true, cuando la iteración actual de la posición de destino está fuera de los límites de extensión, se aplicará la fuerza final.</span><span class="sxs-lookup"><span data-stu-id="16c32-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="16c32-147">**Puntos de instantánea:** puntos dentro del espacio al que se ajustará el sistema.</span><span class="sxs-lookup"><span data-stu-id="16c32-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="16c32-148">**RepeatSnapPoints:** repite los puntos de ajuste al infinito.</span><span class="sxs-lookup"><span data-stu-id="16c32-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="16c32-149">Los puntos de ajuste existentes servirán como módulo donde los puntos de ajuste reales se asignan a los múltiples enteros más cercanos de cada punto de instantánea.</span><span class="sxs-lookup"><span data-stu-id="16c32-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="16c32-150">**SnapRadius:** distancia a la que los puntos de ajuste comienzan a forzar el resorte.</span><span class="sxs-lookup"><span data-stu-id="16c32-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Elastic Volume Snap Grid](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="16c32-152">Extensión elástica de cuaternión</span><span class="sxs-lookup"><span data-stu-id="16c32-152">Quaternion elastic extent</span></span>

<span data-ttu-id="16c32-153">Las extensiones de cuaternión definen un espacio de rotación dimensional de cuatro dimensiones en el que el oscilador del armónico desasistido es libre de girar.</span><span class="sxs-lookup"><span data-stu-id="16c32-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Ejemplo de rotación elástica](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="16c32-155">**SnapPoints:** ángulos euler a los que se ajustará el sistema.</span><span class="sxs-lookup"><span data-stu-id="16c32-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="16c32-156">**RepeatSnapPoints:** repite los puntos de ajuste.</span><span class="sxs-lookup"><span data-stu-id="16c32-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="16c32-157">Los puntos de ajuste existentes servirán como módulo donde los puntos de ajuste reales se asignan a los múltiples enteros más cercanos de cada punto de instantánea.</span><span class="sxs-lookup"><span data-stu-id="16c32-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="16c32-158">**SnapRadius:** ángulo de arco en el que los puntos de ajuste comienzan a forzar el resorte en grados euler.</span><span class="sxs-lookup"><span data-stu-id="16c32-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="16c32-159">Escena de ejemplo de elastics</span><span class="sxs-lookup"><span data-stu-id="16c32-159">Elastics example scene</span></span>

<span data-ttu-id="16c32-160">Puede encontrar ejemplos de configuraciones elásticas en la `ElasticSystemExample` escena.</span><span class="sxs-lookup"><span data-stu-id="16c32-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Escena de ejemplo de elastics](../images/elastics/Elastics_Example_Scene.png)
