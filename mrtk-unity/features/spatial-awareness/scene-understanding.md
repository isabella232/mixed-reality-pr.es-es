---
title: Descripción de la escena
description: describe Scene Understanding in MRTK (Descripción de la escena en MRTK)
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Scene Understanding
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143883"
---
# <a name="scene-understanding"></a><span data-ttu-id="b001e-104">Descripción de la escena</span><span class="sxs-lookup"><span data-stu-id="b001e-104">Scene Understanding</span></span>

<span data-ttu-id="b001e-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) devuelve una representación semántica de entidades de escena, así como sus formas geométricas en __HoloLens 2__ (no se admite HoloLens 1st Gen).</span><span class="sxs-lookup"><span data-stu-id="b001e-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="b001e-106">Algunos casos de uso esperados de esta tecnología son:</span><span class="sxs-lookup"><span data-stu-id="b001e-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="b001e-107">Colocar objetos en la superficie más cercana de un tipo determinado (por ejemplo, la pared y el suelo)</span><span class="sxs-lookup"><span data-stu-id="b001e-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="b001e-108">Construcción de una malla de navegación para juegos de estilo de plataforma</span><span class="sxs-lookup"><span data-stu-id="b001e-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="b001e-109">Proporcionar geometría fácil de usar en el motor físico como cuadrándes</span><span class="sxs-lookup"><span data-stu-id="b001e-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="b001e-110">Acelerar el desarrollo evitando la necesidad de escribir algoritmos similares</span><span class="sxs-lookup"><span data-stu-id="b001e-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="b001e-111">Scene Understanding está disponible como una __característica experimental__ a partir de MRTK 2.6.</span><span class="sxs-lookup"><span data-stu-id="b001e-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="b001e-112">Se integra en MRTK como un [observador espacial](spatial-awareness-getting-started.md#register-observers) denominado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="b001e-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="b001e-113">Scene Understanding funciona tanto con la canalización XR heredada como con la canalización del SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="b001e-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="b001e-114">En ambos casos `WindowsSceneUnderstandingObserver` se usa .</span><span class="sxs-lookup"><span data-stu-id="b001e-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="b001e-115">Información general del observador</span><span class="sxs-lookup"><span data-stu-id="b001e-115">Observer overview</span></span>

<span data-ttu-id="b001e-116">Cuando se le pregunte, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) devolverá [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con atributos útiles para que la aplicación comprenda su entorno.</span><span class="sxs-lookup"><span data-stu-id="b001e-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="b001e-117">La frecuencia de observación, el tipo de objeto devuelto (por ejemplo, la pared, el suelo) y otros comportamientos del observador dependen de la configuración del observador a través del perfil.</span><span class="sxs-lookup"><span data-stu-id="b001e-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="b001e-118">Por ejemplo, si se desea la máscara de oclusión, el observador debe configurarse para generar quads.</span><span class="sxs-lookup"><span data-stu-id="b001e-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="b001e-119">La escena observada se puede guardar como archivo serializado que se puede cargar más adelante para volver a crear la escena en modo de reproducción del editor.</span><span class="sxs-lookup"><span data-stu-id="b001e-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="b001e-120">Configurar</span><span class="sxs-lookup"><span data-stu-id="b001e-120">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b001e-121">Scene Understanding solo se admite en HoloLens 2 y Unity 2019.4 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b001e-121">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="b001e-122">Asegúrese de que la plataforma está establecida en UWP en la configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="b001e-122">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="b001e-123">Adquiera el paquete Scene Understanding a través [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="b001e-123">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="b001e-124">Uso de Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="b001e-124">Using Scene Understanding</span></span>

<span data-ttu-id="b001e-125">La manera más rápida de empezar a trabajar con Scene Understanding es consultar la escena de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="b001e-125">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="b001e-126">Escena de ejemplo de Descripción de la escena</span><span class="sxs-lookup"><span data-stu-id="b001e-126">Scene Understanding sample scene</span></span>

<span data-ttu-id="b001e-127">En Unity, use el Explorador de proyectos para abrir el archivo de escena en `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` y presione reproducir.</span><span class="sxs-lookup"><span data-stu-id="b001e-127">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b001e-128">Al usar la herramienta de características Mixed Reality o importar de otro modo a través de UPM, importe el ejemplo Demos - SpatialAwareness antes de importar el ejemplo Experimental - SceneUnderstanding debido a un problema de dependencia.</span><span class="sxs-lookup"><span data-stu-id="b001e-128">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="b001e-129">Consulte este [problema de GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="b001e-129">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

<span data-ttu-id="b001e-130">En la escena se muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b001e-130">The scene demonstrates the following:</span></span>

* <span data-ttu-id="b001e-131">Visualización de objetos de escena observados con en la interfaz de usuario de la aplicación para configurar el observador</span><span class="sxs-lookup"><span data-stu-id="b001e-131">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="b001e-132">Script `DemoSceneUnderstandingController` de ejemplo que muestra cómo cambiar la configuración del observador y escuchar los eventos pertinentes</span><span class="sxs-lookup"><span data-stu-id="b001e-132">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="b001e-133">Guardar datos de escena en el dispositivo para el desarrollo sin conexión</span><span class="sxs-lookup"><span data-stu-id="b001e-133">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="b001e-134">Carga de datos de escena previamente guardados (archivos .bytes) para admitir el flujo de trabajo de desarrollo en el editor</span><span class="sxs-lookup"><span data-stu-id="b001e-134">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="b001e-135">La escena de ejemplo se basa en la canalización XR heredada.</span><span class="sxs-lookup"><span data-stu-id="b001e-135">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="b001e-136">Si usa la canalización del SDK de XR, debe modificar los perfiles en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="b001e-136">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="b001e-137">El perfil del sistema de reconocimiento espacial de Scene Understanding proporcionado ( ) y los perfiles de observador de `DemoSceneUnderstandingSystemProfile` Scene Understanding ( y ) funcionan para ambas `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="b001e-137">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="b001e-138">Configuración del servicio de observador</span><span class="sxs-lookup"><span data-stu-id="b001e-138">Configuring the observer service</span></span>

<span data-ttu-id="b001e-139">Seleccione el objeto de juego "MixedRealityToolkit" y compruebe el inspector.</span><span class="sxs-lookup"><span data-stu-id="b001e-139">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![descripción de la ubicación de la escena en la jerarquía](../images/spatial-awareness/MRTKHierarchy.png)

![Ubicación de MRTK en inspector](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="b001e-142">Estas opciones le permitirán configurar `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="b001e-142">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="b001e-143">Script de ejemplo</span><span class="sxs-lookup"><span data-stu-id="b001e-143">Example script</span></span>

<span data-ttu-id="b001e-144">El script de _ejemplo DemoSceneUnderstandingController.cs_ muestra los conceptos principales para trabajar con el servicio Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="b001e-144">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="b001e-145">Suscripción a eventos de Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="b001e-145">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="b001e-146">Control de eventos de Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="b001e-146">Handling Scene Understanding events</span></span>
* <span data-ttu-id="b001e-147">Configuración de en `WindowsSceneUnderstandingObserver` tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="b001e-147">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="b001e-148">Los alternancias en el panel de la escena cambian el comportamiento del observador de comprensión de la escena mediante una llamada a las funciones públicas de este script de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="b001e-148">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="b001e-149">Al activar *Crear instancias prefabs,* se mostrará la creación de objetos de ese tamaño para ajustarse a todos los [objetos SpatialAwarenessSceneObject,](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)recopilados perfectamente debajo de un objeto primario.</span><span class="sxs-lookup"><span data-stu-id="b001e-149">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![Opciones del controlador de demostración](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="b001e-151">Notas de la aplicación integrada</span><span class="sxs-lookup"><span data-stu-id="b001e-151">Built app notes</span></span>

<span data-ttu-id="b001e-152">Compile e implemente en HoloLens de la manera estándar.</span><span class="sxs-lookup"><span data-stu-id="b001e-152">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="b001e-153">Una vez en ejecución, debería aparecer una serie de botones para reproducir con las características.</span><span class="sxs-lookup"><span data-stu-id="b001e-153">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="b001e-154">Tenga en cuenta que hay algunas dificultades en la realización de consultas al observador.</span><span class="sxs-lookup"><span data-stu-id="b001e-154">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="b001e-155">La configuración incorrecta de una solicitud de captura hace que la carga del evento no contenga los datos esperados.</span><span class="sxs-lookup"><span data-stu-id="b001e-155">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="b001e-156">Por ejemplo, si no se solicitan cuatros, no habrá texturas de máscara de oclusión.</span><span class="sxs-lookup"><span data-stu-id="b001e-156">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="b001e-157">Como es aconsejable, no aparecerá ninguna malla de mundo si el observador no está configurado para solicitar mallas.</span><span class="sxs-lookup"><span data-stu-id="b001e-157">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="b001e-158">El `DemoSceneUnderstandingController` script se encarga de algunas de estas dependencias, pero no todas.</span><span class="sxs-lookup"><span data-stu-id="b001e-158">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="b001e-159">Se puede acceder a los archivos de escena guardados a través del [portal del dispositivo](/windows/mixed-reality/using-the-windows-device-portal) en `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="b001e-159">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="b001e-160">Estos archivos de escena se pueden usar en el editor si se especifican en el perfil de observador que se encuentra en el inspector.</span><span class="sxs-lookup"><span data-stu-id="b001e-160">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Portal de dispositivos ubicación del archivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de escena serializados en el observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="b001e-163">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b001e-163">See Also</span></span>

* [<span data-ttu-id="b001e-164">Información general sobre la asignación espacial WMR</span><span class="sxs-lookup"><span data-stu-id="b001e-164">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="b001e-165">Información general sobre la asignación espacial WMR</span><span class="sxs-lookup"><span data-stu-id="b001e-165">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding-sdk)