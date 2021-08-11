---
title: Visualización de comentarios de Azure Spatial Anchors
description: Siga este curso para aprender a mostrar comentarios de Azure Spatial Anchors en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, sessions, feedback elements
ms.localizationpriority: high
ms.openlocfilehash: 65a814019909ecacffdd454171075c68497dae1b2123804e07ced1d7e100fdd8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215676"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Visualización de comentarios de Azure Spatial Anchors

En este tutorial, aprenderá a proporcionar a los usuarios comentarios sobre la detección, los eventos y los estados de anclaje al usar Azure Spatial Anchors (ASA).

## <a name="objectives"></a>Objetivos

* Aprender a configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA
* Conocer y explorar los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios

## <a name="setting-up-asa-feedback-panel"></a>Configurar el panel de comentarios de ASA

En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **Instructions** (Instrucciones)  > **TextContent**. Seleccione **Objeto 3D** > **Text - TextMeshPro** (Texto: TextMeshPro) para crear un objeto de texto TextMeshPro como elemento secundario del objeto Instructions (Instrucciones) > TextContent:

![Unity con el objeto TextMeshPro recién creado seleccionado](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> Para que resulte más fácil trabajar con la escena, define <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Visibilidad de la escena) como desactivada para el objeto ParentAnchor haciendo clic en el icono de ojo situado a la izquierda del objeto. Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego.

Cambie el nombre del objeto **Feedback** (Comentarios) del texto recién creado (TMP) y, luego, en la ventana Inspector, cambie su posición y tamaño para que se coloque estratégicamente bajo el texto de instrucción; por ejemplo:

* Cambie el valor **Pos Y** (Posición Y) del componente de transformación de rectángulo a -0,24.
* Cambie el valor **Width** (Ancho) del componente de transformación de rectángulo a 0,555.
* Cambie el valor **Height** (Altura) del componente de transformación de rectángulo a 0,1.

A continuación, elija las propiedades de la fuente para que el texto encaje bien dentro del área de texto; por ejemplo:

* Cambie el **estilo de fuente** del componente TextMeshPro - Text ( TextMeshPro: texto) a Bold (Negrita).
* Cambie el **tamaño de fuente** del componente TextMeshPro - Text (TextMeshPro: texto) a 0,17.
* Cambie la **alineación** del componente TextMeshPro - Text (TextMeshPro: texto) a Center (Centro) y Middle (Medio).

![Unity con el objeto Feedback (Comentarios) configurado](images/mr-learning-asa/asa-04-section1-step1-2.png)

En la ventana Hierarchy (Jerarquía), seleccione el objeto **Feedback** (Comentarios) y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]) y configúrelo del modo siguiente:

* Asigne el objeto **Feedback** (Comentarios) al campo **Feedback Text** (Texto de comentarios) del componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]).

![Unity con el componente Anchor Feedback Script (Script de comentarios de anclaje) configurado](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a crear un panel de interfaz de usuario. Este muestra el estado actual de la experiencia de  Azure Spatial Anchors para proporcionar a los usuarios comentarios en tiempo real.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 5. Azure Spatial Anchors para iOS y Android](mr-learning-asa-05.md)
