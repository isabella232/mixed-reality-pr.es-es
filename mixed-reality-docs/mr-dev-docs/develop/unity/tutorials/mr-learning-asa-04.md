---
title: Visualización de comentarios de Azure Spatial Anchors
description: Siga este curso para aprender a mostrar comentarios de Azure Spatial Anchors en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, sessions, feedback elements
ms.localizationpriority: high
ms.openlocfilehash: f5f92d8b19da6a449b8630d7f87e0719e438b4ab
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590677"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="c1395-104">4. Visualización de comentarios de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c1395-104">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="c1395-105">En este tutorial, aprenderá a proporcionar a los usuarios comentarios sobre la detección, los eventos y los estados de anclaje al usar Azure Spatial Anchors (ASA).</span><span class="sxs-lookup"><span data-stu-id="c1395-105">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="c1395-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c1395-106">Objectives</span></span>

* <span data-ttu-id="c1395-107">Aprender a configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA</span><span class="sxs-lookup"><span data-stu-id="c1395-107">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="c1395-108">Conocer y explorar los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios</span><span class="sxs-lookup"><span data-stu-id="c1395-108">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="c1395-109">Configurar el panel de comentarios de ASA</span><span class="sxs-lookup"><span data-stu-id="c1395-109">Setting up ASA feedback panel</span></span>

<span data-ttu-id="c1395-110">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **Instructions** (Instrucciones)  > **TextContent**.</span><span class="sxs-lookup"><span data-stu-id="c1395-110">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="c1395-111">Seleccione **Objeto 3D** > **Text - TextMeshPro** (Texto: TextMeshPro) para crear un objeto de texto TextMeshPro como elemento secundario del objeto Instructions (Instrucciones) > TextContent:</span><span class="sxs-lookup"><span data-stu-id="c1395-111">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![Unity con el objeto TextMeshPro recién creado seleccionado](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="c1395-113">Para que resulte más fácil trabajar con la escena, define <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Visibilidad de la escena) como desactivada para el objeto ParentAnchor haciendo clic en el icono de ojo situado a la izquierda del objeto.</span><span class="sxs-lookup"><span data-stu-id="c1395-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="c1395-114">Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego.</span><span class="sxs-lookup"><span data-stu-id="c1395-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="c1395-115">Cambie el nombre del objeto **Feedback** (Comentarios) del texto recién creado (TMP) y, luego, en la ventana Inspector, cambie su posición y tamaño para que se coloque estratégicamente bajo el texto de instrucción; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c1395-115">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="c1395-116">Cambie el valor **Pos Y** (Posición Y) del componente de transformación de rectángulo a -0,24.</span><span class="sxs-lookup"><span data-stu-id="c1395-116">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="c1395-117">Cambie el valor **Width** (Ancho) del componente de transformación de rectángulo a 0,555.</span><span class="sxs-lookup"><span data-stu-id="c1395-117">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="c1395-118">Cambie el valor **Height** (Altura) del componente de transformación de rectángulo a 0,1.</span><span class="sxs-lookup"><span data-stu-id="c1395-118">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="c1395-119">A continuación, elija las propiedades de la fuente para que el texto encaje bien dentro del área de texto; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c1395-119">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="c1395-120">Cambie el **estilo de fuente** del componente TextMeshPro - Text ( TextMeshPro: texto) a Bold (Negrita).</span><span class="sxs-lookup"><span data-stu-id="c1395-120">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="c1395-121">Cambie el **tamaño de fuente** del componente TextMeshPro - Text (TextMeshPro: texto) a 0,17.</span><span class="sxs-lookup"><span data-stu-id="c1395-121">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="c1395-122">Cambie la **alineación** del componente TextMeshPro - Text (TextMeshPro: texto) a Center (Centro) y Middle (Medio).</span><span class="sxs-lookup"><span data-stu-id="c1395-122">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![Unity con el objeto Feedback (Comentarios) configurado](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="c1395-124">En la ventana Hierarchy (Jerarquía), seleccione el objeto **Feedback** (Comentarios) y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]) y configúrelo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c1395-124">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="c1395-125">Asigne el objeto **Feedback** (Comentarios) al campo **Feedback Text** (Texto de comentarios) del componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]).</span><span class="sxs-lookup"><span data-stu-id="c1395-125">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![Unity con el componente Anchor Feedback Script (Script de comentarios de anclaje) configurado](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="c1395-127">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="c1395-127">Congratulations</span></span>

<span data-ttu-id="c1395-128">En este tutorial, ha aprendido a crear un panel de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="c1395-128">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="c1395-129">Este muestra el estado actual de la experiencia de  Azure Spatial Anchors para proporcionar a los usuarios comentarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="c1395-129">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1395-130">Tutorial siguiente: 5. Azure Spatial Anchors para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="c1395-130">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
