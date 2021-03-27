---
title: Configuración de la cámara en Unity
description: Obtenga información sobre cómo configurar y usar la cámara principal de Unity para el desarrollo de Windows Mixed Reality para realizar la representación holográfica.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, representación holográfica, holográfica, envolvente, punto de enfoque, búfer de profundidad, solo orientación, posicional, opaco, transparente, recorte, auriculares de realidad mixta, auriculares mixto de realidad de Windows, auriculares de realidad virtual
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636308"
---
# <a name="camera-setup-in-unity"></a>Configuración de la cámara en Unity

Cuando se gasta un auricular de realidad mixta, se convierte en el centro del mundo holográfica. El componente de [cámara](https://docs.unity3d.com/Manual/class-Camera.html) Unity controlará automáticamente la representación de Stereoscopic y seguirá el movimiento y la rotación del cabezal. Sin embargo, para optimizar completamente la calidad visual y la [estabilidad del holograma](../platform-capabilities-and-apis/hologram-stability.md), debe establecer la configuración de la cámara que se describe a continuación.

## <a name="hololens-vs-vr-immersive-headsets"></a>Auriculares con micrófonos de HoloLens y VR

La configuración predeterminada del componente de cámara Unity es para las aplicaciones 3D tradicionales, que necesitan un fondo similar a SkyBOX, ya que no tienen un mundo real.

* Cuando se ejecuta en un **[auricular envolvente](../../discover/immersive-headset-hardware-details.md)**, está representando todo lo que ve el usuario y, por lo tanto, es probable que quiera mantener el skybox.
* Sin embargo, cuando se ejecuta en un **casco holográfica** como [HoloLens](/hololens/hololens2-hardware), el mundo real debe aparecer detrás de todo lo que se representa en la cámara. Establezca el fondo de la cámara para que sea transparente (en HoloLens, las representaciones en negro como transparente) en lugar de una textura SKYBOX:
    1. Seleccionar la cámara principal en el panel de jerarquías
    2. En el panel Inspector, busque el componente Camera y cambie la lista desplegable Clear flags de SKYBOX a Solid color.
    3. Seleccione el selector de colores de fondo y cambie los valores RGBA a (0, 0, 0, 0)
        1. Si el valor se establece desde el código, puede usar Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Instalación de cámara

Sea cual sea el tipo de experiencia que esté desarrollando, la cámara principal es siempre el componente principal de representación de estéreo conectado a la pantalla de montaje de la cabeza del dispositivo. Es más fácil diseñar la aplicación si se imagina la posición inicial del usuario como (X: 0, Y: 0, Z: 0). Dado que la cámara principal está realizando el seguimiento del movimiento del usuario, la posición inicial del usuario se puede establecer estableciendo la posición inicial de la cámara principal.

La elección central que debe tomar es si va a desarrollar para los auriculares de la implementación de HoloLens o de VR. Una vez que lo tenga, vaya a la sección de configuración que se aplica.

### <a name="hololens-camera-setup"></a>Configuración de la cámara de HoloLens

En el caso de las aplicaciones de HoloLens, debe usar delimitadores para los objetos que quiera bloquear en el entorno de la escena. Se recomienda utilizar espacio sin enlazar para maximizar la estabilidad y crear delimitadores en varios salones.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>Configuración de la cámara VR

Windows Mixed Reality es compatible con aplicaciones a través de una amplia gama de [escalas](../../design/coordinate-systems.md#mixed-reality-experience-scales), desde aplicaciones de solo orientación y de escalado sentado hasta las aplicaciones a escala de habitación. En HoloLens, puede ir más allá y compilar aplicaciones a gran escala que permitan a los usuarios recorrer más de 5 metros, explorando todo el piso de un edificio y más allá.

El primer paso para crear una experiencia de realidad mixta en Unity es determinar la [escala de experiencia](../../design/coordinate-systems.md) de destino de la aplicación:

* [Orientación o escalado](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [Permanente o a escala de habitación](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [Escala mundial](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Experiencias de escala de sala o de posición

> [!NOTE]
> Si va a compilar para HL2, le recomendamos que cree una experiencia en el nivel de ojo, o bien considere la posibilidad de usar la información de la [escena](../platform-capabilities-and-apis/scene-understanding-sdk.md) para explicar el piso de la escena.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Experiencias asentadas

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Configuración del fondo de la cámara

Si usa MRTK, el fondo de la cámara se configura y administra automáticamente. Para los proyectos XR SDK o WSA heredado, se recomienda establecer el fondo de la cámara en negro sólido en HoloLens y mantener SKYBOX para VR.

## <a name="using-multiple-cameras"></a>Uso de varias cámaras

Cuando hay varios componentes de cámara en la escena, Unity sabe qué cámara usar para la representación de Stereoscopic en función de qué GameObject tiene la etiqueta MainCamera. En XR heredado, también usa esta etiqueta para sincronizar el seguimiento del encabezado. En el SDK de XR, el seguimiento de encabezado está controlado por un script de TrackedPoseDriver conectado a la cámara.

## <a name="sharing-depth-buffers"></a>Uso compartido de búferes de profundidad

Compartir el búfer de profundidad de la aplicación en Windows cada fotograma proporcionará a la aplicación una de estas dos aumentos en la estabilidad del holograma, en función del tipo de casco que se está representando:

* Los **auriculares envolventes** de la VR pueden encargarse de la Reproyección posicional cuando se proporciona un búfer de profundidad, ajustando los hologramas para una predicción inesperada en la posición y la orientación.
* Los **auriculares HoloLens** tienen varios métodos diferentes. HoloLens 1 seleccionará automáticamente un [punto de enfoque](focus-point-in-unity.md) cuando se proporcione un búfer de profundidad, optimizando la estabilidad del holograma a lo largo del plano que intersecta el mayor contenido. HoloLens 2 estabilizará el contenido mediante [LSR de profundidad (vea la sección comentarios)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Usar planos de recorte

La representación de contenido demasiado cercana al usuario puede resultar incómodo en la realidad mixta. Puede ajustar los [planos de clips cercanos y alejados](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) en el componente de cámara.

1. Seleccionar la **cámara principal** en el panel de **jerarquías**
2. En el panel **Inspector** , busque los planos de **recorte** del componente de **cámara** y cambie el cuadro de texto **Near** de **0,3** a **0,85**. El contenido representado aún más cerca puede dar lugar a la molestia del usuario y debe evitarse según las [directrices de distancia de representación](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).

## <a name="recentering-the-camera"></a>Recentrar la cámara

Si va a crear una [experiencia de escalado original](../../design/coordinate-systems.md), puede volver a centrar el origen mundial de Unity en la posición principal del usuario mediante una llamada a **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** en el SDK de XR o el método **[XRInputSubsystem. TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** en el SDK de XR.

## <a name="teleportation"></a>Teleportabilidad

Esta característica se reserva normalmente para las experiencias de VR:

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Modos de Reproyección

Tanto HoloLens como los auriculares envolventes se reproyectan en cada fotograma que representa la aplicación para ajustarse a cualquier predicción de la posición principal real del usuario cuando se emiten las fotos.

De manera predeterminada:

* Los **auriculares envolventes de VR** se encargarán de la Reproyección posicional si la aplicación proporciona un búfer de profundidad para un fotograma determinado. Los auriculares envolventes también ajustarán los hologramas para una predicción inesperada en la posición y la orientación. Si no se proporciona un búfer de profundidad, el sistema solo corregirá errores de predicciones en la orientación.
* Los **auriculares holográficas** como HoloLens 2 se encargarán de la Reproyección posicional si la aplicación proporciona su búfer de profundidad o no. La Reproyección posicional es posible sin búferes de profundidad en HoloLens, ya que la representación suele ser dispersa con un fondo estable proporcionado por el mundo real.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Gaze](gaze-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también

* [Estabilidad de hologramas](../platform-capabilities-and-apis/hologram-stability.md)
* [Escalas de experiencia](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Pérdida de seguimiento en Unity](tracking-loss-in-unity.md)
* [Delimitadores espaciales](../../design/spatial-anchors.md)
* [Persistencia en Unity](persistence-in-unity.md)
* [Experiencias compartidas en Unity](shared-experiences-in-unity.md)
* [Azure Spatial Anchors](/azure/spatial-anchors)
* [SDK de anclajes espaciales de Azure para Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)