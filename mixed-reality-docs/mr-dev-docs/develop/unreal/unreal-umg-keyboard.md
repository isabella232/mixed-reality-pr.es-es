---
title: UMG y teclado en Unreal
description: Obtenga información sobre cómo usar gráficos de movimiento sin territorio para crear un sistema de interfaz de usuario fuera de los widgets.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, widgets, interfaz de usuario, UMG, gráficos de movimiento inreal, no real Engine, UE, UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609766"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="c22e4-104">UMG y teclado en Unreal</span><span class="sxs-lookup"><span data-stu-id="c22e4-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="c22e4-105">No real Motion Graphics (UMG) es un sistema de interfaz de usuario integrado del motor, que se usa para crear interfaces como menús y cuadros de texto.</span><span class="sxs-lookup"><span data-stu-id="c22e4-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="c22e4-106">Las interfaces de usuario compiladas con UMG se componen de widgets.</span><span class="sxs-lookup"><span data-stu-id="c22e4-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="c22e4-107">Le guiaremos a través de la creación de un nuevo widget, su incorporación al espacio universal y la habilitación de la interacción con el teclado del sistema como ejemplo.</span><span class="sxs-lookup"><span data-stu-id="c22e4-107">We'll guide you through creating a new widget, adding it to world space, and enabling interaction using the system keyboard as an example.</span></span> <span data-ttu-id="c22e4-108">Puede obtener más información sobre UMG en la [documentación](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)oficial del motor no real.</span><span class="sxs-lookup"><span data-stu-id="c22e4-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="c22e4-109">Crear un nuevo widget</span><span class="sxs-lookup"><span data-stu-id="c22e4-109">Create a new widget</span></span>

- <span data-ttu-id="c22e4-110">Cree un Blueprint de widget para diseñar la interfaz de usuario del juego:</span><span class="sxs-lookup"><span data-stu-id="c22e4-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Captura de pantalla de la adición de un Blueprint de widget desde el menú no real](images/unreal-umg-img-01.png)

- <span data-ttu-id="c22e4-112">Abra el nuevo plano y agregue componentes de la paleta al lienzo.</span><span class="sxs-lookup"><span data-stu-id="c22e4-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="c22e4-113">En este caso, hemos agregado dos componentes de cuadro de texto de la sección "entrada":</span><span class="sxs-lookup"><span data-stu-id="c22e4-113">In this case, we've added two Text Box components from the “Input” section:</span></span>

![Captura de pantalla de la ventana de jerarquía con el componente widget de texto resaltado y expandido](images/unreal-umg-img-02.png)

- <span data-ttu-id="c22e4-115">Seleccione un widget en la ventana jerarquía o diseñador y modifique los parámetros en el panel detalles.</span><span class="sxs-lookup"><span data-stu-id="c22e4-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="c22e4-116">En este caso, hemos agregado un "texto de sugerencia" predeterminado y un color de matiz que aparece al mantener el mouse sobre el cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="c22e4-116">In this case, we’ve added some default “Hint Text” and a tint color that appears when you hover over the text box.</span></span>  <span data-ttu-id="c22e4-117">Un cuadro de texto mostrará un teclado virtual en HoloLens cuando interactúe con:</span><span class="sxs-lookup"><span data-stu-id="c22e4-117">A text box will pop up a virtual keyboard on HoloLens when it's interacted with:</span></span>

![Captura de pantalla de los parámetros modificados en la ventana jerarquía](images/unreal-umg-img-03.png)

- <span data-ttu-id="c22e4-119">También se puede suscribir a eventos en el panel de detalles:</span><span class="sxs-lookup"><span data-stu-id="c22e4-119">Events can also be subscribed to in the details panel:</span></span>

![Captura de pantalla de los eventos en el panel de detalles](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="c22e4-121">Agregar un widget a un espacio universal</span><span class="sxs-lookup"><span data-stu-id="c22e4-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="c22e4-122">Cree un nuevo actor, agregue un componente de widget y agregue el actor a la escena:</span><span class="sxs-lookup"><span data-stu-id="c22e4-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Captura de pantalla de un actor con un widget adjunto](images/unreal-umg-img-05.png)

- <span data-ttu-id="c22e4-124">En el panel de detalles del widget, establezca la **clase widget** en el Blueprint de widget creado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="c22e4-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Captura de pantalla del panel de detalles del Blueprint con la clase de widget establecida](images/unreal-umg-img-06.png)

- <span data-ttu-id="c22e4-126">Para un widget de texto, asegúrese de que la casilla **recibir entrada de hardware** está desactivada, por lo que solo actualizaremos su texto desde el teclado virtual:</span><span class="sxs-lookup"><span data-stu-id="c22e4-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Captura de pantalla de la sección de interacción con la entrada de hardware de recepción desactivada](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="c22e4-128">Interacción del widget</span><span class="sxs-lookup"><span data-stu-id="c22e4-128">Widget Interaction</span></span>

<span data-ttu-id="c22e4-129">Los widgets UMG suelen recibir la entrada de un mouse.</span><span class="sxs-lookup"><span data-stu-id="c22e4-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="c22e4-130">En HoloLens o VR, es necesario simular un mouse con un componente de interacción de widget para obtener los mismos eventos.</span><span class="sxs-lookup"><span data-stu-id="c22e4-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="c22e4-131">Cree un nuevo actor, agregue un componente de **interacción de widget** y agregue el actor a la escena:</span><span class="sxs-lookup"><span data-stu-id="c22e4-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Captura de pantalla de un nuevo actor con un componente de interacción widget resaltado](images/unreal-umg-img-08.png)

- <span data-ttu-id="c22e4-133">En el panel de detalles del componente de interacción widget:</span><span class="sxs-lookup"><span data-stu-id="c22e4-133">In the details panel for the Widget Interaction component:</span></span>
    - <span data-ttu-id="c22e4-134">Establezca la distancia de interacción en el valor de distancia que desee.</span><span class="sxs-lookup"><span data-stu-id="c22e4-134">Set the interaction distance to the distance value you want</span></span>
    - <span data-ttu-id="c22e4-135">Establecer el **origen de interacción** en **personalizado**</span><span class="sxs-lookup"><span data-stu-id="c22e4-135">Set the **Interaction Source** to **custom**</span></span>
    - <span data-ttu-id="c22e4-136">Para el desarrollo, establezca **Mostrar depurar** en **true**:</span><span class="sxs-lookup"><span data-stu-id="c22e4-136">For development, set **Show Debug** to **true**:</span></span>

![Captura de pantalla de las propiedades de componente de interacción y depuración de widgets](images/unreal-umg-img-09.png)

<span data-ttu-id="c22e4-138">El valor predeterminado para el origen de interacción es "World", que debe enviar raycasts basándose en la posición mundial del componente de interacción del widget.</span><span class="sxs-lookup"><span data-stu-id="c22e4-138">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component.</span></span> <span data-ttu-id="c22e4-139">En AR y VR, no es el caso.</span><span class="sxs-lookup"><span data-stu-id="c22e4-139">In AR and VR, that's not the case.</span></span>  <span data-ttu-id="c22e4-140">Es importante habilitar "Mostrar depuración" y agregar un matiz de desplazamiento a los widgets para comprobar que el componente de interacción del widget está haciendo lo esperado.</span><span class="sxs-lookup"><span data-stu-id="c22e4-140">Enabling “Show Debug” and adding a hover tint to widgets is important to check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="c22e4-141">La solución consiste en usar un origen personalizado y establecer el Raycast en el gráfico de eventos a partir del rayo de mano.</span><span class="sxs-lookup"><span data-stu-id="c22e4-141">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="c22e4-142">Aquí vamos a llamar a esto desde el paso del evento:</span><span class="sxs-lookup"><span data-stu-id="c22e4-142">Here we're calling this from Event Tick:</span></span>

![Plano del paso de evento](images/unreal-umg-img-10.png)

<span data-ttu-id="c22e4-144">A continuación, agregue eventos del puntero del mouse virtual al componente de interacción de widget que reacciona a la entrada de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c22e4-144">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="c22e4-145">En este caso, enviar un evento de presionar el botón primario cuando se agarre la mano y un evento de liberación del mouse cuando no se agarre:</span><span class="sxs-lookup"><span data-stu-id="c22e4-145">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Blueprint con eventos del puntero del mouse virtual agregados](images/unreal-umg-img-13.png)

<span data-ttu-id="c22e4-147">Ahora, cuando implemente la aplicación en HoloLens 2, verá un rayo de mano que se extiende desde la mano derecha.</span><span class="sxs-lookup"><span data-stu-id="c22e4-147">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="c22e4-148">Si lo dirige a uno de los cuadros de texto editables y a la pulsación aérea, el teclado del sistema aparecerá delante de usted y le permitirá escribir texto.</span><span class="sxs-lookup"><span data-stu-id="c22e4-148">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="c22e4-149">El teclado del sistema HoloLens requiere un motor inreal 4,26 o posterior.</span><span class="sxs-lookup"><span data-stu-id="c22e4-149">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="c22e4-150">Además, el teclado no aparecerá cuando la aplicación se transmita desde el editor no real al casco, solo cuando la aplicación se ejecuta en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c22e4-150">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="c22e4-151">Ver también:</span><span class="sxs-lookup"><span data-stu-id="c22e4-151">See Also:</span></span>
* [<span data-ttu-id="c22e4-152">Documentación de UMG</span><span class="sxs-lookup"><span data-stu-id="c22e4-152">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="c22e4-153">Tutoriales de UMG de los no reales</span><span class="sxs-lookup"><span data-stu-id="c22e4-153">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
