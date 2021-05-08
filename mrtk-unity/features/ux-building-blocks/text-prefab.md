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
# <a name="text-prefab"></a><span data-ttu-id="d6a2a-104">Prefab de texto</span><span class="sxs-lookup"><span data-stu-id="d6a2a-104">Text prefab</span></span>

<span data-ttu-id="d6a2a-105">Estos objetos prefab están optimizados para la calidad de representación en Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="d6a2a-106">Para obtener más información, lea la guía [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Centro de desarrollo de Windows(Texto en Unity en Microsoft Centro de desarrollo de Windows).</span><span class="sxs-lookup"><span data-stu-id="d6a2a-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="d6a2a-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="d6a2a-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="d6a2a-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="d6a2a-108">3DTextPrefab</span></span>

<span data-ttu-id="d6a2a-109">Prefab de Text Mesh 3D (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) con factor de escalado optimizado a una distancia de 2 metros.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="d6a2a-110">(Lea las instrucciones siguientes)</span><span class="sxs-lookup"><span data-stu-id="d6a2a-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="d6a2a-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="d6a2a-111">UITextPrefab</span></span>

<span data-ttu-id="d6a2a-112">Interfaz de usuario text mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) con factor de escalado optimizado a una distancia de 2 metros.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="d6a2a-113">(Lea las instrucciones siguientes)</span><span class="sxs-lookup"><span data-stu-id="d6a2a-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="d6a2a-114">Fuentes</span><span class="sxs-lookup"><span data-stu-id="d6a2a-114">Fonts</span></span>

<span data-ttu-id="d6a2a-115">Fuentes de código abierto (Assets/MRTK/Core/StandardAssets/Fonts) incluidas en Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6a2a-116">Text Prefab usa la fuente de código abierto 'Selawik'.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="d6a2a-117">Para usar Text Prefab con una fuente diferente, importe el archivo de fuente y siga las instrucciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="d6a2a-118">En el ejemplo siguiente se muestra cómo usar la fuente "Segoe UI" con Text Prefab.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![Importar un Segoe UI fuente](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="d6a2a-120">Asigne textura de fuente al material 3DTextScateeUI.mat.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![Asignación de textura de fuente](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="d6a2a-122">En el material 3DTextSeloUI.mat, seleccione el sombreador Custom/3DTextShader.shader.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![Asignación de sombreador](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="d6a2a-124">Asigne Segoe UI fuente y material 3DTextSbioeUI a los componentes de texto de los elementos prefabs.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![Asignación de material y archivo de fuente](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="d6a2a-126">Trabajar con fuentes en Unity</span><span class="sxs-lookup"><span data-stu-id="d6a2a-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="d6a2a-127">Al agregar un nuevo TextMesh 3D a una escena en Unity, hay dos problemas que son visualmente evidentes.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="d6a2a-128">Una, la fuente parece muy grande y dos, la fuente aparece muy desenfoque.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="d6a2a-129">También es interesante observar que el valor predeterminado tamaño de fuente está establecido en cero en el inspector.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="d6a2a-130">Reemplazar este valor cero por 13 no mostrará ninguna diferencia en el tamaño, porque 13 es realmente el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="d6a2a-131">Unity supone que todos los elementos nuevos agregados a una escena tienen un tamaño de 1 unidad de Unity o una escala de transformación del 100 %, lo que se traduce en aproximadamente un medidor en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="d6a2a-132">En el caso de las fuentes, se incluye el rectángulo de selección de un TextMesh 3D, de forma predeterminada con una altura de aproximadamente 1 metro.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="d6a2a-133">Escala de fuentes y tamaños de fuente</span><span class="sxs-lookup"><span data-stu-id="d6a2a-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="d6a2a-134">La mayoría de los diseñadores visuales usan puntos para definir tamaños de fuente en el mundo real, así como sus programas de diseño.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="d6a2a-135">Hay aproximadamente 2835 puntos (2834,645666399962) en 1 medidor.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="d6a2a-136">En función de la conversión del sistema de punto a 1 medidor y el tamaño de fuente TextMesh predeterminado de Unity de 13, la matemática simple de 13 dividida por 2835 equivale a 0,0046 (0,004586111116 para ser exactos) proporciona una buena escala estándar con la que empezar, aunque algunos pueden desear redondear a 0,005.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="d6a2a-137">En cualquier caso, el escalado del objeto o contenedor Text a estos valores no solo permitirá la conversión 1:1 de los tamaños de fuente de un programa de diseño, sino que también proporciona un estándar para mantener la coherencia en toda la aplicación o juego.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="d6a2a-138">Texto de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="d6a2a-138">UI Text</span></span>

<span data-ttu-id="d6a2a-139">Al agregar una interfaz de usuario o un elemento Text basado en lienzo a una escena, la disparidad de tamaño sigue siendo mayor.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="d6a2a-140">Las diferencias en los dos tamaños son aproximadamente del 1000 %, lo que haría que el factor de escala de los componentes de texto basados en la interfaz de usuario llegara a 0,00046 (0,000458611116 para ser exactos) o 0,0005 para el valor redondeado.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="d6a2a-141">**Declinación** de responsabilidades: el valor predeterminado de cualquier fuente puede afectar al tamaño de textura de esa fuente o a cómo se importó la fuente en Unity.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="d6a2a-142">Estas pruebas se realizaron en función de la fuente de Arial predeterminada en Unity, así como de otra fuente importada.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![Tamaño de fuente con factores de escalado](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="d6a2a-144">Text3DSelawik.mat</span><span class="sxs-lookup"><span data-stu-id="d6a2a-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="d6a2a-145">Material para 3DTextPrefab con compatibilidad con oclusión.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="d6a2a-146">Requiere 3DTextShader.shader</span><span class="sxs-lookup"><span data-stu-id="d6a2a-146">Requires 3DTextShader.shader</span></span>

![Material de fuente predeterminado frente a material 3DTextScateeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="d6a2a-148">Text3DShader.shader</span><span class="sxs-lookup"><span data-stu-id="d6a2a-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="d6a2a-149">Sombreador para 3DTextPrefab con compatibilidad con oclusión.</span><span class="sxs-lookup"><span data-stu-id="d6a2a-149">Shader for 3DTextPrefab with occlusion support.</span></span>