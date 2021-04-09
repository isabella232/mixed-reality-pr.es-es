---
title: Tutoriales de MRTK - 4. Posicionamiento de los objetos en la escena
description: En este curso se muestra cómo colocar objetos en la escena y cómo usar Mixed Reality Toolkit (MRTK) para organizar los objetos en una cuadrícula.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, solvers, grid object collection
ms.localizationpriority: high
ms.openlocfilehash: 28cebe871e1046e8668a079affabf6167632cfa4
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105983040"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="be014-105">4. Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="be014-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="be014-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="be014-106">Overview</span></span>

<span data-ttu-id="be014-107">En este tutorial, colocará los objetos proporcionados por los recursos del tutorial en la escena.</span><span class="sxs-lookup"><span data-stu-id="be014-107">In this tutorial, you will position the provided objects from the tutorial assets in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="be014-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="be014-108">Objectives</span></span>

* <span data-ttu-id="be014-109">Obtener información sobre cómo colocar objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="be014-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="be014-110">Aprender a usar la característica de colección de objetos de la cuadrícula de MRTK</span><span class="sxs-lookup"><span data-stu-id="be014-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="be014-111">Creación del objeto principal</span><span class="sxs-lookup"><span data-stu-id="be014-111">Creating the parent object</span></span>

<span data-ttu-id="be014-112">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena:</span><span class="sxs-lookup"><span data-stu-id="be014-112">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Menú contextual emergente de Create Empty (Crear vacío) de Unity](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="be014-114">Para mostrar las ventanas Scene (Escena) y Game (Juego) una al lado de otra como se muestra en la imagen anterior, arrastra la ventana Game (Juego) al lado derecho de la ventana Scene (Escena).</span><span class="sxs-lookup"><span data-stu-id="be014-114">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="be014-115">Para obtener más información sobre cómo personalizar el área de trabajo, puedes consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalización del área de trabajo</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="be014-115">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="be014-116">Haga clic con el botón derecho en el objeto recién creado, seleccione **Rename** (Cambiar nombre) y cambie el nombre a **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="be014-116">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Menú contextual emergente Rename (Cambiar nombre) de Unity](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="be014-118">Con el objeto RoverExplorer todavía seleccionado, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="be014-118">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="be014-119">**Posición**: X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="be014-119">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="be014-120">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="be014-120">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="be014-121">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="be014-121">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto RoverExplorer seleccionado y colocado](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> <span data-ttu-id="be014-123">La cámara representa la cabeza del usuario y se coloca en el origen, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="be014-123">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="be014-124">En general, 1 unidad en Unity es aproximadamente 1 metro en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="be014-124">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="be014-125">Sin embargo, existen excepciones; por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala.</span><span class="sxs-lookup"><span data-stu-id="be014-125">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="be014-126">En el escenario anterior, el objeto RoverExplorer se coloca a 2 metros por delante y 0,6 metros por debajo de la cabeza del usuario.</span><span class="sxs-lookup"><span data-stu-id="be014-126">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="be014-127">Adición de los elementos prefabricados del tutorial</span><span class="sxs-lookup"><span data-stu-id="be014-127">Adding the tutorial prefabs</span></span>

<span data-ttu-id="be014-128">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**:</span><span class="sxs-lookup"><span data-stu-id="be014-128">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Ventana Project (Proyecto) de Unity con la carpeta Prefabs seleccionada](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="be014-130">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">objeto prefabricado</a> es un objeto GameObject preconfigurado almacenado como un recurso de Unity que se puede reutilizar en todo el proyecto.</span><span class="sxs-lookup"><span data-stu-id="be014-130">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="be014-131">En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **Table** (Tabla) sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="be014-131">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="be014-132">**Posición**: X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="be014-132">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="be014-133">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="be014-133">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="be014-134">**Escala**: X = 1.2, Y = 0.01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="be014-134">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity con el objeto prefabricado Table recién agregado seleccionado y colocado](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="be014-136">Para mostrar la escena tal y como se muestra en la imagen anterior, use <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo de escena), situado en la esquina superior derecha de la ventana Scene (Escena) para ajustar el ángulo de visualización a lo largo del eje Z, haga doble clic en el objeto MixedRealityPlayspace para enfocar la cámara y acérquese según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="be014-136">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="be014-137">En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **RoverAssembly** sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="be014-137">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="be014-138">**Posición**: X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="be014-138">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="be014-139">**Rotación**: X = 0, Y = 135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="be014-139">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="be014-140">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="be014-140">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto prefabricado RoverAssembly recién agregado seleccionado y colocado](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="be014-142">Organización de los objetos de una colección</span><span class="sxs-lookup"><span data-stu-id="be014-142">Organizing objects in a collection</span></span>

<span data-ttu-id="be014-143">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **RoverParts** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="be014-143">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="be014-144">**Posición**: X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="be014-144">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="be014-145">**Rotación**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="be014-145">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="be014-146">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="be014-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto RoverParts recién creado seleccionado y colocado](images/mr-learning-base/base-04-section3-step1-1.png)

<span data-ttu-id="be014-148">En la ventana Hierarchy (Jerarquía), seleccione todos los objetos secundarios de RoverExplorer > RoverAssembly > RoverModel > **Parts**, haga clic derecho en ellos y seleccione **Duplicate** (Duplicar) para crear una copia de cada una de las partes:</span><span class="sxs-lookup"><span data-stu-id="be014-148">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity con todos los objetos Parts seleccionados y el menú contextual emergente Duplicate](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="be014-150">Para seleccionar varios objetos adyacentes, mantenga presionada la tecla Mayús mientras usa el mouse para seleccionar el primer y el último objeto.</span><span class="sxs-lookup"><span data-stu-id="be014-150">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="be014-151">Con los objetos secundarios de Parts recién duplicados todavía seleccionados, haga clic en ellos y arrástrelos sobre el objeto **RoverParts** para convertirlos en objetos secundarios del objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="be014-151">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity con los objetos Parts recién duplicados como elementos secundarios del objeto RoverParts](images/mr-learning-base/base-04-section3-step1-3.png)

<span data-ttu-id="be014-153">Para que resulte más fácil trabajar con esta escena, en la ventana Jerarquía, haga clic en el icono del **ojo** situado a la izquierda del objeto para desactivar la **visibilidad de la escena** del objeto **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="be014-153">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="be014-154">Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego:</span><span class="sxs-lookup"><span data-stu-id="be014-154">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity con visibilidad de la escena RoverAssembly desactivada](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> <span data-ttu-id="be014-156">Para obtener más información sobre los controles de visibilidad de la escena y cómo puede usarlos para optimizar la vista de la escena y el flujo de trabajo, puede consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidad de la escena </a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="be014-156">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="be014-157">En la ventana Hierarchy (Jerarquía), borre los nombres de los objetos secundarios de RoverParts reemplazando el **(1)** anexado por **_Part**:</span><span class="sxs-lookup"><span data-stu-id="be014-157">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity con el nombre de las partes duplicadas borrado](images/mr-learning-base/base-04-section3-step1-5.png)

<span data-ttu-id="be014-159">En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverParts**; a continuación, en la ventana Inspector, haga clic en el botón **Add Component** (Agregar componente) y busque y seleccione **GridObjectCollection** para agregar el componente GridObjectCollection al objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="be014-159">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Objeto RoverParts de Unity con Add Component (Agregar componente) GridObjectCollection en curso](images/mr-learning-base/base-04-section3-step1-6.png)

<span data-ttu-id="be014-161">Configure los valores del componente **GridObjectCollection** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="be014-161">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="be014-162">**Tipo de orden**: Alfabético</span><span class="sxs-lookup"><span data-stu-id="be014-162">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="be014-163">**Diseño**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="be014-163">**Layout**: Horizontal</span></span>
* <span data-ttu-id="be014-164">**Ancho de celda**: 0.25</span><span class="sxs-lookup"><span data-stu-id="be014-164">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="be014-165">**Distancia desde el elemento principal**: 0.38</span><span class="sxs-lookup"><span data-stu-id="be014-165">**Distance from parent**: 0.38</span></span>

![Unity con el componente GridObjectCollection configurado](images/mr-learning-base/base-04-section3-step1-7.png)

<span data-ttu-id="be014-167">A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios de RoverParts:</span><span class="sxs-lookup"><span data-stu-id="be014-167">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity con el componente GridObjectCollection aplicado](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="be014-169">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="be014-169">Congratulations</span></span>

<span data-ttu-id="be014-170">En este tutorial, ha aprendido a colocar objetos en la escena en relación con el usuario y a usar la característica de colección de objetos de la cuadrícula de MRTK para organizar los objetos de una colección.</span><span class="sxs-lookup"><span data-stu-id="be014-170">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="be014-171">Tutorial siguiente: 5. Creación de contenido dinámico mediante el uso de solucionadores</span><span class="sxs-lookup"><span data-stu-id="be014-171">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
