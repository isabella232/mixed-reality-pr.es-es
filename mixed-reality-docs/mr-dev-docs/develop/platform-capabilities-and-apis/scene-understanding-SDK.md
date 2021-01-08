---
title: SDK de introducción a la escena
description: Obtenga información sobre cómo instalar y usar el SDK de comprensión de escenas, incluidos componentes, mallas y objetos en aplicaciones de realidad mixta.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Comprensión de escenas, asignación espacial, Windows Mixed Reality, Unity
ms.openlocfilehash: 9520ad604125705c60624254b097de5fc93021ec
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009385"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="40a03-104">Información general del SDK de introducción a la escena</span><span class="sxs-lookup"><span data-stu-id="40a03-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="40a03-105">La descripción de la escena transforma los datos del sensor de entorno no estructurado que captura el dispositivo de realidad mixta y los convierte en una representación abstracta eficaz.</span><span class="sxs-lookup"><span data-stu-id="40a03-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="40a03-106">El SDK actúa como la capa de comunicación entre la aplicación y la escena que comprende el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="40a03-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="40a03-107">Está destinado a imitar construcciones estándar existentes, como gráficos de escenas 3D para representaciones 3D, y rectángulos 2D y paneles para aplicaciones 2D.</span><span class="sxs-lookup"><span data-stu-id="40a03-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="40a03-108">Aunque las construcciones que comprenden los imitadores se asignarán a marcos concretos, en general SceneUnderstanding es independiente del marco de trabajo, lo que permite la interoperabilidad entre diversos marcos que interactúan con él.</span><span class="sxs-lookup"><span data-stu-id="40a03-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="40a03-109">A medida que la comprensión de la escena evolucione el rol del SDK, se asegurará de que las nuevas representaciones y capacidades sigan expuestas dentro de un marco unificado.</span><span class="sxs-lookup"><span data-stu-id="40a03-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="40a03-110">En este documento, en primer lugar, introduciremos conceptos de alto nivel que le ayudarán a familiarizarse con el uso o el entorno de desarrollo y, a continuación, proporcionar documentación más detallada sobre clases y construcciones específicas.</span><span class="sxs-lookup"><span data-stu-id="40a03-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="40a03-111">¿Dónde obtengo el SDK?</span><span class="sxs-lookup"><span data-stu-id="40a03-111">Where do I get the SDK?</span></span>

<span data-ttu-id="40a03-112">El SDK de SceneUnderstanding se descarga a través de NuGet.</span><span class="sxs-lookup"><span data-stu-id="40a03-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="40a03-113">SDK de SceneUnderstanding</span><span class="sxs-lookup"><span data-stu-id="40a03-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="40a03-114">**Nota:** la versión más reciente depende de los paquetes de versión preliminar y debe habilitar los paquetes de versión preliminar para verlo.</span><span class="sxs-lookup"><span data-stu-id="40a03-114">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="40a03-115">En el caso de la versión 0.5.2022-RC y versiones posteriores, la información sobre la escena es compatible con proyecciones de lenguaje para C# y C++ que permiten a las aplicaciones desarrollar aplicaciones para las plataformas Win32 o UWP.</span><span class="sxs-lookup"><span data-stu-id="40a03-115">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="40a03-116">A partir de esta versión, SceneUnderstanding es compatible con la compatibilidad del editor de Unity con el SceneObserver, que se usa únicamente para comunicarse con HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="40a03-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="40a03-117">SceneUnderstanding requiere Windows SDK versión 18362 o posterior.</span><span class="sxs-lookup"><span data-stu-id="40a03-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="40a03-118">Si usa el SDK en un proyecto de Unity, use [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity) para instalar el paquete en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="40a03-118">If you're using the SDK in a Unity project, use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="40a03-119">Información conceptual</span><span class="sxs-lookup"><span data-stu-id="40a03-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="40a03-120">La escena</span><span class="sxs-lookup"><span data-stu-id="40a03-120">The Scene</span></span>

<span data-ttu-id="40a03-121">El dispositivo de realidad mixta integra constantemente información sobre lo que ve en su entorno.</span><span class="sxs-lookup"><span data-stu-id="40a03-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="40a03-122">La comprensión de la escena canaliza todos estos orígenes de datos y genera una sola abstracción unida.</span><span class="sxs-lookup"><span data-stu-id="40a03-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="40a03-123">La comprensión de escenas genera escenas, que son una composición de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representan una instancia de un solo elemento (por ejemplo, un muro/techo/piso). Los propios objetos de la escena son una composición de [SceneComponents, que representan partes más granulares que componen este SceneObject.</span><span class="sxs-lookup"><span data-stu-id="40a03-123">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="40a03-124">Algunos ejemplos de componentes son cuatro y mallas, pero en el futuro podrían representar cuadros de límite, mallas de colisión, metadatos, etc.</span><span class="sxs-lookup"><span data-stu-id="40a03-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="40a03-125">El proceso de conversión de los datos del sensor sin formato en una escena es una operación potencialmente costosa que podría tardar unos segundos en espacios medios (~ 10x10m) hasta minutos para espacios grandes (~ 50x50m) y, por lo tanto, no es algo que el dispositivo está calculando sin solicitud de aplicación.</span><span class="sxs-lookup"><span data-stu-id="40a03-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="40a03-126">En su lugar, la generación de escenas la desencadena la aplicación a petición.</span><span class="sxs-lookup"><span data-stu-id="40a03-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="40a03-127">La clase SceneObserver tiene métodos estáticos que pueden calcular o deserializar una escena, que puede enumerar o interactuar con.</span><span class="sxs-lookup"><span data-stu-id="40a03-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="40a03-128">La acción de "proceso" se ejecuta a petición y se ejecuta en la CPU, pero en un proceso independiente (el controlador de realidad mixta).</span><span class="sxs-lookup"><span data-stu-id="40a03-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="40a03-129">Sin embargo, mientras se realiza el proceso en otro proceso, los datos de la escena resultantes se almacenan y mantienen en la aplicación en el objeto de la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="40a03-130">A continuación se muestra un diagrama que ilustra este flujo de proceso y muestra ejemplos de dos aplicaciones que interconectan con el entorno de tiempo de ejecución de la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagrama del proceso](images/SU-ProcessFlow.png)

<span data-ttu-id="40a03-132">En el lado izquierdo hay un diagrama del tiempo de ejecución de la realidad mixta, que siempre está activado y en ejecución en su propio proceso.</span><span class="sxs-lookup"><span data-stu-id="40a03-132">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="40a03-133">Este tiempo de ejecución es responsable de realizar el seguimiento de los dispositivos, la asignación espacial y otras operaciones que la comprensión de la escena usa para entender y explicar el mundo.</span><span class="sxs-lookup"><span data-stu-id="40a03-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="40a03-134">En el lado derecho del diagrama, se muestran dos aplicaciones teóricas que hacen uso de la comprensión de la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="40a03-135">La primera interfaz de la aplicación con MRTK, que usa el SDK de información de escenas internamente, la segunda aplicación calcula y usa dos instancias de escena independientes.</span><span class="sxs-lookup"><span data-stu-id="40a03-135">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="40a03-136">Las tres escenas de este diagrama generan instancias distintas de las escenas, el controlador no realiza un seguimiento del estado global que se comparte entre las aplicaciones y los objetos de escena de una escena no se encuentran en otro.</span><span class="sxs-lookup"><span data-stu-id="40a03-136">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="40a03-137">La comprensión de la escena proporciona un mecanismo para realizar el seguimiento con el tiempo, pero esto se hace con el SDK.</span><span class="sxs-lookup"><span data-stu-id="40a03-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="40a03-138">El código de seguimiento ya se está ejecutando en el SDK en el proceso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="40a03-138">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="40a03-139">Dado que cada escena almacena sus datos en el espacio de memoria de la aplicación, puede suponer que todas las funciones del objeto de escena o de sus datos internos siempre se ejecutan en el proceso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="40a03-139">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="40a03-140">Layout</span><span class="sxs-lookup"><span data-stu-id="40a03-140">Layout</span></span>

<span data-ttu-id="40a03-141">Para trabajar con la comprensión de la escena, puede ser útil conocer y entender cómo representa los componentes el tiempo de ejecución de forma lógica y física.</span><span class="sxs-lookup"><span data-stu-id="40a03-141">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="40a03-142">La escena representa los datos con un diseño específico que se eligió para ser sencillo al tiempo que se mantiene una estructura subyacente que se pliable para satisfacer los requisitos futuros sin necesidad de revisiones importantes.</span><span class="sxs-lookup"><span data-stu-id="40a03-142">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="40a03-143">Para ello, la escena almacena todos los componentes (bloques de creación de todos los objetos de escena) en una lista plana y define la jerarquía y la composición a través de referencias en las que determinados componentes hacen referencia a otros.</span><span class="sxs-lookup"><span data-stu-id="40a03-143">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="40a03-144">A continuación se presenta un ejemplo de una estructura en su forma plana y lógica.</span><span class="sxs-lookup"><span data-stu-id="40a03-144">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="40a03-145">Diseño lógico</span><span class="sxs-lookup"><span data-stu-id="40a03-145">Logical Layout</span></span></th><th><span data-ttu-id="40a03-146">Diseño físico</span><span class="sxs-lookup"><span data-stu-id="40a03-146">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="40a03-147">Escena</span><span class="sxs-lookup"><span data-stu-id="40a03-147">Scene</span></span>
  <ul>
  <li><span data-ttu-id="40a03-148">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="40a03-148">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="40a03-149">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="40a03-149">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="40a03-150">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="40a03-150">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="40a03-151">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="40a03-151">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="40a03-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="40a03-152">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="40a03-153">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="40a03-153">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="40a03-154">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="40a03-154">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="40a03-155">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="40a03-155">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="40a03-156">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="40a03-156">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="40a03-157">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="40a03-157">SceneObject_1</span></span></li>
  <li><span data-ttu-id="40a03-158">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="40a03-158">SceneObject_2</span></span></li>
  <li><span data-ttu-id="40a03-159">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="40a03-159">SceneObject_3</span></span></li>
  <li><span data-ttu-id="40a03-160">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="40a03-160">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="40a03-161">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="40a03-161">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="40a03-162">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="40a03-162">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="40a03-163">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="40a03-163">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="40a03-164">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="40a03-164">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="40a03-165">En esta ilustración se resalta la diferencia entre el diseño físico y lógico de la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-165">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="40a03-166">A la izquierda, vemos el diseño jerárquico de los datos que la aplicación ve al enumerar la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-166">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="40a03-167">A la derecha, vemos que la escena se compone de 12 componentes distintos a los que se puede tener acceso individualmente si es necesario.</span><span class="sxs-lookup"><span data-stu-id="40a03-167">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="40a03-168">Al procesar una nueva escena, esperamos que las aplicaciones recorran esta jerarquía de manera lógica; sin embargo, al realizar un seguimiento entre las actualizaciones de la escena, algunas aplicaciones solo pueden estar interesadas en determinados componentes que se comparten entre dos escenas.</span><span class="sxs-lookup"><span data-stu-id="40a03-168">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="40a03-169">Introducción a la API</span><span class="sxs-lookup"><span data-stu-id="40a03-169">API overview</span></span>

<span data-ttu-id="40a03-170">En la sección siguiente se proporciona información general de alto nivel sobre las construcciones de comprensión de la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-170">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="40a03-171">Al leer esta sección se proporciona una descripción de cómo se representan las escenas y para qué se usan los distintos componentes.</span><span class="sxs-lookup"><span data-stu-id="40a03-171">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="40a03-172">En la siguiente sección se proporcionan ejemplos de código concretos e información adicional con el glosario en esta información general.</span><span class="sxs-lookup"><span data-stu-id="40a03-172">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="40a03-173">Todos los tipos que se describen a continuación residen en el `Microsoft.MixedReality.SceneUnderstanding` espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="40a03-173">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="40a03-174">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="40a03-174">SceneComponents</span></span>

<span data-ttu-id="40a03-175">Ahora que comprende el diseño lógico de escenas, ahora podemos presentar el concepto de SceneComponents y cómo se usan para crear la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="40a03-175">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="40a03-176">SceneComponents son las descomposiciones más pormenorizadas de SceneUnderstanding que representan una sola cosa principal, por ejemplo, una malla o un cuadro de límite cuádruple o de rectángulo.</span><span class="sxs-lookup"><span data-stu-id="40a03-176">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="40a03-177">SceneComponents son elementos que se pueden actualizar de forma independiente y a los que puede hacer referencia otro SceneComponents, por lo que tienen una única propiedad global como un identificador único, lo que permite este tipo de mecanismo de seguimiento o referencia.</span><span class="sxs-lookup"><span data-stu-id="40a03-177">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="40a03-178">Los identificadores se usan para la composición lógica de la jerarquía de escenas, así como para la persistencia de objetos (la acción de actualizar una escena en relación con otra).</span><span class="sxs-lookup"><span data-stu-id="40a03-178">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="40a03-179">Si está tratando cada escena recién calculada como DISTINCT y simplemente enumerando todos los datos que contiene, los identificadores son en gran medida transparentes para usted.</span><span class="sxs-lookup"><span data-stu-id="40a03-179">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="40a03-180">Sin embargo, si tiene previsto realizar un seguimiento de los componentes de varias actualizaciones, usará los identificadores para indexar y buscar SceneComponents entre los objetos de la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-180">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="40a03-181">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="40a03-181">SceneObjects</span></span>

<span data-ttu-id="40a03-182">Un SceneObject es un SceneComponent que representa una instancia de una "cosa", por ejemplo, una pared, una planta, un límite superior, etc. expresado por su propiedad Kind.</span><span class="sxs-lookup"><span data-stu-id="40a03-182">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="40a03-183">Los SceneObjects son geométricos y, por tanto, tienen funciones y propiedades que representan su ubicación en el espacio, pero no contienen ninguna estructura geométrica o lógica.</span><span class="sxs-lookup"><span data-stu-id="40a03-183">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="40a03-184">En su lugar, SceneObjects hace referencia a otros SceneComponents, específicamente SceneQuads y SceneMeshes, que proporcionan las representaciones variadas que admite el sistema.</span><span class="sxs-lookup"><span data-stu-id="40a03-184">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="40a03-185">Cuando se calcula una nueva escena, es probable que la aplicación Enumere los SceneObjects de la escena para procesar lo que le interesa.</span><span class="sxs-lookup"><span data-stu-id="40a03-185">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="40a03-186">SceneObjects puede tener cualquiera de las siguientes opciones:</span><span class="sxs-lookup"><span data-stu-id="40a03-186">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="40a03-187">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="40a03-187">SceneObjectKind</span></span></th> <th><span data-ttu-id="40a03-188">Description</span><span class="sxs-lookup"><span data-stu-id="40a03-188">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="40a03-189">Fondo</span><span class="sxs-lookup"><span data-stu-id="40a03-189">Background</span></span></td><td><span data-ttu-id="40a03-190">Se sabe que el SceneObject <b>no</b> es uno de los otros tipos reconocidos de objeto de escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-190">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="40a03-191">Esta clase no se debe confundir con Unknown, donde se sabe que el fondo no es mural, piso, techo, etc. Aunque Unknown no se ha categorizado todavía.</span><span class="sxs-lookup"><span data-stu-id="40a03-191">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="40a03-192">Pared</span><span class="sxs-lookup"><span data-stu-id="40a03-192">Wall</span></span></td><td><span data-ttu-id="40a03-193">Una pared física.</span><span class="sxs-lookup"><span data-stu-id="40a03-193">A physical wall.</span></span> <span data-ttu-id="40a03-194">Se supone que las paredes son estructuras de entorno inmóviles.</span><span class="sxs-lookup"><span data-stu-id="40a03-194">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="40a03-195">Floor</span><span class="sxs-lookup"><span data-stu-id="40a03-195">Floor</span></span></td><td><span data-ttu-id="40a03-196">Las plantas son superficies en las que se puede recorrer.</span><span class="sxs-lookup"><span data-stu-id="40a03-196">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="40a03-197">Nota: las escaleras no se encuentran en el suelo.</span><span class="sxs-lookup"><span data-stu-id="40a03-197">Note: stairs aren't floors.</span></span> <span data-ttu-id="40a03-198">Tenga en cuenta también que las plantas suponen cualquier superficie que se puede examinar y, por lo tanto, no hay ninguna suposición explícita de un piso singular.</span><span class="sxs-lookup"><span data-stu-id="40a03-198">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="40a03-199">Estructuras de varios niveles, rampas, etc... debe clasificarse como Floor.</span><span class="sxs-lookup"><span data-stu-id="40a03-199">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="40a03-200">Ceiling</span><span class="sxs-lookup"><span data-stu-id="40a03-200">Ceiling</span></span></td><td><span data-ttu-id="40a03-201">La superficie superior de una habitación.</span><span class="sxs-lookup"><span data-stu-id="40a03-201">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="40a03-202">Plataforma</span><span class="sxs-lookup"><span data-stu-id="40a03-202">Platform</span></span></td><td><span data-ttu-id="40a03-203">Una superficie plana grande en la que se pueden colocar hologramas.</span><span class="sxs-lookup"><span data-stu-id="40a03-203">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="40a03-204">Tienden a representar tablas, contrapartes y otras superficies horizontales grandes.</span><span class="sxs-lookup"><span data-stu-id="40a03-204">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="40a03-205">World</span><span class="sxs-lookup"><span data-stu-id="40a03-205">World</span></span></td><td><span data-ttu-id="40a03-206">Etiqueta reservada para los datos geométricos que es independiente de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="40a03-206">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="40a03-207">La malla generada al establecer la marca de actualización EnableWorldMesh se clasificaría como World.</span><span class="sxs-lookup"><span data-stu-id="40a03-207">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="40a03-208">Desconocido</span><span class="sxs-lookup"><span data-stu-id="40a03-208">Unknown</span></span></td><td><span data-ttu-id="40a03-209">Este objeto de escena todavía se puede clasificar y asignar a un tipo.</span><span class="sxs-lookup"><span data-stu-id="40a03-209">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="40a03-210">No se debe confundir con el fondo, ya que este objeto podría ser cualquier cosa, el sistema no se ha puesto todavía con una clasificación suficientemente alta para ella.</span><span class="sxs-lookup"><span data-stu-id="40a03-210">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="40a03-211">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="40a03-211">SceneMesh</span></span>

<span data-ttu-id="40a03-212">Un SceneMesh es un SceneComponent que se aproxima a la geometría de objetos geométricos arbitrarios mediante una lista de triángulos.</span><span class="sxs-lookup"><span data-stu-id="40a03-212">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="40a03-213">SceneMeshes se usan en varios contextos diferentes, pueden representar componentes de la estructura de celda estanca o como WorldMesh, que representa la malla de asignación espacial sin enlazar asociada a la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-213">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="40a03-214">Los datos de índice y vértices que se proporcionan con cada malla usan el mismo diseño conocido que los [búferes de vértices y de índices](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) que se usan para representar mallas de triángulo en todas las API de representación modernas.</span><span class="sxs-lookup"><span data-stu-id="40a03-214">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="40a03-215">En la comprensión de escenas, las mallas usan índices de 32 bits y es posible que necesiten dividirse en fragmentos para determinados motores de representación.</span><span class="sxs-lookup"><span data-stu-id="40a03-215">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="40a03-216">Orden de bobinado y sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="40a03-216">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="40a03-217">Se espera que todas las mallas generadas por el conocimiento de la escena devuelvan mallas en un sistema de coordenadas de Right-Handed con el orden de bobinado hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="40a03-217">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="40a03-218">Nota: las compilaciones del sistema operativo anteriores a. 191105 pueden tener un error conocido en el que las mallas "mundiales" devolvían en Counter-Clockwise orden de bobinado, que se ha corregido posteriormente.</span><span class="sxs-lookup"><span data-stu-id="40a03-218">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="40a03-219">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="40a03-219">SceneQuad</span></span>

<span data-ttu-id="40a03-220">Un SceneQuad es un SceneComponent que representa superficies 2D que ocupan el mundo 3D.</span><span class="sxs-lookup"><span data-stu-id="40a03-220">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="40a03-221">SceneQuads se puede usar de forma similar a los planos ARKit ARPlaneAnchor o ARCore, pero ofrecen más funcionalidad de alto nivel que los lienzos 2D que usarán las aplicaciones planas o la experiencia de usuario aumentada.</span><span class="sxs-lookup"><span data-stu-id="40a03-221">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="40a03-222">se proporcionan API específicas de 2D para cuádruples que facilitan el uso de la ubicación y el diseño, y el desarrollo (con la excepción de la representación) con cuatros se siente más parecido al trabajo con lienzos 2D que las mallas 3D.</span><span class="sxs-lookup"><span data-stu-id="40a03-222">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="40a03-223">Forma SceneQuad</span><span class="sxs-lookup"><span data-stu-id="40a03-223">SceneQuad shape</span></span>

<span data-ttu-id="40a03-224">SceneQuads define una superficie rectangular limitada en 2D.</span><span class="sxs-lookup"><span data-stu-id="40a03-224">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="40a03-225">Sin embargo, los SceneQuads representan superficies con formas arbitrarias y potencialmente complejas (por ejemplo, una tabla con forma de anillo). Para representar la forma compleja de la superficie de una cuádruple, puede usar la API GetSurfaceMask para representar la forma de la superficie en un búfer de imagen que proporcione.</span><span class="sxs-lookup"><span data-stu-id="40a03-225">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="40a03-226">Si el SceneObject que tiene el cuádruple también tiene una malla, los triángulos de la malla deben ser equivalentes a esta imagen representada, ambos representan la geometría real de la superficie, ya sea en coordenadas 2D o 3D.</span><span class="sxs-lookup"><span data-stu-id="40a03-226">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="40a03-227">Detalles y referencia del SDK de la escena</span><span class="sxs-lookup"><span data-stu-id="40a03-227">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="40a03-228">La siguiente sección le ayudará a familiarizarse con los conceptos básicos de SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="40a03-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="40a03-229">En esta sección se proporcionan los conceptos básicos, momento en el que debe tener suficiente contexto para examinar las aplicaciones de ejemplo para ver cómo se usa SceneUnderstanding de forma holística.</span><span class="sxs-lookup"><span data-stu-id="40a03-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="40a03-230">Inicialización</span><span class="sxs-lookup"><span data-stu-id="40a03-230">Initialization</span></span>

<span data-ttu-id="40a03-231">El primer paso para trabajar con SceneUnderstanding es que la aplicación pueda obtener referencias a un objeto de escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="40a03-232">Esto puede realizarse de una de estas dos formas: el controlador puede calcular una escena, o bien se puede deserializar una escena existente calculada en el pasado.</span><span class="sxs-lookup"><span data-stu-id="40a03-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="40a03-233">Esto último es útil para trabajar con SceneUnderstanding durante el desarrollo, donde las aplicaciones y experiencias se pueden crear rápidamente con un dispositivo de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="40a03-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="40a03-234">Las escenas se calculan mediante una SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="40a03-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="40a03-235">Antes de crear una escena, la aplicación debe consultar el dispositivo para asegurarse de que admite SceneUnderstanding, así como para solicitar acceso de usuario para obtener información que necesita SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="40a03-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="40a03-236">Si no se llama a RequestAccessAsync (), se producirá un error al calcular una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="40a03-237">A continuación, calcularemos una nueva escena que se basa en torno al casco de realidad mixta y que tiene un radio de 10 metros.</span><span class="sxs-lookup"><span data-stu-id="40a03-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="40a03-238">Inicialización de datos (también conocida como.</span><span class="sxs-lookup"><span data-stu-id="40a03-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="40a03-239">la ruta de acceso del equipo)</span><span class="sxs-lookup"><span data-stu-id="40a03-239">the PC Path)</span></span>

<span data-ttu-id="40a03-240">Aunque se pueden calcular escenas para su consumo directo, también se pueden calcular en forma serializada para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="40a03-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="40a03-241">Esto ha demostrado ser útil para el desarrollo, ya que permite a los desarrolladores trabajar y probar la comprensión de la escena sin necesidad de un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="40a03-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="40a03-242">El acto de serializar una escena es casi idéntico al cálculo, los datos se devuelven a la aplicación en lugar de deserializarse localmente mediante el SDK.</span><span class="sxs-lookup"><span data-stu-id="40a03-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="40a03-243">Después, puede deserializarlo usted mismo o guardarlo para su uso futuro.</span><span class="sxs-lookup"><span data-stu-id="40a03-243">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="40a03-244">Enumeración SceneObject</span><span class="sxs-lookup"><span data-stu-id="40a03-244">SceneObject Enumeration</span></span>

<span data-ttu-id="40a03-245">Ahora que la aplicación tiene una escena, la aplicación examinará e interactuará con SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="40a03-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="40a03-246">Esto se hace mediante el acceso a la propiedad **SceneObjects** :</span><span class="sxs-lookup"><span data-stu-id="40a03-246">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="40a03-247">Actualización de componentes y rebúsqueda de componentes</span><span class="sxs-lookup"><span data-stu-id="40a03-247">Component update and refinding components</span></span>

<span data-ttu-id="40a03-248">Hay otra función que recupera los componentes de la escena denominada \**_FindComponent_* _.</span><span class="sxs-lookup"><span data-stu-id="40a03-248">There's another function that retrieves components in the Scene called \**_FindComponent_* _.</span></span> <span data-ttu-id="40a03-249">Esta función es útil cuando se actualizan objetos de seguimiento y se encuentran en escenas posteriores.</span><span class="sxs-lookup"><span data-stu-id="40a03-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="40a03-250">El siguiente código calculará una nueva escena en relación con una escena anterior y, a continuación, buscará el piso en la nueva escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="40a03-251">Acceso a mallas y cuádruples de objetos de escena</span><span class="sxs-lookup"><span data-stu-id="40a03-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="40a03-252">Una vez que se ha detectado SceneObjects, es más probable que la aplicación tenga acceso a los datos contenidos en las cuádruples o mallas de las que se compone.</span><span class="sxs-lookup"><span data-stu-id="40a03-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="40a03-253">Se tiene acceso a estos datos con las propiedades de _*_cuádruples_*_ y _*_mallas_*_ .</span><span class="sxs-lookup"><span data-stu-id="40a03-253">This data is accessed with the _*_Quads_*_ and _*_Meshes_*_ properties.</span></span> <span data-ttu-id="40a03-254">En el código siguiente se enumeran todos los cuádruples y mallas de nuestro objeto Floor.</span><span class="sxs-lookup"><span data-stu-id="40a03-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="40a03-255">Observe que es el SceneObject que tiene la transformación relativa al origen de la escena.</span><span class="sxs-lookup"><span data-stu-id="40a03-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="40a03-256">Esto se debe a que SceneObject representa una instancia de una "Thing" y es localizable en el espacio, las cuádruples y las mallas representan geometría que se transforma con respecto a su elemento primario.</span><span class="sxs-lookup"><span data-stu-id="40a03-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="40a03-257">Es posible que SceneObjects independientes haga referencia al mismo SceneMesh/SceneQuad SceneComponents, y también es posible que una SceneObject tenga más de una SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="40a03-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="40a03-258">Trabajar con transformaciones</span><span class="sxs-lookup"><span data-stu-id="40a03-258">Dealing with Transforms</span></span>

<span data-ttu-id="40a03-259">La comprensión de la escena ha realizado un intento deliberado de alinearse con representaciones de escenas 3D tradicionales al tratar con transformaciones.</span><span class="sxs-lookup"><span data-stu-id="40a03-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="40a03-260">Por lo tanto, cada escena se limita a un sistema de coordenadas único, de forma muy similar a la mayoría de las representaciones comunes del entorno 3D.</span><span class="sxs-lookup"><span data-stu-id="40a03-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="40a03-261">Cada SceneObjects proporciona su ubicación relativa a ese sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="40a03-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="40a03-262">Si la aplicación está tratando con escenas que amplían el límite de lo que proporciona un único origen, puede delimitar SceneObjects a SpatialAnchors, o generar varias escenas y combinarlas juntas, pero para simplificar, se supone que las escenas estancas existen en su propio origen localizado por un NodeId definido por Scene. OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="40a03-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="40a03-263">El siguiente código de Unity, por ejemplo, muestra cómo usar las API de Windows y la percepción de Windows para alinear los sistemas de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="40a03-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="40a03-264">Consulte [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) y [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) para obtener más información sobre las API de percepción de Windows y los [objetos nativos de realidad mixta en Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) para obtener más información sobre cómo obtener una SpatialCoordinateSystem que se corresponda con el origen mundial de Unity.</span><span class="sxs-lookup"><span data-stu-id="40a03-264">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

<span data-ttu-id="40a03-265">Cada `SceneObject` una tiene una transformación, que se aplica a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="40a03-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="40a03-266">En Unity convertiremos en coordenadas correctas y asignaremos transformaciones locales de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="40a03-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a><span data-ttu-id="40a03-267">Cuádruple</span><span class="sxs-lookup"><span data-stu-id="40a03-267">Quad</span></span>

<span data-ttu-id="40a03-268">Las Quad se diseñaron para ayudar en escenarios de selección de ubicación 2D y deben considerarse como extensiones para los elementos de la experiencia de usuario de lienzo 2D.</span><span class="sxs-lookup"><span data-stu-id="40a03-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="40a03-269">Aunque cuádruples son componentes de SceneObjects y se pueden representar en 3D, las propias API en sí suponen que los cuatro son estructuras 2D.</span><span class="sxs-lookup"><span data-stu-id="40a03-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="40a03-270">Ofrecen información como extensión, forma y proporcionan API para la selección de ubicación.</span><span class="sxs-lookup"><span data-stu-id="40a03-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="40a03-271">Las Quad tienen extensiones rectangulares, pero representan superficies 2D con forma arbitraria.</span><span class="sxs-lookup"><span data-stu-id="40a03-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="40a03-272">Para habilitar la selección de ubicación en estas superficies 2D que interactúan con las utilidades de los cuatro entornos en 3D para que esta interacción sea posible.</span><span class="sxs-lookup"><span data-stu-id="40a03-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="40a03-273">Actualmente, la comprensión de la escena proporciona dos funciones, _ *FindCentermostPlacement*\* y **GetSurfaceMask**.</span><span class="sxs-lookup"><span data-stu-id="40a03-273">Currently Scene Understanding provides two such functions, _ *FindCentermostPlacement*\* and **GetSurfaceMask**.</span></span> <span data-ttu-id="40a03-274">FindCentermostPlacement es una API de alto nivel que busca una posición en la cuádruple donde se puede colocar un objeto e intenta encontrar la mejor ubicación para el objeto, lo que garantiza que el cuadro de límite que proporcione permanecerá en la superficie subyacente.</span><span class="sxs-lookup"><span data-stu-id="40a03-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="40a03-275">Las coordenadas de la salida son relativas a la cuádruple en "espacio cuádruple" con la esquina superior izquierda (x = 0, y = 0), del mismo modo que lo haría con otros tipos de rectángulo de Windows.</span><span class="sxs-lookup"><span data-stu-id="40a03-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="40a03-276">No olvide tener esto en cuenta al trabajar con los orígenes de sus propios objetos.</span><span class="sxs-lookup"><span data-stu-id="40a03-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="40a03-277">En el ejemplo siguiente se muestra cómo buscar la ubicación centermost colocar y delimitar un holograma a la cuádruple.</span><span class="sxs-lookup"><span data-stu-id="40a03-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="40a03-278">Los pasos 1-4 son muy dependientes de la implementación o el marco de trabajo en particular, pero los temas deben ser similares.</span><span class="sxs-lookup"><span data-stu-id="40a03-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="40a03-279">Es importante tener en cuenta que la cuádruple simplemente representa un plano 2D enlazado que está localizado en el espacio.</span><span class="sxs-lookup"><span data-stu-id="40a03-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="40a03-280">Teniendo el motor o el marco de trabajo de saber dónde está el cuádruple y la raíz de los objetos en relación con la cuádruple, los hologramas se ubicarán correctamente con respecto al mundo real.</span><span class="sxs-lookup"><span data-stu-id="40a03-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="40a03-281">En malla</span><span class="sxs-lookup"><span data-stu-id="40a03-281">Mesh</span></span>

<span data-ttu-id="40a03-282">Las mallas representan representaciones geométricas de objetos o entornos.</span><span class="sxs-lookup"><span data-stu-id="40a03-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="40a03-283">De forma similar a la [asignación espacial](../../design/spatial-mapping.md), los datos del índice de malla y del vértice que se proporcionan con cada malla de superficie espacial usan el mismo diseño conocido que los búferes de vértices y de índices que se usan para representar mallas de triángulo en todas las API de representación modernas.</span><span class="sxs-lookup"><span data-stu-id="40a03-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="40a03-284">Las posiciones de los vértices se proporcionan en el sistema de coordenadas de `Scene` .</span><span class="sxs-lookup"><span data-stu-id="40a03-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="40a03-285">Las API específicas que se usan para hacer referencia a estos datos son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="40a03-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="40a03-286">El código siguiente proporciona un ejemplo de generación de una lista de triángulos a partir de la estructura de malla:</span><span class="sxs-lookup"><span data-stu-id="40a03-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="40a03-287">Los búferes de índice/vértices se deben >= los recuentos de índice o vértices, pero de lo contrario se puede cambiar el tamaño de forma arbitraria, lo que permite la reutilización de memoria eficaz.</span><span class="sxs-lookup"><span data-stu-id="40a03-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="40a03-288">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="40a03-288">ColliderMesh</span></span>

<span data-ttu-id="40a03-289">Los objetos de escena proporcionan acceso a los datos de malla y de la malla de Colisionador a través de las propiedades meshes y ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="40a03-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="40a03-290">Estas mallas siempre coinciden, lo que significa que el índice i-ésima de la propiedad meshes representa la misma geometría que el índice i de la propiedad ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="40a03-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="40a03-291">Si el objeto en tiempo de ejecución es compatible con las mallas de Colisionador, se garantiza que obtendrá el polígono más bajo, la mayor aproximación de orden y se recomienda usar ColliderMeshes siempre que la aplicación use colisionadores.</span><span class="sxs-lookup"><span data-stu-id="40a03-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="40a03-292">Si el sistema no admite colisiones, el objeto de malla devuelto en ColliderMeshes será el mismo objeto que la malla que reduce las restricciones de memoria.</span><span class="sxs-lookup"><span data-stu-id="40a03-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="40a03-293">Desarrollo con conocimiento de escenas</span><span class="sxs-lookup"><span data-stu-id="40a03-293">Developing with scene understanding</span></span>

<span data-ttu-id="40a03-294">En este punto, debe comprender los principales bloques de creación de la escena que comprende el tiempo de ejecución y el SDK.</span><span class="sxs-lookup"><span data-stu-id="40a03-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="40a03-295">La mayor parte de la eficacia y la complejidad radica en los patrones de acceso, la interacción con Marcos 3D y las herramientas que se pueden escribir sobre estas API para realizar tareas más avanzadas, como la planeación espacial, el análisis de habitación, la navegación, la física, etc.</span><span class="sxs-lookup"><span data-stu-id="40a03-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="40a03-296">Esperamos que se capturen en ejemplos que deberían ser de esperar en la dirección adecuada para que los escenarios se muestren.</span><span class="sxs-lookup"><span data-stu-id="40a03-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="40a03-297">Si hay ejemplos o escenarios que no abordamos, háganoslo saber y vamos a intentar documentar o crear prototipos de lo que necesita.</span><span class="sxs-lookup"><span data-stu-id="40a03-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="40a03-298">¿Dónde puedo obtener código de ejemplo?</span><span class="sxs-lookup"><span data-stu-id="40a03-298">Where can I get sample code?</span></span>

<span data-ttu-id="40a03-299">En la página de la [Página de ejemplo de Unity](https://github.com/sceneunderstanding-microsoft/unitysample) puede encontrar el código de ejemplo de la escena para Unity.</span><span class="sxs-lookup"><span data-stu-id="40a03-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="40a03-300">Esta aplicación le permitirá comunicarse con el dispositivo y representar los distintos objetos de la escena, o bien le permitirá cargar una escena serializada en su equipo y le permitirá experimentar la comprensión de la escena sin un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="40a03-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="40a03-301">¿Dónde puedo obtener escenas de ejemplo?</span><span class="sxs-lookup"><span data-stu-id="40a03-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="40a03-302">Si tiene un HoloLens2, puede guardar cualquier escena que haya capturado guardando el resultado de ComputeSerializedAsync en un archivo y deserializarlo por su comodidad.</span><span class="sxs-lookup"><span data-stu-id="40a03-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="40a03-303">Si no tiene un dispositivo HoloLens2 pero desea jugar con la comprensión de la escena, deberá descargar una escena capturada previamente.</span><span class="sxs-lookup"><span data-stu-id="40a03-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="40a03-304">El ejemplo de comprensión de la escena se incluye actualmente con escenas serializadas que se pueden descargar y usar por su comodidad.</span><span class="sxs-lookup"><span data-stu-id="40a03-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="40a03-305">Puede encontrarlos aquí:</span><span class="sxs-lookup"><span data-stu-id="40a03-305">You can find them here:</span></span>

[<span data-ttu-id="40a03-306">Escenas de ejemplo de la escena</span><span class="sxs-lookup"><span data-stu-id="40a03-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="40a03-307">Consulta también</span><span class="sxs-lookup"><span data-stu-id="40a03-307">See also</span></span>

* [<span data-ttu-id="40a03-308">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="40a03-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="40a03-309">Descripción de escenas</span><span class="sxs-lookup"><span data-stu-id="40a03-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="40a03-310">Ejemplo de Unity</span><span class="sxs-lookup"><span data-stu-id="40a03-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
