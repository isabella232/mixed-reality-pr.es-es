---
ms.openlocfilehash: 7fd590713322c296cbbb14e133b1085aa27bb0197b70d1feca1ecb59ed61a3c7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201755"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Una vez que **MixedRealityFeatureTool** se haya abierto, haga clic en **Start** (Iniciar) para empezar a usar la herramienta Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

El primer paso es apuntar Mixed Reality Feature Tool a **Project path** (Ruta de acceso del proyecto) mediante el botón de **puntos suspensivos**. Haga clic en el botón de puntos suspensivos junto a la ruta de acceso del proyecto y examine la carpeta del proyecto en el explorador, por ejemplo, _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Cuando haya ubicado la carpeta del proyecto, haga clic en el botón Open (Abrir) para volver a Mixed Reality Feature Tool. A continuación, haga clic en **Discover Features** (Detectar características).

> [!NOTE]
> El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo. Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.

> [!Important]
> Mixed Reality Feature Tool realiza la validación para asegurarse de que se ha dirigido a una carpeta de proyecto de Unity. La carpeta debe contener las carpetas Assets, Packages y Project Settings.

Las características se agrupan por categoría para facilitar la búsqueda, haga clic en una lista desplegable **Mixed Reality Toolkit** para buscar paquetes relacionados con Mixed Reality Toolkit, y haga clic en la lista desplegable **Platform Support** (Soporte técnico de la plataforma) para buscar paquetes relacionados con varias plataformas de soporte técnico.

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

Compruebe **Mixed Reality Toolkit Foundation** y haga clic en la lista desplegable situada a un lado para seleccionar **MRTK 2.7.2**, también compruebe **Mixed Reality OpenXR Plugin 1.0.0** y haga clic en la lista desplegable situada a un lado para seleccionar la versión más reciente disponible y, a continuación, haga clic en el botón **Get features** (Obtener características) para descargar los paquetes seleccionados.

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>Configuración del proyecto de Unity

Una vez que Unity haya terminado de importar el paquete de la sección anterior, aparece un mensaje de advertencia para reiniciar el editor de Unity para habilitar los back-end para el nuevo sistema de complementos, haga clic en **Yes** (Sí).

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Una vez que Unity se reinicie, debería aparecer la ventana MRTK Project Configurator (Configurador del proyecto MRTK). Si no aparece, puede abrirlo de forma manual; para ello, vaya a **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar proyecto para MRTK):

![Apertura de la ventana MRTK Project Configurator](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

Haga clic **Unity OpenXR Plugin** para habilitar la administración de complementos de XR y agregue al proyecto los paquetes necesarios.

![Adición de Unity OpenXR Plugin ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

Con esto se importarán los paquetes de Unity necesarios para la administración de complementos de XR. Una vez hecho esto, haga clic en **Show XR Plug-In Management Settings** (Mostrar configuración de administración de complementos de XR) en MRTK Project Configurator (Configurador del proyecto MRTK).

![Show XR Plug-In Management Settings ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

Se abrirá la ventana **Project Settings** (Configuración del proyecto). En la ventana Project Settings (Configuración del proyecto), en **XR Plug-in Management** (Administración de complementos de XR), asegúrese de que se encuentra en la configuración de la Plataforma universal de Windows (pestaña con el logotipo de Windows). Asegúrese también de que **Initialize XR on Startup** (Inicializar XR al iniciar) esté marcada, y luego haga clic en las casillas **OpenXR** y **Microsoft HoloLens feature set** (Conjunto de características de Microsoft HoloLens) para habilitarlos.

![Habilitación de OpenXR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

Una vez que marque la casilla OpenXR, la ventana de MRTK Project Configurator (Configurador del proyecto MRTK) mostrará el mensaje actualizado con el botón **Apply Settings** (Aplicar configuración). Haga clic en el botón **Apply Settings** (Aplicar configuración). 

![Ventana 1 de configuración del proyecto](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

Al hacer clic en Apply Settings (Aplicar configuración), es posible que vea este mensaje de error en la consola. Puede continuar si este es el único error o si no hay ningún error.

![Mensaje de error de comunicación remota de OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

Para validar la configuración de OpenXR, haga clic en **OpenXR** en **XR Plug-in Management** (Administración de complementos de XR) y compruebe estos elementos:
* Depth Submission Mode: **Depth 16 Bit** (Modo de envío de profundidad: profundidad de 16 bits)
* Interaction Profiles: **Microsoft Hand Interaction Profile** (Perfiles de interacción: Perfil de interacción con la mano de Microsoft)

![Ventana 2 de configuración del proyecto](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudarle a mejorar el rendimiento de los gráficos en el proyecto. Para obtener más información sobre este tema, puede consultar la sección <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación Performance (Rendimiento) de MRTK.


En la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK), haga clic en **Next** (Siguiente) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración. (Si la cerró, puede abrirla de forma manual; para ello, vaya a **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** [Realidad mixta > Kit de herramientas > Utilidades > Configurar proyecto para MRTK]).

![Ventana 3 de configuración del proyecto](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Ventana 4 de configuración del proyecto](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

Una vez que haga clic en Apply (Aplicar), Unity intentará reiniciarse para que el sistema de entrada entre en vigor, haga clic en **Apply** para reiniciar el editor de Unity.

### <a name="configure-additional-project-settings"></a>Configuración de valores adicionales del proyecto

En el menú de Unity, seleccione **Edit** > **Project Settings** (Editar > Configuración del proyecto) para abrir la ventana Project Settings (Configuración del proyecto).

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:

![Configuración de publicación de Unity. Nombre de paquete configurado](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> "Package name" es el identificador único para la aplicación. Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.

> [!TIP]
> "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.

# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento XR para Unity 2019/2020 y Windows](#tab/winxr)

Una vez que **MixedRealityFeatureTool** se haya abierto, haga clic en **Start** (Iniciar) para empezar a usar la herramienta Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

El primer paso es apuntar Mixed Reality Feature Tool a **Project path** (Ruta de acceso del proyecto) mediante el botón de **puntos suspensivos**. Haga clic en el botón de puntos suspensivos junto a la ruta de acceso del proyecto y examine la carpeta del proyecto en el explorador, por ejemplo, _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


Cuando haya ubicado la carpeta del proyecto, haga clic en el botón Open (Abrir) para volver a Mixed Reality Feature Tool. A continuación, haga clic en **Discover Features** (Detectar características).

> [!NOTE]
> El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo. Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.

> [!Important]
> Mixed Reality Feature Tool realiza la validación para asegurarse de que se ha dirigido a una carpeta de proyecto de Unity. La carpeta debe contener las carpetas Assets, Packages y Project Settings.

Para facilitar la búsqueda de elementos, las características se agrupan por categoría. Haga clic en la lista desplegable **Mixed Reality Toolkit** para buscar los paquetes relacionados con Mixed Reality Toolkit.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Active la casilla **Mixed Reality Toolkit Foundation**, y haga clic en la lista desplegable a un lado para seleccionar **MRTK 2.7.0** y, a continuación, haga clic en el botón **Get features** (Obtener características) para descargar los paquetes seleccionados.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Configuración del proyecto de Unity

Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no aparece, puede abrirlo de forma manual; para ello, vaya a **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar proyecto para MRTK):

![Apertura de la herramienta del configurador de MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

Haga clic **Built-in Unity Plugin(non-OpenXR)** (Complemento de Unity integrado [distinto de OpenXR]) para habilitar la administración de complementos de XR y agregue al proyecto los paquetes necesarios.

![ Herramienta del configurador de MRTK](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> La captura de pantalla anterior es de Unity 2020, si usa Unity 2019, seleccione **XR SDK/XR Management** (SDK de XR/Administración de XR).

Con esto se importarán los paquetes de Unity necesarios para la administración de complementos de XR. Una vez hecho esto, haga clic en **Show Settings** (Mostrar configuración) en MRTK Project Configurator (Configurador del proyecto MRTK).

![Ventana de configuración del reproductor](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

Con esto se abre la ventana **Project Settings** (Configuración del proyecto). En la ventana Project Settings (Configuración del proyecto) en **XR Plug-in Management** (Administración de complementos de XR), asegúrese de estar en la configuración de la Plataforma universal de Windows, y asegúrese también de que **Initialize XR on Startup** (Inicializar XR en el inicio) está activada y marque la casilla **Windows Mixed Reality**.

![Ventana de configuración del reproductor Enable Mixed Reality-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no es así, use el menú de Unity para abrirla.

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), haga clic en **Next** (Siguiente) y, luego, use la lista desplegable Audio spatializer (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![MRTK Project Configurator: xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:

> * Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw. Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Rendimiento) de MRTK.
> * Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial. Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.

> [!TIP]
> La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto. Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada. Para obtener más información sobre este tema, puede consultar los <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.

Haga clic en **Next** (Siguiente) y, a continuación, en **Done** (Listo) en la ventana MRTK Project Configurator (Configurador del proyecto de MRTK) para finalizar la configuración del proyecto de Unity para XRSDK.

### <a name="configure-additional-project-settings"></a>Configuración de valores adicionales del proyecto

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:

En la ventana Project Settings (Configuración del proyecto), seleccione **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings** (Administración de complementos de XR > Windows Mixed Reality > Configuración del entorno de ejecución) y, a continuación, use el menú desplegable **Depth Buffer Format** (Formato de profundidad del búfer) para seleccionar **16-bit depth** (Profundidad de 16 bits):

![Habilitar la profundidad 16 en Unity](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudar a mejorar el rendimiento de los gráficos en el proyecto. Para obtener más información sobre este tema, puede consultar la sección <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación Performance (Rendimiento) de MRTK.

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:

![Configuración de publicación de Unity. Nombre de paquete configurado](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> "Package name" es el identificador único para la aplicación. Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.

> [!TIP]
> "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

Una vez que **MixedRealityFeatureTool** se haya abierto, haga clic en **Start** (Iniciar) para empezar a usar la herramienta Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

El primer paso es apuntar Mixed Reality Feature Tool a **Project path** (Ruta de acceso del proyecto) mediante el botón de **puntos suspensivos**. Haga clic en el botón de puntos suspensivos junto a la ruta de acceso del proyecto y examine la carpeta del proyecto en el explorador, por ejemplo, _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Cuando haya ubicado la carpeta del proyecto, haga clic en el botón Open (Abrir) para volver a Mixed Reality Feature Tool. A continuación, haga clic en **Discover Features** (Detectar características).

> [!NOTE]
> El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo. Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.

> [!Important]
> Mixed Reality Feature Tool realiza la validación para asegurarse de que se ha dirigido a una carpeta de proyecto de Unity. La carpeta debe contener las carpetas Assets, Packages y Project Settings.

Para facilitar la búsqueda de elementos, las características se agrupan por categoría. Haga clic en la lista desplegable **Mixed Reality Toolkit** para buscar los paquetes relacionados con Mixed Reality Toolkit.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Active **Mixed Reality Toolkit Foundation**, y haga clic en la lista desplegable a un lado para seleccionar **MRTK 2.7.0** y, a continuación, haga clic en el botón **Get features** (Obtener características) para descargar los paquetes seleccionados.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Configuración del proyecto de Unity

Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no aparece, puede abrirlo de forma manual; para ello, vaya a **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar proyecto para MRTK):

![Ruta del menú Configure Unity Project (Configurar proyecto de Unity) de Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

Haga clic en **Legacy XR** (XR heredado) para habilitar Legacy XR y para agregar los paquetes necesarios al proyecto.

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

Haga clic en el botón siguiente para habilitar la configuración de canalización de XR para Legacy XR (XR heredado).

![Ventana de configuración de MRTK de Unity](../images/mr-learning-base/base-02-section5-step1-3.PNG)

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), asegúrese de que todas las opciones estén marcadas y, además, use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![Ventana de configuración de MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:

> * Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw. Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Rendimiento) de MRTK.
> * Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial. Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.

> [!TIP]
> La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto. Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada. Para obtener más información sobre este tema, puede consultar los <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.

Haga clic en **Next** (Siguiente) y, a continuación, en el botón **Done** (Listo) en la ventana MRTK Project Configurator (Configurador del proyecto de MRTK) para finalizar la configuración del proyecto de Unity para Legacy XR (XR heredado).

### <a name="configure-additional-project-settings"></a>Configuración de valores adicionales del proyecto

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR) y, a continuación, use la lista desplegable **Depth Format** (Formato de profundidad) para seleccionar **16-bit depth** (Profundidad de 16 bits):

![Habilitar la profundidad 16 en Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudar a mejorar el rendimiento de los gráficos en el proyecto. Para obtener más información sobre este tema, puede consultar la sección <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación Performance (Rendimiento) de MRTK.

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:

![Configuración de publicación de Unity. Nombre de paquete configurado](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> "Package name" es el identificador único para la aplicación. Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.

> [!TIP]
> "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.
