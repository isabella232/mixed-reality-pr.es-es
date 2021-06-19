---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394589"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Instale el complemento OpenXR con la nueva Mixed Reality Feature Tool. Siga las [instrucciones de instalación y uso](../../welcome-to-mr-feature-tool.md) y seleccione el Mixed Reality complemento **OpenXR** en la categoría Mixed Reality Toolkit:

![Mixed Reality paquetes de feature tool con el complemento xr abierto resaltado](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Establecimiento del destino de compilación

Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:

1. Seleccione File > Build Settings... (Configuración **de compilación de archivos).**
2. Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**
3. Establezca la **arquitectura** en **ARM 64**
4. Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5. Establezca **Build Type** (Tipo de compilación) en **D3D**.
6. Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configuración de la administración de complementos XR para OpenXR

Para establecer OpenXR como runtime en Unity:

1. En el Editor de Unity, vaya **a Editar > configuración del proyecto.**
2. En la lista de configuración, seleccione **Administración de complementos XR.**
3. Active los **cuadros Inicializar XR al inicio** y **OpenXR**
4. Si el destino HoloLens 2, asegúrese de que está en la plataforma para UWP y **seleccione Microsoft HoloLens conjunto de características.**

![Captura de pantalla del panel de configuración del proyecto abierto en el editor de Unity con la administración de complementos XR resaltada](../../images/openxr-img-05.png)

### <a name="optimization"></a>Optimization

Si va a desarrollar para HoloLens 2, vaya a Mixed Reality> **OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance (Aplicar la configuración de proyecto recomendada para HoloLens 2 obtener un mejor rendimiento de la aplicación).

![Captura de pantalla del elemento de menú de realidad mixta abierto con OpenXR seleccionado](../../images/openxr-img-08.png)

> [!IMPORTANT]
> Si ve un icono de advertencia amarillo junto a **Complemento OpenXR,** haga clic en el icono y **seleccione Corregir todo** antes de continuar. Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.

![Captura de pantalla de la ventana de validación del proyecto de OpenXR](../../images/openxr-img-06.png)

Ya está listo para empezar a desarrollar con OpenXR en Unity.  Continúe con la sección siguiente para aprender a usar los ejemplos de OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Proyectos de ejemplo de Unity para OpenXR y HoloLens 2

Consulte el repositorio de ejemplos de [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para ver proyectos de Unity de ejemplo que muestran cómo compilar aplicaciones de Unity para cascos HoloLens 2 o Mixed Reality mediante el complemento Mixed Reality OpenXR.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:

1.  Seleccione File > Build Settings... (Configuración **de compilación de archivos).**
2.  Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**
3.  Establezca la **arquitectura** en **ARM 64**
4.  Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5.  Establezca **Build Type** (Tipo de compilación) en **D3D**.
6.  Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)
7.  Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

Después de configurar la plataforma, debe dejar [](../../../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte:

1. En el Editor de Unity, vaya **a Editar > configuración del** proyecto y seleccione Administración de complementos **XR.**

2. Seleccione **Install XR Plugin Management (Instalar administración de complementos XR).**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](../../images/wmr-config-img-5.png)

3. Seleccione **Initialize XR on Startup (Inicializar XR)** **al iniciar Windows Mixed Reality**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](../../images/wmr-config-img-7.png)

4. Expanda la **sección XR Plug-in Management (Administración** de complementos XR) y seleccione la pestaña **Univeral Windows Platform Settings (Configuración de plataforma de Windows univeral).**
5. Si usa Unity 2020 o posterior, verá las opciones para comprobar **OpenXR** o **Windows Mixed Reality**. 
    * Puede elegir cualquiera de los entornos de ejecución.  Si va a desarrollar específicamente para HoloLens 2 o HP Reverb G2 y decide probar **OpenXR,** active la casilla OpenXR y revise nuestra guía Uso del complemento [de OpenXR](../../openxr-getting-started.md) de Mixed Reality para Unity para configurarse correctamente para estos dispositivos antes de volver a este tutorial.

> [!NOTE]
> A partir de Unity 2020 LTS, Microsoft está adoptando el desarrollo con OpenXR.  A medida que migramos a esta ruta de acceso, en Unity 2021.1 el complemento XR de Windows estará en desuso y se quitará en 2021.2, lo que hace que OpenXR sea la única ruta de acceso admitida. Puede encontrar más información en [Uso del complemento Mixed Reality OpenXR.](../../openxr-getting-started.md)

6. Si decide elegir  el complemento de Windows Mixed Reality, active todas las casillas y establezca **Modo de envío de** profundidad en Profundidad **de 16 bits.**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity Windows Mixed Reality sección resaltada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[XR heredado](#tab/legacy)

Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:

1.  Seleccione File > Build Settings... (Configuración **de compilación de archivos).**
2.  Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**
3.  Establezca la **arquitectura** en **ARM 64**
4.  Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5.  Establezca **Build Type** (Tipo de compilación) en **D3D**.
6.  Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)
7.  Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

Después de configurar la plataforma, debe hacer [](../../../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.

> [!CAUTION]
> El XR heredado está en desuso en Unity 2019 y se ha quitado en Unity 2020.

1. Abra **Configuración del reproductor...** desde la **configuración de compilación... ventana** y expanda el **grupo XR Settings (Configuración de XR).**
2. En la **sección Configuración de XR,** seleccione **Virtual Reality Supported (Virtual Reality compatible)** para agregar la lista Dispositivos de realidad virtual.
3. Establezca **Depth Format (Formato de** profundidad) en Profundidad de **16 bits** y habilite Depth Buffer Sharing (Uso compartido del búfer de **profundidad).**
4. Establecer **el modo de representación estéreo** en Instancia de paso **único**
5. Seleccione **WSA Holographic Remoting Supported** (Comunicación remota holográfica de WSA compatible) si quiere usar la comunicación remota holográfica. 

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la sección Configuración del reproductor resaltada](../../images/wmr-config-img-9.png)