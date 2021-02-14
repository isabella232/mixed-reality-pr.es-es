---
title: Tutoriales de MRTK - 4. Posicionamiento de los objetos en la escena
description: En este curso se muestra cómo colocar objetos en la escena y cómo usar Mixed Reality Toolkit (MRTK) para organizar los objetos en una cuadrícula.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, solvers, grid object collection
ms.localizationpriority: high
ms.openlocfilehash: 9087800eca3536704ed4ef01a5d8178720b6a875
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590533"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="71bad-105">4. Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="71bad-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="71bad-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="71bad-106">Overview</span></span>

<span data-ttu-id="71bad-107">En este tutorial, importará los recursos del tutorial y colocará los objetos proporcionados en la escena.</span><span class="sxs-lookup"><span data-stu-id="71bad-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="71bad-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="71bad-108">Objectives</span></span>

* <span data-ttu-id="71bad-109">Obtener información sobre cómo colocar objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="71bad-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="71bad-110">Aprender a usar la característica de colección de objetos de la cuadrícula de MRTK</span><span class="sxs-lookup"><span data-stu-id="71bad-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="71bad-111">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="71bad-111">Importing the tutorial assets</span></span>

<span data-ttu-id="71bad-112">Descargue el siguiente paquete personalizado de Unity:</span><span class="sxs-lookup"><span data-stu-id="71bad-112">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="71bad-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="71bad-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="71bad-114">Para importar un paquete personalizado de Unity, seleccione **Assets** > **Import Package** > **Custom Package...** (Recursos > Importar paquete > Paquete personalizado...) para abrir la ventana Import package... (Importar paquete...):</span><span class="sxs-lookup"><span data-stu-id="71bad-114">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](images/mr-learning-base/base-04-section1-step1-1.png)

<span data-ttu-id="71bad-116">En la ventana Import package... (Importar paquete...), seleccione el paquete **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage** que ha descargado y haga clic en el botón Open (Abrir):</span><span class="sxs-lookup"><span data-stu-id="71bad-116">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage** you downloaded and click the Open button:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="71bad-118">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón All (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón Import (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="71bad-118">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](images/mr-learning-base/base-04-section1-step1-3.png)

<span data-ttu-id="71bad-120">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="71bad-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](images/mr-learning-base/base-04-section1-step1-4.png)

## <a name="creating-the-parent-object"></a><span data-ttu-id="71bad-122">Creación del objeto principal</span><span class="sxs-lookup"><span data-stu-id="71bad-122">Creating the parent object</span></span>

<span data-ttu-id="71bad-123">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena:</span><span class="sxs-lookup"><span data-stu-id="71bad-123">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Menú contextual emergente de Create Empty (Crear vacío) de Unity](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="71bad-125">Para mostrar las ventanas Scene (Escena) y Game (Juego) una al lado de otra como se muestra en la imagen anterior, arrastra la ventana Game (Juego) al lado derecho de la ventana Scene (Escena).</span><span class="sxs-lookup"><span data-stu-id="71bad-125">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="71bad-126">Para obtener más información sobre cómo personalizar el área de trabajo, puedes consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalización del área de trabajo</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="71bad-126">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="71bad-127">Haga clic con el botón derecho en el objeto recién creado, seleccione **Rename** (Cambiar nombre) y cambie el nombre a **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="71bad-127">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Menú contextual emergente Rename (Cambiar nombre) de Unity](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="71bad-129">Con el objeto RoverExplorer todavía seleccionado, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="71bad-129">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="71bad-130">**Posición**: X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="71bad-130">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="71bad-131">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="71bad-131">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="71bad-132">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="71bad-132">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto RoverExplorer seleccionado y colocado](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="71bad-134">La cámara representa la cabeza del usuario y se coloca en el origen, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="71bad-134">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="71bad-135">En general, 1 unidad en Unity es aproximadamente 1 metro en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="71bad-135">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="71bad-136">Sin embargo, existen excepciones; por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala.</span><span class="sxs-lookup"><span data-stu-id="71bad-136">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="71bad-137">En el escenario anterior, el objeto RoverExplorer se coloca a 2 metros por delante y 0,6 metros por debajo de la cabeza del usuario.</span><span class="sxs-lookup"><span data-stu-id="71bad-137">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="71bad-138">Adición de los elementos prefabricados del tutorial</span><span class="sxs-lookup"><span data-stu-id="71bad-138">Adding the tutorial prefabs</span></span>

<span data-ttu-id="71bad-139">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**:</span><span class="sxs-lookup"><span data-stu-id="71bad-139">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Ventana Project (Proyecto) de Unity con la carpeta Prefabs seleccionada](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="71bad-141">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">objeto prefabricado</a> es un objeto GameObject preconfigurado almacenado como un recurso de Unity que se puede reutilizar en todo el proyecto.</span><span class="sxs-lookup"><span data-stu-id="71bad-141">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="71bad-142">En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **Table** (Tabla) sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="71bad-142">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="71bad-143">**Posición**: X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="71bad-143">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="71bad-144">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="71bad-144">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="71bad-145">**Escala**: X = 1.2, Y = 0.01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="71bad-145">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity con el objeto prefabricado Table recién agregado seleccionado y colocado](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="71bad-147">Para mostrar la escena tal y como se muestra en la imagen anterior, use <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo de escena), situado en la esquina superior derecha de la ventana Scene (Escena) para ajustar el ángulo de visualización a lo largo del eje Z, haga doble clic en el objeto MixedRealityPlayspace para enfocar la cámara y acérquese según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="71bad-147">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="71bad-148">En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **RoverAssembly** sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="71bad-148">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="71bad-149">**Posición**: X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="71bad-149">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="71bad-150">**Rotación**: X = 0, Y = 135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="71bad-150">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="71bad-151">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="71bad-151">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto prefabricado RoverAssembly recién agregado seleccionado y colocado](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="71bad-153">Organización de los objetos de una colección</span><span class="sxs-lookup"><span data-stu-id="71bad-153">Organizing objects in a collection</span></span>

<span data-ttu-id="71bad-154">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **RoverParts** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="71bad-154">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="71bad-155">**Posición**: X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="71bad-155">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="71bad-156">**Rotación**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="71bad-156">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="71bad-157">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="71bad-157">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto RoverParts recién creado seleccionado y colocado](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="71bad-159">En la ventana Hierarchy (Jerarquía), seleccione todos los objetos secundarios de RoverExplorer > RoverAssembly > RoverModel > **Parts**, haga clic derecho en ellos y seleccione **Duplicate** (Duplicar) para crear una copia de cada una de las partes:</span><span class="sxs-lookup"><span data-stu-id="71bad-159">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity con todos los objetos Parts seleccionados y el menú contextual emergente Duplicate](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="71bad-161">Para seleccionar varios objetos adyacentes, mantenga presionada la tecla Mayús mientras usa el mouse para seleccionar el primer y el último objeto.</span><span class="sxs-lookup"><span data-stu-id="71bad-161">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="71bad-162">Con los objetos secundarios de Parts recién duplicados todavía seleccionados, haga clic en ellos y arrástrelos sobre el objeto **RoverParts** para convertirlos en objetos secundarios del objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="71bad-162">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity con los objetos Parts recién duplicados como elementos secundarios del objeto RoverParts](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="71bad-164">Para que resulte más fácil trabajar con esta escena, en la ventana Jerarquía, haga clic en el icono del **ojo** situado a la izquierda del objeto para desactivar la **visibilidad de la escena** del objeto **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="71bad-164">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="71bad-165">Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego:</span><span class="sxs-lookup"><span data-stu-id="71bad-165">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity con visibilidad de la escena RoverAssembly desactivada](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="71bad-167">Para obtener más información sobre los controles de visibilidad de la escena y cómo puede usarlos para optimizar la vista de la escena y el flujo de trabajo, puede consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidad de la escena </a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="71bad-167">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="71bad-168">En la ventana Hierarchy (Jerarquía), borre los nombres de los objetos secundarios de RoverParts reemplazando el **(1)** anexado por **_Part**:</span><span class="sxs-lookup"><span data-stu-id="71bad-168">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity con el nombre de las partes duplicadas borrado](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="71bad-170">En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverParts**; a continuación, en la ventana Inspector, haga clic en el botón **Add Component** (Agregar componente) y busque y seleccione **GridObjectCollection** para agregar el componente GridObjectCollection al objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="71bad-170">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Objeto RoverParts de Unity con Add Component (Agregar componente) GridObjectCollection en curso](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="71bad-172">Configure los valores del componente **GridObjectCollection** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="71bad-172">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="71bad-173">**Tipo de orden**: Alfabético</span><span class="sxs-lookup"><span data-stu-id="71bad-173">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="71bad-174">**Diseño**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="71bad-174">**Layout**: Horizontal</span></span>
* <span data-ttu-id="71bad-175">**Ancho de celda**: 0.25</span><span class="sxs-lookup"><span data-stu-id="71bad-175">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="71bad-176">**Distancia desde el elemento principal**: 0.38</span><span class="sxs-lookup"><span data-stu-id="71bad-176">**Distance from parent**: 0.38</span></span>

![Unity con el componente GridObjectCollection configurado](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="71bad-178">A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios de RoverParts:</span><span class="sxs-lookup"><span data-stu-id="71bad-178">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity con el componente GridObjectCollection aplicado](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="71bad-180">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="71bad-180">Congratulations</span></span>

<span data-ttu-id="71bad-181">En este tutorial, ha aprendido a colocar objetos en la escena en relación con el usuario y a usar la característica de colección de objetos de la cuadrícula de MRTK para organizar los objetos de una colección.</span><span class="sxs-lookup"><span data-stu-id="71bad-181">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="71bad-182">Tutorial siguiente: 5. Creación de contenido dinámico mediante el uso de solucionadores</span><span class="sxs-lookup"><span data-stu-id="71bad-182">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
