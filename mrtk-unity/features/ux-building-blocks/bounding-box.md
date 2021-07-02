---
title: Rectángulo de selección
description: Información general sobre Bounding Box en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Bounding Box
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177547"
---
# <a name="bounding-box"></a><span data-ttu-id="aea5b-104">Rectángulo de selección</span><span class="sxs-lookup"><span data-stu-id="aea5b-104">Bounding box</span></span>

![Rectángulo de selección](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="aea5b-106">El cuadro de límite está en desuso y se reemplaza por su control [de límites de su sucesor.](bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="aea5b-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="aea5b-107">Use [una de las opciones de migración para](#migrating-to-bounds-control) actualizar los objetos de juego existentes.</span><span class="sxs-lookup"><span data-stu-id="aea5b-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="aea5b-108">El [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script proporciona funcionalidad básica para transformar objetos en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="aea5b-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="aea5b-109">Un rectángulo delimitador mostrará un cubo alrededor del holograma para indicar que se puede interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="aea5b-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="aea5b-110">Los identificadores de las esquinas y bordes del cubo permiten escalar o girar el objeto.</span><span class="sxs-lookup"><span data-stu-id="aea5b-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="aea5b-111">El cuadro de límite también reacciona a la entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="aea5b-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="aea5b-112">Por HoloLens 2, por ejemplo, el cuadro de límite responde a la proximidad de los dedos, proporcionando comentarios visuales para ayudar a percibir la distancia desde el objeto.</span><span class="sxs-lookup"><span data-stu-id="aea5b-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="aea5b-113">Todas las interacciones y objetos visuales se pueden personalizar fácilmente.</span><span class="sxs-lookup"><span data-stu-id="aea5b-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="aea5b-114">Para obtener más información, [vea Cuadro de límite y Barra de aplicación](/windows/mixed-reality/app-bar-and-bounding-box) en la Windows Centro de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="aea5b-114">For more information, see [Bounding box and App bar](/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="aea5b-115">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="aea5b-115">Example scene</span></span>

<span data-ttu-id="aea5b-116">Puede encontrar ejemplos de configuraciones de rectángulo de selección en la `BoundingBoxExamples` escena.</span><span class="sxs-lookup"><span data-stu-id="aea5b-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="aea5b-117">Adición y configuración de un rectángulo de selección mediante Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="aea5b-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="aea5b-118">Agregar box collider a un objeto</span><span class="sxs-lookup"><span data-stu-id="aea5b-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="aea5b-119">Asignación `BoundingBox` de script a un objeto</span><span class="sxs-lookup"><span data-stu-id="aea5b-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="aea5b-120">Configuración de opciones, como los métodos de activación (consulte la [sección Propiedades del inspector](#inspector-properties) a continuación)</span><span class="sxs-lookup"><span data-stu-id="aea5b-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="aea5b-121">(Opcional) Asignación de prefabs y materiales para un HoloLens 2 delimitador de estilo (consulte la sección Estilos [de](#handle-styles) identificador a continuación)</span><span class="sxs-lookup"><span data-stu-id="aea5b-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="aea5b-122">Use *el objeto de* destino y el campo Invalidación de *límites* en el inspector para asignar un objeto y colisionador específicos en el objeto con varios componentes secundarios.</span><span class="sxs-lookup"><span data-stu-id="aea5b-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Rectángulo de selección 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="aea5b-124">Cómo agregar y configurar un cuadro de límite en el código</span><span class="sxs-lookup"><span data-stu-id="aea5b-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="aea5b-125">Creación de instancias de GameObject de cubo</span><span class="sxs-lookup"><span data-stu-id="aea5b-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="aea5b-126">Asignación `BoundingBox` de un script a un objeto con colisionador mediante AddComponent<>()</span><span class="sxs-lookup"><span data-stu-id="aea5b-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="aea5b-127">Configurar opciones (consulte la [sección Propiedades del inspector](#inspector-properties) a continuación)</span><span class="sxs-lookup"><span data-stu-id="aea5b-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="aea5b-128">(Opcional) Asigne prefabs y materiales para un HoloLens 2 delimitador de estilo.</span><span class="sxs-lookup"><span data-stu-id="aea5b-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="aea5b-129">Esto todavía requiere asignaciones a través del inspector, ya que los materiales y los objetos prefab deben cargarse dinámicamente.</span><span class="sxs-lookup"><span data-stu-id="aea5b-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="aea5b-130">No se recomienda usar la carpeta "Resources" de Unity o [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) para cargar de forma dinámica sombreadores, ya que es posible que falte permutaciones del sombreador en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="aea5b-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="aea5b-131">Ejemplo: Establecer la escala mínima y máxima del cuadro de límite mediante MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="aea5b-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="aea5b-132">Para establecer la escala mínima y máxima, use [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) .</span><span class="sxs-lookup"><span data-stu-id="aea5b-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="aea5b-133">También puede usar MinMaxScaleConstraint para establecer la escala mínima y máxima para [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="aea5b-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="aea5b-134">Ejemplo: Agregar un cuadro de límite alrededor de un objeto de juego</span><span class="sxs-lookup"><span data-stu-id="aea5b-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="aea5b-135">Para agregar un rectángulo delimitador alrededor de un objeto, basta con agregarle `BoundingBox` un componente:</span><span class="sxs-lookup"><span data-stu-id="aea5b-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="aea5b-136">Propiedades del inspector</span><span class="sxs-lookup"><span data-stu-id="aea5b-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="aea5b-137">Objeto de destino</span><span class="sxs-lookup"><span data-stu-id="aea5b-137">Target object</span></span>

<span data-ttu-id="aea5b-138">Esta propiedad especifica qué objeto se transformará mediante la manipulación del cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="aea5b-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="aea5b-139">Si no se establece ningún objeto, el cuadro de límite tiene como valor predeterminado el objeto propietario.</span><span class="sxs-lookup"><span data-stu-id="aea5b-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="aea5b-140">Invalidación de límites</span><span class="sxs-lookup"><span data-stu-id="aea5b-140">Bounds override</span></span>

<span data-ttu-id="aea5b-141">Establece un colisionador de cuadros del objeto para el cálculo de límites.</span><span class="sxs-lookup"><span data-stu-id="aea5b-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="aea5b-142">Comportamiento de activación</span><span class="sxs-lookup"><span data-stu-id="aea5b-142">Activation behavior</span></span>

<span data-ttu-id="aea5b-143">Hay varias opciones para activar la interfaz del cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="aea5b-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="aea5b-144">*Activar al iniciar:* el cuadro de límite se vuelve visible una vez que se inicia la escena.</span><span class="sxs-lookup"><span data-stu-id="aea5b-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="aea5b-145">*Activar por proximidad:* el cuadro de límite se vuelve visible cuando una mano articulada está cerca del objeto.</span><span class="sxs-lookup"><span data-stu-id="aea5b-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="aea5b-146">*Activar por puntero:* el rectángulo de selección se vuelve visible cuando está dirigido por un puntero de rayos de mano.</span><span class="sxs-lookup"><span data-stu-id="aea5b-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="aea5b-147">*Activar manualmente:* el cuadro de límite no se vuelve visible automáticamente.</span><span class="sxs-lookup"><span data-stu-id="aea5b-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="aea5b-148">Puede activarlo manualmente a través de un script accediendo a la propiedad boundingBox.Active.</span><span class="sxs-lookup"><span data-stu-id="aea5b-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="aea5b-149">Escala mínima</span><span class="sxs-lookup"><span data-stu-id="aea5b-149">Scale minimum</span></span>

<span data-ttu-id="aea5b-150">Escala mínima permitida.</span><span class="sxs-lookup"><span data-stu-id="aea5b-150">The minimum allowed scale.</span></span> <span data-ttu-id="aea5b-151">Esta propiedad está en desuso y es preferible agregar un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="aea5b-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="aea5b-152">Si se agrega este script, la escala mínima se toma de él en lugar del cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="aea5b-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="aea5b-153">Escalado máximo</span><span class="sxs-lookup"><span data-stu-id="aea5b-153">Scale maximum</span></span>

<span data-ttu-id="aea5b-154">Escala máxima permitida.</span><span class="sxs-lookup"><span data-stu-id="aea5b-154">The maximum allowed scale.</span></span> <span data-ttu-id="aea5b-155">Esta propiedad está en desuso y es preferible agregar un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="aea5b-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="aea5b-156">Si se agrega este script, la escala máxima se toma de él en lugar del cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="aea5b-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="aea5b-157">Presentación del cuadro</span><span class="sxs-lookup"><span data-stu-id="aea5b-157">Box display</span></span>

<span data-ttu-id="aea5b-158">Varias opciones de visualización del cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="aea5b-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="aea5b-159">Si Aplanar eje se establece en *Aplanar automático,* el script no permitirá la manipulación a lo largo del eje con la extensión más pequeña.</span><span class="sxs-lookup"><span data-stu-id="aea5b-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="aea5b-160">Esto da como resultado un cuadro de límite 2D, que normalmente se usa para objetos finos.</span><span class="sxs-lookup"><span data-stu-id="aea5b-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="aea5b-161">Asas</span><span class="sxs-lookup"><span data-stu-id="aea5b-161">Handles</span></span>

<span data-ttu-id="aea5b-162">Puede asignar el material y el prefab para invalidar el estilo del identificador.</span><span class="sxs-lookup"><span data-stu-id="aea5b-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="aea5b-163">Si no se asignan identificadores, se mostrarán en el estilo predeterminado.</span><span class="sxs-lookup"><span data-stu-id="aea5b-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="aea5b-164">Events</span><span class="sxs-lookup"><span data-stu-id="aea5b-164">Events</span></span>

<span data-ttu-id="aea5b-165">El cuadro de límite proporciona los siguientes eventos.</span><span class="sxs-lookup"><span data-stu-id="aea5b-165">Bounding box provides the following events.</span></span> <span data-ttu-id="aea5b-166">En este ejemplo se usan estos eventos para reproducir comentarios de audio.</span><span class="sxs-lookup"><span data-stu-id="aea5b-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="aea5b-167">**Girar iniciado:** se desencadena cuando se inicia la rotación.</span><span class="sxs-lookup"><span data-stu-id="aea5b-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="aea5b-168">**Girar finalizado:** se desencadena cuando finaliza la rotación.</span><span class="sxs-lookup"><span data-stu-id="aea5b-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="aea5b-169">**Escalado iniciado:** se inicia cuando se inicia el escalado.</span><span class="sxs-lookup"><span data-stu-id="aea5b-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="aea5b-170">**Escala finalizada:** se produce cuando finaliza el escalado.</span><span class="sxs-lookup"><span data-stu-id="aea5b-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="aea5b-171">Controlar estilos</span><span class="sxs-lookup"><span data-stu-id="aea5b-171">Handle styles</span></span>

<span data-ttu-id="aea5b-172">De forma predeterminada, al asignar el script, se mostrará el identificador del HoloLens [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) de primera generación.</span><span class="sxs-lookup"><span data-stu-id="aea5b-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="aea5b-173">Para usar HoloLens 2 identificadores de estilo, debe asignar prefabs y materiales de identificador adecuados.</span><span class="sxs-lookup"><span data-stu-id="aea5b-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Estilos de identificador de cuadro de límite](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="aea5b-175">A continuación se muestran los requisitos previos, los materiales y los valores de escalado para los identificadores HoloLens 2 cuadro de límite de estilo.</span><span class="sxs-lookup"><span data-stu-id="aea5b-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="aea5b-176">Puede encontrar este ejemplo en la `BoundingBoxExamples` escena.</span><span class="sxs-lookup"><span data-stu-id="aea5b-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="aea5b-177">Identificadores (configuración para HoloLens 2 estilo)</span><span class="sxs-lookup"><span data-stu-id="aea5b-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="aea5b-178">**Material de identificador:** BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="aea5b-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="aea5b-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="aea5b-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="aea5b-180">**Prefab del identificador de** escala: MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="aea5b-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="aea5b-181">**Prefab de pizarra del** controlador de escala: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="aea5b-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="aea5b-182">**Tamaño del identificador de** escala: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="aea5b-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="aea5b-183">**Relleno del colisionador del** controlador de escala: 0,016 (hace que el colisionador que se puede agarrar sea ligeramente mayor que el objeto visual del controlador)</span><span class="sxs-lookup"><span data-stu-id="aea5b-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="aea5b-184">**Prefab del identificador de** rotación: MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="aea5b-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="aea5b-185">**Tamaño del identificador de** rotación: 0,016</span><span class="sxs-lookup"><span data-stu-id="aea5b-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="aea5b-186">**Relleno del colisionador del** controlador de rotación: 0,016 (hace que el colisionador que se puede agarrar sea ligeramente mayor que el objeto visual del controlador)</span><span class="sxs-lookup"><span data-stu-id="aea5b-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="aea5b-187">Proximidad (configuración para HoloLens 2 estilo)</span><span class="sxs-lookup"><span data-stu-id="aea5b-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="aea5b-188">Muestre y oculte los identificadores con animación en función de la distancia a las manos.</span><span class="sxs-lookup"><span data-stu-id="aea5b-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="aea5b-189">Tiene animación de escalado en dos pasos.</span><span class="sxs-lookup"><span data-stu-id="aea5b-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="aea5b-190">**Efecto de proximidad activo:** habilitación de la activación del identificador basado en proximidad</span><span class="sxs-lookup"><span data-stu-id="aea5b-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="aea5b-191">**Controlar la proximidad media:** distancia para el escalado del primer paso</span><span class="sxs-lookup"><span data-stu-id="aea5b-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="aea5b-192">**Control de proximidad: distancia** para el escalado del segundo paso</span><span class="sxs-lookup"><span data-stu-id="aea5b-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="aea5b-193">**Escala lejana:** valor de escala predeterminado del recurso de identificador cuando las manos están fuera del intervalo de la interacción del cuadro de límite (distancia definida anteriormente por "Controlar proximidad media".</span><span class="sxs-lookup"><span data-stu-id="aea5b-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="aea5b-194">Use 0 para ocultar el identificador de forma predeterminada)</span><span class="sxs-lookup"><span data-stu-id="aea5b-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="aea5b-195">**Escala media:** valor de escala del recurso de identificador cuando las manos están dentro del intervalo de la interacción del cuadro de límite (distancia definida anteriormente por "Proximidad de cierre del identificador".</span><span class="sxs-lookup"><span data-stu-id="aea5b-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="aea5b-196">Use 1 para mostrar el tamaño normal)</span><span class="sxs-lookup"><span data-stu-id="aea5b-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="aea5b-197">**Escala de** cierre: valor de escala del recurso de identificador cuando las manos están dentro del intervalo de la interacción de agarre (distancia definida anteriormente por "Proximidad de cierre del controlador".</span><span class="sxs-lookup"><span data-stu-id="aea5b-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="aea5b-198">Usar 1.x para mostrar un tamaño mayor)</span><span class="sxs-lookup"><span data-stu-id="aea5b-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="aea5b-199">Hacer que un objeto se puede mover con el controlador de manipulación</span><span class="sxs-lookup"><span data-stu-id="aea5b-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="aea5b-200">Se puede combinar un cuadro de límite con [`ManipulationHandler.cs`](manipulation-handler.md) para que el objeto se pueda mover mediante la interacción lejana.</span><span class="sxs-lookup"><span data-stu-id="aea5b-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="aea5b-201">El controlador de manipulación admite interacciones de una y dos manos.</span><span class="sxs-lookup"><span data-stu-id="aea5b-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="aea5b-202">[El seguimiento](../input/hand-tracking.md) manual se puede usar para interactuar con un objeto de cerca.</span><span class="sxs-lookup"><span data-stu-id="aea5b-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="aea5b-203">Para que los bordes del cuadro de límite se comporten de la misma manera al moverlo mediante la interacción lejana, se recomienda conectar sus eventos para On Manipulation Started On Manipulation Ended (Manipulación iniciada al finalizar), respectivamente, como se muestra en la captura de pantalla [`ManipulationHandler`](manipulation-handler.md)   /   `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` anterior.</span><span class="sxs-lookup"><span data-stu-id="aea5b-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="aea5b-204">Migración al control de límites</span><span class="sxs-lookup"><span data-stu-id="aea5b-204">Migrating to bounds control</span></span>

<span data-ttu-id="aea5b-205">Las instancias y los requisitos previos existentes que usan el [](../tools/migration-window.md) cuadro de límite se pueden actualizar al nuevo control de límites a través de la ventana de migración que forma parte del paquete de herramientas de MRTK. [](bounding-box.md)</span><span class="sxs-lookup"><span data-stu-id="aea5b-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="aea5b-206">Para actualizar instancias individuales del rectángulo de selección, también hay una opción de migración dentro del inspector de propiedades del componente.</span><span class="sxs-lookup"><span data-stu-id="aea5b-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
