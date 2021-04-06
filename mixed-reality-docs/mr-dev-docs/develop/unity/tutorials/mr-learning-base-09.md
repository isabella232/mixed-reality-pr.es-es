---
title: Uso de los comandos de voz
description: En este curso se muestra cómo configurar, crear y usar los comandos de voz en las aplicaciones de realidad mixta con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, speech commands, voice input
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982955"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="01f7f-104">9. Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="01f7f-104">9. Using speech commands</span></span>

<span data-ttu-id="01f7f-105">En este tutorial, aprenderá a crear comandos de voz y a controlarlos de forma global.</span><span class="sxs-lookup"><span data-stu-id="01f7f-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="01f7f-106">También aprenderá a controlar comandos de voz locales que requieren que el usuario vea el objeto que controla el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="01f7f-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="01f7f-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="01f7f-107">Objectives</span></span>

* <span data-ttu-id="01f7f-108">Aprender a crear comandos de voz</span><span class="sxs-lookup"><span data-stu-id="01f7f-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="01f7f-109">Aprender a controlar los comandos de voz global y localmente</span><span class="sxs-lookup"><span data-stu-id="01f7f-109">Learn how to control speech commands globally and locally</span></span>

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a><span data-ttu-id="01f7f-110">Creación de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="01f7f-110">Creating speech commands</span></span>

<span data-ttu-id="01f7f-111">En la ventana jerarquía, seleccione el objeto **MixedRealityToolkit**, a continuación, en la ventana Inspector, seleccione MixedRealityToolkit > pestaña **Input** (Entrada) y siga los pasos a continuación:</span><span class="sxs-lookup"><span data-stu-id="01f7f-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="01f7f-112">Expanda la sección **Speech** (Voz).</span><span class="sxs-lookup"><span data-stu-id="01f7f-112">Expand the **Speech** section</span></span>
* <span data-ttu-id="01f7f-113">Clone **DefaultMixedRealitySpeechCommandsProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealitySpeechCommandsProfile_.</span><span class="sxs-lookup"><span data-stu-id="01f7f-113">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="01f7f-114">Verifique que **Start Behaviour** (Iniciar comportamiento) está establecido en **Auto Start** (Inicio automático).</span><span class="sxs-lookup"><span data-stu-id="01f7f-114">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Creación de comandos de voz](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="01f7f-116">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="01f7f-116">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="01f7f-117">En Speech (Voz) > sección **Speech Commands** (Comandos de voz), haz clic en el botón **+ Add a New Speech Command** (Agregar nuevo comando de voz) cuatro veces para agregar cuatro nuevos comandos de voz a la lista de comandos de voz existentes y, a continuación, en el campo **Keyword** (Palabra clave), escriba las frases siguientes:</span><span class="sxs-lookup"><span data-stu-id="01f7f-117">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="01f7f-118">Enable Indicator (Habilitar indicador)</span><span class="sxs-lookup"><span data-stu-id="01f7f-118">Enable Indicator</span></span>
* <span data-ttu-id="01f7f-119">Enable Tap to Place (Habilitar pulsar para colocar)</span><span class="sxs-lookup"><span data-stu-id="01f7f-119">Enable Tap to Place</span></span>
* <span data-ttu-id="01f7f-120">Enable Bounds Control (Habilitar control de límites)</span><span class="sxs-lookup"><span data-stu-id="01f7f-120">Enable Bounds Control</span></span>
* <span data-ttu-id="01f7f-121">Disable Bounds Control (Deshabilitar control de límites)</span><span class="sxs-lookup"><span data-stu-id="01f7f-121">Disable Bounds Control</span></span>

![Adición de nuevos comandos de voz](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="01f7f-123">Si el equipo no tiene micrófono, puede asignar un KeyCode a los comandos de voz, lo que le permitirá desencadenarlos cuando se presione la tecla correspondiente.</span><span class="sxs-lookup"><span data-stu-id="01f7f-123">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="01f7f-124">Control de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="01f7f-124">Controlling speech commands</span></span>

<span data-ttu-id="01f7f-125">En la ventana Project (Proyecto), vaya a la carpeta **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Paquetes > Mixed Reality Toolkit Foundation > SDK > Características > Experiencia del usuario > Objetos prefabricados > Información sobre herramientas) para buscar los objetos prefabricados de información sobre herramientas:</span><span class="sxs-lookup"><span data-stu-id="01f7f-125">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Apertura de la carpeta de información sobre herramientas](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="01f7f-127">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena.</span><span class="sxs-lookup"><span data-stu-id="01f7f-127">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="01f7f-128">Asigna al objeto el nombre **SpeechInputHandler_Global** y, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **SpeechInputHandler** y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="01f7f-128">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="01f7f-129">**Desactive** la casilla **Is Focus Required** (Se requiere foco) para que no sea necesario que el usuario observe el objeto con el componente SpeechInputHandler para desencadenar el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="01f7f-129">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="01f7f-130">En la ventana Project (Proyecto), asigne el objeto prefabricado **SpeechConfirmation Tooltip** (Información sobre herramientas de SpeechConfirmation) al campo **Confirmation Tooltip Prefab** (Objeto prefabricado de información sobre herramientas de confirmación de voz) para que este objeto prefabricado aparezca cuando se reconozca un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="01f7f-130">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Configuración del componente de controlador de entrada de voz](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="01f7f-132">En el componente SpeechInputHandler, haga clic en el icono pequeño **+** tres veces para agregar tres elementos de palabra clave:</span><span class="sxs-lookup"><span data-stu-id="01f7f-132">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Adición de elementos de palabra clave al controlador de entrada de voz](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="01f7f-134">Expanda **Element 0** (Elemento 0) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="01f7f-134">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="01f7f-135">En el campo **Keyword** (Palabra clave), escriba **Enable Indicator** (Habilitar indicador) para hacer referencia al comando de voz Enable Indicator que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="01f7f-135">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="01f7f-136">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-136">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="01f7f-137">En la ventana Hierarchy (Jerarquía), asigne el objeto **Indicator** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="01f7f-137">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="01f7f-138">En la lista desplegable **No Function** (Ninguna función), seleccione **GameObject** > **SetActive (bool)** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-138">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="01f7f-139">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="01f7f-139">Check the argument checkbox, so it is **checked**</span></span>

![Configuración del elemento de palabra clave 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="01f7f-141">Expanda **Element 1** (Elemento 1) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="01f7f-141">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="01f7f-142">En el campo **Keyword** (Palabra clave), escriba **Enable Bounds Control** (Habilitar control de límites) para hacer referencia al comando Enable Bounds Control que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="01f7f-142">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="01f7f-143">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="01f7f-144">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="01f7f-144">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="01f7f-145">En la lista desplegable **No Function** (Ninguna función), seleccione **BoundsControl** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento</span><span class="sxs-lookup"><span data-stu-id="01f7f-145">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="01f7f-146">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="01f7f-146">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="01f7f-147">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-147">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="01f7f-148">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="01f7f-148">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="01f7f-149">En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-149">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="01f7f-150">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="01f7f-150">Check the argument checkbox, so it is **checked**</span></span>

![Configuración del elemento de palabra clave 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="01f7f-152">Expanda **Element 2** (Elemento 2) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="01f7f-152">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="01f7f-153">En el campo **Keyword** (Palabra clave), escriba **Disable Bounds Control** (Deshabilitar control de límites) para hacer referencia al comando Disable Bounds Control que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="01f7f-153">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="01f7f-154">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-154">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="01f7f-155">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="01f7f-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="01f7f-156">En la lista desplegable **No Function** (Ninguna función), seleccione **BoundsControl** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento</span><span class="sxs-lookup"><span data-stu-id="01f7f-156">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="01f7f-157">Verifique que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="01f7f-157">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="01f7f-158">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-158">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="01f7f-159">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="01f7f-159">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="01f7f-160">En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-160">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="01f7f-161">Verifique que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="01f7f-161">Verify that the argument checkbox is **unchecked**</span></span>

![Configuración del elemento de palabra clave 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="01f7f-163">En la ventana Hierarchy (Jerarquía), seleccione RoverExplorer > objeto **RoverAssembly** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **SpeechInputHandler** y configúrelo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="01f7f-163">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="01f7f-164">Verifique que la casilla **Is Focus Required** (Se requiere foco) esté **activada** para exigir que el usuario observe el objeto con el componente SpeechInputHandler, es decir, RoverAssembly, para desencadenar el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="01f7f-164">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="01f7f-165">En la ventana Project (Proyecto), asigne el objeto prefabricado **SpeechConfirmation Tooltip** (Información sobre herramientas de SpeechConfirmation) al campo **Confirmation Tooltip Prefab** (Objeto prefabricado de información sobre herramientas de confirmación de voz) para que este objeto prefabricado aparezca cuando se reconozca un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="01f7f-165">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Adición del controlador de entrada de voz al ensamblado del róver](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="01f7f-167">En el componente SpeechInputHandler, haga clic en el icono **+** pequeño para agregar un elemento de palabra clave, expanda el elemento recién creado y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="01f7f-167">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="01f7f-168">En el campo **Keyword** (Palabra clave), escriba **Enable Tap to Place** (Habilitar pulsar para colocar) para hacer referencia al comando de voz Enable Tap to Place que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="01f7f-168">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="01f7f-169">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-169">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="01f7f-170">En la ventana Hierarchy (Jerarquía), asigne el propio objeto, es decir, el mismo objeto **RoverAssembly**, al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="01f7f-170">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="01f7f-171">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-171">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="01f7f-172">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="01f7f-172">Check the argument checkbox, so it is **checked**</span></span>

![Configuración del controlador de entrada de voz en el ensamblado del róver](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="01f7f-174">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="01f7f-174">Congratulations</span></span>

<span data-ttu-id="01f7f-175">En este tutorial, ha aprendido a crear comandos de voz y a controlarlos de forma global.</span><span class="sxs-lookup"><span data-stu-id="01f7f-175">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="01f7f-176">También ha aprendido a controlar comandos de voz locales que requieren que el usuario vea el objeto que controla el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="01f7f-176">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="01f7f-177">Esto también concluye la serie de [tutoriales de introducción](mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="01f7f-177">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="01f7f-178">A través de estos tutoriales, ha creado correctamente una experiencia de realidad mixta completa desde cero con MRTK.</span><span class="sxs-lookup"><span data-stu-id="01f7f-178">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="01f7f-179">En las siguientes dos series de tutoriales, [Tutoriales de Azure Spatial Anchors](mr-learning-asa-01.md) y [Tutoriales de funcionalidades para varios usuarios](mr-learning-sharing-01.md), primero aprenderá a integrar Azure Spatial Anchors en el proyecto para anclar la experiencia del explorador de róver que creó en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="01f7f-179">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="01f7f-180">A continuación, aprenderá a agregar funcionalidades de varios usuarios al proyecto para compartir movimientos de usuarios y objetos en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="01f7f-180">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="01f7f-181">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="01f7f-181">Next Development Checkpoint</span></span>

<span data-ttu-id="01f7f-182">Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, la siguiente tarea consiste en familiarizarse con los principales bloques de creación de aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="01f7f-182">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="01f7f-183">Interacciones básicas</span><span class="sxs-lookup"><span data-stu-id="01f7f-183">Basic interactions</span></span>](../../../out-of-scope/mrtk-101.md)

<span data-ttu-id="01f7f-184">Puede volver a los [puntos de control de desarrollo de Unity](../unity-development-overview.md#1-getting-started) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="01f7f-184">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>