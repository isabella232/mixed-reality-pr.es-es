---
title: Inicialización de su proyecto e implementación de su primera aplicación
description: En este curso se muestra cómo configurar un proyecto de Unity para Mixed Reality Toolkit (MRTK) y cómo implementarlo en HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ff479df81316ab5ceeabf045ad1bbae007190ed4
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238149"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inicialización de su proyecto e implementación de su primera aplicación

En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e importar MRTK. También le guiará a través de la configuración, la compilación y la implementación de una escena básica de Unity desde Visual Studio a HoloLens 2. Una vez que la haya implementado en HoloLens 2, debería ver una malla de asignación espacial que cubre las superficies que HoloLens percibe. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.

## <a name="objectives"></a>Objetivos

* Aprender a configurar Unity para el desarrollo de HoloLens
* Aprender a compilar e implementar la aplicación en HoloLens
* Ver la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas en un dispositivo HoloLens 2

## <a name="creating-the-unity-project"></a>Creación del proyecto de Unity

Inicia **Unity Hub**, selecciona la pestaña **Projects** (Proyectos) y haz clic en la **flecha hacia abajo** situada junto al botón **New** (Nuevo):

![Unity Hub con el botón New (Nuevo) resaltado](images/mr-learning-base/base-02-section1-step1-1.png)

En el desplegable, seleccione la **versión** de Unity especificada en los [Requisitos previos](mr-learning-base-01.md#prerequisites):

![Unity Hub con lista desplegable del selector de la nueva versión](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Si la versión de Unity determinada no está disponible en Unity Hub, puede iniciar la instalación desde el <a href="https://unity3d.com/get-unity/download/archive" target="_blank">archivo de descarga</a> de Unity.

En la ventana Create a new project (Crear un proyecto nuevo):

* Asegúrate de que la opción **Templates** (Plantillas) está establecida como **3D**.
* Escribe un **nombre de proyecto** adecuado, por ejemplo, _Tutoriales MRTK_
* Elige una **ubicación** adecuada para almacenar el proyecto, por ejemplo, _D:\MixedRealityLearning_.
* Haz clic en el botón **Create** (Crear) para crear e iniciar el nuevo proyecto de Unity.

![Unity Hub con la ventana para crear un nuevo proyecto rellena](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres. Por lo tanto, debe guardar el proyecto de Unity cerca de la raíz de la unidad.

Espera a que Unity cree el proyecto:

![Creación de nuevo proyecto de Unity en curso](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Cambio de la plataforma de compilación

En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](images/mr-learning-base/base-02-section2-step1-1.png)

En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado para cambiar de plataforma desde Standalone (Independiente)](images/mr-learning-base/base-02-section2-step1-2.png)

Espera a que Unity termine de cambiar la plataforma:

![Cambio de plataforma de Unity en curso](images/mr-learning-base/base-02-section2-step1-3.png)

Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:

![Ventana Build (Compilación) de Unity con el icono de cerrar resaltado](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>Importación de los recursos esenciales de TextMeshPro

En el menú de Unity, seleccione **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Ventana > TextMeshPro > Importar recursos esenciales de TMP) para abrir la ventana Import Unity Package (Importar paquete de Unity):

![Ruta de menú Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-1.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![Ventana Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Los elementos de la interfaz de usuario de MRTK requieren los recursos esenciales de TextMeshPro. Puede omitir este paso si no va a usar los elementos de la interfaz de usuario de MRTK en el proyecto.

## <a name="importing-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

### <a name="using-the-mixed-reality-feature-tool"></a>Uso de la herramienta de características de Mixed Reality

Para instalar MRTK con la nueva herramienta de características de Mixed Reality, siga las [instrucciones de instalación y uso](../welcome-to-mr-feature-tool.md) y seleccione el paquete **Mixed Reality Toolkit Foundation** en la categoría de Mixed Reality Toolkit.

### <a name="using-unity-packages"></a>Uso de paquetes de Unity

Para instalar MRTK con un paquete personalizado, haga lo siguiente:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

En el menú de Unity, selecciona **Assets** > **Import Package** > **Custom Package...** (Recursos > Importar paquete > Paquete personalizado...) para abrir la ventana Import package... (Importar paquete...):

![Ruta de menú Import Custom Package… (Importar paquete personalizado…) de Unity](images/mr-learning-base/base-02-section4-step1-1.png)

En la ventana Import package... (Importar paquete...), seleccione el paquete **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** que descargó y haga clic en el botón **Open** (Abrir):

![Import Custom Package (Importar paquete personalizado) de Unity con la ventana de mensajes Open (Abrir)](images/mr-learning-base/base-02-section4-step1-2.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![Ventana de importación de Unity MRTK Foundation](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>Configuración del proyecto de Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Aplicación de la configuración del configurador del proyecto de MRTK

Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no aparece, puede abrirlo de forma manual seleccionando la opción **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity):

![Ruta del menú Configure Unity Project (Configurar proyecto de Unity) de Unity](images/mr-learning-base/base-02-section5-step1-1.png)

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), expanda la sección **Modify Configurations (Modificar configuraciones)** , asegúrese de que todas las demás opciones están seleccionadas y haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:

> * Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw. Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) (Rendimiento) de MRTK.
> * Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial. Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.

### <a name="2-configure-additional-project-settings"></a>2. Configuración de valores adicionales del proyecto

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:

![Ruta del menú Project Settings… (Configuración del proyecto…) de Unity](images/mr-learning-base/base-02-section5-step2-1.png)

En la ventana Configuración del proyecto, seleccione **XR Plug-in Management** > **Instalar XR Plug-in Management** para instalar XR Plug-in Management:

![Configuración del proyecto con XR Plugin Management seleccionado](images/mr-learning-base/base-02-section5-step2-2.png)

Después de que Unity haya terminado de instalar XR Plug-in Management. Asegúrese de estar en la configuración de la Plataforma universal de Windows y active Initialize XR on Startup (Inicializar XR al inicio).

![Configuración de XR Plug-in Management en Unity](images/mr-learning-base/base-02-section5-step2-3.png)

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR), haga clic en el icono **+** y seleccione Windows Mixed Reality para agregar el SDK de Windows Mixed Reality:

![XR Settings (Configuración de XR) de Unity con la opción para agregar el SDK de Windows Mixed Reality seleccionada](images/mr-learning-base/base-02-section5-step2-4.png)

Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no es así, use el menú de Unity para abrirla.

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![Ventana del configurador del proyecto MRTK con la propiedad Audio spatializer (Espacializador de audio) resaltada](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto. Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada. Para obtener más información sobre este tema, puede consultar los <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR) y, a continuación, use la lista desplegable **Depth Format** (Formato de profundidad) para seleccionar **16-bit depth** (Profundidad de 16 bits):

![Habilitar la profundidad 16 en Unity](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudar a mejorar el rendimiento de los gráficos en el proyecto. Para obtener más información sobre este tema, puede consultar la sección <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">Performance</a> (Rendimiento) de MRTK.

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:

![Publishing Settings (Configuración de publicación) de Unity con Package name (Nombre del paquete) configurado](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> "Package name" es el identificador único para la aplicación. Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.

> [!TIP]
> "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.

## <a name="creating-and-configuring-the-scene"></a>Creación y configuración de la escena

En el menú de Unity, seleccione **File** > **New Scene** (Archivo > Nueva escena) para crear una nueva escena:

![Ruta del menú New Scene (Nueva escena) de Unity](images/mr-learning-base/base-02-section6-step1-1.png)

En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Agregar a escena y configurar...) para agregar MRTK a la escena actual:

![Ruta del menú Add to Scene and Configure… (Agregar a escena y configurar…) de Unity](images/mr-learning-base/base-02-section6-step1-2.png)

Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, compruebe que el perfil de configuración **MixedRealityToolkit** se haya definido como **DefaultMixedRealityToolkitConfigurationProfile**:

![Componente MixedRealityToolkit de Unity con DefaultMixedRealityTookitConfigurationProfile seleccionado](images/mr-learning-base/base-02-section6-step1-3.png)

En el menú de Unity, selecciona **File** > **Save As...** (Archivo > Guardar como...) para abrir la ventana Save Scene (Guardar escena):

![Ruta del menú Save As… (Guardar como…) de Unity](images/mr-learning-base/base-02-section6-step1-4.png)

En la ventana Save Scene (Guardar escena), desplázate hasta la carpeta **Scenes** (Escenas) del proyecto, asígnale un nombre adecuado (por ejemplo, _GettingStarted_), y haz clic en el botón **Save** (Guardar) para guardar la escena:

![Ventana de solicitud Save Scene (Guardar escena) de Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>Compilación de la aplicación a HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Compilar el proyecto de Unity

En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).

En la ventana Build Settings (Configuración de compilación), haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación) y, a continuación, haz clic en el botón **Build** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows):

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado](images/mr-learning-base/base-02-section7-step1-1.png)

En la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows), elige una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, crea una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _Introducción_, y haz clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](images/mr-learning-base/base-02-section7-step1-2.png)

Espera a que Unity finalice el proceso de compilación:

![Proceso de compilación de Unity en curso](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilar e implementar la aplicación

Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación. Navega dentro de la carpeta y haz doble clic en el archivo de solución para abrirlo en Visual Studio:

![Explorador de Windows con la solución de Visual Studio recién creada seleccionada](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que tiene todos los componentes de requisitos previos de la documentación **[Instalación de herramientas](../../install-the-tools.md)** .

Configure Visual Studio para HoloLens 2. Para ello, selecciona la configuración **Maestro** o **Publicación**, la arquitectura **ARM64** y la opción **Dispositivo** como destino:

![Visual Studio configurado para implementar en HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> Si va a realizar la implementación en HoloLens (1ª. generación), seleccione la arquitectura **x86**.

> [!NOTE]
> En el caso de HoloLens, normalmente se compilará para la arquitectura ARM. Sin embargo, hay un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conocido</strong></a> en Unity 2019.3 que produce errores al seleccionar ARM como arquitectura de compilación en Visual Studio. La solución recomendada es compilar para ARM64. Si no es una opción, vaya a **Edit > Project Settings > Player > Other Settings** (Editar > Configuración del proyecto > Reproductor > Otras opciones) y deshabilite **Graphics Jobs** (Trabajos de gráficos).

> [!NOTE]
> Si no ve Dispositivo como opción de destino, es posible que deba cambiar el proyecto de inicio de la solución de Visual Studio del proyecto de IL2CPP al proyecto de UWP. Para ello, en el Explorador de soluciones, haga clic con el botón derecho en NombreDelProyecto (Windows Universal) y seleccione **Establecer como proyecto de inicio**.

Conecte su HoloLens al equipo y, a continuación, seleccione **Depurar** > **Iniciar sin depurar** para compilar e realizar la implementación en el dispositivo:

![Ruta del menú Iniciar sin depuración en Visual Studio](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en Modo de desarrollador y emparejado con el equipo de desarrollo. Ambos pasos pueden completarse siguiendo [estas instrucciones](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> También puede realizar la implementación en el [emulador de HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o crear un [paquete de aplicación](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para la instalación de prueba.

Al usar Iniciar sin depurar, la aplicación se inicia automáticamente en el dispositivo sin el depurador de Visual Studio adjunto.

Seleccione **Compilar > Implementar solución** para realizar una implementación en el dispositivo sin que se inicie automáticamente la aplicación.

> [!NOTE]
>Es posible que veas el generador de perfiles de diagnóstico en la aplicación, que puedes activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico). Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento. Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Enhorabuena

Ya ha implementado su primera aplicación de HoloLens 2. A medida que avance, debería ver una malla de asignación espacial que cubre todas las superficies que HoloLens ha percibido. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación. Estas características son solo algunas partes fundamentales incluidas en MRTK. En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 3. Configuración de los perfiles de MRTK](mr-learning-base-03.md)