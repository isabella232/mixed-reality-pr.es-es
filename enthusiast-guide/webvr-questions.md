---
title: Preguntas más frecuentes sobre WebVR
description: Manténgase al día con los Mixed Reality solución de problemas de aplicaciones web que van más allá de la documentación de soporte técnico al consumidor estándar.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, WebVR
ms.openlocfilehash: d0f91af9cf14d8019707e504a9f8bc076bbe39db566895f17e1e56d6b906336d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211097"
---
# <a name="webvr-faqs"></a>Preguntas más frecuentes sobre WebVR

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>¿Por qué no puedo ver mis controladores al ver contenido de realidad virtual desde Edge?

No todo el contenido de WebVR está escrito para admitir controladores de movimiento. WebVR permite a los desarrolladores de contenido admitir diferentes tipos de entrada, como controladores de juegos o controladores de movimiento. Si no ve los controladores en un sitio, probablemente no tenga compatibilidad con el controlador de movimiento.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>¿Por qué no puedo usar el mouse en una vista envolvente de WebVR?

El uso de un mouse es una característica opcional de la especificación WebVR. No todos los exploradores admiten esta característica y no todo el contenido webVR está escrito para admitir la entrada del mouse. WebVR permite a los desarrolladores de contenido admitir diferentes tipos de entrada, como mouse, teclado, controladores de juegos o controladores de movimiento. El comportamiento de entrada del mouse varía según el explorador. Dentro Microsoft Edge, los autores de sitios web deben asegurarse de que toman "pointerlock" al presentar al casco para que la entrada del mouse funcione.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Por qué no puedo ver vídeos de 360 grados de Youtube, Facebook, Vimeo, The Guardian, etc., de Edge en VR.

Hay una especificación de WebVR que permite a los sitios web iniciar experiencias de realidad virtual directamente desde el explorador. Los autores de estos sitios web no han implementado esta especificación en este momento. Puede haber aplicaciones descargables en algunas plataformas que permitan ver contenido de realidad virtual de estos proveedores.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>¿Por qué no puedo escribir VR desde Firefox o Chrome?

WebVR solo es compatible con Windows Mixed Reality dispositivos en Edge en este momento.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Al escribir VR desde un sitio web, ¿por qué veo una pantalla en blanco en el casco?

Es posible que el sitio web no haya implementado compatibilidad con máquinas con varias GPU (incluidos los portátiles de GPU híbridas). Intente:

* Recargue la página.
* En las máquinas de escritorio, conecte el casco en el mismo adaptador de gráficos que el monitor que muestra Microsoft Edge. Conecte ambos a la tarjeta gráfica de mayor potencia, no al adaptador de gráficos integrado.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Al salir de vr al ver un vídeo desde Edge, el sonido continúa reproduciendo, pero la ventana de Edge aparece atenuada.

Se trata de un problema conocido al ejecutar WebVR desde Edge en el Mixed Reality Casa sobre el acantilado. Para resolverlo, presione escape en el teclado en lugar del botón de ventanas para salir de la experiencia de WebVR, o active la ventana de Edge en gris seleccionándose y, a continuación, detenga el vídeo.

## <a name="can-i-use-webvr-on-the-hololens"></a>¿Puedo usar WebVR en el HoloLens

Microsoft no ha anunciado nada sobre WebVR en el HoloLens en este momento.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>¿Por qué mi vista está en el nivel de planta al ver el contenido de WebVR desde Edge?

El sitio web no admite correctamente Windows Mixed Reality cascos. Para solucionar este problema:

1. Coloque el casco en el suelo del espacio.
2. Vaya a la página WebVR mediante Microsoft Edge en el escritorio (no dentro de la realidad mixta).
3. Seleccione "Enter VR" (Escribir VR).
4. Espere de cinco a 10 segundos para que la experiencia entre completamente en modo inmersivo.
5. Coloque el casco.

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a>La pantalla es de baja resolución en algunas experiencias de WebVR.

Esos sitios web no admiten correctamente cascos de alta resolución. Para solucionar este problema:

* Si inicia WebVR desde el escritorio (en lugar de la versión de realidad mixta Casa sobre el acantilado), asegúrese de que la ventana está maximizada antes de seleccionar "Entrar VR".
* Evite el tamaño de la Microsoft Edge después de haber entrado en VR.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>¿Por qué sale la vista inmersiva de WebVR cuando cambio las pestañas del explorador?

Este comportamiento es normal. Por motivos de seguridad, solo la pestaña activa del explorador puede acceder a los cascos conectados.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>¿Por qué no puedo escuchar audio en una experiencia de WebVR determinada?

Es posible que el sitio web use el formato de archivo de audio OGG, Microsoft Edge no es compatible actualmente.

Puede notificar sitios rotos directamente al equipo del explorador de Microsoft Edge en el seguimiento de problemas [o](https://developer.microsoft.com/microsoft-edge/platform/issues/)a través de Twitter [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>¿Por qué los comentarios hápticos no funcionan en WebVR con controladores de movimiento?

Microsoft Edge no admite actualmente hápticos en las extensiones de api del gamepad de WebVR.