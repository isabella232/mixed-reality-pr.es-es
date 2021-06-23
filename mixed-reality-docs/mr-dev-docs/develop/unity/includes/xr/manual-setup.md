---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535730"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Instale el complemento OpenXR con la nueva Mixed Reality Feature Tool. Siga las [instrucciones de instalación y uso y](../../welcome-to-mr-feature-tool.md) seleccione el paquete Mixed Reality complemento **OpenXR** en la **categoría Soporte técnico de la** plataforma:

![Mixed Reality paquetes de feature tool con el complemento xr abierto resaltado](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Establecimiento del destino de compilación

Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:

1. Seleccione File > Build Settings... (Configuración **de compilación de archivos).**
2. Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**
3. Establezca **Architecture** (Arquitectura) en **ARM64**.
4. Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5. Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).
6. Establezca **Versión del SDK de destino** en Instalado más **reciente**

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configuración de la administración de complementos XR para OpenXR

Para establecer OpenXR como runtime en Unity:

1. En el Editor de Unity, vaya **a Editar > configuración del proyecto.**
2. En la lista de configuración, seleccione **Administración de complementos XR.**
3. Seleccione **Instalar administración de complementos XR** si aparece Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos ![ XR resaltada](../../images/wmr-config-img-5.png)
4. Active la **casilla Initialize XR on Startup (Inicializar XR al iniciar)**
5. Si el destino es Desktop VR, permanezca en la pestaña PC Independiente (el monitor) y active las casillas **OpenXR** **y Windows Mixed Reality de características.**
6. Si el destino es HoloLens 2, cambie a la pestaña Plataforma universal de Windows (el logotipo de Windows) y seleccione los cuadros **OpenXR** **y Microsoft HoloLens de características.**

![Captura de pantalla del panel de configuración del proyecto abierto en el editor de Unity con la administración de complementos XR resaltada](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Si ve un icono de advertencia amarillo junto a **Complemento OpenXR,** haga clic en el icono y seleccione **Corregir todo** antes de continuar. Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.

![Captura de pantalla de la ventana de validación del proyecto de OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

Si va a desarrollar para HoloLens 2, seleccione el elemento de menú Mixed Reality > **Project > Apply recommended project settings for HoloLens 2** (Aplicar configuración de proyecto recomendada para HoloLens 2 obtener un mejor rendimiento de la aplicación).

![Captura de pantalla del elemento de menú de realidad mixta abierto con OpenXR seleccionado](../../images/openxr-img-08.png)

Ya está listo para empezar a desarrollar con OpenXR en Unity.  Continúe con la sección siguiente para aprender a usar los ejemplos de OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Proyectos de ejemplo de Unity para OpenXR y HoloLens 2

Consulte el repositorio de ejemplos de [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para ver proyectos de Unity de ejemplo que muestran cómo compilar aplicaciones de Unity para cascos HoloLens 2 o Mixed Reality mediante el complemento Mixed Reality OpenXR.

O bien, si está listo para empezar a trabajar por su cuenta desde un proyecto en blanco, vaya al artículo [Configuración de la](../../camera-in-unity.md) cámara.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

> [!CAUTION]
> El complemento XR de Windows está en desuso en Unity 2021.1 y se quitará en Unity 2021.2.  Para el desarrollo de Unity 2020, Microsoft recomienda el complemento OpenXR en su lugar.

Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:

1.  Seleccione File > Build Settings... (Configuración **de compilación de archivos).**
2.  Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**
3.  Establezca **Architecture** (Arquitectura) en **ARM64**.
4.  Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5.  Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).
6.  Establezca **Versión del SDK de destino** en Instalado más **reciente**
7.  Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

Después de configurar la plataforma, debe dejar [](../../../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte:

1. En el Editor de Unity, vaya **a Editar > configuración del** proyecto y seleccione Administración de complementos **XR.**

2. Seleccione **Install XR Plugin Management (Instalar administración de complementos XR)** si aparece.

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](../../images/wmr-config-img-5.png)

3. Seleccione **Initialize XR on Startup (Inicializar XR)** **al iniciar Windows Mixed Reality**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](../../images/wmr-config-img-7.png)

4. Seleccione la **sección XR Plug-in Management** Windows Mixed Reality (Administración de complementos XR), active todas las casillas y establezca Depth Buffer Format (Formato del búfer de profundidad) en Depth Buffer 16 Bit (Búfer de  >   profundidad de  **16 bits).**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity Windows Mixed Reality sección resaltada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[XR heredado](#tab/legacy)

> [!CAUTION]
> El XR heredado está en desuso en Unity 2019 y se ha quitado en Unity 2020.

Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:

1.  Seleccione File > Build Settings... (Configuración **de compilación de archivos).**
2.  Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**
3.  Establezca **Architecture** (Arquitectura) en **ARM64**.
4.  Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5.  Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).
6.  Establezca **Versión del SDK de destino** en Instalado más **reciente**
7.  Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

Después de configurar la plataforma, debe hacer [](../../../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.

1. Abra **Configuración del reproductor...** desde la **configuración de compilación... ventana** y expanda el **grupo XR Settings (Configuración de XR).**
2. En la **sección Configuración de XR,** seleccione **Virtual Reality Supported (Virtual Reality compatible)** para agregar la lista Dispositivos de realidad virtual.
3. Establezca **Depth Format (Formato de** profundidad) en profundidad de **16 bits** y active Enable Depth Buffer Sharing **(Habilitar uso compartido de búfer de profundidad).**
4. En **Stereo Rendering Mode** (Modo de representación estéreo), seleccione **Single Pass Instanced** (Instancia de paso único)
5. Seleccione **WSA Holographic Remoting Supported (Comunicación** remota holográfica de WSA compatible) si desea usar la comunicación remota del modo de reproducción holográfica.

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la sección Configuración del reproductor resaltada](../../images/wmr-config-img-9.png)
