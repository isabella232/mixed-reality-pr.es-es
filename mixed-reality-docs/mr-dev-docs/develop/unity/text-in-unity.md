---
title: Texto en Unity
description: 'Para mostrar texto en Unity, hay dos tipos de componentes de texto que puede usar: texto de la interfaz de usuario y malla de texto 3D.'
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, fuentes, tipografía, IU, experiencia de usuario, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: da2932234793a6db160d3bc2bd6dba02318c83bd
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010496"
---
# <a name="text-in-unity"></a>Texto en Unity

El texto es uno de los componentes más importantes de las aplicaciones holográficas. Para mostrar el texto en Unity, hay tres tipos de componentes de texto que puede usar: texto de la interfaz de usuario, malla de texto 3D y pro de malla de texto. De forma predeterminada, el texto de la interfaz de usuario y la malla de texto 3D aparecen borrosos y son demasiado grandes. Cambiar algunas variables da como resultado un texto más nítido y de mayor calidad con un tamaño manejable en HoloLens. Puede lograr una mejor calidad de representación si aplica un factor de escala para obtener las dimensiones adecuadas al usar los componentes de texto de la interfaz de usuario y malla de texto 3D.

![Cómo obtener texto nítido y bonito](images/hug-text-02-640px.png)<br>
*Texto predeterminado borroso en Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Trabajar con texto 3D de Unity (malla de texto) y texto de la interfaz de usuario

Unity supone que todos los elementos nuevos que se agregan a una escena tienen el tamaño de una unidad de Unity o una escala de transformación del 100%. Una unidad Unity se traduce en aproximadamente 1 medidor en HoloLens. En el caso de las fuentes, el cuadro de límite para un TextMesh 3D entra de forma predeterminada en aproximadamente 1 medidor de alto.

![Trabajar con fuentes en Unity](images/640px-hug-text-03.png)<br>
*El texto 3D de Unity predeterminado (malla de texto) ocupa una unidad de Unity, que es de 1 metro*

<br>

La mayoría de los diseñadores visuales usan puntos para definir tamaños de fuente en el mundo real. Hay aproximadamente 2835 puntos (2, 834.645666399962) en 1 medidor. En función de la conversión del sistema de punto a 1 medidor y el tamaño de fuente de la malla de texto predeterminado de la unidad 13, la matemática simple de 13 dividida entre 2835 es igual a 0,0046 (0.004586111116 a ser exacta), lo que proporciona una buena escala estándar para empezar (es posible que desee redondear a 0,005). El escalado del objeto o contenedor de texto a estos valores no solo permitirá la conversión 1:1 de los tamaños de fuente en un programa de diseño, sino que también proporciona un estándar para que pueda mantener la coherencia a lo largo de su experiencia.

![Ajustar los valores para el texto 3D de Unity y el texto de la interfaz de usuario](images/Text_In_Unity_Measurements1.png)<br>
*Ajustar los valores para el texto 3D de Unity y el texto de la interfaz de usuario*

<br>

![Malla de texto 3D de Unity con valores optimizados](images/hug-text-05-1000px.png)<br>
*Malla de texto 3D de Unity con valores optimizados*

<br>

Al agregar un elemento de texto basado en lienzo o en una interfaz de usuario a una escena, el tamaño de la disparidad todavía es mayor. Las diferencias en los dos tamaños son aproximadamente del 1000%, lo que haría que el factor de escala para los componentes de texto basados en la interfaz de usuario fuera 0,00046 (0.0004586111116 es exacto) o 0,0005 para el valor redondeado.

![Texto de la interfaz de usuario de Unity con valores optimizados](images/hug-text-04-1000px.png)<br>
*Texto de la interfaz de usuario de Unity con valores optimizados*

<br>

>[!NOTE]
>El valor predeterminado de cualquier fuente puede verse afectado por el tamaño de la textura de esa fuente o por el modo en que se importó la fuente a Unity. Estas pruebas se realizaron según la fuente Arial predeterminada en Unity, así como otra fuente importada.

## <a name="working-with-text-mesh-pro"></a>Trabajar con la malla de texto Pro

Con la malla de texto de Unity, puede proteger la calidad de representación de texto. Admite los contornos de texto nítidos independientemente de la distancia mediante la técnica de [campo de distancia con signo (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) . Con el mismo método de cálculo que hemos usado anteriormente para la malla de texto 3D y el texto de la interfaz de usuario, podemos encontrar los valores de escalado adecuados para usarlos con puntos tipográficos convencionales. Dado que la fuente pro de la malla de texto 3D predeterminada con el tamaño de 36 tiene un tamaño de límite de 2,5 unidades de Unity (2,5 m), podemos usar un valor de escalado de 0,005 para obtener el tamaño del punto. La malla de texto Pro en el menú de la interfaz de usuario tiene un tamaño de límite predeterminado de 25 unidades de Unity (25 m). Esto nos da 0,0005 para el valor de escalado.

![Escalado de valores para el texto 3D de Unity y la interfaz de usuario](images/Text_In_Unity_Measurements2.png)<br>
*Escalado de valores para el texto 3D de Unity y la interfaz de usuario*

## <a name="recommended-text-size"></a>Tamaño de texto recomendado
Como cabe esperar, los tamaños de tipo que usamos en un equipo o un dispositivo de tableta (normalmente entre 12 – 32pt.) son pequeños a una distancia de 2 metros. Depende de las características de cada fuente, pero, en general, el ángulo de visualización mínimo recomendado y el alto de la fuente para la legibilidad se encuentran en torno a 0.35 °-0,4 °/12.21-13.97 mm según nuestros estudios de investigación de usuarios. Es aproximadamente 35-40 PT con el factor de escala introducido anteriormente.

En el caso de la interacción cercana en 0,45 m (45 cm), el ángulo de visualización de la fuente mínima de lectura y el alto son 0,4 °-0,5 °/3.14 – 3,9 mm. Es aproximadamente 9-12 pt con el factor de escala introducido anteriormente.

![Contenido del intervalo de interacción Near y Far ](images/typography-distance-1000px.jpg)
 *en el intervalo de interacción Near y Far*

### <a name="the-minimum-legible-font-size"></a>El tamaño mínimo de fuente legible
| Distancia | Ángulo de visualización | Alto de texto | Tamaño de fuente |
|---------|---------|---------|---------|
| 45 cm (distancia de manipulación directa) | 0,4 °-0,5 ° | 3.14:3,9 mm | 8.9:11.13 pt |
| 2 m | 0.35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 PT |


### <a name="the-comfortably-legible-font-size"></a>Tamaño de fuente cómodamente legible
| Distancia | Ángulo de visualización | Alto de texto | Tamaño de fuente |
|---------|---------|---------|---------|
| 45 cm (distancia de manipulación directa) | 0,65 °-0,8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2 m | 0,6 °-0,75 ° | 20.9-26.2 mm | 59.4-74.2 PT |

Segoe UI (la fuente predeterminada para Windows) funciona bien en la mayoría de los casos. Sin embargo, evite usar familias de fuentes ligeras o semiligeras con un tamaño reducido, ya que los trazos verticales finos vibrarán y disminuirán la legibilidad. Las fuentes modernas con un grosor de trazo suficiente funcionan bien. Por ejemplo, Helvetica y Arial parecen magníficas y son legibles en HoloLens con pesos normales o en negrita.

![Visualización del ángulo de ](images/Text_In_Unity_ViewingAngle.jpg)
 *visualización de la distancia, el ángulo y el alto del texto*

## <a name="text-with-mixed-reality-toolkit-v2"></a>Texto con el kit de herramientas de realidad mixta V2

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Calidad de representación de texto nítido con la dimensión adecuada

En función de estos factores de escala, hemos creado [texto Prefabs con texto de interfaz de usuario y malla de texto 3D](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text). Los desarrolladores pueden usar estos Prefabs para obtener texto nítido y un tamaño de fuente coherente.

![Calidad de representación de texto nítido con la dimensión adecuada](images/hug-text-06-1000px.png)<br>
*Calidad de representación de texto nítido con la dimensión adecuada*

### <a name="shader-with-occlusion-support"></a>Sombreador con compatibilidad con oclusión

El material de fuente predeterminado de Unity no admite la oclusión. Por este motivo, verá el texto detrás de los objetos de forma predeterminada. Hemos incluido un [sombreador simple que admite la oclusión](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader). La imagen siguiente muestra el texto con el material de fuente predeterminado (izquierda) y el texto con una oclusión adecuada (derecha).

![Sombreador con compatibilidad con oclusión](images/hug-text-07-1000px.png)<br>
*Sombreador con compatibilidad con oclusión*

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de creación:

> [!div class="nextstepaction"]
> [Entrada de voz](voice-input-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.


## <a name="see-also"></a>Consulte también
* [Text recurso prefabricado in the MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [Tipografía](../../design/typography.md)
