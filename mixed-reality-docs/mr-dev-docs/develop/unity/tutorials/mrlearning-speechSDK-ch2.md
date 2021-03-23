---
title: Adición de un modo sin conexión para la traducción de voz a texto local
description: Complete este curso para aprender a agregar el modo sin conexión para la traducción de voz a texto local en aplicaciones de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, speech recognition, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 2e7a48dc4bb64eb177e6fa290f4918345c3d642f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590157"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="2cc72-104">2. Adición de un modo sin conexión para la traducción de voz a texto local</span><span class="sxs-lookup"><span data-stu-id="2cc72-104">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="2cc72-105">En este tutorial, agregarás la posibilidad de ejecutar comandos con el reconocimiento de voz de Azure, lo que te permitirá hacer que pase algo en función de la palabra o frase que definas.</span><span class="sxs-lookup"><span data-stu-id="2cc72-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="2cc72-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2cc72-106">Objectives</span></span>

* <span data-ttu-id="2cc72-107">Aprender a usar el reconocimiento de voz de Azure para ejecutar comandos</span><span class="sxs-lookup"><span data-stu-id="2cc72-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="2cc72-108">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="2cc72-108">Instructions</span></span>

<span data-ttu-id="2cc72-109">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Wake Word Recognizer (Script)** (Reconocimiento de la palabra de activación de Lunarcom [script]) al objeto Lunarcom y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="2cc72-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="2cc72-110">En el campo **Wake Word** (Palabra de activación), escribe una frase adecuada; por ejemplo, _Activate terminal_ (Activar terminal).</span><span class="sxs-lookup"><span data-stu-id="2cc72-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="2cc72-111">En el campo **Dismiss Word** (Palabra de descarte), escribe una frase adecuada; por ejemplo, _Dismiss terminal_ (Descartar terminal).</span><span class="sxs-lookup"><span data-stu-id="2cc72-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Editor de Unity con el componente Wake Word Recognizer (Script) (Reconocimiento de palabra de activación [script])](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2cc72-113">El componente Wake Word Recognizer (Script) (Reconocimiento de palabra de activación [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2cc72-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="2cc72-114">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="2cc72-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="2cc72-115">Si ahora entras en el modo de juego, como en el tutorial anterior, el panel del terminal está habilitado de forma predeterminada, pero puedes deshabilitarlo diciendo la palabra de descarte: **Dismiss terminal** (Descartar terminal):</span><span class="sxs-lookup"><span data-stu-id="2cc72-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![Editor de Unity en modo de reproducción con la característica de reconocedor de voz en uso](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="2cc72-117">Para volver a habilitarlo, indica la palabra de activación **Activate terminal** (Activar terminal):</span><span class="sxs-lookup"><span data-stu-id="2cc72-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![Editor de Unity en modo de reproducción con el terminal activo](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="2cc72-119">La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="2cc72-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="2cc72-120">Si prevé que no podrá conectarse a Azure con frecuencia, también puede implementar comandos de voz mediante MRTK, para lo que debe seguir las instrucciones de [Uso de comandos de voz](mr-learning-base-09.md).</span><span class="sxs-lookup"><span data-stu-id="2cc72-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2cc72-121">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2cc72-121">Congratulations</span></span>

<span data-ttu-id="2cc72-122">Has implementado comandos de voz con tecnología de Azure.</span><span class="sxs-lookup"><span data-stu-id="2cc72-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="2cc72-123">Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="2cc72-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="2cc72-124">En el próximo tutorial, aprenderás a traducir la voz mediante la traducción de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="2cc72-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2cc72-125">Tutorial siguiente: 3. Adición del componente de traducción de voz de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="2cc72-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
