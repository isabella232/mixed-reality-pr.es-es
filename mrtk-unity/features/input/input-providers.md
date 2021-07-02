---
title: Proveedores de entrada
description: Documentación sobre diferentes tipos de proveedores de entrada en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176757"
---
# <a name="input-providers"></a><span data-ttu-id="1f922-104">Proveedores de entrada</span><span class="sxs-lookup"><span data-stu-id="1f922-104">Input providers</span></span>

<span data-ttu-id="1f922-105">Los proveedores de entrada se registran en **el perfil de proveedores de servicios registrados**, que se encuentra en Mixed Reality Toolkit componente:</span><span class="sxs-lookup"><span data-stu-id="1f922-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="1f922-106">Estos son los proveedores de entrada disponibles de forma gratuita, junto con sus controladores correspondientes:</span><span class="sxs-lookup"><span data-stu-id="1f922-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="1f922-107">Proveedor de entrada</span><span class="sxs-lookup"><span data-stu-id="1f922-107">Input Provider</span></span> | <span data-ttu-id="1f922-108">Controladores</span><span class="sxs-lookup"><span data-stu-id="1f922-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="1f922-109">Mano simulada</span><span class="sxs-lookup"><span data-stu-id="1f922-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="1f922-110">Mouse</span><span class="sxs-lookup"><span data-stu-id="1f922-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="1f922-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="1f922-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="1f922-112">Generic Generic (Genérico)</span><span class="sxs-lookup"><span data-stu-id="1f922-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="1f922-113">Controlador táctil de Unity</span><span class="sxs-lookup"><span data-stu-id="1f922-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="1f922-114">*None*</span><span class="sxs-lookup"><span data-stu-id="1f922-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="1f922-115">Mano articulada de WMR, controlador WMR, GGV wmr (mirada, gesto y voz)</span><span class="sxs-lookup"><span data-stu-id="1f922-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="1f922-116">*None*</span><span class="sxs-lookup"><span data-stu-id="1f922-116">*None*</span></span> |

<span data-ttu-id="1f922-117">Los proveedores de dictado y voz no crean ningún controlador, genera sus propios eventos de entrada especializados directamente.</span><span class="sxs-lookup"><span data-stu-id="1f922-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="1f922-118">Los proveedores de entrada personalizados se pueden crear implementando la [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interfaz .</span><span class="sxs-lookup"><span data-stu-id="1f922-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="1f922-119">Para más información, consulte Creación [de un proveedor de datos del sistema de entrada.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="1f922-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
