---
ms.openlocfilehash: ce1f02bd2846cadc4e970fef738fb4b46bc3a09f10742b820a0998491c590c80
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204297"
---
# <a name="all-platforms"></a>[Todas las plataformas](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Habilitación del complemento de controlador de movimiento de HP 

El perfil de interacción y las asignaciones de controladores se encuentran en el complemento HP Motion Controller, que debe habilitarse para exponer las asignaciones del controlador al sistema de entrada de Unreal.

![Habilitación del complemento OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Configuración del inicio y HMDPluginPriority

La entrada en Unreal mediante SteamVR tiene algunas diferencias.  Al configurar el proyecto, primero asegúrese de que usa el nuevo sistema de entrada de SteamVR mediante la adición **de vr. SteamVR.EnableVRInput=1 en** la sección **Inicio** **de Engine/Config/ConsoleVariables.ini**.  Este ini se encuentra en el directorio de instalación del motor, no en el directorio del proyecto.

![Actualización de la configuración de inicio](../images/reverb-g2-img-07.png)

El complemento HP Motion Controller habilitará OpenXR.  Si no usa OpenXR, deberá editar hmdpluginpriority de SteamVR en BaseEngine.ini en el mismo directorio que ConsoleVariables.ini.  Cambie el valor de SteamVR para que sea mayor que el valor de OpenXRHMD.

![Actualización de la configuración de HMDPluginPriority](../images/reverb-g2-img-08.png)


