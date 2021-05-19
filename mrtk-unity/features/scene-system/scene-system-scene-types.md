---
title: Tipos de escenas del sistema de escenas
description: Documentación sobre diferentes tipos de escena en MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144576"
---
# <a name="scene-types"></a><span data-ttu-id="e5abf-104">Tipos de escena</span><span class="sxs-lookup"><span data-stu-id="e5abf-104">Scene types</span></span>

<span data-ttu-id="e5abf-105">Las escenas se han dividido en tres tipos y cada tipo tiene una función diferente.</span><span class="sxs-lookup"><span data-stu-id="e5abf-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![Sistema de escena en la jerarquía](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="e5abf-107">Escenas de contenido</span><span class="sxs-lookup"><span data-stu-id="e5abf-107">Content scenes</span></span>

<span data-ttu-id="e5abf-108">Estas son las escenas con las que está acostumbrado.</span><span class="sxs-lookup"><span data-stu-id="e5abf-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="e5abf-109">Cualquier tipo de contenido se puede almacenar en ellos y se puede cargar o descargar en cualquier combinación.</span><span class="sxs-lookup"><span data-stu-id="e5abf-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="e5abf-110">Las escenas de contenido están habilitadas de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="e5abf-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="e5abf-111">El servicio puede cargar o descargar cualquier escena incluida en la matriz `Content Scenes` del perfil.</span><span class="sxs-lookup"><span data-stu-id="e5abf-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="e5abf-112">Escenas de administrador</span><span class="sxs-lookup"><span data-stu-id="e5abf-112">Manager scenes</span></span>

<span data-ttu-id="e5abf-113">Una sola escena con una instancia de MixedRealityToolkit necesaria.</span><span class="sxs-lookup"><span data-stu-id="e5abf-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="e5abf-114">Esta escena se cargará primero en el inicio y permanecerá cargada durante la vigencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e5abf-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="e5abf-115">La escena del administrador también puede hospedar otros objetos que nunca deben destruirse.</span><span class="sxs-lookup"><span data-stu-id="e5abf-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="e5abf-116">Esta es la alternativa preferida a DontDestroyOnLoad.</span><span class="sxs-lookup"><span data-stu-id="e5abf-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="e5abf-117">Para habilitar esta característica, compruebe `Use Manager Scene` el perfil y arrastre un objeto de escena al `Manager Scene` campo.</span><span class="sxs-lookup"><span data-stu-id="e5abf-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="e5abf-118">Escenas de iluminación</span><span class="sxs-lookup"><span data-stu-id="e5abf-118">Lighting scenes</span></span>

<span data-ttu-id="e5abf-119">Conjunto de escenas que almacenan información de iluminación y objetos de iluminación.</span><span class="sxs-lookup"><span data-stu-id="e5abf-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="e5abf-120">Solo se puede cargar uno a la vez y su configuración se puede combinar durante las cargas para realizar transiciones de iluminación fluidas.</span><span class="sxs-lookup"><span data-stu-id="e5abf-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="e5abf-121">La configuración de iluminación de Unity (luz ambiente, skyboxes, etc.) puede ser difícil de administrar al usar la carga aditiva porque están asociadas a escenas individuales y el comportamiento de invalidación no es sencillo.</span><span class="sxs-lookup"><span data-stu-id="e5abf-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="e5abf-122">En la práctica, esto puede causar confusión cuando los recursos se crearon en condiciones de iluminación que no se obtienen en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e5abf-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![Configuración de iluminación del sistema de escena](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="e5abf-124">Scene System usa escenas de iluminación para garantizar que esta configuración siga siendo coherente independientemente de las escenas que se carguen o activen, tanto en modo de edición como en modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="e5abf-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="e5abf-125">Para habilitar esta característica, compruebe `Use Lighting Scene` el perfil y rellene la `Lighting Scenes` matriz.</span><span class="sxs-lookup"><span data-stu-id="e5abf-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="e5abf-126">Configuración de iluminación almacenada en caché</span><span class="sxs-lookup"><span data-stu-id="e5abf-126">Cached lighting settings</span></span>

<span data-ttu-id="e5abf-127">El perfil almacena copias almacenadas en caché de la configuración de iluminación que se mantiene en las escenas de iluminación.</span><span class="sxs-lookup"><span data-stu-id="e5abf-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="e5abf-128">Si esa configuración cambia en las escenas de iluminación, deberá actualizar la memoria caché para asegurarse de que la iluminación aparece según lo previsto en el modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="e5abf-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="e5abf-129">El perfil mostrará una advertencia cuando sospeche que la configuración almacenada en caché no está actualizada.</span><span class="sxs-lookup"><span data-stu-id="e5abf-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="e5abf-130">Al hacer clic, se cargará cada una de `Update Cached Lighting Settings` las escenas de iluminación, se extraerá su configuración y, a continuación, se almacenarán en el perfil.</span><span class="sxs-lookup"><span data-stu-id="e5abf-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![Configuración de iluminación almacenada en caché del sistema de escena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="e5abf-132">Comportamiento del editor</span><span class="sxs-lookup"><span data-stu-id="e5abf-132">Editor behavior</span></span>

<span data-ttu-id="e5abf-133">Una ventaja de usar escenas de iluminación es saber que el contenido está encendido correctamente durante la edición.</span><span class="sxs-lookup"><span data-stu-id="e5abf-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="e5abf-134">Con este fin, scene service mantendrá una escena de iluminación cargada en todo momento y copiará la configuración de iluminación de esa escena en la escena activa actual.\*</span><span class="sxs-lookup"><span data-stu-id="e5abf-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="e5abf-135">Puede cambiar la escena de iluminación que se carga abriendo el inspector de servicio del sistema de [escena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="e5abf-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="e5abf-136">En el modo de edición, puede realizar una transición instantánea entre escenas de iluminación.</span><span class="sxs-lookup"><span data-stu-id="e5abf-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="e5abf-137">En el modo de reproducción, puede obtener una vista previa de las transiciones.</span><span class="sxs-lookup"><span data-stu-id="e5abf-137">In play mode, you can preview transitions.</span></span>

![Inspector del sistema de escena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="e5abf-139">\**Nota: Normalmente, la escena activa determina la configuración de iluminación en el editor. Sin embargo, se decide no usar esta característica para aplicar la configuración de iluminación, ya que la escena activa también es donde se colocan los objetos recién creados de forma predeterminada, y las escenas de iluminación solo pueden contener componentes de iluminación. En su lugar, la configuración de la escena de iluminación actual se copia automáticamente en la configuración de la escena activa. Tenga en cuenta que esto dará lugar a que la configuración de iluminación de la escena de contenido se sobresalte.*</span><span class="sxs-lookup"><span data-stu-id="e5abf-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
