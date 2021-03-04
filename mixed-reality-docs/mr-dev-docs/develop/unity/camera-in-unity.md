---
title: Cámara en Unity
description: Obtenga información sobre cómo configurar y usar la cámara principal de Unity para el desarrollo de Windows Mixed Reality para realizar la representación holográfica.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, representación holográfica, holográfica, envolvente, punto de enfoque, búfer de profundidad, solo orientación, posicional, opaco, transparente, recorte, auriculares de realidad mixta, auriculares mixto de realidad de Windows, auriculares de realidad virtual
ms.openlocfilehash: 865d19482e5f612eab95fa2f74cb2bad59171496
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759771"
---
# <a name="camera-in-unity"></a>Cámara en Unity

Cuando se gasta un auricular de realidad mixta, se convierte en el centro del mundo holográfica. El componente de [cámara](https://docs.unity3d.com/Manual/class-Camera.html) Unity controlará automáticamente la representación de Stereoscopic y seguirá el movimiento y la rotación del cabezal. Sin embargo, para optimizar completamente la calidad visual y la [estabilidad del holograma](../platform-capabilities-and-apis/hologram-stability.md), debe establecer la configuración de la cámara que se describe a continuación.

## <a name="setup"></a>Configurar

1. Vaya a la sección **otras opciones** de **configuración del reproductor de la tienda Windows** .
2. Elija **Windows Mixed Reality** como el dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.
3. Seleccionar **realidad virtual compatible**

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, cuando se crea una nueva escena en Unity, contiene una cámara principal GameObject en la jerarquía que incluye el componente de cámara, pero no tiene la configuración que se aplica correctamente.

## <a name="holographic-vs-immersive-headsets"></a>Auriculares holográfica frente a auriculares envolvente

La configuración predeterminada del componente de cámara Unity es para las aplicaciones 3D tradicionales, que necesitan un fondo similar a SkyBOX, ya que no tienen un mundo real.

* Cuando se ejecuta en un **[auricular envolvente](../../discover/immersive-headset-hardware-details.md)**, está representando todo lo que ve el usuario y, por lo tanto, es probable que quiera mantener el skybox.
* Sin embargo, cuando se ejecuta en un **casco holográfica** como [HoloLens](/hololens/hololens1-hardware), el mundo real debe aparecer detrás de todo lo que se representa en la cámara. Establezca el fondo de la cámara para que sea transparente (en HoloLens, las representaciones en negro como transparente) en lugar de una textura SKYBOX:
    1. Seleccionar la cámara principal en el panel de jerarquías
    2. En el panel Inspector, busque el componente Camera y cambie la lista desplegable Clear flags de SKYBOX a Solid color.
    3. Seleccione el selector de colores de fondo y cambie los valores RGBA a (0, 0, 0, 0)

Puede usar el código de script para determinar en tiempo de ejecución si el casco es inmersivo o Holographic comprobando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).

## <a name="positioning-the-camera"></a>Posicionamiento de la cámara

Es más fácil diseñar la aplicación si se imagina la posición inicial del usuario como (X: 0, Y: 0, Z: 0). Dado que la cámara principal está realizando el seguimiento del movimiento del usuario, la posición inicial del usuario se puede establecer estableciendo la posición inicial de la cámara principal.

1. Seleccionar cámara principal en el panel jerarquía
2. En el panel Inspector, busque el componente de transformación y cambie la posición de (X: 0, Y: 1, Z:-10) a (X: 0, Y: 0, Z: 0)

   ![Cámara en el panel del inspector en Unity](images/maincamera-350px.png)  
   *Cámara en el panel del inspector en Unity*

## <a name="clip-planes"></a>Planos de recortes

La representación de contenido demasiado cercana al usuario puede resultar incómodo en la realidad mixta. Puede ajustar los [planos de clips cercanos y alejados](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) en el componente de cámara.

1. Seleccionar la cámara principal en el panel de jerarquías
2. En el panel Inspector, busque los planos de recorte del componente de cámara y cambie el cuadro de texto Near de 0,3 a 0,85. El contenido representado aún más cerca puede dar lugar a la molestia del usuario y debe evitarse según las [directrices de distancia de representación](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Varias cámaras

Cuando hay varios componentes de cámara en la escena, Unity sabe qué cámara usar para la representación de Stereoscopic y el seguimiento de encabezado en función de qué GameObject tiene la etiqueta MainCamera.

## <a name="recentering-a-seated-experience"></a>Recentro de una experiencia sentada

Si va a crear una [experiencia de escalado original](../../design/coordinate-systems.md), puede volver a centrar el origen mundial de Unity en la posición principal del usuario mediante una llamada a **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .

## <a name="reprojection-modes"></a>Modos de Reproyección

Tanto HoloLens como los auriculares envolventes se reproyectan en cada fotograma que representa la aplicación para ajustarse a cualquier predicción de la posición principal real del usuario cuando se emiten las fotos.

De manera predeterminada:

* Los **auriculares envolventes** se encargarán de la Reproyección posicional si la aplicación proporciona un búfer de profundidad para un fotograma determinado. Los auriculares envolventes también ajustarán los hologramas para una predicción inesperada en la posición y la orientación. Si no se proporciona un búfer de profundidad, el sistema solo corregirá errores de predicciones en la orientación.
* Los **auriculares holográficas** como HoloLens se encargarán de la Reproyección posicional si la aplicación proporciona su búfer de profundidad o no.  La Reproyección posicional es posible sin búferes de profundidad en HoloLens, ya que la representación suele ser dispersa con un fondo estable proporcionado por el mundo real.

Si sabe que está creando una [experiencia de solo orientación](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) con contenido rígidomente bloqueado por el cuerpo (por ejemplo, contenido de vídeo de 360 grados), puede establecer explícitamente el modo de Reproyección en Orientation solo estableciendo [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) en [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Uso compartido de los búferes de profundidad con Windows

Compartir el búfer de profundidad de la aplicación en Windows cada fotograma proporcionará a la aplicación una de estas dos aumentos en la estabilidad del holograma, en función del tipo de casco que se está representando:

* Los **auriculares envolventes** pueden encargarse de la Reproyección posicional cuando se proporciona un búfer de profundidad, ajustando los hologramas para una predicción inesperada en la posición y la orientación.
* Los **auriculares holográficas** tienen varios métodos diferentes. HoloLens 1 seleccionará automáticamente un [punto de enfoque](focus-point-in-unity.md) cuando se proporcione un búfer de profundidad, optimizando la estabilidad del holograma a lo largo del plano que intersecta el mayor contenido. HoloLens 2 estabilizará el contenido mediante [LSR de profundidad (vea la sección comentarios)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

Para establecer si la aplicación de Unity proporcionará un búfer de profundidad a Windows:

1. Vaya a **Editar**  >  **configuración de proyecto**  >  **reproductor**  >  **plataforma universal de Windows pestaña**  >  **XR configuración**.
2. Expanda el elemento **SDK de Windows Mixed Reality** .
3. Active o desactive la casilla **Habilitar uso compartido del búfer de profundidad** .  La opción Habilitar el uso compartido de búfer de profundidad está activada de forma predeterminada en los proyectos nuevos, ya que esta característica se ha agregado a Unity y se desactivará de forma predeterminada para los proyectos anteriores que se actualizaron.

Un búfer de profundidad puede mejorar la calidad visual, siempre y cuando Windows pueda asignar con precisión los valores normalizados de profundidad por píxel en el búfer de profundidad a distancias en metros, con los planos cercanos y lejanos que haya establecido en Unity en la cámara principal.  Si las pasadas de representación controlan los valores de profundidad de maneras típicas, generalmente debería estar bien aquí, aunque las pasadas de representación translúcidas que escriben en el búfer de profundidad mientras se muestran a los píxeles de color existentes pueden confundir la Reproyección.  Si sabe que las fases de representación van a dejar muchos de los píxeles de profundidad finales con valores de profundidad inexactos, es probable que obtenga una mejor calidad visual si desactiva "habilitar el uso compartido del búfer de profundidad".

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit"></a>Configuración automática de escenas y cámaras con el kit de herramientas de realidad mixta 

Siga la guía [paso a paso](tutorials/mr-learning-base-01.md) para agregar el kit de herramientas de realidad mixta al proyecto de Unity y se configurará el proyecto automáticamente. También puede configurar manualmente el proyecto sin MRTK con la guía de la sección siguiente.

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
* [Cámara principal de MixedRealityToolkit. recurso prefabricado](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)