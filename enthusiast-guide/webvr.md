---
title: Uso de WebVR con Windows Mixed Reality
description: Conozca los conceptos básicos de WebVR, cómo usarlo con Microsoft Edge en cascos Windows Mixed Reality y solución de problemas comunes.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, WebVR, Edge, Microsoft Edge, exploración web
ms.openlocfilehash: f61fff3c8d5083236c10d79d3824c489111f8d2be2138984f5613f295849bdf2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214129"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Uso de WebVR con Windows Mixed Reality

>[!IMPORTANT]
>La mayoría de los exploradores web modernos han dejado de ser compatibles con WebVR en favor de WebXR, el nuevo estándar para crear experiencias web envolventes para cascos de realidad virtual. Instale el [nuevo Microsoft Edge](using-microsoft-edge.md) compatibilidad con WebXR.

## <a name="what-is-webvr"></a>Qué es WebVR

[WebVR](https://webvr.info) es una especificación abierta que le permite experimentar vr directamente desde un explorador. Si un sitio web implementa compatibilidad con WebVR y proporciona contenido 3D, puede mostrar contenido envolvente en el casco, con el consentimiento del usuario.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>¿Cuál es la diferencia entre WebVR y la exploración de la web en VR?

WebVR es una tecnología que permite a un autor del sitio web agregar funcionalidad de realidad virtual a una página. La API de WebVR se usa en una página para mostrar contenido 3D (como vídeo de 360 grados, un modelo 3D o un juego 3D) a la totalidad del casco. **Ejemplo:** Ver un vídeo de 360 en [cnn.com/vr](http://cnn.com/vr). Si una página admite WebVR, agregará un botón u otro elemento de interfaz de usuario que puede seleccionar para escribir VR.

La exploración de la web en VR significa usar el explorador Edge mientras lleva el casco, como una pizarra de aplicación 2D dentro de La casa de los bordes.

## <a name="do-all-websites-support-webvr"></a>¿Todos los sitios web admiten WebVR?

No. Los autores de sitios web deben optar por usar WebVR y pueden crear sitios optimizados para exploradores, cascos y controladores específicos. Parte del contenido de WebVR está optimizado solo para dispositivos móviles de realidad virtual. Además, tenga en cuenta que los sitios web deben crear y proporcionar contenido de WebVR explícitamente. El número de sitios que tienen contenido compatible con WebVR está creciendo cada día.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>¿Puedo usar mi Vive/Oculus, etc., para ver el contenido de WebVR en Microsoft Edge

No. Se Windows Mixed Reality casco para usar WebVR en Edge. Sin embargo, puede acceder al contenido de WebVR en otro explorador; consulte la lista completa de dispositivos y exploradores compatibles en: [WebVR.rocks](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>¿Dónde puedo encontrar la documentación para desarrolladores de WebVR?

La documentación para desarrolladores se encuentra aquí: [Documentación para desarrolladores de WebVR.](/microsoft-edge/webvr/)

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>He encontrado un sitio web con WebVR que no funciona en Windows Mixed Reality. ¿Qué debo hacer?

Puede notificar sitios rotos directamente al equipo del explorador de Microsoft Edge en el seguimiento de problemas [o](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)a través de Twitter [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

También puede registrar errores mediante la aplicación Centro de opiniones sobre Windows en la categoría :

Microsoft Edge -> sitio web

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>¿Qué es una buena página para probar si WebVR funciona?

Consulte [webvr.info ejemplos](http://webvr.info/samples/XX-vr-controllers.html).

## <a name="how-do-i-set-up-webvr"></a>Cómo configurar WebVR

Para experimentar el contenido de WebVR en un Windows Mixed Reality casco (mediante hardware o simulación), debe:

1. Asegúrese de que el casco está conectado.
2. Inicie Microsoft Edge, ya sea en el escritorio o en Mixed Reality.
3. Vaya a una página habilitada para WebVR.
4. Seleccione el botón Entrar VR dentro de la página (la ubicación y la representación visual de este botón pueden variar según el sitio web). Puede tener un aspecto similar a:\
   ![Imagen de vr -vr-](images/75px-enter-vr.png)
5. La primera vez que intente escribir VR en un dominio específico, el explorador le pedirá su consentimiento para usar la vista inmersiva. Seleccione Sí: ![Interfaz de usuario de consentimiento que se muestra en el primer intento de escribir VR en un dominio determinado](images/1053px-Webvr-consent-ui.png)
6. El casco debería empezar a mostrar el contenido de WebVR.

## <a name="see-also"></a>Consulte también

* [Solución de problemas > WebVR](webvr-questions.md)
* [Cómo entrar en su primera experiencia de WebVR](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Uso de juegos y aplicaciones en Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Su Mixed Reality inicio](your-mixed-reality-home.md)
* [Sistema de seguimiento](tracking-system.md)
* [Controladores de movimiento](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Presentación de comentarios](filing-feedback.md)