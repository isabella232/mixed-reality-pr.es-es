---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638742"
---
# <a name="all-platforms"></a>[<span data-ttu-id="9d7cd-101">Todas las plataformas</span><span class="sxs-lookup"><span data-stu-id="9d7cd-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="9d7cd-102">Habilitación del complemento de controlador de movimiento de HP</span><span class="sxs-lookup"><span data-stu-id="9d7cd-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="9d7cd-103">Las asignaciones del perfil de interacción y del controlador se encuentran en el complemento de controlador de movimiento de HP, que debe estar habilitado para exponer las asignaciones de controlador al sistema de entrada no real.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![Habilitación del complemento OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="9d7cd-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="9d7cd-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="9d7cd-106">Configuración de startup y HMDPluginPriority</span><span class="sxs-lookup"><span data-stu-id="9d7cd-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="9d7cd-107">La entrada en poco real con SteamVR tiene algunas diferencias.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="9d7cd-108">Al configurar el proyecto, primero asegúrese de que está usando el nuevo sistema de entrada de SteamVR agregando **VR. SteamVR. EnableVRInput = 1** a la sección **Startup** de **Engine/config/ConsoleVariables.ini** .</span><span class="sxs-lookup"><span data-stu-id="9d7cd-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="9d7cd-109">Este ini se encuentra en el directorio de instalación del motor, no en el directorio del proyecto.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-109">This ini is found in the engine install directory, not the project directory.</span></span>

![Actualización de la configuración de inicio](../images/reverb-g2-img-07.png)

<span data-ttu-id="9d7cd-111">El complemento de controlador de movimiento de HP habilitará OpenXR.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="9d7cd-112">Si no usa OpenXR, tendrá que editar el HMDPluginPriority de SteamVR en BaseEngine.ini en el mismo directorio que ConsoleVariables.ini.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="9d7cd-113">Cambie el valor de SteamVR para que sea mayor que el valor de OpenXRHMD.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![Actualización de la configuración de HMDPluginPriority](../images/reverb-g2-img-08.png)


