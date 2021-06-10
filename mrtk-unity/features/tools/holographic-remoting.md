---
title: Control remoto de holografías
description: Documentación sobre la comunicación remota holográfica con MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 196bbb7027389ea75ddc577e4efc397ca779d550
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647183"
---
# <a name="holographic-remoting"></a>Control remoto de holografías

La comunicación remota holográfica transmite contenido holográfico de un equipo a su Microsoft HoloLens en tiempo real, mediante una conexión de Wi-Fi o USB. Esta característica puede aumentar significativamente la productividad de los desarrolladores al desarrollar aplicaciones de realidad mixta.

El SDK de XR como se mencionó a continuación hace referencia a la nueva canalización de XR de [Unity en Unity 2019.3 y posteriores.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) Consulte [aquí](../../configuration/getting-started-with-mrtk-and-xrsdk.md) para obtener más información sobre el uso del SDK de XR con MRTK. XR heredado hace referencia a la canalización XR existente que se incluye en Unity 2018, está en desuso en Unity 2019.3 y se ha quitado en Unity 2020.

## <a name="initial-setup"></a>Instalación inicial

Para habilitar la comunicación remota con HoloLens, es importante asegurarse de que el proyecto usa los componentes de comunicación remota más recientes.

1. Abrir **ventana > Administrador de paquetes**
    - Si usa XR heredado: compruebe que está instalada la versión más reciente **Windows Mixed Reality** paquete.
    - Si usa el SDK de XR: compruebe que está instalada la versión más reciente del paquete del complemento XR de **Windows.**
1. Asegúrese de que la aplicación holographic remoting más reciente está instalada, en HoloLens, a través del Microsoft Store.

Continúe con las [instrucciones de instalación de XR heredadas](#legacy-xr-setup-instructions) o las instrucciones de configuración del SDK de [XR](#xr-sdk-setup-instructions) en función de la canalización que se utilice en el proyecto.

## <a name="legacy-xr-setup-instructions"></a>Instrucciones de configuración de XR heredadas

Las instrucciones siguientes solo se aplican a la comunicación remota con HoloLens 2. Si solo realiza comunicación remota con HoloLens (1ª generación), vaya directamente a Conexión a [HoloLens con Wi-Fi.](#connecting-to-the-hololens-with-wi-fi)

Cuando se usa una HoloLens 2, se ha agregado compatibilidad con la comunicación remota de datos de seguimiento ocular y de manos articuladas a MRTK. Para habilitar estas características, siga los pasos descritos en [Importación de DotNetWinRT en el proyecto](#import-dotnetwinrt-into-the-project).

Una vez importado, el siguiente paso consiste en seleccionar **Mixed Reality**  >    >  **Toolkit Utilities**  >  **Windows Mixed Reality**  >  **Check Configuration (Comprobar configuración).** Este paso agrega una definición de scripting que habilita la dependencia DotNetWinRT.

> [!NOTE]
> Cuando se usa Unity 2019.4 y versiones más recientes, no es necesario ejecutar la utilidad Comprobar configuración.

Para habilitar el seguimiento de las uniones de manos y el seguimiento ocular, siga los pasos de las secciones Depuración HoloLens 2 comunicación remota a través de la importación de paquetes de **Unity** y las secciones relacionadas.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Depuración de HoloLens 2 comunicación remota a través de la importación de paquetes de Unity

Si HoloLens 2 de las manos y el seguimiento de los ojos no funcionan con la comunicación remota, hay algunos puntos comunes de posibles problemas. Se enumeran a continuación en el orden en que se deben comprobar.

Estos problemas son especialmente relevantes cuando se ejecutan **en Unity 2019.3** o posterior.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importación de DotNetWinRT en el proyecto

1. Descargar la herramienta [Mixed Reality características](https://aka.ms/MRFeatureTool)

1. En la **vista Detectar características,** seleccione *Mixed Reality proyecciones de WinRT.*

    ![Selección del paquete DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. Haga **clic en Obtener** características y continúe con la importación del [paquete](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT en la configuración del reproductor

> [!NOTE]
> Cuando se usa Unity 2019.4 y versiones más recientes, el DOTNETWINRT_PRESENT define se incluye en los archivos .asmdef adecuados y no en la configuración del reproductor de Unity. El paso Comprobar configuración no es necesario.

A partir de la versión 2.5.0 de MRTK, por motivos de rendimiento, este #define ya no se establece automáticamente. Para habilitar esta marca, use el elemento de menú Mixed Reality  >  **Toolkit Utilities**  >  **Windows Mixed Reality** Check Configuration  >  **(Comprobar** configuración).

> [!Note]
> El elemento Comprobar configuración no muestra una confirmación. Para confirmar que se ha establecido la definición, vaya a Configuración del reproductor de Unity. Desde allí, en la pestaña UWP, active Otras configuraciones para definir símbolos de scripting. Asegúrese de DOTNETWINRT_PRESENT está escrito correctamente en esa lista. Si está ahí, este paso se ha hecho correctamente.

![DotNetWinRT Present](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>Eliminación de HoloLens 2 de comunicación remota específica

Si tiene conflictos u otros problemas debido a la presencia del adaptador de DotNetWinRT, póngase en contacto con uno de nuestros recursos [de ayuda.](../../index.md#getting-help)

## <a name="xr-sdk-setup-instructions"></a>Instrucciones de configuración del SDK de XR

Siga las Windows Mixed Reality de configuración de la página Introducción a [MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) y el SDK de XR y asegúrese de realizar el paso necesario para la comunicación remota de HoloLens en el editor.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Conexión a HoloLens con Wi-Fi

Una vez configurado el proyecto, se puede establecer una conexión con HoloLens.

1. En File > Build Settings (Configuración **de compilación** de archivos), asegúrese de que el tipo de compilación del proyecto está **establecido en Plataforma universal de Windows**
1. En HoloLens, inicie la **aplicación Holographic Remoting.**
1. En Unity, seleccione **Window > XR > Holographic Emulation (if using legacy XR) /Windows XR Plugin Remoting (if using XR SDK)**[Emulación holográfica de XR (si usa XR SDK heredado)].

    ![Iniciar emulación holográfica](../images/tools/remoting/StartHolographicEmulation.png)

1. Establezca **Modo de emulación** **en Remoto en Dispositivo.**

    ![Establecer el modo de emulación](../images/tools/remoting/SelectEmulationMode.png)

1. (**_Solo se aplica a XR heredado)_** Seleccione la versión **del dispositivo.**

    ![Selección de la versión del dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. Con la dirección IP que muestra la aplicación Holographic Remoting Player, establezca el **campo Equipo** remoto.

    ![Escriba la dirección IP.](../images/tools/remoting/EnterIPAddress.png)

1. Haga clic en **Conectar**.

> [!NOTE]
> Si no puede conectarse, asegúrese de que el HoloLens 2 está conectado al equipo y reinicie Unity.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Conexión a HoloLens con cable USB

La conexión de cable USB proporciona una mejor calidad y estabilidad de la representación. Para usar la conexión de cable USB, desconéctese de HoloLens Wi-Fi en configuración de HoloLens e inicie la aplicación Holographic Remoting Player. Se mostrará una dirección IP que comienza por 169. Use esta dirección IP en la configuración de emulación holográfica de Unity para conectarse. Una vez identificada la dirección IP del cable USB, es seguro conectar HoloLens a Wi-Fi nuevo.

## <a name="starting-a-remoting-session"></a>Inicio de una sesión de comunicación remota

Con Unity conectado a HoloLens, escriba el modo de reproducción en el editor.

Una vez completada la sesión, salga del modo de reproducción.

> [!NOTE]
> Hay un problema conocido con algunas versiones de Unity en las que el editor puede que se bloquee al entrar en modo de reproducción durante una sesión de comunicación remota. Este problema puede manifestarse si la ventana Holográfica está abierta cuando se carga el proyecto. Para asegurarse de que este problema no se produce, cierre siempre el cuadro de diálogo Holográfico antes de salir de Unity.

## <a name="see-also"></a>Vea también

- [Solución de problemas y limitaciones de Holographic Remoting](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Términos de licencia del software de Comunicación remota holográfica de Microsoft](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)