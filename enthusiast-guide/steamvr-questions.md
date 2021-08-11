---
title: Preguntas más frecuentes sobre SteamVR
description: Solución de Windows Mixed Reality de problemas de SteamVR que va más allá de nuestra documentación estándar de soporte al consumidor.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, SteamVR
ms.openlocfilehash: 0fb9c07dda8fe354966403bc9c6a21acb600e61cb943c270eb9c87f5ec2fb89a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199501"
---
# <a name="steamvr-faqs"></a>Preguntas más frecuentes sobre SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>¿Cómo puedo reproducir juegos de SteamVR en mi casco Windows Mixed Reality dispositivo?

1. [Descargue e instale SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe) El tutorial de SteamVR debe iniciarse automáticamente al iniciar SteamVR.
2. Conectar el casco al equipo y active los controladores de movimiento.
3. Una Windows Mixed Reality de inicio y los controladores estén visibles, abra la aplicación Dete en el escritorio.
4. Use la aplicación Dete para iniciar un juego de SteamVR desde la biblioteca de Steam. Para iniciar juegos de SteamVR sin quitarse los cascos, bázctelos e inscántelos en Windows Mixed Reality de inicio **> Todas las aplicaciones.**

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Un mensaje indica "Para usar SteamVR con Windows Mixed Reality, debe instalar la actualización de Windows más reciente" o "Windows modo de desarrollador requerido"

1. Asegúrese de que el equipo ejecuta la versión más reciente de Windows 10. Vaya a **Configuración > System > Acerca** de y, en "Windows specifications", asegúrese de que "Compilación del sistema operativo" es 16299.64 o superior.
2. Asegúrese de que no tiene ninguna actualización en espera de descarga o instalación. Vaya a **Configuración > Update & Security > Windows Update** y seleccione "Buscar actualizaciones". Es posible que tenga que comprobar varias veces hasta que no haya más actualizaciones disponibles y, a continuación, reinicie el equipo.

## <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR se bloquea después de actualizar Windows

Algunas versiones anteriores de Windows Mixed Reality para SteamVR ya no son compatibles con Windows. Para asegurarse de que la versión de Windows Mixed Reality para SteamVR es actual:

1. En la biblioteca de Steam, vaya **a Software > Windows Mixed Reality for SteamVR**.
2. Haga clic con el botón derecho en él y vaya a "Propiedades".
3. Seleccione la pestaña "Actualizar" y "Mantener siempre actualizada esta aplicación".
4. Para forzar la actualización, vaya a la pestaña "Archivos locales" y seleccione "Comprobar la integridad de los archivos de aplicación".
5. Reinicie Steam y SteamVR.

Si Todavía se bloquea SteamVR después de la actualización, es posible que tenga dos instalaciones de Windows Mixed Reality para SteamVR en la máquina. Para confirmar:

1. Busque ```%localappdata%\openvr\openvrpaths.vrpath``` y ábralo en Bloc de notas.
2. Busque varias entradas en las secciones "Controladores externos" para "MixedRealityVRDriver".
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Si ve varias entradas, quite la anterior de las dos entradas. Una vez que solo tenga una entrada, ya no debería haber una coma al final de la línea. Por ejemplo:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Guarde el archivo y ciérrelo.
5. Reinicie Steam y SteamVR.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Mis controladores no funcionan según lo previsto en SteamVR

1. Cierre SteamVR.
2. Vuelva a Windows Mixed Reality inicio y confirme que los controladores funcionan.
3. Vuelva a iniciar la experiencia de SteamVR y los controladores deben volver a la normalidad.
4. Si los problemas persisten, resalte los comentarios [Centro de opiniones sobre Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) en la Mixed Reality e incluya SteamVR en el resumen.

Usará los controladores de movimiento de forma diferente en distintos juegos. Estos son algunos aspectos básicos que le ayudarán a empezar:
* Para abrir el panel de Steam, presione directamente en el botón de posición izquierdo.
* Para salir de un juego de SteamVR y volver al Windows Mixed Reality inicio, presione Windows botón. A continuación, seleccione Mixed Reality inicio que aparece en pantalla.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Mis controladores izquierdo y derecho se invierten en SteamVR

Inicie el juego con los controladores desactivados y, a continuación, active el controlador izquierdo, seguido del derecho.

## <a name="my-games-are-running-slowly"></a>Mis juegos se ejecutan lentamente

1. Asegúrese de que el equipo cumple las especificaciones de SteamVR en Windows Mixed Reality y el juego que está reproduciendo.
2. En Portal de realidad mixta escritorio, seleccione "Pausar" para detener la versión preliminar del escritorio.
3. Vaya a **Configuración > System > Acerca** de y, en "Windows specifications", asegúrese de que "OS Build" es 16299.64 o posterior.
4. Asegúrese de que el equipo tiene los controladores de gráficos más recientes ("Buscar actualizaciones" en Windows Update).
5. Compruebe "Administrador de tareas" para ver qué otros procesos podrían estar consumiendo recursos en el equipo.
6. Compruebe si Steam está descargando un juego en segundo plano, lo que consume recursos y hace que los juegos se ejecuten mal.
7. Una pequeña clase de aplicaciones que no tienen una ventana visible (por ejemplo, Inicio de SteamVR), tienen un problema de rendimiento conocido. La mayoría de las aplicaciones no se encuentran en esta categoría y una corrección estará disponible en una actualización futura.

Si sigue teniendo problemas de rendimiento inesperados, envíenos sus comentarios mediante el [Centro de opiniones sobre Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Asegúrese de seguir las instrucciones para incluir [un seguimiento de rendimiento de SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr).

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR muestra un error de compositor (por ejemplo, "Shared IPC Compositor Conectar Failed (400)").

Esto puede ocurrir si el casco y el monitor principal están en dos adaptadores de vídeo diferentes. Conecte el monitor al mismo adaptador que el casco y configúrelo como monitor principal en Configuración **app > System > Display**.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>El contenido de SteamVR aparece en un lugar incorrecto, como debajo del suelo o encima de la cabeza

Restablezca la posición:

1. Seleccione la huella digital del controlador izquierdo para abrir el "Panel de SteamVR".
2. Seleccione el botón "Configuración".
3. Seleccione "Restablecer posición asentada".

## <a name="my-steam-app-closed-unexpectedly"></a>La aplicación My Steam se cerró inesperadamente

La aplicación de Steam se cerrará si:

* Se bloquea la pantalla del equipo
* Quitar el casco
* Cambio de usuarios
* El equipo entra en suspensión
