---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392657"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. Cambio de la plataforma de compilación

En el menú de Unity, seleccione File > Build Settings (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).

En la ventana Build Settings (Configuración de compilación), seleccione la plataforma **PC, Mac & Linux Standalone** (PC, Mac y Linux independiente) y haga clic en el botón **Switch Platform** (Cambiar plataforma) para cambiar la plataforma de compilación:

![Cambio de la plataforma de compilación](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

Cuando Unity haya terminado de cambiar la plataforma, haga clic en el icono con la x para cerrar la ventana Build Settings (Configuración de compilación).

### <a name="2-set-the-project-settings"></a>2. Configuración del proyecto

En el menú de Unity, seleccione **Edit** > **Project Configuración** > **XR Plug-in Management** (Editar > Configuración del proyecto > Administración de complementos de XR), asegúrese de estar en la pestaña Windows Standalone (Windows independiente) y active las casillas **OpenXR** y **Windows Mixed Reality feature set** (Conjunto de características de Windows Mixed Reality).

![Habilitación de OpenXR y Windows Mixed Reality feature set](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

En la ventana Project Settings (Configuración del proyecto), seleccione **OpenXR** y asegúrese de estar en la pestaña Windows Standalone (Windows independiente) y cambie **Depth submission mode** (Modo de envío de profundidad) de None (Ninguno) a **Depth 16 Bit** (Profundidad de 16 bits).

En la pestaña Interaction profiles (Perfiles de interacción), haga clic en el símbolo + para agregar **Eye Gaze Interaction Profile** (Perfil de interacción de mirada) y **Microsoft Hand Interaction Profile** (Perfil de interacción con la mano de Microsoft).

![Adición de Eye Gaze Interaction Profile y Microsoft Hand Interaction Profile](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

En **Open XR feature groups** > **All features** (Grupos de características de OpenXR > Todas las características), marque la casilla **Holographic App Remoting** (Comunicación remota de aplicación holográfica).

![Habilitación de Holographic App Remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

A continuación, active la casilla **Windows Mixed Reality** y, en el grupo Windows Mixed Reality, marque la casilla **Holographic App Remoting** (Comunicación remota de aplicación holográfica).

![Habilitación de Holographic App Remoting en Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. Compilación del proyecto de Unity

En el menú de Unity, seleccione File > Build Settings (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).

En la ventana Build Settings (Configuración de compilación), haga clic en el botón ***Add Open Scenes** _ (Agregar escenas abiertas) para agregar la escena actual a las escenas. En la lista Build (Compilación), haga clic en el botón _ *Build**:

![Ventana Build Settings (Configuración de compilación) de Unity con la escena agregada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

Elija una ubicación adecuada para almacenar la compilación, por ejemplo, Documents\MixedRealityLearning. Cree una nueva carpeta y asígnele un nombre adecuado, por ejemplo, ComunicaciónRemotaHolográficaPC. A continuación, haga clic en el botón ***Select Folder*** (Seleccionar carpeta) para iniciar el proceso de compilación:

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

Espere a que Unity finalice el proceso de compilación.

![Proceso de compilación de Unity en curso](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

Haga doble clic en el archivo ejecutable para abrir la aplicación para PC de comunicación remota holográfica en el equipo.

> [!NOTE]
> Debido a algunos problemas conocidos de la aplicación para PC de comunicación remota holográfica compilada como UWP, estamos compilando la aplicación para PC como Windows Standalone (Windows independiente) para OpenXR.


# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1. Configuración del reproductor

En la sección **XR Settings** (Configuración de XR), seleccione la casilla **WSA Holographic Remoting Supported** (Admitir la comunicación remota holográfica de WSA) y habilite la comunicación remota holográfica.

![Ventana XR Settings (Configuración de XR) de Unity con WSA Holographic Remoting Supported (Admitir la comunicación remota holográfica de WSA) habilitado](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Compilación del proyecto de Unity

En el menú de Unity, seleccione File > Build Settings (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).

En la ventana Build Settings (Configuración de compilación), haga clic en el botón ***Add Open Scenes** _ (Agregar escenas abiertas) para agregar la escena actual a las escenas. En la lista Build (Compilación), haga clic en el *_botón Build_* (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar Plataforma universal de Windows):

![Ventana Build Settings (Configuración de compilación) de Unity con la escena agregada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

En la ventana Build Universal Windows Platform (Compilar Plataforma universal de Windows), elija una ubicación adecuada para almacenar la compilación, como por ejemplo, Mis Documentos\AprendizajeRealidadMixta. Cree una nueva carpeta y asígnele un nombre adecuado, por ejemplo, ComunicaciónRemotaHolográficaPC. A continuación, haga clic en el botón ***Select Folder*** (Seleccionar carpeta) para iniciar el proceso de compilación:

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Espere a que Unity finalice el proceso de compilación.

![Proceso de compilación de Unity en curso](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Compilar e implementar la aplicación

Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación. Navegue dentro de la carpeta y haga doble clic en el archivo .sln para abrirlo en Visual Studio:

![Explorador de Windows con la solución de Visual Studio recién creada seleccionada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que todos los componentes de los requisitos previos estén instalados, tal como se especifica en la documentación Instalación de herramientas.

Configure Visual Studio para PC. Para ello, selecciona la configuración Publicación, la arquitectura x64 y la opción Equipo local como destino:

![Visual Studio configurado para el equipo local](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Haga clic en el botón que indica ***Equipo local***. Comienza la compilación e implementación de la aplicación en el PC. La aplicación se instalará de forma predeterminada en su PC.
