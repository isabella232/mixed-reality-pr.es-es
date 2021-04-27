---
ms.openlocfilehash: d8d46da1a1a095074f059b53ebd997e1b6f89961
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984266"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento XR para Unity 2019/2020 y Windows](#tab/winxr)

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:

![Ruta del menú Project Settings… (Configuración del proyecto…) de Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

En la ventana Configuración del proyecto, seleccione **XR Plug-in Management** > **Instalar XR Plug-in Management** para instalar XR Plug-in Management:

![Configuración de XR de Unity](../images/mr-learning-base/base-02-section5-step2-2.png)

Después de que Unity haya terminado de instalar XR Plug-in Management. Asegúrese de estar en la configuración de la Plataforma universal de Windows y de activar las casillas **Initialize XR on Startup** (Inicializar XR al inicio) y **Windows Mixed Reality**.

![XR Settings (Configuración de XR) de Unity con la opción para agregar el SDK de Windows Mixed Reality](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no es así, use el menú de Unity para abrirla.

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![XR Settings (Configuración de XR) de Unity con la opción del SDK de Windows Mixed Reality seleccionada](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto. Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada. Para obtener más información sobre este tema, puede consultar los <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.

En la ventana Project Settings (Configuración del proyecto), seleccione **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings** (Configuración del entorno de ejecución) y, a continuación, use el menú desplegable **Depth Buffer Format** (Formato de profundidad del búfer) para seleccionar **16-bit depth** (Profundidad de 16 bits):

![Configuración de publicación de Unity con el nombre del paquete resaltado](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudar a mejorar el rendimiento de los gráficos en el proyecto. Para obtener más información sobre este tema, puede consultar la sección <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">Performance</a> (Rendimiento) de MRTK.

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:

![Configuración de publicación de Unity con el nombre del paquete](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> "Package name" es el identificador único para la aplicación. Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.

> [!TIP]
> "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:

![Ruta del menú Project Settings… (Configuración del proyecto…) de Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

En la ventana Configuración del proyecto, seleccione **XR Plug-in Management** > **Instalar XR Plug-in Management** para instalar XR Plug-in Management:

![Configuración de XR de Unity con la opción Install XR plug-in management (Instalar XR Plug-in Management) seleccionada](../images/mr-learning-base/base-02-section5-step2-2.png)

Después de que Unity haya terminado de instalar XR Plug-in Management. Asegúrese de estar en la configuración de la Plataforma universal de Windows y de activar las casillas **Initialize XR on Startup** (Inicializar XR al inicio), **OpenXR** y **Microsoft HoloLens feature set** (Conjunto de características de Microsoft HoloLens).

![Configuración de XR de Unity con la opción para agregar OpenXR y las características de Microsoft HoloLens seleccionadas](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

>[!Important]
>Si ve un icono de advertencia rojo junto al complemento OpenXR (versión preliminar), haga clic en el icono y seleccione Fix all (Corregir todo) antes de continuar. Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.
>![Menú de validación del proyecto de OpenXR con todos los problemas seleccionados que se van a corregir.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)

En la barra de menús de la parte superior de la pantalla, vaya a **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2 (Aplicar la configuración de proyecto recomendada para HoloLens 2)** para obtener un mejor rendimiento de la aplicación.

![Menú de Mixed Reality con las opciones OpenXR y Apply recommended project settings for HoloLens 2 (Aplicar la configuración de proyecto recomendada para HoloLens 2) seleccionadas](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

Una vez que Unity haya terminado de importar los archivos necesarios, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no es así, use el menú de Unity para abrirla.

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![Ventana de configuración de MRTK con las opciones predeterminadas seleccionadas](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto. Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada. Para obtener más información sobre este tema, puede consultar los <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.


En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:

![Configuración de publicación de Unity](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> "Package name" es el identificador único para la aplicación. Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.

> [!TIP]
> "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR) y la casilla **Virtual Reality Supported** (Compatibilidad con realidad virtual); haga clic en el icono **+** y, después, seleccione Windows Mixed Reality para agregar el SDK de Windows Mixed Reality:

![XR Settings (Configuración de XR) de Unity con la opción para agregar el SDK de Windows Mixed Reality seleccionada](../images/mr-learning-base/base-02-section5-step2-4.png)

Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no aparece, puede abrirlo de forma manual desde el menú Unity seleccionando la opción **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity)

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![Ventana de configuración de MRTK](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto. Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada. Para obtener más información sobre este tema, puede consultar los <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR) y, a continuación, use la lista desplegable **Depth Format** (Formato de profundidad) para seleccionar **16-bit depth** (Profundidad de 16 bits):

![Habilitar la profundidad 16 en Unity](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudar a mejorar el rendimiento de los gráficos en el proyecto. Para obtener más información sobre este tema, puede consultar la sección <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación Performance (Rendimiento) de MRTK.

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:

![Configuración de publicación de Unity. Nombre de paquete configurado](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> "Package name" es el identificador único para la aplicación. Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.

> [!TIP]
> "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.
