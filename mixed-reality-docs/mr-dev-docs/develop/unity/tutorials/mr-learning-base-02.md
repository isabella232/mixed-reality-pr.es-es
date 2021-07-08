---
title: Inicialización de su proyecto e implementación de su primera aplicación
description: En este curso se muestra cómo configurar un proyecto de Unity para Mixed Reality Toolkit (MRTK) y cómo implementarlo en HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175840"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inicialización de su proyecto e implementación de su primera aplicación

En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con Mixed Reality Toolkit (MRTK) e importar MRTK. También le guiará a través de la configuración, la compilación y la implementación de una escena básica de Unity desde Visual Studio a HoloLens 2. Una vez que la haya implementado en HoloLens 2, debería ver una malla de asignación espacial que cubre las superficies que HoloLens percibe. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.

## <a name="objectives"></a>Objetivos

* Aprender a configurar Unity para el desarrollo de HoloLens
* Aprender a compilar e implementar la aplicación en HoloLens
* Ver la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas en un dispositivo HoloLens 2

### <a name="steps-overview"></a>Descripción general de los pasos
:::row:::
    :::column:::
       ![Descripción general del paso 1](images/mr-learning-base/base-02-overview-step1.png) **1. Crear un proyecto de Unity**
    :::column-end:::
    :::column:::
       ![Descripción general del paso 2](images/mr-learning-base/base-02-overview-step2.png) **2. Importar MRTK en el proyecto**
    :::column-end:::
    :::column:::
       ![Descripción general del paso 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configurar una nueva escena con MRTK**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![Descripción general del paso 4](images/mr-learning-base/base-02-overview-step4.png) **4. Compilar el proyecto de Unity**
    :::column-end:::
    :::column:::
       ![Descripción general del paso 5](images/mr-learning-base/base-02-overview-step5.png) **5. Compilar el proyecto para UWP**
    :::column-end:::
    :::column:::
       ![Descripción general del paso 6](images/mr-learning-base/base-02-overview-step6.png) **6. Ejecutar el proyecto en el dispositivo**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>Creación del proyecto de Unity

Inicia **Unity Hub**, selecciona la pestaña **Projects** (Proyectos) y haz clic en la **flecha hacia abajo** situada junto al botón **New** (Nuevo):

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

En el desplegable, seleccione la **versión** de Unity especificada en los [Requisitos previos](mr-learning-base-01.md#prerequisites):

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> Si la versión de Unity determinada no está disponible en Unity Hub, puede iniciar la instalación desde el <a href="https://unity3d.com/get-unity/download/archive" target="_blank">archivo de descarga</a> de Unity.

En la ventana Create a new project (Crear un proyecto nuevo):

* Asegúrate de que la opción **Templates** (Plantillas) está establecida como **3D**.
* Escribe un **nombre de proyecto** adecuado, por ejemplo, _Tutoriales MRTK_
* Elige una **ubicación** adecuada para almacenar el proyecto, por ejemplo, _D:\MixedRealityLearning_.
* Haz clic en el botón **Create** (Crear) para crear e iniciar el nuevo proyecto de Unity.

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres. Por lo tanto, debe guardar el proyecto de Unity cerca de la raíz de la unidad.

Espera a que Unity cree el proyecto:

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>Cambio de la plataforma de compilación

En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](images/mr-learning-base/base-02-section2-step1-1.png)

En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y:

1. Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
2. Establezca la **arquitectura** en **ARM 64** 
3. Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).
4. Establezca la **versión del SDK de destino** en **Instalada la más reciente**.
5. Establezca **Minimum Platform Version** (Versión mínima de la plataforma) en **10.0.1024.0**.
6. Establezca la **versión de Visual Studio**  en **Instalada la más reciente**.
7. Establezca **Compilar y ejecutar en** en **Dispositivo USB**.
8. Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).
9. Haga clic en el botón Switch Platform (Cambiar plataforma).

![Configuración de compilación de Unity con la configuración establecida para Plataforma universal de Windows](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

Espera a que Unity termine de cambiar la plataforma:

![Cambio de plataforma de Unity en curso](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

Cuando Unity haya terminado de cambiar la plataforma, haga clic en el icono con la **x** para cerrar la ventana Build Settings (Configuración de compilación).

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>Importación de Mixed Reality Toolkit y configuración del proyecto de Unity

Para importar Mixed Reality Toolkit en el proyecto de Unity, habrá que usar la herramienta [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md), que permite a los desarrolladores detectar, actualizar y agregar paquetes de características de Mixed Reality a proyectos de Unity. Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación.

Descargue la versión más reciente de la herramienta Mixed Reality Feature Tool del [Centro de descarga de Microsoft](https://aka.ms/MRFeatureTool). Cuando finalice la descarga, descomprima el archivo y guárdelo en el escritorio.

> [!NOTE]
> Para que pueda ejecutar la herramienta, instale el [entorno de ejecución de .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)

Abra el archivo ejecutable, **MixedRealityFeatureTool**, que se encuentra en la carpeta descargada, para iniciar la herramienta Mixed Reality Feature Tool.  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Creación de la escena y configuración de MRTK

En el menú de Unity, seleccione **File** > **New Scene** (Nuevo > Nueva escena):

![Ruta del menú New Scene (Nueva escena) de Unity](images/mr-learning-base/base-02-section6-step1-1.png)

En la ventana **New Scene** (Nueva escena), seleccione **Basic (Built-in)** (Básico [integrado]) y haga clic en **Create** (Crear) para crear una escena:

![Ventana New Scene de Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> La captura de pantalla anterior corresponde a Unity 2020, si usa Unity 2019, al hacer clic en **Create** (Crear), se creará una nueva escena vacía.

En el menú de Unity, seleccione **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** (Realidad mixta > Kit de herramientas > Agregar a escena y configurar...) para agregar MRTK a la escena actual:

![Ruta del menú Add to Scene and Configure… (Agregar a escena y configurar…) de Unity](images/mr-learning-base/base-02-section6-step1-2.png)

Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, compruebe que el perfil de configuración **MixedRealityToolkit** se haya definido como **DefaultMixedRealityToolkitConfigurationProfile**:

![Componente MixedRealityToolkit de Unity con DefaultMixedRealityTookitConfigurationProfile seleccionado](images/mr-learning-base/base-02-section6-step1-3.png)

En el menú de Unity, selecciona **File** > **Save As...** (Archivo > Guardar como...) para abrir la ventana Save Scene (Guardar escena):

![Ruta del menú Save As… (Guardar como…) de Unity](images/mr-learning-base/base-02-section6-step1-4.png)

Guarde la escena en el proyecto en **Asset** > **Scenes** (Recurso > Escenas).

![Ventana de solicitud Save Scene (Guardar escena) de Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>Adición de la interacción de la mano a un objeto

En el menú de Unity, seleccione **GameObject** > **3D Object** > **Cube** (GameObject > Objeto 3D > Cubo) para agregar un objeto de cubo a la escena.

![Adición de un objeto Cube a la escena](images/mr-learning-base/base-02-section8-step1-1.png)

Haga clic en el objeto **Cube** (Cubo) en la ventana Hierarchy (Jerarquía) y, en la ventana Inspector, configure su componente **Transform** (Transformación) como se muestra a continuación.

* **Posición**: X = 0, Y = 0.1, Z = 0.5
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala**: X = 0.1, Y = 0.1, Z = 0.1

1 unidad de Unity es 1 metro. Hemos actualizado el tamaño del cubo a 10×10×10 cm, situado a 50 cm de la posición del casco (0,0,0), 10 cm por debajo del nivel de los ojos para una interacción cómoda. 

Si usa la escala predeterminada (1,1,1), el cubo será demasiado grande. Si usa la posición predeterminada (0,0,0), el cubo se colocará en la misma posición que el casco, y no podrá verlo hasta que no retroceda.

![Ajuste de la información de transformación](images/mr-learning-base/base-02-section8-step1-1b.png)

Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **Cube** (Cubo) y, a continuación, volver a acercarse ligeramente. O bien, puede usar la tecla F para acercar y centrar el objeto.

Para interactuar y agarrar un objeto con seguimiento de manos, el objeto debe tener:
 * Componente de colisionador, como **Box Collider** (Colisionador de cuadro) (el cubo de Unity ya tiene un colisionador de cuadro de manera predeterminada)
 * Componente **Object Manipulator (Script)** (Manipulador de objetos [script])
 * Componente **NearInteractionGrabbable(Script)**

El script **ObjectManipulator** de MRTK hace que un objeto se pueda mover, escalar y girar con una mano o las dos. Este script es compatible con el modelo de entrada de manipulación directa, porque permite al usuario tocar los hologramas directamente con las manos.

Con el objeto **Cube** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, haga clic en el botón **Add Component** (Agregar componente) y busque y seleccione el script **Object Manipulator** (Manipulador de objetos) para agregar el script correspondiente al objeto Cube.

![Adición de Object Manipulator (Manipulador de objetos) al objeto Cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

Repita el mismo procedimiento para agregar un **script Near Interaction Grabbable** (Interacción próxima de agarre) al objeto Cube

![Adición de Near Interaction Grabbable (Interacción próxima de agarre) al objeto Cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> Cuando se agrega un manipulador de objetos (script), en este caso, se agrega automáticamente el administrador de restricciones (script) porque el manipulador de objetos (script) depende de él.

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>Prueba de la aplicación en el editor de Unity con la simulación de entrada de MRTK

Con la simulación de entrada de MRTK, puede probar varios tipos de interacción en el editor de Unity sin necesidad de compilar ni implementar en un dispositivo. Esto le permite iterar rápidamente las ideas en el proceso de diseño y desarrollo. Use combinaciones de teclado y mouse para controlar las entradas simuladas.

Haga clic en el botón de reproducción e ingrese al modo de reproducción. Mantenga presionada la tecla **Mayús izquierda** o la **barra espaciadora** para abrir el controlador (manos simuladas), el mouse moverá el controlador, que también se puede alejar o acercar de la cámara mediante la rueda del mouse. Una vez que el puntero esté en el objeto Cube (Cubo), mantenga presionado el **botón izquierdo del mouse** para agarrar el objeto Cube.

* Presiona las teclas **W, A, S, D, Q, E** para mover la cámara.
* Mantenga presionado el **botón derecho del mouse** y muévalo para mirar alrededor.
* Para abrir las manos simuladas, presione la **barra espaciadora (mano derecha)** o la **tecla Mayús izquierda (mano izquierda)** .
* Para mantener las manos simuladas en la vista, presione las teclas **T** o **Y**.
* Para girar las manos simuladas, mantenga presionada la tecla **CTRL** y mueva el mouse.

![Modo Juego](images/mr-learning-base/base-02-section8-step1-4.gif)


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
>Es posible que vea el generador de perfiles de diagnóstico en la aplicación, que puede activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico). Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento. Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Enhorabuena

Ya ha implementado su primera aplicación de HoloLens 2. Una vez que se abra la aplicación, el usuario debería ver un objeto Cube delante suyo e interactuar con él moviéndolo y, además, a medida que avance, aparecerá una malla de asignación espacial que cubre las superficies que percibe HoloLens. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación. Estas características son solo algunas partes fundamentales incluidas en MRTK. En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 3. Configuración de los perfiles de MRTK](mr-learning-base-03.md)
