---
title: Uso de los comandos de voz
description: En este curso se muestra cómo configurar, crear y usar los comandos de voz en las aplicaciones de realidad mixta con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, speech commands, voice input
ms.localizationpriority: high
ms.openlocfilehash: c87f3bb801b2fc32ed1aa42f2a4754bc83320587
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550255"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="2ee5d-104">9. Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="2ee5d-104">9. Using speech commands</span></span>

<span data-ttu-id="2ee5d-105">En este tutorial, aprenderá a crear comandos de voz y a controlarlos de forma global.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="2ee5d-106">También aprenderá a controlar comandos de voz locales que requieren que el usuario vea el objeto que controla el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="2ee5d-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2ee5d-107">Objectives</span></span>

* <span data-ttu-id="2ee5d-108">Aprender a crear comandos de voz</span><span class="sxs-lookup"><span data-stu-id="2ee5d-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="2ee5d-109">Aprender a controlar los comandos de voz global y localmente</span><span class="sxs-lookup"><span data-stu-id="2ee5d-109">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="2ee5d-110">Asegurarse de que la funcionalidad del micrófono está habilitada</span><span class="sxs-lookup"><span data-stu-id="2ee5d-110">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="2ee5d-111">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Microphone Capability** (Habilitar funcionalidad del micrófono) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Enable microphone capability (Habilitar la funcionalidad del micrófono)](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2ee5d-113">La funcionalidad del micrófono debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](mr-learning-base-02.md#creating-and-configuring-the-scene) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-113">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="2ee5d-114">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="2ee5d-115">Creación de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="2ee5d-115">Creating speech commands</span></span>

<span data-ttu-id="2ee5d-116">En la ventana jerarquía, seleccione el objeto **MixedRealityToolkit**, a continuación, en la ventana Inspector, seleccione MixedRealityToolkit > pestaña **Input** (Entrada) y siga los pasos a continuación:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="2ee5d-117">Expanda la sección **Speech** (Voz).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-117">Expand the **Speech** section</span></span>
* <span data-ttu-id="2ee5d-118">Clone **DefaultMixedRealitySpeechCommandsProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealitySpeechCommandsProfile_.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-118">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="2ee5d-119">Verifique que **Start Behaviour** (Iniciar comportamiento) está establecido en **Auto Start** (Inicio automático).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-119">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Creación de comandos de voz](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="2ee5d-121">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-121">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="2ee5d-122">En Speech (Voz) > sección **Speech Commands** (Comandos de voz), haz clic en el botón **+ Add a New Speech Command** (Agregar nuevo comando de voz) cuatro veces para agregar cuatro nuevos comandos de voz a la lista de comandos de voz existentes y, a continuación, en el campo **Keyword** (Palabra clave), escriba las frases siguientes:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-122">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="2ee5d-123">Enable Indicator (Habilitar indicador)</span><span class="sxs-lookup"><span data-stu-id="2ee5d-123">Enable Indicator</span></span>
* <span data-ttu-id="2ee5d-124">Enable Tap to Place (Habilitar pulsar para colocar)</span><span class="sxs-lookup"><span data-stu-id="2ee5d-124">Enable Tap to Place</span></span>
* <span data-ttu-id="2ee5d-125">Enable Bounds Control (Habilitar control de límites)</span><span class="sxs-lookup"><span data-stu-id="2ee5d-125">Enable Bounds Control</span></span>
* <span data-ttu-id="2ee5d-126">Disable Bounds Control (Deshabilitar control de límites)</span><span class="sxs-lookup"><span data-stu-id="2ee5d-126">Disable Bounds Control</span></span>

![Adición de nuevos comandos de voz](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="2ee5d-128">Si el equipo no tiene micrófono, puede asignar un KeyCode a los comandos de voz, lo que le permitirá desencadenarlos cuando se presione la tecla correspondiente.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-128">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="2ee5d-129">Control de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="2ee5d-129">Controlling speech commands</span></span>

<span data-ttu-id="2ee5d-130">En la ventana Project (Proyecto), vaya a la carpeta **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Paquetes > Mixed Reality Toolkit Foundation > SDK > Características > Experiencia del usuario > Objetos prefabricados > Información sobre herramientas) para buscar los objetos prefabricados de información sobre herramientas:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-130">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Apertura de la carpeta de información sobre herramientas](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="2ee5d-132">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-132">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="2ee5d-133">Asigna al objeto el nombre **SpeechInputHandler_Global** y, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **SpeechInputHandler** y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-133">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="2ee5d-134">**Desactive** la casilla **Is Focus Required** (Se requiere foco) para que no sea necesario que el usuario observe el objeto con el componente SpeechInputHandler para desencadenar el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-134">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="2ee5d-135">En la ventana Project (Proyecto), asigne el objeto prefabricado **SpeechConfirmation Tooltip** (Información sobre herramientas de SpeechConfirmation) al campo **Confirmation Tooltip Prefab** (Objeto prefabricado de información sobre herramientas de confirmación de voz) para que este objeto prefabricado aparezca cuando se reconozca un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-135">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Configuración del componente de controlador de entrada de voz](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="2ee5d-137">En el componente SpeechInputHandler, haga clic en el icono pequeño **+** tres veces para agregar tres elementos de palabra clave:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-137">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Adición de elementos de palabra clave al controlador de entrada de voz](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="2ee5d-139">Expanda **Element 0** (Elemento 0) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-139">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="2ee5d-140">En el campo **Keyword** (Palabra clave), escriba **Enable Indicator** (Habilitar indicador) para hacer referencia al comando de voz Enable Indicator que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-140">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="2ee5d-141">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-141">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="2ee5d-142">En la ventana Hierarchy (Jerarquía), asigne el objeto **Indicator** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-142">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="2ee5d-143">En la lista desplegable **No Function** (Ninguna función), seleccione **GameObject** > **SetActive (bool)** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-143">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="2ee5d-144">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-144">Check the argument checkbox, so it is **checked**</span></span>

![Configuración del elemento de palabra clave 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="2ee5d-146">Expanda **Element 1** (Elemento 1) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-146">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="2ee5d-147">En el campo **Keyword** (Palabra clave), escriba **Enable Bounds Control** (Habilitar control de límites) para hacer referencia al comando Enable Bounds Control que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-147">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="2ee5d-148">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-148">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="2ee5d-149">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-149">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="2ee5d-150">En la lista desplegable **No Function** (Ninguna función), seleccione **BoundsControl** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento</span><span class="sxs-lookup"><span data-stu-id="2ee5d-150">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="2ee5d-151">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-151">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="2ee5d-152">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-152">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="2ee5d-153">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-153">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="2ee5d-154">En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-154">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="2ee5d-155">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-155">Check the argument checkbox, so it is **checked**</span></span>

![Configuración del elemento de palabra clave 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="2ee5d-157">Expanda **Element 2** (Elemento 2) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-157">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="2ee5d-158">En el campo **Keyword** (Palabra clave), escriba **Disable Bounds Control** (Deshabilitar control de límites) para hacer referencia al comando Disable Bounds Control que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-158">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="2ee5d-159">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-159">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="2ee5d-160">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-160">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="2ee5d-161">En la lista desplegable **No Function** (Ninguna función), seleccione **BoundsControl** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento</span><span class="sxs-lookup"><span data-stu-id="2ee5d-161">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="2ee5d-162">Verifique que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-162">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="2ee5d-163">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-163">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="2ee5d-164">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-164">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="2ee5d-165">En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-165">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="2ee5d-166">Verifique que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-166">Verify that the argument checkbox is **unchecked**</span></span>

![Configuración del elemento de palabra clave 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="2ee5d-168">En la ventana Hierarchy (Jerarquía), seleccione RoverExplorer > objeto **RoverAssembly** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **SpeechInputHandler** y configúrelo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-168">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="2ee5d-169">Verifique que la casilla **Is Focus Required** (Se requiere foco) esté **activada** para exigir que el usuario observe el objeto con el componente SpeechInputHandler, es decir, RoverAssembly, para desencadenar el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-169">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="2ee5d-170">En la ventana Project (Proyecto), asigne el objeto prefabricado **SpeechConfirmation Tooltip** (Información sobre herramientas de SpeechConfirmation) al campo **Confirmation Tooltip Prefab** (Objeto prefabricado de información sobre herramientas de confirmación de voz) para que este objeto prefabricado aparezca cuando se reconozca un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-170">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Adición del controlador de entrada de voz al ensamblado del róver](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="2ee5d-172">En el componente SpeechInputHandler, haga clic en el icono **+** pequeño para agregar un elemento de palabra clave, expanda el elemento recién creado y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="2ee5d-172">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="2ee5d-173">En el campo **Keyword** (Palabra clave), escriba **Enable Tap to Place** (Habilitar pulsar para colocar) para hacer referencia al comando de voz Enable Tap to Place que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-173">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="2ee5d-174">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-174">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="2ee5d-175">En la ventana Hierarchy (Jerarquía), asigne el propio objeto, es decir, el mismo objeto **RoverAssembly**, al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-175">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="2ee5d-176">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-176">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="2ee5d-177">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-177">Check the argument checkbox, so it is **checked**</span></span>

![Configuración del controlador de entrada de voz en el ensamblado del róver](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="2ee5d-179">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2ee5d-179">Congratulations</span></span>

<span data-ttu-id="2ee5d-180">En este tutorial, ha aprendido a crear comandos de voz y a controlarlos de forma global.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-180">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="2ee5d-181">También ha aprendido a controlar comandos de voz locales que requieren que el usuario vea el objeto que controla el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-181">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="2ee5d-182">Esto también concluye la serie de [tutoriales de introducción](mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5d-182">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="2ee5d-183">A través de estos tutoriales, ha creado correctamente una experiencia de realidad mixta completa desde cero con MRTK.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-183">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="2ee5d-184">En las siguientes dos series de tutoriales, [Tutoriales de Azure Spatial Anchors](mr-learning-asa-01.md) y [Tutoriales de funcionalidades para varios usuarios](mr-learning-sharing-01.md), primero aprenderá a integrar Azure Spatial Anchors en el proyecto para anclar la experiencia del explorador de róver que creó en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-184">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="2ee5d-185">A continuación, aprenderá a agregar funcionalidades de varios usuarios al proyecto para compartir movimientos de usuarios y objetos en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-185">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2ee5d-186">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="2ee5d-186">Next Development Checkpoint</span></span>

<span data-ttu-id="2ee5d-187">Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, la siguiente tarea consiste en familiarizarse con los principales bloques de creación de aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-187">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ee5d-188">Interacciones básicas</span><span class="sxs-lookup"><span data-stu-id="2ee5d-188">Basic interactions</span></span>](../../../out-of-scope/mrtk-101.md)

<span data-ttu-id="2ee5d-189">Puede volver a los [puntos de control de desarrollo de Unity](../unity-development-overview.md#1-getting-started) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="2ee5d-189">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>