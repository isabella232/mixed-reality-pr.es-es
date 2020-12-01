---
title: UMG y teclado en no real
description: Obtenga información sobre cómo usar gráficos de movimiento sin territorio para crear un sistema de interfaz de usuario fuera de los widgets.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, widgets, interfaz de usuario, UMG, gráficos de movimiento inreal, no real Engine, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355405"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="60d34-104">UMG y teclado en no real</span><span class="sxs-lookup"><span data-stu-id="60d34-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="60d34-105">No real Motion Graphics (UMG) es un sistema de interfaz de usuario integrado del motor, que se usa para crear interfaces como menús y cuadros de texto.</span><span class="sxs-lookup"><span data-stu-id="60d34-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="60d34-106">Las interfaces de usuario compiladas con UMG se componen de widgets.</span><span class="sxs-lookup"><span data-stu-id="60d34-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="60d34-107">En esta guía se muestra cómo crear un nuevo widget, agregarlo a un espacio universal y habilitar la interacción con ese widget en realidad mixta, mediante el teclado del sistema como ejemplo.</span><span class="sxs-lookup"><span data-stu-id="60d34-107">This guide will show you how to create a new widget, add it to world space, and enable interaction with that widget in mixed reality, using the system keyboard as an example.</span></span> <span data-ttu-id="60d34-108">Puede obtener más información sobre UMG en la [documentación](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)oficial del motor no real.</span><span class="sxs-lookup"><span data-stu-id="60d34-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="60d34-109">Crear un nuevo widget</span><span class="sxs-lookup"><span data-stu-id="60d34-109">Create a new widget</span></span>

- <span data-ttu-id="60d34-110">Cree un Blueprint de widget para diseñar la interfaz de usuario del juego:</span><span class="sxs-lookup"><span data-stu-id="60d34-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Captura de pantalla de la adición de un Blueprint de widget desde el menú no real](images/unreal-umg-img-01.png)

- <span data-ttu-id="60d34-112">Abra el nuevo plano y agregue componentes de la paleta al lienzo.</span><span class="sxs-lookup"><span data-stu-id="60d34-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="60d34-113">En este caso, hemos agregado dos componentes de cuadro de texto de la sección "entrada":</span><span class="sxs-lookup"><span data-stu-id="60d34-113">In this case we have added two Text Box components from the “Input” section:</span></span>

![Captura de pantalla de la ventana de jerarquía con el componente widget de texto resaltado y expandido](images/unreal-umg-img-02.png)

- <span data-ttu-id="60d34-115">Seleccione un widget en la ventana jerarquía o diseñador y modifique los parámetros en el panel detalles.</span><span class="sxs-lookup"><span data-stu-id="60d34-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="60d34-116">En este caso, hemos agregado algunos valores predeterminados de "sugerencia" y un color de matiz cuando el cursor se mantiene sobre el cuadro de texto para proporcionar comentarios sobre los que el widget está listo para interactuar.</span><span class="sxs-lookup"><span data-stu-id="60d34-116">In this case, we’ve added some default “Hint Text” and a tint color when the cursor is hovering over the text box to give feedback that the widget is ready to be interacted with.</span></span>  <span data-ttu-id="60d34-117">Un cuadro de texto mostrará un teclado virtual en HoloLens cuando se interactúe con:</span><span class="sxs-lookup"><span data-stu-id="60d34-117">A text box will pop up a virtual keyboard on HoloLens when it is interacted with:</span></span>

![Captura de pantalla de los parámetros modificados en la ventana jerarquía](images/unreal-umg-img-03.png)

- <span data-ttu-id="60d34-119">También se puede suscribir a eventos en el panel de detalles:</span><span class="sxs-lookup"><span data-stu-id="60d34-119">Events can also be subscribed to in the details panel:</span></span>

![Captura de pantalla de los eventos en el panel de detalles](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="60d34-121">Agregar un widget a un espacio universal</span><span class="sxs-lookup"><span data-stu-id="60d34-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="60d34-122">Cree un nuevo actor, agregue un componente de widget y agregue el actor a la escena:</span><span class="sxs-lookup"><span data-stu-id="60d34-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Captura de pantalla de un actor con un widget adjunto](images/unreal-umg-img-05.png)

- <span data-ttu-id="60d34-124">En el panel de detalles del widget, establezca la **clase widget** en el Blueprint de widget creado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="60d34-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Captura de pantalla del panel de detalles del Blueprint con la clase de widget establecida](images/unreal-umg-img-06.png)

- <span data-ttu-id="60d34-126">Para un widget de texto, asegúrese de que la casilla **recibir entrada de hardware** está desactivada, por lo que solo actualizaremos su texto desde el teclado virtual:</span><span class="sxs-lookup"><span data-stu-id="60d34-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Captura de pantalla de la sección de interacción con la entrada de hardware de recepción desactivada](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="60d34-128">Interacción del widget</span><span class="sxs-lookup"><span data-stu-id="60d34-128">Widget Interaction</span></span>

<span data-ttu-id="60d34-129">Los widgets UMG suelen recibir la entrada de un mouse.</span><span class="sxs-lookup"><span data-stu-id="60d34-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="60d34-130">En HoloLens o VR, es necesario simular un mouse con un componente de interacción de widget para obtener los mismos eventos.</span><span class="sxs-lookup"><span data-stu-id="60d34-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="60d34-131">Cree un nuevo actor, agregue un componente de **interacción de widget** y agregue el actor a la escena:</span><span class="sxs-lookup"><span data-stu-id="60d34-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Captura de pantalla de un nuevo actor con un componente de interacción widget resaltado](images/unreal-umg-img-08.png)

- <span data-ttu-id="60d34-133">En el panel de detalles del componente de interacción widget, establezca la distancia de interacción en la distancia deseada, establezca el **origen de interacción** en **personalizado** y, en desarrollo, establezca **Mostrar depurar** en **true**:</span><span class="sxs-lookup"><span data-stu-id="60d34-133">In the details panel for the Widget Interaction component, set the interaction distance to the desired distance, set the **Interaction Source** to **custom**, and for development, set **Show Debug** to **true**:</span></span>

![Captura de pantalla de las propiedades de componente de interacción y depuración de widgets](images/unreal-umg-img-09.png)

<span data-ttu-id="60d34-135">El valor predeterminado para el origen de interacción es "World", que debe enviar raycasts basándose en la posición mundial del componente de interacción del widget, pero en AR y VR esto no parece ser el caso.</span><span class="sxs-lookup"><span data-stu-id="60d34-135">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component, but in AR and VR this does not appear to be the case.</span></span>  <span data-ttu-id="60d34-136">Habilitar "Mostrar depuración" y agregar un matiz de desplazamiento a los widgets mientras se desarrollan es importante para comprobar que el componente de interacción del widget está haciendo lo esperado.</span><span class="sxs-lookup"><span data-stu-id="60d34-136">Enabling “Show Debug” and adding a hover tint to widgets while developing is important to sanity check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="60d34-137">La solución consiste en usar un origen personalizado y establecer el Raycast en el gráfico de eventos a partir del rayo de mano.</span><span class="sxs-lookup"><span data-stu-id="60d34-137">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="60d34-138">Aquí nos llamaremos desde el paso del evento:</span><span class="sxs-lookup"><span data-stu-id="60d34-138">Here we are calling this from Event Tick:</span></span>

![Plano del paso de evento](images/unreal-umg-img-10.png)

<span data-ttu-id="60d34-140">A continuación, agregue eventos del puntero del mouse virtual al componente de interacción de widget que reacciona a la entrada de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="60d34-140">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="60d34-141">En este caso, enviar un evento de presionar el botón primario cuando se agarre la mano y un evento de liberación del mouse cuando no se agarre:</span><span class="sxs-lookup"><span data-stu-id="60d34-141">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Blueprint con eventos del puntero del mouse virtual agregados](images/unreal-umg-img-13.png)

<span data-ttu-id="60d34-143">Ahora, cuando implemente la aplicación en HoloLens 2, verá un rayo de mano que se extiende desde la mano derecha.</span><span class="sxs-lookup"><span data-stu-id="60d34-143">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="60d34-144">Si lo dirige a uno de los cuadros de texto editables y a la pulsación aérea, el teclado del sistema aparecerá delante de usted y le permitirá escribir texto.</span><span class="sxs-lookup"><span data-stu-id="60d34-144">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="60d34-145">El teclado del sistema HoloLens requiere un motor inreal 4,26 o posterior.</span><span class="sxs-lookup"><span data-stu-id="60d34-145">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="60d34-146">Además, el teclado no aparecerá cuando la aplicación se transmita desde el editor no real al casco, solo cuando la aplicación se ejecuta en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60d34-146">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="60d34-147">Ver también:</span><span class="sxs-lookup"><span data-stu-id="60d34-147">See Also:</span></span>
* [<span data-ttu-id="60d34-148">Documentación de UMG</span><span class="sxs-lookup"><span data-stu-id="60d34-148">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="60d34-149">Tutoriales de UMG de los no reales</span><span class="sxs-lookup"><span data-stu-id="60d34-149">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
