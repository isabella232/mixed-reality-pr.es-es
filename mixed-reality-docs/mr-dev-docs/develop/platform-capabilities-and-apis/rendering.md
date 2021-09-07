---
title: Representación
description: Obtenga información sobre cómo la representación holográfica permite que la aplicación dibuje un holograma en una ubicación precisa del mundo en torno al usuario.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: representación, holograma
ms.openlocfilehash: 5bd06b9ca521e489a8944a1813b735a0fe1d60a5
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244228"
---
# <a name="holographic-rendering"></a>Representación holográfica

La representación holográfica permite que la aplicación dibuje un holograma en una ubicación precisa del mundo en torno al usuario, ya sea que se coloque con precisión en el mundo físico o dentro de un dominio virtual que haya creado. [Hologramas](../../discover/hologram.md) objetos están hechos de sonido y luz. La representación permite que la aplicación agregue la luz.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (primera generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Representación</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Representación de holografías

La clave para la representación holográfica es saber qué tipo de dispositivo se usa. Los dispositivos **con pantallas de consulta,** [como HoloLens](/hololens/hololens1-hardware), agregan luz al mundo. Los píxeles negros son totalmente transparentes, mientras que los píxeles más claros son cada vez más opacos. Dado que la luz de las pantallas se agrega a la luz del mundo real, los píxeles blanco son translúcidos.

Aunque la representación estereomática proporciona una [](../../design/interaction-fundamentals.md) indicación de profundidad para los hologramas, agregar efectos de puesta a tierra puede ayudar a los usuarios a ver más fácilmente qué superficie está cerca de un holograma. Una técnica de puesta a tierra consiste en agregar un brillo alrededor de un holograma en la superficie cercana y, a continuación, representar una sombra contra este brillo. De esta manera, la sombra parece restar luz del entorno. [El sonido espacial](../../design/spatial-sound.md) es otra indicación de profundidad importante, que permite a los usuarios razonar sobre la distancia y la ubicación relativa de un holograma.

Los **dispositivos con pantallas** opacas, [como Windows Mixed Reality cascos envolventes,](../../discover/immersive-headset-hardware-details.md)bloquean el mundo. Los píxeles negros son de color negro sólido y cualquier otro color aparece como ese color para el usuario. La aplicación es responsable de representar todo lo que ve el usuario. Esto hace que sea aún más importante mantener una frecuencia de actualización constante para que los usuarios tengan una experiencia cómoda.

## <a name="predicted-rendering-parameters"></a>Parámetros de representación predichos

Los cascos de realidad mixta (tanto HoloLens como los cascos envolventes) siguen continuamente la posición y la orientación de la cabeza del usuario con respecto a su entorno. A medida que la aplicación comienza a preparar su siguiente fotograma, el sistema predice dónde estará la cabeza del usuario en el futuro en el momento exacto en que el marco aparece en las pantallas. En función de esta predicción, el sistema calcula la vista y las transformaciones de proyección que se usarán para ese marco. La aplicación **debe usar estas transformaciones para generar resultados correctos.** Si no se usan transformaciones proporcionadas por el sistema, la imagen resultante no se alineará con el mundo real, lo que provocará una incomodidad del usuario.

> [!NOTE]
> Para predecir con precisión cuándo llegará un nuevo fotograma a las pantallas, el sistema mide constantemente la latencia efectiva de un extremo a otro de la canalización de representación de la aplicación. Aunque el sistema se ajusta a la longitud de la canalización de representación, puede mejorar la estabilidad del holograma manteniendo esa canalización lo más corta posible.

Las aplicaciones que usan técnicas avanzadas para aumentar la predicción del sistema pueden invalidar las transformaciones de proyección y vista del sistema. Estas aplicaciones deben seguir utilizando transformaciones proporcionadas por el sistema como base para que sus transformaciones personalizadas produzcan resultados significativos.

## <a name="other-rendering-parameters"></a>Otros parámetros de representación

Al representar un marco, el sistema especifica la ventanilla del búfer de reserva en la que debe dibujarse la aplicación. Esta ventanilla suele ser menor que el tamaño completo del búfer de fotogramas. Sea cual sea el tamaño de la ventanilla, una vez que la aplicación representa el marco, el sistema escala la imagen para rellenar la totalidad de las pantallas.

En el caso de las aplicaciones que no pueden representarse a la velocidad de actualización [necesaria,](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) los parámetros de representación del sistema se pueden configurar para reducir la presión de memoria y el costo de representación a costa de un mayor alias de píxel. También se puede cambiar el formato del búfer de reserva, que para algunas aplicaciones puede ayudar a mejorar el ancho de banda de memoria y el rendimiento de píxeles.

La frustum de representación, la resolución y la velocidad de fotogramas en la que se le pide a la aplicación que se represente también pueden cambiar de fotograma a fotograma, y pueden diferir en el ojo izquierdo y derecho. Por ejemplo, cuando [la](/hololens/holographic-photos-and-videos) captura de realidad mixta [](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) (MRC) está activa y no se opta por la configuración de la vista de la cámara de fotos y vídeos, se podría representar un ojo con un FOV o resolución más grandes.

Para cualquier fotograma determinado, la aplicación debe *representarse* mediante la transformación de vista, la transformación de proyección y la resolución de ventanilla proporcionadas por el sistema. Además, la aplicación nunca debe asumir que ningún parámetro de representación o vista permanece fijo de fotograma a fotograma. Los motores como Unity controlan todas estas transformaciones en sus propios objetos de cámara para que siempre se respete el movimiento físico de los usuarios y el estado del sistema. Si la aplicación permite el movimiento virtual del usuario a través del mundo (por ejemplo, mediante el uso de la huella digital en un gamepad), puede agregar un objeto de plataforma principal encima de la cámara que lo mueva. Esto hace que la cámara refleje el movimiento físico y virtual del usuario. Si la aplicación modifica la transformación de vista, la transformación de proyección o la dimensión de ventanilla proporcionada por el sistema, debe informar al sistema mediante una llamada a la [API de invalidación adecuada.](/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)

Para mejorar la estabilidad de la representación holográfica, la aplicación debe proporcionar a Windows cada fotograma el búfer de profundidad que usó para la representación. Si la aplicación proporciona un búfer de profundidad, debe tener valores de profundidad coherentes, con la profundidad expresada en metros de la cámara. Esto permite al sistema usar los datos de profundidad por píxel para estabilizar mejor el contenido si la cabeza del usuario termina ligeramente desfasada de la ubicación predicho. Si no puede proporcionar el búfer de profundidad, puede proporcionar un punto de enfoque y normal, definiendo un plano que atraviesa la mayor parte del contenido. Si se proporcionan el búfer de profundidad y un plano de enfoque, el sistema podría usar ambos. En concreto, resulta útil proporcionar el búfer de profundidad y un punto de enfoque que incluya un vector de velocidad cuando la aplicación muestre hologramas que están en movimiento.

Consulte el [artículo Representación en DirectX](../native/rendering-in-directx.md) para obtener detalles de bajo nivel sobre este tema.

## <a name="holographic-cameras"></a>Cámaras holográficas

Windows Mixed Reality presenta el concepto de una **cámara holográfica**. Las cámaras holográficas son similares a las cámaras tradicionales que se encuentran en los textos gráficos 3D. definen las propiedades extrínsecos (posición y orientación) y intrínsecas de la cámara. (Por ejemplo, el campo de vista se usa para ver una escena 3D virtual). A diferencia de las cámaras 3D tradicionales, la aplicación no controla la posición, la orientación y las propiedades intrínsecas de la cámara. En su lugar, la posición y la orientación de la cámara holográfica se controlan implícitamente mediante el movimiento del usuario. El movimiento del usuario se retransmite a la aplicación fotograma a fotograma a través de una transformación de vista. Del mismo modo, las propiedades intrínsecas de la cámara se definen mediante la óptica calibrada del dispositivo y la retransmisión fotograma a fotograma a través de la transformación de proyección.

En general, la aplicación se representará para una sola cámara estéreo. Un bucle de representación sólido admitirá varias cámaras y admitirá cámaras mono y estéreo. Por ejemplo, el sistema podría pedir a la aplicación que se represente desde una perspectiva alternativa cuando el usuario activa una característica como la captura [de realidad](/hololens/holographic-photos-and-videos) mixta (MRC), dependiendo de la forma del casco. Las aplicaciones que pueden admitir varias cámaras las obtienen [optando por](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) el [tipo](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) de cámaras que pueden admitir.

## <a name="volume-rendering"></a>Representación de volúmenes

Al representar mris médicos o volúmenes [](volume-rendering.md) de ingeniería en 3D, a menudo se usan técnicas de representación de volúmenes. Estas técnicas pueden ser interesantes en la realidad mixta, donde los usuarios pueden ver de forma natural este volumen desde ángulos clave, simplemente moviendo la cabeza.

## <a name="supported-resolutions-on-hololens-first-gen"></a>Resoluciones admitidas en HoloLens (primera generación)

* El tamaño máximo de la ventanilla es una propiedad de [HolographicDisplay.](/uwp/api/windows.graphics.holographic.holographicdisplay) HoloLens se establece en el tamaño máximo de la ventanilla, que es 720p (1268 x 720), de forma predeterminada.
* El tamaño de la ventanilla se puede cambiar estableciendo ViewportScaleFactor en HolographicCamera. Este factor de escala está en el intervalo de 0 a 1.
* El tamaño de ventanilla más bajo admitido en HoloLens (primera generación) es el 50 % de 720p, que es 360p (634 x 360). Se trata de un ViewportScaleFactor de 0,5.
* No se recomienda nada inferior a 540p debido a la degradación visual, pero se puede usar para identificar cuellos de botella en la velocidad de relleno de píxeles.

## <a name="supported-resolutions-on-hololens-2"></a>Resoluciones admitidas en HoloLens 2

* Los tamaños de destino de representación actuales y máximos admitidos son propiedades de la [configuración de vista](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens 2 se establece en el tamaño máximo del destino de representación, que es 1440 x 936, de forma predeterminada.
* Las aplicaciones pueden cambiar el tamaño de los búferes de destino de representación llamando al método RequestRenderTargetSize para solicitar un nuevo tamaño de destino de representación. Se elegirá un nuevo tamaño de destino de representación, que cumpla o supere el tamaño de destino de representación solicitado. Esta API cambia el tamaño del búfer de destino de representación, que requiere reasignación de memoria en la GPU. Las implicaciones de esto incluyen: el tamaño del destino de representación se puede reducir verticalmente para reducir la presión de memoria en la GPU y no se debe llamar a este método con alta frecuencia.
* Las aplicaciones todavía pueden cambiar el tamaño de la ventanilla de la misma manera que lo hacían para HoloLens 1. No hay ninguna reasignación de memoria agregada en la GPU, por lo que se puede cambiar con alta frecuencia, pero no se puede usar para reducir la presión de memoria en la GPU.
* El tamaño de ventanilla más bajo admitido en HoloLens 2 es 634 x 412, un ViewportScaleFactor de aproximadamente 0,44 cuando el tamaño de destino de representación predeterminado está en uso.
* Si se proporciona un tamaño de destino de representación que es menor que el tamaño de ventanilla admitido más bajo, se omitirá el factor de escala de la ventanilla.
* No se recomienda nada inferior a 540p debido a la degradación visual, pero se puede usar para identificar cuellos de botella en la velocidad de relleno de píxeles.



## <a name="see-also"></a>Consulte también
* [Estabilidad de hologramas](hologram-stability.md)
* [Representación en DirectX](../native/rendering-in-directx.md)