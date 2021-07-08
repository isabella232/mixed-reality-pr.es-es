---
title: Tutoriales de MRTK - 4. Posicionamiento de los objetos en la escena
description: En este curso se muestra cómo colocar objetos en la escena y cómo usar Mixed Reality Toolkit (MRTK) para organizar los objetos en una cuadrícula.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, solvers, grid object collection
ms.localizationpriority: high
ms.openlocfilehash: d5d10893ba8274139c6e09b8cd426d58a0b3a0cb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175477"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="07748-105">4. Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="07748-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="07748-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="07748-106">Overview</span></span>

<span data-ttu-id="07748-107">En este tutorial, colocará los objetos proporcionados por los recursos del tutorial en la escena.</span><span class="sxs-lookup"><span data-stu-id="07748-107">In this tutorial, you will position the provided objects from the tutorial assets in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="07748-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="07748-108">Objectives</span></span>

* <span data-ttu-id="07748-109">Obtener información sobre cómo colocar objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="07748-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="07748-110">Aprender a usar la característica de colección de objetos de la cuadrícula de MRTK</span><span class="sxs-lookup"><span data-stu-id="07748-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="07748-111">Importación de los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="07748-111">Importing the TextMeshPro Essential Resources</span></span>
<span data-ttu-id="07748-112">Los elementos de la interfaz de usuario de MRTK requieren los recursos esenciales de TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="07748-112">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="07748-113">En el menú de Unity, seleccione **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Ventana > TextMeshPro > Importar recursos esenciales de TMP) para abrir la ventana Import Unity Package (Importar paquete de Unity):</span><span class="sxs-lookup"><span data-stu-id="07748-113">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Ruta de menú Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="07748-115">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="07748-115">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Ventana Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="07748-117">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="07748-117">Importing the tutorial assets</span></span>

<span data-ttu-id="07748-118">Descargue el siguiente paquete personalizado de Unity.</span><span class="sxs-lookup"><span data-stu-id="07748-118">Download the following Unity custom package.</span></span> <span data-ttu-id="07748-119">Este paquete incluye recursos 3D, como el róver de Marte que vamos a usar en este tutorial.</span><span class="sxs-lookup"><span data-stu-id="07748-119">This package includes 3D assets such as Mars Rover that we are going to use in this tutorial.</span></span>

* [<span data-ttu-id="07748-120">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="07748-120">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="07748-121">Para importar un paquete personalizado de Unity, seleccione **Assets** > **Import Package** > **Custom Package...** (Recursos > Importar paquete > Paquete personalizado...) para abrir la ventana Import package... (Importar paquete...):</span><span class="sxs-lookup"><span data-stu-id="07748-121">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Importación de un paquete personalizado](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="07748-123">En la ventana Import package... (Importar paquete...), seleccione el paquete **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** que ha descargado y haga clic en el botón Open (Abrir):</span><span class="sxs-lookup"><span data-stu-id="07748-123">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Selección de un paquete de recursos](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="07748-125">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón All (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón Import (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="07748-125">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Selección de todos los recursos que se van a importar](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="07748-127">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="07748-127">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Ventana de proyecto de Unity después de importar recursos](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="creating-the-parent-object"></a><span data-ttu-id="07748-129">Creación del objeto principal</span><span class="sxs-lookup"><span data-stu-id="07748-129">Creating the parent object</span></span>

<span data-ttu-id="07748-130">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena:</span><span class="sxs-lookup"><span data-stu-id="07748-130">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Menú contextual emergente de Create Empty (Crear vacío) de Unity](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="07748-132">Para mostrar las ventanas Scene (Escena) y Game (Juego) una al lado de otra como se muestra en la imagen anterior, arrastra la ventana Game (Juego) al lado derecho de la ventana Scene (Escena).</span><span class="sxs-lookup"><span data-stu-id="07748-132">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="07748-133">Para obtener más información sobre cómo personalizar el área de trabajo, puedes consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalización del área de trabajo</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="07748-133">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="07748-134">Haga clic con el botón derecho en el objeto recién creado, seleccione **Rename** (Cambiar nombre) y cambie el nombre a **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="07748-134">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Menú contextual emergente Rename (Cambiar nombre) de Unity](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="07748-136">Con el objeto RoverExplorer todavía seleccionado, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="07748-136">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="07748-137">**Posición**: X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="07748-137">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="07748-138">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="07748-138">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="07748-139">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="07748-139">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto RoverExplorer seleccionado y colocado](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> <span data-ttu-id="07748-141">La cámara representa la cabeza del usuario y se coloca en el origen, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="07748-141">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="07748-142">En general, 1 unidad en Unity es aproximadamente 1 metro en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="07748-142">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="07748-143">Sin embargo, existen excepciones; por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala.</span><span class="sxs-lookup"><span data-stu-id="07748-143">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="07748-144">En el escenario anterior, el objeto RoverExplorer se coloca a 2 metros por delante y 0,6 metros por debajo de la cabeza del usuario.</span><span class="sxs-lookup"><span data-stu-id="07748-144">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="07748-145">Adición de los elementos prefabricados del tutorial</span><span class="sxs-lookup"><span data-stu-id="07748-145">Adding the tutorial prefabs</span></span>

<span data-ttu-id="07748-146">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**:</span><span class="sxs-lookup"><span data-stu-id="07748-146">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Ventana Project (Proyecto) de Unity con la carpeta Prefabs seleccionada](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="07748-148">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">objeto prefabricado</a> es un objeto GameObject preconfigurado almacenado como un recurso de Unity que se puede reutilizar en todo el proyecto.</span><span class="sxs-lookup"><span data-stu-id="07748-148">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="07748-149">En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **Table** (Tabla) sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="07748-149">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="07748-150">**Posición**: X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="07748-150">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="07748-151">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="07748-151">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="07748-152">**Escala**: X = 1.2, Y = 0.01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="07748-152">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity con el objeto prefabricado Table recién agregado seleccionado y colocado](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="07748-154">Para mostrar la escena tal y como se muestra en la imagen anterior, use <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo de escena), situado en la esquina superior derecha de la ventana Scene (Escena) para ajustar el ángulo de visualización a lo largo del eje Z, haga doble clic en el objeto MixedRealityPlayspace para enfocar la cámara y acérquese según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="07748-154">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="07748-155">En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **RoverAssembly** sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="07748-155">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="07748-156">**Posición**: X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="07748-156">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="07748-157">**Rotación**: X = 0, Y = 135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="07748-157">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="07748-158">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="07748-158">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto prefabricado RoverAssembly recién agregado seleccionado y colocado](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="07748-160">Organización de los objetos de una colección</span><span class="sxs-lookup"><span data-stu-id="07748-160">Organizing objects in a collection</span></span>

<span data-ttu-id="07748-161">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **RoverParts** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="07748-161">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="07748-162">**Posición**: X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="07748-162">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="07748-163">**Rotación**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="07748-163">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="07748-164">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="07748-164">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto RoverParts recién creado seleccionado y colocado](images/mr-learning-base/base-04-section3-step1-1.png)

<span data-ttu-id="07748-166">En la ventana Hierarchy (Jerarquía), seleccione todos los objetos secundarios de RoverExplorer > RoverAssembly > RoverModel > **Parts**, haga clic derecho en ellos y seleccione **Duplicate** (Duplicar) para crear una copia de cada una de las partes:</span><span class="sxs-lookup"><span data-stu-id="07748-166">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity con todos los objetos Parts seleccionados y el menú contextual emergente Duplicate](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="07748-168">Para seleccionar varios objetos adyacentes, mantenga presionada la tecla Mayús mientras usa el mouse para seleccionar el primer y el último objeto.</span><span class="sxs-lookup"><span data-stu-id="07748-168">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="07748-169">Con los objetos secundarios de Parts recién duplicados todavía seleccionados, haga clic en ellos y arrástrelos sobre el objeto **RoverParts** para convertirlos en objetos secundarios del objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="07748-169">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity con los objetos Parts recién duplicados como elementos secundarios del objeto RoverParts](images/mr-learning-base/base-04-section3-step1-3.png)

<span data-ttu-id="07748-171">Para que resulte más fácil trabajar con esta escena, en la ventana Jerarquía, haga clic en el icono del **ojo** situado a la izquierda del objeto para desactivar la **visibilidad de la escena** del objeto **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="07748-171">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="07748-172">Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego:</span><span class="sxs-lookup"><span data-stu-id="07748-172">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity con visibilidad de la escena RoverAssembly desactivada](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> <span data-ttu-id="07748-174">Para obtener más información sobre los controles de visibilidad de la escena y cómo puede usarlos para optimizar la vista de la escena y el flujo de trabajo, puede consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidad de la escena </a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="07748-174">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="07748-175">En la ventana Hierarchy (Jerarquía), borre los nombres de los objetos secundarios de RoverParts reemplazando el **(1)** anexado por **_Part**:</span><span class="sxs-lookup"><span data-stu-id="07748-175">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity con el nombre de las partes duplicadas borrado](images/mr-learning-base/base-04-section3-step1-5.png)

<span data-ttu-id="07748-177">En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverParts**; a continuación, en la ventana Inspector, haga clic en el botón **Add Component** (Agregar componente) y busque y seleccione **GridObjectCollection** para agregar el componente GridObjectCollection al objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="07748-177">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Objeto RoverParts de Unity con Add Component (Agregar componente) GridObjectCollection en curso](images/mr-learning-base/base-04-section3-step1-6.png)

<span data-ttu-id="07748-179">Configure los valores del componente **GridObjectCollection** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="07748-179">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="07748-180">**Tipo de orden**: Alfabético</span><span class="sxs-lookup"><span data-stu-id="07748-180">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="07748-181">**Diseño**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="07748-181">**Layout**: Horizontal</span></span>
* <span data-ttu-id="07748-182">**Ancho de celda**: 0.25</span><span class="sxs-lookup"><span data-stu-id="07748-182">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="07748-183">**Distancia desde el elemento principal**: 0.38</span><span class="sxs-lookup"><span data-stu-id="07748-183">**Distance from parent**: 0.38</span></span>

![Unity con el componente GridObjectCollection configurado](images/mr-learning-base/base-04-section3-step1-7.png)

<span data-ttu-id="07748-185">A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios de RoverParts:</span><span class="sxs-lookup"><span data-stu-id="07748-185">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity con el componente GridObjectCollection aplicado](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="07748-187">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="07748-187">Congratulations</span></span>

<span data-ttu-id="07748-188">En este tutorial, ha aprendido a colocar objetos en la escena en relación con el usuario y a usar la característica de colección de objetos de la cuadrícula de MRTK para organizar los objetos de una colección.</span><span class="sxs-lookup"><span data-stu-id="07748-188">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="07748-189">Tutorial siguiente: 5. Creación de contenido dinámico mediante el uso de solucionadores</span><span class="sxs-lookup"><span data-stu-id="07748-189">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
