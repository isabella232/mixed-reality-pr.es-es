---
title: Configuración de observadores de malla para el dispositivo
description: Configuración del observador de malla espacial lista para usar en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281933"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="d4aa6-104">Configuración de observadores de malla para el dispositivo</span><span class="sxs-lookup"><span data-stu-id="d4aa6-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="d4aa6-105">Esta guía le guiará a través de la configuración del observador de malla espacial integrada en MRTK que admite la plataforma Windows Mixed Reality (es decir,</span><span class="sxs-lookup"><span data-stu-id="d4aa6-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="d4aa6-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="d4aa6-106">HoloLens).</span></span> <span data-ttu-id="d4aa6-107">La implementación predeterminada proporcionada por el Mixed Reality Toolkit es [la clase WindowsMixedRealitySpatialMeshObserver.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="d4aa6-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="d4aa6-108">Muchas de las propiedades de este artículo se aplican a [otras implementaciones de Observer personalizadas.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="d4aa6-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="d4aa6-109">Configuración del perfil</span><span class="sxs-lookup"><span data-stu-id="d4aa6-109">Profile settings</span></span>

<span data-ttu-id="d4aa6-110">Los dos elementos siguientes deben definirse primero al configurar un perfil de observador de malla espacial para el [sistema de reconocimiento espacial](spatial-awareness-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="d4aa6-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="d4aa6-111">Implementación concreta del tipo de observador</span><span class="sxs-lookup"><span data-stu-id="d4aa6-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="d4aa6-112">lista de plataformas admitidas para ejecutar este observador</span><span class="sxs-lookup"><span data-stu-id="d4aa6-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="d4aa6-113">Todos los observadores deben extender la [interfaz IMixedRealitySpatialAwarenessObserver.](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)</span><span class="sxs-lookup"><span data-stu-id="d4aa6-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Tipos de plataforma de Configuración observador de malla](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="d4aa6-115">Configuración general</span><span class="sxs-lookup"><span data-stu-id="d4aa6-115">General settings</span></span>

![Configuración general del Configuración mesh observer](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="d4aa6-117">**Comportamiento de inicio**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-117">**Startup Behavior**</span></span>

<span data-ttu-id="d4aa6-118">El comportamiento de inicio especifica si el observador comenzará a ejecutarse cuando se cree una instancia por primera vez.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="d4aa6-119">Las dos opciones son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="d4aa6-119">The two options are:</span></span>

* <span data-ttu-id="d4aa6-120">*Inicio automático:* el valor predeterminado por el que el observador iniciará la operación después de la inicialización.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="d4aa6-121">*Inicio manual:* el observador esperará a que se le dirija para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="d4aa6-122">Si usa *Inicio manual*, debe [reanudarlos y suspenderlos en tiempo de ejecución a través del código](usage-guide.md#starting-and-stopping-mesh-observation).</span><span class="sxs-lookup"><span data-stu-id="d4aa6-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="d4aa6-123">**Intervalo de actualización**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-123">**Update Interval**</span></span>

<span data-ttu-id="d4aa6-124">Tiempo, en segundos, entre las solicitudes a la plataforma para actualizar los datos de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="d4aa6-125">Los valores típicos se encuentra en el intervalo de 0,1 y 5,0 segundos.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="d4aa6-126">**Is Stationary Observer**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="d4aa6-127">Indica si el observador debe permanecer o no estacionados o si se va a mover y actualizar con el usuario.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="d4aa6-128">Si es true, *la forma observador con* el volumen definido por Extensiones *de* observación permanecerá en el origen en el inicio.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="d4aa6-129">Si es false, el espacio Observador seguirá la cabeza del usuario como origen de la forma.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="d4aa6-130">No se calcularán datos de malla para ningún área física fuera del espacio de observador tal como se define en estas propiedades: *Is Stationary Observer*, *Observer Shape*\* y *Observation Extents*.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="d4aa6-131">**Forma de observador**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-131">**Observer Shape**</span></span>

<span data-ttu-id="d4aa6-132">La forma de observador define el tipo de volumen que usará el observador de malla al observar mallas.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="d4aa6-133">Las opciones admitidas son:</span><span class="sxs-lookup"><span data-stu-id="d4aa6-133">The supported options are:</span></span>

* <span data-ttu-id="d4aa6-134">*Cubo alineado del eje:* forma rectangular que permanece alineada con los ejes del sistema de coordenadas mundial, como se determina en el inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="d4aa6-135">*Cubo alineado por el usuario:* forma rectangular que gira para alinearse con el sistema de coordenadas local de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="d4aa6-136">*Sphere:* volumen esférico con un centro en el origen del espacio mundial.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="d4aa6-137">El valor X de la *propiedad Observation Extents* se usará como radio de la esfera.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="d4aa6-138">**Extensiones de observación**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-138">**Observation Extents**</span></span>

<span data-ttu-id="d4aa6-139">Las extensiones de observación definen la distancia desde el punto de observación que se observarán las mallas.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="d4aa6-140">Configuración física</span><span class="sxs-lookup"><span data-stu-id="d4aa6-140">Physics settings</span></span>

![Mesh Observer Physics Configuración](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="d4aa6-142">**Capa de física**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-142">**Physics Layer**</span></span>

<span data-ttu-id="d4aa6-143">Capa física en la que se colocarán los objetos de malla espacial para interactuar con los sistemas Unity Physics y RayCast.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="d4aa6-144">El Mixed Reality Toolkit reserva la *capa 31* de forma predeterminada para que la usen los observadores de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="d4aa6-145">**Recalcular normales**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-145">**Recalculate Normals**</span></span>

<span data-ttu-id="d4aa6-146">Especifica si el observador de malla recalculará o no las normales de la malla después de la observación.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="d4aa6-147">Esta configuración está disponible para garantizar que las aplicaciones reciben mallas que contienen datos normales válidos en plataformas que no las devuelven con mallas.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="d4aa6-148">Configuración de nivel de detalle</span><span class="sxs-lookup"><span data-stu-id="d4aa6-148">Level of detail settings</span></span>

![Nivel de detalle del observador de malla Configuración](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="d4aa6-150">**Nivel de detalle**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-150">**Level of Detail**</span></span>

<span data-ttu-id="d4aa6-151">Especifica el nivel de detalle (LOD) de los datos de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="d4aa6-152">Los valores definidos actualmente son General, Fine y Custom.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="d4aa6-153">*General: coloca* un impacto menor en el rendimiento de la aplicación y es una excelente opción para la navegación y la búsqueda de plano.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="d4aa6-154">*Medio:* la configuración equilibrada suele ser útil para experiencias que analizan continuamente el entorno en busca de características grandes, plantas y paredes, así como detalles de oclusión.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="d4aa6-155">*Bien:* por lo general, tiene un mayor impacto en el rendimiento de la aplicación y es una excelente opción para las mallas de oclusión.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="d4aa6-156">*Personalizado:* requiere que la aplicación especifique la propiedad *Triangles/Cubic Meter* y permite a las aplicaciones ajustar la precisión frente al impacto en el rendimiento del observador de malla espacial.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="d4aa6-157">No se garantiza que todas las plataformas respetan todos los valores *triángulos o* medidores cúbicos.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="d4aa6-158">Se recomienda encarecidamente la experimentación y la generación de perfiles cuando se usa un LOD personalizado.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="d4aa6-159">**Triángulos por medidor cúbica**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="d4aa6-160">Válido cuando se usa *el valor* Personalizado para la **propiedad Nivel** de detalle y especifica la densidad del triángulo para la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="d4aa6-161">Configuración de pantalla</span><span class="sxs-lookup"><span data-stu-id="d4aa6-161">Display settings</span></span>

![Pantalla de observador de malla Configuración](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="d4aa6-163">**Opción mostrar**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-163">**Display Option**</span></span>

<span data-ttu-id="d4aa6-164">Especifica cómo el observador va a mostrar las mallas espaciales.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="d4aa6-165">Los valores admitidos son:</span><span class="sxs-lookup"><span data-stu-id="d4aa6-165">Supported values are:</span></span>

* <span data-ttu-id="d4aa6-166">*Ninguno:* el observador no representará la malla</span><span class="sxs-lookup"><span data-stu-id="d4aa6-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="d4aa6-167">*Visible:* los datos de malla estarán visibles mediante *el material visible*</span><span class="sxs-lookup"><span data-stu-id="d4aa6-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="d4aa6-168">*Oclusión:* los datos de malla serán elementos occluir en la escena mediante el *material de oclusión*</span><span class="sxs-lookup"><span data-stu-id="d4aa6-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![Selección de la implementación del sistema de reconocimiento espacial](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="d4aa6-170">Los observadores espaciales se [pueden reanudar o suspender en tiempo de ejecución mediante código.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="d4aa6-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="d4aa6-171">Establecer *Opción de visualización* en *Ninguno* NO **detiene** la ejecución del observador.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="d4aa6-172">Si desea detener todos los observadores, las aplicaciones tendrán que suspender todos los observadores a través de [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="d4aa6-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="d4aa6-173">**Visible Material**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-173">**Visible Material**</span></span>

<span data-ttu-id="d4aa6-174">Indica el material que se va a usar al visualizar la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="d4aa6-175">**Material de oclusión**</span><span class="sxs-lookup"><span data-stu-id="d4aa6-175">**Occlusion Material**</span></span>

<span data-ttu-id="d4aa6-176">Indica el material que se va a usar para hacer que la malla espacial occlude hologramas.</span><span class="sxs-lookup"><span data-stu-id="d4aa6-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4aa6-177">Vea también</span><span class="sxs-lookup"><span data-stu-id="d4aa6-177">See also</span></span>

* [<span data-ttu-id="d4aa6-178">Sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="d4aa6-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="d4aa6-179">Configuración del sistema de reconocimiento espacial mediante código</span><span class="sxs-lookup"><span data-stu-id="d4aa6-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="d4aa6-180">Documentación de la API IMixedRealitySpatialAwarenessObserver</span><span class="sxs-lookup"><span data-stu-id="d4aa6-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="d4aa6-181">Documentación de la API IMixedRealitySpatialAwarenessMeshObserver</span><span class="sxs-lookup"><span data-stu-id="d4aa6-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="d4aa6-182">Documentación de la API BaseSpatialObserver</span><span class="sxs-lookup"><span data-stu-id="d4aa6-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
