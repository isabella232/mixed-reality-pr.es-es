---
title: Adición del componente Speech Translation de Azure Cognitive Services
description: En este curso, aprenderá a agregar la traducción de voz de Azure Cognitive Services en aplicaciones de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, speech recognition, Windows 10, speech translation
ms.localizationpriority: high
ms.openlocfilehash: bcc966b63f4c3e5bb9e6d6a38dc7f0312b288402
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590147"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="2585c-104">3. Adición del componente Speech Translation de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="2585c-104">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="2585c-105">En este tutorial, agregarás traducción de voz al proyecto, lo que te permitirá traducir y transcribir la voz en tres idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="2585c-105">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="2585c-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2585c-106">Objectives</span></span>

* <span data-ttu-id="2585c-107">Aprender a integrar la traducción de voz de Azure</span><span class="sxs-lookup"><span data-stu-id="2585c-107">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="2585c-108">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="2585c-108">Instructions</span></span>

<span data-ttu-id="2585c-109">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Translation Recognizer (Script)** (Reconocimiento de traducción de Lunarcom [script]) al objeto Lunarcom y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="2585c-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="2585c-110">Cambia **Target Language** (Idioma de destino) al idioma que quieras; por ejemplo, _German_ (Alemán).</span><span class="sxs-lookup"><span data-stu-id="2585c-110">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2585c-112">El componente Lunarcom Translation Recognizer (Script) (Reconocimiento de traducción de Lunarcom [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2585c-112">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="2585c-113">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="2585c-113">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="2585c-114">Si ahora entras en el modo de juego, puedes probar la traducción de voz presionando primero el botón del satélite:</span><span class="sxs-lookup"><span data-stu-id="2585c-114">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="2585c-115">A continuación, suponiendo que el equipo tiene un micrófono, cuando digas algo, la voz se traducirá al idioma seleccionado y se transcribirá en el panel del terminal:</span><span class="sxs-lookup"><span data-stu-id="2585c-115">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="2585c-117">La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="2585c-117">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2585c-118">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2585c-118">Congratulations</span></span>

<span data-ttu-id="2585c-119">Ahora, el proyecto puede traducir correctamente las palabras que digas en varios idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="2585c-119">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="2585c-120">Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="2585c-120">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2585c-121">Tutorial siguiente: 4. Configuración de reconocimiento de intenciones y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="2585c-121">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
