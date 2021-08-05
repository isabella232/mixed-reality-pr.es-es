---
title: Introducción al desarrollo de JavaScript
description: Información general sobre Mixed Reality desarrollo con JavaScript para cascos envolventes web, móviles y windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 video, 360 videos, 360 photo, 360 photos, 360 content, immersive web, immersive-web, IW, immersiveweb
ms.openlocfilehash: de6314b5651740eca23a9078d4b05e1d92344d1742ea433d7b924cbde4457b8c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210511"
---
# <a name="javascript-development-overview"></a>Introducción al desarrollo con JavaScript

JavaScript es uno de los lenguajes de programación más populares del mundo. Es simple, ligero y se usa ampliamente en la Web. Aproveche la potencia de sus conocimientos de JavaScript y web para crear experiencias Mixed Reality atractivas.

## <a name="mixed-reality-applications-on-the-web"></a>Mixed Reality aplicaciones en la web

Mixed Reality características están disponibles en la Web mediante el uso de [WebXR](webxr-overview.md). Puede ver contenido de realidad virtual (VR) y realidad aumentada (AR) en un explorador compatible habilitado para WebXR sin instalar ningún software o complementos adicionales. Puede usar ese mismo explorador con un dispositivo físico como el HoloLens 2. Consulte nuestra [documentación de WebXR](webxr-overview.md) para obtener más detalles.

> [!NOTE]
> **WebVR está** en desuso y no está disponible en los exploradores actuales, por lo que no debe usarse para ningún desarrollo nuevo. Deberá migrar todas las implementaciones de **WebVR** existentes a **WebXR.**

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>¿Qué puedo usar para desarrollar experiencias web envolventes?

En la lista siguiente se muestran las API y los marcos de JavaScript para crear experiencias envolventes que actualmente dominan el mercado y que son ampliamente aceptadas y adoptadas por Mixed Reality desarrolladores de JavaScript:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon es un motor 3D de JavaScript que facilita el desarrollo de contenido 3D y aplicaciones inmersivas. Antes de empezar a trabajar con aplicaciones envolventes, se recomienda conocer los aspectos básicos del Babylon.js desarrollo.<br/><br/>- Aprenda a compilar aplicaciones 3D con babylon.js [Introducción.](https://doc.babylonjs.com/start)<br/>- Jugar con ejemplos 3D y su código fuente mediante babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>- Profundizar en [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>- Aprenda a empezar a trabajar con nuestros tutoriales Creación [de la primera aplicación "Hola mundo!".](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Logotipo de BabylonJS](images/babylon.js.example.png) |
|[**Marco A**](https://aframe.io/) <br/><br/>Un marco es un marco de JavaScript declarativo para empezar a trabajar con Virtual Reality en la Web. Consulte la documentación [de A-Frame](https://aframe.io/docs/1.2.0/introduction/) para obtener más información. |![Marco A](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js es una popular biblioteca 3D para crear experiencias envolventes. Obtenga más información sobre [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) en la página de documentación y explorando [ejemplos .](https://threejs.org/examples/#webgl_animation_cloth) |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Puede acceder a las API de dispositivos WebXR directamente mediante las API de WebGL. WebGL (Biblioteca de gráficos web) es una API de JavaScript para representar gráficos 3D y 2D interactivos de alto rendimiento en cualquier explorador web compatible sin el uso de complementos. |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre cómo empezar a trabajar con nuestros tutoriales.

> [!div class="nextstepaction"]
> [Creación de la primera aplicación "Hola mundo!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>Consulte también

* [Información general sobre WebXR](webxr-overview.md)
* [Especificación de api de dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentación de Api de dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Ejemplos de WebXR](https://immersive-web.github.io/webxr-samples/)
* [Uso Babylon.js para crear experiencias de WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality y la nueva Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Github del W3C de La Web inmersiva](https://github.com/immersive-web)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [Extensiones de Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) [y Gamepad](https://w3c.github.io/gamepad/extensions.html)
