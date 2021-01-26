---
title: Integración de Azure Bot Service con LUIS
description: Complete este curso para aprender a implementar Azure Bot Service y el reconocimiento del lenguaje natural en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, hololens 2, azure bot service, luis, natural language, conversation bot, azure cloud services, azure custom vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 7119dfd54c2b5384ff0e219a494ca8423fe4ebfc
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583384"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="1fb92-104">5. Integración de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="1fb92-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="1fb92-105">En este tutorial, aprenderá a usar **Azure Bot Service** en la aplicación de demostración de **HoloLens 2** para agregar el reconocimiento del lenguaje (LUIS) y dejar que el bot ayude al usuario al buscar **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="1fb92-106">Este es un tutorial de dos partes en el que, en la primera parte, crea el bot con [Bot Composer](/composer/introduction) como una solución sin código y echa un vistazo rápido a la función de Azure que alimenta el bot con los datos necesarios.</span><span class="sxs-lookup"><span data-stu-id="1fb92-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="1fb92-107">En la segunda parte se usa **BotManager (script)** en el proyecto de Unity para consumir el servicio de bot hospedado.</span><span class="sxs-lookup"><span data-stu-id="1fb92-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="1fb92-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1fb92-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="1fb92-109">1ª parte</span><span class="sxs-lookup"><span data-stu-id="1fb92-109">Part 1</span></span>

* <span data-ttu-id="1fb92-110">Aprender los aspectos básicos de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="1fb92-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="1fb92-111">Aprender a usar Bot Composer para crear un bot</span><span class="sxs-lookup"><span data-stu-id="1fb92-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="1fb92-112">Aprender a usar una función de Azure para proporcionar datos de Azure Storage</span><span class="sxs-lookup"><span data-stu-id="1fb92-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="1fb92-113">2ª parte</span><span class="sxs-lookup"><span data-stu-id="1fb92-113">Part 2</span></span>

* <span data-ttu-id="1fb92-114">Aprender a configurar la escena para usar Azure Bot Service en este proyecto</span><span class="sxs-lookup"><span data-stu-id="1fb92-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="1fb92-115">Aprender a establecer y encontrar objetos conversando con el bot</span><span class="sxs-lookup"><span data-stu-id="1fb92-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="1fb92-116">Descripción de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="1fb92-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="1fb92-117">**Azure Bot Service** permite a los desarrolladores crear bots inteligentes que pueden mantener conversaciones naturales con los usuarios gracias a **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="1fb92-118">Un bot de conversación es una excelente manera de ampliar las formas de las que un usuario puede interactuar con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1fb92-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="1fb92-119">Un bot puede actuar como una colección de knowledge base con [QnA Marker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) a fin de mantener una conversación sofisticada con la eficacia de [Language Understanding (LUIS)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="1fb92-119">A Bot can act as a knowledge base with a [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0).</span></span>

<span data-ttu-id="1fb92-120">Obtenga más información sobre [Azure Bot Service](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="1fb92-120">Learn more about [Azure Bot Service](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="1fb92-121">1ª parte: creación del bot</span><span class="sxs-lookup"><span data-stu-id="1fb92-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="1fb92-122">Antes de poder usar el bot en la aplicación de Unity, debe desarrollarlo, proporcionarle datos y hospedarlo en **Azure**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="1fb92-123">El objetivo del bot es tener las capacidades para indicar cuántos *objetos con seguimiento* se almacenan en la base de datos, buscar un *objeto con seguimiento* por su nombre y indicar al usuario información básica sobre el mismo.</span><span class="sxs-lookup"><span data-stu-id="1fb92-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="1fb92-124">Vista rápida de la función de Azure de objetos con seguimiento</span><span class="sxs-lookup"><span data-stu-id="1fb92-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="1fb92-125">Está a punto de empezar a crear el bot, pero para que resulte útil, debe proporcionarle un recurso del que pueda extraer datos.</span><span class="sxs-lookup"><span data-stu-id="1fb92-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="1fb92-126">Dado que el *bot* podrá contar la cantidad de **objetos con seguimiento**, buscar objetos específicos por nombre e indicar detalles, usará una función de Azure sencilla que tenga acceso al **almacenamiento de tablas de Azure**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="1fb92-127">Descargue el proyecto de la función de Azure para objetos con seguimiento [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) y extráigalo en el disco duro.</span><span class="sxs-lookup"><span data-stu-id="1fb92-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="1fb92-128">Esta función de Azure tiene dos acciones, **Count** y **Find**, que se pueden invocar a través de llamadas *HTTP* *GET* básicas.</span><span class="sxs-lookup"><span data-stu-id="1fb92-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="1fb92-129">Puede inspeccionar el código en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="1fb92-130">Obtenga más información sobre [Azure Functions](/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="1fb92-130">Learn more about [Azure Functions](/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="1fb92-131">La función **Count** consulta en el **almacenamiento de tablas** todos los elementos **TrackedObjects** de la tabla, es muy sencillo.</span><span class="sxs-lookup"><span data-stu-id="1fb92-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="1fb92-132">Por otra parte, la función **Find** toma un parámetro de consulta *name* de la solicitud *GET* y consulta en el **almacenamiento de tablas** un elemento **TrackedObject** coincidente y devuelve un DTO como JSON.</span><span class="sxs-lookup"><span data-stu-id="1fb92-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="1fb92-133">Puede implementar esta **función de Azure** directamente desde **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-133">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="1fb92-134">Aquí encontrará toda la información relacionada con la [implementación de la función de Azure](/azure/devops/pipelines/targets/azure-functions?preserve-view=true&tabs=dotnet-core%2cyaml&view=azure-devops).</span><span class="sxs-lookup"><span data-stu-id="1fb92-134">Find here all information regarding [Azure Function deployment](/azure/devops/pipelines/targets/azure-functions?preserve-view=true&tabs=dotnet-core%2cyaml&view=azure-devops).</span></span>

<span data-ttu-id="1fb92-135">Una vez que haya completado la implementación, en el **portal de Azure**, abra el recurso correspondiente y haga clic en **Configuración**, que se encuentra en la sección *Configuración*.</span><span class="sxs-lookup"><span data-stu-id="1fb92-135">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="1fb92-136">En **Configuración de la aplicación** debe proporcionar la *cadena de conexión* a **Azure Storage** donde se almacenan los **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-136">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="1fb92-137">Haga clic en **Nueva configuración de la aplicación** y use para el nombre: **AzureStorageConnectionString** y para el valor proporcione la *cadena de conexión* correcta.</span><span class="sxs-lookup"><span data-stu-id="1fb92-137">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="1fb92-138">Después de ello, haga clic en **Guardar** y la **función de Azure** está lista para hacer funcionar el *bot* que creará a continuación.</span><span class="sxs-lookup"><span data-stu-id="1fb92-138">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="1fb92-139">Creación de un bot de conversación</span><span class="sxs-lookup"><span data-stu-id="1fb92-139">Creating a conversation Bot</span></span>

<span data-ttu-id="1fb92-140">Hay varias maneras de desarrollar un bot de conversación basado en Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="1fb92-140">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="1fb92-141">En esta lección usará la aplicación de escritorio [Bot Framework Composer](/composer/), que es un diseñador visual perfecto para el desarrollo rápido.</span><span class="sxs-lookup"><span data-stu-id="1fb92-141">In this lesson you will use the [Bot Framework Composer](/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="1fb92-142">Puede descargar las últimas versiones desde el [repositorio de GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="1fb92-142">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="1fb92-143">Está disponible para Windows, Mac y Linux.</span><span class="sxs-lookup"><span data-stu-id="1fb92-143">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="1fb92-144">Una vez que se haya instalado **Bot Framework Composer**, inicie la aplicación y debería ver esta interfaz:</span><span class="sxs-lookup"><span data-stu-id="1fb92-144">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Página principal de Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="1fb92-146">Hemos preparado un proyecto de Bot Composer que proporciona los cuadros de diálogo y desencadenadores necesarios para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="1fb92-146">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="1fb92-147">Descargue el proyecto de Bot Framework Composer [BotComposerProject_TrackedObjectsBot. zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) y extráigalo en el disco duro.</span><span class="sxs-lookup"><span data-stu-id="1fb92-147">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="1fb92-148">En la barra superior, haga clic en **Abrir** y seleccione el proyecto de Bot Framework que ha descargado, denominado **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-148">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="1fb92-149">Una vez que el proyecto esté totalmente cargado, debería ver el proyecto listo.</span><span class="sxs-lookup"><span data-stu-id="1fb92-149">After the project is fully loaded, you should see the project ready.</span></span>

![Bot Framework Composer con el proyecto TrackedObjectsBot abierto](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="1fb92-151">Vamos a centrarnos en el lado izquierdo, en el que puede ver el **panel Diálogos**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-151">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="1fb92-152">Allí hay un diálogo denominado **TrackedObjectsBot** en el que puede ver varios **desencadenadores**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-152">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="1fb92-153">Obtenga más información acerca de los [conceptos de Bot Framework](/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="1fb92-153">Learn more about [Bot Framework concepts](/composer/concept-dialog).</span></span>

<span data-ttu-id="1fb92-154">Estos desencadenadores hacen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1fb92-154">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="1fb92-155">Saludo</span><span class="sxs-lookup"><span data-stu-id="1fb92-155">Greeting</span></span>

<span data-ttu-id="1fb92-156">Este es el punto de entrada del *bot* de chat cuando un *usuario* inicia una conversación.</span><span class="sxs-lookup"><span data-stu-id="1fb92-156">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![Desencadenador Greeting (Saludo) del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="1fb92-158">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="1fb92-158">AskingForCount</span></span>

<span data-ttu-id="1fb92-159">Este diálogo se desencadena cuando el *usuario* pide el recuento de todos los **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-159">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="1fb92-160">Estas son las frases que lo desencadenan:</span><span class="sxs-lookup"><span data-stu-id="1fb92-160">These are the trigger phrases:</span></span>

>* <span data-ttu-id="1fb92-161">contar todo</span><span class="sxs-lookup"><span data-stu-id="1fb92-161">count me all</span></span>
>* <span data-ttu-id="1fb92-162">cuántos se almacenan</span><span class="sxs-lookup"><span data-stu-id="1fb92-162">how many are stored</span></span>

![Desencadenador AskForCount del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="1fb92-164">Gracias a [LUIS](/composer/how-to-use-luis), el *usuario* no tiene que formular las frases de la manera exacta, lo que permite una conversación natural para el *usuario*.</span><span class="sxs-lookup"><span data-stu-id="1fb92-164">Thanks to [LUIS](/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="1fb92-165">En este diálogo, el *bot* también se comunicará con la función de Azure **Count**, lo que de detallará más adelante.</span><span class="sxs-lookup"><span data-stu-id="1fb92-165">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="1fb92-166">Intención desconocida</span><span class="sxs-lookup"><span data-stu-id="1fb92-166">Unknown Intent</span></span>

<span data-ttu-id="1fb92-167">Este diálogo se desencadena si la entrada del *usuario* no se ajusta a ninguna otra condición desencadenadora y responde al usuario que intente de nuevo su pregunta.</span><span class="sxs-lookup"><span data-stu-id="1fb92-167">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![Desencadenador Unknown Intent (Intención desconocida) del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="1fb92-169">FindEntity</span><span class="sxs-lookup"><span data-stu-id="1fb92-169">FindEntity</span></span>

<span data-ttu-id="1fb92-170">El último diálogo es más complejo, ya que contiene bifurcaciones y almacena datos en la memoria de *bots*.</span><span class="sxs-lookup"><span data-stu-id="1fb92-170">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="1fb92-171">Solicita al usuario el *nombre* del **objeto con seguimiento** del que quiere saber más información, realiza una consulta a la función de Azure **Find** y usa la respuesta para continuar con la conversación.</span><span class="sxs-lookup"><span data-stu-id="1fb92-171">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![Desencadenador FindEntity del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="1fb92-173">Si no se encuentra el **objeto con seguimiento**, se informa al usuario y finaliza la conversación.</span><span class="sxs-lookup"><span data-stu-id="1fb92-173">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="1fb92-174">Cuando se encuentra el **objeto con seguimiento** en cuestión, el bot comprobará qué propiedades están disponibles e informará sobre ellas.</span><span class="sxs-lookup"><span data-stu-id="1fb92-174">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="1fb92-175">Adaptación del bot</span><span class="sxs-lookup"><span data-stu-id="1fb92-175">Adapting the Bot</span></span>

<span data-ttu-id="1fb92-176">Los desencadenadores **AskingForCount** y **FindEntity** deben comunicarse con el back-end, lo que significa que tiene que agregar la dirección URL correcta de la **función de Azure** que implementó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1fb92-176">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="1fb92-177">En el panel de diálogos, haga clic en **AskingForCount** y busque la acción *Enviar una solicitud HTTP*; aquí puede ver el campo **URL** que necesita para cambiar la URL correcta para el punto de conexión de la función **Count**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-177">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![Configuración de puntos de conexión del desencadenador AskingForCount del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="1fb92-179">Por último, busque el desencadenador **FindEntity** y busque la acción *Enviar una solicitud HTTP*; en el campo **URL**, cambie la dirección URL por el punto de conexión de la función **Find**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-179">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![Configuración de puntos de conexión del desencadenador FindEntity del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="1fb92-181">Con todo definido, ya está listo para implementar el bot.</span><span class="sxs-lookup"><span data-stu-id="1fb92-181">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="1fb92-182">Puesto que tiene Bot Framework Composer instalado, puede publicarlo directamente desde allí.</span><span class="sxs-lookup"><span data-stu-id="1fb92-182">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="1fb92-183">Obtenga más información sobre cómo [publicar un bot desde Bot Composer](/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="1fb92-183">Learn more about [Publish a bot from Bot Composer](/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="1fb92-184">No dude en experimentar con el bot agregando más frases desencadenadoras, nuevas respuestas o bifurcaciones de conversación.</span><span class="sxs-lookup"><span data-stu-id="1fb92-184">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="1fb92-185">Parte 2: configuración de todo en Unity</span><span class="sxs-lookup"><span data-stu-id="1fb92-185">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="1fb92-186">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="1fb92-186">Preparing the scene</span></span>

<span data-ttu-id="1fb92-187">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-187">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Ventana Project (Proyecto) de Unity con el objeto prefabricado ChatBotManager seleccionado](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="1fb92-189">Desde ahí, mueva el elemento prefabricado **ChatBotManager** a la jerarquía de la escena.</span><span class="sxs-lookup"><span data-stu-id="1fb92-189">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="1fb92-190">Una vez que agregue ChatBotManager a la escena, haga clic en el componente **Chat Bot Manager** (Administrador de bot de chat).</span><span class="sxs-lookup"><span data-stu-id="1fb92-190">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="1fb92-191">En el inspector verá que hay un campo **Direct Line Secret Key** (Clave secreta de línea directa) que debe rellenar.</span><span class="sxs-lookup"><span data-stu-id="1fb92-191">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="1fb92-192">Puede recuperar la *clave secreta* del portal de Azure; para ello, busque el recurso del tipo **Registro de canales de bots** que ha creado en la primera parte de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="1fb92-192">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![Unity con el objeto prefabricado ChatBotManager recién agregado aún seleccionado](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="1fb92-194">Ahora, conectará el objeto **ChatBotManager** con el componente **ChatBotController** adjunto al objeto **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="1fb92-194">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="1fb92-195">En la jerarquía, seleccione **ChatBotPanel** y verá un campo vacío **Chat Bot Manager** (Administrador de bots de chat); arrastre desde la jerarquía el objeto **ChatBotManager** al campo **Chat Bot Manager** (Administrador de bots de chat).</span><span class="sxs-lookup"><span data-stu-id="1fb92-195">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![Unity con el panel ChatBotPanel configurado](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="1fb92-197">A continuación, necesita una manera de abrir **ChatBotPanel** para que el usuario pueda interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="1fb92-197">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="1fb92-198">En la ventana Scene (Escena) es posible que haya observado que hay un botón secundario *Chat bot* (Bot de chat) en el objeto **MainMenu**, que usará para resolver este problema.</span><span class="sxs-lookup"><span data-stu-id="1fb92-198">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="1fb92-199">En la jerarquía, busque **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** y busque en el Inspector el script *ButtonConfigHelper*.</span><span class="sxs-lookup"><span data-stu-id="1fb92-199">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="1fb92-200">Allí verá una ranura vacía en la devolución de llamada del evento **OnClick()** .</span><span class="sxs-lookup"><span data-stu-id="1fb92-200">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="1fb92-201">Arrastre y coloque **ChatBotPanel** en la ranura del evento, en la lista desplegable vaya a *GameObject*, seleccione en el submenú *SetActive (bool)* y active la casilla.</span><span class="sxs-lookup"><span data-stu-id="1fb92-201">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![Unity con el elemento ButtonChatBot configurado](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="1fb92-203">Ahora el bot de chat puede iniciarse desde el menú principal, por lo que la escena está lista para su uso.</span><span class="sxs-lookup"><span data-stu-id="1fb92-203">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="1fb92-204">Puesta a prueba del bot</span><span class="sxs-lookup"><span data-stu-id="1fb92-204">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="1fb92-205">Pregunta sobre la cantidad de objetos con seguimiento</span><span class="sxs-lookup"><span data-stu-id="1fb92-205">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="1fb92-206">En primer lugar, realice una prueba en la que pida al bot cuántos **objetos con seguimiento** se almacenan en la base de datos.</span><span class="sxs-lookup"><span data-stu-id="1fb92-206">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="1fb92-207">Esta vez debe ejecutar la aplicación desde HoloLens 2 porque es posible que servicios como *texto a voz* no estén disponibles en el sistema.</span><span class="sxs-lookup"><span data-stu-id="1fb92-207">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="1fb92-208">Ejecute la aplicación en HoloLens 2 y haga clic en el botón *Bot de chat* situado junto al menú principal.</span><span class="sxs-lookup"><span data-stu-id="1fb92-208">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="1fb92-209">El bot le saludará. Pregunte **¿cuántos objetos tenemos?**</span><span class="sxs-lookup"><span data-stu-id="1fb92-209">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="1fb92-210">Debe indicarle la cantidad y finalizar la conversación.</span><span class="sxs-lookup"><span data-stu-id="1fb92-210">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="1fb92-211">Pregunta sobre un objeto con seguimiento</span><span class="sxs-lookup"><span data-stu-id="1fb92-211">Asking about a tracked object</span></span>

<span data-ttu-id="1fb92-212">Vuelva a ejecutar la aplicación y, esta vez, pregunte **busca un objeto con seguimiento**; el bot le pedirá el nombre, al que debe responder con "coche" o el nombre de otro *objeto con seguimiento* que sepa que existe en la base de datos.</span><span class="sxs-lookup"><span data-stu-id="1fb92-212">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="1fb92-213">El bot le indicará detalles como la descripción y si tiene un anclaje espacial asignado.</span><span class="sxs-lookup"><span data-stu-id="1fb92-213">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="1fb92-214">Pruebe de preguntar por un **objeto con seguimiento** que no exista y escuche cómo responde el bot.</span><span class="sxs-lookup"><span data-stu-id="1fb92-214">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="1fb92-215">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="1fb92-215">Congratulations</span></span>

<span data-ttu-id="1fb92-216">En este tutorial ha aprendido cómo se puede usar Azure Bot Framework para interactuar con la aplicación mediante la conversación con lenguaje natural.</span><span class="sxs-lookup"><span data-stu-id="1fb92-216">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="1fb92-217">Ha aprendido a desarrollar su propio bot y cuáles son las piezas necesarias para que funcione.</span><span class="sxs-lookup"><span data-stu-id="1fb92-217">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="1fb92-218">Conclusión</span><span class="sxs-lookup"><span data-stu-id="1fb92-218">Conclusion</span></span>

<span data-ttu-id="1fb92-219">A lo largo de esta serie de tutoriales, ha experimentado cómo **Azure Cloud Services** ha incorporado características nuevas y emocionantes a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1fb92-219">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="1fb92-220">Ahora puede almacenar datos e imágenes en la nube con **Azure Storage**, usar **Azure Custom Vision** para asociar imágenes y entrenar un modelo, incorporar objetos a un contexto local con **anclajes espaciales de Azure** e implementar **Azure Bot Framework con tecnología de LUIS** para agregar un bot de conversación para un patrón de interacción nuevo y natural.</span><span class="sxs-lookup"><span data-stu-id="1fb92-220">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>