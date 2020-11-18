---
title: Cámara de foto y vídeo HoloLens en Unreal
description: Guía para usar la cámara de foto y vídeo HoloLens en Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, PV camera, MRC
ms.openlocfilehash: 6302a64fcde2a16b6ae1cb570215629a3e6ea9e5
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573239"
---
# <a name="hololens-photovideo-camera-in-unreal"></a>Cámara de foto y vídeo HoloLens en Unreal

## <a name="overview"></a>Introducción

HoloLens tiene una cámara de foto y vídeo (PV) que se usa para la Captura de realidad mixta (MRC) y que una aplicación puede usar para acceder a los objetos visuales del mundo real. 

> [!IMPORTANT]
> La cámara de foto y vídeo no es compatible con el control remoto de holografías, pero es posible usar una cámara web conectada a su equipo para simular la funcionalidad de dicha cámara de HoloLens.

## <a name="render-from-the-pv-camera-for-mrc"></a>Representación de la cámara PV para MRC

> [!NOTE]
> Se requiere **Unreal Engine 4.25** o versión posterior.

El sistema y las grabadoras de MRC personalizadas crean capturas de realidad mixta mediante la combinación de la cámara PV con hologramas representados por la aplicación inmersiva.

De forma predeterminada, la captura de realidad mixta usa la salida holográfica del ojo derecho. Si una aplicación inmersiva elige la [representación de la cámara PV](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), se usará en su lugar. Esto mejora el mapeo entre el mundo real y los hologramas en el vídeo de MRC.

Para participar en la representación de la cámara PV:

1. Llame a **SetEnabledMixedRealityCamera** y **ResizeMixedRealityCamera**
    * Use los valores **Tamaño X** y **Tamaño Y** para establecer las dimensiones del vídeo.

![Tercera cámara](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

Unreal controlará las solicitudes de MRC para representarlas desde la perspectiva de la cámara PV.

> [!NOTE]
> Solo cuando se desencadena la [Captura de realidad mixta](../../mixed-reality-capture.md), se pedirá a la aplicación que represente desde la perspectiva de la cámara de foto y vídeo.

## <a name="using-the-pv-camera"></a>Uso de la cámara PV

La textura de la cámara web se puede recuperar en el juego en tiempo de ejecución, pero debe habilitarse en la opción del editor **Editar > Configuración del proyecto**:
1. Vaya a **Plataformas > HoloLens > Capacidades** y marca **Cámara Web**.
    * Use la función **StartCameraCapture** para usar la cámara web en tiempo de ejecución y la función **StopCameraCapture** para detener la grabación.

![Inicio y detención de la cámara](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Representación de una imagen
Para representar la imagen de la cámara:
1. Cree una instancia de material dinámico basada en un material del proyecto, que se denomine **PVCamMat** en la siguiente captura de pantalla.  
2. Establezca la instancia de material dinámico en una variable de **referencia de objeto dinámico de instancia de material**.  
3. Establezca el material del objeto en la escena que representará la fuente de la cámara para esta nueva instancia de material dinámico.
    * Inicie un temporizador que se usará para enlazar la imagen de la cámara al material.

![Representación de la cámara](images/unreal-camera-render.PNG)

4. Cree una nueva función para este temporizador, en este caso **MaterialTimer**, y llame a **GetARCameraImage** para obtener la textura de la cámara web.  
5. Si esta textura es válida, defina un parámetro de textura en el sombreador para esta imagen.  De lo contrario, vuelve a iniciar el temporizador de materiales.

![Textura de cámara desde la cámara web](images/unreal-camera-texture.PNG)

5. Asegúrese de que el material tiene un parámetro que coincide con el nombre de **SetTextureParameterValue** que está enlazado a una entrada de color. Sin esto, la imagen de la cámara no puede mostrarse correctamente.

![Textura de cámara](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar las API y funcionalidades de la plataforma de realidad mixta. Desde aquí, puede continuar con el tema siguiente:

> [!div class="nextstepaction"]
> [Códigos QR](unreal-qr-codes.md)

O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:

> [!div class="nextstepaction"]
> [Implementación en el dispositivo](unreal-deploying.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) en cualquier momento.

## <a name="see-also"></a>Consulta también
* [Cámara localizable](../platform-capabilities-and-apis/locatable-camera.md)
* [Captura de realidad mixta para desarrolladores](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
