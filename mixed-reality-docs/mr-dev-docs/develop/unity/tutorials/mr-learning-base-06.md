---
title: Creación de interfaces de usuario
description: En este curso se muestra cómo usar Mixed Reality Toolkit (MRTK) para crear interfaces de usuario estáticas y dinámicas.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, prefabs, holograms, tooltips
ms.localizationpriority: high
ms.openlocfilehash: 0abfb4ea2fac3a2e50837c219a465c4ab002e69d
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110280"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="a6757-104">6. Creación de interfaces de usuario</span><span class="sxs-lookup"><span data-stu-id="a6757-104">6. Creating user interfaces</span></span>

<span data-ttu-id="a6757-105">En este tutorial, obtendrá información sobre cómo crear una interfaz de usuario sencilla con los elementos prefabricados de botón y menú de MRTK junto con el componente TextMeshPro de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6757-105">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="a6757-106">También aprenderá a configurar los botones para desencadenar eventos y agregar elementos dinámicos de información sobre herramientas en la interfaz de usuario para proporcionar a los usuarios información adicional.</span><span class="sxs-lookup"><span data-stu-id="a6757-106">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="a6757-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a6757-107">Objectives</span></span>

* <span data-ttu-id="a6757-108">Aprender a organizar los botones de una colección</span><span class="sxs-lookup"><span data-stu-id="a6757-108">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="a6757-109">Aprender a usar los elementos prefabricados de menú de MRTK</span><span class="sxs-lookup"><span data-stu-id="a6757-109">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="a6757-110">Aprender a interactuar con hologramas mediante botones y elementos de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="a6757-110">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="a6757-111">Aprender a agregar elementos de texto</span><span class="sxs-lookup"><span data-stu-id="a6757-111">Learn how to add text elements</span></span>
* <span data-ttu-id="a6757-112">Aprender a generar información sobre herramientas en objetos dinámicamente</span><span class="sxs-lookup"><span data-stu-id="a6757-112">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="a6757-113">Creación de un panel estático de botones</span><span class="sxs-lookup"><span data-stu-id="a6757-113">Creating a static panel of buttons</span></span>

<span data-ttu-id="a6757-114">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** ( Crear vacío)para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **Buttons** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="a6757-114">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="a6757-115">**Posición**: X = 0.6, Y = 0.036, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="a6757-115">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="a6757-116">**Rotación**: X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="a6757-116">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="a6757-117">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="a6757-117">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con el objeto Buttons recién creado seleccionado y colocado](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="a6757-119">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, haga clic y arrastre el elemento prefabricado **PressableRoundButton** sobre el objeto **Buttons** y, a continuación, haga clic con el botón derecho en PressableRoundButton, seleccione **Duplicate** (Duplicar) para crear una copia y repita el proceso hasta que tenga un total de tres objetos PressableRoundButton:</span><span class="sxs-lookup"><span data-stu-id="a6757-119">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![Unity con los objetos prefabricados PressableRoundButton recién agregados](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="a6757-121">En la ventana Hierarchy (Jerarquía), seleccione el objeto **Buttons** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **GridObjectCollection** y configúrelo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a6757-121">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="a6757-122">**Tipo de orden**: Orden secundario</span><span class="sxs-lookup"><span data-stu-id="a6757-122">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="a6757-123">**Diseño**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="a6757-123">**Layout**: Horizontal</span></span>
* <span data-ttu-id="a6757-124">**Ancho de celda**: 0.2</span><span class="sxs-lookup"><span data-stu-id="a6757-124">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="a6757-125">**Ancla**: Centro a la izquierda</span><span class="sxs-lookup"><span data-stu-id="a6757-125">**Anchor**: Middle Left</span></span>

<span data-ttu-id="a6757-126">A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios del objeto Buttons:</span><span class="sxs-lookup"><span data-stu-id="a6757-126">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![Objeto Buttons de Unity con el componente GridObjectCollection agregado, configurado y aplicado](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="a6757-128">En la ventana Hierarchy (Jerarquía), asigne el nombre **Hints**, **Explode** y **Reset** a los botones.</span><span class="sxs-lookup"><span data-stu-id="a6757-128">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="a6757-129">Para cada botón, seleccione el objeto secundario **SeeItSayItLabel** > **TextMeshPro** y, a continuación, en la ventana Inspector, cambie el texto del componente **TextMeshPro - Text** respectivo para que coincida con los nombres de los botones:</span><span class="sxs-lookup"><span data-stu-id="a6757-129">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![Unity con etiquetas de texto de botón configuradas](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="a6757-131">Una vez hecho esto, contraiga los objetos secundarios del objeto Buttons.</span><span class="sxs-lookup"><span data-stu-id="a6757-131">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="a6757-132">En la ventana Hierarchy (Jerarquí)a, seleccione el objeto del botón **Hints** y, a continuación, en la ventana Inspector, configure el evento **Interactable.OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a6757-132">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="a6757-133">Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="a6757-133">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a6757-134">En la lista desplegable **No function** (Ninguna función), seleccione **PlacementHintsController** > **TogglePlacementHints ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="a6757-134">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del objeto de botón Hints configurado](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> <span data-ttu-id="a6757-136">El componente Interactable es un contenedor todo en uno que hace que se puede interactuar fácilmente con cualquier objeto y que este tenga capacidad de respuesta a las entradas.</span><span class="sxs-lookup"><span data-stu-id="a6757-136">The Interactable component is an all-in-one container to make any object easily interactable and responsive to input.</span></span> <span data-ttu-id="a6757-137">Interactable actúa como una instrucción comodín para todos los tipos de entradas como, por ejemplo, entradas táctiles, haces de mano, voz, etc., y canaliza estas interacciones en eventos y respuestas de tema visual.</span><span class="sxs-lookup"><span data-stu-id="a6757-137">Interactable acts as a catch-all for all types of input including touch, hand rays, speech, etc. and funnels these interactions into events and visual theme responses.</span></span> <span data-ttu-id="a6757-138">Para aprender a configurarlo para diferentes tipos de entrada y personalizar su tema visual, puede consultar la guía sobre [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) en el [Portal de documentación de MRTK](/windows/mixed-reality/mrtk-unity/).</span><span class="sxs-lookup"><span data-stu-id="a6757-138">To learn how to configure it for different input types and customize it's visual theme, you can refer to the [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) guide in the [MRTK Documentation Portal](/windows/mixed-reality/mrtk-unity/).</span></span>

<span data-ttu-id="a6757-139">En la ventana Hierarchy (Jerarquía), seleccione el objeto del botón **Explode** y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a6757-139">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="a6757-140">Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="a6757-140">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a6757-141">En la lista desplegable **No function** (Ninguna función), seleccione **ExplodedViewController** > **ToggleExplodedView ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="a6757-141">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del objeto de botón Explode configurado](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="a6757-143">Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionada la barra espaciadora para activar la mano y use el mouse para presionar el botón **Hints** para activar y desactivar la visibilidad de los objetos de sugerencia de colocación:</span><span class="sxs-lookup"><span data-stu-id="a6757-143">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![Vista dividida del modo de reproducción de Unity con el botón Hints presionado](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="a6757-145">y el botón **Explode** para activar y desactivar la vista seccionada:</span><span class="sxs-lookup"><span data-stu-id="a6757-145">and the **Explode** button to toggle the exploded view on and off:</span></span>

![Vista dividida del modo de reproducción de Unity con el botón Explode presionado](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="a6757-147">Creación de un menú dinámico que sigue al usuario</span><span class="sxs-lookup"><span data-stu-id="a6757-147">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="a6757-148">En la ventana Proyecto, vaya a la carpeta PackagesMixed Reality Toolkit FoundationSDKFeatures\*\*UXPrefabsMenus (Paquetes > Mixed Reality Toolkit Foundation > SDK > Características > Experiencia del usuario > Objetos prefabricados > Menús), haga clic y arrastre el elemento prefabricado NearMenu4x1 a la ventana Hierarchy (Jerarquía), establezca el valor del campo Position (Posición) del área Transform (Transformación) en X = 0; Y = -0,4; Z = 0 y configúrelo de la forma siguiente:</span><span class="sxs-lookup"><span data-stu-id="a6757-148">In the Project window, navigate to the **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="a6757-149">Compruebe que el **Tracked Target Type** (Tipo de objetivo de seguimiento) del componente **SolverHandler** esté establecido en **Head** (Cabeza).</span><span class="sxs-lookup"><span data-stu-id="a6757-149">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="a6757-150">Marque la casilla junto al componente **RadialView** del solucionador para que esté habilitado de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="a6757-150">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![Unity con el objeto prefabricado Menu recién agregado seleccionado](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="a6757-152">En la ventana Hierarchy (Jerarquía), cambie el nombre del objeto a **Menu** y, a continuación, expanda el objeto secundario **ButtonCollection** para mostrar los cuatro botones:</span><span class="sxs-lookup"><span data-stu-id="a6757-152">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![Unity con el objeto Menu seleccionado y el objeto ButtonCollection expandido](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="a6757-154">Cambie el nombre del primer botón en ButtonCollection por Indicator y, a continuación, en la ventana Inspector, configure el componente Button Config Helper (Script) (Asistente de configuración del botón [script]) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a6757-154">Rename the first button in the ButtonCollection to Indicator, then in the Inspector window, configure the Button Config Helper (Script) component as follows:</span></span>

* <span data-ttu-id="a6757-155">Cambie el **texto de la etiqueta principal** para que coincida con el nombre del botón.</span><span class="sxs-lookup"><span data-stu-id="a6757-155">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="a6757-156">Asigne el objeto Indicator, que parece un cheurón, al campo None (Object) (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="a6757-156">Assign the Indicator object that looks like a chevron, to the None (Object) field</span></span>
* <span data-ttu-id="a6757-157">En la lista desplegable **No Function** (Ninguna función), seleccione **GameObject** > **SetActive (bool)** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="a6757-157">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="a6757-158">Compruebe que la casilla del argumento esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="a6757-158">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="a6757-159">Cambie el **icono** al icono de "búsqueda".</span><span class="sxs-lookup"><span data-stu-id="a6757-159">Change the **Icon** to the 'search' icon</span></span>

![Unity con el objeto de botón Indicator con Button Config Helper configurado](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="a6757-161">Para deshabilitar el objeto Indicator en forma de cheurón, en la ventana Hierarchy (Jerarquía), seleccione el objeto Indicator similar a un cheurón y, a continuación, en la ventana Inspector:</span><span class="sxs-lookup"><span data-stu-id="a6757-161">To disable the chevron Indicator object, in the Hierarchy window, select the Indicator object that looks like chevron, then in the Inspector window:</span></span>

* <span data-ttu-id="a6757-162">Desactive la casilla situada junto a su nombre para que esté inactivo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a6757-162">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="a6757-163">Use el botón **Agregar componente** para agregar el componente **Controlador del indicador de dirección (Script)** .</span><span class="sxs-lookup"><span data-stu-id="a6757-163">Use the **Add Component** button to add the **Directional Indicator Controller (Script)** component</span></span>

![Unity con el objeto Indicator seleccionado, deshabilitado, y el componente DirectionalIndicatorController agregado](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="a6757-165">Ahora, cuando se inicia la aplicación, el objeto Indicator en forma de cheurón está deshabilitado de forma predeterminada y se puede habilitar presionando el botón Indicator.</span><span class="sxs-lookup"><span data-stu-id="a6757-165">Now, when the app starts, the chevron Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

> [!NOTE]
> <span data-ttu-id="a6757-166">El componente Directional Indicator Controller (Script) (Controlador de indicador direccional [script]) no forma parte de MRTK, pero se incluyó con los recursos del tutorial.</span><span class="sxs-lookup"><span data-stu-id="a6757-166">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="a6757-167">Cambie el nombre del segundo botón por **TapToPlace** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a6757-167">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="a6757-168">Cambie el **texto de la etiqueta principal** para que coincida con el nombre del botón.</span><span class="sxs-lookup"><span data-stu-id="a6757-168">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="a6757-169">Asigne el objeto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="a6757-169">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a6757-170">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool Enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="a6757-170">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="a6757-171">Compruebe que la casilla del argumento esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="a6757-171">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="a6757-172">Cambie el **icono** al icono de "mano con rayo".</span><span class="sxs-lookup"><span data-stu-id="a6757-172">Change the **Icon** to the 'hand with ray' icon</span></span>

![Unity con el objeto de botón TapToPlace con Button Config Helper configurado](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="a6757-174">En la ventana Jerarquía, seleccione el objeto **RoverAssembly** y, a continuación, en la ventana Inspector, configure el componente **Tap To Place (Script)** (Pulsar para colocar [Script]) del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a6757-174">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="a6757-175">Desactive la casilla situada junto a su nombre para que esté inactivo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a6757-175">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="a6757-176">En la sección del evento **On Placing Stopped ()** , haga clic en el icono **+** para agregar un nuevo evento:</span><span class="sxs-lookup"><span data-stu-id="a6757-176">In the **On Placing Stopped ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="a6757-177">Asigne el objeto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="a6757-177">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a6757-178">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool Enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="a6757-178">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="a6757-179">Compruebe que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="a6757-179">Verify that the argument checkbox is **unchecked**</span></span>

![Unity con el componente TapToPlace reconfigurado](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="a6757-181">Ahora, cuando se inicia la aplicación, la funcionalidad Tap to Place (Tocar para colocar) está deshabilitada de forma predeterminada y se puede habilitar presionando el botón Tap to Place.</span><span class="sxs-lookup"><span data-stu-id="a6757-181">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="a6757-182">Además, cuando se complete la acción de tocar para colocar, se deshabilitará.</span><span class="sxs-lookup"><span data-stu-id="a6757-182">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="a6757-183">Agregación de texto a la escena</span><span class="sxs-lookup"><span data-stu-id="a6757-183">Adding text to the scene</span></span>

<span data-ttu-id="a6757-184">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **Table** (Tabla) y seleccione **3D Object** > **Text - TextMeshPro** (Objeto 3D > Texto - TextMeshPro) para agregar un objeto de texto como elemento secundario del objeto Table y, a continuación, en la ventana Inspector, configure el componente **Rect Transform** (Transformación rectangular) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="a6757-184">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="a6757-185">Cambie **Pos Y** (Posición Y) a 1.</span><span class="sxs-lookup"><span data-stu-id="a6757-185">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="a6757-186">Cambie **Width** (Ancho) a 1.</span><span class="sxs-lookup"><span data-stu-id="a6757-186">Change **Width** to 1</span></span>
* <span data-ttu-id="a6757-187">Cambie **Height** (Altura) a 1.</span><span class="sxs-lookup"><span data-stu-id="a6757-187">Change **Height** to 1</span></span>
* <span data-ttu-id="a6757-188">Cambie **Rotation X** (Rotación X) a 90.</span><span class="sxs-lookup"><span data-stu-id="a6757-188">Change **Rotation X** to 90</span></span>

![Unity con el objeto TextMeshPro recién creado seleccionado](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="a6757-190">A continuación, configure el componente **TextMeshPro - Text** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="a6757-190">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="a6757-191">Cambie **Text** (Texto) a Rover Explorer.</span><span class="sxs-lookup"><span data-stu-id="a6757-191">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="a6757-192">Cambie **Font Style** (Estilo de fuente) a Bold (Negrita).</span><span class="sxs-lookup"><span data-stu-id="a6757-192">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="a6757-193">Cambie **Font Size** (Tamaño de fuente) a 1.</span><span class="sxs-lookup"><span data-stu-id="a6757-193">Change **Font Size** to 1</span></span>
* <span data-ttu-id="a6757-194">Cambie Extra Settings > **Margins** (Configuración adicional > Márgenes) a 0.03.</span><span class="sxs-lookup"><span data-stu-id="a6757-194">Change Extra Settings > **Margins** to 0.03</span></span>

![Unity con el componente TextMeshPro configurado](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="a6757-196">Agregación de información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="a6757-196">Adding tooltips</span></span>

<span data-ttu-id="a6757-197">En la ventana Project (Proyecto), vaya a la carpeta **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Paquetes > Mixed Reality Toolkit Foundation > SDK > Características > Experiencia del usuario > Objetos prefabricados > Información sobre herramientas) para buscar los objetos prefabricados de información sobre herramientas:</span><span class="sxs-lookup"><span data-stu-id="a6757-197">In the Project window, navigate to the **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Ventana Project (Proyecto) de Unity con la carpeta ToolTips seleccionada](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="a6757-199">En la ventana Hierarchy (Jerarquía), expanda el objeto RoverExplorer > **RoverParts** y seleccione todos los objetos secundarios de partes, y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **ToolTipSpawner** y configúrelo de la forma siguiente:</span><span class="sxs-lookup"><span data-stu-id="a6757-199">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="a6757-200">Asegúrese de que la casilla de verificación **Focus enabled** (Enfoque habilitado) está activada para requerir que el usuario mire la parte para que aparezca la información sobre herramientas.</span><span class="sxs-lookup"><span data-stu-id="a6757-200">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="a6757-201">Asigne el elemento prefabricado **Simple Line ToolTip** (Información sobre herramientas de línea simple) desde la ventana Project (Proyecto) al campo **Prefab** (Elemento prefabricado).</span><span class="sxs-lookup"><span data-stu-id="a6757-201">Assign the **Simple Line ToolTip** prefab from the Project window to the **Prefab** field</span></span>
* <span data-ttu-id="a6757-202">Cambie ToolTip Override Settings > **Settings Mode** (Configuración de invalidación de información sobre herramientas > Modo de configuración) a **Override** (Invalidar).</span><span class="sxs-lookup"><span data-stu-id="a6757-202">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="a6757-203">Cambie ToolTip Override Settings > **Manual Pivot Local Position Y** (Configuración de invalidación de información sobre herramientas > Posición Y local del pivote manual) a **1.5**.</span><span class="sxs-lookup"><span data-stu-id="a6757-203">Change the ToolTip Override Settings > **Manual Pivot Local Position Y** to **1.5**</span></span>

![Unity con todos los objetos de partes del róver seleccionados y el componente ToolTipSpawner agregado y configurado](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="a6757-205">En la ventana Hierarchy (Jerarquía), seleccione Capmera_Part, RoverParts > **Camera_Part** y configure el componente **ToolTipSpawner** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="a6757-205">In the Hierarchy window, select the Camera_Part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="a6757-206">Cambie **Tool Tip Text** para reflejar el nombre de la parte; por ejemplo, **Camera**.</span><span class="sxs-lookup"><span data-stu-id="a6757-206">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![Unity con ToolTipText Camera configurado](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="a6757-208">**Repita** este paso para cada uno de los objetos de parte del rover para configurar el componente **ToolTipSpawner** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="a6757-208">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="a6757-209">Para **Generator_Part**, cambie **Tool Tip Text** a **Generator**.</span><span class="sxs-lookup"><span data-stu-id="a6757-209">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="a6757-210">Para **Lights_Part**, cambie **Tool Tip Text** a **Lights**.</span><span class="sxs-lookup"><span data-stu-id="a6757-210">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="a6757-211">Para **UHFAntenna_Part**, cambie **Tool Tip Text** a **UHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="a6757-211">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="a6757-212">Para **Spectrometer_Part**, cambie **Tool Tip Text** a **Spectrometer**.</span><span class="sxs-lookup"><span data-stu-id="a6757-212">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="a6757-213">Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionado el botón derecho del mouse mientras mueve el mouse hasta que la mirada entre en contacto con una de las partes y la información sobre herramientas de la parte se mostrará:</span><span class="sxs-lookup"><span data-stu-id="a6757-213">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![Vista dividida del modo de reproducción de Unity con información sobre herramientas desencadenada por la mirada](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="a6757-215">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="a6757-215">Congratulations</span></span>

<span data-ttu-id="a6757-216">En este tutorial, aprendió a crear una interfaz de usuario sencilla con los elementos prefabricados de botón y menú proporcionados por MRTK junto con el componente TextMeshPro de Unity y a configurar los botones para desencadenar eventos cuando se presionan.</span><span class="sxs-lookup"><span data-stu-id="a6757-216">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="a6757-217">También ha aprendido a agregar elementos dinámicos de información sobre herramientas en la interfaz de usuario para proporcionar información adicional al usuario.</span><span class="sxs-lookup"><span data-stu-id="a6757-217">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6757-218">Tutorial siguiente: 7. Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="a6757-218">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)
