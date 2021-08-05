---
title: Implementación en HoloLens y cascos de WMR
description: Documentación para compilar e implementar aplicaciones en varios dispositivos.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Visual Studio
ms.openlocfilehash: 622c7ca4b9c527630b5677fe377d1d3108bdfe08c9dc616bfd4d3256b83b9ab0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209516"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>Implementación en HoloLens y cascos de WMR

Hay dos maneras de implementar aplicaciones compiladas con MRTK en el dispositivo Windows: univeral Windows Platform (UWP) y la plataforma independiente. Las aplicaciones creadas para HoloLens 1 o HoloLens 2 deben tener como destino UWP, mientras que las aplicaciones creadas para cascos WMR pueden tener como destino UWP o independiente.

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>Compilación e implementación de MRTK para HoloLens 1, HoloLens 2 y cascos WMR (UWP)

Puede encontrar instrucciones sobre cómo compilar e implementar para **HoloLens 1** **y HoloLens 2** (UWP) en Compilar la aplicación en [el dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device). Estos pasos también le permiten implementar en **cascos WMR.**

> [!NOTE]
> Al implementar la aplicación en el dispositivo en Visual Studio, debe configurar los Visual Studio de forma ligeramente diferente en función del dispositivo. Las configuraciones son las siguientes:
>
>| Plataforma | Configuración | Architecture | Destino |
|---|---|---|---|
| HoloLens 2 | Versión o maestra | ARM64 | Dispositivo |
| HoloLens 1 | Versión o maestra | x86 | Dispositivo |
| Cascos WMR | Versión o maestra | x64 | Equipo local |

**Sugerencia:** Al compilar para HoloLens 1, HoloLens 2 o WMR, se recomienda que las opciones de compilación "Versión del SDK de destino" y "Versión mínima de la plataforma" se parezcan a las de la imagen siguiente:

![Ventana de compilación](../features/images/getting-started/BuildWindow.png)

El resto de opciones de configuración pueden ser diferentes (p. ej., Configuración de compilación/Arquitectura/Tipo de compilación y otras opciones se pueden cambiar dentro de la solución de Visual Studio).

Asegúrese de que la lista desplegable de versión de SDK de destino incluya la opción "10.0.18362.0". En caso contrario, es necesario instalar el [Windows SDK más reciente](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

### <a name="unity-20192020-and-hololens"></a>Unity 2019/2020 y HoloLens

Si una HoloLens aplicación aparece como un panel 2D en el dispositivo, asegúrese de que se han configurado las siguientes opciones en Unity antes de implementar la aplicación para UWP:

Si usa la compatibilidad con XR integrada heredada (solo Unity 2019):

1. Vaya a Edit > Project Settings, Player (Editar > Configuración del proyecto, Jugador)
1. En **XR Settings** (Configuración de XR) en la pestaña UWP, asegúrese de que la opción **Virtual Reality Supported** (Compatible con realidad virtual) está habilitada y de que el SDK de **Windows Mixed Reality** se ha agregado a los SDK.
1. Compilación e implementación en Visual Studio

Si usa OpenXR o Windows complementos XR:

1. Siga los pasos que encontrará en [Introducción a XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Asegúrese de que el perfil de configuración sea **DefaultXRSDKConfigurationProfile**
1. Vaya a **Edit > Project Settings, XR-Plugin Management** (Editar > Configuración del proyecto, Administración del complemento XR) y asegúrese de que **Windows Mixed Reality** está habilitado.
1. Compilación e implementación en Visual Studio

>[!IMPORTANT]
> Si usa Unity 2019.3.x, seleccione **ARM64** y no **ARM** como arquitectura de compilación en Visual Studio. Con la configuración predeterminada de Unity en Unity 2019.3.x, una aplicación de Unity no se implementará en HoloLens si se selecciona ARM debido a un error de Unity.
>
> Si se requiere la arquitectura de ARM, vaya a **Edit > Project Settings, Player** (Editar > Configuración del proyecto, Jugador) y, en el menú **Other Settings** (Otras opciones) , deshabilite **Graphics Jobs** (Trabajos de gráficos). Al deshabilitar **Graphics Jobs** (Trabajos de gráficos) permitirá que la aplicación se implemente con la arquitectura de compilación de ARM para Unity 2019.3.x, pero se recomienda ARM64.
>
> Este problema se corrigió en Unity 2019.4 y Unity 2020.3.

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>Creación e implementación de MRTK en cascos WMR (independiente)

Las compilaciones independientes de MRTK se pueden usar en cascos WMR. Una compilación independiente para un casco de WMR requiere los siguientes pasos adicionales:

> [!NOTE]
> El SDK de XR de Unity también admite WMR nativo en compilaciones independientes, pero no requiere el complemento SteamVR o WMR. Estos pasos son necesarios para la versión de XR heredada de Unity.

1. Instalación de [Steam](https://store.steampowered.com/about/)
1. Instalación de [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. Instalación del [complemento de WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

### <a name="how-to-use-wmr-plugin"></a>Uso del complemento de MWR

1. Abra Steam y busque el complemento de Windows Mixed Reality.
    - Compruebe que SteamVR esté cerrado antes de iniciar el complemento de WMR. Al iniciar el complemento de WMR, también se inicia SteamVR.
    - Asegúrese de que el casco de WMR está conectado.

    ![Búsqueda de complementos de WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Seleccione **Launch** (Iniciar) para Windows Mixed Reality para el complemento SteamVR.

    ![Complemento de WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - Se iniciará SteamVR y el complemento de WMR y aparecerá una nueva ventana de estado de seguimiento para el casco de WMR.
    - Para obtener más información, visite la [documentación de Steam de Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)

        ![Aspecto de inicio de WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. En Unity, con la escena de MRTK abierta, vaya a **File > Build Settings** (Archivo > Configuración de la compilación).

1. Compilación de la escena
    - Seleccione **Add Open Scene** (Agregar escena abierta).
    - Asegúrese de que la plataforma sea **Standalone** (Independiente).
    - Seleccione **Build** (Compilar).
    - Elija la ubicación de la nueva compilación en el Explorador de archivos

    ![Configuración de compilación para plataformas independientes](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Se creará un nuevo archivo ejecutable de Unity. Para iniciar la aplicación, selecciónelo en el Explorador de archivos.

    ![Unity en el Explorador de archivos](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Vea también

- [Compatibilidad con Android y iOS](using-ar-foundation.md)
- [Compatibilidad con el movimiento Leap](leap-motion-mrtk.md)
- [Detección de las capacidades de la plataforma](detecting-platform-capabilities.md)
