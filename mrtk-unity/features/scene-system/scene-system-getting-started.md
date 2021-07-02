---
title: Introducción al sistema de escena
description: Página de aterrizaje del sistema de escena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 16adf431498f8146ca2cc60565e59dc8ae03fd92
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177572"
---
# <a name="scene-system-getting-started"></a><span data-ttu-id="d9fe5-104">Introducción al sistema de escena</span><span class="sxs-lookup"><span data-stu-id="d9fe5-104">Scene system getting started</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="d9fe5-105">Cuándo usar el sistema de escena</span><span class="sxs-lookup"><span data-stu-id="d9fe5-105">When to use the scene system</span></span>

<span data-ttu-id="d9fe5-106">Si el proyecto consta de una sola escena, es probable que el sistema de escena no sea necesario.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="d9fe5-107">Resulta muy útil cuando se cumple una o varias de las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="d9fe5-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="d9fe5-108">El proyecto tiene varias escenas.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="d9fe5-109">Está acostumbrado a cargar una sola escena, pero no le gusta la forma en que destruye la instancia de MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="d9fe5-110">Quiere una manera sencilla de cargar varias escenas de forma aditiva para construir su experiencia.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="d9fe5-111">Quiere una manera sencilla de realizar un seguimiento de las operaciones de carga en curso o una manera sencilla de controlar la activación de la escena para varias escenas que se cargan a la vez.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="d9fe5-112">Quiere mantener la iluminación coherente y predecible en todas las escenas.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="d9fe5-113">Recursos del sistema de escena</span><span class="sxs-lookup"><span data-stu-id="d9fe5-113">Scene System Resources</span></span>

<span data-ttu-id="d9fe5-114">De forma predeterminada, scene system usa un par de objetos de escena (escena DefaultManagerScene y DefaultLighting).</span><span class="sxs-lookup"><span data-stu-id="d9fe5-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="d9fe5-115">Si no se encuentra ninguna de estas escenas, aparecerá un mensaje en el inspector de perfil del sistema de escena.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Mensaje de recursos predeterminados](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="d9fe5-117">! [Nota] Si el proyecto usa escenas de iluminación y administrador personalizados, este mensaje se puede omitir de forma segura.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="d9fe5-118">En las secciones siguientes se describe ahora para resolver este mensaje, en función del método que se usó para importar el Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="d9fe5-119">Unity Administrador de paquetes (UPM)</span><span class="sxs-lookup"><span data-stu-id="d9fe5-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="d9fe5-120">En el Mixed Reality Toolkit paquetes UPM, los recursos del sistema de escena se empaquetan como ejemplo.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="d9fe5-121">Debido a que los paquetes UPM son inmutables, Unity no puede abrir el archivo de escena necesario a menos que se importen explícitamente en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="d9fe5-122">Para importar, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="d9fe5-122">To import use the following steps:</span></span>

- <span data-ttu-id="d9fe5-123">Seleccione **Ventana**  >  **Administrador de paquetes**</span><span class="sxs-lookup"><span data-stu-id="d9fe5-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="d9fe5-124">Selección **de Mixed Reality Toolkit Foundation**</span><span class="sxs-lookup"><span data-stu-id="d9fe5-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="d9fe5-125">Buscar **recursos del sistema de escena** en la sección **Ejemplos**</span><span class="sxs-lookup"><span data-stu-id="d9fe5-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Importación de recursos del sistema de escena](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="d9fe5-127">Seleccione **Importar.**</span><span class="sxs-lookup"><span data-stu-id="d9fe5-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="d9fe5-128">Archivos de recursos (.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="d9fe5-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="d9fe5-129">Si se ha eliminado la carpeta SceneSystemResources o se ha deseleccionado durante la importación, se puede recuperar mediante los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="d9fe5-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="d9fe5-130">Seleccionar recursos  >  **Import Package** Custom  >  **Package**</span><span class="sxs-lookup"><span data-stu-id="d9fe5-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="d9fe5-131">Abra **Microsoft.MixedReality.Toolkit. Paquete foundation**</span><span class="sxs-lookup"><span data-stu-id="d9fe5-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="d9fe5-132">Asegúrese de **que Services/SceneSystem/SceneSystemResources** y todas las opciones secundarias están seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Volver a importar recursos del sistema de escena](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="d9fe5-134">Seleccione **Importar.**</span><span class="sxs-lookup"><span data-stu-id="d9fe5-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="d9fe5-135">Uso del sistema de escena</span><span class="sxs-lookup"><span data-stu-id="d9fe5-135">How to use the scene system</span></span>

- [<span data-ttu-id="d9fe5-136">Tipos de escena</span><span class="sxs-lookup"><span data-stu-id="d9fe5-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="d9fe5-137">Carga de escena de contenido</span><span class="sxs-lookup"><span data-stu-id="d9fe5-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="d9fe5-138">Supervisión de la carga de contenido</span><span class="sxs-lookup"><span data-stu-id="d9fe5-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="d9fe5-139">Carga de escena de iluminación</span><span class="sxs-lookup"><span data-stu-id="d9fe5-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="d9fe5-140">Configuración del editor</span><span class="sxs-lookup"><span data-stu-id="d9fe5-140">Editor settings</span></span>

<span data-ttu-id="d9fe5-141">De forma predeterminada, scene system aplica varios comportamientos en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="d9fe5-142">Si encuentra cualquiera de estos comportamientos con mucha mano, se pueden deshabilitar en la sección **Editor Configuración** del perfil del sistema de escena.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="d9fe5-143">`Editor Manage Build Settings:` Si es true, el servicio actualizará la configuración de compilación automáticamente, lo que garantiza que se agregan todas las escenas de contenido, iluminación y administrador.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="d9fe5-144">Deshabilite esta opción si desea un control total sobre la configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="d9fe5-145">`Editor Enforce Scene Order:` Si es true, el servicio se asegurará de que la escena del administrador se muestra primero en la jerarquía de la escena, seguida de la iluminación y, a continuación, del contenido.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="d9fe5-146">Deshabilite esta opción si desea un control total sobre la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="d9fe5-147">`Editor Manage Loaded Scenes:` Si es true, el servicio garantizará que siempre se carguen el administrador, el contenido y las escenas de iluminación.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="d9fe5-148">Deshabilite si desea un control total sobre las escenas que se cargan en el editor.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="d9fe5-149">`Editor Enforce Lighting Scene Types:` Si es true, el servicio se asegurará de que solo se permiten los componentes relacionados con la iluminación definidos en `PermittedLightingSceneComponentTypes` en las escenas de iluminación.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="d9fe5-150">Deshabilite si desea un control total sobre el contenido de las escenas de iluminación.</span><span class="sxs-lookup"><span data-stu-id="d9fe5-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Configuración del editor del sistema de escena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
