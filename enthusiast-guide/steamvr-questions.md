---
title: Preguntas más frecuentes sobre SteamVR
description: Solución avanzada de problemas de realidad mixta de Windows que va más allá de nuestra documentación de soporte técnico estándar para el consumidor.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, SteamVR
ms.openlocfilehash: 0e355fc5035d7966f52642058d2f0ecc91b88351
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692426"
---
# <a name="steamvr-faqs"></a>Preguntas más frecuentes sobre SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>¿Cómo puedo jugar a SteamVR Games en el casco de la realidad mixta de Windows?

1. [Descargue e instale SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe). El tutorial de SteamVR debe iniciarse automáticamente al iniciar SteamVR.
2. Conecte los auriculares al equipo y encienda los controladores de movimiento.
3. Una vez que se haya cargado la Página principal de Windows Mixed Reality y los controladores estén visibles, abra la aplicación de vapor en el escritorio.
4. Use la aplicación de vapor para iniciar un juego de SteamVR desde la biblioteca de vapor. Para iniciar juegos de SteamVR sin desconectar el casco, busque e inícielo en Inicio de Windows Mixed Reality **> todas las aplicaciones** . 

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Un mensaje dice "para usar SteamVR con Windows Mixed Reality, debe instalar la Windows Update más reciente" o "modo de desarrollador de Windows necesario".

1. Asegúrese de que el equipo está ejecutando la versión más reciente de Windows 10. Vaya a **configuración > sistema > acerca** de y, en "Especificaciones de Windows", asegúrese de que "compilación de SO" sea 16299,64 o superior.
2. Asegúrese de que no tiene ninguna actualización en espera para descargar o instalar. Vaya a **configuración > actualizar & seguridad > Windows Update** y seleccione "buscar actualizaciones". Es posible que tenga que comprobar varias veces hasta que no haya más actualizaciones disponibles y, a continuación, reiniciar el equipo.

## <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR se bloquea después de actualizar Windows.

Algunas versiones anteriores de Windows Mixed Reality para SteamVR ya no son compatibles con Windows. Para asegurarse de que la versión de Windows Mixed Reality para SteamVR es actual:
1. En la biblioteca de vapor, vaya a **Software > Windows Mixed Reality para SteamVR** .
2. Haga clic con el botón derecho en él y vaya a "propiedades".
3. Seleccione la pestaña "actualizar" y "mantener siempre actualizada esta aplicación".
4. Fuerce la actualización; para ello, vaya a la pestaña "archivos locales" y seleccione "comprobar la integridad de los archivos de aplicación".
5. Reinicie vapor y SteamVR.

Si SteamVR todavía se bloquea después de la actualización, es posible que tenga dos instalaciones de Windows Mixed Reality para SteamVR en el equipo. Para confirmar si este es el caso:
1. Búsquelo ```%localappdata%\openvr\openvrpaths.vrpath``` y ábralo en el Bloc de notas.
2. En las secciones "controladores externos", busque varias entradas para "MixedRealityVRDriver" 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Si ve varias entradas, quite las dos entradas más antiguas. Una vez que solo tiene una entrada, ya no debería haber una coma al final de la línea. Por ejemplo:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Guarde el archivo y ciérrelo.
5. Reinicie vapor y SteamVR.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Mis controladores no funcionan como se esperaba en SteamVR.

1. Cierre SteamVR.
2. Vuelva a la Página principal de Windows Mixed Reality y confirme que los controladores funcionan.
3. Vuelva a iniciar la experiencia de SteamVR y los controladores deben volver a la normalidad.
4. Si los problemas persisten, envíe los comentarios de los archivos con el [centro de comentarios de Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) en la categoría realidad mixta e incluya SteamVR en el resumen.

Tenga en cuenta que usará los controladores de movimiento de forma diferente en distintos juegos. Estos son algunos aspectos básicos que le ayudarán a empezar:
* Para abrir el panel de vapor, presione hacia abajo en el stick analógico izquierdo.
* Para salir de un juego de SteamVR y volver a la Página principal de Windows Mixed Reality, presione el botón Windows. A continuación, seleccione el botón Inicio de realidad mixta que aparece en la pantalla.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Los controladores izquierdo y derecho se invierten en SteamVR.

Inicie el juego con los controladores desactivado y, a continuación, encienda el controlador izquierdo, seguido del derecho.

## <a name="my-games-are-running-slowly"></a>Mis juegos se ejecutan lentamente.

1. Asegúrese de que su equipo cumple con las especificaciones de SteamVR en Windows Mixed Reality y del juego SteamVR que está reproduciendo.
2. En el portal de realidad mixta del escritorio, seleccione "pausar" para detener la vista previa del escritorio.
3. Vaya a **configuración > sistema > sobre** y en "Especificaciones de Windows", asegúrese de que "compilación de SO" sea 16299,64 o posterior.
4. Asegúrese de que el equipo tiene los controladores de gráficos más recientes ("buscar actualizaciones" en Windows Update).
5. Consulte "Administrador de tareas" para ver qué otros procesos podrían estar consumiendo recursos en su PC.
6. Compruebe si la secuencia está descargando un juego en segundo plano. Esto puede consumir recursos y hacer que los juegos se ejecuten de forma deficiente.
7. Una pequeña clase de aplicaciones que no tienen una ventana visible (por ejemplo, SteamVR Home) tienen un problema de rendimiento conocido. La gran mayoría de las aplicaciones no entran en esta categoría y una corrección estará disponible en una futura actualización.

Si sigue teniendo problemas de rendimiento inesperados, envíenos sus comentarios mediante el [centro de comentarios de Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Asegúrese de seguir las instrucciones para [incluir un seguimiento de rendimiento de SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr). 

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR muestra un error del compositor (por ejemplo, "error al conectar el compositor de IPC compartido (400)").

Esto puede ocurrir si los auriculares y el monitor principal están en dos adaptadores de vídeo diferentes. Conecte el monitor al mismo adaptador que el casco y configúrelo para que sea el monitor principal de configuración de la **aplicación > sistema > pantalla** .

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>El contenido de SteamVR aparece en el lugar equivocado, como debajo del piso o por encima de mi cabeza.

Restablezca su posición: 
1. Haga clic en el stick de la izquierda del controlador para abrir el "panel de SteamVR".
2. Seleccione el botón "configuración".
3. Seleccione "restablecer posición asentada".

## <a name="my-steam-app-closed-unexpectedly"></a>La aplicación de vapor se cerró de forma inesperada.

La aplicación de vapor se cerrará si bloquea la pantalla del equipo, quita el casco, cambia de usuario o si el equipo entra en suspensión.
