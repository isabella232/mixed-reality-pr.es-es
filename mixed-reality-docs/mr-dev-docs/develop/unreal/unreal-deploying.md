---
title: Implementación en el dispositivo en Unreal
description: Obtenga información sobre todo lo que necesita saber sobre la implementación de aplicaciones de realidad mixta en HoloLens 2 con el editor o el portal de dispositivos.
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, implementación en dispositivo, PC, documentación, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: 24b2c013e1c9f25f54be9a6fefec8a86846c1746
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009755"
---
# <a name="deploy-to-device-in-unreal"></a>Implementación en el dispositivo en Unreal

Hay dos maneras de implementar una aplicación no real en HoloLens 2:
* Directamente desde el editor desareal
* Como un paquete cargado a través del portal de dispositivos

Ambas opciones requieren la configuración de HoloLens para usar el portal de [dispositivos](../platform-capabilities-and-apis/using-the-windows-device-portal.md) para el desarrollo.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Implementación en el dispositivo desde el editor desareal

1. Seleccione la flecha desplegable situada junto al botón **iniciar** . Inicialmente, la opción de dispositivo HoloLens estará atenuada.

![Iniciar opciones de lista desplegable](images/unreal/launch-dropdown.png)

2. Abra el **Device Manager** y tenga en cuenta que HoloLens no aparecerá automáticamente en la lista de dispositivos.

3. Expanda la sección **Agregar un dispositivo** que no está en la lista.

4. Seleccione **HoloLens** como **plataforma**.

5. Escriba la dirección IP y la información de puerto de los dispositivos separadas por un signo de dos puntos como identificador de dispositivo. Por ejemplo, "127.0.0.1:10080" (cuando se conecta a través de USB). Use las credenciales de nombre de usuario y contraseña del portal de dispositivos.

6. Presione **Agregar** y cierre el administrador de dispositivos.
    * Si hay un error, como una dirección o credenciales de usuario incorrectas, se imprimirá un mensaje en el registro de salida.

![Agregar un dispositivo que no está en la lista](images/unreal/add-unlisted-device.png)

7. Seleccione de nuevo la flecha desplegable situada junto al botón **iniciar** . esta vez debería ver el dispositivo HoloLens que acaba de agregar. Seleccione el dispositivo HoloLens para compilar e implementar en HoloLens.

>[!NOTE]
>La compilación para el dispositivo puede implicar la recompilación de los sombreadores (especialmente en la primera ejecución). esto puede tardar unos minutos. No deje que el dispositivo pase a suspensión hasta que la aplicación se esté ejecutando (es posible que tenga que hacerlo). De lo contrario, se producirá un error de compilación del sombreador.

## <a name="deploying-to-device-via-device-portal"></a>Implementación en el dispositivo a través del portal de dispositivos

Puede encontrar instrucciones detalladas sobre cómo empaquetar e implementar una aplicación en la [serie de tutoriales inreal](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo no real que hemos diseñado, se encuentra en medio de la fase de implementación. Desde aquí, puede seguir agregando Advanced Services:

> [!div class="nextstepaction"]
> [Servicios avanzados](unreal-development-overview.md#5-adding-services)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) en cualquier momento.
