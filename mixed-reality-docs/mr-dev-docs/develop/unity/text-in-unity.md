---
title: Texto en Unity
description: 'Para mostrar texto en Unity, hay dos tipos de componentes de texto que puede usar: texto de la interfaz de usuario y malla de texto 3D.'
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, fuente, tipografía, interfaz de usuario, experiencia de usuario, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 3e5f296e9526e62bde7d03a0fee7847f4664e4a67187fcda1e66e22aa03053b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207977"
---
# <a name="text-in-unity"></a>Texto en Unity

El texto es uno de los componentes más importantes de las aplicaciones holográficas. Para mostrar texto en Unity, hay tres tipos de componentes de texto que puede usar: texto de la interfaz de usuario, malla de texto 3D y malla de texto Pro. De forma predeterminada, el texto de la interfaz de usuario y la malla de texto 3D aparecen desenfocados y son demasiado grandes. El cambio de algunas variables da como resultado texto más nítido y de mayor calidad con un tamaño administrable en HoloLens. Puede lograr una mejor calidad de representación mediante la aplicación de un factor de escalado para obtener las dimensiones adecuadas al usar los componentes texto de la interfaz de usuario y malla de texto 3D.

![Cómo obtener texto nítido y descriptivo](images/hug-text-02-640px.png)<br>
*Texto predeterminado desenfocado en Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Trabajar con texto 3D de Unity (malla de texto) y texto de la interfaz de usuario

Unity supone que todos los elementos nuevos agregados a una escena tienen un tamaño de unidad de Unity o una escala de transformación del 100 %. Una unidad de Unity se traduce en aproximadamente un medidor en HoloLens. En el caso de las fuentes, el rectángulo de selección de un TextMesh 3D se incluye de forma predeterminada con una altura de aproximadamente 1 metro.

![Trabajar con fuentes en Unity](images/640px-hug-text-03.png)<br>
*El texto 3D predeterminado de Unity (malla de texto) ocupa una unidad de Unity, que es de 1 metro*

<br>

La mayoría de los diseñadores visuales usan puntos para definir tamaños de fuente en el mundo real. Hay aproximadamente 2835 puntos (2834,645666399962) en un medidor. En función de la conversión del sistema de punto a 1 medidor y el tamaño de fuente predeterminado de Text Mesh de Unity de 13, la matemática simple de 13 dividida por 2835 equivale a 0,0046 (0,004586111116 para ser exactos), lo que proporciona una buena escala estándar con la que empezar (es posible que algunos quieran redondear a 0,005). El escalado del objeto o contenedor de texto a estos valores no solo permitirá la conversión 1:1 de tamaños de fuente en un programa de diseño, sino que también proporciona un estándar para que pueda mantener la coherencia a lo largo de la experiencia.

![Escalado de valores para el texto 3D de Unity y el texto de la interfaz de usuario](images/Text_In_Unity_Measurements1.png)<br>
*Escalado de valores para el texto 3D de Unity y el texto de la interfaz de usuario*

<br>

![Malla de texto 3D de Unity con valores optimizados](images/hug-text-05-1000px.png)<br>
*Malla de texto 3D de Unity con valores optimizados*

<br>

Al agregar una interfaz de usuario o un elemento de texto basado en lienzo a una escena, la disparidad de tamaño es aún mayor. Las diferencias en los dos tamaños son aproximadamente del 1000 %, lo que traería el factor de escala para los componentes de texto basados en la interfaz de usuario a 0,00046 (0,000458611116 para ser exactos) o 0,0005 para el valor redondeado.

![Texto de la interfaz de usuario de Unity con valores optimizados](images/hug-text-04-1000px.png)<br>
*Texto de la interfaz de usuario de Unity con valores optimizados*

<br>

>[!NOTE]
>El valor predeterminado de cualquier fuente puede verse afectado por el tamaño de textura de esa fuente o por cómo se importó la fuente en Unity. Estas pruebas se realizaron en función de la fuente de Arial predeterminada en Unity, así como de otra fuente importada.

## <a name="working-with-text-mesh-pro"></a>Trabajar con text mesh Pro

Con text mesh de Unity Pro, puede proteger la calidad de la representación de texto. Admite contornos de texto nítidos independientemente de la distancia mediante la técnica campo de distancia [firmada (SDF).](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) Con el mismo método de cálculo que usamos anteriormente para la malla de texto 3D y el texto de la interfaz de usuario, podemos encontrar los valores de escalado adecuados para usarlos con puntos tipográficos convencionales. Dado que la fuente 3D Text Mesh Pro predeterminada con el tamaño de 36 tiene un tamaño de límite de 2,5 unidades de Unity (2,5 m), podemos usar un valor de escalado de 0,005 para obtener el tamaño de punto. La malla de Pro en el menú de la interfaz de usuario tiene un tamaño de límite predeterminado de 25 unidades de Unity (25 m). Esto nos proporciona 0,0005 para el valor de escalado.

![Escalado de valores para el texto 3D y la interfaz de usuario de Unity](images/Text_In_Unity_Measurements2.png)<br>
*Escalado de valores para el texto 3D y la interfaz de usuario de Unity*

## <a name="recommended-text-size"></a>Tamaño de texto recomendado

Como puede esperar, los tamaños de tipo que usamos en un equipo o un dispositivo de tableta (normalmente entre 12 y 32pt) tienen un aspecto pequeño a una distancia de 2 metros. Depende de las características de cada fuente, pero en general, el ángulo de visualización mínimo recomendado y la altura de la fuente para la legibilidad son aproximadamente de 0,35°-0,4°/12,21-13,97 mm según nuestros estudios de investigación de usuario. Es aproximadamente de 35-40 pt con el factor de escalado introducido anteriormente.

Para la interacción cercana a 0,45 m (45 cm), el ángulo de visualización de la fuente legible mínima y la altura son 0,4°-0,5° /3,14–3,9 mm. Se trata de entre 9 y 12 puntos con el factor de escalado introducido anteriormente.

![Intervalo de interacción cercano y lejano ](images/typography-distance-1000px.jpg)
 *Contenido en un intervalo de interacción cercano y lejano*

### <a name="the-minimum-legible-font-size"></a>El tamaño mínimo de fuente legible

| Distancia | Ángulo | Alto del texto | Tamaño de fuente |
|---------|---------|---------|---------|
| 45 cm (distancia de manipulación directa) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>Tamaño de fuente legible cómodo

| Distancia | Ángulo | Alto del texto | Tamaño de fuente |
|---------|---------|---------|---------|
| 45 cm (distancia de manipulación directa) | 0.65°-0.8° | 5,1-6,3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20,9-26,2 mm | 59.4-74.2 pt |

Segoe UI (la fuente predeterminada para Windows) funciona bien en la mayoría de los casos. Sin embargo, evite el uso de familias de fuentes ligeras o semi ligeras en tamaño pequeño, ya que los trazos verticales finos se vibraciónrán y degradarán la legibilidad. Las fuentes modernas con suficiente grosor de trazo funcionan bien. Por ejemplo, Helvetica y Arial parecen impresionantes y son legibles en HoloLens con pesos normales o en negrita.

![Ángulo de ](images/Text_In_Unity_ViewingAngle.jpg)
 *visualización Distancia de visualización, ángulo y alto del texto*

## <a name="text-with-mixed-reality-toolkit-v2"></a>Texto con Mixed Reality Toolkit v2

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Calidad de representación de texto nítido con la dimensión adecuada

En función de estos factores de escalado, hemos creado objetos [prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)de texto con texto de la interfaz de usuario y malla de texto 3D . Los desarrolladores pueden usar estos objetos prefabs para obtener texto nítido y un tamaño de fuente coherente.

![Calidad de representación de texto nítido con la dimensión adecuada](images/hug-text-06-1000px.png)<br>
*Calidad de representación de texto nítido con la dimensión adecuada*

### <a name="shader-with-occlusion-support"></a>Sombreador con compatibilidad con oclusión

El material de fuente predeterminado de Unity no admite la oclusión. Por este problema, verá el texto detrás de los objetos de forma predeterminada. Hemos incluido un sombreador [simple que admite la oclusión](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader). En la imagen siguiente se muestra el texto con material de fuente predeterminado (izquierda) y el texto con oclusión adecuada (derecha).

![Sombreador con compatibilidad con oclusión](images/hug-text-07-1000px.png)<br>
*Sombreador con compatibilidad con oclusión*

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra a la mitad de la exploración de los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Entrada de voz](voice-input-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también

* [Prefab de texto en MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [Tipografía](../../design/typography.md)
