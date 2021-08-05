---
title: Configuración de la cámara en Unity
description: Aprenda a configurar y usar la cámara principal de Unity para Windows Mixed Reality desarrollo para realizar la representación holográfica.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, representación holográfica, holográfica, envolvente, punto de enfoque, búfer de profundidad, solo orientación, posicional, opaco, transparente, clip, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 1ac8c16e7bdd6b85b05c837e1a27fbd1e4cf4489ccb03d10ea5e952b2656cbe8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212333"
---
# <a name="camera-setup-in-unity"></a>Configuración de la cámara en Unity

Cuando se usa un casco de realidad mixta, se convierte en el centro del mundo holográfico. El componente [Cámara de](https://docs.unity3d.com/Manual/class-Camera.html) Unity controlará automáticamente la representación estereomática y seguirá el movimiento y la rotación de la cabeza. Sin embargo, para optimizar completamente la calidad visual y la estabilidad [del holograma,](../platform-capabilities-and-apis/hologram-stability.md)debe establecer la configuración de la cámara que se describe a continuación.

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens cascos envolventes frente a realidad virtual

La configuración predeterminada en el componente Cámara de Unity es para las aplicaciones 3D tradicionales, que necesitan un fondo similar a Skybox, ya que no tienen un mundo real.

* Cuando se ejecuta en un casco **[envolvente,](../../discover/immersive-headset-hardware-details.md)** se representa todo lo que ve el usuario, por lo que es probable que quiera mantener el skybox.
* Sin embargo, cuando se ejecuta en **un** casco holográfico [como HoloLens](/hololens/hololens2-hardware), el mundo real debe aparecer detrás de todo lo que representa la cámara. Establezca el fondo de la cámara en transparente (en HoloLens, el negro se representa como transparente) en lugar de una textura skybox:
    1. Seleccione la cámara principal en el panel Jerarquía.
    2. En el panel Inspector, busque el componente Camera (Cámara) y cambie la lista desplegable Clear Flags (Borrar marcas) de Skybox a Solid Color (Color sólido).
    3. Seleccione el selector Color de fondo y cambie los valores RGBA a (0, 0, 0, 0)
        1. Si establece esto desde el código, puede usar el de Unity. [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Instalación de cámara

Sea cual sea el tipo de experiencia que desarrolle, la cámara principal siempre es el componente de representación estéreo principal asociado a la pantalla montada en la cabeza del dispositivo. Será más fácil crear la aplicación si se imagine que la posición inicial del usuario es (X: 0, Y: 0, Z: 0). Puesto que la cámara principal está haciendo un seguimiento del movimiento de la cabeza del usuario, la posición inicial del usuario se puede establecer estableciendo la posición inicial de la cámara principal.

La opción central que debe tomar es si va a desarrollar para cascos envolventes HoloLens vr. Una vez que lo haya hecho, vaya a la sección de configuración que se aplique.

### <a name="hololens-camera-setup"></a>HoloLens configuración de la cámara

Para HoloLens aplicaciones, debe usar delimitadores para los objetos que quiera bloquear en el entorno de escena. Se recomienda usar espacio sin enlazar para maximizar la estabilidad y crear anclajes en varias salas.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>Configuración de la cámara vr

Windows Mixed Reality aplicaciones en una amplia gama de [escalas](../../design/coordinate-systems.md#mixed-reality-experience-scales)de experiencia, desde aplicaciones de solo orientación y de escalado asentado hasta aplicaciones de escala de sala. Por HoloLens, puede ir más allá y crear aplicaciones a escala mundial que permiten a los usuarios recorrer más de 5 metros, explorando toda una planta de un edificio y más allá.

El primer paso para crear una experiencia de realidad mixta en Unity es determinar a qué escala [de experiencia](../../design/coordinate-systems.md) se dirigirá la aplicación:

* [Orientación o escala asentada](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [Escala de habitación o de pie](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [Escala mundial](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Experiencias a escala de habitación o permanentes

> [!NOTE]
> Si va a crear para HL2, se recomienda crear una experiencia con los ojos o usar [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) para razonar sobre el suelo de la escena.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Experiencias asentadas

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Configuración del fondo de la cámara

Si usa MRTK, el fondo de la cámara se configura y administra automáticamente. En el caso del SDK de XR o los proyectos WSA heredados, se recomienda establecer el fondo de la cámara en negro sólido en HoloLens y mantener el skybox para VR.

## <a name="using-multiple-cameras"></a>Uso de varias cámaras

Cuando hay varios componentes camera en la escena, Unity sabe qué cámara usar para la representación estereotipa en función de qué GameObject tiene la etiqueta MainCamera. En XR heredado, también usa esta etiqueta para sincronizar el seguimiento de la cabeza. En el SDK de XR, el seguimiento de la cabeza está controlado por un script TrackedPoseDriver asociado a la cámara.

## <a name="sharing-depth-buffers"></a>Uso compartido de búferes de profundidad

Compartir el búfer de profundidad de la aplicación para Windows cada fotograma dará a la aplicación una de las dos potenciaciones de estabilidad del holograma, en función del tipo de casco para el que se representa:

* **Los cascos envolventes** de REALIDAD virtual pueden ocuparse de la reproducción posicional cuando se proporciona un búfer de profundidad, ajustando los hologramas para que no se puedan interpretar correctamente en la posición y la orientación.
* **HoloLens cascos tienen** algunos métodos diferentes. HoloLens 1 seleccionará automáticamente un punto de enfoque cuando se proporciona un búfer de profundidad, optimizando la estabilidad del holograma [a](focus-point-in-unity.md) lo largo del plano que forma una intersección con la mayor parte del contenido. HoloLens 2 estabilizará el contenido mediante [LSR de profundidad (vea Comentarios).](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Uso de planos de recorte

La representación de contenido demasiado cerca del usuario puede no estar incomodable en la realidad mixta. Puede ajustar los planos [de recorte cercanos y lejanos](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) en el componente Cámara.

1. Seleccione la **cámara principal en** el panel **Jerarquía.**
2. En el panel **Inspector,** busque el componente  **Des** recortar **planos** de la cámara y cambie el cuadro de texto Cerca de **0.3** a **0.85**. El contenido representado aún más cerca puede provocar molestias al usuario y debe evitarse según las [directrices de distancia de representación](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).

## <a name="recentering-the-camera"></a>Reciente de la cámara

Si va [a](../../design/coordinate-systems.md)crear una experiencia de escalado asentado, puede hacer más reciente el origen mundial de Unity en la posición de la cabeza actual del usuario mediante una llamada a **[la XR. Método InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** en XR heredado o el método **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** en el SDK de XR.

## <a name="teleportation"></a>Teleportabilidad

Esta característica se reserva normalmente para experiencias de realidad virtual:

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Modos de reproducción

Tanto HoloLens cascos envolventes como los cascos envolventes volverán a proyectar cada fotograma que representa la aplicación para ajustarse a cualquier interpretación errónea de la posición real de la cabeza del usuario cuando se emiten fotones.

De manera predeterminada:

* **Los cascos envolventes** vr se encargan de la reproducción posicional si la aplicación proporciona un búfer de profundidad para un fotograma determinado. Los cascos envolventes también ajustarán los hologramas para que se despredicen en la posición y la orientación. Si no se proporciona un búfer de profundidad, el sistema solo corregirá los errores de orientación.
* **Los cascos holográficos** como HoloLens 2 se encargan de la reproducción posicional independientemente de si la aplicación proporciona su búfer de profundidad o no. La reproducción posicional es posible sin búferes de profundidad en HoloLens, ya que la representación suele ser dispersa con un fondo estable proporcionado por el mundo real.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si va a seguir el recorrido de desarrollo de Unity que hemos diseñado, se encuentra a la mitad de la exploración de los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

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
* [SDK de Azure Spatial Anchors para Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)