---
title: Integración de Azure Bot Service con LUIS
description: Complete este curso para aprender a implementar Azure Bot Service y el reconocimiento del lenguaje natural en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, hololens 2, azure bot service, luis, natural language, conversation bot, azure cloud services, azure custom vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 10386bf75f9f3d0c9669ad37195188220a1dcb75
ms.sourcegitcommit: daa45a19a3a353334380cda78fee7fa149f0e48b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2021
ms.locfileid: "98981820"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="204ba-104">5. Integración de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="204ba-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="204ba-105">En este tutorial, aprenderá a usar **Azure Bot Service** en la aplicación de demostración de **HoloLens 2** para agregar el reconocimiento del lenguaje (LUIS) y dejar que el bot ayude al usuario al buscar **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="204ba-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="204ba-106">Este es un tutorial de dos partes en el que, en la primera parte, crea el bot con [Bot Composer](https://docs.microsoft.com/composer/introduction) como una solución sin código y echa un vistazo rápido a la función de Azure que alimenta el bot con los datos necesarios.</span><span class="sxs-lookup"><span data-stu-id="204ba-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="204ba-107">En la segunda parte se usa **BotManager (script)** en el proyecto de Unity para consumir el servicio de bot hospedado.</span><span class="sxs-lookup"><span data-stu-id="204ba-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="204ba-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="204ba-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="204ba-109">1ª parte</span><span class="sxs-lookup"><span data-stu-id="204ba-109">Part 1</span></span>

* <span data-ttu-id="204ba-110">Aprender los aspectos básicos de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="204ba-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="204ba-111">Aprender a usar Bot Composer para crear un bot</span><span class="sxs-lookup"><span data-stu-id="204ba-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="204ba-112">Aprender a usar una función de Azure para proporcionar datos de Azure Storage</span><span class="sxs-lookup"><span data-stu-id="204ba-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="204ba-113">2ª parte</span><span class="sxs-lookup"><span data-stu-id="204ba-113">Part 2</span></span>

* <span data-ttu-id="204ba-114">Aprender a configurar la escena para usar Azure Bot Service en este proyecto</span><span class="sxs-lookup"><span data-stu-id="204ba-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="204ba-115">Aprender a establecer y encontrar objetos conversando con el bot</span><span class="sxs-lookup"><span data-stu-id="204ba-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="204ba-116">Descripción de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="204ba-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="204ba-117">**Azure Bot Service** permite a los desarrolladores crear bots inteligentes que pueden mantener conversaciones naturales con los usuarios gracias a **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="204ba-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="204ba-118">Un bot de conversación es una excelente manera de ampliar las formas de las que un usuario puede interactuar con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="204ba-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="204ba-119">Un bot puede actuar como una colección de knowledge base con [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) a fin de mantener una conversación sofisticada con la eficacia de [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="204ba-119">A Bot can act as a knowledge base with a [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

<span data-ttu-id="204ba-120">Obtenga más información sobre [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="204ba-120">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="204ba-121">1ª parte: creación del bot</span><span class="sxs-lookup"><span data-stu-id="204ba-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="204ba-122">Antes de poder usar el bot en la aplicación de Unity, debe desarrollarlo, proporcionarle datos y hospedarlo en **Azure**.</span><span class="sxs-lookup"><span data-stu-id="204ba-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="204ba-123">El objetivo del bot es tener las capacidades para indicar cuántos *objetos con seguimiento* se almacenan en la base de datos, buscar un *objeto con seguimiento* por su nombre y indicar al usuario información básica sobre el mismo.</span><span class="sxs-lookup"><span data-stu-id="204ba-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="204ba-124">Vista rápida de la función de Azure de objetos con seguimiento</span><span class="sxs-lookup"><span data-stu-id="204ba-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="204ba-125">Está a punto de empezar a crear el bot, pero para que resulte útil, debe proporcionarle un recurso del que pueda extraer datos.</span><span class="sxs-lookup"><span data-stu-id="204ba-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="204ba-126">Dado que el *bot* podrá contar la cantidad de **objetos con seguimiento**, buscar objetos específicos por nombre e indicar detalles, usará una función de Azure sencilla que tenga acceso al **almacenamiento de tablas de Azure**.</span><span class="sxs-lookup"><span data-stu-id="204ba-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="204ba-127">Descargue el proyecto de la función de Azure para objetos con seguimiento [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) y extráigalo en el disco duro.</span><span class="sxs-lookup"><span data-stu-id="204ba-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="204ba-128">Esta función de Azure tiene dos acciones, **Count** y **Find**, que se pueden invocar a través de llamadas *HTTP* *GET* básicas.</span><span class="sxs-lookup"><span data-stu-id="204ba-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="204ba-129">Puede inspeccionar el código en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="204ba-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="204ba-130">Obtenga más información sobre [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="204ba-130">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="204ba-131">La función **Count** consulta en el **almacenamiento de tablas** todos los elementos **TrackedObjects** de la tabla, es muy sencillo.</span><span class="sxs-lookup"><span data-stu-id="204ba-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="204ba-132">Por otra parte, la función **Find** toma un parámetro de consulta *name* de la solicitud *GET* y consulta en el **almacenamiento de tablas** un elemento **TrackedObject** coincidente y devuelve un DTO como JSON.</span><span class="sxs-lookup"><span data-stu-id="204ba-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="204ba-133">Para implementar esta **función de Azure** directamente desde **Visual Studio**, abra la carpeta descargada AzureFunction_TrackedObjectsService y el archivo **.sln** con Visual Studio. ![Inicio de Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-1.png).</span><span class="sxs-lookup"><span data-stu-id="204ba-133">To deploy this **Azure Function** directly from **Visual Studio**, open the downloaded AzureFunction_TrackedObjectsService folder and open the present **.sln** file with visual studio ![Bot Framework Composer Home](images/mr-learning-azure/tutorial5-section3-step1-1.png)</span></span>

<span data-ttu-id="204ba-134">Una vez cargado el archivo en Visual Studio, haga clic con el botón derecho sobre **Tracked object service** (Servicio de objeto con seguimiento) en el explorador de soluciones y seleccione Publicar. ![Inicio de Bot Framework Composer.](images/mr-learning-azure/tutorial5-section3-step1-2.png)</span><span class="sxs-lookup"><span data-stu-id="204ba-134">Once file loaded in visual studio, Right click over **Tracked object sevice** in solution explorer and select publish ![Bot Framework Composer Home](images/mr-learning-azure/tutorial5-section3-step1-2.png)</span></span>

<span data-ttu-id="204ba-135">Se mostrará el elemento emergente Publicar y se le pedirá la plataforma de destino. Seleccione Azure y haga clic en el botón **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="204ba-135">The publish pop up will be displayed and ask for target flatform Select azure and click on **Next** button</span></span>

![Página principal de Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-3.png)

<span data-ttu-id="204ba-137">En el destino específico, seleccione **Azure Function App (Windows)** y haga clic en el botón **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="204ba-137">In specific target select **Azure Function App(Windows)** and click on **Next** button</span></span>

![Página principal de Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-4.png)

<span data-ttu-id="204ba-139">Si no ha iniciado sesión en Azure, iníciela a través de Visual Studio, y la ventana tendrá el siguiente aspecto.</span><span class="sxs-lookup"><span data-stu-id="204ba-139">If you are not logged in to azure please login through visual studio and the window look like</span></span>

![Página principal de Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-5.png)

<span data-ttu-id="204ba-141">Haga clic en el botón para crear una nueva aplicación de funciones en la cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="204ba-141">Click on pulse button to create new Function App in azure account</span></span>

![Página principal de Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-6.png)

* <span data-ttu-id="204ba-143">En **Nombre**, escriba un nombre adecuado para el servicio; por ejemplo, *TrackedObjectsService*.</span><span class="sxs-lookup"><span data-stu-id="204ba-143">For **Name**, enter a suitable name for the service, for example, *TrackedObjectsService*</span></span>
* <span data-ttu-id="204ba-144">En **Tipo de plan**, elija Consumo.</span><span class="sxs-lookup"><span data-stu-id="204ba-144">For **Plan Type**, choose consumption</span></span>
* <span data-ttu-id="204ba-145">En **Ubicación**, elija una ubicación cercana a la ubicación física de los usuarios de la aplicación; por ejemplo, *(EE. UU.) Oeste de EE. UU.*</span><span class="sxs-lookup"><span data-stu-id="204ba-145">For **Location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="204ba-146">En **Grupo de recursos** y **Almacenamiento**, elija la cuenta de almacenamiento y el grupo de Azure correspondientes que se crearon en secciones anteriores.</span><span class="sxs-lookup"><span data-stu-id="204ba-146">For **Resource Group** and **Storage**, choose respective azure group and storage account have been created in pervious chapters.</span></span>

<span data-ttu-id="204ba-147">Una vez que haya creado la aplicación de funciones, haga clic en el botón **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="204ba-147">Once Function App created click on **Finish** button</span></span> 

![Página principal de Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-7.png)

<span data-ttu-id="204ba-149">Después del proceso de finalización, se abrirá una ventana de publicación. Haga clic en el botón **Publicar** para publicar la función y espere a que se publique.</span><span class="sxs-lookup"><span data-stu-id="204ba-149">A publish pop up will be opened after the finish process, click on **Publish** button to publish the function and wait for publish</span></span>

![Página principal de Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-8.png)

<span data-ttu-id="204ba-151">Una vez finalizada la publicación, haga clic en **Administrar en Azure Portal** en la sección Acciones. Se le llevará a una función específica de Azure Portal, en la que deberá hacer clic en **Configuración**, que se encuentra en la sección *Configuración*.</span><span class="sxs-lookup"><span data-stu-id="204ba-151">Once completion of publish click on **Manage in Azure portal** under Actions section it is take you to specific function in azure portal and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="204ba-152">En **Configuración de la aplicación** debe proporcionar la *cadena de conexión* a **Azure Storage** donde se almacenan los **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="204ba-152">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="204ba-153">Haga clic en **Nueva configuración de la aplicación** y use para el nombre: **AzureStorageConnectionString** y para el valor proporcione la *cadena de conexión* correcta.</span><span class="sxs-lookup"><span data-stu-id="204ba-153">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="204ba-154">Después de ello, haga clic en **Guardar** y la **función de Azure** está lista para hacer funcionar el *bot* que creará a continuación.</span><span class="sxs-lookup"><span data-stu-id="204ba-154">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

<span data-ttu-id="204ba-155">Para obtener la URL de recuento y búsqueda, seleccione **Funciones**, que se encuentra en la sección *Funciones*.</span><span class="sxs-lookup"><span data-stu-id="204ba-155">To get URL of count and Find , select **Functions** which is under the *Functions* section.</span></span> <span data-ttu-id="204ba-156">Aquí podrá consultar tanto la función de recuento como la de búsqueda. Seleccione la función de recuento en la parte superior, donde se encuentra el botón *Obtener la dirección URL de la función*.</span><span class="sxs-lookup"><span data-stu-id="204ba-156">here you can find both Count and Find function, select Count function on top side you can find the *Get Function Url* button.</span></span> <span data-ttu-id="204ba-157">Siga el mismo procedimiento para obtener la dirección URL de la función de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="204ba-157">Follow the same procedure to get Find function Url.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="204ba-158">Creación de un bot de conversación</span><span class="sxs-lookup"><span data-stu-id="204ba-158">Creating a conversation Bot</span></span>

<span data-ttu-id="204ba-159">Hay varias maneras de desarrollar un bot de conversación basado en Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="204ba-159">There are several ways to develop a Bot Framework based conversational bot.</span></span> <span data-ttu-id="204ba-160">En esta lección usará la aplicación de escritorio [Bot Framework Composer](https://docs.microsoft.com/composer/), que es un diseñador visual perfecto para el desarrollo rápido.</span><span class="sxs-lookup"><span data-stu-id="204ba-160">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="204ba-161">Puede descargar las últimas versiones desde el [repositorio de GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="204ba-161">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="204ba-162">Está disponible para Windows, Mac y Linux.</span><span class="sxs-lookup"><span data-stu-id="204ba-162">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="204ba-163">Una vez que se haya instalado **Bot Framework Composer**, inicie la aplicación y debería ver esta interfaz:</span><span class="sxs-lookup"><span data-stu-id="204ba-163">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Página principal de Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="204ba-165">Hemos preparado un proyecto de Bot Composer que proporciona los cuadros de diálogo y desencadenadores necesarios para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="204ba-165">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="204ba-166">Descargue el proyecto de Bot Framework Composer [BotComposerProject_TrackedObjectsBot. zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) y extráigalo en el disco duro.</span><span class="sxs-lookup"><span data-stu-id="204ba-166">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="204ba-167">En la barra superior, haga clic en **Abrir** y seleccione el proyecto de Bot Framework que ha descargado, denominado **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="204ba-167">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="204ba-168">Una vez que el proyecto esté totalmente cargado, debería ver el proyecto listo.</span><span class="sxs-lookup"><span data-stu-id="204ba-168">After the project is fully loaded, you should see the project ready.</span></span>

![Bot Framework Composer con el proyecto TrackedObjectsBot abierto](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="204ba-170">Vamos a centrarnos en el lado izquierdo, en el que puede ver el **panel Diálogos**.</span><span class="sxs-lookup"><span data-stu-id="204ba-170">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="204ba-171">Allí hay un diálogo denominado **TrackedObjectsBot** en el que puede ver varios **desencadenadores**.</span><span class="sxs-lookup"><span data-stu-id="204ba-171">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="204ba-172">Obtenga más información acerca de los [conceptos de Bot Framework](https://docs.microsoft.com/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="204ba-172">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="204ba-173">Estos desencadenadores hacen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="204ba-173">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="204ba-174">Saludo</span><span class="sxs-lookup"><span data-stu-id="204ba-174">Greeting</span></span>

<span data-ttu-id="204ba-175">Este es el punto de entrada del *bot* de chat cuando un *usuario* inicia una conversación.</span><span class="sxs-lookup"><span data-stu-id="204ba-175">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![Desencadenador Greeting (Saludo) del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="204ba-177">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="204ba-177">AskingForCount</span></span>

<span data-ttu-id="204ba-178">Este diálogo se desencadena cuando el *usuario* pide el recuento de todos los **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="204ba-178">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="204ba-179">Estas son las frases que lo desencadenan:</span><span class="sxs-lookup"><span data-stu-id="204ba-179">These are the trigger phrases:</span></span>

>* <span data-ttu-id="204ba-180">contar todo</span><span class="sxs-lookup"><span data-stu-id="204ba-180">count me all</span></span>
>* <span data-ttu-id="204ba-181">cuántos se almacenan</span><span class="sxs-lookup"><span data-stu-id="204ba-181">how many are stored</span></span>

![Desencadenador AskForCount del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="204ba-183">Gracias a [LUIS](https://docs.microsoft.com/composer/how-to-use-luis), el *usuario* no tiene que formular las frases de la manera exacta, lo que permite una conversación natural para el *usuario*.</span><span class="sxs-lookup"><span data-stu-id="204ba-183">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="204ba-184">En este diálogo, el *bot* también se comunicará con la función de Azure **Count**, lo que de detallará más adelante.</span><span class="sxs-lookup"><span data-stu-id="204ba-184">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="204ba-185">Intención desconocida</span><span class="sxs-lookup"><span data-stu-id="204ba-185">Unknown Intent</span></span>

<span data-ttu-id="204ba-186">Este diálogo se desencadena si la entrada del *usuario* no se ajusta a ninguna otra condición desencadenadora y responde al usuario que intente de nuevo su pregunta.</span><span class="sxs-lookup"><span data-stu-id="204ba-186">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![Desencadenador Unknown Intent (Intención desconocida) del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="204ba-188">FindEntity</span><span class="sxs-lookup"><span data-stu-id="204ba-188">FindEntity</span></span>

<span data-ttu-id="204ba-189">El último diálogo es más complejo, ya que contiene bifurcaciones y almacena datos en la memoria de *bots*.</span><span class="sxs-lookup"><span data-stu-id="204ba-189">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="204ba-190">Solicita al usuario el *nombre* del **objeto con seguimiento** del que quiere saber más información, realiza una consulta a la función de Azure **Find** y usa la respuesta para continuar con la conversación.</span><span class="sxs-lookup"><span data-stu-id="204ba-190">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![Desencadenador FindEntity del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="204ba-192">Si no se encuentra el **objeto con seguimiento**, se informa al usuario y finaliza la conversación.</span><span class="sxs-lookup"><span data-stu-id="204ba-192">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="204ba-193">Cuando se encuentra el **objeto con seguimiento** en cuestión, el bot comprobará qué propiedades están disponibles e informará sobre ellas.</span><span class="sxs-lookup"><span data-stu-id="204ba-193">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="204ba-194">Adaptación del bot</span><span class="sxs-lookup"><span data-stu-id="204ba-194">Adapting the Bot</span></span>

<span data-ttu-id="204ba-195">Los desencadenadores **AskingForCount** y **FindEntity** deben comunicarse con el back-end, lo que significa que tiene que agregar la dirección URL correcta de la **función de Azure** que implementó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="204ba-195">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="204ba-196">En el panel de diálogos, haga clic en **AskingForCount** y busque la acción *Enviar una solicitud HTTP*; aquí puede ver el campo **URL** que necesita para cambiar la URL correcta para el punto de conexión de la función **Count**.</span><span class="sxs-lookup"><span data-stu-id="204ba-196">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![Configuración de puntos de conexión del desencadenador AskingForCount del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="204ba-198">Por último, busque el desencadenador **FindEntity** y busque la acción *Enviar una solicitud HTTP*; en el campo **URL**, cambie la dirección URL por el punto de conexión de la función **Find**.</span><span class="sxs-lookup"><span data-stu-id="204ba-198">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![Configuración de puntos de conexión del desencadenador FindEntity del cuadro de diálogo del proyecto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="204ba-200">Con todo definido, ya está listo para implementar el bot.</span><span class="sxs-lookup"><span data-stu-id="204ba-200">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="204ba-201">Puesto que tiene Bot Framework Composer instalado, puede publicarlo directamente desde allí.</span><span class="sxs-lookup"><span data-stu-id="204ba-201">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="204ba-202">Obtenga más información sobre cómo [publicar un bot desde Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="204ba-202">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="204ba-203">No dude en experimentar con el bot agregando más frases desencadenadoras, nuevas respuestas o bifurcaciones de conversación.</span><span class="sxs-lookup"><span data-stu-id="204ba-203">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="204ba-204">Parte 2: configuración de todo en Unity</span><span class="sxs-lookup"><span data-stu-id="204ba-204">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="204ba-205">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="204ba-205">Preparing the scene</span></span>

<span data-ttu-id="204ba-206">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="204ba-206">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Ventana Project (Proyecto) de Unity con el objeto prefabricado ChatBotManager seleccionado](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="204ba-208">Desde ahí, mueva el elemento prefabricado **ChatBotManager** a la jerarquía de la escena.</span><span class="sxs-lookup"><span data-stu-id="204ba-208">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="204ba-209">Una vez que agregue ChatBotManager a la escena, haga clic en el componente **Chat Bot Manager** (Administrador de bot de chat).</span><span class="sxs-lookup"><span data-stu-id="204ba-209">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="204ba-210">En el inspector verá que hay un campo **Direct Line Secret Key** (Clave secreta de línea directa) que debe rellenar.</span><span class="sxs-lookup"><span data-stu-id="204ba-210">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="204ba-211">Puede recuperar la *clave secreta* del portal de Azure; para ello, busque el recurso del tipo **Registro de canales de bots** que ha creado en la primera parte de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="204ba-211">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![Unity con el objeto prefabricado ChatBotManager recién agregado aún seleccionado](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="204ba-213">Ahora, conectará el objeto **ChatBotManager** con el componente **ChatBotController** adjunto al objeto **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="204ba-213">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="204ba-214">En la jerarquía, seleccione **ChatBotPanel** y verá un campo vacío **Chat Bot Manager** (Administrador de bots de chat); arrastre desde la jerarquía el objeto **ChatBotManager** al campo **Chat Bot Manager** (Administrador de bots de chat).</span><span class="sxs-lookup"><span data-stu-id="204ba-214">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![Unity con el panel ChatBotPanel configurado](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="204ba-216">A continuación, necesita una manera de abrir **ChatBotPanel** para que el usuario pueda interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="204ba-216">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="204ba-217">En la ventana Scene (Escena) es posible que haya observado que hay un botón secundario *Chat bot* (Bot de chat) en el objeto **MainMenu**, que usará para resolver este problema.</span><span class="sxs-lookup"><span data-stu-id="204ba-217">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="204ba-218">En la jerarquía, busque **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** y busque en el Inspector el script *ButtonConfigHelper*.</span><span class="sxs-lookup"><span data-stu-id="204ba-218">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="204ba-219">Allí verá una ranura vacía en la devolución de llamada del evento **OnClick()** .</span><span class="sxs-lookup"><span data-stu-id="204ba-219">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="204ba-220">Arrastre y coloque **ChatBotPanel** en la ranura del evento, en la lista desplegable vaya a *GameObject*, seleccione en el submenú *SetActive (bool)* y active la casilla.</span><span class="sxs-lookup"><span data-stu-id="204ba-220">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![Unity con el elemento ButtonChatBot configurado](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="204ba-222">Ahora el bot de chat puede iniciarse desde el menú principal, por lo que la escena está lista para su uso.</span><span class="sxs-lookup"><span data-stu-id="204ba-222">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="204ba-223">Puesta a prueba del bot</span><span class="sxs-lookup"><span data-stu-id="204ba-223">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="204ba-224">Pregunta sobre la cantidad de objetos con seguimiento</span><span class="sxs-lookup"><span data-stu-id="204ba-224">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="204ba-225">En primer lugar, realice una prueba en la que pida al bot cuántos **objetos con seguimiento** se almacenan en la base de datos.</span><span class="sxs-lookup"><span data-stu-id="204ba-225">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="204ba-226">Esta vez debe ejecutar la aplicación desde HoloLens 2 porque es posible que servicios como *texto a voz* no estén disponibles en el sistema.</span><span class="sxs-lookup"><span data-stu-id="204ba-226">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="204ba-227">Ejecute la aplicación en HoloLens 2 y haga clic en el botón *Bot de chat* situado junto al menú principal.</span><span class="sxs-lookup"><span data-stu-id="204ba-227">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="204ba-228">El bot le saludará. Pregunte **¿cuántos objetos tenemos?**</span><span class="sxs-lookup"><span data-stu-id="204ba-228">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="204ba-229">Debe indicarle la cantidad y finalizar la conversación.</span><span class="sxs-lookup"><span data-stu-id="204ba-229">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="204ba-230">Pregunta sobre un objeto con seguimiento</span><span class="sxs-lookup"><span data-stu-id="204ba-230">Asking about a tracked object</span></span>

<span data-ttu-id="204ba-231">Vuelva a ejecutar la aplicación y, esta vez, pregunte **busca un objeto con seguimiento**; el bot le pedirá el nombre, al que debe responder con "coche" o el nombre de otro *objeto con seguimiento* que sepa que existe en la base de datos.</span><span class="sxs-lookup"><span data-stu-id="204ba-231">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="204ba-232">El bot le indicará detalles como la descripción y si tiene un anclaje espacial asignado.</span><span class="sxs-lookup"><span data-stu-id="204ba-232">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="204ba-233">Pruebe de preguntar por un **objeto con seguimiento** que no exista y escuche cómo responde el bot.</span><span class="sxs-lookup"><span data-stu-id="204ba-233">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="204ba-234">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="204ba-234">Congratulations</span></span>

<span data-ttu-id="204ba-235">En este tutorial ha aprendido cómo se puede usar Azure Bot Framework para interactuar con la aplicación mediante la conversación con lenguaje natural.</span><span class="sxs-lookup"><span data-stu-id="204ba-235">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="204ba-236">Ha aprendido a desarrollar su propio bot y cuáles son las piezas necesarias para que funcione.</span><span class="sxs-lookup"><span data-stu-id="204ba-236">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="204ba-237">Conclusión</span><span class="sxs-lookup"><span data-stu-id="204ba-237">Conclusion</span></span>

<span data-ttu-id="204ba-238">A lo largo de esta serie de tutoriales, ha experimentado cómo **Azure Cloud Services** ha incorporado características nuevas y emocionantes a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="204ba-238">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="204ba-239">Ahora puede almacenar datos e imágenes en la nube con **Azure Storage**, usar **Azure Custom Vision** para asociar imágenes y entrenar un modelo, incorporar objetos a un contexto local con **anclajes espaciales de Azure** e implementar **Azure Bot Framework con tecnología de LUIS** para agregar un bot de conversación para un patrón de interacción nuevo y natural.</span><span class="sxs-lookup"><span data-stu-id="204ba-239">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
