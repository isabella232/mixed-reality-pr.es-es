---
ms.openlocfilehash: 17719d2547aa10981e7b8cdf0d2c7d56823e6da5
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345118"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. En HoloLens, vaya a la **Microsoft Store** e instale la **[aplicación Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya al menú **Editar** y seleccione **Project Settings (Configuración del proyecto).**
1. Seleccione **Administración de complementos XR.**
1. Asegúrese de **que la pestaña Independiente** de Windows está seleccionada, busque **OpenXR** **y Windows Mixed Reality de** características en la lista y active sus casillas.
1. A continuación, vaya al **menú Ventana,** expanda el submenú **XR** y seleccione OpenXR Editor Remoting (Comunicación remota **del editor de OpenXR).**
1. Haga clic **en Habilitar comunicación remota del editor.**
1. Si aparece **el botón Habilitar** dependencias que faltan, haga clic también en eso. En el cuadro de error situado encima del botón se describen las características que está habilitando y por qué.
1. En **Remote Host Name (Nombre de** host remoto), escriba la dirección IP de HoloLens.
   1. Cambie otras opciones según sea necesario.
   1. El editor intentará conectarse una vez iniciado el modo de reproducción.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en HoloLens.

# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento XR para Unity 2019/2020 y Windows](#tab/winxr)

1. En HoloLens, vaya a la **Microsoft Store** e instale la **[aplicación Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya al menú **Editar** y seleccione **Project Settings (Configuración del proyecto).**
1. Seleccione **Administración de complementos XR.**
1. Asegúrese de **que la pestaña Independiente** de Windows está seleccionada, busque **Windows Mixed Reality** en la lista y active su casilla.
1. A continuación, vaya al **menú Ventana,** expanda el submenú **XR** y seleccione Windows XR Plugin Remoting (Comunicación remota **del complemento XR de Windows).**
1. Establezca **Modo de emulación** **en Remoto en Dispositivo.**
1. En **Equipo remoto,** escriba la dirección IP de HoloLens.
1. Para conectarse, haga lo siguiente:
   1. Para conectarse manualmente, desactive **Conectar al reproducir** y seleccione **Conectar.** Debería ver el **cambio de Estado de** conexión a Conectado **y** ver la pantalla en blanco en HoloLens.
   1. Para conectarse automáticamente, active **Conectar en Play**. El editor intentará conectarse una vez iniciado el modo de reproducción.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en HoloLens.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

1. En HoloLens, vaya a la **Microsoft Store** e instale la **[aplicación Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. En HoloLens, inicie la **aplicación Holographic Remoting Player.**
1. En Unity, vaya  al menú Ventana, expanda el submenú **XR** y seleccione **Emulación holográfica** (marcada como en desuso en Unity 2019).
1. Establezca **Modo de emulación** **en Remoto en Dispositivo.**
1. Establezca **La versión del** dispositivo según si usa hololens de primera generación o un HoloLens 2.
1. En **Equipo remoto,** escriba la dirección IP de HoloLens.
1. Seleccione **Conectar**. Debería ver el **cambio de Estado de** conexión a Conectado **y** ver la pantalla en blanco en HoloLens.
1. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en HoloLens.
