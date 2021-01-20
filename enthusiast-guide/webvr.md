---
title: Uso de WebVR con Windows Mixed Reality
description: Conozca los conceptos básicos de WebVR, cómo usarlos con Microsoft Edge en auriculares de realidad mixta de Windows y problemas comunes de solución de problemas.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, WebVR, Edge, Microsoft Edge, exploración Web
ms.openlocfilehash: 89d9e51bf4adb63e7836968a0112849f7ac403d0
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581754"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Uso de WebVR con Windows Mixed Reality

>[!IMPORTANT]
>La mayoría de los exploradores Web modernos tienen compatibilidad en desuso de WebVR en favor de WebXR, el nuevo estándar para crear experiencias Web envolventes para auriculares VR. Instale [el nuevo Microsoft Edge para la](using-microsoft-edge.md) compatibilidad con WebXR.

## <a name="what-is-webvr"></a>Qué es WebVR

[WebVR](https://webvr.info) es una especificación abierta que le permite experimentar el funcionamiento de VR desde un explorador. Si un sitio web implementa la compatibilidad con WebVR y proporciona contenido 3D, puede mostrar el contenido envolvente del casco con el consentimiento del usuario.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>¿Cuál es la diferencia entre WebVR y explorar la web en VR?

WebVR es una tecnología que permite al autor de un sitio web agregar la funcionalidad de VR a una página. La API de WebVR se usa en una página para mostrar contenido 3D (por ejemplo, un vídeo de 360 grados, un modelo 3D o un juego 3D) para todo el casco. **Ejemplo:** Visualización de un vídeo de 360 en [CNN.com/VR](http://cnn.com/vr). Si una página admite WebVR, agregará un botón u otro elemento de la interfaz de usuario que puede seleccionar para especificar VR.

Explorar la web en VR significa usar el explorador Edge mientras usa el casco, como una pizarra de aplicación 2D dentro de Cliffhouse.

## <a name="do-all-websites-support-webvr"></a>Hacer que todos los sitios web admitan WebVR

No. Los autores de sitios web deben participar en el uso de WebVR y pueden crear sitios optimizados para exploradores, auriculares y controladores específicos. Algunos contenidos de WebVR están optimizados solo para dispositivos móviles de VR. Además, tenga en cuenta que los sitios web deben crear y proporcionar contenido de WebVR de forma explícita. El número de sitios que tienen algún contenido compatible con WebVR está creciendo cada día.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>¿Puedo usar mi Naopak/Oculus, etc., para ver el contenido de WebVR en Microsoft Edge?

No. Se requiere un casco de Windows Mixed Reality para usar WebVR en Edge. Sin embargo, puede tener acceso al contenido de WebVR en otro explorador. Consulte la lista completa de dispositivos y exploradores compatibles en: [WebVR. Rocks](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>¿Dónde puedo encontrar la documentación para desarrolladores de WebVR

La documentación para desarrolladores se encuentra aquí: [documentación para desarrolladores de WebVR](/microsoft-edge/webvr/).

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>He encontrado un sitio web con WebVR que no funciona en Windows Mixed Reality. ¿Qué hago?

Puede notificar sitios rotos directamente al equipo del explorador Microsoft Edge en el [rastreador de problemas](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)o a través de twitter con [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

También puede registrar errores mediante la aplicación centro de comentarios de Windows en categoría:

Problemas con el sitio web de Microsoft Edge->

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>¿Qué es una buena página para probar si WebVR está funcionando?

Vea los [ejemplos de webvr.info](http://webvr.info/samples/XX-vr-controllers.html).

## <a name="how-do-i-set-up-webvr"></a>Cómo configurar WebVR

Para experimentar el contenido de WebVR en un casco de realidad mixta de Windows (con hardware o simulación), debe:

1. Asegúrese de que el casco está conectado.
2. Inicie Microsoft Edge, ya sea en el escritorio o en una realidad mixta.
3. Navegue a una página habilitada para WebVR.
4. Seleccione el botón escribir VR dentro de la página (la ubicación y la representación visual de este botón pueden variar en función del sitio web). Puede tener un aspecto similar a: \
   ![Imagen de la VR](images/75px-enter-vr.png)
5. La primera vez que intente especificar VR en un dominio específico, el explorador solicitará consentimiento para usar la vista envolvente, seleccione Sí: ![Interfaz de usuario de consentimiento que se muestra en el primer intento de especificar VR en un dominio determinado](images/1053px-Webvr-consent-ui.png)
6. Los auriculares deben empezar a mostrar el contenido de WebVR.

## <a name="see-also"></a>Consulte también

* [Solución de problemas de > WebVR](webvr-questions.md)
* [Cómo llegar a su primera experiencia de WebVR](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Uso de juegos y aplicaciones en Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Su página principal de realidad mixta](your-mixed-reality-home.md)
* [Sistema de seguimiento](tracking-system.md)
* [Controladores de movimiento](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Enviar comentarios](filing-feedback.md)