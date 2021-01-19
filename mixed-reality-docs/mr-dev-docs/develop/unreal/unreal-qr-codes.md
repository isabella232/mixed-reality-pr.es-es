---
title: Códigos QR en Unreal
description: Obtenga información sobre cómo configurar y usar códigos QR, y sobre cómo realizar su seguimiento, en aplicaciones de realidad mixta de Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: d896af683a86a1b27e5d100df744222085574a93
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247748"
---
# <a name="qr-codes-in-unreal"></a>Códigos QR en Unreal

HoloLens 2 puede ver los códigos QR en el espacio del mundo real a través de la cámara web, que los representa como hologramas en la posición del mundo real de cada código. HoloLens 2 también puede representar hologramas en la misma ubicación en varios dispositivos para crear una experiencia compartida. Asegúrese de seguir estos procedimientos recomendados para agregar códigos QR a las aplicaciones:

- Zonas tranquilas
- Iluminación y fondo
- Tamaño, distancia y posición angular

Preste especial atención a las [consideraciones del ambiente](../../environment-considerations-for-hololens.md) al colocar códigos QR en la aplicación. Puede encontrar más información sobre cada uno de estos temas e instrucciones sobre cómo descargar el paquete de NuGet necesario en el documento principal de [seguimiento de código QR](../platform-capabilities-and-apis/qr-code-tracking.md).

> [!CAUTION]
> Los códigos QR son el único tipo de imágenes de las que HoloLens puede realizar un seguimiento de forma predefinida. El módulo **UARTrackedImage** de Unreal no se admite en HoloLens. Si necesita realizar un seguimiento de las imágenes personalizadas, puede acceder a la [cámara web](unreal-hololens-camera.md) del dispositivo y procesar imágenes mediante una biblioteca de reconocimiento de imágenes de terceros. 

## <a name="enabling-qr-detection"></a>Habilitación de la detección de QR

Como HoloLens 2 necesita usar la cámara web para ver los códigos QR, deberá habilitarla en la configuración del proyecto:
- Abra **Editar > Configuración del proyecto**, desplácese hasta la sección **Plataformas** y seleccione **HoloLens**.
    + Expanda la sección **Funcionalidades** y marque **Cámara web**.  
- También deberá participar en el seguimiento del código QR mediante la [adición de un activo ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>Configuración de un código QR con seguimiento

Los códigos QR aparecen en el sistema de geometría con seguimiento de AR de Unreal como una imagen con seguimiento. Para que esto funcione, deberá hacer lo siguiente:
1. Cree un plano técnico de actor y agregue el componente **ARTrackableNotify**.

![Notificación de seguimiento de AR de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Seleccione **ARTrackableNotify** y expanda la sección **Eventos** en el panel **Detalles**:

![Eventos con QR](images/unreal-spatialmapping-events.PNG)

3. Haga clic en **+** junto a **On Add Tracked Geometry** (Al agregar geometría con seguimiento) para agregar el nodo al gráfico de eventos.
    - Puede encontrar la lista completa de eventos en la API de componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).

![Adición de un nodo al evento On Add Tracked Geometry (Al agregar geometría con seguimiento)](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>Uso de un código QR con seguimiento

El gráfico de eventos de la siguiente imagen muestra el evento **OnUpdateTrackedImage** que se usa para representar un punto en el centro de un código QR e imprimir sus datos.

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

Esto es lo que sucede:
1. En primer lugar, convierte la imagen con seguimiento en un elemento **ARTrackedQRCode** para comprobar que la imagen actualizada actual es un código QR.  
2. Los datos codificados se recuperan de la variable **QRCode**. Puede obtener la parte superior izquierda del código QR en la ubicación de **GetLocalToWorldTransform** y las dimensiones con **GetEstimateSize**.

También puede [obtener el sistema de coordenadas para un código QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) en el código.

## <a name="finding-the-unique-id"></a>Búsqueda del identificador único

Cada código QR tiene un id. de GUID único, que puede buscar:
- Arrastrando y colocando el marcador **As ARTracked QRCode** (Como QRCode ARTracked) y buscando **Get Unique ID** (Obtener id. único).

![GUID de QR](images/unreal-qr-guid.PNG)

Ocurren muchas cosas en segundo plano con los códigos QR, por lo que esto no es todo. Asegúrese de consultar los siguientes vínculos para obtener más detalles sobre ellos.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar las API y funcionalidades de la plataforma de realidad mixta. Desde aquí, puede continuar con el tema siguiente:

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:

> [!div class="nextstepaction"]
> [Implementación en el dispositivo](unreal-deploying.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#3-advanced-features) en cualquier momento.

## <a name="see-also"></a>Consulta también
* [Asignación espacial](../../design/spatial-mapping.md)
* [Hologramas](../../discover/hologram.md)
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
