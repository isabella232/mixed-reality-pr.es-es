---
title: Inicialización de su proyecto e implementación de su primera aplicación
description: En este curso se muestra cómo configurar un proyecto de Unity para Mixed Reality Toolkit (MRTK) y cómo implementarlo en HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: b0b8d97471dfae9d6dc6bbee26079af04f97de62
ms.sourcegitcommit: 94ae851f78e5b861af601b445f8f0a3405197c40
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2021
ms.locfileid: "107716026"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inicialización de su proyecto e implementación de su primera aplicación

En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> e importar MRTK. También le guiará a través de la configuración, la compilación y la implementación de una escena básica de Unity desde Visual Studio a HoloLens 2. Una vez que la haya implementado en HoloLens 2, debería ver una malla de asignación espacial que cubre las superficies que HoloLens percibe. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

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

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a>Importación de los recursos esenciales de TextMeshPro

En el menú de Unity, seleccione **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Ventana > TextMeshPro > Importar recursos esenciales de TMP) para abrir la ventana Import Unity Package (Importar paquete de Unity):

![Ruta de menú Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-1.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![Ventana Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Los elementos de la interfaz de usuario de MRTK requieren los recursos esenciales de TextMeshPro. Puede omitir este paso si no va a usar los elementos de la interfaz de usuario de MRTK en el proyecto.

## <a name="importing-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

Para importar Mixed Reality Toolkit en el proyecto de Unity, habrá que usar la herramienta [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md), que permite a los desarrolladores detectar, actualizar y agregar paquetes de características de Mixed Reality a proyectos de Unity. Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación.

Descargue la versión más reciente de la herramienta Mixed Reality Feature Tool del [Centro de descarga de Microsoft](https://aka.ms/MRFeatureTool). Cuando finalice la descarga, descomprima el archivo y guárdelo en el escritorio.

> [!NOTE]
> Para que pueda ejecutar la herramienta, instale el [entorno de ejecución de .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)

> [!NOTE]
> La herramienta Mixed Reality Feature Tool solo se puede ejecutar en Windows. En el caso de MacOS, siga este [procedimiento](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) para descargar e importar Mixed Reality Toolkit en el proyecto de Unity.

Abra el archivo ejecutable, **MixedRealityFeatureTool**, que se encuentra en la carpeta descargada, para iniciar la herramienta Mixed Reality Feature Tool.  

![Abrir MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a>Configuración del proyecto de Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Aplicación de la configuración del configurador del proyecto de MRTK

Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no aparece, puede abrirlo de forma manual seleccionando la opción **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity):

![Ruta del menú Configure Unity Project (Configurar proyecto de Unity) de Unity](images/mr-learning-base/base-02-section5-step1-1.png)

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), expanda la sección **Modify Configurations (Modificar configuraciones)** , asegúrese de que todas las demás opciones están seleccionadas y haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:

> * Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw. Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Rendimiento) de MRTK.
> * Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial. Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.

### <a name="2-configure-additional-project-settings"></a>2. Configuración de valores adicionales del proyecto

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Creación de la escena y configuración de MRTK

En el menú de Unity, seleccione **File** > **New Scene** (Archivo > Nueva escena) para crear una nueva escena:

![Ruta del menú New Scene (Nueva escena) de Unity](images/mr-learning-base/base-02-section6-step1-1.png)

En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Agregar a escena y configurar...) para agregar MRTK a la escena actual:

![Ruta del menú Add to Scene and Configure… (Agregar a escena y configurar…) de Unity](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

En el menú de Unity, selecciona **File** > **Save As...** (Archivo > Guardar como...) para abrir la ventana Save Scene (Guardar escena):

![Ruta del menú Save As… (Guardar como…) de Unity](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudarle a mejorar el rendimiento de los gráficos en el proyecto. Para obtener más información sobre este tema, puede consultar la sección <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Performance</a> (Rendimiento) de MRTK.

![Ventana de solicitud Save Scene (Guardar escena) de Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descargue el siguiente paquete personalizado de Unity:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

Para importar un paquete personalizado de Unity, seleccione **Assets** > **Import Package** > **Custom Package...** (Recursos > Importar paquete > Paquete personalizado...) para abrir la ventana Import package... (Importar paquete...):

![Importación de un paquete personalizado](images/mr-learning-base/base-02-section7-step1-1.png)

En la ventana Import package... (Importar paquete...), seleccione el paquete **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** que ha descargado y haga clic en el botón Open (Abrir):

![Selección de un paquete de recursos](images/mr-learning-base/base-02-section7-step1-2.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón All (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón Import (Importar) para importar los recursos:

![Selección de todos los recursos que se van a importar](images/mr-learning-base/base-02-section7-step1-3.png)

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![Ventana de proyecto de Unity después de importar recursos](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a>Configuración de la escena

En la ventana Project (Proyecto), vaya a la carpeta Assets > MRTK.Tutorials.GettingStarted > Prefabs:

En la ventana Project (Proyecto), haga clic y arrastre el recurso prefabricado **Cube** a la ventana Hierarchy (Jerarquía). Después, en la ventana Inspector configure su componente **Transform** (Transformación) como se indica a continuación

* **Posición**: X = 0, Y = 0, Z = 0,5
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Adición de un objeto Cube a la escena](images/mr-learning-base/base-02-section8-step1-1.png)

Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **Cube** y, a continuación, volver a acercarse ligeramente:

Para interactuar y agarrar un objeto para que siga las manos, el objeto debe tener un componente Collider (Colisionador), por ejemplo un **Box Collider** (Colisionador de cuadro), un componente **Object Manipulator (Script)** (Manipulador de objetos) y un componente **NearInteractionGrabbable (Script)** .

Con el objeto **Cube** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, haga clic en el botón **Add Component** (Agregar componente) y busque y seleccione el script **Object Manipulator** (Manipulador de objetos) para agregar el script correspondiente al objeto Cube.

![Adición de Object Manipulator (Manipulador de objetos) al objeto Cube](images/mr-learning-base/base-02-section8-step1-2.png)

Repita el mismo procedimiento para agregar un **script Near Interaction Grabbable** (Interacción próxima de agarre) al objeto Cube

![Adición de Near Interaction Grabbable (Interacción próxima de agarre) al objeto Cube](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> Cuando se agrega un manipulador de objetos (script), en este caso, se agrega automáticamente el administrador de restricciones (script) porque el manipulador de objetos (script) depende de él.

> [!NOTE]
> Para los fines de este tutorial, los colisionadores ya se han agregado al objeto Cube. Para obtener más información sobre los colisionadores, visita la documentación sobre <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">colisionadores</a> de Unity.

Para probar esto en el editor de Unity, puede entrar en el modo de reproducción y mantener presionada la tecla **Mayús Izq** o **Espacio** para habilitar el controlador. El movimiento del mouse moverá el controlador y también este se puede alejar o acercar con respecto a la cámara con la rueda del mouse. Una vez que el puntero esté en el objeto Cube, mantenga presionado el **botón primario del mouse** para desplazarlo.

![Modo Juego](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a>Compilación de la aplicación a HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Compilar el proyecto de Unity

En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).

En la ventana Build Settings (Configuración de compilación), haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación) y, a continuación, haz clic en el botón **Build** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows):

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado](images/mr-learning-base/base-02-section9-step1-1.png)

En la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows), elige una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, crea una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _Introducción_, y haz clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](images/mr-learning-base/base-02-section9-step1-2.png)

Espera a que Unity finalice el proceso de compilación:

![Proceso de compilación de Unity en curso](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilar e implementar la aplicación

Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación. Navega dentro de la carpeta y haz doble clic en el archivo de solución para abrirlo en Visual Studio:

![Explorador de Windows con la solución de Visual Studio recién creada seleccionada](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que tiene todos los componentes de requisitos previos de la documentación **[Instalación de herramientas](../../install-the-tools.md)** .

Configure Visual Studio para HoloLens 2. Para ello, selecciona la configuración **Maestro** o **Publicación**, la arquitectura **ARM64** y la opción **Dispositivo** como destino:

![Visual Studio configurado para implementar en HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> Si va a realizar la implementación en HoloLens (1ª. generación), seleccione la arquitectura **x86**.

> [!NOTE]
> En el caso de HoloLens, normalmente se compilará para la arquitectura ARM. Sin embargo, hay un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conocido</strong></a> en Unity 2019.3 que produce errores al seleccionar ARM como arquitectura de compilación en Visual Studio. La solución recomendada es compilar para ARM64. Si no es una opción, vaya a **Edit > Project Settings > Player > Other Settings** (Editar > Configuración del proyecto > Reproductor > Otras opciones) y deshabilite **Graphics Jobs** (Trabajos de gráficos).

> [!NOTE]
> Si no ve Dispositivo como opción de destino, es posible que deba cambiar el proyecto de inicio de la solución de Visual Studio del proyecto de IL2CPP al proyecto de UWP. Para ello, en el Explorador de soluciones, haga clic con el botón derecho en NombreDelProyecto (Windows Universal) y seleccione **Establecer como proyecto de inicio**.

Conecte su HoloLens al equipo y, a continuación, seleccione **Depurar** > **Iniciar sin depurar** para compilar e realizar la implementación en el dispositivo:

![Ruta del menú Iniciar sin depuración en Visual Studio](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en Modo de desarrollador y emparejado con el equipo de desarrollo. Ambos pasos pueden completarse siguiendo [estas instrucciones](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> También puede realizar la implementación en el [emulador de HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o crear un [paquete de aplicación](/windows/uwp/packaging/packaging-uwp-apps) para la instalación de prueba.

Al usar Iniciar sin depurar, la aplicación se inicia automáticamente en el dispositivo sin el depurador de Visual Studio adjunto.

Seleccione **Compilar > Implementar solución** para realizar una implementación en el dispositivo sin que se inicie automáticamente la aplicación.

> [!NOTE]
>Es posible que veas el generador de perfiles de diagnóstico en la aplicación, que puedes activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico). Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento. Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Enhorabuena

Ya ha implementado su primera aplicación de HoloLens 2. Una vez que se abra la aplicación, el usuario debería ver un objeto Cube delante suyo e interactuar con él moviéndolo y, además, a medida que avance, aparecerá una malla de asignación espacial que cubre las superficies que percibe HoloLens. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación. Estas características son solo algunas partes fundamentales incluidas en MRTK. En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 3. Configuración de los perfiles de MRTK](mr-learning-base-03.md)
