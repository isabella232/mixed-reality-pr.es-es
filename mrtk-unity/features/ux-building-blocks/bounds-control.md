---
title: BoundsControl
description: Información general sobre el control de límites en MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, control de límites,
ms.openlocfilehash: 65558861955f782cf9d81a8bb4ec3a31dee03fde
ms.sourcegitcommit: 95ea5f3cf873acc93c4614fbccaa093e0f5186f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2021
ms.locfileid: "110487732"
---
# <a name="bounds-control"></a><span data-ttu-id="15f31-104">Control Límites</span><span class="sxs-lookup"><span data-stu-id="15f31-104">Bounds control</span></span>

![Control Límites](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="15f31-106">*BoundsControl es* el nuevo componente para el comportamiento de manipulación, que se encontró anteriormente *en BoundingBox*.</span><span class="sxs-lookup"><span data-stu-id="15f31-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="15f31-107">El control de límites realiza una serie de mejoras y simplificaciones en la configuración y agrega nuevas características.</span><span class="sxs-lookup"><span data-stu-id="15f31-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="15f31-108">Este componente es un reemplazo del rectángulo de selección, que estará en desuso.</span><span class="sxs-lookup"><span data-stu-id="15f31-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="15f31-109">El [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script proporciona funcionalidad básica para transformar objetos en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="15f31-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="15f31-110">Un control de límites mostrará un cuadro alrededor del holograma para indicar que se puede interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="15f31-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="15f31-111">Los identificadores de las esquinas y bordes del cuadro permiten escalar, girar o traducir el objeto.</span><span class="sxs-lookup"><span data-stu-id="15f31-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="15f31-112">El control de límites también reacciona a la entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="15f31-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="15f31-113">Por HoloLens 2, por ejemplo, el control de límites responde a la proximidad de los dedos, proporcionando comentarios visuales para ayudar a percibir la distancia desde el objeto.</span><span class="sxs-lookup"><span data-stu-id="15f31-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="15f31-114">Todas las interacciones y objetos visuales se pueden personalizar fácilmente.</span><span class="sxs-lookup"><span data-stu-id="15f31-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="15f31-115">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="15f31-115">Example scene</span></span>

<span data-ttu-id="15f31-116">Puede encontrar ejemplos de configuraciones de control de límites en la `BoundsControlExamples` escena.</span><span class="sxs-lookup"><span data-stu-id="15f31-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="15f31-117">Propiedades del inspector</span><span class="sxs-lookup"><span data-stu-id="15f31-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="15f31-118">Objeto de destino</span><span class="sxs-lookup"><span data-stu-id="15f31-118">Target object</span></span>

<span data-ttu-id="15f31-119">Esta propiedad especifica qué objeto se transformará mediante la manipulación del control de límites.</span><span class="sxs-lookup"><span data-stu-id="15f31-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="15f31-120">Si no se establece ningún objeto, el valor predeterminado es el objeto propietario.</span><span class="sxs-lookup"><span data-stu-id="15f31-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="15f31-121">Comportamiento de activación</span><span class="sxs-lookup"><span data-stu-id="15f31-121">Activation behavior</span></span>

<span data-ttu-id="15f31-122">Hay varias opciones para activar la interfaz de control de límites.</span><span class="sxs-lookup"><span data-stu-id="15f31-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="15f31-123">*Activar al iniciar:* el control Límites se vuelve visible una vez que se inicia la escena.</span><span class="sxs-lookup"><span data-stu-id="15f31-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="15f31-124">*Activar por proximidad:* el control límites se hace visible cuando una mano articulada está cerca del objeto.</span><span class="sxs-lookup"><span data-stu-id="15f31-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="15f31-125">*Activar por puntero:* el control Límites se vuelve visible cuando se apunta a él mediante un puntero de rayo de mano.</span><span class="sxs-lookup"><span data-stu-id="15f31-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="15f31-126">*Activar por proximidad y* puntero: el control de límites se vuelve visible cuando el destino es un puntero de rayo de mano o una mano articulada está cerca del objeto.</span><span class="sxs-lookup"><span data-stu-id="15f31-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="15f31-127">*Activar manualmente:* el control Límites no se hace visible automáticamente.</span><span class="sxs-lookup"><span data-stu-id="15f31-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="15f31-128">Puede activarlo manualmente a través de un script accediendo a la propiedad boundsControl.Active.</span><span class="sxs-lookup"><span data-stu-id="15f31-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="15f31-129">Invalidación de límites</span><span class="sxs-lookup"><span data-stu-id="15f31-129">Bounds override</span></span>

<span data-ttu-id="15f31-130">Establece un colisionador de cuadro del objeto para el cálculo de límites.</span><span class="sxs-lookup"><span data-stu-id="15f31-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="15f31-131">Relleno de cuadro</span><span class="sxs-lookup"><span data-stu-id="15f31-131">Box padding</span></span>

<span data-ttu-id="15f31-132">Agrega un relleno a los límites del colisionador utilizados para calcular las extensiones del control.</span><span class="sxs-lookup"><span data-stu-id="15f31-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="15f31-133">Esto influirá no solo en la interacción, sino que también afectará a los objetos visuales.</span><span class="sxs-lookup"><span data-stu-id="15f31-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="15f31-134">Eje aplanado</span><span class="sxs-lookup"><span data-stu-id="15f31-134">Flatten axis</span></span>

<span data-ttu-id="15f31-135">Indica si el control está aplanado en uno de los ejes, lo que lo hace 2 dimensiones y no permite la manipulación a lo largo de ese eje.</span><span class="sxs-lookup"><span data-stu-id="15f31-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="15f31-136">Esta característica se puede usar para objetos finos como pizarras.</span><span class="sxs-lookup"><span data-stu-id="15f31-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="15f31-137">Si el eje de aplanado se establece *en Aplanar* automáticamente, el script seleccionará automáticamente el eje con la extensión más pequeña como eje plano.</span><span class="sxs-lookup"><span data-stu-id="15f31-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="15f31-138">Suavizado</span><span class="sxs-lookup"><span data-stu-id="15f31-138">Smoothing</span></span>

<span data-ttu-id="15f31-139">La sección de suavizado permite configurar el comportamiento de suavizado para escalar y girar el control.</span><span class="sxs-lookup"><span data-stu-id="15f31-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="15f31-140">Objetos visuales</span><span class="sxs-lookup"><span data-stu-id="15f31-140">Visuals</span></span>

<span data-ttu-id="15f31-141">La apariencia del control de límites se puede configurar modificando una de las configuraciones de objetos visuales correspondientes.</span><span class="sxs-lookup"><span data-stu-id="15f31-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="15f31-142">Las configuraciones visuales son objetos vinculados o que pueden incluirse en scripts y se describen con más detalle en la sección del objeto [de configuración](#configuration-objects).</span><span class="sxs-lookup"><span data-stu-id="15f31-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="15f31-143">Objetos de configuración</span><span class="sxs-lookup"><span data-stu-id="15f31-143">Configuration Objects</span></span>

<span data-ttu-id="15f31-144">El control incluye un conjunto de objetos de configuración que se pueden almacenar como objetos que pueden incluirse en scripts y compartirse entre instancias o elementos prefabs diferentes.</span><span class="sxs-lookup"><span data-stu-id="15f31-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="15f31-145">Las configuraciones se pueden compartir y vincular como archivos de recursos individuales que pueden incluirse en scripts o recursos anidados que se pueden incluir en scripts dentro de objetos prefab.</span><span class="sxs-lookup"><span data-stu-id="15f31-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="15f31-146">También se pueden definir otras configuraciones directamente en la instancia sin vincular a un recurso que puede incluir scripts externo o anidado.</span><span class="sxs-lookup"><span data-stu-id="15f31-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="15f31-147">El inspector de control de límites indicará si una configuración se comparte o se inline como parte de la instancia actual mostrando un mensaje en el inspector de propiedades.</span><span class="sxs-lookup"><span data-stu-id="15f31-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="15f31-148">Además, las instancias compartidas no se podrán editar directamente en la propia ventana de propiedades de control de límites, sino que el recurso al que está vinculando debe modificarse directamente para evitar cambios accidentales en las configuraciones compartidas.</span><span class="sxs-lookup"><span data-stu-id="15f31-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="15f31-149">Actualmente, el control de límites ofrece opciones de objetos de configuración para las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="15f31-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="15f31-150">Asas</span><span class="sxs-lookup"><span data-stu-id="15f31-150">Handles</span></span>
  * [<span data-ttu-id="15f31-151">Identificadores de escala</span><span class="sxs-lookup"><span data-stu-id="15f31-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="15f31-152">Identificadores de rotación</span><span class="sxs-lookup"><span data-stu-id="15f31-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="15f31-153">Identificadores de traducción</span><span class="sxs-lookup"><span data-stu-id="15f31-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="15f31-154">Vínculos/Wireframe</span><span class="sxs-lookup"><span data-stu-id="15f31-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="15f31-155">Presentación del cuadro</span><span class="sxs-lookup"><span data-stu-id="15f31-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="15f31-156">Efecto de proximidad</span><span class="sxs-lookup"><span data-stu-id="15f31-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="15f31-157">Configuración de Box</span><span class="sxs-lookup"><span data-stu-id="15f31-157">Box configuration</span></span>

<span data-ttu-id="15f31-158">La configuración del cuadro es responsable de representar un cuadro sólido con límites definidos a través del tamaño del colisionador y el relleno del cuadro.</span><span class="sxs-lookup"><span data-stu-id="15f31-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="15f31-159">Se pueden configurar las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="15f31-159">The following properties can be set up:</span></span>

* <span data-ttu-id="15f31-160">**Material de cuadro:** define el material aplicado al cuadro representado cuando no tiene lugar ninguna interacción.</span><span class="sxs-lookup"><span data-stu-id="15f31-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="15f31-161">Solo se representará un cuadro si se establece este material.</span><span class="sxs-lookup"><span data-stu-id="15f31-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="15f31-162">**Material de caja capturada:** material para la caja cuando el usuario interactúa con el control mediante la interacción cercana o lejana.</span><span class="sxs-lookup"><span data-stu-id="15f31-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="15f31-163">**Escala de presentación del eje** aplanado: escala que se aplica a la pantalla de cuadro si uno de los ejes está [plano.](#flatten-axis)</span><span class="sxs-lookup"><span data-stu-id="15f31-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="15f31-164">Configuración de identificadores de escalado</span><span class="sxs-lookup"><span data-stu-id="15f31-164">Scale handles configuration</span></span>

<span data-ttu-id="15f31-165">Este cajón de propiedades permite modificar el comportamiento y la visualización de los identificadores de escala del control de límites.</span><span class="sxs-lookup"><span data-stu-id="15f31-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="15f31-166">**Material de identificador:** material aplicado a los identificadores.</span><span class="sxs-lookup"><span data-stu-id="15f31-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="15f31-167">**Manipula el material tomado:** material aplicado al asa capturada.</span><span class="sxs-lookup"><span data-stu-id="15f31-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="15f31-168">**Controlar prefab:** prefab opcional para el identificador de escala.</span><span class="sxs-lookup"><span data-stu-id="15f31-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="15f31-169">Si no está establecido, MRTK usará un cubo como valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="15f31-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="15f31-170">**Tamaño del identificador:** tamaño del identificador de escala.</span><span class="sxs-lookup"><span data-stu-id="15f31-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="15f31-171">**Relleno del colisionador:** relleno que se agrega al colisionador del controlador.</span><span class="sxs-lookup"><span data-stu-id="15f31-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="15f31-172">**Dibujar tether al manipular**: cuando está activo dibujará una línea de tether desde el punto de inicio de la interacción hasta la posición actual de la mano o del puntero.</span><span class="sxs-lookup"><span data-stu-id="15f31-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="15f31-173">**Los controladores omiten al** colisionador: si un colisionador se vincula aquí, los controladores omitirán cualquier colisión con este colisionador.</span><span class="sxs-lookup"><span data-stu-id="15f31-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="15f31-174">**Control del prefab de pizarra:** prefab que se va a usar para el identificador cuando el control se aplana.</span><span class="sxs-lookup"><span data-stu-id="15f31-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="15f31-175">**Mostrar identificadores de escala:** controla la visibilidad del identificador.</span><span class="sxs-lookup"><span data-stu-id="15f31-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="15f31-176">**Comportamiento de escala:** se puede establecer en escalado uniforme o no uniforme.</span><span class="sxs-lookup"><span data-stu-id="15f31-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="15f31-177">Configuración de identificadores de rotación</span><span class="sxs-lookup"><span data-stu-id="15f31-177">Rotation handles configuration</span></span>

<span data-ttu-id="15f31-178">Esta configuración define el comportamiento del identificador de rotación.</span><span class="sxs-lookup"><span data-stu-id="15f31-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="15f31-179">**Material de identificador:** material aplicado a los identificadores.</span><span class="sxs-lookup"><span data-stu-id="15f31-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="15f31-180">**Manipula el material tomado:** material aplicado al asa capturada.</span><span class="sxs-lookup"><span data-stu-id="15f31-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="15f31-181">**Controlar prefab:** prefab opcional para el identificador.</span><span class="sxs-lookup"><span data-stu-id="15f31-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="15f31-182">Si no está establecido, MRTK usará una esfera como valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="15f31-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="15f31-183">**Tamaño del identificador:** tamaño del identificador.</span><span class="sxs-lookup"><span data-stu-id="15f31-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="15f31-184">**Relleno del colisionador:** relleno que se agrega al colisionador del controlador.</span><span class="sxs-lookup"><span data-stu-id="15f31-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="15f31-185">**Dibujar tether al manipular**: cuando está activo dibujará una línea de tether desde el punto de inicio de la interacción hasta la posición actual de la mano o del puntero.</span><span class="sxs-lookup"><span data-stu-id="15f31-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="15f31-186">**Los controladores omiten al** colisionador: si un colisionador se vincula aquí, los controladores omitirán cualquier colisión con este colisionador.</span><span class="sxs-lookup"><span data-stu-id="15f31-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="15f31-187">**Controlar el tipo de colisionador prefab:** tipo de colisionador que se va a usar con el identificador creado.</span><span class="sxs-lookup"><span data-stu-id="15f31-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="15f31-188">**Mostrar identificador para X:** controla la visibilidad del identificador para el eje X.</span><span class="sxs-lookup"><span data-stu-id="15f31-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="15f31-189">**Mostrar identificador para Y:** controla la visibilidad del identificador para el eje Y.</span><span class="sxs-lookup"><span data-stu-id="15f31-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="15f31-190">**Mostrar identificador para Z:** controla la visibilidad del identificador para el eje Z.</span><span class="sxs-lookup"><span data-stu-id="15f31-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="15f31-191">Configuración de identificadores de traducción</span><span class="sxs-lookup"><span data-stu-id="15f31-191">Translation handles configuration</span></span>

<span data-ttu-id="15f31-192">Permite habilitar y configurar identificadores de traducción para el control de límites.</span><span class="sxs-lookup"><span data-stu-id="15f31-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="15f31-193">Tenga en cuenta que los identificadores de traducción están deshabilitados de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="15f31-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="15f31-194">**Material de identificador:** material aplicado a los identificadores.</span><span class="sxs-lookup"><span data-stu-id="15f31-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="15f31-195">**Manipula el material tomado:** material aplicado al asa capturada.</span><span class="sxs-lookup"><span data-stu-id="15f31-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="15f31-196">**Controlar prefab:** prefab opcional para el identificador.</span><span class="sxs-lookup"><span data-stu-id="15f31-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="15f31-197">Si no está establecido, MRTK usará una esfera como valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="15f31-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="15f31-198">**Tamaño del identificador:** tamaño del identificador.</span><span class="sxs-lookup"><span data-stu-id="15f31-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="15f31-199">**Relleno del colisionador:** relleno que se agrega al colisionador del controlador.</span><span class="sxs-lookup"><span data-stu-id="15f31-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="15f31-200">**Dibujar tether al manipular**: cuando está activo dibujará una línea de tether desde el punto de inicio de la interacción hasta la posición actual de la mano o del puntero.</span><span class="sxs-lookup"><span data-stu-id="15f31-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="15f31-201">**Los controladores omiten al** colisionador: si un colisionador se vincula aquí, los controladores omitirán cualquier colisión con este colisionador.</span><span class="sxs-lookup"><span data-stu-id="15f31-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="15f31-202">**Controlar el tipo de colisionador prefab:** tipo de colisionador que se va a usar con el identificador creado.</span><span class="sxs-lookup"><span data-stu-id="15f31-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="15f31-203">**Mostrar identificador para X:** controla la visibilidad del identificador del eje X.</span><span class="sxs-lookup"><span data-stu-id="15f31-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="15f31-204">**Mostrar identificador para Y:** controla la visibilidad del identificador para el eje Y.</span><span class="sxs-lookup"><span data-stu-id="15f31-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="15f31-205">**Mostrar identificador para Z:** controla la visibilidad del identificador para el eje Z.</span><span class="sxs-lookup"><span data-stu-id="15f31-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="15f31-206">Configuración de vínculos (wireframe)</span><span class="sxs-lookup"><span data-stu-id="15f31-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="15f31-207">La configuración de vínculos habilita la característica wireframe del control de límites.</span><span class="sxs-lookup"><span data-stu-id="15f31-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="15f31-208">Se pueden configurar las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="15f31-208">The following properties can be configured:</span></span>

* <span data-ttu-id="15f31-209">**Material de wireframe:** el material aplicado a la malla de wireframe.</span><span class="sxs-lookup"><span data-stu-id="15f31-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="15f31-210">**Radio del borde de la trama** de conexión: grosor de la trama de conexión.</span><span class="sxs-lookup"><span data-stu-id="15f31-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="15f31-211">**Forma de wireframe:** la forma del wireframe puede ser cúbica o cilíndrica.</span><span class="sxs-lookup"><span data-stu-id="15f31-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="15f31-212">**Mostrar wireframe:** controla la visibilidad del wireframe.</span><span class="sxs-lookup"><span data-stu-id="15f31-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="15f31-213">Configuración del efecto de proximidad</span><span class="sxs-lookup"><span data-stu-id="15f31-213">Proximity effect configuration</span></span>

<span data-ttu-id="15f31-214">Mostrar y ocultar los controladores con animación en función de la distancia a las manos.</span><span class="sxs-lookup"><span data-stu-id="15f31-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="15f31-215">Tiene animación de escalado en dos pasos.</span><span class="sxs-lookup"><span data-stu-id="15f31-215">It has two-step scaling animation.</span></span> <span data-ttu-id="15f31-216">Los valores predeterminados se establecen en HoloLens 2 comportamiento de estilo.</span><span class="sxs-lookup"><span data-stu-id="15f31-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="15f31-217">**Efecto de proximidad activo:** habilitación de la activación del identificador basado en proximidad</span><span class="sxs-lookup"><span data-stu-id="15f31-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="15f31-218">**Proximidad media del objeto:** distancia para el escalado del primer paso</span><span class="sxs-lookup"><span data-stu-id="15f31-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="15f31-219">**Proximidad de cierre de objeto:** distancia para el escalado del segundo paso</span><span class="sxs-lookup"><span data-stu-id="15f31-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="15f31-220">**Escala lejana:** valor de escala predeterminado del recurso de controlador cuando las manos están fuera del intervalo de la interacción de control de límites (distancia definida anteriormente por "Controlar la proximidad media".</span><span class="sxs-lookup"><span data-stu-id="15f31-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="15f31-221">Use 0 para ocultar el identificador de forma predeterminada)</span><span class="sxs-lookup"><span data-stu-id="15f31-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="15f31-222">**Escala media:** valor de escala del recurso de identificador cuando las manos están dentro del intervalo de la interacción de control de límites (distancia definida anteriormente por "Controlar proximidad cercana".</span><span class="sxs-lookup"><span data-stu-id="15f31-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="15f31-223">Use 1 para mostrar el tamaño normal)</span><span class="sxs-lookup"><span data-stu-id="15f31-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="15f31-224">**Close Scale**(Escala de cierre): valor de escala del recurso de controlador cuando las manos están dentro del intervalo de la interacción de la toma (distancia definida anteriormente por "Controlar proximidad cercana".</span><span class="sxs-lookup"><span data-stu-id="15f31-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="15f31-225">Usar 1.x para mostrar un tamaño mayor)</span><span class="sxs-lookup"><span data-stu-id="15f31-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="15f31-226">**Frecuencia de crecimiento lejano:** la velocidad de escala de un objeto escalado por proximidad se escala cuando la mano se mueve de proximidad media a lejana.</span><span class="sxs-lookup"><span data-stu-id="15f31-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="15f31-227">**Tasa de crecimiento medio:** la velocidad de escala de un objeto escalado de proximidad se escala cuando la mano se mueve de proximidad media a cercana.</span><span class="sxs-lookup"><span data-stu-id="15f31-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="15f31-228">**Close Grow Rate**(Velocidad de crecimiento de cierre): la velocidad de escalado de un objeto con escala de proximidad se escala cuando la mano pasa de una proximidad cercana al centro de objetos.</span><span class="sxs-lookup"><span data-stu-id="15f31-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="15f31-229">Sistema de restricciones</span><span class="sxs-lookup"><span data-stu-id="15f31-229">Constraint System</span></span>

<span data-ttu-id="15f31-230">El control de límites admite el uso del [administrador de](constraint-manager.md) restricciones para limitar o modificar el comportamiento de traducción, rotación o escalado mientras se usan identificadores de control de límites.</span><span class="sxs-lookup"><span data-stu-id="15f31-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="15f31-231">El inspector de propiedades mostrará todos los administradores de restricciones disponibles asociados al mismo objeto de juego en una lista desplegable con una opción para desplazarse y resaltar el administrador de restricciones seleccionado.</span><span class="sxs-lookup"><span data-stu-id="15f31-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="15f31-232">Events</span><span class="sxs-lookup"><span data-stu-id="15f31-232">Events</span></span>

<span data-ttu-id="15f31-233">El control Bounds proporciona los siguientes eventos.</span><span class="sxs-lookup"><span data-stu-id="15f31-233">Bounds control provides the following events.</span></span> <span data-ttu-id="15f31-234">En este ejemplo se usan estos eventos para reproducir comentarios de audio.</span><span class="sxs-lookup"><span data-stu-id="15f31-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="15f31-235">**Girar iniciado:** se desencadena cuando se inicia la rotación.</span><span class="sxs-lookup"><span data-stu-id="15f31-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="15f31-236">**Girar detenido:** se desencadena cuando se detiene la rotación.</span><span class="sxs-lookup"><span data-stu-id="15f31-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="15f31-237">**Escalado iniciado:** se inicia cuando se inicia el escalado.</span><span class="sxs-lookup"><span data-stu-id="15f31-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="15f31-238">**Escala detenida:** se produce cuando se detiene el escalado.</span><span class="sxs-lookup"><span data-stu-id="15f31-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="15f31-239">**Translate Started**: se inicia cuando se inicia la traducción.</span><span class="sxs-lookup"><span data-stu-id="15f31-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="15f31-240">Translate Stopped ( **Traducción detenida):** se desasozca cuando se detenga la traducción.</span><span class="sxs-lookup"><span data-stu-id="15f31-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="15f31-241">Elásticos (experimentales)</span><span class="sxs-lookup"><span data-stu-id="15f31-241">Elastics (Experimental)</span></span>

<span data-ttu-id="15f31-242">Los elásticos se pueden usar al manipular objetos a través del control de límites.</span><span class="sxs-lookup"><span data-stu-id="15f31-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="15f31-243">Tenga en cuenta que [el sistema elástico](../elastics/elastic-system.md) sigue en estado experimental.</span><span class="sxs-lookup"><span data-stu-id="15f31-243">Note that the [elastics system](../elastics/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="15f31-244">Para habilitar los elásticos, vincule un componente de administrador elástico existente o cree y vincule un nuevo administrador de elásticos mediante el `Add Elastics Manager` botón .</span><span class="sxs-lookup"><span data-stu-id="15f31-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="15f31-245">Estilos de control</span><span class="sxs-lookup"><span data-stu-id="15f31-245">Handle styles</span></span>

<span data-ttu-id="15f31-246">De forma predeterminada, al asignar el script, se mostrará el identificador del estilo de [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 1.ª generación de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15f31-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="15f31-247">Para usar HoloLens 2 estilo, debe asignar prefabs y materiales de identificador adecuados.</span><span class="sxs-lookup"><span data-stu-id="15f31-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Estilos de identificador de control de límites 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="15f31-249">A continuación se muestran los requisitos previos, los materiales y los valores de escalado para los identificadores HoloLens 2 control de límites de estilo.</span><span class="sxs-lookup"><span data-stu-id="15f31-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="15f31-250">Puede encontrar este ejemplo en la `BoundsControlExamples` escena.</span><span class="sxs-lookup"><span data-stu-id="15f31-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="15f31-251">Identificadores (configuración para HoloLens 2 estilo)</span><span class="sxs-lookup"><span data-stu-id="15f31-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="15f31-252">**Material de** identificador: BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="15f31-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="15f31-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="15f31-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="15f31-254">**Prefab del identificador de** escala: MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="15f31-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="15f31-255">**Prefab de pizarra del** controlador de escala: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="15f31-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="15f31-256">**Tamaño del identificador de** escala: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="15f31-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="15f31-257">**Relleno del colisionador** del controlador de escala: 0,016 (hace que el colisionador que se puede agarrar sea ligeramente mayor que el objeto visual del controlador)</span><span class="sxs-lookup"><span data-stu-id="15f31-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="15f31-258">**Prefab de** identificador de rotación: MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="15f31-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="15f31-259">**Tamaño del identificador de** rotación: 0,016</span><span class="sxs-lookup"><span data-stu-id="15f31-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="15f31-260">**Relleno del colisionador del** controlador de rotación: 0,016 (hace que el colisionador que se puede agarrar sea ligeramente mayor que el objeto visual del controlador)</span><span class="sxs-lookup"><span data-stu-id="15f31-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="15f31-261">Cambios de transformación con manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="15f31-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="15f31-262">Un control de límites se puede usar en combinación con [`ObjectManipulator.cs`](object-manipulator.md) para permitir ciertos tipos de manipulación (por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="15f31-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="15f31-263">mover el objeto ) sin usar identificadores.</span><span class="sxs-lookup"><span data-stu-id="15f31-263">moving the object) without using handles.</span></span> <span data-ttu-id="15f31-264">El controlador de manipulación admite interacciones de una y dos manos.</span><span class="sxs-lookup"><span data-stu-id="15f31-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="15f31-265">[El seguimiento](../input/hand-tracking.md) de manos se puede usar para interactuar con un objeto de cerca.</span><span class="sxs-lookup"><span data-stu-id="15f31-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="15f31-266">Para que los bordes del control de límites se comporten de la misma manera al moverlo mediante la interacción lejana, se recomienda conectar sus eventos para On Manipulation Started On Manipulation Ended (Al manipular iniciada al finalizar la manipulación) a respectivamente, como se muestra en la captura de pantalla [`ObjectManipulator`](object-manipulator.md)   /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` anterior.</span><span class="sxs-lookup"><span data-stu-id="15f31-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="15f31-267">Adición y configuración de un control de límites mediante Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="15f31-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="15f31-268">Agregar Box Collider a un objeto</span><span class="sxs-lookup"><span data-stu-id="15f31-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="15f31-269">Asignación `BoundsControl` de un script a un objeto</span><span class="sxs-lookup"><span data-stu-id="15f31-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="15f31-270">Configurar opciones, como los métodos de activación (consulte la [sección Propiedades del inspector](#inspector-properties) a continuación)</span><span class="sxs-lookup"><span data-stu-id="15f31-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="15f31-271">(Opcional) Asignación de prefabs y materiales para un control HoloLens 2 de estilo (consulte [la](#handle-styles) sección Estilos de control a continuación)</span><span class="sxs-lookup"><span data-stu-id="15f31-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="15f31-272">Use *el campo Target Object* (Objeto de destino) y Bounds Override (Invalidación de *límites)* en el inspector para asignar un objeto específico y un colisionador en el objeto con varios componentes secundarios.</span><span class="sxs-lookup"><span data-stu-id="15f31-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Control de límites](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="15f31-274">Adición y configuración de un control de límites en el código</span><span class="sxs-lookup"><span data-stu-id="15f31-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="15f31-275">Creación de instancias de GameObject de cubo</span><span class="sxs-lookup"><span data-stu-id="15f31-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="15f31-276">Asignación `BoundsControl` de un script a un objeto con colisionador mediante AddComponent<>()</span><span class="sxs-lookup"><span data-stu-id="15f31-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="15f31-277">Configure las opciones directamente en el control o a través de una de las configuraciones que se pueden incluir en scripts (consulte la [sección Propiedades](#inspector-properties) y [configuraciones del](#configuration-objects) inspector a continuación).</span><span class="sxs-lookup"><span data-stu-id="15f31-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="15f31-278">(Opcional) Asigne prefabs y materiales para un control HoloLens 2 de estilo.</span><span class="sxs-lookup"><span data-stu-id="15f31-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="15f31-279">Esto todavía requiere asignaciones a través del inspector, ya que los materiales y objetos prefabs deben cargarse dinámicamente.</span><span class="sxs-lookup"><span data-stu-id="15f31-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="15f31-280">No se recomienda usar la carpeta "Resources" de Unity o [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) para cargar sombreadores dinámicamente, ya que es posible que falte permutaciones del sombreador en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="15f31-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="15f31-281">Ejemplo: Establecer la escala de control de límites mínimos y máximos mediante MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="15f31-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="15f31-282">Para establecer la escala mínima y máxima, adjunte un al [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) control .</span><span class="sxs-lookup"><span data-stu-id="15f31-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="15f31-283">A medida que el control de límites asocia y activa automáticamente el administrador de restricciones, MinMaxScaleConstraint se aplicará automáticamente a los cambios de transformación una vez asociado y configurado.</span><span class="sxs-lookup"><span data-stu-id="15f31-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="15f31-284">También puede usar MinMaxScaleConstraint para establecer la escala mínima y máxima para [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .</span><span class="sxs-lookup"><span data-stu-id="15f31-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="15f31-285">Ejemplo: Agregar control de límites alrededor de un objeto de juego</span><span class="sxs-lookup"><span data-stu-id="15f31-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="15f31-286">Para agregar un control de límites alrededor de un objeto, basta con agregarle `BoundsControl` un componente:</span><span class="sxs-lookup"><span data-stu-id="15f31-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="15f31-287">Migración desde el rectángulo de selección</span><span class="sxs-lookup"><span data-stu-id="15f31-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="15f31-288">Las instancias y los requisitos previos existentes mediante el cuadro [](../tools/migration-window.md) de límite se pueden actualizar al nuevo control de límites a través de la ventana de migración que forma parte del paquete de herramientas de MRTK. [](bounding-box.md)</span><span class="sxs-lookup"><span data-stu-id="15f31-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="15f31-289">Para actualizar instancias individuales del rectángulo de selección, también hay una opción de migración dentro del inspector de propiedades del componente.</span><span class="sxs-lookup"><span data-stu-id="15f31-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="15f31-290">Vea también</span><span class="sxs-lookup"><span data-stu-id="15f31-290">See also</span></span>

* [<span data-ttu-id="15f31-291">Manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="15f31-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="15f31-292">Administrador de restricciones</span><span class="sxs-lookup"><span data-stu-id="15f31-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="15f31-293">El plazo de migración</span><span class="sxs-lookup"><span data-stu-id="15f31-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="15f31-294">Sistema elástico (experimental)</span><span class="sxs-lookup"><span data-stu-id="15f31-294">Elastics system (Experimental)</span></span>](../elastics/elastic-system.md)
