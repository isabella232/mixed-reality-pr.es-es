---
title: Proveedores de entrada
description: Documentación sobre diferentes tipos de proveedores de entrada en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 134ab9304a9fb56ff67dd52e46d030dec2ca4b4c8e528e2c51046fc60c1918f7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207654"
---
# <a name="input-providers"></a>Proveedores de entrada

Los proveedores de entrada se registran en **el perfil de proveedores de servicios registrados**, que se encuentra en Mixed Reality Toolkit componente:

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

Estos son los proveedores de entrada disponibles de forma gratuita, junto con sus controladores correspondientes:

| Proveedor de entrada | Controladores |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Mano simulada |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Mouse  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Generic Generic (Genérico)  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Controlador táctil de Unity  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *Ninguno*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | Mano articulada de WMR, controlador WMR, GGV wmr (mirada, gesto y voz) |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *Ninguno* |

Los proveedores de dictado y voz no crean ningún controlador, genera sus propios eventos de entrada especializados directamente.

Los proveedores de entrada personalizados se pueden crear implementando la [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interfaz .

Para más información, consulte Creación [de un proveedor de datos del sistema de entrada.](create-data-provider.md)
