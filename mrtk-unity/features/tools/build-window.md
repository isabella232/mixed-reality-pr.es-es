---
title: Ventana de compilación de MRTK
description: Documentación sobre el uso de la ventana de compilación en MRTK para Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, compilación, ventana de compilación, herramientas
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196872"
---
# <a name="build-window"></a><span data-ttu-id="5c6fe-104">Ventana de compilación</span><span class="sxs-lookup"><span data-stu-id="5c6fe-104">Build window</span></span>
![Compilación & flujo de implementación](images/MRTK_BuildWindow0.png)

<span data-ttu-id="5c6fe-106">La ventana de compilación de MRTK facilita la compilación & implementar MRTK-Unity proyectos.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="5c6fe-107">Con un solo clic, puede compilar un proyecto de Unity y generar Visual Studio solución(. SLN), paquete de aplicación para UWP(. APPX) e instale el paquete de aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="5c6fe-108">Opciones de compilación de Unity</span><span class="sxs-lookup"><span data-stu-id="5c6fe-108">Unity Build Options</span></span>
![Ventana Compilación: Opciones de compilación de Unity 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="5c6fe-110">Estas escenas son de la configuración de compilación de Unity.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="5c6fe-111">Puede cambiar el tipo de dispositivo de destino mediante el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="5c6fe-112">Opciones de compilación de Appx</span><span class="sxs-lookup"><span data-stu-id="5c6fe-112">Appx Build Options</span></span>
![Ventana Compilación: Opciones de compilación de Appx 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="5c6fe-114">En esta pestaña se muestra la configuración de Visual Studio solución.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="5c6fe-115">Para habilitar HoloLens 2 entrada de seguimiento ocular, active la opción **Gaze Input Capability** (Funcionalidad de entrada de mirada).</span><span class="sxs-lookup"><span data-stu-id="5c6fe-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="5c6fe-116">Puede asignar el archivo .glb en el campo Modelo del iniciador de aplicaciones **3D** para el icono personalizado del iniciador de aplicaciones 3D.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="5c6fe-117">Consulte la [guía de diseño del iniciador de aplicaciones 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="5c6fe-118">De forma predeterminada, **Incremento automático** está activado en Opciones de control de versiones.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="5c6fe-119">Las versiones de AppX se incrementarán automáticamente.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="5c6fe-120">Opciones de implementación</span><span class="sxs-lookup"><span data-stu-id="5c6fe-120">Deploy Options</span></span>
![Ventana Compilación: Opciones de implementación 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="5c6fe-122">En esta pestaña, puede conectarse al dispositivo si escribe el nombre de usuario y la contraseña de la Portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="5c6fe-123">En la parte inferior de la página, puede encontrar una lista de los paquetes de aplicación que se han creado.</span><span class="sxs-lookup"><span data-stu-id="5c6fe-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

