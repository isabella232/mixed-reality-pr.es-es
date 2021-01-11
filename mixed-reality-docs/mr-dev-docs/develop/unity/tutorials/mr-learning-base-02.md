---
title: Tutoriales de MRTK - 2. Inicialización de su proyecto e implementación de su primera aplicación
description: En este curso se muestra cómo configurar un proyecto de Unity para Mixed Reality Toolkit (MRTK) y cómo implementarlo en HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859534"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inicialización de su proyecto e implementación de su primera aplicación

## <a name="overview"></a>Introducción

En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e importar MRTK. También le guiará a través de la configuración, la compilación y la implementación de una escena básica de Unity desde Visual Studio a HoloLens 2. Una vez que la haya implementado en HoloLens 2, debería ver una malla de asignación espacial que cubre las superficies que HoloLens percibe. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.

## <a name="objectives"></a>Objetivos

* Aprender a configurar Unity para el desarrollo de HoloLens.
* Aprender a compilar e implementar la aplicación en HoloLens.
* Ver la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas en un dispositivo HoloLens 2.

## <a name="creating-the-unity-project"></a>Creación del proyecto de Unity

1. Inicie **Unity Hub**, seleccione la pestaña **Proyectos** y haga clic en la **flecha hacia abajo** situada junto al botón **Nuevo**:

![Unity Hub con la flecha hacia abajo del botón "Nuevo" resaltada.](images/mr-learning-base/base-02-section1-step1-1.png)

2. En el menú desplegable, seleccione la versión de Unity especificada en los [Requisitos previos](mr-learning-base-01.md#prerequisites):

![Selección de la versión de Unity.](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Si la versión de Unity determinada no está disponible en Unity Hub, puede iniciar la instalación desde el <a href="https://unity3d.com/get-unity/download/archive" target="_blank">archivo de descarga</a> de Unity.

3. En la ventana **Crear un proyecto nuevo**, haga lo siguiente:

    * Asegúrese de que la opción **Plantillas** está establecida como **3D**.
    * En el cuadro **Nombre del proyecto**, escriba un nombre adecuado para el proyecto (por ejemplo, "Tutoriales MRTK").
    * Haga clic en el botón de tres puntos situado junto a **Ubicación** y, a continuación, vaya a la carpeta en la que quiera guardar el proyecto.

> [!CAUTION]
> Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres. Por lo tanto, debe guardar el proyecto de Unity cerca de la raíz de la unidad.

    * Haga clic en el botón **Crear**. Esta opción crea e inicia el nuevo proyecto de Unity.

![Unity Hub con la ventana para crear un nuevo proyecto rellena.](images/mr-learning-base/base-02-section1-step1-3.png)

La barra de estado le mantiene al tanto del progreso realizado.

![La barra de progreso de Unity le mantiene al tanto del estado de "creación del proyecto".](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Cambio de la plataforma de compilación

1. En la barra del menú, seleccione **Archivo** > **Configuración de compilación...** .

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](images/mr-learning-base/base-02-section2-step1-1.png)

2. En la ventana de **Configuración de compilación**, seleccione **Plataforma universal de Windows** y haga clic en el botón **Cambiar plataforma**:

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado para cambiar de plataforma desde Standalone (Independiente)](images/mr-learning-base/base-02-section2-step1-2.png)

3. Espere a que Unity termine de cambiar la plataforma y, a continuación, cierre la ventana **Configuración de compilación**.

## <a name="importing-the-textmeshpro-essential-resources"></a>Importación de los recursos esenciales de TextMeshPro

Los elementos de la interfaz de usuario de MRTK requieren los recursos esenciales de TextMeshPro. Si no va a usar los elementos de la interfaz de usuario de MRTK en el proyecto, puede omitir este paso.

1. En la barra del menú, seleccione **Ventana**  > **TextMeshPro** > **Import TMP Essential Resources** (Importar recursos esenciales de TMP).

![Ruta de menú Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-1.png)

2. En la ventana **Import Unity Package** (Importar paquete de Unity), haga clic en el botón **Todos** para asegurarse de que todos los recursos están seleccionados y, a continuación, haga clic en el botón **Importar** para importar los recursos:

![Ventana Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

1. Descarga el paquete personalizado de Unity:

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. En la barra del menú, seleccione **Recursos** > **Paquete de importación** > **Paquete personalizado...** .
3. En el cuadro de diálogo **Importar paquete...** , vaya a la ubicación del paquete que acaba de descargar, selecciónelo y, a continuación, haga clic en el botón **Abrir**.
4. En la ventana **Import Unity Package** (Importar paquete de Unity), haga clic en el botón **Todos** para asegurarse de que todos los recursos están seleccionados y, a continuación, haga clic en el botón **Importar** para importar los recursos.

## <a name="selecting-mrtk-and-project-settings"></a>Selección de la configuración de MRTK y del proyecto

Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK). Si no aparece, puede abrirlo de forma manual seleccionando la opción **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity):

![Ruta del menú Configure Unity Project (Configurar proyecto de Unity) de Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. En la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK), expanda la sección **Modificar configuraciones** si fuera necesario, y asegúrese de que todas las demás opciones están seleccionadas.

![Ventana de Configurador del proyecto de MRTK con la opción Modificar configuraciones a la vista.](images/mr-learning-base/base-02-section5-step1-2.png)

2. Para aplicar la configuración, haga clic en el botón **Aplicar**.

![Botón "Aplicar" en MRTK.](images/mr-learning-base/apply.png)

> [!NOTE]
> Está usando la versión de XR heredada integrada de Unity en lugar del nuevo sistema de complementos de XR, ya que el nuevo sistema no es totalmente compatible con las [versiones recomendadas de Unity y MRTK](mr-learning-base-01.md#prerequisites) para esta serie de tutoriales. Si ve alguna advertencia acerca de que la versión de XR integrada está en desuso, puede omitirla.

> [!TIP]
> La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:
>
> * Enable legacy XR (Habilitar la versión de XR heredada): Habilita VR para el proyecto.
> * Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw. Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) (Rendimiento) de MRTK.
> * Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial. Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.

3. En la barra del menú, seleccione **Editar** > **Configuración del proyecto...** .

4. En la ventana **Configuración del proyecto**, seleccione **Reproductor**, haga clic en la lista desplegable **Configuración de XR** y, a continuación, active la casilla situada junto a **Virtual Reality Supported** (Compatibilidad con realidad virtual):

![Se muestra la Configuración de XR de Unity con la opción de compatibilidad con realidad virtual.](images/mr-learning-base/base-02-section5-step2-2.png)

Esta opción importa el SDK de Windows Mixed Reality:

![Se muestra la Configuración de XR de Unity con los SDK de realidad virtual.](images/mr-learning-base/mixed-reality-sdk.png)

Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK). Si no aparece, puede abrirla mediante la opción **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Kit de herramientas de Mixed Reality > Utilidades > Configurar proyecto de Unity).

5. En la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK), haga clic en la lista desplegable **Audio spatializer** (Espacializador de audio) y, a continuación, seleccione **MS HRTF Spatializer** (Espacializador MS HRTF).

![Configuración del proyecto con las opciones del Espacializador de audio a la vista.](images/mr-learning-base/base-02-section5-step2-3.png)

6. Haga clic en el botón **Aplicar**. Esta opción cierra la ventana de **MRTK Project Configurator** (Configurador del proyecto MRTK).

    > [!TIP]
    > La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto. Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada. Para obtener más información sobre este tema, puede consultar los tutoriales de audio espacial.

7. En la ventana **Configuración del proyecto**, haga clic en la lista desplegable **Depth Format** (Formato de profundidad) y, a continuación, seleccione **Profundidad de 16 bits**:

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Configuración de XR de Unity con profundidad de 16 bits seleccionada.":::

    > [!TIP]
    > Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudarle a mejorar el rendimiento de los gráficos en el proyecto. Para obtener más información sobre este tema, puede consultar la sección [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) (Uso compartido del búfer de profundidad [HoloLens]) de la documentación [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) (Rendimiento) de MRTK.

8. Haga clic en la lista desplegable **Publishing Settings** (Configuración de publicación) y, a continuación, en el cuadro **Nombre del paquete**, escriba un nombre adecuado (por ejemplo, "MRTK-Tutorials-Getting-Started").

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Configuración de publicación de Unity con el nombre del paquete configurado.":::

    **Nombre del paquete y nombre del producto**

    - "Package name" es el identificador único para la aplicación. Debe crear este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.
    - "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para que la búsqueda de la aplicación sea más fácil durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo en la parte superior.

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Configuración del proyecto de Unity con el nombre de producto configurado.":::

9. Cierre la ventana **Configuración del proyecto**.

## <a name="creating-and-configuring-the-scene"></a>Creación y configuración de la escena

1. En la barra del menú, haga clic en **Archivo** > **Importar**.
2. Para agregar MRTK a la escena, vaya a la barra del menú y seleccione **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Kit de herramientas de Mixed Reality > Agregar a la escena y configurar...).

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Ruta del menú &quot;Agregar a la escena y configurar…&quot; de Unity.":::

3. En la ventana **Jerarquía**, asegúrese de que el objeto **MixedRealityToolkit** esté seleccionado.

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Asegúrese de que MixedRealityTookit está seleccionado.":::

4. En la sección **MixedRealityToolkit** de la ventana **Inspector**, compruebe que el perfil de configuración está establecido en **DefaultMixedRealityToolkitConfigurationProfile**:

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Componente MixedRealityToolkit de Unity con DefaultMixedRealityTookitConfigurationProfile seleccionado.":::

    > [!IMPORTANT]
    > Normalmente, se usa el perfil DefaultHoloLens2ConfigurationProfile para desarrollar para HoloLens. Sin embargo, en este tutorial usará DefaultMixedRealityToolkitConfigurationProfile. En el siguiente tutorial, [Configuración de los perfiles de MRTK](mr-learning-base-03.md), cambiará al perfil DefaultHoloLens2ConfigurationProfile.

5. En la barra del menú, haga clic en **Archivo** > **Guardar como...** .
6. En el cuadro de diálogo **Guardar escena**, vaya a la carpeta **Escenas** del proyecto. En el cuadro **Nombre de archivo**, escriba un nombre adecuado para la escena (por ejemplo, "\_GettingStarted\_") y, a continuación, haga clic en el botón **Guardar**.

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Ventana de solicitud para Guardar la escena de Unity.":::

## <a name="building-and-deploying-to-your-hololens-2"></a>Creación e implementación en HoloLens 2

> Antes de compilar contenido en el dispositivo, confirme lo siguiente:
- El dispositivo está en modo de desarrollador.
- El dispositivo está emparejado con el equipo de desarrollo. Si no es así, verá el cuadro de diálogo siguiente en Visual Studio durante el proceso de compilación:

![Entrada de PIN para el emparejamiento de dispositivos](images/mr-learning-base/pin-request.png)

 Para obtener más información sobre estos dos pasos, consulte [Uso de Visual Studio para implementar y depurar](../../platform-capabilities-and-apis/using-visual-studio.md).

1. En la barra del menú, seleccione **Archivo** > **Configuración de compilación...** .
2. En la ventana **Configuración de compilación**, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación).

![Agregar la escena actual a la lista "Escenas en la compilación".](images/mr-learning-base/base-02-section7-step1-1.png)

3. Haga clic en el botón **Build** (Compilación).

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Haga clic en el botón Build (Compilación).":::

4. En el cuadro de diálogo **Build Universal Windows Platform** (Compilar Plataforma universal de Windows), elija una ubicación adecuada para guardar la compilación (por ejemplo, puede crear una carpeta denominada "Compilaciones" en la carpeta "Tutoriales de MRTK"). Cree una nueva carpeta y asígnele un nombre adecuado (por ejemplo, "GettingStarted"), seleccione la carpeta y, a continuación, haga clic en el botón **Seleccionar carpeta** para iniciar el proceso de compilación.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Ventana de compilación de Unity con la carpeta de compilación a la vista.":::

    Aparecerá una barra de estado que le indicará el progreso de la compilación.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Proceso de compilación de Unity en curso.":::

    > [!TIP]
    > También puede realizar la implementación en el [emulador de HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o crear un [paquete de aplicación](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para la instalación de prueba.

5. Cuando se haya completado el proceso de compilación, use el Explorador de archivos para obtener la ubicación donde almacenó la compilación y, a continuación, haga doble clic en el archivo de solución para abrirlo en Visual Studio:

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Explorador de Windows con la solución de Visual Studio recién creada seleccionada.":::

    > [!NOTE]
    > Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que tiene todos los componentes de requisitos previos de la documentación **[Instalación de herramientas](../../install-the-tools.md)** .

6. Para configurar Visual Studio para HoloLens, seleccione la configuración **Master** o **Publicación**, la arquitectura **ARM64** y la opción **Dispositivo** como destino.

    > [!TIP]
    > Si va a realizar la implementación en HoloLens (1ª. generación), seleccione la arquitectura **x86**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio configurado para implementar en HoloLens 2.":::

    > [!NOTE]
    > En el caso de HoloLens, normalmente se compilará para la arquitectura ARM. Sin embargo, hay un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conocido</strong></a> en Unity 2019.3 que produce errores al seleccionar ARM como arquitectura de compilación en Visual Studio. La solución recomendada es compilar para ARM64. Si no es una opción, vaya a **Edit > Project Settings > Player > Other Settings** (Editar > Configuración del proyecto > Reproductor > Otras opciones) y deshabilite **Graphics Jobs** (Trabajos de gráficos).

    > [!NOTE]
    > Si no ve Dispositivo como opción de destino, es posible que deba cambiar el proyecto de inicio de la solución de Visual Studio del proyecto de IL2CPP al proyecto de UWP. Para ello, en el Explorador de soluciones, haga clic con el botón derecho en el nombre del proyecto (Windows Universal) y seleccione **Establecer como proyecto de inicio**.

7. Conecte el dispositivo HoloLens al equipo y, a continuación, realice una de las acciones siguientes:
- Para compilar la aplicación, impleméntela en HoloLens e iníciela automáticamente sin adjuntar el depurador de Visual Studio; en la barra del menú, seleccione **Depurar** > **Iniciar sin depurar**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Ruta del menú Iniciar sin depurar de Visual Studio.":::

- Si quiere compilar e implementar la aplicación en HoloLens, pero no que se inicie automáticamente, en la barra del menú, seleccione **Compilar > Implementar la solución**.

    > [!NOTE]
    >Es posible que veas el generador de perfiles de diagnóstico en la aplicación, que puedes activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico). Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento. Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Enhorabuena

Ya ha implementado su primera aplicación de HoloLens 2. A medida que avance, debería ver una malla de asignación espacial que cubre todas las superficies que HoloLens ha percibido. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación. Estas características son solo algunas partes fundamentales incluidas en MRTK. En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 3. Configuración de los perfiles de MRTK](mr-learning-base-03.md)
