---
title: Configuración de reconocimiento de intenciones y comprensión del lenguaje natural
description: Complete este curso para aprender a configurar la comprensión del lenguaje natural y la intención en las aplicaciones de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, speech recognition, Windows 10, LUIS, LUIS portal, intent, entities, utterances, natural language understanding
ms.localizationpriority: high
ms.openlocfilehash: 49e2b44000add22e924d9552f60b63ac1ac30288
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590367"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="2f491-104">4. Configuración de reconocimiento de intenciones y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="2f491-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="2f491-105">En este tutorial, explorarás el reconocimiento de la intención del servicio Voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="2f491-105">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="2f491-106">El reconocimiento de la intención te permite equipar nuestra aplicación con comandos de voz con tecnología de IA que permite a los usuarios indicar comandos de voz no específicos y conseguir, igualmente, que les entienda el sistema.</span><span class="sxs-lookup"><span data-stu-id="2f491-106">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="2f491-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2f491-107">Objectives</span></span>

* <span data-ttu-id="2f491-108">Aprender a configurar la intención, las entidades y las expresiones en el portal de LUIS</span><span class="sxs-lookup"><span data-stu-id="2f491-108">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="2f491-109">Aprender a implementar la comprensión del lenguaje natural y la intención en nuestra aplicación</span><span class="sxs-lookup"><span data-stu-id="2f491-109">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="2f491-110">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="2f491-110">Preparing the scene</span></span>

<span data-ttu-id="2f491-111">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Intent Recognizer (Script)** (Reconocimiento de la intención de Lunarcom [script]):</span><span class="sxs-lookup"><span data-stu-id="2f491-111">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="2f491-113">En la ventana Project (Proyecto), navega hasta la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** (Recursos > MRTK.Tutorials.GettingStarted > Objetos prefabricados > RocketLauncher), arrastra el objeto prefabricado **RocketLauncher_Complete** a la ventana Hierarchy (Jerarquía) y, a continuación, colócalo en una ubicación adecuada; por ejemplo, delante de la cámara:</span><span class="sxs-lookup"><span data-stu-id="2f491-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="2f491-114">Transforma el valor de **Position** (Posición) X = 0, Y = 0,4, Z = 1</span><span class="sxs-lookup"><span data-stu-id="2f491-114">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="2f491-115">Transforma el valor de **Rotation** (Giro) X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2f491-115">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="2f491-117">En la ventana Hierarchy (Jerarquía), selecciona de nuevo el objeto **Lunarcom**, expande el objeto **RocketLauncher_Complete** > **Button** (Botón) y asigna cada uno de los objetos secundarios del objeto **Buttons** (Botones) al campo **Lunar Launcher Buttons** (Botones del lanzacohetes lunar):</span><span class="sxs-lookup"><span data-stu-id="2f491-117">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="2f491-119">Creación del recurso de Azure Language Understanding</span><span class="sxs-lookup"><span data-stu-id="2f491-119">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="2f491-120">En esta sección, crearás un recurso de predicción de Azure para la aplicación de Language Understanding Intelligent Service (LUIS) que crearás en la próxima sección.</span><span class="sxs-lookup"><span data-stu-id="2f491-120">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="2f491-121">Inicia sesión en <a href="https://portal.azure.com" target="_blank">Azure</a> y haz clic en **Crear un recurso**.</span><span class="sxs-lookup"><span data-stu-id="2f491-121">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="2f491-122">A continuación, busca y selecciona **Language Understanding**:</span><span class="sxs-lookup"><span data-stu-id="2f491-122">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="2f491-124">Haz clic en el botón **Crear** para crear una instancia de este servicio:</span><span class="sxs-lookup"><span data-stu-id="2f491-124">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="2f491-126">En la página Crear, haz clic en la opción **Predicción** y escribe los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="2f491-126">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="2f491-127">En **Suscripción**, selecciona **Free Trail** (Prueba gratuita) si tienes una suscripción de prueba. De lo contrario, selecciona una de las otras suscripciones.</span><span class="sxs-lookup"><span data-stu-id="2f491-127">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="2f491-128">Para **Grupo de recursos**, haga clic en el vínculo **Crear nuevo**, escriba un nombre adecuado; por ejemplo, *MRKT-Tutorials* y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="2f491-128">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click on **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="2f491-130">En el momento de redactar este documento, no es necesario crear un recurso de creación porque se generará automáticamente una clave de prueba de creación en LUIS cuando crees Language Understanding Intelligent Service (LUIS) en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="2f491-130">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="2f491-131">Si ya tienes otro grupo de recursos adecuado en tu cuenta de Azure; por ejemplo, si completaste el tutorial de [Azure Spatial Anchors](mr-learning-asa-01.md), puedes usar este grupo de recursos en lugar de crear uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="2f491-131">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mr-learning-asa-01.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="2f491-132">Mientras sigues en la página Crear, escribe los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="2f491-132">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="2f491-133">En **Nombre**, escribe un nombre adecuado para el servicio; por ejemplo, *MRTK-tutoriales-AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="2f491-133">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="2f491-134">Para **Ubicación de la predicción**, elige una ubicación cercana a la ubicación física de los usuarios de la aplicación; por ejemplo,  *(EE. UU.) Oeste de EE. UU.*</span><span class="sxs-lookup"><span data-stu-id="2f491-134">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="2f491-135">Para **Plan de tarifa de predicción**, para los fines de este tutorial, selecciona **F0 (5 llamadas por segundo, 10 000 llamadas al mes)** .</span><span class="sxs-lookup"><span data-stu-id="2f491-135">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="2f491-137">A continuación, haga clic en la pestaña **Revisar y crear**, revise los detalles y haga clic en el botón **Crear** situado en la parte inferior de la página para crear el recurso, así como el nuevo grupo de recursos, si configuró alguno para su creación:</span><span class="sxs-lookup"><span data-stu-id="2f491-137">Next, click on **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="2f491-139">Después de hacer clic en el botón Crear, tendrás que esperar a que se cree el servicio, lo que puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="2f491-139">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="2f491-140">Una vez completado el proceso de creación de recursos, se mostrará el mensaje **Se completó la implementación**:</span><span class="sxs-lookup"><span data-stu-id="2f491-140">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="2f491-142">Creación de Language Understanding Intelligent Service (LUIS)</span><span class="sxs-lookup"><span data-stu-id="2f491-142">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="2f491-143">En esta sección, crearás una aplicación de LUIS, configurarás y entrenarás su modelo de predicción y lo conectará al recurso de predicción de Azure que creaste en el paso anterior.</span><span class="sxs-lookup"><span data-stu-id="2f491-143">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="2f491-144">En concreto, crearás una intención: si el usuario dice que se debe realizar una acción, la aplicación desencadenará el evento Interactable.OnClick() en uno de los tres botones rojos de la escena, dependiendo del botón al que haga referencia el usuario.</span><span class="sxs-lookup"><span data-stu-id="2f491-144">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="2f491-145">Por ejemplo, si el usuario dice **go ahead and launch the rocket** (adelante, lanza el cohete), la aplicación predecirá que **adelante** significa que se debe realizar alguna **acción** y que el evento Interactable.OnClick() de **destino** está en el botón **launch** (lanzar).</span><span class="sxs-lookup"><span data-stu-id="2f491-145">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="2f491-146">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="2f491-146">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2f491-147">Crear una aplicación de LUIS</span><span class="sxs-lookup"><span data-stu-id="2f491-147">Create a LUIS app</span></span>
2. <span data-ttu-id="2f491-148">Crear intenciones</span><span class="sxs-lookup"><span data-stu-id="2f491-148">Create intents</span></span>
3. <span data-ttu-id="2f491-149">Crear expresiones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="2f491-149">Create example utterances</span></span>
4. <span data-ttu-id="2f491-150">Crear entidades</span><span class="sxs-lookup"><span data-stu-id="2f491-150">Create entities</span></span>
5. <span data-ttu-id="2f491-151">Asignar entidades a las expresiones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="2f491-151">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="2f491-152">Entrenar, probar y publicar la aplicación</span><span class="sxs-lookup"><span data-stu-id="2f491-152">Train, test, and publish the app</span></span>
7. <span data-ttu-id="2f491-153">Asignar un recurso de predicción de Azure a la aplicación</span><span class="sxs-lookup"><span data-stu-id="2f491-153">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="2f491-154">1. Crear una aplicación de LUIS</span><span class="sxs-lookup"><span data-stu-id="2f491-154">1. Create a LUIS app</span></span>

<span data-ttu-id="2f491-155">Con la misma cuenta de usuario que usaste para crear el recurso de Azure en la sección anterior, inicia sesión en <a href="https://www.luis.ai" target="_blank">LUIS</a>, selecciona tu país y acepta los términos de uso.</span><span class="sxs-lookup"><span data-stu-id="2f491-155">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="2f491-156">En el paso siguiente, cuando se te pida **vincular la cuenta de Azure**, elige **Continuar usando la clave de prueba** para usar un recurso de creación de Azure en su lugar.</span><span class="sxs-lookup"><span data-stu-id="2f491-156">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="2f491-157">Si ya te has registrado en LUIS y ha expirado la clave de prueba de creación, puedes consultar la documentación [Migración a una clave de creación de recursos de Azure](/azure/cognitive-services/luis/luis-migration-authoring) para cambiar el recurso de creación de LUIS a Azure.</span><span class="sxs-lookup"><span data-stu-id="2f491-157">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="2f491-158">Una vez iniciada la sesión, haga clic en **Nueva aplicación** y especifique los valores siguientes en la ventana emergente **Crear una aplicación**:</span><span class="sxs-lookup"><span data-stu-id="2f491-158">Once signed in, click **New app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="2f491-159">En **Nombre**, escribe un nombre adecuado; por ejemplo, *MRTK Tutorials - AzureSpeechServices*.</span><span class="sxs-lookup"><span data-stu-id="2f491-159">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="2f491-160">En **Referencia cultural**, selecciona **Inglés**</span><span class="sxs-lookup"><span data-stu-id="2f491-160">For **Culture**, select **English**</span></span>
* <span data-ttu-id="2f491-161">En **Descripción**, puedes escribir una descripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="2f491-161">For **Description**, optionally enter a suitable description</span></span>
* <span data-ttu-id="2f491-162">En **Recurso de predicción**, seleccione en la lista desplegable el recurso de predicción creado en Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="2f491-162">For **Prediction resource**, select the prediction resource by dropdown list that had been created azure portal.</span></span>

<span data-ttu-id="2f491-163">A continuación, haz clic en el botón **Listo** para crear la aplicación:</span><span class="sxs-lookup"><span data-stu-id="2f491-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="2f491-165">Una vez creada la aplicación, se te dirigirá a su página **Panel**:</span><span class="sxs-lookup"><span data-stu-id="2f491-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="2f491-167">2. Crear intenciones</span><span class="sxs-lookup"><span data-stu-id="2f491-167">2. Create intents</span></span>

<span data-ttu-id="2f491-168">Desde la página Panel, vaya a la página Compilación > Activos de la aplicación > **Intenciones**, haga clic en **Crear** y escriba el siguiente valor en la ventana emergente **Crear intención**:</span><span class="sxs-lookup"><span data-stu-id="2f491-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="2f491-169">En **Nombre de la intención**, escribe **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="2f491-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="2f491-170">A continuación, haz clic en el botón **Listo** para crear la nueva intención:</span><span class="sxs-lookup"><span data-stu-id="2f491-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="2f491-172">Para los fines de este tutorial, el proyecto de Unity hará referencia a esta intención por su nombre, "PressButton".</span><span class="sxs-lookup"><span data-stu-id="2f491-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="2f491-173">Por lo tanto, es muy importante que asignes exactamente el mismo nombre a la intención.</span><span class="sxs-lookup"><span data-stu-id="2f491-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="2f491-174">Una vez creada la intención, se te dirigirá a su página:</span><span class="sxs-lookup"><span data-stu-id="2f491-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="2f491-176">3. Crear expresiones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="2f491-176">3. Create example utterances</span></span>

<span data-ttu-id="2f491-177">En la lista **Expresión de ejemplo** de la intención **PressButton**, agrega las siguientes expresiones de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="2f491-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="2f491-178">activate launch sequence (activar secuencia de lanzamiento)</span><span class="sxs-lookup"><span data-stu-id="2f491-178">activate launch sequence</span></span>
* <span data-ttu-id="2f491-179">show me a placement hint (mostrar sugerencia de selección de ubicación)</span><span class="sxs-lookup"><span data-stu-id="2f491-179">show me a placement hint</span></span>
* <span data-ttu-id="2f491-180">initiate the launch sequence (iniciar secuencia de lanzamiento)</span><span class="sxs-lookup"><span data-stu-id="2f491-180">initiate the launch sequence</span></span>
* <span data-ttu-id="2f491-181">press placement hints button (presionar botón de sugerencias)</span><span class="sxs-lookup"><span data-stu-id="2f491-181">press placement hints button</span></span>
* <span data-ttu-id="2f491-182">give me a hint (proporcionar sugerencia)</span><span class="sxs-lookup"><span data-stu-id="2f491-182">give me a hint</span></span>
* <span data-ttu-id="2f491-183">push the launch button (presionar botón de lanzamiento)</span><span class="sxs-lookup"><span data-stu-id="2f491-183">push the launch button</span></span>
* <span data-ttu-id="2f491-184">i need a hint (necesito una sugerencia)</span><span class="sxs-lookup"><span data-stu-id="2f491-184">i need a hint</span></span>
* <span data-ttu-id="2f491-185">press the reset button (presionar botón de restablecimiento)</span><span class="sxs-lookup"><span data-stu-id="2f491-185">press the reset button</span></span>
* <span data-ttu-id="2f491-186">time to reset the experience (hora de restablecer la experiencia)</span><span class="sxs-lookup"><span data-stu-id="2f491-186">time to reset the experience</span></span>
* <span data-ttu-id="2f491-187">go ahead and launch the rocket (adelante, lanza el cohete)</span><span class="sxs-lookup"><span data-stu-id="2f491-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="2f491-188">Una vez agregadas todas las expresiones de ejemplo, la página de la intención PressButton debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="2f491-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="2f491-190">Para los fines de este tutorial, el proyecto de Unity hará referencia a las palabras "hint" (sugerencia), "hints" (sugerencias), "reset" (restablecimiento) y "launch" (lanzar).</span><span class="sxs-lookup"><span data-stu-id="2f491-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="2f491-191">Por lo tanto, es muy importante que escribas estas palabras exactamente de la misma manera.</span><span class="sxs-lookup"><span data-stu-id="2f491-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="2f491-192">4. Crear entidades</span><span class="sxs-lookup"><span data-stu-id="2f491-192">4. Create entities</span></span>

<span data-ttu-id="2f491-193">Desde la página de la intención PressButton, vaya a la página Compilación > Activos de la aplicación > **Entidades**, haga clic en **Crear** y escriba los valores siguientes en la ventana emergente **Crear una nueva entidad**:</span><span class="sxs-lookup"><span data-stu-id="2f491-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="2f491-194">En **Nombre de entidad**, escribe **Action**.</span><span class="sxs-lookup"><span data-stu-id="2f491-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="2f491-195">En **Tipo de entidad**, seleccione **Machine learned** (De aprendizaje automático).</span><span class="sxs-lookup"><span data-stu-id="2f491-195">For **Entity type**, select **Machine learned**</span></span>

<span data-ttu-id="2f491-196">A continuación, haga clic en el botón **Crear** para crear la nueva entidad:</span><span class="sxs-lookup"><span data-stu-id="2f491-196">Then click the **Create** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="2f491-198">**Repite** el paso anterior para crear otra entidad denominada **Target**. De este modo, tendrás dos entidades denominadas Action y Target:</span><span class="sxs-lookup"><span data-stu-id="2f491-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="2f491-200">Para los fines de este tutorial, el proyecto de Unity hará referencia a estas entidades por su nombre, "Action" y "Target".</span><span class="sxs-lookup"><span data-stu-id="2f491-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="2f491-201">Por lo tanto, es muy importante que asignes exactamente el mismo nombre a las entidades.</span><span class="sxs-lookup"><span data-stu-id="2f491-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="2f491-202">5. Asignar entidades a las expresiones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="2f491-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="2f491-203">Desde la página Entidades, vuelve a la página de la intención **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="2f491-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="2f491-204">De vuelta a la página de la intención PressButton, haz clic en la palabra **go** y, después, en la palabra **ahead** y, a continuación, selecciona **Action (Simple)** en el menú contextual para etiquetar **go ahead** como valor de la entidad **Action**:</span><span class="sxs-lookup"><span data-stu-id="2f491-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="2f491-206">Ahora, la frase **go ahead** está definida como un valor de la entidad **Action**.</span><span class="sxs-lookup"><span data-stu-id="2f491-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="2f491-207">Ahora puede ver el valor de la entidad de acción bajo las palabras go ahead:</span><span class="sxs-lookup"><span data-stu-id="2f491-207">Now you can notice the action entity value under the word go ahead:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="2f491-209">La línea roja que aparece debajo de la etiqueta en la imagen anterior indica que el valor de la entidad no se ha predicho, lo que se resolverá al entrenar el modelo en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="2f491-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="2f491-210">A continuación, haz clic en la palabra **launch** y selecciona **Target (Simple)** en el menú contextual emergente para etiquetar **launch** como valor de la entidad **Target**:</span><span class="sxs-lookup"><span data-stu-id="2f491-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="2f491-212">Ahora, la palabra **launch** está definida como un valor de la entidad **Target**. Ya aparece el valor de la entidad Target bajo la palabra launch:</span><span class="sxs-lookup"><span data-stu-id="2f491-212">The **launch** word is now defined as a **Target** entity value.Now you can notice the Target entity value under the word launch :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="2f491-214">Ahora, la expresión de ejemplo de la intención PressButton "go ahead and launch the rocket" (adelante, lanza el cohete) se ha configurado para predecirse como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="2f491-214">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="2f491-215">Intención: PressButton</span><span class="sxs-lookup"><span data-stu-id="2f491-215">Intent: PressButton</span></span>
* <span data-ttu-id="2f491-216">Entidad Action: go ahead</span><span class="sxs-lookup"><span data-stu-id="2f491-216">Action entity: go ahead</span></span>
* <span data-ttu-id="2f491-217">Entidad Target: launch</span><span class="sxs-lookup"><span data-stu-id="2f491-217">Target entity: launch</span></span>

<span data-ttu-id="2f491-218">**Repite** el proceso anterior de dos pasos para asignar una etiqueta de entidad Action y Target a cada una de las expresiones de ejemplo, teniendo en cuenta que las siguientes palabras se deben etiquetar como entidades **Target**:</span><span class="sxs-lookup"><span data-stu-id="2f491-218">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="2f491-219">**hint** (destinada a HintsButton en el proyecto de Unity)</span><span class="sxs-lookup"><span data-stu-id="2f491-219">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="2f491-220">**hints** (destinada a HintsButton en el proyecto de Unity)</span><span class="sxs-lookup"><span data-stu-id="2f491-220">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="2f491-221">**reset** (destinada a ResetButton en el proyecto de Unity)</span><span class="sxs-lookup"><span data-stu-id="2f491-221">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="2f491-222">**launch** (destinada a LaunchButton en el proyecto de Unity)</span><span class="sxs-lookup"><span data-stu-id="2f491-222">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="2f491-223">Una vez etiquetadas todas las expresiones de ejemplo, la página de la intención PressButton debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="2f491-223">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="2f491-225">6. Entrenar, probar y publicar la aplicación</span><span class="sxs-lookup"><span data-stu-id="2f491-225">6. Train, test, and publish the app</span></span>

<span data-ttu-id="2f491-226">Para entrenar la aplicación, haz clic en el botón **Entrenar** y espera a que se complete el proceso de entrenamiento:</span><span class="sxs-lookup"><span data-stu-id="2f491-226">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="2f491-228">Como puedes ver en la imagen anterior, se han quitado las líneas rojas de todas las etiquetas, lo que indica que se han predicho todos los valores de entidad.</span><span class="sxs-lookup"><span data-stu-id="2f491-228">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="2f491-229">Observa también que el icono de estado situado a la izquierda del botón Entrenar ha cambiado de color rojo a verde.</span><span class="sxs-lookup"><span data-stu-id="2f491-229">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="2f491-230">Cuando se acabe de procesar el entrenamiento, haz clic en el botón **Probar**, escribe **go ahead and launch the rocket** y presiona la tecla Entrar:</span><span class="sxs-lookup"><span data-stu-id="2f491-230">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="2f491-232">Una vez procesada la expresión de prueba, haz clic en **Inspeccionar** para ver el resultado de la prueba:</span><span class="sxs-lookup"><span data-stu-id="2f491-232">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="2f491-233">Intención: PressButton (con una certeza del 98,5 %)</span><span class="sxs-lookup"><span data-stu-id="2f491-233">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="2f491-234">Entidad Action: go ahead</span><span class="sxs-lookup"><span data-stu-id="2f491-234">Action entity: go ahead</span></span>
* <span data-ttu-id="2f491-235">Entidad Target: launch</span><span class="sxs-lookup"><span data-stu-id="2f491-235">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="2f491-237">Para publicar la aplicación, haga clic en el botón **Publicar** de la parte superior derecha y, a continuación, en la ventana emergente **Elige el espacio de publicación y la configuración**, seleccione **Producción** y haga clic en el botón **Listo**:</span><span class="sxs-lookup"><span data-stu-id="2f491-237">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Done** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="2f491-239">Espera hasta que se complete el proceso de publicación:</span><span class="sxs-lookup"><span data-stu-id="2f491-239">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

<span data-ttu-id="2f491-241">Vaya a Administrar > Configuración de la aplicación > página **Recursos de Azure**. La página de recursos de Azure debería tener un aspecto similar a este:</span><span class="sxs-lookup"><span data-stu-id="2f491-241">Navigate to the Manage > Application Settings > **Azure Resources** page, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-6.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="2f491-243">Conexión del proyecto de Unity con la aplicación de LUIS</span><span class="sxs-lookup"><span data-stu-id="2f491-243">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="2f491-244">En la página Administrar > Configuración de la aplicación > **Recursos de Azure**, haz clic en el icono **copiar** para copiar el **Ejemplo de consulta**:</span><span class="sxs-lookup"><span data-stu-id="2f491-244">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="2f491-246">Desde el proyecto de Unity, en la ventana Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, busca el componente **Lunarcom Intent Recognizer (Script)** (Reconocimiento de la intención de Lunarcom [script]) y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="2f491-246">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="2f491-247">En el campo **LUIS Endpoint** (Punto de conexión de LUIS), después del **Ejemplo de consulta** que copiaste en el paso anterior:</span><span class="sxs-lookup"><span data-stu-id="2f491-247">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="2f491-249">Probar y mejorar el reconocimiento de la intención</span><span class="sxs-lookup"><span data-stu-id="2f491-249">Testing and improving the intent recognition</span></span>

<span data-ttu-id="2f491-250">Para usar el reconocimiento de la intención directamente en el editor de Unity, debes permitir que el equipo de desarrollo use el dictado.</span><span class="sxs-lookup"><span data-stu-id="2f491-250">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="2f491-251">Para comprobar esta configuración, abre la **Configuración** de Windows, elige **Privacidad** > **Voz** y asegúrate de que el **Reconocimiento de voz en línea** esté activado:</span><span class="sxs-lookup"><span data-stu-id="2f491-251">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="2f491-253">Si ahora entras en el modo de juego, puedes probar el reconocimiento de la intención presionando el botón del cohete:</span><span class="sxs-lookup"><span data-stu-id="2f491-253">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="2f491-254">Después, suponiendo que el equipo tiene micrófono, al decir la primera expresión de ejemplo, **go ahead and launch the rocket** (adelante, lanza el cohete), verás el lanzamiento al espacio de LunarModule:</span><span class="sxs-lookup"><span data-stu-id="2f491-254">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="2f491-256">Prueba todas las **expresiones de ejemplo**, algunas **variaciones de las expresiones de ejemplo** y algunas **expresiones aleatorias**.</span><span class="sxs-lookup"><span data-stu-id="2f491-256">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="2f491-257">A continuación, vuelve a <a href="https://www.luis.ai" target="_blank">LUIS</a> y ve a la página Compilación > Mejorar el rendimiento de la aplicación > **Revisar las expresiones de punto de conexión**, usa el botón de **alternancia** para cambiar ente la vista predeterminada de entidades y la de **tokens** y, a continuación, revisa las expresiones:</span><span class="sxs-lookup"><span data-stu-id="2f491-257">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="2f491-258">En la columna **Expresión**, cambia y quita las etiquetas asignadas según sea necesario para alinearlas con tu intención.</span><span class="sxs-lookup"><span data-stu-id="2f491-258">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="2f491-259">En la columna **Intención alineada**, comprueba que la intención sea correcta.</span><span class="sxs-lookup"><span data-stu-id="2f491-259">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="2f491-260">En la columna **Agregar o eliminar**, haz clic en el botón de marca de verificación verde para agregar la expresión o en el botón x rojo para eliminarla.</span><span class="sxs-lookup"><span data-stu-id="2f491-260">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="2f491-261">Cuando haya revisado todas las expresiones que quieras, haz clic en el botón **Entrenar** para volver a entrenar el modelo y, luego, en el botón **Publicar** para volver a publicar la aplicación actualizada:</span><span class="sxs-lookup"><span data-stu-id="2f491-261">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="2f491-263">Si una expresión de punto de conexión no está alineada con la intención de PressButton, pero quieres que el modelo sepa que la expresión no tiene ninguna intención, puedes cambiar la intención alineada a Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2f491-263">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="2f491-264">**Repite** este proceso tantas veces como quieras para mejorar el modelo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2f491-264">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2f491-265">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2f491-265">Congratulations</span></span>

<span data-ttu-id="2f491-266">Ahora, el proyecto tiene comandos de voz con tecnología de IA, lo que permite que la aplicación reconozca la intención de los usuarios aunque no usen comandos precisos.</span><span class="sxs-lookup"><span data-stu-id="2f491-266">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="2f491-267">Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="2f491-267">Run the application on your device to ensure the feature is working properly.</span></span>