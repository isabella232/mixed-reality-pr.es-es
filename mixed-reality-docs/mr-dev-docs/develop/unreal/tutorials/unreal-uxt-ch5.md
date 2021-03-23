---
title: 5. Adición de un botón y restablecimiento de la ubicación de las piezas
description: Parte 5 de 6 de una serie de tutoriales para compilar una aplicación de ajedrez con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 8e16865e89c06c37f2932f1828bf8ca5551e6fce
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609696"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="f53fc-104">5. Adición de un botón y restablecimiento de la ubicación de las piezas</span><span class="sxs-lookup"><span data-stu-id="f53fc-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="f53fc-105">En el tutorial anterior, agregó actores de interacción manual a los componentes Peón y Manipulador en el tablero de ajedrez para que fueran interactivos.</span><span class="sxs-lookup"><span data-stu-id="f53fc-105">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="f53fc-106">En esta sección, seguirá usando el complemento UX Tools de Mixed Reality Toolkit para crear la aplicación de ajedrez con nuevas funciones y referencias de actor en los planos técnicos.</span><span class="sxs-lookup"><span data-stu-id="f53fc-106">In this section, you'll continue to use the Mixed Reality Toolkit UX Tools plugin to build out your chess app with new functions and Actor references in Blueprints.</span></span> <span data-ttu-id="f53fc-107">Al final de esta sección, estará listo para empaquetar e implementar la aplicación de realidad mixta en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="f53fc-107">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="f53fc-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f53fc-108">Objectives</span></span>

* <span data-ttu-id="f53fc-109">Adición de un botón interactivo</span><span class="sxs-lookup"><span data-stu-id="f53fc-109">Adding an interactive button</span></span>
* <span data-ttu-id="f53fc-110">Creación de una función para restablecer la ubicación de las piezas</span><span class="sxs-lookup"><span data-stu-id="f53fc-110">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="f53fc-111">Enlace del botón para que desencadene la función cuando se presione</span><span class="sxs-lookup"><span data-stu-id="f53fc-111">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="f53fc-112">Creación de una función de restablecimiento</span><span class="sxs-lookup"><span data-stu-id="f53fc-112">Creating a reset function</span></span>

<span data-ttu-id="f53fc-113">La primera tarea consiste en crear un plano técnico de función que reestablezca una pieza de ajedrez a su posición original en la escena.</span><span class="sxs-lookup"><span data-stu-id="f53fc-113">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span>

1.  <span data-ttu-id="f53fc-114">Abra **WhiteKing**, seleccione el icono **+** situado junto a la sección **Funciones** de **Mi plano técnico** y asígnele el nombre **Reset Location**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-114">Open **WhiteKing**, select the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span>

2.  <span data-ttu-id="f53fc-115">Arrastre la ejecución desde **Reset Location** y suéltela en la cuadrícula del plano técnico para crear un nodo **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-115">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span>
    * <span data-ttu-id="f53fc-116">Esta función define la transformación (ubicación, rotación y escala) de un actor en relación con su elemento principal.</span><span class="sxs-lookup"><span data-stu-id="f53fc-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="f53fc-117">Usará esta función para restablecer la posición del rey en el tablero, incluso si la posición original del tablero ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="f53fc-117">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span>

3. <span data-ttu-id="f53fc-118">Haga clic con el botón derecho en el gráfico de eventos, seleccione **Make Transform** (Realizar transformación) y cambie su **Location** (Ubicación) a **X =-26**, **Y = 4**, **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-118">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="f53fc-119">Conecte su **Return Value** (Valor devuelto) a la marca de **New Relative Transform** (Nueva transformación relativa) en **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-119">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span>

![Función Reset Location (Restablecer ubicación)](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="f53fc-121">**Compile** y **guarde** el proyecto antes de volver a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="f53fc-121">**Compile** and **Save** the project before returning to the Main window.</span></span>


## <a name="adding-a-button"></a><span data-ttu-id="f53fc-122">Agregar un botón</span><span class="sxs-lookup"><span data-stu-id="f53fc-122">Adding a button</span></span>

<span data-ttu-id="f53fc-123">Ahora que la función está configurada correctamente, la siguiente tarea consiste en crear un botón que la desencadene cuando se toque.</span><span class="sxs-lookup"><span data-stu-id="f53fc-123">Now that the function is set up correctly, your next task is to create a button that fires it off when touched.</span></span>

1.  <span data-ttu-id="f53fc-124">Haga clic en **Agregar nuevo > Clase de plano técnico**, expanda la sección **Todas las clases** y busque **UxtPressableButtonActor**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-124">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **UxtPressableButtonActor**.</span></span>
    * <span data-ttu-id="f53fc-125">Asigne a este botón el nombre **ResetButton** y haga doble clic para abrir el plano técnico.</span><span class="sxs-lookup"><span data-stu-id="f53fc-125">Name it **ResetButton** and double click to open the Blueprint</span></span>

![Subclase del nuevo plano técnico del botón de estilo HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="f53fc-127">Asegúrese de que la opción **ResetButton(self)** está seleccionada en el panel **Componentes**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-127">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="f53fc-128">En el panel **Detalles**, desplácese hasta la sección **Botón**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-128">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="f53fc-129">Cambie la opción predeterminada de **Etiqueta del botón** a "Restablecer", expanda la sección **Pincel de icono del botón** y presione el botón **Abrir editor del pincel de icono**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-129">Change the default **Button Label** to "Reset", expand the **Button Icon Brush** section, and press the **Open Icon Brush Editor** button.</span></span>

![Establecimiento de la etiqueta y el icono en el botón](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="f53fc-131">Se abrirá el editor de pincel de icono, que puede usar para seleccionar un nuevo icono para el botón.</span><span class="sxs-lookup"><span data-stu-id="f53fc-131">The Icon Brush Editor will open, which you can use to select a new icon for your button.</span></span>

![Selección de un icono para el botón](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="f53fc-133">Hay muchas otras opciones de configuración que puede ajustar para configurar el botón.</span><span class="sxs-lookup"><span data-stu-id="f53fc-133">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="f53fc-134">Para obtener más información acerca del componente UXT Pressable Button, consulte la [documentación](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span><span class="sxs-lookup"><span data-stu-id="f53fc-134">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="f53fc-135">Haga clic en **ButtonComponent (heredado)** en el panel **Componentes** y desplácese hacia abajo en el panel **Detalles** hasta la sección **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-135">Click **ButtonComponent (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span>
    * <span data-ttu-id="f53fc-136">Haga clic en el botón verde **+** situado junto a **On Button Pressed** (Al presionar un botón) para agregar un evento al gráfico de eventos, que se llamará cuando se presione el botón.</span><span class="sxs-lookup"><span data-stu-id="f53fc-136">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span>

<span data-ttu-id="f53fc-137">Desde aquí, llamará a la función **Reset Location** de **WhiteKing**, que necesita una referencia al actor **WhiteKing** en el nivel.</span><span class="sxs-lookup"><span data-stu-id="f53fc-137">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span>

4.  <span data-ttu-id="f53fc-138">En el panel **Mi plano técnico**, vaya a la sección **Variables**, haga clic en el botón **+** y asigne a la variable el nombre **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-138">In the **My Blueprint** panel, navigate to the **Variables** section, click the **+** button, and name the variable **WhiteKing**.</span></span>
    * <span data-ttu-id="f53fc-139">En el panel **Details** (Detalles), seleccione la lista desplegable situada junto a **Variable Type** (Tipo de variable), busque **WhiteKing** y seleccione **Object Reference** (Referencia de objetos).</span><span class="sxs-lookup"><span data-stu-id="f53fc-139">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span>
    * <span data-ttu-id="f53fc-140">Active la casilla situada junto a **instancia editable**, que permite establecer la variable desde el nivel principal.</span><span class="sxs-lookup"><span data-stu-id="f53fc-140">Check the box next to **Instance Editable**, which allows the variable to be set from the Main Level.</span></span>

![Crear una variable](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="f53fc-142">Arrastre la variable de WhiteKing desde **My Blueprint > Variables** (Mi plano técnico > Variables) hasta el gráfico de eventos del botón de restablecimiento y elija **Get WhiteKing** (Obtener WhiteKing).</span><span class="sxs-lookup"><span data-stu-id="f53fc-142">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span>

## <a name="firing-the-function"></a><span data-ttu-id="f53fc-143">Activación de la función</span><span class="sxs-lookup"><span data-stu-id="f53fc-143">Firing the function</span></span>

<span data-ttu-id="f53fc-144">Lo único que queda es activar oficialmente la función de restablecimiento cuando se presiona el botón.</span><span class="sxs-lookup"><span data-stu-id="f53fc-144">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="f53fc-145">Arrastra la marca de salida de WhiteKing y suéltala para colocar un nodo nuevo.</span><span class="sxs-lookup"><span data-stu-id="f53fc-145">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="f53fc-146">Selecciona la función **Reset Location** (Restaurar ubicación).</span><span class="sxs-lookup"><span data-stu-id="f53fc-146">Select the **Reset Location** function.</span></span> <span data-ttu-id="f53fc-147">Por último, arrastra la marca de ejecución de salida de **On Button Pressed** (Al presionar un botón) a la marca de ejecución de entrada de **Reset Location** (Restablecer ubicación).</span><span class="sxs-lookup"><span data-stu-id="f53fc-147">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="f53fc-148">**Compila** y **guarda** el plano técnico ResetButton y, a continuación, vuelve a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="f53fc-148">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span>

![Llamar a la función Reset Location (Restablecer ubicación) desde On Button Pressed (Al presionar un botón)](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="f53fc-150">Arrastre **ResetButton** a la ventanilla y establezca su ubicación en **X = 50**, **Y =-25** y **Z = 10**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-150">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="f53fc-151">Establezca su rotación en **Z = 180**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-151">Set its rotation to **Z = 180**.</span></span> <span data-ttu-id="f53fc-152">En **Default** (Valor predeterminado), establezca el valor de la variable **WhiteKing** en **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="f53fc-152">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![Definir la variable](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="f53fc-154">Ejecute la aplicación, mueva la pieza de ajedrez a una nueva ubicación y presione el botón de estilo HoloLens 2 para ver la lógica de restablecimiento en acción.</span><span class="sxs-lookup"><span data-stu-id="f53fc-154">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="f53fc-155">Ahora tiene una aplicación de realidad mixta con un tablero y una pieza de ajedrez interactivos, así como un botón totalmente funcional que restablece la ubicación de la pieza.</span><span class="sxs-lookup"><span data-stu-id="f53fc-155">You now have a mixed reality app with an interactable chess piece and board, and a fully functioning button that resets the piece’s location.</span></span> <span data-ttu-id="f53fc-156">Puede encontrar la aplicación completada hasta este momento en su repositorio de [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span><span class="sxs-lookup"><span data-stu-id="f53fc-156">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="f53fc-157">No dude en profundizar más allá de este tutorial y configurar el resto de las piezas de ajedrez de modo que se restablezca todo el tablero cuando se presione el botón de restablecimiento.</span><span class="sxs-lookup"><span data-stu-id="f53fc-157">Feel free to go beyond this tutorial and set up the rest of the chess pieces so that the entire board is reset when you press the reset button.</span></span>

![Escena final en la ventanilla](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="f53fc-159">Está listo para pasar a la sección final de este tutorial, donde aprenderá a empaquetar e implementar la aplicación en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="f53fc-159">You're ready to move on to the final section of this tutorial where you'll learn how to package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f53fc-160">En este punto, debe actualizar el proyecto con la **[configuración de rendimiento de Unreal](../performance-recommendations-for-unreal.md)** recomendada antes de implementar la aplicación en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="f53fc-160">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="f53fc-161">Sección siguiente: 6. Empaquetado y implementación en el dispositivo o emulador</span><span class="sxs-lookup"><span data-stu-id="f53fc-161">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
