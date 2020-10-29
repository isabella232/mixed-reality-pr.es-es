---
title: Preguntas más frecuentes sobre WebVR
description: Solución avanzada de problemas de realidad mixta de Windows que va más allá de nuestra documentación de soporte técnico estándar para el consumidor.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, WebVR
ms.openlocfilehash: 8bc7ab010c1f6ebddf899262b09ba1d08f4ab3ae
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692371"
---
# <a name="webvr-faqs"></a>Preguntas más frecuentes sobre WebVR

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>¿Por qué no veo mis controladores al ver el contenido de VR desde Edge?

No todo el contenido de WebVR se crea para admitir controladores de movimiento. WebVR permite a los desarrolladores de contenido admitir distintos tipos de entrada, como controladores de juegos o controladores de movimiento. Si no ve los controladores en un sitio, probablemente no tenga compatibilidad con el controlador de movimiento.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>¿Por qué no puedo usar el mouse en una vista WebVR envolvente?

Esta es una característica opcional de la especificación WebVR. No todos los exploradores admiten esta característica y no se crea todo el contenido de WebVR para admitir la entrada del mouse. WebVR permite a los desarrolladores de contenido admitir distintos tipos de entrada, como el mouse, el teclado, los controladores de juegos o los controladores de movimiento. El comportamiento de la entrada del mouse varía según el explorador. Dentro de Microsoft Edge, los autores de sitios web deben asegurarse de que usan "pointerlock" cuando se presentan al casco para que la entrada del mouse funcione.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>¿Por qué no puedo ver vídeos de 360 Degrees de YouTube/Facebook/Vimeo/The Guardian, etc. de Edge en VR?

Existe una especificación de WebVR que permite que los sitios web inicien experiencias de VR directamente desde el explorador y que los autores de estos sitios web no hayan implementado esta especificación en este momento. Puede haber aplicaciones descargables en algunas plataformas que permitan ver el contenido de VR de estos proveedores.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>¿Por qué no puedo especificar VR desde Firefox o Chrome?

WebVR solo es compatible con dispositivos de Windows Mixed Reality en Edge en este momento.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Cuando se especifica VR desde un sitio web, ¿por qué veo una pantalla en blanco en el casco?

Es posible que el sitio web no haya implementado compatibilidad con máquinas con varias GPU (incluidos los equipos portátiles de GPU híbrida). Intente:
* Recargue la página.
* En equipos de escritorio, conecte los auriculares al mismo adaptador de gráficos que el monitor que muestra Microsoft Edge. Conecte ambos en la tarjeta de gráficos de mayor potencia, no en el adaptador de gráficos integrado.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Al salir de VR al ver un vídeo desde la periferia, el sonido continúa jugando, pero la ventana del borde está atenuada.

Se trata de un problema conocido al ejecutar WebVR desde Edge en la casa de la realidad de la realidad mixta. Para resolverlo, presione ESC en el teclado en lugar de presionar el botón Windows para salir de la experiencia WebVR, o bien Active la ventana de borde atenuado seleccionándola y, a continuación, detenga el vídeo.

## <a name="can-i-use-webvr-on-the-hololens"></a>¿Puedo usar WebVR en HoloLens?

En este momento, Microsoft no ha anunciado nada sobre WebVR en HoloLens.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>¿Por qué mi vista está en el nivel inferior al ver el contenido de WebVR desde el perímetro?

El sitio web no admite correctamente auriculares con Windows Mixed Reality. Para solucionar este problema:
1. Coloque los auriculares en el suelo del espacio.
2. Vaya a la página WebVR con Microsoft Edge en el escritorio (no en la realidad mixta).
3. Seleccione "Enter VR".
4. Espere entre cinco y 10 segundos para que la experiencia entre en el modo inmersivo completo.
5. Colóquelo en el casco.

## <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>La pantalla tiene una resolución muy baja en algunas experiencias de WebVR.

Estos sitios web no admiten correctamente auriculares de alta resolución. Para solucionar este problema:
* Si el inicio de WebVR desde el escritorio (en lugar de la realidad de la realidad es el acantilado, asegúrese de que la ventana está maximizada antes de seleccionar "Enter VR".
* Evite cambiar el tamaño de la ventana de Microsoft Edge después de haber escrito VR.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>¿Por qué se sale de la vista envolvente WebVR al cambiar las pestañas del explorador?

Este es el comportamiento esperado. Por motivos de seguridad, solo la pestaña del explorador activo puede acceder a los auriculares conectados.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>¿Por qué no puedo oír audio en una experiencia de WebVR determinada?

Es posible que el sitio web use el formato de archivo de audio OGG, que Microsoft Edge no admite actualmente.

Puede notificar sitios rotos directamente al equipo del explorador Microsoft Edge en el [rastreador de problemas](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)o a través de twitter con [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>¿Por qué los comentarios hápticos no funcionan en WebVR con los controladores de movimiento?

Microsoft Edge no es compatible actualmente con hápticos en las extensiones de la API del controlador de juegos de WebVR.

