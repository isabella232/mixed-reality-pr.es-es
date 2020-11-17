---
title: Mira fijamente inrealmente
description: Tutorial sobre la configuración de la entrada de fijamente para HoloLens y el motor no real
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679054"
---
# <a name="gaze-input"></a><span data-ttu-id="5e63a-104">Entrada de mira</span><span class="sxs-lookup"><span data-stu-id="5e63a-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="5e63a-105">Información general</span><span class="sxs-lookup"><span data-stu-id="5e63a-105">Overview</span></span>

<span data-ttu-id="5e63a-106">El [complemento de Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) no proporciona funciones integradas para la entrada de mirada, pero HoloLens 2 admite el seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="5e63a-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="5e63a-107">Las características de seguimiento reales son proporcionadas por las API de seguimiento de visualización y **seguimiento** de los **cabezales** y incluyen:</span><span class="sxs-lookup"><span data-stu-id="5e63a-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="5e63a-108">Información del dispositivo</span><span class="sxs-lookup"><span data-stu-id="5e63a-108">Device information</span></span>
- <span data-ttu-id="5e63a-109">Sensores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="5e63a-109">Tracking sensors</span></span>
- <span data-ttu-id="5e63a-110">Orientación y posición</span><span class="sxs-lookup"><span data-stu-id="5e63a-110">Orientation and position</span></span>
- <span data-ttu-id="5e63a-111">Recorte de paneles</span><span class="sxs-lookup"><span data-stu-id="5e63a-111">Clipping panes</span></span>
- <span data-ttu-id="5e63a-112">Mira la información de datos y seguimiento</span><span class="sxs-lookup"><span data-stu-id="5e63a-112">Gaze data and tracking information</span></span>

<span data-ttu-id="5e63a-113">Puede encontrar una lista completa de las características en la documentación de la pantalla y el [seguimiento](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) de los ojos [montados](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) .</span><span class="sxs-lookup"><span data-stu-id="5e63a-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="5e63a-114">Además de las API no reales, consulte la documentación sobre la [interacción basada en miras](../../design/eye-gaze-interaction.md) en la vista de hololens 2 y lea cómo funciona el [seguimiento ocular en hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .</span><span class="sxs-lookup"><span data-stu-id="5e63a-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e63a-115">El seguimiento ocular solo se admite en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5e63a-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="5e63a-116">Habilitación del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="5e63a-116">Enabling eye tracking</span></span>
<span data-ttu-id="5e63a-117">La entrada de mirada debe estar habilitada en la configuración del proyecto de HoloLens antes de poder usar cualquiera de las API de inreal.</span><span class="sxs-lookup"><span data-stu-id="5e63a-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="5e63a-118">Cuando se inicie la aplicación, verá una solicitud de consentimiento que se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="5e63a-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="5e63a-119">Seleccione **sí** para establecer el permiso y obtener acceso a la entrada de mira.</span><span class="sxs-lookup"><span data-stu-id="5e63a-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="5e63a-120">Si necesita cambiar esta configuración en cualquier momento, se puede encontrar en la aplicación de **configuración** .</span><span class="sxs-lookup"><span data-stu-id="5e63a-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Permisos de entrada ocular](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="5e63a-122">El seguimiento ocular de HoloLens en inreal solo tiene un único rayo de miración para ambos ojos en lugar de los dos rayos necesarios para el seguimiento de Stereoscopic, que no se admite.</span><span class="sxs-lookup"><span data-stu-id="5e63a-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="5e63a-123">Esta es toda la configuración que necesitará para empezar a agregar entradas de fijamente a las aplicaciones de HoloLens 2 en el mismo equipo.</span><span class="sxs-lookup"><span data-stu-id="5e63a-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="5e63a-124">Puede encontrar más información sobre la entrada y cómo afecta a los usuarios de realidad mixta en los vínculos siguientes.</span><span class="sxs-lookup"><span data-stu-id="5e63a-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="5e63a-125">Asegúrese de pensar en ellos al compilar experiencias interactivas.</span><span class="sxs-lookup"><span data-stu-id="5e63a-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5e63a-126">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="5e63a-126">Next Development Checkpoint</span></span>

<span data-ttu-id="5e63a-127">Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="5e63a-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="5e63a-128">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="5e63a-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e63a-129">Seguimiento de las manos</span><span class="sxs-lookup"><span data-stu-id="5e63a-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="5e63a-130">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="5e63a-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e63a-131">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="5e63a-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="5e63a-132">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="5e63a-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e63a-133">Consulta también</span><span class="sxs-lookup"><span data-stu-id="5e63a-133">See also</span></span>
* [<span data-ttu-id="5e63a-134">Calibración</span><span class="sxs-lookup"><span data-stu-id="5e63a-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="5e63a-135">Comodidad</span><span class="sxs-lookup"><span data-stu-id="5e63a-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="5e63a-136">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="5e63a-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="5e63a-137">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="5e63a-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
