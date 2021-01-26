---
title: Captura de realidad mixta para desarrolladores
description: Obtenga información sobre las prácticas recomendadas para habilitar, usar y representar una captura de realidad mixta para desarrolladores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, Foto, vídeo, captura, cámara
ms.openlocfilehash: 2539c8e2a6f26ba1f36cd28502bf8d0f50803657
ms.sourcegitcommit: bd9b2734903652b106db86686428c03acf104707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2021
ms.locfileid: "98763724"
---
# <a name="mixed-reality-capture-for-developers"></a>Captura de realidad mixta para desarrolladores

> [!NOTE]
> Consulte [representación de la cámara PV](#render-from-the-pv-camera-opt-in) a continuación para obtener instrucciones sobre una nueva funcionalidad de MRC para HoloLens 2.

Puede tomar una foto o un vídeo de [captura de realidad mixta](/hololens/holographic-photos-and-videos) (MRC) en cualquier momento, pero hay algunas cosas que debe tener en cuenta al desarrollar la aplicación. Esto incluye procedimientos recomendados para la calidad visual de MRC y para responder a los cambios del sistema mientras se capturan MRCs.

Los desarrolladores también pueden integrar sin problemas la captura y la inserción de la realidad mixta en sus aplicaciones.

MRC en HoloLens (primera generación) es compatible con vídeos y fotos de hasta 720p, mientras que MRC en HoloLens 2 es compatible con vídeos de hasta 1080p y fotos de hasta 4K.

## <a name="the-importance-of-quality-mrc"></a>La importancia de la MRC de calidad

Tanto si se trata de capturas de pantallas de realidad mixta de la página de Microsoft Store como de otros usuarios que comparten contenido de captura en redes sociales, un medio de captura de realidad mixta suele ser la primera vez que los usuarios se expongan a la aplicación Puede usar MRC para demostrar su aplicación, educar a los usuarios, animar a los usuarios a compartir sus interacciones de mundo mixtas y para la investigación de los usuarios y la solución de problemas.

## <a name="how-mrc-impacts-your-app"></a>Cómo afecta la MRC a la aplicación

### <a name="enabling-mrc-in-your-app"></a>Habilitación de MRC en la aplicación

De forma predeterminada, una aplicación no tiene que hacer nada para permitir que los usuarios tomen capturas de realidad mixta.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Habilitación de la alineación mejorada de MRC en la aplicación

De forma predeterminada, la captura de realidad mixta combina la salida holográfica del ojo derecho con la cámara de foto/vídeo (PV). Estos dos orígenes se combinan mediante el punto de enfoque establecido por la aplicación envolvente que se está ejecutando actualmente.

Esto significa que los hologramas fuera del plano de foco no se alinearán debido a la distancia física entre la cámara PV y la pantalla derecha.

#### <a name="set-the-focus-point"></a>Establecer el punto de enfoque

Las aplicaciones envolventes (en HoloLens) deben establecer el [punto de enfoque](../unity/focus-point-in-unity.md) en el que quieren que el plano de estabilización sea. Esto garantiza la mejor alineación en el casco y en la captura de realidad mixta.

Si no se establece un punto de enfoque, el plano de estabilización tendrá un valor predeterminado de 2 metros.

#### <a name="render-from-the-pv-camera-opt-in"></a>Representación de la cámara PV (participación)

HoloLens 2 agrega la posibilidad de que una aplicación envolvente se **represente desde la cámara PV** mientras se ejecuta la captura de realidad mixta. Para asegurarse de que la aplicación admite la representación adicional correctamente, la aplicación tiene que participar en esta funcionalidad.

La representación de la cámara PV ofrece las siguientes mejoras con respecto a la experiencia predeterminada de MRC:
* La alineación de hologramas en el entorno físico y las manos de las interacciones cercanas deben ser precisas en todas las distancias. Evite tener un desplazamiento en distancias que no sean el punto de enfoque tal como puede ver en el MRC predeterminado.
* El ojo adecuado en el casco no se verá comprometido, ya que no se usará para representar los hologramas para la salida de MRC.

Hay tres pasos para habilitar la representación desde la cámara PV:
1. Habilitación de PhotoVideoCamera HolographicViewConfiguration
2. Controlar la representación HolographicCamera adicional
3. Compruebe que los sombreadores y el código se representan correctamente desde este HolographicCamera adicional

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>Habilitación de PhotoVideoCamera HolographicViewConfiguration en DirectX

Para participar en la representación de la cámara PV, una aplicación simplemente permite el [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)de PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Control del procesamiento de HolographicCamera adicional en DirectX

Cuando la aplicación tiene participación en la representación de la cámara PV y se inicia la captura de realidad mixta:
1. Se activará el evento CameraAdded de HolographicSpace. Este evento se puede diferir si la aplicación no puede controlar la cámara en este momento.
2. Una vez que el evento se haya completado sin aplazamientos pendientes, el HolographicCamera aparecerá en la lista AddedCameras de HolographicFrame siguiente.

Cuando se detiene la captura de realidad mixta (o si la aplicación deshabilita la configuración de vista mientras se está ejecutando la captura de realidad mixta): el HolographicCamera aparecerá en la lista RemovedCameras de HolographicFrame siguiente y se activará el evento CameraRemoved de HolographicSpace.

Se ha agregado una propiedad [ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) a HolographicCamera para ayudar a identificar la configuración a la que pertenece una cámara.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Habilitación de PhotoVideoCamera HolographicViewConfiguration en Unity

> [!NOTE]
> Si usa Unity 2018, requiere **Unity 2018.4.13 F1** o una versión más reciente. Si usa Unity 2019, requiere **unity 2019,4** o una versión más reciente.

Para participar en la representación de la cámara PV al usar el [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html), habilite el proveedor de [configuración de cámara de realidad mixta de Windows](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html) y active la opción **representar desde la cámara PV**.

Si no está usando el kit de herramientas de realidad mixta, puede usar un componente para [participar manualmente](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) como se describió anteriormente para DirectX.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Control del procesamiento de HolographicCamera adicional en Unity

Esto se hace automáticamente por Unity.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Habilitación de PhotoVideoCamera HolographicViewConfiguration en la realidad

> [!NOTE]
> Se requiere **Unreal Engine 4.25** o versión posterior.

Para participar en la representación de la cámara PV:

1. Llame a **SetEnabledMixedRealityCamera** y **ResizeMixedRealityCamera**
    * Use los valores **Tamaño X** y **Tamaño Y** para establecer las dimensiones del vídeo.

![Tercera cámara](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Controlar el HolographicCamera adicional que se representa en inreal

Esto se hace automáticamente de forma automática.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Comprobar que los sombreadores y el código admiten cámaras adicionales

Ejecutar una captura de realidad mixta y comprobar la alineación inusual, el contenido que falta o los problemas de rendimiento. Actualice los sombreadores y el código según corresponda.

Si hay ciertas escenas que no pueden admitir la representación en una cámara adicional, puede deshabilitar el HolographicViewConfiguration de PhotoVideoCamera.

### <a name="disabling-mrc-in-your-app"></a>Deshabilitación de MRC en la aplicación

#### <a name="2d-app"></a>aplicación 2D

las aplicaciones 2D pueden elegir que el contenido visual esté oculto cuando se ejecute la captura de realidad mixta:
* Presente con la marca [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present)
* Crear la cadena de intercambio de la aplicación con la marca [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)
* Con la actualización de Windows 10 de mayo de 2019, estableciendo [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) de ApplicationView

#### <a name="immersive-app"></a>Aplicación envolvente

Las aplicaciones envolventes pueden optar por tener el contenido visual excluido de la captura de realidad mixta:
* Configuración de [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) de HolographicCameraRenderingParameter para deshabilitar la captura de realidad mixta para su fotograma asociado
* Configuración de [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) de HolographicCamera para deshabilitar la captura de realidad mixta para su cámara holográfica asociada

#### <a name="password-keyboard"></a>Teclado de contraseña

Con la actualización de Windows 10 de mayo de 2019, el contenido visual se excluye automáticamente de la captura de realidad mixta cuando se ve una contraseña o un teclado de PIN.

### <a name="knowing-when-mrc-is-active"></a>Saber cuándo está activa la MRC

Una aplicación puede usar la clase [AppCapture](/uwp/api/Windows.Media.Capture.AppCapture) para saber cuándo se está ejecutando la captura de realidad mixta del sistema (para audio o vídeo).

>[!NOTE]
>La API de [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) de AppCapture puede devolver null si la captura de realidad mixta no está disponible en el dispositivo. También es importante anular el registro del evento CapturingChanged cuando la aplicación está suspendida; de lo contrario, MRC puede entrar en un estado bloqueado.

### <a name="best-practices-hololens-specific"></a>Procedimientos recomendados (específicos de HoloLens)

Se espera que el MRC funcione sin ningún esfuerzo de desarrollo adicional, pero hay algunos aspectos que deben tenerse en cuenta al proporcionar la mejor experiencia de captura de la realidad mixta.

**MRC usa el canal alfa del holograma para combinar con la imagen de la [cámara](locatable-camera.md)**

El paso más importante es asegurarse de que la aplicación se está borrando a negro transparente en lugar de desplazarse al negro opaco. En Unity, esto se realiza de forma predeterminada con el MixedRealityToolkit. Si está desarrollando en una unidad que no es de Unity, puede que tenga que hacer un cambio de una línea.

Estos son algunos de los artefactos que puede ver en MRC si la aplicación no está borrando el negro transparente:

**Errores de ejemplo**: bordes negros alrededor del contenido (no se puede borrar a negro transparente)

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

**Errores de ejemplo**: la escena de fondo completa del holograma aparece en negro. Si se establece un valor alfa de fondo de uno, se obtiene un fondo negro.

![Si se establece un valor alfa de fondo de 1, se produce un fondo negro.](images/clearopaqueblack-300px.png)

**Resultado esperado**: los hologramas aparecen correctamente combinados con el mundo real (resultado esperado si se borra a transparente negro)

![Resultado esperado si se borra a negro transparente](images/cleartransparentblack-300px.png)

**Solución**:
* Cambie cualquier contenido que se muestre como negro opaco para que tenga un valor alfa de 0.
* Asegúrese de que la aplicación se está borrando a negro transparente.
* De forma predeterminada, Unity se borra automáticamente con el MixedRealityToolkit, pero si se trata de una aplicación que no es Unity, debe modificar el color usado con ID3D11DeiceContext:: ClearRenderTargetView (). Desea asegurarse de que está claro a negro transparente (0, 0, 0, 0) en lugar de negro opaco (0, 0, 0, 1).

Ahora puede ajustar los valores alfa de sus recursos si lo desea, pero normalmente no es necesario. La mayoría de las veces, MRCs tendrá un aspecto correcto. MRC supone que el alfa se multiplica previamente. Los valores alfa solo afectan a la captura de MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Qué esperar cuando se habilita MRC en HoloLens

Lo siguiente se aplica tanto a HoloLens (primera generación) como a HoloLens 2, a menos que se indique lo contrario:

* El sistema limitará la aplicación a la representación de 30 Hz. Esto crea cierto espacio para que se ejecute el MRC, por lo que la aplicación no necesita mantener una reserva de presupuesto constante y también coincide con el registro de vídeo de MRC fotogramas de 30 fps.
* El contenido de hologramas en el ojo adecuado del dispositivo puede parecer "brillar" al grabar y transmitir por secuencias el MRC: el texto puede ser más difícil de leer y los bordes de hologramas pueden aparecer más Jaggy (al participar en la tercera cámara en **HoloLens 2** se evita este riesgo).
* Las fotos y los vídeos de MRC respetarán el [punto de enfoque](../unity/focus-point-in-unity.md) de la aplicación si la aplicación lo ha habilitado, lo que le ayudará a garantizar que los hologramas se colocan con precisión. En el caso de los vídeos, el punto de enfoque se suaviza para que los hologramas parezcan desplazarse lentamente en su lugar si la profundidad del punto de enfoque cambia significativamente. Los hologramas que se encuentran en diferentes profundidades del punto de enfoque pueden aparecer como desplazamiento desde el mundo real (vea el ejemplo siguiente, donde el punto de enfoque se establece en 2 metros, pero el holograma se coloca en un medidor).

![Los hologramas de 2 metros aparecerán perfectamente registrados en el mundo. Los hologramas en distancias cercanas o Far pueden ser ligeramente desplazamientos.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integración de la funcionalidad de MRC desde dentro de la aplicación

La aplicación de realidad mixta puede iniciar la captura de fotos o vídeos de MRC desde dentro de la aplicación y el contenido capturado se pone a disposición de la aplicación sin que se almacene en el "rollo de cámara" del dispositivo. Puede crear una grabadora de MRC personalizada o aprovechar la interfaz de usuario de captura de cámara integrada. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC con interfaz de usuario de cámara integrada

Los desarrolladores pueden usar la *[API de captura de imágenes](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* de la cámara para obtener una foto o vídeo de realidad mixta capturada por el usuario con solo unas pocas líneas de código.

Esta API inicia la interfaz de usuario de la cámara MRC integrada, donde los usuarios pueden tomar fotos o vídeos y devuelven la captura resultante a la aplicación. Puede crear una grabadora personalizada de captura de realidad mixta si necesita agregar su propia interfaz de usuario de la cámara o un acceso de nivel inferior a las secuencias de captura.

### <a name="creating-a-custom-mrc-recorder"></a>Creación de una grabadora de MRC personalizada

Aunque el usuario siempre puede desencadenar una foto o un vídeo mediante el servicio de captura de MRC del sistema, es posible que una aplicación quiera compilar una aplicación de cámara personalizada que incluya hologramas en el flujo de la cámara como MRC. Esto permite a la aplicación iniciar capturas de la entrada del usuario, compilar una interfaz de usuario de grabación personalizada o personalizar la configuración de MRC para nombrar algunos ejemplos.

**HoloStudio agrega una cámara de MRC personalizada con efectos de MRC**

![HoloStudio agrega una cámara de MRC personalizada con efectos de MRC](images/cameraiconholostudio-300px.jpg)

Las aplicaciones de Unity deben ver [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) de la propiedad para habilitar los hologramas.

Otras aplicaciones pueden hacerlo mediante el uso de las [API de captura de multimedia de Windows](/uwp/api/Windows.Media.Capture.MediaCapture) para controlar la cámara y agregar un efecto de vídeo y audio de MRC para incluir los hologramas virtuales y el audio de las aplicaciones en las imágenes y los vídeos.

Las aplicaciones tienen dos opciones para agregar el efecto:
* La API anterior: [Windows. Media. Capture. MediaCapture. AddEffectAsync ()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* La nueva API recomendada de Microsoft (devuelve un objeto, lo que permite manipular propiedades dinámicas): [Windows. Media. Capture. MediaCapture. AddVideoEffectAsync ()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows. Media. Capture. mediacapture. AddAudioEffectAsync (),](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) que requiere que la aplicación cree su propia implementación de [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) y [IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition). Consulte la [aplicación de ejemplo de MRC](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) para obtener ejemplos.

>[!NOTE]
> Visual Studio no reconocerá el espacio de nombres Windows. Media. MixedRealityCapture, pero las cadenas seguirán siendo válidas.

Efecto de vídeo de MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureVideoEffect**)

|  Nombre de la propiedad  |  Tipo  |  Valor predeterminado  |  Descripción |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (videograbación)  |  Describir en qué secuencia de captura se utiliza este efecto. Audio no está disponible. |
|  HologramCompositionEnabled  |  boolean  |  true  |  Marca para habilitar o deshabilitar los hologramas en la captura de vídeo. |
|  RecordingIndicatorEnabled  |  boolean  |  true  |  Marca para habilitar o deshabilitar el indicador de grabación en pantalla durante la captura de hologramas. |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar la estabilización de vídeo con el seguimiento de HoloLens. |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Establezca el número de fotogramas históricos que se usan para la estabilización de vídeo. 0 es 0-latencia y casi "gratis" desde una perspectiva de eficacia y rendimiento. 15 se recomienda para obtener una mayor calidad (a costa de 15 fotogramas de latencia y memoria). |
|  GlobalOpacityCoefficient  |  FLOAT  |  0,9 (HoloLens) 1,0 (auricular envolvente)  |  Establezca el coeficiente de opacidad global del holograma en el intervalo de 0,0 (totalmente transparente) a 1,0 (totalmente opaco). |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar la devolución de un marco vacío si hay una aplicación de UWP 2D que muestra contenido protegido. Si esta marca es falsa y una aplicación de UWP en 2D muestra contenido protegido, la aplicación de UWP de 2D se reemplazará por una textura de contenido protegido tanto en el casco como en la captura de realidad mixta. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar que muestra la malla de área oculta y el contenido adyacente de la cámara holográfica. |
| Outlocate | Size | 0, 0 | Establezca el tamaño de salida deseado después de recortar para la estabilización de vídeo. Se elige un tamaño de recorte predeterminado si es 0 o se especifica un tamaño de salida no válido. |
| PreferredHologramPerspective | UINT32 | **Representación de** la configuración de la cámara en el portal de dispositivos de Windows | Enumeración usada para indicar qué configuración de la vista de cámara holográfica debe capturarse: 0 (Mostrar) significa que no se le pedirá a la aplicación que se represente desde la cámara de foto/vídeo, 1 (PhotoVideoCamera) solicitará a la aplicación que se represente desde la cámara de foto/vídeo (si la aplicación lo admite). Solo se admite en HoloLens 2 |

>[!NOTE]
> Puede cambiar el valor predeterminado de **PreferredHologramPerspective** en el portal de dispositivos de Windows. para ello, vaya a la [Página de captura de realidad mixta](using-the-windows-device-portal.md#mixed-reality-capture) y desactive la opción **representar de la cámara**. El valor predeterminado es **1 (PhotoVideoCamera)**, pero se puede desactivar para establecerlo en **0 (Mostrar)**.
>
> El valor predeterminado de **PreferredHologramPerspective** era **0 (Mostrar)** antes de la actualización del 2020 de junio (windows Holographic, versión 2004 compilación 19041,1106 y windows Holographic, versión 1903 compilación 18362,1064).

Efecto de audio de MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureAudioEffect**)

| Nombre de la propiedad | Tipo | Valor predeterminado | Descripción |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (MIC y audio del sistema) | Enumeración que se usa para indicar qué orígenes de audio se deben usar: 0 (solo audio de MIC), 1 (solo audio del sistema), 2 (MIC y audio del sistema) |
| LoopbackGain | FLOAT | Configuración de **ganancia de audio de aplicación** en el portal de dispositivos de Windows | Obtener para aplicar al volumen de audio del sistema. Oscila entre 0,0 y 5,0. Solo se admite en HoloLens 2 |
| MicrophoneGain | FLOAT | Configuración de **ganancia de audio de MIC** en el portal de dispositivos de Windows | Obtener para aplicar al volumen de MIC. Oscila entre 0,0 y 5,0. Solo se admite en HoloLens 2 |

>[!NOTE]
> Puede cambiar el valor predeterminado de **LoopbackGain** o **MicrophoneGain** en el portal de dispositivos de Windows. para ello, vaya a la página de [captura de realidad mixta](using-the-windows-device-portal.md#mixed-reality-capture) y ajuste el control deslizante junto a su configuración correspondiente. Ambos valores tienen como valor predeterminado **1,0**, pero se pueden establecer en cualquier valor entre **0,0** y **5,0**.
>
> Se ha agregado el uso del portal de dispositivos de Windows para configurar los valores de ganancia predeterminados con la actualización de junio de 2020 (Windows Holographic, versión 2004 compilación 19041,1106 y Windows Holographic, versión 1903 compilación 18362,1064).

### <a name="simultaneous-mrc-limitations"></a>Limitaciones de MRC simultáneas

Debe tener en cuenta ciertas limitaciones cuando varias aplicaciones acceden a MRC al mismo tiempo.

#### <a name="photovideo-camera-access"></a>Acceso a cámaras de fotos o vídeos

En HoloLens 1, MRC no podrá capturar una foto o capturar vídeo mientras un proceso está grabando vídeo o realizando una foto. Lo contrario también es cierto: si se está ejecutando MRC, la aplicación no podrá obtener acceso a la cámara. 

Con HoloLens 2, es posible compartir el acceso a la cámara. Si no necesita el control directo de la resolución o la velocidad de fotogramas, puede inicializar MediaCapture mediante la [propiedad SharedMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) con SharedReadOnly.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>Acceso integrado a cámaras de foto/vídeo de MRC

Funcionalidad de MRC integrada en Windows 10 (a través de Cortana, menú Inicio, métodos abreviados de hardware, Miracast, Windows Device portal):

* Se ejecutará con ExclusiveControl de forma predeterminada

Sin embargo, se ha agregado compatibilidad al subsistema de MRC para funcionar en modo compartido: 

* Si una aplicación solicita acceso de ExclusiveControl a la cámara de fotos o vídeos, el MRC integrado se detendrá automáticamente con la cámara de fotos o vídeos, de modo que la solicitud de la aplicación se realizará correctamente. 
* Si se inicia el MRC integrado en una aplicación de ExclusiveControl, el MRC integrado se ejecutará en modo SharedReadOnly 

Esta funcionalidad de modo compartido tiene algunas restricciones:

* Foto a través de Cortana, accesos directos de hardware o menú Inicio: requiere la actualización 2018 de abril de Windows 10 (o posterior)
* Vídeo a través de Cortana, accesos directos de hardware o menú Inicio: requiere la actualización 2018 de abril de Windows 10 (o posterior)
* Streaming de MRC en Miracast: requiere la actualización 2018 de octubre de Windows 10 (o posterior)
* Streaming de MRC en el portal de dispositivos de Windows o a través de la aplicación complementaria de HoloLens: requiere HoloLens 2

>[!NOTE]
> La resolución y la velocidad de fotogramas de la interfaz de usuario de la cámara MRC integrada pueden reducirse de sus valores normales cuando otra aplicación está usando la cámara de fotos o vídeos.

#### <a name="mrc-access-for-developers"></a>Acceso a MRC para desarrolladores

Se recomienda solicitar siempre el control exclusivo de la cámara al usar MRC. Esto garantizará que la aplicación tenga control total sobre la configuración de la cámara, siempre y cuando Conozca las limitaciones indicadas anteriormente. 

* Crear un objeto de captura multimedia con la [configuración de inicialización](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)
* Establezca la propiedad [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) en **Exclusive**

> [!CAUTION]
> Asegúrese de leer atentamente los [comentarios de SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) antes de continuar.

* Configure la cámara de la forma que desee.
* Iniciar la aplicación, capturar fotogramas de vídeo con la API de inicio y, después, habilitar MRC

> [!CAUTION]
> Si inicia MRC antes de iniciar la aplicación, no podemos garantizar que la característica funcionará según lo previsto.

Puede encontrar una muestra completa del proceso anterior en el ejemplo de [seguimiento de caras holográficas](/samples/microsoft/windows-universal-samples/holographicfacetracking).

> [!NOTE]
> Antes de la actualización del 2018 de abril de Windows 10, la grabadora personalizada de MRC de una aplicación se excluyeba mutuamente con el sistema MRC (captura de fotografías, captura de vídeos o streaming desde el portal de dispositivos de Windows).

## <a name="see-also"></a>Consulte también

* [Captura de realidad mixta](/hololens/holographic-photos-and-videos)
* [Vista del espectador](spectator-view.md)
* [Introducción al desarrollo de Unity](../unity/unity-development-overview.md)
* [Introducción al desarrollo de Unreal](../unreal/unreal-development-overview.md)
