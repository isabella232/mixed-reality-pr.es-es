---
title: Captura de realidad mixta para desarrolladores
description: Obtenga información sobre los procedimientos recomendados para habilitar, usar y representar la captura de realidad mixta para desarrolladores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, photo, video, capture, camera
ms.openlocfilehash: ec1a53d2f623a8047c2ee1973d8d6f20458ade88
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110247"
---
# <a name="mixed-reality-capture-for-developers"></a>Captura de realidad mixta para desarrolladores

> [!NOTE]
> Consulte [Representación desde la cámara PV](#render-from-the-pv-camera-opt-in) a continuación para obtener instrucciones sobre una nueva funcionalidad de MRC para HoloLens 2.

Puede tomar una foto [o](/hololens/holographic-photos-and-videos) un vídeo de captura de realidad mixta (MRC) en cualquier momento, pero hay algunas cosas que debe tener en cuenta al desarrollar la aplicación. Esto incluye los procedimientos recomendados para la calidad visual de MRC y la capacidad de respuesta a los cambios del sistema mientras se capturan los MRC.

Los desarrolladores también pueden integrar perfectamente la captura y la inserción de realidad mixta en sus aplicaciones.

MRC en HoloLens (primera generación) admite vídeos y fotos de hasta 720p, mientras que MRC en HoloLens 2 admite vídeos de hasta 1080p y fotos de hasta 4K de resolución.

## <a name="the-importance-of-quality-mrc"></a>Importancia de MRC de calidad

Tanto si se trata de capturas de pantalla de realidad mixta en la página de Microsoft Store como de otros usuarios que comparten contenido de captura en redes sociales, Captura de realidad mixta los medios suelen ser la primera exposición de los usuarios a la aplicación. Puede usar MRC para hacer demostraciones de la aplicación, formar a los usuarios, animar a los usuarios a compartir sus interacciones del mundo mixto y para la investigación y la resolución de problemas de los usuarios.

## <a name="how-mrc-impacts-your-app"></a>Cómo afecta MRC a la aplicación

### <a name="enabling-mrc-in-your-app"></a>Habilitación de MRC en la aplicación

De forma predeterminada, una aplicación no tiene que hacer nada para permitir que los usuarios realicen capturas de realidad mixta.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Habilitación de la alineación mejorada para MRC en la aplicación

De forma predeterminada, la captura de realidad mixta combina la salida holográfica del ojo derecho con la cámara de foto/vídeo (PV). Estos dos orígenes se combinan mediante el punto de enfoque establecido por la aplicación inmersiva que se está ejecutando actualmente.

Esto significa que los hologramas fuera del plano de enfoque no se alinearán debido a la distancia física entre la cámara PV y la pantalla derecha.

#### <a name="set-the-focus-point"></a>Establecer el punto de enfoque

Las aplicaciones inmersivas (en [](../unity/focus-point-in-unity.md) HoloLens) deben establecer el punto de enfoque de dónde quieren que esté su plano de estabilización. Esto garantiza la mejor alineación tanto en el casco como en la captura de realidad mixta.

Si no se establece un punto de enfoque, el plano de estabilización se establecerá de forma predeterminada en 2 metros.

#### <a name="render-from-the-pv-camera-opt-in"></a>Representación desde la cámara PV (participar)

HoloLens 2 agrega la capacidad de que una aplicación inmersiva se represente desde la cámara **PV** mientras se ejecuta la captura de realidad mixta. Para asegurarse de que la aplicación admite correctamente la representación adicional, la aplicación tiene que participar en esta funcionalidad.

La representación desde la cámara PV ofrece las siguientes mejoras con respecto a la experiencia de MRC predeterminada:
* La alineación del holograma con el entorno físico y las manos para interacciones cercanas debe ser precisa a todas las distancias. Evite tener un desplazamiento a distancias diferentes del punto de enfoque, como puede ver en el MRC predeterminado.
* El ojo derecho del casco no se ve comprometido, ya que no se usará para representar los hologramas para la salida de MRC.

Hay tres pasos para habilitar la representación desde la cámara PV:
1. Habilitación de PhotoVideoCamera HolographicViewConfiguration
2. Control de la representación adicional de HolographicCamera
3. Compruebe que los sombreadores y el código se representan correctamente desde este holographicCamera adicional.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>Habilitación de PhotoVideoCamera HolographicViewConfiguration en DirectX

Para participar en la representación desde la cámara PV, una aplicación simplemente habilita [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)de PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Control de la representación adicional de HolographicCamera en DirectX

Cuando la aplicación tiene la opción de participar en la representación desde la cámara PV y se inicia la captura de realidad mixta:
1. Se mostrará el evento CameraAdded de HolographicSpace. Este evento se puede aplazar si la aplicación no puede controlar la cámara en este momento.
2. Una vez que el evento se haya completado sin aplazamientos pendientes, HolographicCamera aparecerá en la siguiente lista AddedCamdoras de HolographicFrame.

Cuando se detiene la captura de realidad mixta (o si la aplicación deshabilita la configuración de vista mientras se ejecuta la captura de realidad mixta): HolographicCamera aparecerá en la siguiente lista RemovedCamgrafía de HolographicFrame y se activará el evento CameraRemoved de HolographicSpace.

Se ha agregado una propiedad [ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) a HolographicCamera para ayudar a identificar la configuración a la que pertenece una cámara.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Habilitación de PhotoVideoCamera HolographicViewConfiguration en Unity

> [!NOTE]
> Si usa Unity 2018, esto requiere **Unity 2018.4.13f1** o posterior. Si usa Unity 2019, esto requiere **Unity 2019.4** o una versión más reciente.

Para participar en la representación desde la cámara PV al [](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) usar el kit de herramientas de [Mixed Reality,](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)habilite el proveedor de configuración de la cámara Windows Mixed Reality y active Representar desde la cámara **PV**.

Si no usa el kit de herramientas de Mixed Reality, [](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) puede usar un componente para participar manualmente como se describió anteriormente para DirectX.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Control de la representación adicional de HolographicCamera en Unity

Unity lo hace automáticamente.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Habilitación de PhotoVideoCamera HolographicViewConfiguration en Unreal

> [!NOTE]
> Se requiere **Unreal Engine 4.25** o versión posterior.

Para participar en la representación de la cámara PV:

1. Llame a **SetEnabledMixedRealityCamera** y **ResizeMixedRealityCamera**
    * Use los valores **Tamaño X** y **Tamaño Y** para establecer las dimensiones del vídeo.

![Tercera cámara](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Control de la representación adicional de HolographicCamera en Unreal

Unreal lo hace automáticamente.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Comprobar que los sombreadores y el código admiten cámaras adicionales

Ejecute una captura de realidad mixta y compruebe si hay alineación inusual, falta contenido o problemas de rendimiento. Actualice los sombreadores y el código según corresponda.

Si hay determinadas escenas que no admiten la representación en una cámara adicional, puede deshabilitar HolographicViewConfiguration de PhotoVideoCamera.

### <a name="disabling-mrc-in-your-app"></a>Deshabilitación de MRC en la aplicación

#### <a name="2d-app"></a>Aplicación 2D

Las aplicaciones 2D pueden optar por ocultar su contenido visual cuando se ejecuta la captura de realidad mixta:
* Presente con la [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) marca
* Creación de la cadena de intercambio de la aplicación [con la DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) aplicación
* Con el Actualización de mayo de 2019 de Windows 10, establecer [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) de ApplicationView

#### <a name="immersive-app"></a>Aplicación inmersiva

Las aplicaciones inmersivas pueden optar por que su contenido visual se excluya de la captura de realidad mixta mediante:
* Establecimiento de [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) de HolographicCameraRenderingParameter para deshabilitar la captura de realidad mixta para su fotograma asociado
* Configuración de [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) de HolographicCamera para deshabilitar la captura de realidad mixta para su cámara holográfica asociada

#### <a name="password-keyboard"></a>Teclado de contraseña

Con la Actualización de mayo de 2019 de Windows 10, el contenido visual se excluye automáticamente de la captura de realidad mixta cuando se ve una contraseña o un teclado anclado.

### <a name="knowing-when-mrc-is-active"></a>Saber cuándo mrc está activo

Una aplicación puede usar la clase [AppCapture](/uwp/api/Windows.Media.Capture.AppCapture) para saber cuándo se ejecuta la captura de realidad mixta del sistema (para audio o vídeo).

>[!NOTE]
>La API [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) de AppCapture puede devolver null si la captura de realidad mixta no está disponible en el dispositivo. También es importante des registrar el evento CapturingChanged cuando se suspende la aplicación; de lo contrario, MRC puede entrar en un estado bloqueado.

### <a name="best-practices-hololens-specific"></a>Procedimientos recomendados (específicos de HoloLens)

Se espera que MRC funcione sin esfuerzos de desarrollo adicionales, pero hay algunas cosas que debe tener en cuenta al proporcionar la mejor experiencia de captura de realidad mixta.

**MRC usa el canal alfa del holograma para combinar con las imágenes [de](locatable-camera.md) la cámara**

El paso más importante es asegurarse de que la aplicación se borra en negro transparente en lugar de borrar a negro opaco. En Unity, esto se hace de forma predeterminada con MixedRealityToolkit. Si está desarrollando en un lugar que no es unity, es posible que tenga que realizar un cambio de una línea.

Estos son algunos de los artefactos que puede ver en MRC si la aplicación no se borra como negro transparente:

**Errores de ejemplo:** bordes negros alrededor del contenido (no se puede borrar a negro transparente)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**Errores de ejemplo:** toda la escena de fondo del holograma aparece en negro. Establecer un valor alfa de fondo de uno da como resultado un fondo negro

![Establecer un valor alfa de fondo de 1 da como resultado un fondo negro](images/clearopaqueblack-300px.png)

**Resultado esperado:** los hologramas aparecen correctamente combinados con el mundo real (resultado esperado si se borra a negro transparente).

![Resultado esperado si se borra a negro transparente](images/cleartransparentblack-300px.png)

**Solución**:
* Cambie cualquier contenido que se muestre como negro opaco para que tenga un valor alfa de 0.
* Asegúrese de que la aplicación se borra en negro transparente.
* El valor predeterminado de Unity es borrar automáticamente con MixedRealityToolkit, pero si se trata de una aplicación que no es de Unity, debe modificar el color usado con ID3D11DeiceContext::ClearRenderTargetView(). Quiere asegurarse de borrar a negro transparente (0,0,0,0) en lugar de negro opaco (0,0,0,1).

Ahora puede ajustar los valores alfa de los recursos si lo desea, pero normalmente no es necesario. La mayoría de las veces, los MRC tendrán un buen aspecto desde el primer momento. MRC presupone alfa multiplicado previamente. Los valores alfa solo afectarán a la captura de MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Qué esperar cuando MRC está habilitado en HoloLens

Lo siguiente se aplica tanto a HoloLens (primera generación) como a HoloLens 2, a menos que se indique lo contrario:

* El sistema limitará la aplicación a la representación de 30 Hz. Esto crea un espacio para que MRC se ejecute, por lo que la aplicación no necesita mantener una reserva de presupuesto constante y también coincide con la velocidad de fotogramas del registro de vídeo de MRC de 30 fps.
* El contenido del holograma en el ojo derecho del dispositivo puede parecer "desenlace" al grabar o transmitir MRC: el texto puede ser más difícil de leer y los bordes del holograma pueden parecer más jaggy (participar en la representación de la tercera cámara en **HoloLens 2** evita este riesgo).
* Las fotos y vídeos de MRC respetarán el punto de enfoque de la aplicación si la aplicación lo ha habilitado, lo que ayudará a garantizar que los hologramas se coloquen con precisión. [](../unity/focus-point-in-unity.md) En el caso de los vídeos, el punto de enfoque se suaviza para que los hologramas parezcan desplazarse lentamente si la profundidad del punto de enfoque cambia significativamente. Los hologramas que se encuentran en profundidades diferentes del punto de enfoque pueden parecer desplazamientos del mundo real (vea el ejemplo siguiente, donde el punto de enfoque está establecido en 2 metros, pero el holograma se coloca en 1 metro).

![Los hologramas de 2 metros aparecerán perfectamente registrados en el mundo. Los hologramas a distancias cercanas o lejanas pueden estar ligeramente desplazados.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integración de la funcionalidad de MRC desde la aplicación

La aplicación de realidad mixta puede iniciar la captura de fotos o vídeos de MRC desde dentro de la aplicación, y el contenido capturado está disponible para la aplicación sin almacenarse en el "lanzamiento de cámara" del dispositivo. Puede crear una grabadora MRC personalizada o aprovechar las ventajas de la interfaz de usuario de captura de cámara integrada. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC con interfaz de usuario de cámara integrada

Los desarrolladores pueden usar *[camera capture UI API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* para obtener una foto o un vídeo de realidad mixta capturados por el usuario con solo unas pocas líneas de código.

Esta API inicia la interfaz de usuario de la cámara DE MRC integrada, donde los usuarios pueden tomar una foto o un vídeo y devuelve la captura resultante a la aplicación. Puede crear una grabadora de Captura de realidad mixta personalizada si necesita agregar su propia interfaz de usuario de cámara o acceso de nivel inferior para capturar secuencias.

### <a name="creating-a-custom-mrc-recorder"></a>Creación de una grabadora MRC personalizada

Aunque el usuario siempre puede desencadenar una foto o un vídeo mediante el servicio de captura de MRC del sistema, es posible que una aplicación quiera crear una aplicación de cámara personalizada que incluya hologramas en el flujo de cámara como MRC. Esto permite a la aplicación iniciar capturas desde la entrada del usuario, crear una interfaz de usuario de grabación personalizada o personalizar la configuración de MRC para nombrar algunos ejemplos.

**HoloStudio agrega una cámara MRC personalizada mediante efectos de MRC**

![HoloStudio agrega una cámara MRC personalizada mediante efectos de MRC](images/cameraiconholostudio-300px.jpg)

Las aplicaciones de Unity [deben Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) la propiedad para habilitar hologramas.

Otras aplicaciones pueden hacerlo mediante las API de captura de [Windows Media](/uwp/api/Windows.Media.Capture.MediaCapture) para controlar la cámara y agregar un efecto mrc vídeo y audio para incluir hologramas virtuales y audio de aplicación en imágenes fijas y vídeos.

Las aplicaciones tienen dos opciones para agregar el efecto:
* La API anterior: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* La nueva API recomendada de Microsoft (devuelve un objeto, lo que permite manipular propiedades dinámicas): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) que requieren que la aplicación cree su propia implementación de [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) e [IAudioEffectDefinition.](/uwp/api/windows.media.effects.iaudioeffectdefinition) Consulte la [aplicación de ejemplo de MRC](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) para obtener ejemplos.

>[!NOTE]
> El espacio de nombres Windows.Media.MixedRealityCapture no se reconocerá Visual Studio, pero las cadenas siguen siendo válidas.

Efecto de vídeo MRC (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Nombre de la propiedad  |  Tipo  |  Valor predeterminado  |  Descripción |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Describa para qué secuencia de captura se usa este efecto. El audio no está disponible. |
|  HologramCompositionEnabled  |  boolean  |  true  |  Marca para habilitar o deshabilitar hologramas en la captura de vídeo. |
|  RecordingIndicatorEnabled  |  boolean  |  true  |  Marca para habilitar o deshabilitar el indicador de grabación en pantalla durante la captura de hologramas. |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar la estabilización de vídeo con tecnología del rastreador de HoloLens. |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Establezca cuántos fotogramas históricos se usan para la estabilización de vídeo. 0 es una latencia de 0 y casi "gratis" desde una perspectiva de energía y rendimiento. Se recomienda 15 para obtener la máxima calidad (a costa de 15 fotogramas de latencia y memoria). |
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 (casco envolvente)  |  Establezca el coeficiente de opacidad global del holograma en el intervalo de 0,0 (totalmente transparente) a 1,0 (totalmente opaco). |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar la devolución de un marco vacío si hay una aplicación para UWP 2d que muestra contenido protegido. Si esta marca es false y una aplicación para UWP 2d muestra contenido protegido, la aplicación para UWP 2d se reemplazará por una textura de contenido protegido tanto en el casco como en la captura de realidad mixta. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar mostrando la malla de área oculta de la cámara holográfica y el contenido vecino. |
| OutputSize | Size | 0, 0 | Establezca el tamaño de salida deseado después de recortar para la estabilización de vídeo. Se elige un tamaño de recorte predeterminado si se especifica 0 o un tamaño de salida no válido. |
| PreferredHologramPerspective | UINT32 | **Configuración Representar desde la** cámara en el Portal de dispositivos Windows | Enumeración que se usa para indicar qué configuración de vista de cámara holográfica se debe capturar: 0 (Mostrar) significa que no se pedirá a la aplicación que se represente desde la cámara de fotos o vídeos; 1 (PhotoVideoCamera) pedirá a la aplicación que se represente desde la cámara de fotos y vídeo (si la aplicación la admite). Solo se admite en HoloLens 2 |

>[!NOTE]
> Para cambiar el valor predeterminado de **PreferredHologramPerspective** en el Portal de dispositivos Windows, vaya a la página [Captura de realidad mixta](using-the-windows-device-portal.md#mixed-reality-capture) y desactive Representar desde la **cámara.** El valor predeterminado es **1 (PhotoVideoCamera),** pero se puede desactivar para establecerlo en **0 (Mostrar).**
>
> El valor predeterminado de **PreferredHologramPerspective** era **0 (Display)** antes de la actualización de junio de 2020 (Windows Holographic, compilación 19041.1106 y Windows Holographic, versión 18362.1064).

Efecto de audio MRC (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

| Nombre de la propiedad | Tipo | Valor predeterminado | Descripción |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (audio de micrófono y sistema) | Enumeración usada para indicar qué orígenes de audio se deben usar: 0 (solo audio de micrófono), 1 (solo audio del sistema), 2 (audio de micrófono y sistema) |
| LoopbackGain | FLOAT | **Configuración de ganancia de audio** de la aplicación en el Portal de dispositivos Windows | Obtenga para aplicarlo al volumen de audio del sistema. Va de 0,0 a 5,0. Solo se admite en HoloLens 2 |
| MicrophoneGain | FLOAT | **Configuración de ganancia de** audio de micrófono en la Portal de dispositivos Windows | Obtenga para aplicar al volumen de micrófono. Oscila entre 0,0 y 5,0. Solo se admite en HoloLens 2 |

>[!NOTE]
> Para cambiar el valor predeterminado de **LoopbackGain** o **MicrophoneGain** en el Portal de dispositivos Windows, vaya a la página Captura de realidad mixta y ajuste el control deslizante junto [a](using-the-windows-device-portal.md#mixed-reality-capture) sus respectivas configuraciones. Ambos valores tienen como valor predeterminado **1.0,** pero se pueden establecer en cualquier valor entre **0.0** y **5.0.**
>
> El Portal de dispositivos Windows para configurar los valores de ganancia predeterminados se agregó con la actualización de junio de 2020 (Windows Holographic, versión 2004, compilación 19041.1106 y Windows Holographic, versión 1903 compilación 18362.1064).

### <a name="simultaneous-mrc-limitations"></a>Limitaciones de MRC simultáneas

Debe tener en cuenta ciertas limitaciones cuando varias aplicaciones acceden a MRC al mismo tiempo.

#### <a name="photovideo-camera-access"></a>Acceso a la cámara de fotos y vídeos

En HoloLens 1, MRC no podrá capturar una foto o capturar vídeo mientras un proceso está grabando vídeo o tomando una foto. Lo contrario también es cierto: si MRC se está ejecutando, la aplicación no podrá obtener acceso a la cámara. 

Con HoloLens 2, es posible compartir el acceso a la cámara. Si no necesita un control directo de la resolución o la velocidad de fotogramas, puede inicializar MediaCapture mediante la propiedad [SharedMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) con SharedReadOnly.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>Acceso integrado a la cámara de fotos y vídeos de MRC

Funcionalidad mrc integrada en Windows 10 (a través de Cortana, menú Inicio, accesos directos de hardware, Miracast, Portal de dispositivos Windows):

* Se ejecutará con ExclusiveControl de forma predeterminada

Sin embargo, se ha agregado compatibilidad al subsistema MRC para que funcione en modo compartido: 

* Si una aplicación solicita acceso ExclusiveControl a la cámara de fotos y vídeos, MRC integrado dejará de usar automáticamente la cámara de fotos y vídeos para que la solicitud de la aplicación se haga correctamente. 
* Si se inicia MRC integrado mientras una aplicación tiene ExclusiveControl, MRC integrado se ejecutará en modo SharedReadOnly. 

Esta funcionalidad de modo compartido tiene ciertas restricciones:

* Foto a través de Cortana, accesos directos de hardware o menú Inicio: requiere la Actualización de abril de 2018 de Windows 10 (o posterior)
* Vídeo a través de Cortana, accesos directos de hardware o menú Inicio: requiere la Actualización de abril de 2018 de Windows 10 (o posterior)
* Streaming de MRC a través de Miracast: requiere la Actualización de octubre de 2018 de Windows 10 (o posterior)
* Streaming de MRC a Portal de dispositivos Windows o a través de la aplicación complementaria holoLens: requiere HoloLens 2

>[!NOTE]
> La resolución y la velocidad de fotogramas de la interfaz de usuario de la cámara MRC integrada podrían reducirse de sus valores normales cuando otra aplicación usa la cámara de fotos y vídeos.

#### <a name="mrc-access-for-developers"></a>Acceso de MRC para desarrolladores

Se recomienda solicitar siempre control exclusivo para la cámara cuando se usa MRC. Esto garantizará que la aplicación tenga control total de la configuración de la cámara, siempre que sea consciente de las limitaciones enumeradas anteriormente. 

* Creación de un objeto de captura multimedia mediante la configuración [de inicialización](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)
* Establezca la [propiedad SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) en **exclusive.**

> [!CAUTION]
> Asegúrese de leer detenidamente los comentarios [de SharingMode antes](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) de continuar.

* Configure la cámara de la manera que quiera.
* Inicio de la aplicación, captura de fotogramas de vídeo con la API de inicio y habilitación de MRC

> [!CAUTION]
> Si inicia MRC antes de iniciar la aplicación, no podemos garantizar que la característica funcionará según lo previsto.

Puede encontrar un ejemplo completo del proceso anterior en el ejemplo de seguimiento de [caras holográficas](/samples/microsoft/windows-universal-samples/holographicfacetracking).

> [!NOTE]
> Antes de Actualización de abril de 2018 de Windows 10, la grabadora MRC personalizada de una aplicación era mutuamente excluyente con MRC del sistema (captura de fotos, captura de vídeos o streaming desde la Portal de dispositivos Windows).

## <a name="see-also"></a>Consulte también

* [Captura de realidad mixta](/hololens/holographic-photos-and-videos)
* [Vista del espectador](spectator-view.md)
* [Introducción al desarrollo de Unity](../unity/unity-development-overview.md)
* [Introducción al desarrollo de Unreal](../unreal/unreal-development-overview.md)
