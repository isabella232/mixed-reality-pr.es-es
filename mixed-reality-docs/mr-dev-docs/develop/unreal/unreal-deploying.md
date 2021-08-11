---
title: Implementación en el dispositivo en Unreal
description: Obtenga información sobre todo lo que necesita saber sobre la implementación de aplicaciones de Unreal de realidad mixta en HoloLens 2 el portal del editor o del dispositivo.
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, deploy to device, PC, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
appliesto:
- HoloLens 2
ms.openlocfilehash: d6df3f9af21a0759c98306c28696d21eac7687b92d3cb74a9cd9948122cbcbcc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226650"
---
# <a name="deploy-to-device-in-unreal"></a>Implementación en el dispositivo en Unreal

Hay dos maneras de implementar una aplicación de Unreal para HoloLens 2:
* Directamente desde el editor de Unreal
* Como paquete cargado a través del portal de dispositivos

Ambas opciones requieren que configure los HoloLens usar el [portal de dispositivos para](../platform-capabilities-and-apis/using-the-windows-device-portal.md) el desarrollo.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Implementación en el dispositivo desde el editor de Unreal

1. Seleccione la flecha desplegable situada junto al **botón** Iniciar. Inicialmente, la HoloLens del dispositivo estará atenuada.

![Opciones de la lista desplegable De inicio](images/unreal/launch-dropdown.png)

2. Abra el **Administrador de dispositivos** y tenga en cuenta que el HoloLens no aparecerá automáticamente en la lista de dispositivos.

3. Expanda la **sección Agregar un dispositivo no publicado.**

4. Seleccione **HoloLens** como **plataforma.**

5. Escriba la dirección IP y la información de puerto de los dispositivos separados por dos puntos como identificador del dispositivo. Por ejemplo, "127.0.0.1:10080" (cuando se conecta a través de USB). Use sus credenciales Portal de dispositivos nombre de usuario y contraseña.

6. Presione **Agregar** y cierre el administrador de dispositivos.
    * Si se produce un error, como una dirección incorrecta o credenciales de usuario, se imprimirá un mensaje en el registro de salida.

![Adición de un dispositivo no publicado](images/unreal/add-unlisted-device.png)

7. Vuelva a seleccionar la  flecha desplegable situada junto al botón Iniciar. Esta vez debería ver el HoloLens que acaba de agregar. Seleccione el HoloLens que desea compilar e implementar en el HoloLens.

>[!NOTE]
>La compilación para el dispositivo puede implicar la recompilación de sombreadores (especialmente en la primera ejecución): esto puede tardar un tiempo. No deje que el dispositivo entre en suspensión hasta que la aplicación se esté ejecutando (es posible que tenga que usarlo). De lo contrario, se producirá un error en la compilación del sombreador.

## <a name="deploying-to-device-via-device-portal"></a>Implementación en el dispositivo a través del portal de dispositivos

Puede encontrar instrucciones detalladas sobre cómo empaquetar e implementar una aplicación en la serie [de tutoriales de Unreal](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el recorrido de desarrollo de Unreal que hemos diseñado, se encuentra en medio de la fase de implementación. Desde aquí, puede seguir agregando servicios avanzados:

> [!div class="nextstepaction"]
> [Servicios avanzados](unreal-development-overview.md#5-adding-services)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) en cualquier momento.
