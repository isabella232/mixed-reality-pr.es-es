---
title: Proveedores de entrada
description: Documentación sobre diferentes tipos de proveedores de entrada en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145265"
---
# <a name="input-providers"></a><span data-ttu-id="06b8d-104">Proveedores de entrada</span><span class="sxs-lookup"><span data-stu-id="06b8d-104">Input providers</span></span>

<span data-ttu-id="06b8d-105">Los proveedores de entrada se registran en **el perfil de proveedores de servicios registrados,** que se encuentra en el componente Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="06b8d-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="06b8d-106">Estos son los proveedores de entrada disponibles de forma gratuita, junto con sus controladores correspondientes:</span><span class="sxs-lookup"><span data-stu-id="06b8d-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="06b8d-107">Proveedor de entrada</span><span class="sxs-lookup"><span data-stu-id="06b8d-107">Input Provider</span></span> | <span data-ttu-id="06b8d-108">Controladores</span><span class="sxs-lookup"><span data-stu-id="06b8d-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="06b8d-109">Mano simulada</span><span class="sxs-lookup"><span data-stu-id="06b8d-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="06b8d-110">Mouse</span><span class="sxs-lookup"><span data-stu-id="06b8d-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="06b8d-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="06b8d-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="06b8d-112">Generic Generic (Genérico)</span><span class="sxs-lookup"><span data-stu-id="06b8d-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="06b8d-113">Controlador táctil de Unity</span><span class="sxs-lookup"><span data-stu-id="06b8d-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="06b8d-114">*Ninguno*</span><span class="sxs-lookup"><span data-stu-id="06b8d-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="06b8d-115">Mano articulada de WMR, controlador WMR, GGV wmr (mirada, gesto y voz)</span><span class="sxs-lookup"><span data-stu-id="06b8d-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="06b8d-116">*Ninguno*</span><span class="sxs-lookup"><span data-stu-id="06b8d-116">*None*</span></span> |

<span data-ttu-id="06b8d-117">Los proveedores de dictado y voz no crean ningún controlador, genera sus propios eventos de entrada especializados directamente.</span><span class="sxs-lookup"><span data-stu-id="06b8d-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="06b8d-118">Los proveedores de entrada personalizados se pueden crear implementando la [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interfaz .</span><span class="sxs-lookup"><span data-stu-id="06b8d-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="06b8d-119">Para más información, consulte Creación [de un proveedor de datos del sistema de entrada.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="06b8d-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
