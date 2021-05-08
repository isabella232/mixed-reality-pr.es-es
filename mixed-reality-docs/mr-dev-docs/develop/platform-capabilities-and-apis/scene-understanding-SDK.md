---
title: SDK de descripción de la escena
description: Obtenga información sobre cómo instalar y usar el SDK de Scene Understanding, incluidos componentes, mallas y objetos en aplicaciones de realidad mixta.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Scene Understanding, Spatial Mapping, Windows Mixed Reality, Unity
ms.openlocfilehash: 2f6e0c9d0370caed2b2bc01399b9e4fc00836556
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644841"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="a8e60-104">Introducción al SDK de descripción de la escena</span><span class="sxs-lookup"><span data-stu-id="a8e60-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="a8e60-105">La comprensión de la escena transforma los datos no estructurados del sensor del entorno que el Mixed Reality captura y los convierte en una representación abstracta eficaz.</span><span class="sxs-lookup"><span data-stu-id="a8e60-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="a8e60-106">El SDK actúa como capa de comunicación entre la aplicación y el entorno de ejecución de Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="a8e60-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="a8e60-107">Su objetivo es imitar construcciones estándar existentes, como gráficos de escena 3D para representaciones 3D y rectángulos y paneles 2D para aplicaciones 2D.</span><span class="sxs-lookup"><span data-stu-id="a8e60-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="a8e60-108">Aunque las construcciones que scene understanding imita se asignarán a marcos concretos, en general SceneUnderstanding es un marco independiente que permite la interoperabilidad entre diversos marcos que interactúan con él.</span><span class="sxs-lookup"><span data-stu-id="a8e60-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="a8e60-109">A medida que Scene Understanding evoluciona, el rol del SDK es garantizar que las nuevas representaciones y funcionalidades se sigan exponendo dentro de un marco unificado.</span><span class="sxs-lookup"><span data-stu-id="a8e60-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="a8e60-110">En este documento, primero presentaremos conceptos de alto nivel que le ayudarán a familiarizarse con el entorno o el uso de desarrollo y, a continuación, proporcionaremos documentación más detallada para clases y construcciones específicas.</span><span class="sxs-lookup"><span data-stu-id="a8e60-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="a8e60-111">¿Dónde puedo obtener el SDK?</span><span class="sxs-lookup"><span data-stu-id="a8e60-111">Where do I get the SDK?</span></span>

<span data-ttu-id="a8e60-112">El SDK SceneUnderstanding se puede descargar a través [de Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a8e60-112">The SceneUnderstanding SDK is downloadable via the [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md).</span></span>

<span data-ttu-id="a8e60-113">**Nota:** La versión más reciente depende de los paquetes de versión preliminar y deberá habilitar los paquetes de versión preliminar para verla.</span><span class="sxs-lookup"><span data-stu-id="a8e60-113">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="a8e60-114">Para la versión 0.5.2022-rc y versiones posteriores, Scene Understanding admite proyecciones de lenguaje para C# y C++ que permiten a las aplicaciones desarrollar aplicaciones para plataformas Win32 o UWP.</span><span class="sxs-lookup"><span data-stu-id="a8e60-114">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="a8e60-115">Desde esta versión, SceneUnderstanding admite la compatibilidad con Unity en el editor que no incluye SceneObserver, que se usa únicamente para comunicarse con HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="a8e60-115">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="a8e60-116">SceneUnderstanding requiere Windows SDK versión 18362 o posterior.</span><span class="sxs-lookup"><span data-stu-id="a8e60-116">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

## <a name="conceptual-overview"></a><span data-ttu-id="a8e60-117">Información conceptual</span><span class="sxs-lookup"><span data-stu-id="a8e60-117">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="a8e60-118">La escena</span><span class="sxs-lookup"><span data-stu-id="a8e60-118">The Scene</span></span>

<span data-ttu-id="a8e60-119">El dispositivo de realidad mixta integra constantemente información sobre lo que ve en su entorno.</span><span class="sxs-lookup"><span data-stu-id="a8e60-119">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="a8e60-120">Scene Understanding embudos todos estos orígenes de datos y genera una única abstracción cohesiva.</span><span class="sxs-lookup"><span data-stu-id="a8e60-120">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="a8e60-121">Scene Understanding genera escenas, que son una composición de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representan una instancia de una sola cosa (por ejemplo, una pared, un límite o un suelo). Los propios objetos scene son una composición de [SceneComponents, que representan partes más granulares que constituyen este SceneObject.</span><span class="sxs-lookup"><span data-stu-id="a8e60-121">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="a8e60-122">Algunos ejemplos de componentes son quads y mallas, pero en el futuro podrían representar rectángulos delimitadores, mallas de colisión, metadatos, etc.</span><span class="sxs-lookup"><span data-stu-id="a8e60-122">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="a8e60-123">El proceso de convertir los datos del sensor sin procesar en una escena es una operación potencialmente costosa que podría tardar segundos para los espacios medios (~10 x 10 m) en minutos para espacios grandes (~50 x 50 m) y, por tanto, no es algo que el dispositivo esté calculando sin solicitud de aplicación.</span><span class="sxs-lookup"><span data-stu-id="a8e60-123">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="a8e60-124">En su lugar, la aplicación desencadena la generación de escenas a petición.</span><span class="sxs-lookup"><span data-stu-id="a8e60-124">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="a8e60-125">La clase SceneObserver tiene métodos estáticos que pueden calcular o deserializar una escena, con la que puede enumerar e interactuar.</span><span class="sxs-lookup"><span data-stu-id="a8e60-125">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="a8e60-126">La acción "Compute" se ejecuta a petición y se ejecuta en la CPU, pero en un proceso independiente (Mixed Reality Driver).</span><span class="sxs-lookup"><span data-stu-id="a8e60-126">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="a8e60-127">Sin embargo, mientras calculamos en otro proceso, los datos de la escena resultantes se almacenan y mantienen en la aplicación en el objeto Scene.</span><span class="sxs-lookup"><span data-stu-id="a8e60-127">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="a8e60-128">A continuación se muestra un diagrama que ilustra este flujo de proceso y muestra ejemplos de dos aplicaciones que se interfacing con el entorno de ejecución de Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="a8e60-128">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagrama de procesos](images/SU-ProcessFlow.png)

<span data-ttu-id="a8e60-130">En el lado izquierdo hay un diagrama del entorno de ejecución de realidad mixta, que siempre está en funcionamiento en su propio proceso.</span><span class="sxs-lookup"><span data-stu-id="a8e60-130">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="a8e60-131">Este runtime es responsable de realizar el seguimiento de dispositivos, la asignación espacial y otras operaciones que Scene Understanding usa para comprender y razonar sobre el mundo que le rodea.</span><span class="sxs-lookup"><span data-stu-id="a8e60-131">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="a8e60-132">En el lado derecho del diagrama, se muestran dos aplicaciones teóricas que usan Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="a8e60-132">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="a8e60-133">La primera aplicación se interfaces con MRTK, que usa el SDK de Scene Understanding internamente, la segunda aplicación calcula y usa dos instancias de escena independientes.</span><span class="sxs-lookup"><span data-stu-id="a8e60-133">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="a8e60-134">Las tres escenas de este diagrama generan instancias distintas de las escenas, el controlador no está siguiendo el estado global que se comparte entre las aplicaciones y los objetos de escena de una escena no se encuentran en otra.</span><span class="sxs-lookup"><span data-stu-id="a8e60-134">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="a8e60-135">Scene Understanding proporciona un mecanismo para realizar un seguimiento a lo largo del tiempo, pero esto se hace mediante el SDK.</span><span class="sxs-lookup"><span data-stu-id="a8e60-135">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="a8e60-136">El código de seguimiento ya se está ejecutando en el SDK en el proceso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a8e60-136">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="a8e60-137">Dado que cada escena almacena sus datos en el espacio de memoria de la aplicación, puede suponer que todas las funciones del objeto Scene o sus datos internos siempre se ejecutan en el proceso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a8e60-137">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="a8e60-138">Diseño</span><span class="sxs-lookup"><span data-stu-id="a8e60-138">Layout</span></span>

<span data-ttu-id="a8e60-139">Para trabajar con Scene Understanding, puede ser útil conocer y comprender cómo el tiempo de ejecución representa los componentes de forma lógica y física.</span><span class="sxs-lookup"><span data-stu-id="a8e60-139">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="a8e60-140">La escena representa los datos con un diseño específico que se eligió para ser sencillos al tiempo que se mantiene una estructura subyacente que es ajustable para satisfacer los requisitos futuros sin necesidad de revisiones importantes.</span><span class="sxs-lookup"><span data-stu-id="a8e60-140">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="a8e60-141">Para ello, la escena almacena todos los componentes (bloques de creación de todos los objetos de escena) en una lista plana y define la jerarquía y la composición a través de referencias donde componentes específicos hacen referencia a otros.</span><span class="sxs-lookup"><span data-stu-id="a8e60-141">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="a8e60-142">A continuación se presenta un ejemplo de una estructura en su forma plana y lógica.</span><span class="sxs-lookup"><span data-stu-id="a8e60-142">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="a8e60-143">Diseño lógico</span><span class="sxs-lookup"><span data-stu-id="a8e60-143">Logical Layout</span></span></th><th><span data-ttu-id="a8e60-144">Diseño físico</span><span class="sxs-lookup"><span data-stu-id="a8e60-144">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="a8e60-145">Escena</span><span class="sxs-lookup"><span data-stu-id="a8e60-145">Scene</span></span>
  <ul>
  <li><span data-ttu-id="a8e60-146">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="a8e60-146">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="a8e60-147">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="a8e60-147">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="a8e60-148">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="a8e60-148">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="a8e60-149">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="a8e60-149">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="a8e60-150">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="a8e60-150">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="a8e60-151">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="a8e60-151">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="a8e60-152">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="a8e60-152">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="a8e60-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="a8e60-153">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="a8e60-154">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="a8e60-154">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="a8e60-155">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="a8e60-155">SceneObject_1</span></span></li>
  <li><span data-ttu-id="a8e60-156">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="a8e60-156">SceneObject_2</span></span></li>
  <li><span data-ttu-id="a8e60-157">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="a8e60-157">SceneObject_3</span></span></li>
  <li><span data-ttu-id="a8e60-158">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="a8e60-158">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="a8e60-159">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="a8e60-159">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="a8e60-160">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="a8e60-160">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="a8e60-161">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="a8e60-161">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="a8e60-162">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="a8e60-162">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="a8e60-163">En esta ilustración se resalta la diferencia entre el diseño físico y lógico de la escena.</span><span class="sxs-lookup"><span data-stu-id="a8e60-163">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="a8e60-164">A la izquierda, vemos el diseño jerárquico de los datos que la aplicación ve al enumerar la escena.</span><span class="sxs-lookup"><span data-stu-id="a8e60-164">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="a8e60-165">A la derecha, vemos que la escena consta de 12 componentes distintos que son accesibles individualmente si es necesario.</span><span class="sxs-lookup"><span data-stu-id="a8e60-165">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="a8e60-166">Al procesar una nueva escena, esperamos que las aplicaciones recorridon esta jerarquía de forma lógica; sin embargo, al realizar el seguimiento entre las actualizaciones de la escena, algunas aplicaciones solo pueden estar interesadas en dirigirse a componentes específicos que se comparten entre dos escenas.</span><span class="sxs-lookup"><span data-stu-id="a8e60-166">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="a8e60-167">Introducción a la API</span><span class="sxs-lookup"><span data-stu-id="a8e60-167">API overview</span></span>

<span data-ttu-id="a8e60-168">En la sección siguiente se proporciona información general de alto nivel de las construcciones de Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="a8e60-168">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="a8e60-169">La lectura de esta sección le permitirá comprender cómo se representan las escenas y para qué se usan los distintos componentes.</span><span class="sxs-lookup"><span data-stu-id="a8e60-169">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="a8e60-170">En la sección siguiente se proporcionarán ejemplos de código concretos y detalles adicionales que se glosarán en esta información general.</span><span class="sxs-lookup"><span data-stu-id="a8e60-170">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="a8e60-171">Todos los tipos descritos a continuación residen en el espacio de `Microsoft.MixedReality.SceneUnderstanding` nombres .</span><span class="sxs-lookup"><span data-stu-id="a8e60-171">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="a8e60-172">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="a8e60-172">SceneComponents</span></span>

<span data-ttu-id="a8e60-173">Ahora que comprende el diseño lógico de las escenas, ahora podemos presentar el concepto de SceneComponents y cómo se usan para crear la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="a8e60-173">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="a8e60-174">SceneComponents son las descomposicións más pormenorizados de SceneUnderstanding que representan un único elemento principal, por ejemplo, una malla, un cuadrándulo o un rectángulo de límite.</span><span class="sxs-lookup"><span data-stu-id="a8e60-174">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="a8e60-175">SceneComponents son elementos que se pueden actualizar de forma independiente y a los que otros SceneComponents pueden hacer referencia, por lo que tienen una única propiedad global con un identificador único que permite este tipo de mecanismo de seguimiento o referencia.</span><span class="sxs-lookup"><span data-stu-id="a8e60-175">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="a8e60-176">Los identificadores se usan para la composición lógica de la jerarquía de escena, así como para la persistencia de objetos (el acto de actualizar una escena en relación con otra).</span><span class="sxs-lookup"><span data-stu-id="a8e60-176">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="a8e60-177">Si está tratando cada escena recién calculada como distinta y simplemente enumerando todos los datos dentro de ella, los identificadores son en gran medida transparentes para usted.</span><span class="sxs-lookup"><span data-stu-id="a8e60-177">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="a8e60-178">Sin embargo, si planea realizar un seguimiento de los componentes a través de varias actualizaciones, usará los identificadores para indexar y buscar SceneComponents entre objetos scene.</span><span class="sxs-lookup"><span data-stu-id="a8e60-178">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="a8e60-179">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="a8e60-179">SceneObjects</span></span>

<span data-ttu-id="a8e60-180">Un SceneObject es un SceneComponent que representa una instancia de una "cosa", por ejemplo, una pared, un suelo, un límite superior, etc.... expresado por su propiedad Kind.</span><span class="sxs-lookup"><span data-stu-id="a8e60-180">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="a8e60-181">SceneObjects son geométricos y, por tanto, tienen funciones y propiedades que representan su ubicación en el espacio, pero no contienen ninguna estructura geométrica o lógica.</span><span class="sxs-lookup"><span data-stu-id="a8e60-181">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="a8e60-182">En su lugar, SceneObjects hace referencia a otros SceneComponents, específicamente SceneQuads y SceneMeshes, que proporcionan las diversas representaciones compatibles con el sistema.</span><span class="sxs-lookup"><span data-stu-id="a8e60-182">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="a8e60-183">Cuando se calcula una nueva escena, lo más probable es que la aplicación enumere los SceneObjects de la escena para procesar lo que le interesa.</span><span class="sxs-lookup"><span data-stu-id="a8e60-183">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="a8e60-184">SceneObjects puede tener cualquiera de los siguientes elementos:</span><span class="sxs-lookup"><span data-stu-id="a8e60-184">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="a8e60-185">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="a8e60-185">SceneObjectKind</span></span></th> <th><span data-ttu-id="a8e60-186">Descripción</span><span class="sxs-lookup"><span data-stu-id="a8e60-186">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="a8e60-187">Fondo</span><span class="sxs-lookup"><span data-stu-id="a8e60-187">Background</span></span></td><td><span data-ttu-id="a8e60-188">Se sabe que SceneObject no es <b>uno</b> de los otros tipos reconocidos de objeto de escena.</span><span class="sxs-lookup"><span data-stu-id="a8e60-188">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="a8e60-189">Esta clase no debe confundirse con Desconocido, donde se sabe que background no es de la pared, el suelo o el límite superior, etc.... mientras que desconocido aún no se ha clasificado por categorías.</span><span class="sxs-lookup"><span data-stu-id="a8e60-189">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="a8e60-190">Pared</span><span class="sxs-lookup"><span data-stu-id="a8e60-190">Wall</span></span></td><td><span data-ttu-id="a8e60-191">Una pared física.</span><span class="sxs-lookup"><span data-stu-id="a8e60-191">A physical wall.</span></span> <span data-ttu-id="a8e60-192">Se supone que las paredes son estructuras ambientales legibles.</span><span class="sxs-lookup"><span data-stu-id="a8e60-192">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="a8e60-193">Floor</span><span class="sxs-lookup"><span data-stu-id="a8e60-193">Floor</span></span></td><td><span data-ttu-id="a8e60-194">Los suelos son cualquier superficie en la que se puede recorrer.</span><span class="sxs-lookup"><span data-stu-id="a8e60-194">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="a8e60-195">Nota: Los suelos no son plantas.</span><span class="sxs-lookup"><span data-stu-id="a8e60-195">Note: stairs aren't floors.</span></span> <span data-ttu-id="a8e60-196">Tenga en cuenta también que los suelos asumen cualquier superficie a pie y, por tanto, no hay ninguna suposición explícita de una planta singular.</span><span class="sxs-lookup"><span data-stu-id="a8e60-196">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="a8e60-197">Estructuras de varios niveles, rampas, etc.... debe clasificarse como floor.</span><span class="sxs-lookup"><span data-stu-id="a8e60-197">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="a8e60-198">Ceiling</span><span class="sxs-lookup"><span data-stu-id="a8e60-198">Ceiling</span></span></td><td><span data-ttu-id="a8e60-199">Superficie superior de una sala.</span><span class="sxs-lookup"><span data-stu-id="a8e60-199">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="a8e60-200">Plataforma</span><span class="sxs-lookup"><span data-stu-id="a8e60-200">Platform</span></span></td><td><span data-ttu-id="a8e60-201">Una gran superficie plana en la que podría colocar hologramas.</span><span class="sxs-lookup"><span data-stu-id="a8e60-201">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="a8e60-202">Tienden a representar tablas, contratops y otras superficies horizontales grandes.</span><span class="sxs-lookup"><span data-stu-id="a8e60-202">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="a8e60-203">World</span><span class="sxs-lookup"><span data-stu-id="a8e60-203">World</span></span></td><td><span data-ttu-id="a8e60-204">Una etiqueta reservada para los datos geométricos que es independiente del etiquetado.</span><span class="sxs-lookup"><span data-stu-id="a8e60-204">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="a8e60-205">La malla generada estableciendo la marca de actualización EnableWorldMesh se clasificaría como world.</span><span class="sxs-lookup"><span data-stu-id="a8e60-205">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="a8e60-206">Desconocido</span><span class="sxs-lookup"><span data-stu-id="a8e60-206">Unknown</span></span></td><td><span data-ttu-id="a8e60-207">Este objeto de escena aún no se ha clasificado y se le ha asignado un tipo.</span><span class="sxs-lookup"><span data-stu-id="a8e60-207">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="a8e60-208">Esto no debe confundirse con Background, ya que este objeto podría ser cualquier cosa, el sistema todavía no ha llegado con una clasificación lo suficientemente fuerte para él.</span><span class="sxs-lookup"><span data-stu-id="a8e60-208">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="a8e60-209">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="a8e60-209">SceneMesh</span></span>

<span data-ttu-id="a8e60-210">SceneMesh es un SceneComponent que aproxima la geometría de objetos geométricos arbitrarios mediante una lista de triángulos.</span><span class="sxs-lookup"><span data-stu-id="a8e60-210">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="a8e60-211">SceneMeshes se usa en varios contextos diferentes, pueden representar componentes de la estructura de celdas estancas o como WorldMesh, que representa la malla de asignación espacial sin enlazar asociada a la escena.</span><span class="sxs-lookup"><span data-stu-id="a8e60-211">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="a8e60-212">Los datos de índice y vértice proporcionados con cada malla usan el mismo diseño conocido que los búferes de vértice e índice que se usan para representar [mallas](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) de triángulo en todas las API de representación modernas.</span><span class="sxs-lookup"><span data-stu-id="a8e60-212">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="a8e60-213">En Scene Understanding, las mallas usan índices de 32 bits y es posible que deba dividirse en fragmentos para determinados motores de representación.</span><span class="sxs-lookup"><span data-stu-id="a8e60-213">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="a8e60-214">Orden de viento y sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="a8e60-214">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="a8e60-215">Se espera que todas las mallas producidas por Scene Understanding devuelvan mallas en un Right-Handed de coordenadas mediante el orden de sinuoso en el sentido de las agujas del reloj.</span><span class="sxs-lookup"><span data-stu-id="a8e60-215">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="a8e60-216">Nota: Las compilaciones del sistema operativo anteriores Counter-Clockwise .191105 pueden tener un error conocido en el que las mallas "World" devolvían en orden de sinuoso, que posteriormente se ha corregido.</span><span class="sxs-lookup"><span data-stu-id="a8e60-216">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="a8e60-217">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="a8e60-217">SceneQuad</span></span>

<span data-ttu-id="a8e60-218">SceneQuad es un SceneComponent que representa superficies 2d que ocupan el mundo 3d.</span><span class="sxs-lookup"><span data-stu-id="a8e60-218">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="a8e60-219">SceneQuads se puede usar de forma similar a ARKit ARPlaneAnchor o ARCore Planes, pero ofrecen una funcionalidad más alta como lienzos 2d para que los usen las aplicaciones planas o la experiencia de usuario aumentada.</span><span class="sxs-lookup"><span data-stu-id="a8e60-219">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="a8e60-220">Las API específicas 2D se proporcionan para los quads que hacen que la colocación y el diseño sean fáciles de usar, y el desarrollo (a excepción de la representación) con quads debe ser más parecido a trabajar con lienzos 2d que con mallas 3d.</span><span class="sxs-lookup"><span data-stu-id="a8e60-220">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="a8e60-221">Forma SceneQuad</span><span class="sxs-lookup"><span data-stu-id="a8e60-221">SceneQuad shape</span></span>

<span data-ttu-id="a8e60-222">SceneQuads define una superficie rectangular limitada en 2d.</span><span class="sxs-lookup"><span data-stu-id="a8e60-222">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="a8e60-223">Sin embargo, SceneQuads representa superficies con formas arbitrarias y potencialmente complejas (por ejemplo, una tabla con forma de anillo). Para representar la forma compleja de la superficie de un quad, puede usar la API GetSurfaceMask para representar la forma de la superficie en un búfer de imagen que proporcione.</span><span class="sxs-lookup"><span data-stu-id="a8e60-223">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="a8e60-224">Si sceneObject que tiene el cuadrándulo también tiene una malla, los triángulos de malla deben ser equivalentes a esta imagen representado, ambos representan la geometría real de la superficie, ya sea en coordenadas 2d o 3d.</span><span class="sxs-lookup"><span data-stu-id="a8e60-224">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="a8e60-225">Referencia y detalles del SDK de descripción de la escena</span><span class="sxs-lookup"><span data-stu-id="a8e60-225">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="a8e60-226">La sección siguiente le ayudará a familiarizarse con los conceptos básicos de SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="a8e60-226">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="a8e60-227">En esta sección se proporcionan los conceptos básicos, momento en el que debe tener suficiente contexto para examinar las aplicaciones de ejemplo para ver cómo se usa SceneUnderstanding holísticamente.</span><span class="sxs-lookup"><span data-stu-id="a8e60-227">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="a8e60-228">Inicialización</span><span class="sxs-lookup"><span data-stu-id="a8e60-228">Initialization</span></span>

<span data-ttu-id="a8e60-229">El primer paso para trabajar con SceneUnderstanding es que la aplicación obtenga referencia a un objeto Scene.</span><span class="sxs-lookup"><span data-stu-id="a8e60-229">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="a8e60-230">Esto se puede hacer de dos maneras: una escena se puede calcular mediante el controlador o una escena existente que se calculó en el pasado se puede deseriar.</span><span class="sxs-lookup"><span data-stu-id="a8e60-230">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="a8e60-231">Este último es útil para trabajar con SceneUnderstanding durante el desarrollo, donde las aplicaciones y experiencias se pueden crear prototipos rápidamente sin un dispositivo de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="a8e60-231">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="a8e60-232">Las escenas se calculan mediante SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="a8e60-232">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="a8e60-233">Antes de crear una escena, la aplicación debe consultar el dispositivo para asegurarse de que admite SceneUnderstanding, así como para solicitar al usuario acceso a la información que SceneUnderstanding necesita.</span><span class="sxs-lookup"><span data-stu-id="a8e60-233">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="a8e60-234">Si no se llama a RequestAccessAsync(), se producirá un error al calcular una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="a8e60-234">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="a8e60-235">A continuación, calcularemos una nueva escena que se basa en el casco Mixed Reality y tiene un radio de 10 metros.</span><span class="sxs-lookup"><span data-stu-id="a8e60-235">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

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

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="a8e60-236">Inicialización a partir de datos (también conocido como .</span><span class="sxs-lookup"><span data-stu-id="a8e60-236">Initialization from Data (also known as.</span></span> <span data-ttu-id="a8e60-237">la ruta de acceso del equipo)</span><span class="sxs-lookup"><span data-stu-id="a8e60-237">the PC Path)</span></span>

<span data-ttu-id="a8e60-238">Aunque las escenas se pueden calcular para consumo directo, también se pueden calcular en formato serializado para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="a8e60-238">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="a8e60-239">Esto ha demostrado ser útil para el desarrollo, ya que permite a los desarrolladores trabajar en Scene Understanding y probarlo sin necesidad de un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a8e60-239">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="a8e60-240">El acto de serializar una escena es casi idéntico a calcularla; los datos se devuelven a la aplicación en lugar de que el SDK lo deserialice localmente.</span><span class="sxs-lookup"><span data-stu-id="a8e60-240">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="a8e60-241">A continuación, puede deserializarlo usted mismo o guardarlo para su uso futuro.</span><span class="sxs-lookup"><span data-stu-id="a8e60-241">You may then deserialize it yourself or save it for future use.</span></span>

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

### <a name="sceneobject-enumeration"></a><span data-ttu-id="a8e60-242">Enumeración SceneObject</span><span class="sxs-lookup"><span data-stu-id="a8e60-242">SceneObject Enumeration</span></span>

<span data-ttu-id="a8e60-243">Ahora que la aplicación tiene una escena, la aplicación buscará e interactuará con SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="a8e60-243">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="a8e60-244">Para ello, acceda a **la propiedad SceneObjects:**</span><span class="sxs-lookup"><span data-stu-id="a8e60-244">This is done by accessing the **SceneObjects** property:</span></span>

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

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="a8e60-245">Componentes de actualización y refinamiento de componentes</span><span class="sxs-lookup"><span data-stu-id="a8e60-245">Component update and refinding components</span></span>

<span data-ttu-id="a8e60-246">Hay otra función que recupera componentes de la escena denominada ***FindComponent.***</span><span class="sxs-lookup"><span data-stu-id="a8e60-246">There's another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="a8e60-247">Esta función es útil al actualizar objetos de seguimiento y buscarlos en escenas posteriores.</span><span class="sxs-lookup"><span data-stu-id="a8e60-247">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="a8e60-248">El código siguiente calculará una nueva escena con respecto a una escena anterior y, a continuación, buscará el suelo en la nueva escena.</span><span class="sxs-lookup"><span data-stu-id="a8e60-248">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

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

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="a8e60-249">Acceso a mallas y quads desde objetos de escena</span><span class="sxs-lookup"><span data-stu-id="a8e60-249">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="a8e60-250">Una vez que se hayan encontrado sceneObjects, lo más probable es que la aplicación quiera acceder a los datos contenidos en los quads o mallas de los que se compone.</span><span class="sxs-lookup"><span data-stu-id="a8e60-250">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="a8e60-251">Se accede a estos datos con las propiedades \***Quads** _ y _ \*_Meshes_\*\*.</span><span class="sxs-lookup"><span data-stu-id="a8e60-251">This data is accessed with the ***Quads** _ and _ *_Meshes_** properties.</span></span> <span data-ttu-id="a8e60-252">El código siguiente enumerará todos los quads y mallas de nuestro objeto floor.</span><span class="sxs-lookup"><span data-stu-id="a8e60-252">The following code will enumerate all quads and meshes of our floor object.</span></span>

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

<span data-ttu-id="a8e60-253">Observe que es SceneObject el que tiene la transformación relativa al origen de la escena.</span><span class="sxs-lookup"><span data-stu-id="a8e60-253">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="a8e60-254">Esto se debe a que SceneObject representa una instancia de una "cosa" y es localizable en el espacio, los cuádros y las mallas representan la geometría que se transforma en relación con su elemento primario.</span><span class="sxs-lookup"><span data-stu-id="a8e60-254">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="a8e60-255">Es posible que sceneObjects independientes haga referencia a los mismos SceneMesh/SceneQuad SceneComponents, y también es posible que sceneObject tenga más de un SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="a8e60-255">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="a8e60-256">Tratar con transformaciones</span><span class="sxs-lookup"><span data-stu-id="a8e60-256">Dealing with Transforms</span></span>

<span data-ttu-id="a8e60-257">Scene Understanding ha realizado un intento intencionado de alinearse con las representaciones de escena 3D tradicionales al tratar con transformaciones.</span><span class="sxs-lookup"><span data-stu-id="a8e60-257">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="a8e60-258">Por lo tanto, cada escena se limita a un único sistema de coordenadas muy parecido a las representaciones ambientales 3D más comunes.</span><span class="sxs-lookup"><span data-stu-id="a8e60-258">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="a8e60-259">SceneObjects proporciona su ubicación en relación con ese sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="a8e60-259">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="a8e60-260">Si la aplicación está trabajando con escenas que extienden el límite de lo que proporciona un único origen, puede delimitar SceneObjects a SpatialAnchors o generar varias escenas y combinarlas, pero por motivos de simplicidad suponemos que existen escenas estancas en su propio origen que se localizan mediante un NodeId definido por Scene.OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="a8e60-260">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="a8e60-261">El siguiente código de Unity, por ejemplo, muestra cómo usar las API de Windows Perception y Unity para alinear los sistemas de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="a8e60-261">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="a8e60-262">Consulte [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) y [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) para obtener más información sobre las API de Windows Perception y Mixed Reality los objetos nativos en [Unity](/windows/mixed-reality/unity-xrdevice-advanced) para obtener más información sobre cómo obtener un spatialcoordinateSystem que se corresponda con el origen mundial de Unity.</span><span class="sxs-lookup"><span data-stu-id="a8e60-262">See [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](/windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

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

<span data-ttu-id="a8e60-263">Cada `SceneObject` tiene una transformación, que luego se aplica a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="a8e60-263">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="a8e60-264">En Unity, convertemos a coordenadas a la derecha y asignamos transformaciones locales de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a8e60-264">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

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

### <a name="quad"></a><span data-ttu-id="a8e60-265">cuádruple</span><span class="sxs-lookup"><span data-stu-id="a8e60-265">Quad</span></span>

<span data-ttu-id="a8e60-266">Los quads se diseñaron para ayudar a los escenarios de selección de ubicación en 2D y deben considerarse como extensiones de los elementos de la experiencia de usuario del lienzo 2D.</span><span class="sxs-lookup"><span data-stu-id="a8e60-266">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="a8e60-267">Aunque los quads son componentes de SceneObjects y se pueden representar en 3D, las propias API de Quad asumen que quads son estructuras 2D.</span><span class="sxs-lookup"><span data-stu-id="a8e60-267">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="a8e60-268">Ofrecen información como la extensión, la forma y proporcionan API para la selección de ubicación.</span><span class="sxs-lookup"><span data-stu-id="a8e60-268">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="a8e60-269">Los quads tienen extensiones rectangulares, pero representan superficies 2D con forma arbitraria.</span><span class="sxs-lookup"><span data-stu-id="a8e60-269">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="a8e60-270">Para habilitar la selección de ubicación en estas superficies 2D que interactúan con los cuadrántos del entorno 3D, se ofrecen utilidades para que esta interacción sea posible.</span><span class="sxs-lookup"><span data-stu-id="a8e60-270">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="a8e60-271">Actualmente, Scene Understanding proporciona dos funciones de este tipo, **FindCentermostPlacement** y **GetSurfaceMask.**</span><span class="sxs-lookup"><span data-stu-id="a8e60-271">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetSurfaceMask**.</span></span> <span data-ttu-id="a8e60-272">FindCentermostPlacement es una API de alto nivel que localiza una posición en el cuadrángolo donde se puede colocar un objeto e intentará encontrar la mejor ubicación para el objeto, lo que garantiza que el rectángulo de selección que proporcione permanecerá en la superficie subyacente.</span><span class="sxs-lookup"><span data-stu-id="a8e60-272">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="a8e60-273">Las coordenadas de la salida son relativas al cuadrándular en "quad space" y la esquina superior izquierda es (x = 0, y = 0), igual que lo sería con otros tipos de ventanas Rect.</span><span class="sxs-lookup"><span data-stu-id="a8e60-273">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="a8e60-274">Asegúrese de tener esto en cuenta al trabajar con los orígenes de sus propios objetos.</span><span class="sxs-lookup"><span data-stu-id="a8e60-274">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="a8e60-275">En el ejemplo siguiente se muestra cómo buscar la ubicación colocable más central y delimitar un holograma al cuadránculo.</span><span class="sxs-lookup"><span data-stu-id="a8e60-275">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

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

<span data-ttu-id="a8e60-276">Los pasos 1 a 4 dependen en gran medida de su marco o implementación concretos, pero los temas deben ser similares.</span><span class="sxs-lookup"><span data-stu-id="a8e60-276">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="a8e60-277">Es importante tener en cuenta que el quad simplemente representa un plano 2D delimitado que se localiza en el espacio.</span><span class="sxs-lookup"><span data-stu-id="a8e60-277">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="a8e60-278">Al hacer que el motor o el marco sepan dónde está el cuádigo y raíz de los objetos en relación con el cuadrángrama, los hologramas se ubicarán correctamente con respecto al mundo real.</span><span class="sxs-lookup"><span data-stu-id="a8e60-278">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="a8e60-279">En malla</span><span class="sxs-lookup"><span data-stu-id="a8e60-279">Mesh</span></span>

<span data-ttu-id="a8e60-280">Las mallas representan representaciones geométricas de objetos o entornos.</span><span class="sxs-lookup"><span data-stu-id="a8e60-280">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="a8e60-281">De forma muy similar a la asignación [espacial,](../../design/spatial-mapping.md)los datos de índice de malla y vértice proporcionados con cada malla de superficie espacial usan el mismo diseño conocido que los búferes de vértice e índice que se usan para representar mallas de triángulo en todas las API de representación modernas.</span><span class="sxs-lookup"><span data-stu-id="a8e60-281">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="a8e60-282">Las posiciones de vértice se proporcionan en el sistema de coordenadas de `Scene` .</span><span class="sxs-lookup"><span data-stu-id="a8e60-282">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="a8e60-283">Las API específicas que se usan para hacer referencia a estos datos son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="a8e60-283">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="a8e60-284">El código siguiente proporciona un ejemplo de generación de una lista de triángulos a partir de la estructura de malla:</span><span class="sxs-lookup"><span data-stu-id="a8e60-284">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="a8e60-285">Los búferes de índice o vértice deben ser >= los recuentos de índice o vértice, pero de lo contrario pueden tener un tamaño arbitrario que permita una reutilización eficaz de la memoria.</span><span class="sxs-lookup"><span data-stu-id="a8e60-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="a8e60-286">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="a8e60-286">ColliderMesh</span></span>

<span data-ttu-id="a8e60-287">Los objetos de escena proporcionan acceso a los datos de malla y malla de colisionador a través de las propiedades Meshes y ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="a8e60-287">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="a8e60-288">Estas mallas siempre coincidirán, lo que significa que el índice i'th de la propiedad Meshes representa la misma geometría que el índice i'th de la propiedad ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="a8e60-288">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="a8e60-289">Si el runtime/objeto admite mallas de colisionador, se garantiza que obtiene el polígono más bajo y la aproximación de orden más alto y es una buena práctica usar ColliderMeshes dondequiera que la aplicación use colisiondores.</span><span class="sxs-lookup"><span data-stu-id="a8e60-289">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="a8e60-290">Si el sistema no admite colisiones, el objeto Mesh devuelto en ColliderMeshes será el mismo objeto que la malla que reduce las restricciones de memoria.</span><span class="sxs-lookup"><span data-stu-id="a8e60-290">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="a8e60-291">Desarrollo con la comprensión de la escena</span><span class="sxs-lookup"><span data-stu-id="a8e60-291">Developing with scene understanding</span></span>

<span data-ttu-id="a8e60-292">En este punto, debe comprender los bloques de creación principales de la escena que comprenden el entorno de ejecución y el SDK.</span><span class="sxs-lookup"><span data-stu-id="a8e60-292">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="a8e60-293">La mayor parte de la potencia y complejidad radica en los patrones de acceso, la interacción con marcos 3D y las herramientas que se pueden escribir sobre estas API para realizar tareas más avanzadas, como el planeamiento espacial, el análisis de sala, la navegación, la física, etc.</span><span class="sxs-lookup"><span data-stu-id="a8e60-293">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="a8e60-294">Esperamos capturar estos datos en ejemplos que, con suerte, le guiarán en la dirección adecuada para hacer que sus escenarios resalten.</span><span class="sxs-lookup"><span data-stu-id="a8e60-294">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="a8e60-295">Si hay ejemplos o escenarios que no estamos abordando, háganoslo saber e intentaremos documentar o crear prototipos de lo que necesita.</span><span class="sxs-lookup"><span data-stu-id="a8e60-295">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="a8e60-296">¿Dónde puedo obtener código de ejemplo?</span><span class="sxs-lookup"><span data-stu-id="a8e60-296">Where can I get sample code?</span></span>

<span data-ttu-id="a8e60-297">El código de ejemplo de Scene Understanding para Unity se puede encontrar en nuestra [página de ejemplo de Unity.](https://github.com/sceneunderstanding-microsoft/unitysample)</span><span class="sxs-lookup"><span data-stu-id="a8e60-297">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="a8e60-298">Esta aplicación le permitirá comunicarse con el dispositivo y representar los distintos objetos de escena, o bien, le permitirá cargar una escena serializada en el equipo y le permitirá experimentar Scene Understanding sin un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a8e60-298">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="a8e60-299">¿Dónde puedo obtener escenas de ejemplo?</span><span class="sxs-lookup"><span data-stu-id="a8e60-299">Where can I get sample scenes?</span></span>

<span data-ttu-id="a8e60-300">Si tienes un HoloLens2, puedes guardar cualquier escena que hayas capturado guardando la salida de ComputeSerializedAsync en un archivo y deserializarla por tu comodidad.</span><span class="sxs-lookup"><span data-stu-id="a8e60-300">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="a8e60-301">Si no tiene un dispositivo HoloLens2 pero quiere jugar con Scene Understanding, deberá descargar una escena capturada previamente.</span><span class="sxs-lookup"><span data-stu-id="a8e60-301">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="a8e60-302">El ejemplo Scene Understanding se distribuye actualmente con escenas serializadas que se pueden descargar y usar según su propia comodidad.</span><span class="sxs-lookup"><span data-stu-id="a8e60-302">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="a8e60-303">Puede encontrarlos aquí:</span><span class="sxs-lookup"><span data-stu-id="a8e60-303">You can find them here:</span></span>

[<span data-ttu-id="a8e60-304">Escenas de ejemplo de descripción de la escena</span><span class="sxs-lookup"><span data-stu-id="a8e60-304">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a><span data-ttu-id="a8e60-305">Consulta también</span><span class="sxs-lookup"><span data-stu-id="a8e60-305">See also</span></span>

* [<span data-ttu-id="a8e60-306">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="a8e60-306">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="a8e60-307">Descripción de escenas</span><span class="sxs-lookup"><span data-stu-id="a8e60-307">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="a8e60-308">Ejemplo de Unity</span><span class="sxs-lookup"><span data-stu-id="a8e60-308">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)