---
title: Sombreador estándar de MRTK
description: Documentación de MRTKStandardShader
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, Material Shader
ms.openlocfilehash: 0a92388bc9be7c11967501709031f559f17f8966
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176446"
---
# <a name="mrtk-standard-shader"></a>Sombreador estándar de MRTK

![Ejemplos de sombreador estándar](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

El sistema de sombreado estándar de MRTK usa un sombreador único y flexible que puede lograr objetos visuales similares al sombreador estándar de Unity, implementar principios [de Sistema Fluent Design](https://www.microsoft.com/design/fluent/) y mantener el rendimiento en dispositivos de realidad mixta.

## <a name="example-scenes"></a>Escenas de ejemplo

Puede encontrar los ejemplos de material del sombreador en la **escena MaterialGallery** en `MRTK/Examples/Demos/StandardShader/Scenes/` . Todos los materiales de esta escena usan el sombreador MRTK/Standard.

![Galería de materiales](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

Puede encontrar una escena de comparación para comparar y probar el sombreador MRTK/Standard con el ejemplo de sombreador Unity/Standard en la **escena StandardMaterialComparison** en `MRTK/Examples/Demos/StandardShader/Scenes/` .

![Comparación de materiales](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Architecture

El sistema de sombreado MRTK/Standard es un "sombreador uber" que usa la característica variante del programa de sombreador de [Unity](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) para generar automáticamente código de sombreador óptimo basado en propiedades de material. Cuando un usuario selecciona propiedades de material en el inspector de material, solo incurre en costos de rendimiento para las características que ha habilitado.

## <a name="material-inspector"></a>Inspector de material

Existe un inspector de material personalizado para el sombreador MRTK/Standard denominado [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) . El inspector habilita o deshabilita automáticamente las características del sombreador, en función de la selección del usuario y de los asistentes en la configuración del estado de representación. Para obtener más información sobre cada **característica, mantenga el puntero sobre cada propiedad en el Editor de Unity para obtener información sobre herramientas.**

![Material Inspector](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

La primera parte del inspector controla el estado de representación del material. *El modo de* representación determina cuándo y cómo se representará un material. El objetivo del sombreador MRTK/Standard es reflejar los modos de representación que se encuentran [en el sombreador Unity/Standard](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html). El sombreador MRTK/Standard también incluye un modo *de* representación aditiva y el *modo de* representación personalizado para un control de usuario completo.

| Modo de representación |         Descripción                                                       |
|----------------|---------------------------------------------------------------------------|
| Opaca         | (Valor predeterminado) Adecuado para objetos sólidos normales sin áreas transparentes.    |
| Recorte         | Permite la creación de efectos transparentes que tienen bordes duros entre las áreas opacas y transparentes. En este modo, no hay áreas semitransparentes, la textura es 100 % opaca o invisible. Esto resulta útil cuando se usa la transparencia para crear la forma de los materiales, como la humedad. |
| Atenuación           | Permite a los valores de transparencia atenuar completamente un objeto, incluidos los reflejos o resaltados especulares que pueda tener. Este modo es útil si desea animar un objeto que se desvanecha hacia dentro o hacia fuera. No es adecuado para representar materiales transparentes realistas, como el transparente o el cristal, ya que los reflejos y los resaltados también se atenuarán. |
| Transparente    | Adecuado para representar materiales transparentes realistas, como el metal transparente o el cristal. En este modo, el propio material toma los valores de transparencia (en función del canal alfa de la textura y el alfa del tono). Sin embargo, los reflejos y los resaltados de iluminación seguirán siendo visibles con total claridad, como es el caso de los materiales transparentes reales. |
| Aditivo       | Habilita un modo de combinación de suma, que suma el color de píxel anterior con el color de píxel actual. Este es el modo de transparencia preferido para evitar problemas de ordenación de transparencia.     |
| Personalizado         | Permite controlar manualmente todos los aspectos del modo de representación. Solo para uso avanzado.   |

![Modos de representación](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| Modo Cull |             Descripción                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Desactivado       | Deshabilita la selección de caras. La selección solo debe establecerse en Desactivado cuando se requiere una malla de dos lados.                                                                                        |
| Front     | Habilita la selección de caras frontales.                                                                                                                                                        |
| Atrás      | (Valor predeterminado) Habilita [la selección de cara posterior.](https://en.wikipedia.org/wiki/Back-face_culling) La selección de cara posterior debe habilitarse con la mayor frecuencia posible para mejorar el rendimiento de la representación. |

## <a name="performance"></a>Rendimiento

Una de las principales ventajas de usar el sombreador mrtk estándar sobre el sombreador estándar de Unity es el rendimiento. El sombreador estándar de MRTK es extensible para usar solo las características habilitadas. Sin embargo, el sombreador mrtk estándar también se ha escrito para ofrecer resultados éticos comparables como el sombreador estándar de Unity, pero con un costo mucho menor. Una manera sencilla de comparar el rendimiento del sombreador es a través del número de operaciones que se deben realizar en la GPU. Por supuesto, la magnitud de los cálculos puede fluctuar según las características habilitadas y otras configuraciones de representación. Pero, en general, el sombreador ESTÁNDAR DE MRTK realiza un cálculo significativamente menor que el sombreador Estándar de Unity.

Ejemplo de estadísticas de sombreador estándar de Unity

![Estadísticas de sombreador estándar de Unity](../images/performance/UnityStandardShader-Stats.PNG)

Ejemplo de estadísticas de sombreador estándar de MRTK

![Estadísticas de sombreador estándar de MRTK](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> Estos resultados se pueden generar seleccionando y viendo un recurso de [sombreador](https://docs.unity3d.com/Manual/class-Shader.html) en el inspector de Unity y, a continuación, haciendo clic en el *botón Compilar y mostrar* código.

## <a name="lighting"></a>Iluminación

MRTK/Standard usa una aproximación sencilla para la iluminación. Dado que este sombreador no calcula la corrección física y la conservación energética, se representa de forma rápida y eficaz. Blinn-Phong es la técnica de iluminación principal que se combina con Fresnel y la iluminación basada en imágenes para una iluminación aproximada basada en la física. El sombreador admite las siguientes técnicas de iluminación:

### <a name="directional-light"></a>Luz direccional

El sombreador respetará la dirección, el color y la intensidad de la primera luz direccional de Unity en la escena (si está habilitada). Las luces de punto dinámico, las luces de spot o cualquier otra luz de Unity no se tendrán en cuenta en la iluminación en tiempo real.

### <a name="spherical-harmonics"></a>Armónicos esféricos

El sombreador usará los sondeos de luz para aproximar las luces de la escena mediante [armónicas esféricas,](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)si está habilitada. Los cálculos de armónicos esféricos se realizan por vértice para reducir el costo de cálculo.

### <a name="lightmapping"></a>Lightmapping

En el caso de la iluminación estática, el sombreador respetará los mapas de luz creados por el [sistema lightmapping de](https://docs.unity3d.com/Manual/Lightmapping.html)Unity. Simplemente marque el representador como estático (o lightmap static) para usar mapas claros.

### <a name="hover-light"></a>Mantener el puntero sobre la luz

* Consulte [Hover Light (Mantener el puntero de la luz)](hover-light.md)

### <a name="proximity-light"></a>Luz de proximidad

* Consulte [Luz de proximidad.](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>Compatibilidad con la canalización de representación ligera que admite scripts

MRTK contiene una ruta de actualización que permite a los desarrolladores usar la canalización de representación ligera que admite scripts (LWRP) de Unity con sombreadores MRTK. Probado en unity 2019.1.1f1 y paquete ligero RP 5.7.2. o instrucciones sobre cómo empezar a trabajar con LWRP, consulte [esta página](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html).

Para realizar la actualización de MRTK, seleccione: Mixed Reality Toolkit **-> Utilities -> Upgrade MRTK Standard Shader for Lightweight Render Pipeline**

![actualización de lwrp](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

Después de que se produzca la actualización, se modificará el sombreador MRTK/Standard y se deben solucionar todos los materiales de shader (error de sombreador). Para comprobar que la actualización se ha realizado correctamente, compruebe la consola de: **Recursos actualizados/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader** para su uso con la canalización de representación ligera.

## <a name="ugui-support"></a>Compatibilidad con UGUI

El sistema de sombreado estándar de MRTK funciona con el sistema de interfaz de usuario [integrado de](https://docs.unity3d.com/Manual/UISystem.html)Unity. En los componentes de la interfaz de usuario de Unity, unity_ObjectToWorld matriz de transformación no es la matriz de transformación de la transformación local en la que reside el componente Gráfico, sino la de su lienzo primario. Muchos efectos de sombreador ESTÁNDAR/MRTK requieren que se conozca la escala de objetos. Para resolver este problema, almacenará información de escalado en atributos de canal UV durante la construcción de [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) la malla de interfaz de usuario.

Tenga en cuenta que, al usar un componente de imagen de Unity, se recomienda especificar "None (Sprite)" para la imagen de origen para evitar que la interfaz de usuario de Unity genere vértices adicionales.

Un lienzo dentro de MRTK solicitará la adición de un [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) elemento cuando se requiera uno:

![efecto de malla de escala](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>Combinador de textura

Para mejorar la paridad con el sombreador Estándar de Unity por píxel de píxel, los valores de suavizado, emisivo y oclusión se pueden controlar a través del [empaquetado del canal.](http://wiki.polycount.com/wiki/ChannelPacking) Por ejemplo:

![ejemplo de mapa de canal](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

Cuando se usa el empaquetado del canal, solo tiene que muestrear y cargar una textura en la memoria en lugar de cuatro independientes. Al escribir los mapas de textura en un programa como Insenso o Photoshop, puede empaquetarlos a mano de la siguiente manera:

| Canal | Propiedad             |
|---------|----------------------|
| Rojo     | Metálico             |
| Verde   | Oclusión            |
| Azul    | Emisión (escala gris) |
| Alpha   | Suavidad           |

O bien, puede usar la herramienta combinador de texturas MRTK. Para abrir la herramienta, seleccione: **Mixed Reality Toolkit -> Utilities -> Texture Combiner,** que abrirá la ventana siguiente:

![ejemplo de combinador de textura](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Esta ventana se puede rellenar automáticamente seleccionando un sombreador estándar de Unity y haciendo clic en "Rellenar automáticamente desde material estándar". O bien, puede especificar manualmente una textura (o un valor constante) por canal rojo, verde, azul o alfa. La combinación de textura está acelerada por GPU y no requiere que la textura de entrada sea accesible desde la CPU.

## <a name="additional-feature-documentation"></a>Documentación adicional sobre características

A continuación se muestran detalles adicionales sobre una serie de detalles de características disponibles con el sombreador MRTK/Standard.

### <a name="primitive-clipping"></a>Recorte primitivo

![recorte primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* Consulte [El primitivo de recorte](clipping-primitive.md)

### <a name="mesh-outlines"></a>Contornos de malla

Muchas técnicas de contorno de malla se realizan mediante una [técnica posterior al](https://docs.unity3d.com/Manual/PostProcessingOverview.html) procesamiento. El procesamiento posterior proporciona esquemas de gran calidad, pero puede ser prohibitivamente costoso en muchos Mixed Reality dispositivos. Puede encontrar una escena que muestra el uso de contornos de malla en la  **escena OutlineExamples** en `MRTK/Examples/Demos/StandardShader/Scenes/` .

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) y [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) se pueden usar para representar un contorno alrededor de un representador de malla. La habilitación de este componente presenta un paso de representación adicional del objeto que se describe, pero está diseñado para ejecutarse correctamente en dispositivos Mixed Reality móviles y no utiliza ningún proceso posterior. Entre las limitaciones de este efecto se incluyen que no funciona bien en objetos que no son herméticos (o que deben tener dos lados) y pueden producirse problemas de ordenación de profundidad en objetos superpuestos.

Los comportamientos de esquema están diseñados para usarse junto con el sombreador MRTK/Standard. Los materiales de contorno suelen ser un color sólido sin iluminación, pero se pueden configurar para lograr una amplia gama de efectos. La configuración predeterminada de un material de esquema es la siguiente:

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. Escritura en profundidad: debe deshabilitarse para los materiales de contorno para asegurarse de que el contorno no impide que se rescriba otro objeto.
2. Extrusión de vértices: debe habilitarse para representar el contorno.
3. Usar normales fluidas: esta configuración es opcional para algunas mallas. La extrusión se produce moviendo un vértice a lo largo de un vértice normal, en algunas mallas que se extruen a lo largo de las normales predeterminadas provocará discontinuidades en el contorno. Para corregir estas discontinuidades, puede marcar esta casilla para usar otro conjunto de normales suavizadas generadas por [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) es un componente que se puede usar para generar automáticamente normales suavizadas en una malla. Este método agrupa los vértices en una malla que comparten la misma ubicación en el espacio y, a continuación, promedia los valores normales de esos vértices. Este proceso crea una copia de la malla subyacente y solo se debe usar cuando sea necesario.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. Normales fluidas generadas a través de [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) .
2. Normales predeterminadas usadas, observe los artefactos alrededor de las esquinas del cubo.

### <a name="stencil-testing"></a>Pruebas de galería de símbolos

Compatibilidad integrada con pruebas de galería de símbolos configurables para lograr una amplia gama de efectos. Por ejemplo, los portales:

![prueba de galería de símbolos](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>Compatibilidad con colores con instancias

Compatibilidad de color con instancias para proporcionar a miles de mallas con instancias de GPU propiedades de material únicas:

![propiedades de instancia](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Asignación de Triplanar

La asignación triplanar es una técnica para texturar mediante programación una malla. A menudo se usa en terrenos, mallas sin UV o formas difíciles de desencapsular. Esta implementación admite la proyección de espacio global o local, la especificación de la subilidad de mezcla y la compatibilidad normal con mapas. Tenga en cuenta que cada textura usada requiere 3 muestras de textura, por lo que debe usar con moderación en situaciones críticas para el rendimiento.

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>Extrusión de vértices

Extrusión de vértices en el espacio mundial. Resulta útil para visualizar volúmenes de límite extruidos o transiciones dentro y fuera de mallas.

![escala de mapa normal 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>Varios

Casilla para controlar las optimizaciones de albedo. Como optimización, las operaciones albedo se deshabilitan cuando no se especifica ninguna textura albedo. Esto es útil para controlar la [carga de textura remota.](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)

Simplemente active esta casilla:

![Asignación de albedo](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

Se admiten texturas de recorte por píxel, suavizado de contorno basado en borde local y escalado de mapa normal.

![escala de mapa normal 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>Consulte también

* [Interactuable](../ux-building-blocks/interactable.md)
* [Luz de desplazamiento](hover-light.md)
* [Luz de proximidad](proximity-light.md)
* [Primitivo de recorte](clipping-primitive.md)
