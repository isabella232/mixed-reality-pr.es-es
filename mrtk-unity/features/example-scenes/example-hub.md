---
title: Centro de conectividad de ejemplos de MRTK
description: Información general sobre escenas de ejemplo en MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: b7a55e46b2c283b5a75395b9e99874af6020a171
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282000"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="4a316-104">Centro de conectividad de ejemplos de MRTK</span><span class="sxs-lookup"><span data-stu-id="4a316-104">MRTK Examples Hub</span></span>

![Centro de conectividad de ejemplos de MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="4a316-106">El centro de ejemplos de MRTK es una escena de Unity que facilita la experiencia de varias escenas.</span><span class="sxs-lookup"><span data-stu-id="4a316-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="4a316-107">Usa el sistema de escena de MRTK para cargar & descargar las escenas.</span><span class="sxs-lookup"><span data-stu-id="4a316-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="4a316-108">**MRTKExamplesHub.unity es** la escena del contenedor que tiene componentes compartidos, como ``MixedRealityToolkit`` y ``MixedRealityPlayspace`` .</span><span class="sxs-lookup"><span data-stu-id="4a316-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="4a316-109">**La escena MRTKExamplesHubMainMenu.unity** tiene los botones de cubo.</span><span class="sxs-lookup"><span data-stu-id="4a316-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="4a316-110">Requisito previo</span><span class="sxs-lookup"><span data-stu-id="4a316-110">Prerequisite</span></span>

<span data-ttu-id="4a316-111">El centro de ejemplos de MRTK usa [scene transition service y](../extensions/scene-transition-service.md) scripts relacionados.</span><span class="sxs-lookup"><span data-stu-id="4a316-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="4a316-112">Si usa MRTK a través de paquetes de Unity, importe **Microsoft.MixedReality.Toolkit. Unity.Extensions.x.x.x.unitypackage,** que forma parte de los [paquetes de versión](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="4a316-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="4a316-113">Si usa MRTK a través del clon del repositorio, ya debe tener la **carpeta MRTK/Extensions** en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4a316-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="4a316-114">MRTKExamplesHub scene y el sistema de escena</span><span class="sxs-lookup"><span data-stu-id="4a316-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="4a316-115">Abra **MRTKExamplesHub.unity,** que se encuentra en Es una escena vacía con `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace y LoadHubOnStartup.</span><span class="sxs-lookup"><span data-stu-id="4a316-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="4a316-116">Esta escena está configurada para usar el sistema de escena de MRTK.</span><span class="sxs-lookup"><span data-stu-id="4a316-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="4a316-117">Haga `MixedRealitySceneSystem` clic en MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="4a316-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="4a316-118">Se mostrará la información del sistema de escena en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="4a316-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="4a316-119">En la parte inferior del inspector, muestra la lista de las escenas definidas en el perfil del sistema de escena.</span><span class="sxs-lookup"><span data-stu-id="4a316-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="4a316-120">Puede hacer clic en los nombres de escena para cargarlos o descargarlos.</span><span class="sxs-lookup"><span data-stu-id="4a316-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="4a316-121">Ejemplo de carga _de la escena de MRTKExamplesHub_ haciendo clic en el nombre de la escena en la lista.</span><span class="sxs-lookup"><span data-stu-id="4a316-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="4a316-122">Ejemplo de carga _de la escena HandInteractionExamples._</span><span class="sxs-lookup"><span data-stu-id="4a316-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="4a316-123">Ejemplo de carga de varias escenas.</span><span class="sxs-lookup"><span data-stu-id="4a316-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="4a316-124">Ejecución de la escena</span><span class="sxs-lookup"><span data-stu-id="4a316-124">Running the scene</span></span>

<span data-ttu-id="4a316-125">La escena funciona tanto en el modo de juego de Unity como en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4a316-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="4a316-126">Ejecute la **escena MRTKExamplesHub** en el editor de Unity y use la simulación de entrada de MRTK para interactuar con el contenido de la escena.</span><span class="sxs-lookup"><span data-stu-id="4a316-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="4a316-127">Para compilar e implementar, basta con compilar la escena **de MRTKExamplesHub** con otras escenas que se incluyen en la lista del sistema de escenas.</span><span class="sxs-lookup"><span data-stu-id="4a316-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="4a316-128">El inspector también facilita la adición de escenas al cuadro de Configuración.</span><span class="sxs-lookup"><span data-stu-id="4a316-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="4a316-129">En el cuadro Configuración, asegúrese de que la escena **de MRTKExamplesHub** se encuentra en la parte superior de la lista en el índice 0.</span><span class="sxs-lookup"><span data-stu-id="4a316-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="4a316-130">Cómo carga MRTKExamplesHub una escena</span><span class="sxs-lookup"><span data-stu-id="4a316-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="4a316-131">En la **escena de MRTKExamplesHub,** puede encontrar el ``ExamplesHubButton`` prefab.</span><span class="sxs-lookup"><span data-stu-id="4a316-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="4a316-132">Hay un objeto **FrontPlate** en el objeto prefab que contiene ``Interactable`` .</span><span class="sxs-lookup"><span data-stu-id="4a316-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="4a316-133">Con el evento y de Interactable, desencadena la función ``OnClick()`` ``OnTouch()`` **LoadContent()** del script **LoadContentScene.**</span><span class="sxs-lookup"><span data-stu-id="4a316-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="4a316-134">En el inspector del script **LoadContentScene,** puede definir el nombre de la escena que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="4a316-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="4a316-135">El script usa la función LoadContent() de Scene System para cargar la escena.</span><span class="sxs-lookup"><span data-stu-id="4a316-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="4a316-136">Consulte la página [Scene System (Sistema de](../scene-system/scene-system-getting-started.md) escena) para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="4a316-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="4a316-137">Volver a la escena del menú principal</span><span class="sxs-lookup"><span data-stu-id="4a316-137">Returning to the main menu scene</span></span>

<span data-ttu-id="4a316-138">Para volver a la escena del menú principal (MRTKExamplesHubMainMenu), puede usar el mismo método scene `LoadContent()` system.</span><span class="sxs-lookup"><span data-stu-id="4a316-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="4a316-139">**ToggleFeaturesPanelExamplesHub.prefab** proporciona el botón "Inicio" que contiene el script **LoadContentScene.**</span><span class="sxs-lookup"><span data-stu-id="4a316-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="4a316-140">Use este elemento prefab o proporcione un botón de inicio personalizado en cada escena para permitir que el usuario vuelva a la escena principal.</span><span class="sxs-lookup"><span data-stu-id="4a316-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="4a316-141">Se puede colocar **ToggleFeaturesPanelExamplesHub.prefab** en la escena **de MRTKExamplesHub** para que siempre sea visible, ya que **MRTKExamplesHub es** una escena de contenedor compartido.</span><span class="sxs-lookup"><span data-stu-id="4a316-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="4a316-142">Asegúrese de ocultar o desactivar **ToggleFeaturesPanel.prefab en** cada escena de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="4a316-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="4a316-143">Agregar botones adicionales</span><span class="sxs-lookup"><span data-stu-id="4a316-143">Adding additional buttons</span></span>

<span data-ttu-id="4a316-144">En el **objeto CubeCollection,** duplique (o agregue) los elementos prefabs _ExampleHubButton_ y haga clic en **Actualizar** colección en `GridObjectCollection` .</span><span class="sxs-lookup"><span data-stu-id="4a316-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="4a316-145">Esto actualizará el diseño del cilindro en función del nuevo número total de botones.</span><span class="sxs-lookup"><span data-stu-id="4a316-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="4a316-146">Consulte la página [Colección de objetos](../ux-building-blocks/object-collection.md) para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="4a316-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="4a316-147">Después de agregar los botones, actualice el nombre de la escena en el script **LoadContentScene** (explicado anteriormente).</span><span class="sxs-lookup"><span data-stu-id="4a316-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="4a316-148">Agregue escenas adicionales al perfil del sistema de escena.</span><span class="sxs-lookup"><span data-stu-id="4a316-148">Add additional scenes to the Scene System's profile.</span></span>
