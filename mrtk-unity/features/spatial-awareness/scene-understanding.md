---
title: Descripción de la escena
description: describe Scene Understanding in MRTK (Descripción de la escena en MRTK)
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Scene Understanding
ms.openlocfilehash: 1ed6f93216fc90e7c6332f2b9c40911d25d96d2a
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743552"
---
# <a name="scene-understanding"></a><span data-ttu-id="8f271-104">Descripción de la escena</span><span class="sxs-lookup"><span data-stu-id="8f271-104">Scene Understanding</span></span>

<span data-ttu-id="8f271-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) devuelve una representación semántica de entidades de escena, así como sus formas geométricas __en HoloLens 2__ (no se admite HoloLens 1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="8f271-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="8f271-106">Algunos casos de uso esperados de esta tecnología son:</span><span class="sxs-lookup"><span data-stu-id="8f271-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="8f271-107">Colocar objetos en la superficie más cercana de un tipo determinado (por ejemplo, la pared y el suelo)</span><span class="sxs-lookup"><span data-stu-id="8f271-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="8f271-108">Construcción de malla de navegación para juegos de estilo de plataforma</span><span class="sxs-lookup"><span data-stu-id="8f271-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="8f271-109">Proporcionar geometría fácil de usar en el motor físico como quads</span><span class="sxs-lookup"><span data-stu-id="8f271-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="8f271-110">Acelerar el desarrollo evitando la necesidad de escribir algoritmos similares</span><span class="sxs-lookup"><span data-stu-id="8f271-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="8f271-111">Scene Understanding se presenta como una __característica experimental__ en MRTK 2.6.</span><span class="sxs-lookup"><span data-stu-id="8f271-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="8f271-112">Se integra en MRTK como un [observador espacial](spatial-awareness-getting-started.md#register-observers) denominado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="8f271-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="8f271-113">Scene Understanding funciona tanto con la canalización de XR heredada como con la canalización del SDK de XR (tanto OpenXR (a partir de MRTK 2.7) como con el complemento XR de Windows.</span><span class="sxs-lookup"><span data-stu-id="8f271-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="8f271-114">En ambos casos `WindowsSceneUnderstandingObserver` se usa .</span><span class="sxs-lookup"><span data-stu-id="8f271-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="8f271-115">No se admite el uso de Scene Understanding in Remoting.</span><span class="sxs-lookup"><span data-stu-id="8f271-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="8f271-116">Información general del observador</span><span class="sxs-lookup"><span data-stu-id="8f271-116">Observer overview</span></span>

<span data-ttu-id="8f271-117">Cuando se le pregunte, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) devolverá [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con atributos útiles para que la aplicación comprenda su entorno.</span><span class="sxs-lookup"><span data-stu-id="8f271-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="8f271-118">La frecuencia de observación, el tipo de objeto devuelto (por ejemplo, la pared, el suelo) y otros comportamientos del observador dependen de la configuración del observador a través del perfil.</span><span class="sxs-lookup"><span data-stu-id="8f271-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="8f271-119">Por ejemplo, si se desea la máscara de oclusión, el observador debe configurarse para generar quads.</span><span class="sxs-lookup"><span data-stu-id="8f271-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="8f271-120">La escena observada se puede guardar como archivo serializado que se puede cargar más adelante para volver a crear la escena en modo de reproducción del editor.</span><span class="sxs-lookup"><span data-stu-id="8f271-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="8f271-121">Configurar</span><span class="sxs-lookup"><span data-stu-id="8f271-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f271-122">Scene Understanding solo se admite en HoloLens 2 y Unity 2019.4 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="8f271-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="8f271-123">Asegúrese de que la plataforma está establecida en UWP en la configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="8f271-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="8f271-124">Adquiera el paquete Scene Understanding a través [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="8f271-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="8f271-125">Uso de Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="8f271-125">Using Scene Understanding</span></span>

<span data-ttu-id="8f271-126">La manera más rápida de empezar a trabajar con Scene Understanding es consultar la escena de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="8f271-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="8f271-127">Escena de ejemplo de Descripción de la escena</span><span class="sxs-lookup"><span data-stu-id="8f271-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="8f271-128">En Unity, use el Explorador de proyectos para abrir el archivo de escena en `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` y presione reproducir.</span><span class="sxs-lookup"><span data-stu-id="8f271-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="8f271-129">Solo se aplica a MRTK 2.6.0: al usar la herramienta de características de Mixed Reality o importar de otro modo a través de UPM, importe el ejemplo Demos - SpatialAwareness antes de importar el ejemplo Experimental - SceneUnderstanding debido a un problema de dependencia.</span><span class="sxs-lookup"><span data-stu-id="8f271-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="8f271-130">Consulte este [problema de GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="8f271-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="8f271-131">En la escena se muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8f271-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="8f271-132">Visualización de objetos de escena observados con en la interfaz de usuario de la aplicación para configurar el observador</span><span class="sxs-lookup"><span data-stu-id="8f271-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="8f271-133">Script `DemoSceneUnderstandingController` de ejemplo que muestra cómo cambiar la configuración del observador y escuchar los eventos pertinentes</span><span class="sxs-lookup"><span data-stu-id="8f271-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="8f271-134">Guardar datos de escena en el dispositivo para el desarrollo sin conexión</span><span class="sxs-lookup"><span data-stu-id="8f271-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="8f271-135">Carga de datos de escena previamente guardados (archivos .bytes) para admitir el flujo de trabajo de desarrollo en el editor</span><span class="sxs-lookup"><span data-stu-id="8f271-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f271-136">De forma `ShouldLoadFromFile` predeterminada, la propiedad del observador se establece en false.</span><span class="sxs-lookup"><span data-stu-id="8f271-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="8f271-137">Para ver la visualización de una sala de ejemplo serializada, consulte la sección configuración del servicio [de](#configuring-the-observer-service) observador a continuación y establezca la propiedad en true en el editor.</span><span class="sxs-lookup"><span data-stu-id="8f271-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="8f271-138">La escena de ejemplo se basa en la canalización XR heredada.</span><span class="sxs-lookup"><span data-stu-id="8f271-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="8f271-139">Si usa la canalización del SDK de XR, debe modificar los perfiles en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="8f271-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="8f271-140">El perfil del sistema de reconocimiento espacial de Scene Understanding proporcionado ( ) y los perfiles de observador de `DemoSceneUnderstandingSystemProfile` Scene Understanding ( y ) funcionan para ambas `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="8f271-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="8f271-141">La escena de ejemplo registra una `There is no active AsyncCoroutineRunner when an action is posted.` advertencia en determinadas circunstancias debido al orden de ejecución de inicialización o subproceso.</span><span class="sxs-lookup"><span data-stu-id="8f271-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="8f271-142">Si puede confirmar que el componente está asociado al GameObject "Demo Controller" y el componente/GameObject permanece habilitado o activo en la escena (el caso predeterminado), la advertencia se puede omitir de forma `AsyncCoroutineRunner` segura.</span><span class="sxs-lookup"><span data-stu-id="8f271-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="8f271-143">Configuración del servicio de observador</span><span class="sxs-lookup"><span data-stu-id="8f271-143">Configuring the observer service</span></span>

<span data-ttu-id="8f271-144">Seleccione el objeto de juego "MixedRealityToolkit" y compruebe el inspector.</span><span class="sxs-lookup"><span data-stu-id="8f271-144">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![descripción de la ubicación de la escena en la jerarquía](../images/spatial-awareness/MRTKHierarchy.png)

![Ubicación de MRTK en inspector](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="8f271-147">Estas opciones permitirán que se configure `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="8f271-147">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="8f271-148">Script de ejemplo</span><span class="sxs-lookup"><span data-stu-id="8f271-148">Example script</span></span>

<span data-ttu-id="8f271-149">El script de _ejemplo DemoSceneUnderstandingController.cs_ muestra los conceptos principales para trabajar con el servicio Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="8f271-149">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="8f271-150">Suscripción a eventos de Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="8f271-150">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="8f271-151">Control de eventos de Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="8f271-151">Handling Scene Understanding events</span></span>
* <span data-ttu-id="8f271-152">Configuración de en `WindowsSceneUnderstandingObserver` tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="8f271-152">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="8f271-153">Los alternancias del panel de la escena cambian el comportamiento del observador de comprensión de la escena mediante una llamada a las funciones públicas de este script de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="8f271-153">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="8f271-154">Al activar Crear instancias *prefabs*, se mostrará la creación de objetos de ese tamaño para ajustarse a todos [los objetos SpatialAwarenessSceneObject,](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)recopilados perfectamente bajo un objeto primario.</span><span class="sxs-lookup"><span data-stu-id="8f271-154">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![opciones del controlador de demostración](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="8f271-156">Notas de la aplicación creada</span><span class="sxs-lookup"><span data-stu-id="8f271-156">Built app notes</span></span>

<span data-ttu-id="8f271-157">Compile e implemente en HoloLens de la manera estándar.</span><span class="sxs-lookup"><span data-stu-id="8f271-157">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="8f271-158">Una vez en ejecución, debería aparecer una serie de botones para reproducir con las características.</span><span class="sxs-lookup"><span data-stu-id="8f271-158">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="8f271-159">Tenga en cuenta que hay algunas dificultades en la realización de consultas al observador.</span><span class="sxs-lookup"><span data-stu-id="8f271-159">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="8f271-160">La configuración incorrecta de una solicitud de captura hace que la carga del evento no contenga los datos esperados.</span><span class="sxs-lookup"><span data-stu-id="8f271-160">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="8f271-161">Por ejemplo, si no se solicitan quads, no habrá texturas de máscara de oclusión.</span><span class="sxs-lookup"><span data-stu-id="8f271-161">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="8f271-162">Como es aconsejable, no aparecerá ninguna malla del mundo si el observador no está configurado para solicitar mallas.</span><span class="sxs-lookup"><span data-stu-id="8f271-162">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="8f271-163">El `DemoSceneUnderstandingController` script se encarga de algunas de estas dependencias, pero no de todas.</span><span class="sxs-lookup"><span data-stu-id="8f271-163">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="8f271-164">Se puede acceder a los archivos de escena guardados a través del [portal del dispositivo](/windows/mixed-reality/using-the-windows-device-portal) en `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="8f271-164">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="8f271-165">Estos archivos de escena se pueden usar en el editor si se especifican en el perfil de observador que se encuentra en el inspector.</span><span class="sxs-lookup"><span data-stu-id="8f271-165">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Portal de dispositivos ubicación del archivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de escena serializados en el observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="8f271-168">Consulte también</span><span class="sxs-lookup"><span data-stu-id="8f271-168">See Also</span></span>

* [<span data-ttu-id="8f271-169">Información general de Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="8f271-169">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="8f271-170">Introducción al SDK de Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="8f271-170">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)