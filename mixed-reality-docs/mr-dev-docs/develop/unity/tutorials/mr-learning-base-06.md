---
title: 'Tutoriales de introducción: 6. Creación de interfaces de usuario'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 3d8cfa7206aa6004cdf62db977ca760daed9a27c
ms.sourcegitcommit: adbdb0a38e0dc5ac82f847c7b2ef87f27c16b5f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2020
ms.locfileid: "92493241"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="27d5b-105">6. Creación de interfaces de usuario</span><span class="sxs-lookup"><span data-stu-id="27d5b-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="27d5b-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="27d5b-106">Overview</span></span>

<span data-ttu-id="27d5b-107">En este tutorial, obtendrá información sobre cómo crear una interfaz de usuario sencilla con los elementos prefabricados de botón y menú de MRTK junto con el componente TextMeshPro de Unity.</span><span class="sxs-lookup"><span data-stu-id="27d5b-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="27d5b-108">También aprenderá a configurar los botones para desencadenar eventos y agregar elementos dinámicos de información sobre herramientas en la interfaz de usuario para proporcionar a los usuarios información adicional.</span><span class="sxs-lookup"><span data-stu-id="27d5b-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="27d5b-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="27d5b-109">Objectives</span></span>

* <span data-ttu-id="27d5b-110">Aprender a organizar los botones de una colección</span><span class="sxs-lookup"><span data-stu-id="27d5b-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="27d5b-111">Aprender a usar los elementos prefabricados de menú de MRTK</span><span class="sxs-lookup"><span data-stu-id="27d5b-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="27d5b-112">Aprender a interactuar con hologramas mediante botones y elementos de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="27d5b-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="27d5b-113">Aprender a agregar elementos de texto</span><span class="sxs-lookup"><span data-stu-id="27d5b-113">Learn how to add text elements</span></span>
* <span data-ttu-id="27d5b-114">Aprender a generar información sobre herramientas en objetos dinámicamente</span><span class="sxs-lookup"><span data-stu-id="27d5b-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="27d5b-115">Creación de un panel estático de botones</span><span class="sxs-lookup"><span data-stu-id="27d5b-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="27d5b-116">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** ( Crear vacío)para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **Buttons** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="27d5b-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons** , and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="27d5b-117">**Posición** : X = 0.6, Y = 0.036, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="27d5b-117">**Position** : X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="27d5b-118">**Rotación** : X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="27d5b-118">**Rotation** : X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="27d5b-119">**Escala** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="27d5b-119">**Scale** : X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="27d5b-121">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** , haga clic y arrastre el elemento prefabricado **PressableRoundButton** sobre el objeto **Buttons** y, a continuación, haga clic con el botón derecho en PressableRoundButton, seleccione **Duplicate** (Duplicar) para crear una copia y repita el proceso hasta que tenga un total de tres objetos PressableRoundButton:</span><span class="sxs-lookup"><span data-stu-id="27d5b-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="27d5b-123">En la ventana Hierarchy (Jerarquía), seleccione el objeto **Buttons** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **GridObjectCollection** y configúrelo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="27d5b-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="27d5b-124">**Tipo de orden** : Orden secundario</span><span class="sxs-lookup"><span data-stu-id="27d5b-124">**Sort Type** : Child Order</span></span>
* <span data-ttu-id="27d5b-125">**Diseño** : Horizontal</span><span class="sxs-lookup"><span data-stu-id="27d5b-125">**Layout** : Horizontal</span></span>
* <span data-ttu-id="27d5b-126">**Ancho de celda** : 0.2</span><span class="sxs-lookup"><span data-stu-id="27d5b-126">**Cell Width** : 0.2</span></span>
* <span data-ttu-id="27d5b-127">**Ancla** : Centro a la izquierda</span><span class="sxs-lookup"><span data-stu-id="27d5b-127">**Anchor** : Middle Left</span></span>

<span data-ttu-id="27d5b-128">A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios del objeto Buttons:</span><span class="sxs-lookup"><span data-stu-id="27d5b-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="27d5b-130">En la ventana Hierarchy (Jerarquía), asigne el nombre **Hints** , **Explode** y **Reset** a los botones.</span><span class="sxs-lookup"><span data-stu-id="27d5b-130">In the Hierarchy window, name the buttons **Hints** , **Explode** , and **Reset** .</span></span>

<span data-ttu-id="27d5b-131">Para cada botón, seleccione el objeto secundario **SeeItSayItLabel** > **TextMeshPro** y, a continuación, en la ventana Inspector, cambie el texto del componente **TextMeshPro - Text** respectivo para que coincida con los nombres de los botones:</span><span class="sxs-lookup"><span data-stu-id="27d5b-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="27d5b-133">Una vez hecho esto, contraiga los objetos secundarios del objeto Buttons.</span><span class="sxs-lookup"><span data-stu-id="27d5b-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="27d5b-134">En la ventana Hierarchy (Jerarquí)a, seleccione el objeto del botón **Hints** y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="27d5b-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="27d5b-135">Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="27d5b-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="27d5b-136">En la lista desplegable **No function** (Ninguna función), seleccione **PlacementHintsController** > **TogglePlacementHints ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="27d5b-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

<span data-ttu-id="27d5b-138">En la ventana Hierarchy (Jerarquí)a, seleccione el objeto del botón **Explode** y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="27d5b-138">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="27d5b-139">Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="27d5b-139">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="27d5b-140">En la lista desplegable **No function** (Ninguna función), seleccione **ExplodedViewController** > **ToggleExplodedView ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="27d5b-140">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="27d5b-142">Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionada la barra espaciadora para activar la mano y use el mouse para presionar el botón **Hints** para activar y desactivar la visibilidad de los objetos de sugerencia de colocación:</span><span class="sxs-lookup"><span data-stu-id="27d5b-142">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="27d5b-144">y el botón **Explode** para activar y desactivar la vista seccionada:</span><span class="sxs-lookup"><span data-stu-id="27d5b-144">and the **Explode** button to toggle the exploded view on and off:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="27d5b-146">Creación de un menú dinámico que sigue al usuario</span><span class="sxs-lookup"><span data-stu-id="27d5b-146">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="27d5b-147">En la ventana Proyecto, vaya a la carpeta **Recursos** > **MRTK** > **SDK** > **Características** > **Experiencia del usuario** > **Prefabs (Elementos prefabricados)**  > **Menús** , haga clic y arrastre el elemento prefabricado **NearMenu4x1** en la ventana Jerarquía, establezca su **posición** de transformación en X = 0, Y = -0.4, Z = 0 y configúrelo de la forma siguiente:</span><span class="sxs-lookup"><span data-stu-id="27d5b-147">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="27d5b-148">Compruebe que el **Tracked Target Type** (Tipo de objetivo de seguimiento) del componente **SolverHandler** esté establecido en **Head** (Cabeza).</span><span class="sxs-lookup"><span data-stu-id="27d5b-148">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="27d5b-149">Marque la casilla junto al componente **RadialView** del solucionador para que esté habilitado de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="27d5b-149">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="27d5b-151">En la ventana Hierarchy (Jerarquía), cambie el nombre del objeto a **Menu** y, a continuación, expanda el objeto secundario **ButtonCollection** para mostrar los cuatro botones:</span><span class="sxs-lookup"><span data-stu-id="27d5b-151">In the Hierarchy window, rename the object to **Menu** , then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="27d5b-153">Cambie el nombre del primer botón por **Indicator** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="27d5b-153">Rename the first button to **Indicator** , then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="27d5b-154">Cambie el **texto de la etiqueta principal** para que coincida con el nombre del botón.</span><span class="sxs-lookup"><span data-stu-id="27d5b-154">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="27d5b-155">Asigne el objeto **Indicator** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="27d5b-155">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="27d5b-156">En la lista desplegable **No Function** (Ninguna función), seleccione **GameObject** > **SetActive (bool)** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="27d5b-156">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="27d5b-157">Compruebe que la casilla del argumento esté **activada** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-157">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="27d5b-158">Cambie el **icono** al icono de "búsqueda".</span><span class="sxs-lookup"><span data-stu-id="27d5b-158">Change the **Icon** to the 'search' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="27d5b-160">En la ventana Jerarquía, seleccione el objeto **Indicador** y, a continuación, en la ventana del Inspector:</span><span class="sxs-lookup"><span data-stu-id="27d5b-160">In the Hierarchy window, select the **Indicator** object, then in the Inspector window:</span></span>

* <span data-ttu-id="27d5b-161">Desactive la casilla situada junto a su nombre para que esté inactivo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="27d5b-161">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="27d5b-162">Use el botón **Agregar componente** para agregar el componente **Controlador del indicador de dirección (Script)** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-162">Use the **Add Component** button to add the **Directional Indicator Controller (Script)** component</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="27d5b-164">Ahora, cuando se inicia la aplicación, el objeto Indicator está deshabilitado de forma predeterminada y se puede habilitar presionando el botón Indicator.</span><span class="sxs-lookup"><span data-stu-id="27d5b-164">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="27d5b-165">Cambie el nombre del segundo botón por **TapToPlace** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="27d5b-165">Rename the second button to **TapToPlace** , then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="27d5b-166">Cambie el **texto de la etiqueta principal** para que coincida con el nombre del botón.</span><span class="sxs-lookup"><span data-stu-id="27d5b-166">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="27d5b-167">Asigne el objeto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="27d5b-167">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="27d5b-168">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool Enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="27d5b-168">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="27d5b-169">Compruebe que la casilla del argumento esté **activada** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-169">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="27d5b-170">Cambie el **icono** al icono de "mano con rayo".</span><span class="sxs-lookup"><span data-stu-id="27d5b-170">Change the **Icon** to the 'hand with ray' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="27d5b-172">En la ventana Jerarquía, seleccione el objeto **RoverAssembly** y, a continuación, en la ventana Inspector, configure el componente **Tap To Place (Script)** (Pulsar para colocar [Script]) del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="27d5b-172">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="27d5b-173">Desactive la casilla situada junto a su nombre para que esté inactivo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="27d5b-173">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="27d5b-174">En la sección del evento **On Placing Stopped ()** , haga clic en el icono **+** para agregar un nuevo evento:</span><span class="sxs-lookup"><span data-stu-id="27d5b-174">In the **On Placing Stopped ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="27d5b-175">Asigne el objeto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="27d5b-175">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="27d5b-176">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool Enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="27d5b-176">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="27d5b-177">Compruebe que la casilla del argumento esté **desactivada** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-177">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="27d5b-179">Ahora, cuando se inicia la aplicación, la funcionalidad Tap to Place (Tocar para colocar) está deshabilitada de forma predeterminada y se puede habilitar presionando el botón Tap to Place.</span><span class="sxs-lookup"><span data-stu-id="27d5b-179">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="27d5b-180">Además, cuando se complete la acción de tocar para colocar, se deshabilitará.</span><span class="sxs-lookup"><span data-stu-id="27d5b-180">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="27d5b-181">Agregación de texto a la escena</span><span class="sxs-lookup"><span data-stu-id="27d5b-181">Adding text to the scene</span></span>

<span data-ttu-id="27d5b-182">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **Table** (Tabla) y seleccione **3D Object** > **Text - TextMeshPro** (Objeto 3D > Texto - TextMeshPro) para agregar un objeto de texto como elemento secundario del objeto Table y, a continuación, en la ventana Inspector, configure el componente **Rect Transform** (Transformación rectangular) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="27d5b-182">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="27d5b-183">Cambie **Pos Y** (Posición Y) a 1.</span><span class="sxs-lookup"><span data-stu-id="27d5b-183">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="27d5b-184">Cambie **Width** (Ancho) a 1.</span><span class="sxs-lookup"><span data-stu-id="27d5b-184">Change **Width** to 1</span></span>
* <span data-ttu-id="27d5b-185">Cambie **Height** (Altura) a 1.</span><span class="sxs-lookup"><span data-stu-id="27d5b-185">Change **Height** to 1</span></span>
* <span data-ttu-id="27d5b-186">Cambie **Rotation X** (Rotación X) a 90.</span><span class="sxs-lookup"><span data-stu-id="27d5b-186">Change **Rotation X** to 90</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="27d5b-188">A continuación, configure el componente **TextMeshPro - Text** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="27d5b-188">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="27d5b-189">Cambie **Text** (Texto) a Rover Explorer.</span><span class="sxs-lookup"><span data-stu-id="27d5b-189">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="27d5b-190">Cambie **Font Style** (Estilo de fuente) a Bold (Negrita).</span><span class="sxs-lookup"><span data-stu-id="27d5b-190">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="27d5b-191">Cambie **Font Size** (Tamaño de fuente) a 1.</span><span class="sxs-lookup"><span data-stu-id="27d5b-191">Change **Font Size** to 1</span></span>
* <span data-ttu-id="27d5b-192">Cambie Extra Settings > **Margins** (Configuración adicional > Márgenes) a 0.03.</span><span class="sxs-lookup"><span data-stu-id="27d5b-192">Change Extra Settings > **Margins** to 0.03</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="27d5b-194">Agregación de información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="27d5b-194">Adding tooltips</span></span>

<span data-ttu-id="27d5b-195">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** para buscar los objetos prefabricados de información sobre herramientas:</span><span class="sxs-lookup"><span data-stu-id="27d5b-195">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="27d5b-197">En la ventana Hierarchy (Jerarquía), expanda el objeto RoverExplorer > **RoverParts** y seleccione todos los objetos secundarios de partes, y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **ToolTipSpawner** y configúrelo de la forma siguiente:</span><span class="sxs-lookup"><span data-stu-id="27d5b-197">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="27d5b-198">Asegúrese de que la casilla de verificación **Focus enabled** (Enfoque habilitado) está activada para requerir que el usuario mire la parte para que aparezca la información sobre herramientas.</span><span class="sxs-lookup"><span data-stu-id="27d5b-198">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="27d5b-199">Asigne el elemento prefabricado **Simple Line ToolTip** (Información sobre herramientas de línea simple) desde la ventana Project (Proyecto) al campo **Tool Tip Prefab** (Elemento prefabricado de información de herramientas).</span><span class="sxs-lookup"><span data-stu-id="27d5b-199">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="27d5b-200">Cambie ToolTip Override Settings > **Settings Mode** (Configuración de invalidación de información sobre herramientas > Modo de configuración) a **Override** (Invalidar).</span><span class="sxs-lookup"><span data-stu-id="27d5b-200">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="27d5b-201">Cambie ToolTip Override Settings > **Manual Pivot Local Position Y** (Configuración de invalidación de información sobre herramientas > Posición Y local del pivote manual) a **1.5** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-201">Change the ToolTip Override Settings > **Manual Pivot Local Position Y** to **1.5**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="27d5b-203">En la ventana Hierarchy (Jerarquía), seleccione la primera parte del rover, RoverParts > **Camera_Part** y configure el componente **ToolTipSpawner** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="27d5b-203">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part** , and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="27d5b-204">Cambie **Tool Tip Text** para reflejar el nombre de la parte; por ejemplo, **Camera** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-204">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="27d5b-206">**Repita** este paso para cada uno de los objetos de parte del rover para configurar el componente **ToolTipSpawner** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="27d5b-206">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="27d5b-207">Para **Generator_Part** , cambie **Tool Tip Text** a **Generator** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-207">For the **Generator_Part** , change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="27d5b-208">Para **Lights_Part** , cambie **Tool Tip Text** a **Lights** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-208">For the **Lights_Part** , change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="27d5b-209">Para **UHFAntenna_Part** , cambie **Tool Tip Text** a **UHF Antenna** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-209">For the **UHFAntenna_Part** , change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="27d5b-210">Para **Spectrometer_Part** , cambie **Tool Tip Text** a **Spectrometer** .</span><span class="sxs-lookup"><span data-stu-id="27d5b-210">For the **Spectrometer_Part** , change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="27d5b-211">Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionado el botón derecho del mouse mientras mueve el mouse hasta que la mirada entre en contacto con una de las partes y la información sobre herramientas de la parte se mostrará:</span><span class="sxs-lookup"><span data-stu-id="27d5b-211">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="27d5b-213">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="27d5b-213">Congratulations</span></span>

<span data-ttu-id="27d5b-214">En este tutorial, aprendió a crear una interfaz de usuario sencilla con los elementos prefabricados de botón y menú proporcionados por MRTK junto con el componente TextMeshPro de Unity y a configurar los botones para desencadenar eventos cuando se presionan.</span><span class="sxs-lookup"><span data-stu-id="27d5b-214">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="27d5b-215">También ha aprendido a agregar elementos dinámicos de información sobre herramientas en la interfaz de usuario para proporcionar información adicional al usuario.</span><span class="sxs-lookup"><span data-stu-id="27d5b-215">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="27d5b-216">Tutorial siguiente: 7. Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="27d5b-216">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)