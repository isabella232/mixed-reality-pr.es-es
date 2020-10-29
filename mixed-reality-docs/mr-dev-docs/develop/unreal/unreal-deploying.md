---
title: Implementación en el dispositivo en Unreal
description: Guía para la implementación en el dispositivo de un equipo inreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, implementación en dispositivo, equipo, documentación
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691955"
---
# <a name="deploy-to-device-in-unreal"></a>Implementación en el dispositivo en Unreal

## <a name="overview"></a>Información general
Hay dos maneras de implementar una aplicación no real en HoloLens 2:
* Directamente desde el editor desareal
* Como un paquete cargado a través del portal de dispositivos

Ambas opciones requieren la configuración de HoloLens para usar el portal de [dispositivos](../platform-capabilities-and-apis/using-the-windows-device-portal.md) para el desarrollo.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Implementación en el dispositivo desde el editor desareal

1. Haga clic en la flecha desplegable situada junto al botón **iniciar** . Inicialmente, la opción de dispositivo HoloLens estará atenuada.

![Iniciar opciones de lista desplegable](images/unreal/launch-dropdown.png)

2. Abra el **Device Manager** . Tenga en cuenta que HoloLens no aparecerá automáticamente en la lista de dispositivos.

3. Expanda la sección **Agregar un dispositivo** que no está en la lista.

4. Seleccione **HoloLens** como **plataforma** .

5. Escriba la dirección IP y la información de puerto de los dispositivos separadas por un signo de dos puntos como identificador de dispositivo. Por ejemplo, "127.0.0.1:10080" (cuando se conecta a través de USB). Use las credenciales de nombre de usuario y contraseña del portal de dispositivos.

6. Presione **Agregar** y cierre el administrador de dispositivos.
    * En el caso de un error (por ejemplo, una dirección incorrecta, un nombre de usuario o una contraseña), se imprimirá un mensaje en el registro de salida.

![Agregar un dispositivo que no está en la lista](images/unreal/add-unlisted-device.png)

7. Haga clic en la flecha desplegable situada junto al botón **Launch (iniciar** ) de nuevo; esta vez debería ver el dispositivo HoloLens que acaba de agregar. Seleccione el dispositivo HoloLens para compilar e implementar en HoloLens.

>[!NOTE]
>La compilación para el dispositivo puede implicar la recompilación de los sombreadores (especialmente en la primera ejecución). esto puede tardar unos minutos. No deje que el dispositivo pase a suspensión hasta que la aplicación se esté ejecutando (es posible que tenga que hacerlo). De lo contrario, se producirá un error de compilación del sombreador.

## <a name="deploying-to-device-via-device-portal"></a>Implementación en el dispositivo a través del portal de dispositivos

Puede encontrar instrucciones detalladas sobre cómo [empaquetar e implementar una aplicación](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) en la última sección del introducción con una serie de tutoriales inreal.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de punto de control de desarrollo no real que hemos diseñado, se encuentra en medio de la fase de implementación. Desde aquí, puede seguir agregando Advanced Services:

> [!div class="nextstepaction"]
> [Servicios avanzados](unreal-development-overview.md#5-adding-services)

Siempre puede volver a los puntos de [control de desarrollo no reales](unreal-development-overview.md#4-deploying-to-a-device) en cualquier momento.
