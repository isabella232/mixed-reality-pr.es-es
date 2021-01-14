---
title: Entrada de voz en inreal
description: Obtenga información sobre cómo configurar y usar la entrada de voz, las asignaciones de voz y el reconocimiento en aplicaciones de realidad mixta no reales para dispositivos HoloLens 2.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, inreal, no real, motor 4, UE4, HoloLens 2, voz, entrada de voz, reconocimiento de voz, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 466b41c522e95f9fe3d618ad221dde8ccd925634
ms.sourcegitcommit: a688bf0f1b796e4860f8252e852be79053937088
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205840"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="d542a-104">Entrada de voz en inreal</span><span class="sxs-lookup"><span data-stu-id="d542a-104">Voice Input in Unreal</span></span>

<span data-ttu-id="d542a-105">La entrada de voz en no real permite interactuar con un holograma sin tener que usar gestos de mano y solo es compatible con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d542a-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="d542a-106">La entrada de voz en HoloLens 2 se basa en el mismo motor que admite la voz en todas las demás aplicaciones universales de Windows, pero no real usa un motor más limitado para procesar la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="d542a-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="d542a-107">Esto limita las características de entrada de voz en no real a las asignaciones de voz predefinidas, que se describen en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="d542a-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="d542a-108">Habilitación del reconocimiento de voz</span><span class="sxs-lookup"><span data-stu-id="d542a-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="d542a-109">Si usa el complemento de Windows Mixed Reality, la entrada de voz no requiere ninguna API especial de Windows Mixed Reality; se basa en la API de asignación de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) de Engine 4 inreal Engine existente.</span><span class="sxs-lookup"><span data-stu-id="d542a-109">If you use Windows Mixed Reality Plugin, Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> <span data-ttu-id="d542a-110">Si usa OpenXR, debe instalar Adicionalmente el [complemento de Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="d542a-110">If you use OpenXR, you should additionally install [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="d542a-111">Para habilitar el reconocimiento de voz en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="d542a-111">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="d542a-112">Seleccione **configuración del proyecto > plataforma > HoloLens > funcionalidades** y habilite el **micrófono**.</span><span class="sxs-lookup"><span data-stu-id="d542a-112">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="d542a-113">Habilitado el reconocimiento de voz en **configuración > privacidad > voz** y seleccione **Inglés**.</span><span class="sxs-lookup"><span data-stu-id="d542a-113">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="d542a-114">El reconocimiento de voz siempre funciona en el idioma de visualización de Windows configurado en la aplicación de **configuración** .</span><span class="sxs-lookup"><span data-stu-id="d542a-114">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="d542a-115">Se recomienda habilitar también el reconocimiento de **voz en línea** para obtener la mejor calidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="d542a-115">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Configuración del reconocimiento de voz de Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="d542a-117">Se mostrará un cuadro de diálogo cuando se inicie la aplicación por primera vez para preguntar si desea habilitar el micrófono.</span><span class="sxs-lookup"><span data-stu-id="d542a-117">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="d542a-118">Si selecciona **sí** , se iniciará la entrada de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d542a-118">Selecting **Yes** starts voice input in the app.</span></span>

## <a name="adding-speech-mappings"></a><span data-ttu-id="d542a-119">Agregar asignaciones de voz</span><span class="sxs-lookup"><span data-stu-id="d542a-119">Adding Speech Mappings</span></span>

<span data-ttu-id="d542a-120">La conexión de voz a la acción es un paso importante cuando se usa la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="d542a-120">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="d542a-121">Estas asignaciones supervisan las palabras clave de la aplicación para la voz que un usuario podría decir y, a continuación, activa una acción vinculada.</span><span class="sxs-lookup"><span data-stu-id="d542a-121">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="d542a-122">Puede buscar las asignaciones de voz:</span><span class="sxs-lookup"><span data-stu-id="d542a-122">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="d542a-123">Seleccione **editar > configuración del proyecto**, desplácese hasta la sección **motor** y haga clic en **entrada**.</span><span class="sxs-lookup"><span data-stu-id="d542a-123">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="d542a-124">Para agregar una nueva asignación de voz para un comando de salto:</span><span class="sxs-lookup"><span data-stu-id="d542a-124">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="d542a-125">Seleccione el **+** icono situado junto a **elementos** de la matriz y rellene los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="d542a-125">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="d542a-126">**jumpWord** para **el nombre de acción**</span><span class="sxs-lookup"><span data-stu-id="d542a-126">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="d542a-127">**saltar** la **palabra clave de voz**</span><span class="sxs-lookup"><span data-stu-id="d542a-127">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="d542a-128">Cualquier palabra o frase en inglés (s) se puede usar como palabra clave.</span><span class="sxs-lookup"><span data-stu-id="d542a-128">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Configuración de entrada del motor de UE4](images/unreal/engine-input.png)

<span data-ttu-id="d542a-130">Las asignaciones de voz se pueden usar como componentes de entrada como asignaciones de acción o de eje o como nodos de plano en el gráfico de eventos.</span><span class="sxs-lookup"><span data-stu-id="d542a-130">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="d542a-131">Por ejemplo, puede vincular el comando de salto para imprimir dos registros diferentes en función de Cuándo se pronuncia la palabra:</span><span class="sxs-lookup"><span data-stu-id="d542a-131">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="d542a-132">Haga doble clic en un plano para abrirlo en el **gráfico de eventos**.</span><span class="sxs-lookup"><span data-stu-id="d542a-132">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="d542a-133">**Haga clic con el botón derecho** y busque el nombre de la **acción** de la asignación de voz (en este caso, **jumpWord**) y presione **entrar** para agregar un nodo de **acción de entrada** al gráfico.</span><span class="sxs-lookup"><span data-stu-id="d542a-133">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="d542a-134">Arrastre y coloque el anclaje **presionado** en el nodo de la **cadena de impresión** , tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="d542a-134">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="d542a-135">Puede dejar el PIN **liberado** vacío, no ejecutará nada para las asignaciones de voz.</span><span class="sxs-lookup"><span data-stu-id="d542a-135">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Acción simple para voz](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="d542a-137">Juegue a la aplicación, por ejemplo, la palabra **Jump** y observe que la consola imprime los registros.</span><span class="sxs-lookup"><span data-stu-id="d542a-137">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="d542a-138">Esta es toda la configuración que necesitará para empezar a agregar entradas de voz a las aplicaciones de HoloLens en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="d542a-138">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="d542a-139">Puede encontrar más información sobre la voz y la interactividad en los vínculos siguientes y asegúrese de pensar en la experiencia que está creando para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="d542a-139">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d542a-140">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="d542a-140">Next Development Checkpoint</span></span>

<span data-ttu-id="d542a-141">Si está siguiendo el viaje de desarrollo no real que hemos diseñado, la tarea siguiente está explorando las funcionalidades y API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="d542a-141">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="d542a-142">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="d542a-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="d542a-143">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="d542a-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d542a-144">Consulta también</span><span class="sxs-lookup"><span data-stu-id="d542a-144">See also</span></span>
* [<span data-ttu-id="d542a-145">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="d542a-145">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="d542a-146">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="d542a-146">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="d542a-147">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="d542a-147">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

