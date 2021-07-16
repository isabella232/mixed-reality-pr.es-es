---
ms.openlocfilehash: f7a018d34ee17589ae2e12c2f50f744d736534e2
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2021
ms.locfileid: "114339924"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. En el HoloLens, vaya **al** Microsoft Store e instale la aplicación **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En el HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya al **menú Editar** y **seleccione Project Configuración**.
1. Seleccione **XR Plug-in Management**(Administración de complementos XR).
1. Asegúrese de **Windows pestaña Independiente** está seleccionada, busque **OpenXR** **y Windows Mixed Reality características** establecidas en la lista y active sus casillas.
1. A continuación, vaya al **menú Ventana,** expanda el submenú **XR** y seleccione Comunicación remota **del Editor de OpenXR.**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con la administración de complementos XR resaltada](../images/openxr-features-img-02.png)

1. Haga clic **en Habilitar comunicación remota del editor.**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con características resaltadas](../images/openxr-features-img-03.png)

1. Si aparece **el botón Habilitar** dependencias que faltan, haga clic en eso también. En el cuadro de error situado encima del botón se describen las características que está habilitando y por qué.
1. En **Nombre de host remoto,** escriba la dirección IP del HoloLens.
   1. Cambie otras opciones según sea necesario.
   1. El editor intentará conectarse una vez iniciado el modo de reproducción.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en el HoloLens. Para depurar scripts de C# en modo de reproducción, [Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

> [!NOTE]
> A partir de la versión 0.1.0, el entorno de ejecución de comunicación remota holográfica no admite anclajes y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.  Esta característica se va a publicar en futuras versiones.

# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento XR para Unity 2019/2020 y Windows](#tab/winxr)

1. En el HoloLens, vaya **al** Microsoft Store e instale la aplicación **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En el HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya al **menú Editar** y **seleccione Project Configuración**.
1. Seleccione **XR Plug-in Management**(Administración de complementos XR).
1. Asegúrese de que la **pestaña PC, Mac & Linux Independiente** está seleccionada, busque Windows Mixed Reality en la lista y active su casilla. 
1. A continuación, vaya al **menú Ventana,** expanda el submenú **XR** y seleccione Windows **remota del complemento XR.**
1. Establezca **Modo de emulación** **en Remoto en Dispositivo.**
1. En **Equipo remoto,** escriba la dirección IP del HoloLens.
1. Para conectarse, haga lo siguiente:
   1. Para conectarse manualmente, desactive **Conectar en Reproducir** y seleccione **Conectar**. Debería ver el cambio **de Estado de** conexión a **Conectado** y ver la pantalla en blanco en el HoloLens.
   1. Para conectarse automáticamente, compruebe **Conectar en Reproducir**. El editor intentará conectarse una vez iniciado el modo de reproducción.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en el HoloLens. Para depurar scripts de C# en modo de reproducción, [Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

1. En el HoloLens, vaya **al** Microsoft Store e instale la aplicación **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En el HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya  al menú Ventana, expanda el submenú **XR** y seleccione **Emulación holográfica** (marcada como en desuso en Unity 2019).
1. Establezca **Modo de emulación** **en Remoto en Dispositivo.**
1. Establezca **Versión del** dispositivo según si usa una versión de primera generación HoloLens o una HoloLens 2.
1. En **Equipo remoto,** escriba la dirección IP del HoloLens.
1. Seleccione **Conectar**. Debería ver el cambio **de Estado de** conexión a **Conectado** y ver la pantalla en blanco en el HoloLens.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en el HoloLens. Para depurar scripts de C# en modo de reproducción, [Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).
