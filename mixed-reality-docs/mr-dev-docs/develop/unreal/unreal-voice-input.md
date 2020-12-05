---
title: Entrada de voz
description: Tutorial sobre la configuración y el uso de la entrada de voz en HoloLens 2 e inreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, inreal, no real, motor 4, UE4, HoloLens 2, voz, entrada de voz, reconocimiento de voz, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 504a2d978e3c9bc698e8edd11ea8a4d6be13795a
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609756"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="11974-104">Entrada de voz en inreal</span><span class="sxs-lookup"><span data-stu-id="11974-104">Voice Input in Unreal</span></span>

<span data-ttu-id="11974-105">La entrada de voz en no real permite interactuar con un holograma sin tener que usar gestos de mano y solo es compatible con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="11974-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="11974-106">La entrada de voz en HoloLens 2 se basa en el mismo motor que admite la voz en todas las demás aplicaciones universales de Windows, pero no real usa un motor más limitado para procesar la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="11974-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="11974-107">Esto limita las características de entrada de voz en no real a las asignaciones de voz predefinidas, que se describen en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="11974-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="11974-108">Habilitación del reconocimiento de voz</span><span class="sxs-lookup"><span data-stu-id="11974-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="11974-109">Para habilitar el reconocimiento de voz en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="11974-109">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="11974-110">Seleccione **configuración del proyecto > plataforma > HoloLens > funcionalidades** y habilite el **micrófono**.</span><span class="sxs-lookup"><span data-stu-id="11974-110">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="11974-111">Habilitado el reconocimiento de voz en **configuración > privacidad > voz** y seleccione **Inglés**.</span><span class="sxs-lookup"><span data-stu-id="11974-111">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="11974-112">El reconocimiento de voz siempre funciona en el idioma de visualización de Windows configurado en la aplicación de **configuración** .</span><span class="sxs-lookup"><span data-stu-id="11974-112">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="11974-113">Se recomienda habilitar también el reconocimiento de **voz en línea** para obtener la mejor calidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="11974-113">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Configuración del reconocimiento de voz de Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="11974-115">Se mostrará un cuadro de diálogo cuando se inicie la aplicación por primera vez para preguntar si desea habilitar el micrófono.</span><span class="sxs-lookup"><span data-stu-id="11974-115">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="11974-116">Si selecciona **sí** , se iniciará la entrada de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="11974-116">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="11974-117">La entrada de voz no requiere ninguna API especial de Windows Mixed Reality; se basa en la API de asignación de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) de Engine 4 inreal Engine existente.</span><span class="sxs-lookup"><span data-stu-id="11974-117">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="11974-118">Agregar asignaciones de voz</span><span class="sxs-lookup"><span data-stu-id="11974-118">Adding Speech Mappings</span></span>

<span data-ttu-id="11974-119">La conexión de voz a la acción es un paso importante cuando se usa la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="11974-119">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="11974-120">Estas asignaciones supervisan las palabras clave de la aplicación para la voz que un usuario podría decir y, a continuación, activa una acción vinculada.</span><span class="sxs-lookup"><span data-stu-id="11974-120">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="11974-121">Puede buscar las asignaciones de voz:</span><span class="sxs-lookup"><span data-stu-id="11974-121">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="11974-122">Seleccione **editar > configuración del proyecto**, desplácese hasta la sección **motor** y haga clic en **entrada**.</span><span class="sxs-lookup"><span data-stu-id="11974-122">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="11974-123">Para agregar una nueva asignación de voz para un comando de salto:</span><span class="sxs-lookup"><span data-stu-id="11974-123">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="11974-124">Seleccione el **+** icono situado junto a **elementos** de la matriz y rellene los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="11974-124">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="11974-125">**jumpWord** para **el nombre de acción**</span><span class="sxs-lookup"><span data-stu-id="11974-125">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="11974-126">**saltar** la **palabra clave de voz**</span><span class="sxs-lookup"><span data-stu-id="11974-126">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="11974-127">Cualquier palabra o frase en inglés (s) se puede usar como palabra clave.</span><span class="sxs-lookup"><span data-stu-id="11974-127">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Configuración de entrada del motor de UE4](images/unreal/engine-input.png)

<span data-ttu-id="11974-129">Las asignaciones de voz se pueden usar como componentes de entrada como asignaciones de acción o de eje o como nodos de plano en el gráfico de eventos.</span><span class="sxs-lookup"><span data-stu-id="11974-129">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="11974-130">Por ejemplo, puede vincular el comando de salto para imprimir dos registros diferentes en función de Cuándo se pronuncia la palabra:</span><span class="sxs-lookup"><span data-stu-id="11974-130">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="11974-131">Haga doble clic en un plano para abrirlo en el **gráfico de eventos**.</span><span class="sxs-lookup"><span data-stu-id="11974-131">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="11974-132">**Haga clic con el botón derecho** y busque el nombre de la **acción** de la asignación de voz (en este caso, **jumpWord**) y presione **entrar** para agregar un nodo de **acción de entrada** al gráfico.</span><span class="sxs-lookup"><span data-stu-id="11974-132">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="11974-133">Arrastre y coloque el anclaje **presionado** en el nodo de la **cadena de impresión** , tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="11974-133">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="11974-134">Puede dejar el PIN **liberado** vacío, no ejecutará nada para las asignaciones de voz.</span><span class="sxs-lookup"><span data-stu-id="11974-134">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Acción simple para voz](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="11974-136">Juegue a la aplicación, por ejemplo, la palabra **Jump** y observe que la consola imprime los registros.</span><span class="sxs-lookup"><span data-stu-id="11974-136">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="11974-137">Esta es toda la configuración que necesitará para empezar a agregar entradas de voz a las aplicaciones de HoloLens en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="11974-137">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="11974-138">Puede encontrar más información sobre la voz y la interactividad en los vínculos siguientes y asegúrese de pensar en la experiencia que está creando para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="11974-138">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="11974-139">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="11974-139">Next Development Checkpoint</span></span>

<span data-ttu-id="11974-140">Si está siguiendo el viaje de desarrollo no real que hemos diseñado, la tarea siguiente está explorando las funcionalidades y API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="11974-140">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="11974-141">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="11974-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="11974-142">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="11974-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="11974-143">Consulta también</span><span class="sxs-lookup"><span data-stu-id="11974-143">See also</span></span>
* [<span data-ttu-id="11974-144">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="11974-144">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="11974-145">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="11974-145">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="11974-146">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="11974-146">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

