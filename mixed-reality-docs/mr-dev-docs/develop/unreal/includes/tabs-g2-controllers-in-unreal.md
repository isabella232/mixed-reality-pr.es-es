---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638742"
---
# <a name="all-platforms"></a>[Todas las plataformas](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Habilitación del complemento de controlador de movimiento de HP 

Las asignaciones del perfil de interacción y del controlador se encuentran en el complemento de controlador de movimiento de HP, que debe estar habilitado para exponer las asignaciones de controlador al sistema de entrada no real.

![Habilitación del complemento OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Configuración de startup y HMDPluginPriority

La entrada en poco real con SteamVR tiene algunas diferencias.  Al configurar el proyecto, primero asegúrese de que está usando el nuevo sistema de entrada de SteamVR agregando **VR. SteamVR. EnableVRInput = 1** a la sección **Startup** de **Engine/config/ConsoleVariables.ini** .  Este ini se encuentra en el directorio de instalación del motor, no en el directorio del proyecto.

![Actualización de la configuración de inicio](../images/reverb-g2-img-07.png)

El complemento de controlador de movimiento de HP habilitará OpenXR.  Si no usa OpenXR, tendrá que editar el HMDPluginPriority de SteamVR en BaseEngine.ini en el mismo directorio que ConsoleVariables.ini.  Cambie el valor de SteamVR para que sea mayor que el valor de OpenXRHMD.

![Actualización de la configuración de HMDPluginPriority](../images/reverb-g2-img-08.png)


