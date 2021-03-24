---
title: Información general sobre el desarrollo de JavaScript
description: Información general sobre el desarrollo de realidad mixta con JavaScript para auriculares Web, móviles y de Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: 'JavaScript, WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, webxr, Web Mr, WebAr, 360, 360 video, 360 videos, 360 Photo, 360 photos, contenido de 360, Web inmersivo, envolventes: Web, IW, immersiveweb'
ms.openlocfilehash: 051c6079da939224c88d6414978b2b4b0e67f87c
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909120"
---
# <a name="javascript-development-overview"></a>Introducción al desarrollo con JavaScript

JavaScript es uno de los lenguajes de programación más populares del mundo. Es sencillo, ligero y ampliamente utilizado en la Web. Aproveche el potencial de sus conocimientos de JavaScript y web para crear experiencias de realidad mixta más atractivas.

## <a name="mixed-reality-applications-on-the-web"></a>Aplicaciones de realidad mixta en la web

Las características de realidad mixta están disponibles en la web mediante el uso de [WebXR](webxr-overview.md). Puede ver la realidad virtual (VR) y el contenido de realidad aumentada (AR) en un explorador compatible con WebXR sin necesidad de instalar software o complementos adicionales. Puede usar ese mismo explorador con un dispositivo físico como HoloLens 2. Consulte nuestra documentación de [WebXR](webxr-overview.md) para obtener más información.

> [!NOTE]
> **WebVR** está en desuso y no está disponible en los exploradores actuales, por lo que no debe usarse para ningún desarrollo nuevo. Tendrá que migrar las implementaciones de **WebVR** existentes hacia delante a **WebXR**.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>¿Qué puedo usar para desarrollar experiencias Web envolventes?

En la siguiente lista se muestran las plataformas y las API de JavaScript para crear experiencias envolventes que dominan actualmente el mercado y que los desarrolladores de JavaScript de realidad mixta aceptan y adoptan:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon es un motor 3D de JavaScript que facilita el desarrollo de contenido 3D y aplicaciones envolventes. Antes de empezar a trabajar con aplicaciones envolventes, se recomienda conocer los aspectos básicos del desarrollo de Babylon.js.<br/><br/>-Aprenda a crear aplicaciones 3D con babylon.js [Introducción](https://doc.babylonjs.com/start).<br/>-Reproducir con ejemplos 3D y su código fuente mediante el uso [de babylon.js](https://doc.babylonjs.com/examples/)<br/>-Profundizar en [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>: Obtenga información sobre cómo empezar a usar los tutoriales [creación de la primera aplicación "Hola mundo!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Logotipo de BabylonJS](images/babylon.js.example.png) |
|[**A-marco**](https://aframe.io/) <br/><br/>A-Frame es un marco de JavaScript declarativo para empezar a trabajar con la realidad virtual en la Web. Consulte la [documentación del marco](https://aframe.io/docs/1.2.0/introduction/) a para obtener más información. |![A-marco](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js es una popular biblioteca 3D para crear experiencias envolventes. Obtenga más información sobre [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) en la página de documentación y mediante la exploración de [ejemplos](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Puede acceder a las API del dispositivo WebXR directamente mediante las API de WebGL. WebGL (biblioteca de gráficos Web) es una API de JavaScript para representar gráficos 2D y 3D interactivos de alto rendimiento en cualquier explorador Web compatible sin el uso de complementos. |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre cómo empezar a trabajar con nuestros tutoriales.

> [!div class="nextstepaction"]
> [Cree su primera aplicación "Hola mundo!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>Consulte también

* [Información general de WebXR](webxr-overview.md)
* [Especificación de la API de dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentación de la API del dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Ejemplos de WebXR](https://immersive-web.github.io/webxr-samples/)
* [Uso de Babylon.js para crear experiencias de WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality y el nuevo Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [GitHub Web de W3C envolvente](https://github.com/immersive-web)
* [API de WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) y [extensiones de controlador](https://w3c.github.io/gamepad/extensions.html) para juegos
