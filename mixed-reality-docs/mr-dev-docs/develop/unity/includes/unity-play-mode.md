---
ms.openlocfilehash: 40d24083ec83b9d6faebc00cf801d1f6f55fddd7
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392302"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. En HoloLens, vaya al Microsoft Store **e** instale la **[aplicación Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya al menú **Editar** y seleccione **Configuración del proyecto.**
1. Seleccione **XR Plug-in Management**(Administración de complementos XR).
1. Asegúrese de **que la pestaña Independiente** de Windows está seleccionada, busque **OpenXR** **y Windows Mixed Reality características** establecidas en la lista y active sus casillas.
1. A continuación, vaya al **menú Ventana,** expanda el submenú **XR** y seleccione Comunicación remota **del Editor de OpenXR.**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con la administración de complementos XR resaltada](../images/openxr-features-img-02.png)

1. Haga clic **en Habilitar comunicación remota del editor.**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con características resaltadas](../images/openxr-features-img-03.png)

1. Si aparece **el botón Habilitar** dependencias que faltan, haga clic en eso también. En el cuadro de error situado encima del botón se describen las características que está habilitando y por qué.
1. En **Remote Host Name (Nombre de** host remoto), escriba la dirección IP de HoloLens.
   1. Cambie otras opciones según sea necesario.
   1. El editor intentará conectarse una vez iniciado el modo de reproducción.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en HoloLens. Para depurar scripts de C# en modo de reproducción, [Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

> [!NOTE]
> A partir de la versión 0.1.0, el entorno de ejecución de comunicación remota holográfica no admite anclajes y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.  Esta característica se va a publicar en futuras versiones.

# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento XR para Unity 2019/2020 y Windows](#tab/winxr)

1. En HoloLens, vaya al Microsoft Store **e** instale la **[aplicación Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya al menú **Editar** y seleccione **Configuración del proyecto.**
1. Seleccione **XR Plug-in Management**(Administración de complementos XR).
1. Asegúrese de **que la pestaña Independiente** de Windows está seleccionada, busque **Windows Mixed Reality** en la lista y active su casilla.
1. A continuación, vaya al **menú Ventana,** expanda el submenú **XR** y seleccione Comunicación remota **del complemento XR de Windows.**
1. Establezca **Modo de emulación** **en Remoto en Dispositivo.**
1. En **Equipo remoto,** escriba la dirección IP de HoloLens.
1. Para conectarse, haga lo siguiente:
   1. Para conectarse manualmente, desactive **Conectar en Play** y seleccione **Conectar.** Debería ver el cambio **de Estado de** conexión a Conectado **y** ver que la pantalla se deja en blanco en HoloLens.
   1. Para conectarse automáticamente, active **Conectar en Play**. El editor intentará conectarse una vez iniciado el modo de reproducción.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en HoloLens. Para depurar scripts de C# en modo de reproducción, [Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

1. En HoloLens, vaya al Microsoft Store **e** instale la **[aplicación Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya  al menú Ventana, expanda el submenú **XR** y seleccione **Emulación holográfica** (marcada como en desuso en Unity 2019).
1. Establezca **Modo de emulación** **en Remoto en Dispositivo.**
1. Establezca **Versión del** dispositivo según si usa una versión de HoloLens de primera generación o un HoloLens 2.
1. En **Equipo remoto,** escriba la dirección IP de HoloLens.
1. Seleccione **Conectar**. Debería ver el cambio **de Estado de** conexión a Conectado **y** ver que la pantalla se deja en blanco en HoloLens.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en HoloLens. Para depurar scripts de C# en modo de reproducción, [Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).
