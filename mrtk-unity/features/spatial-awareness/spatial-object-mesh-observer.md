---
title: Observador de la malla de objetos espaciales
description: Documentación sobre el observador de malla espacial en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144453"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="5857a-104">Configuración de observadores de malla para el editor</span><span class="sxs-lookup"><span data-stu-id="5857a-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="5857a-105">Una manera cómoda de proporcionar datos de malla de entorno en el editor de Unity es usar la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) clase .</span><span class="sxs-lookup"><span data-stu-id="5857a-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="5857a-106">El *observador de malla de* objetos espaciales es un proveedor de datos solo de editor para el sistema [de](spatial-awareness-getting-started.md) reconocimiento espacial que permite importar datos del modelo 3D para representar una malla espacial.</span><span class="sxs-lookup"><span data-stu-id="5857a-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="5857a-107">Un uso común del observador de *la* malla de objetos espaciales es importar los datos examinados a través de un Microsoft HoloLens para probar cómo se adapta una experiencia a distintos entornos desde Unity.</span><span class="sxs-lookup"><span data-stu-id="5857a-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="5857a-108">Introducción</span><span class="sxs-lookup"><span data-stu-id="5857a-108">Getting started</span></span>

<span data-ttu-id="5857a-109">En esta guía se le guiará por la configuración de *un observador de malla de objetos espaciales.*</span><span class="sxs-lookup"><span data-stu-id="5857a-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="5857a-110">Hay tres pasos clave para habilitar esta característica.</span><span class="sxs-lookup"><span data-stu-id="5857a-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="5857a-111">Agregar un observador *de malla de objetos espaciales* al perfil del sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="5857a-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="5857a-112">Establecer el objeto Environment Mesh Data</span><span class="sxs-lookup"><span data-stu-id="5857a-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="5857a-113">Configuración del resto de las propiedades del perfil de Mesh Observer</span><span class="sxs-lookup"><span data-stu-id="5857a-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="5857a-114">Configuración de un perfil *de observador de malla de objetos espaciales*</span><span class="sxs-lookup"><span data-stu-id="5857a-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="5857a-115">Seleccione el perfil de *configuración Mixed Reality Toolkit* deseado o seleccione el objeto Mixed Reality *Toolkit* en la escena.</span><span class="sxs-lookup"><span data-stu-id="5857a-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="5857a-116">Abra o expanda la *pestaña Spatial Awareness System (Sistema de reconocimiento espacial).*</span><span class="sxs-lookup"><span data-stu-id="5857a-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="5857a-117">Haga clic en *el botón "Agregar observador espacial".*</span><span class="sxs-lookup"><span data-stu-id="5857a-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Agregar observador espacial](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="5857a-119">Seleccione el *tipo SpatialObjectMeshObserver.*</span><span class="sxs-lookup"><span data-stu-id="5857a-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Selección del observador de la malla de objetos espaciales](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="5857a-121">Seleccione el objeto *de malla espacial deseado.*</span><span class="sxs-lookup"><span data-stu-id="5857a-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="5857a-122">De forma predeterminada, el observador se configura con un modelo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="5857a-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="5857a-123">Este modelo se creó mediante un Microsoft HoloLens, pero es posible [crear un nuevo objeto de malla de examen](#acquiring-environment-scans).</span><span class="sxs-lookup"><span data-stu-id="5857a-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="5857a-124">Configuración del resto de las propiedades del perfil de Mesh Observer</span><span class="sxs-lookup"><span data-stu-id="5857a-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![Selección del objeto mesh](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="5857a-126">Notas del perfil de observador de malla de objetos espaciales</span><span class="sxs-lookup"><span data-stu-id="5857a-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="5857a-127">Puesto que *el observador de malla* de objetos espaciales carga datos de un modelo 3D, no respeta algunas de las configuraciones estándar del observador de malla que se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="5857a-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="5857a-128">**Intervalo de actualización**</span><span class="sxs-lookup"><span data-stu-id="5857a-128">**Update Interval**</span></span>

<span data-ttu-id="5857a-129">El  *observador de malla de objetos* espaciales envía todas las mallas a una aplicación cuando se carga el modelo.</span><span class="sxs-lookup"><span data-stu-id="5857a-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="5857a-130">No simula diferencias de tiempo entre actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="5857a-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="5857a-131">Una aplicación puede volver a recibir los eventos de malla llamando a [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) y [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="5857a-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="5857a-132">**Is Stationary Observer**</span><span class="sxs-lookup"><span data-stu-id="5857a-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="5857a-133">El *observador de malla de objetos* espaciales considera que todos los objetos de malla 3D son insaltentes y no tiene en cuenta el origen.</span><span class="sxs-lookup"><span data-stu-id="5857a-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="5857a-134">**Forma y extensiones del observador**</span><span class="sxs-lookup"><span data-stu-id="5857a-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="5857a-135">El  *observador de malla de objetos espaciales* envía toda la malla 3D a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5857a-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="5857a-136">No se tienen en cuenta la forma y las extensiones del observador.</span><span class="sxs-lookup"><span data-stu-id="5857a-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="5857a-137">**Nivel de detalle y triángulos/medidor cúbica**</span><span class="sxs-lookup"><span data-stu-id="5857a-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="5857a-138">El observador no intenta encontrar los LOD del modelo 3D al enviar las mallas a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5857a-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="5857a-139">Adquisición de exámenes de entorno</span><span class="sxs-lookup"><span data-stu-id="5857a-139">Acquiring environment scans</span></span>

<span data-ttu-id="5857a-140">En esta sección se describe información adicional para crear y recopilar archivos *de objeto* de malla espacial para su uso con el observador de malla de *objetos espaciales*.</span><span class="sxs-lookup"><span data-stu-id="5857a-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="5857a-141">Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="5857a-141">Windows Device Portal</span></span>

<span data-ttu-id="5857a-142">El [Portal de dispositivos Windows](/windows/mixed-reality/using-the-windows-device-portal) se puede usar para descargar la malla espacial, como un archivo .obj, desde un Microsoft HoloLens dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5857a-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="5857a-143">Examinar simplemente a pie y ver el entorno deseado con un HoloLens</span><span class="sxs-lookup"><span data-stu-id="5857a-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="5857a-144">Conéctese a HoloLens mediante el Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="5857a-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="5857a-145">Vaya a la *página Vista 3D.*</span><span class="sxs-lookup"><span data-stu-id="5857a-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="5857a-146">Haga clic en *el botón Actualizar* en la sección *Asignación* espacial.</span><span class="sxs-lookup"><span data-stu-id="5857a-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="5857a-147">Haga clic en *el botón* Guardar de la *sección Asignación* espacial para guardar el archivo obj en el equipo.</span><span class="sxs-lookup"><span data-stu-id="5857a-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="5857a-148">**Archivos .room de HoloToolkit**</span><span class="sxs-lookup"><span data-stu-id="5857a-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="5857a-149">Muchos desarrolladores habrán usado previamente HoloToolkit para examinar entornos y crear archivos .room.</span><span class="sxs-lookup"><span data-stu-id="5857a-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="5857a-150">Ahora Mixed Reality Toolkit admite la importación de estos archivos como GameObjects en Unity y usarlos como objetos *de* malla espacial en el observador.</span><span class="sxs-lookup"><span data-stu-id="5857a-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="5857a-151">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5857a-151">See also</span></span>

- [<span data-ttu-id="5857a-152">Perfiles</span><span class="sxs-lookup"><span data-stu-id="5857a-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="5857a-153">guía de configuración del perfil de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="5857a-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="5857a-154">Introducción al reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="5857a-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="5857a-155">Configuración de observadores de malla en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="5857a-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="5857a-156">Configuración de observadores de malla mediante código</span><span class="sxs-lookup"><span data-stu-id="5857a-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="5857a-157">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="5857a-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)