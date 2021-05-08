---
title: TextPrefab
description: Información general de TextPrefab en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, TMP,
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489295"
---
# <a name="text-prefab"></a>Prefab de texto

Estos objetos prefab están optimizados para la calidad de representación en Windows Mixed Reality. Para obtener más información, lea la guía [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Centro de desarrollo de Windows(Texto en Unity en Microsoft Centro de desarrollo de Windows).

## <a name="prefabs"></a>Requisitos previos

### <a name="3dtextprefab"></a>3DTextPrefab

Prefab de Text Mesh 3D (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) con factor de escalado optimizado a una distancia de 2 metros. (Lea las instrucciones siguientes)

### <a name="uitextprefab"></a>UITextPrefab

Interfaz de usuario text mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) con factor de escalado optimizado a una distancia de 2 metros. (Lea las instrucciones siguientes)

## <a name="fonts"></a>Fuentes

Fuentes de código abierto (Assets/MRTK/Core/StandardAssets/Fonts) incluidas en Mixed Reality Toolkit.

> [!IMPORTANT]
> Text Prefab usa la fuente de código abierto 'Selawik'. Para usar Text Prefab con una fuente diferente, importe el archivo de fuente y siga las instrucciones siguientes. En el ejemplo siguiente se muestra cómo usar la fuente "Segoe UI" con Text Prefab.

![Importar un Segoe UI fuente](../images/text-prefab/TextPrefabInstructions01.png)

1. Asigne textura de fuente al material 3DTextScateeUI.mat.

    ![Asignación de textura de fuente](../images/text-prefab/TextPrefabInstructions02.png)

1. En el material 3DTextSeloUI.mat, seleccione el sombreador Custom/3DTextShader.shader.

    ![Asignación de sombreador](../images/text-prefab/TextPrefabInstructions03.png)

1. Asigne Segoe UI fuente y material 3DTextSbioeUI a los componentes de texto de los elementos prefabs.

    ![Asignación de material y archivo de fuente](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Trabajar con fuentes en Unity

Al agregar un nuevo TextMesh 3D a una escena en Unity, hay dos problemas que son visualmente evidentes. Una, la fuente parece muy grande y dos, la fuente aparece muy desenfoque. También es interesante observar que el valor predeterminado tamaño de fuente está establecido en cero en el inspector. Reemplazar este valor cero por 13 no mostrará ninguna diferencia en el tamaño, porque 13 es realmente el valor predeterminado.

Unity supone que todos los elementos nuevos agregados a una escena tienen un tamaño de 1 unidad de Unity o una escala de transformación del 100 %, lo que se traduce en aproximadamente un medidor en HoloLens. En el caso de las fuentes, se incluye el rectángulo de selección de un TextMesh 3D, de forma predeterminada con una altura de aproximadamente 1 metro.

### <a name="font-scale-and-font-sizes"></a>Escala de fuentes y tamaños de fuente

La mayoría de los diseñadores visuales usan puntos para definir tamaños de fuente en el mundo real, así como sus programas de diseño. Hay aproximadamente 2835 puntos (2834,645666399962) en 1 medidor. En función de la conversión del sistema de punto a 1 medidor y el tamaño de fuente TextMesh predeterminado de Unity de 13, la matemática simple de 13 dividida por 2835 equivale a 0,0046 (0,004586111116 para ser exactos) proporciona una buena escala estándar con la que empezar, aunque algunos pueden desear redondear a 0,005.

En cualquier caso, el escalado del objeto o contenedor Text a estos valores no solo permitirá la conversión 1:1 de los tamaños de fuente de un programa de diseño, sino que también proporciona un estándar para mantener la coherencia en toda la aplicación o juego.

### <a name="ui-text"></a>Texto de interfaz de usuario

Al agregar una interfaz de usuario o un elemento Text basado en lienzo a una escena, la disparidad de tamaño sigue siendo mayor. Las diferencias en los dos tamaños son aproximadamente del 1000 %, lo que haría que el factor de escala de los componentes de texto basados en la interfaz de usuario llegara a 0,00046 (0,000458611116 para ser exactos) o 0,0005 para el valor redondeado.

**Declinación** de responsabilidades: el valor predeterminado de cualquier fuente puede afectar al tamaño de textura de esa fuente o a cómo se importó la fuente en Unity. Estas pruebas se realizaron en función de la fuente de Arial predeterminada en Unity, así como de otra fuente importada.

![Tamaño de fuente con factores de escalado](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik.mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

Material para 3DTextPrefab con compatibilidad con oclusión. Requiere 3DTextShader.shader

![Material de fuente predeterminado frente a material 3DTextScateeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader.shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

Sombreador para 3DTextPrefab con compatibilidad con oclusión.