---
title: Azure Spatial Anchors en Unreal
description: Aprenda a crear, administrar y ubicar los delimitadores espaciales de Azure existentes en aplicaciones de realidad mixta de Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure development, spatial anchors, mixed reality, development, features, new project, emulator, documentation, guides, holograms, game development, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 01d7217f038519d68eabfbf4f273c7ff8cbe7193
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496203"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="e592a-104">Azure Spatial Anchors en Unreal</span><span class="sxs-lookup"><span data-stu-id="e592a-104">Azure Spatial Anchors in Unreal</span></span>

<span data-ttu-id="e592a-105">Azure Spatial Anchors es un servicio de Microsoft Mixed Reality, que permite que los dispositivos de realidad aumentada detecten, compartan y conserven puntos de anclaje en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="e592a-105">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="e592a-106">En la documentación siguiente se proporcionan instrucciones para integrar el servicio de Azure Spatial Anchors en un proyecto de Unreal.</span><span class="sxs-lookup"><span data-stu-id="e592a-106">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="e592a-107">Si busca más información, consulte el [servicio de Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="e592a-107">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="e592a-108">Unreal Engine 4.26 ahora tiene complementos para la compatibilidad con ARKit y ARCore si usa iOS o Android como destino.</span><span class="sxs-lookup"><span data-stu-id="e592a-108">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e592a-109">Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube.</span><span class="sxs-lookup"><span data-stu-id="e592a-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="e592a-110">Si tiene pensado almacenar los anclajes localmente en un dispositivo, hay un documento de [Anclajes espaciales locales](unreal-spatial-anchors.md) que puede guiarle por el proceso.</span><span class="sxs-lookup"><span data-stu-id="e592a-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="e592a-111">Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.</span><span class="sxs-lookup"><span data-stu-id="e592a-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e592a-112">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="e592a-112">Prerequisites</span></span>

<span data-ttu-id="e592a-113">Para completar esta guía, asegúrese de tener:</span><span class="sxs-lookup"><span data-stu-id="e592a-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="e592a-114">Instalado [Unreal versión 4.25](https://www.unrealengine.com/get-now) o posterior</span><span class="sxs-lookup"><span data-stu-id="e592a-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="e592a-115">Un [proyecto de HoloLens 2](tutorials/unreal-uxt-ch1.md) configurado en Unreal</span><span class="sxs-lookup"><span data-stu-id="e592a-115">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="e592a-116">Leída la [información general de Azure Spatial Anchors](/azure/spatial-anchors/overview)</span><span class="sxs-lookup"><span data-stu-id="e592a-116">Read through the [Azure Spatial Anchors overview](/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="e592a-117">Conocimientos básicos de C++ y Unreal</span><span class="sxs-lookup"><span data-stu-id="e592a-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="e592a-118">Obtención de información de cuenta de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e592a-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="e592a-119">Antes de usar Azure Spatial Anchors en un proyecto, debe:</span><span class="sxs-lookup"><span data-stu-id="e592a-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="e592a-120">[Crear un recurso de anclajes espaciales](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) y copiar los campos de la cuenta que se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="e592a-120">[Create a spatial anchors resource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="e592a-121">Estos valores se usan para autenticar a los usuarios con la cuenta de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="e592a-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="e592a-122">**Id. de cuenta**</span><span class="sxs-lookup"><span data-stu-id="e592a-122">**Account ID**</span></span>
    * <span data-ttu-id="e592a-123">**Clave de cuenta**</span><span class="sxs-lookup"><span data-stu-id="e592a-123">**Account Key**</span></span>

<span data-ttu-id="e592a-124">Para obtener más información, consulte los documentos de [autenticación de Azure Spatial Anchors](/azure/spatial-anchors/concepts/authentication?tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="e592a-124">Check out the [Azure Spatial Anchors authentication](/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="e592a-125">Azure Spatial Anchors en Unreal 4.25 no admite tokens de autenticación de Azure AD, pero la compatibilidad con esta funcionalidad estará disponible en una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="e592a-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="enabling-internet-access"></a><span data-ttu-id="e592a-126">Habilitación del acceso a Internet</span><span class="sxs-lookup"><span data-stu-id="e592a-126">Enabling Internet access</span></span>

<span data-ttu-id="e592a-127">Abra **Configuración del proyecto > HoloLens** y habilite la funcionalidad **Internet Client** (Cliente de Internet):</span><span class="sxs-lookup"><span data-stu-id="e592a-127">Open **Project Settings > HoloLens** and enable the **Internet Client** capability:</span></span>

![Configuración del proyecto de HoloLens con funcionalidades resaltadas](images/asa-enable-wifi-connection.jpg)

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="e592a-129">Adición de complementos de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e592a-129">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="e592a-130">Para habilitar los complementos de Azure Spatial Anchors en el editor de Unreal:</span><span class="sxs-lookup"><span data-stu-id="e592a-130">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="e592a-131">Haga clic en **Edit > Plugins** (Editar > Complementos) y busque **AzureSpatialAnchors** y **AzureSpatialAnchorsForWMR**.</span><span class="sxs-lookup"><span data-stu-id="e592a-131">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="e592a-132">Active la casilla **Enabled** (Habilitado) en ambos complementos para permitir el acceso a las bibliotecas de planos técnicos de Azure Spatial Anchors en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e592a-132">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Captura de pantalla de los complementos de Spatial Anchors en el editor de Unreal](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="e592a-134">Una vez hecho esto, reinicie Unreal Editor para que los cambios de los complementos surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="e592a-134">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="e592a-135">El proyecto ahora está listo para usar Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-135">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="e592a-136">Inicio de una sesión en Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e592a-136">Starting a Spatial Anchors session</span></span>

<span data-ttu-id="e592a-137">Una sesión de Azure Spatial Anchors permite que las aplicaciones cliente se comuniquen con el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-137">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="e592a-138">Deberá crear e iniciar una sesión de Azure Spatial Anchors para crear, conservar y compartir Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="e592a-138">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="e592a-139">Abra el plano técnico del Pawn (Peón) que está usando en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e592a-139">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="e592a-140">Agregue dos variables de cadena para **Account ID** (ID. de cuenta) y **Account Key** (Clave de cuenta) y, a continuación, asigne los valores correspondientes de la cuenta de Azure Spatial Anchors para autenticar la sesión.</span><span class="sxs-lookup"><span data-stu-id="e592a-140">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Captura de pantalla del panel de detalles con el identificador, la clave y el tipo de variable de la cuenta de Azure Spatial Anchors resaltados](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="e592a-142">Para iniciar una sesión de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="e592a-142">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="e592a-143">Compruebe que se está ejecutando una **AR Session** (Sesión de AR) en la aplicación de HoloLens, ya que la sesión de Azure Spatial Anchors no puede iniciarse mientras no se esté ejecutando una sesión de AR.</span><span class="sxs-lookup"><span data-stu-id="e592a-143">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="e592a-144">Si no tiene una configurada, [cree un recurso de AR Session](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="e592a-144">If you don't have one setup, [create an AR Session asset](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="e592a-145">Agregue el evento personalizado **Start Azure Spatial Anchors Session** (Iniciar sesión de Azure Spatial Anchors) y configúrelo como se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="e592a-145">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="e592a-146">Al crear una sesión no se inicia la sesión de manera predeterminada, lo que le permite configurar la sesión para la autenticación en el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-146">Creating a session doesn't start the session by default, which allows you to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Plano técnico del evento personalizado de inicio de sesión de Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="e592a-148">Configure la sesión de Azure Spatial Anchors para que proporcione **Account ID** (Id. de cuenta) y **Account Key** (Clave de cuenta).</span><span class="sxs-lookup"><span data-stu-id="e592a-148">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![Plano técnico de la función de sesión de configuración con el id. de cuenta y la clave agregada](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="e592a-150">Inicie la sesión de Azure Spatial Anchors, lo que permite a la aplicación crear y ubicar los Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-150">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Plano técnico de la función de inicio de sesión de Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="e592a-152">Se recomienda limpiar los recursos de Azure Spatial Anchors en el plano técnico Event Graph (Gráfico de eventos) cuando ya no use el servicio:</span><span class="sxs-lookup"><span data-stu-id="e592a-152">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="e592a-153">Detenga la sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-153">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="e592a-154">La sesión ya no estará en ejecución, pero sus recursos asociados seguirán existiendo en el complemento de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-154">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Plano técnico del evento personalizado de detención de sesiones de Azure Spatial Anchors y función de detención de sesión](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="e592a-156">Destruya la sesión de Azure Spatial Anchors para limpiar los recursos de la sesión de Azure Spatial Anchors aún conocidos por el complemento de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-156">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Plano técnico de la función de destrucción de sesión](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="e592a-158">El plano técnico Event Graph (Gráfico de eventos) debe ser similar a la siguiente captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="e592a-158">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Plano técnico del gráfico de eventos completo de la configuración de la sesión de Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a><span data-ttu-id="e592a-160">Creación de un anclaje</span><span class="sxs-lookup"><span data-stu-id="e592a-160">Creating an anchor</span></span>

<span data-ttu-id="e592a-161">Una instancia de Azure Spatial Anchors representa un lugar del mundo físico en el espacio de la aplicación de realidad aumentada, que fija el contenido de la realidad aumentada a ubicaciones físicas.</span><span class="sxs-lookup"><span data-stu-id="e592a-161">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to physical locations.</span></span> <span data-ttu-id="e592a-162">Los Azure Spatial Anchors también se pueden compartir entre distintos usuarios.</span><span class="sxs-lookup"><span data-stu-id="e592a-162">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="e592a-163">Este uso compartido permite que el contenido de la realidad aumentada dibujado en diferentes dispositivos se coloque en la misma ubicación del mundo físico.</span><span class="sxs-lookup"><span data-stu-id="e592a-163">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="e592a-164">Para crear un nuevo Azure Spatial Anchor:</span><span class="sxs-lookup"><span data-stu-id="e592a-164">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="e592a-165">Compruebe que haya una sesión de Azure Spatial Anchors en ejecución.</span><span class="sxs-lookup"><span data-stu-id="e592a-165">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="e592a-166">La aplicación no puede crear o conservar un Azure Spatial Anchor cuando no se está ejecutando ninguna sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-166">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Plano técnico del evento personalizado de creación de una instancia de Azure Spatial Anchor](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="e592a-168">Cree u obtenga un **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** (Componente de escena) de Unreal cuya ubicación deba conservarse.</span><span class="sxs-lookup"><span data-stu-id="e592a-168">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="e592a-169">En la imagen siguiente, el componente **Scene Component Needing Anchor** se usa como variable.</span><span class="sxs-lookup"><span data-stu-id="e592a-169">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="e592a-170">Se necesita un componente de escena de Unreal para establecer una transformación del mundo de la aplicación para un [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) (Marca de AR) y Azure Spatial Anchor.</span><span class="sxs-lookup"><span data-stu-id="e592a-170">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Plano técnico del evento personalizado de creación de una instancia de Azure Spatial Anchors con el componente de la escena](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="e592a-172">Para construir y guardar un Azure Spatial Anchor para un componente de escena de Unreal:</span><span class="sxs-lookup"><span data-stu-id="e592a-172">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="e592a-173">Llame al [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) (Componente de marca) para el componente de escena de Unreal y especifique la **World Transform** (Transformación de mundos) del componente de escena como la transformación de mundos que se usa para AR Pin (Marca de AR).</span><span class="sxs-lookup"><span data-stu-id="e592a-173">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="e592a-174">Unreal realiza un seguimiento de los puntos de AR en el espacio de la aplicación mediante AR Pins (Marcas de AR), que se usan para crear un Azure Spatial Anchor.</span><span class="sxs-lookup"><span data-stu-id="e592a-174">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="e592a-175">En Unreal, una AR Pin (Marca de AR) es análoga a SpatialAnchor en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e592a-175">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Plano técnico del componente de la escena conectado a la función de anclaje de componentes](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="e592a-177">Llame a **Create Cloud Anchor** (Crear anclaje de nube) con la AR Pin (Marca de AR) recién creada.</span><span class="sxs-lookup"><span data-stu-id="e592a-177">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="e592a-178">Create Cloud Anchor crea un Azure Spatial Anchor de forma local, pero no en el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-178">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="e592a-179">Los parámetros del Azure Spatial Anchor, como una fecha de expiración, se pueden establecer antes de crear el Azure Spatial Anchor con el servicio.</span><span class="sxs-lookup"><span data-stu-id="e592a-179">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Plano técnico de la función de anclaje de componentes conectada a la función de creación de anclaje en la nube que devuelve ARPin](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="e592a-181">Establezca la expiración del Azure Spatial Anchor.</span><span class="sxs-lookup"><span data-stu-id="e592a-181">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="e592a-182">El parámetro Lifetime (Duración) de la función permite al desarrollador especificar en segundos cuánto tiempo debe el servicio mantener el anclaje.</span><span class="sxs-lookup"><span data-stu-id="e592a-182">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="e592a-183">Por ejemplo, una expiración de una semana tomaría un valor de 60 segundos x 60 minutos x 24 horas x 7 días = 604 800 segundos.</span><span class="sxs-lookup"><span data-stu-id="e592a-183">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Plano técnico de la función de anclaje en la nube conectada a la función de establecimiento de la expiración con el valor de duración establecido en 604 800 segundos](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="e592a-185">Después de establecer los parámetros de los anclajes, declare el anclaje como listo para guardarse.</span><span class="sxs-lookup"><span data-stu-id="e592a-185">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="e592a-186">En el ejemplo siguiente, el Azure Spatial Anchor recién creado se agrega a un conjunto de Azure Spatial Anchors que debe guardarse.</span><span class="sxs-lookup"><span data-stu-id="e592a-186">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="e592a-187">Este conjunto se declara como variable para el plano técnico del Pawn (Peón).</span><span class="sxs-lookup"><span data-stu-id="e592a-187">This set is declared as a variable for the Pawn blueprint.</span></span>

![Plano técnico del anclaje listo para guardarse en el establecimiento de la variable](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="e592a-189">Guardado de un anclaje</span><span class="sxs-lookup"><span data-stu-id="e592a-189">Saving an Anchor</span></span>

<span data-ttu-id="e592a-190">Después de configurar el Azure Spatial Anchor con sus parámetros, llame a **Save Cloud Anchor** (Guardar anclaje de nube).</span><span class="sxs-lookup"><span data-stu-id="e592a-190">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="e592a-191">Save Cloud Anchor declara el anclaje en el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-191">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="e592a-192">Cuando la llamada a Save Cloud Anchor se realiza correctamente, el Azure Spatial Anchor está disponible para otros usuarios del servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-192">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Plano técnico de la llamada a la función de guardado del anclaje en la nube](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="e592a-194">Save Cloud Anchor es una función asincrónica y solo se puede llamar desde un evento de subproceso de juego, como **EventTick**.</span><span class="sxs-lookup"><span data-stu-id="e592a-194">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="e592a-195">Es posible que Save Cloud Anchor no aparezca como una función de plano técnico en el plano técnico personalizado Functions (Funciones).</span><span class="sxs-lookup"><span data-stu-id="e592a-195">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="e592a-196">Sin embargo, debe estar disponible en el editor de planos técnicos Event Graph (Gráfico de eventos) del Pawn (Peón).</span><span class="sxs-lookup"><span data-stu-id="e592a-196">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="e592a-197">En el ejemplo siguiente, el Azure Spatial Anchor se almacena en un conjunto durante una devolución de llamada del evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="e592a-197">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="e592a-198">Después, el elemento se guarda en EventTick.</span><span class="sxs-lookup"><span data-stu-id="e592a-198">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="e592a-199">Se pueden necesitar varios intentos para guardar un Azure Spatial Anchor, en función de la cantidad de datos espaciales que se hayan creado en la sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-199">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="e592a-200">Por eso es conveniente comprobar si la llamada de guardado se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="e592a-200">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="e592a-201">Si el anclaje no se guarda, vuelva a agregarlo al conjunto de anclajes que todavía deben guardarse.</span><span class="sxs-lookup"><span data-stu-id="e592a-201">If the anchor doesn't save, readd it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="e592a-202">Los EventTicks futuros intentarán guardar el anclaje hasta que se almacene correctamente.</span><span class="sxs-lookup"><span data-stu-id="e592a-202">Future EventTicks will keep trying to save the anchor until it's successfully stored.</span></span>

![Plano técnico que muestra como se vuelven a guardar los anclajes no guardados en el establecimiento de la variable](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="e592a-204">Una vez que se guarde el anclaje, la transformación de AR Pins (Marcas de AR) actúa como transformación de referencia para colocar contenido en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e592a-204">Once the anchor saves, the AR Pins' transform acts as a reference transform for placing content in your app.</span></span> <span data-ttu-id="e592a-205">Otros usuarios pueden detectar este anclaje y alinear el contenido de AR para diferentes dispositivos del mundo físico.</span><span class="sxs-lookup"><span data-stu-id="e592a-205">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="e592a-206">Eliminación de un anclaje</span><span class="sxs-lookup"><span data-stu-id="e592a-206">Deleting an Anchor</span></span>

<span data-ttu-id="e592a-207">Puede eliminar los anclajes del servicio Azure Spatial Anchors llamando a **Delete Cloud Anchor** (Eliminar anclaje de nube).</span><span class="sxs-lookup"><span data-stu-id="e592a-207">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![Plano técnico de la llamada a la función de eliminación del anclaje en la nube](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="e592a-209">Delete Cloud Anchor es una función latente y solo se puede llamar desde un evento de subproceso de juego, como EventTick.</span><span class="sxs-lookup"><span data-stu-id="e592a-209">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="e592a-210">Es posible que Delete Cloud Anchor no aparezca como una función de plano técnico en el plano técnico personalizado Functions (Funciones).</span><span class="sxs-lookup"><span data-stu-id="e592a-210">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="e592a-211">Sin embargo, debe estar disponible en el editor de planos técnicos Event Graph (Gráfico de eventos) del Pawn (Peón).</span><span class="sxs-lookup"><span data-stu-id="e592a-211">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="e592a-212">En el ejemplo siguiente, el anclaje está marcado para su eliminación en un evento de entrada personalizado.</span><span class="sxs-lookup"><span data-stu-id="e592a-212">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="e592a-213">A continuación, se intenta la eliminación en EventTick.</span><span class="sxs-lookup"><span data-stu-id="e592a-213">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="e592a-214">Si se produce un error en la eliminación del anclaje, agregue el Azure Spatial Anchor al conjunto de anclajes marcados para su eliminación y vuelva a intentarlo en EventTicks posteriores.</span><span class="sxs-lookup"><span data-stu-id="e592a-214">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="e592a-215">El plano técnico Event Graph (Gráfico de eventos) ahora debe ser similar a la siguiente captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="e592a-215">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Plano técnico del gráfico de eventos completo para controlar los anclajes en la nube](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="e592a-217">Detección de anclajes preexistentes</span><span class="sxs-lookup"><span data-stu-id="e592a-217">Locating pre-existing anchors</span></span>

<span data-ttu-id="e592a-218">Los anclajes existentes pueden ser creados por elementos del mismo nivel con el servicio de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="e592a-218">Existing anchors can be created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="e592a-219">Obtenga un identificador de Azure Spatial Anchor para el anclaje que desea detectar.</span><span class="sxs-lookup"><span data-stu-id="e592a-219">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="e592a-220">Se puede obtener un identificador de anclaje para un anclaje creado por el mismo dispositivo en una sesión anterior de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-220">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="e592a-221">También se puede crear y compartir mediante dispositivos del mismo nivel que interactúen con el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-221">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Plano técnico del evento personalizado de almacenamiento del identificador de Azure Spatial Anchors con la función de obtención del identificador de la nube de Azure](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="e592a-223">Agregue un componente **AzureSpatialAnchorsEvent** al plano técnico del Pawn (Peón).</span><span class="sxs-lookup"><span data-stu-id="e592a-223">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="e592a-224">Este componente le permite suscribirse a varios eventos de Azure Spatial Anchors, como los eventos a los que se llama cuando se detectan Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-224">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Captura de pantalla de BP_Pawn abierto en el editor de plano técnico con los paneles de componentes y de detalles abiertos](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="e592a-226">Suscríbase a **ASAAnchor Located Delegate** (Delegado detectado de ASAAnchor) para el componente **AzureSpatialAnchorsEvent**.</span><span class="sxs-lookup"><span data-stu-id="e592a-226">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="e592a-227">El delegado permite que la aplicación sepa cuándo se han encontrado nuevos anclajes asociados con la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-227">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="e592a-228">Con la devolución de llamada del evento, no se crearán de forma predeterminada AR Pins (Marcas de AR) para los Azure Spatial Anchors creados por pares mediante la sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="e592a-228">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="e592a-229">Para crear una AR Pin (Marca de AR) para el Spatial Anchor de Azure detectado, los desarrolladores pueden llamar a **Create ARPin Around Azure Cloud Spatial Anchor** (Crear ARPin en función del anclaje espacial en la nube de Azure).</span><span class="sxs-lookup"><span data-stu-id="e592a-229">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![Plano técnico del evento para empezar a jugar conectado al delegado ubicado en ASAAnchor](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="e592a-231">Para buscar las instancias de Azure Spatial Anchors creadas por los elementos del mismo nivel mediante el servicio de Azure Spatial Anchors, la aplicación tendrá que crear un **Monitor de Azure Spatial Anchors**:</span><span class="sxs-lookup"><span data-stu-id="e592a-231">To locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="e592a-232">Compruebe que haya una sesión de Azure Spatial Anchors en ejecución.</span><span class="sxs-lookup"><span data-stu-id="e592a-232">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="e592a-233">Cree un **AzureSpatialAnchorsLocateCriteria**.</span><span class="sxs-lookup"><span data-stu-id="e592a-233">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="e592a-234">Puede especificar varios parámetros de ubicación, como la distancia desde el usuario o la distancia desde otro anclaje.</span><span class="sxs-lookup"><span data-stu-id="e592a-234">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="e592a-235">Declare el identificador de Azure Spatial Anchors que busca en **AzureSpatialAnchorsLocateCritieria**.</span><span class="sxs-lookup"><span data-stu-id="e592a-235">Declare the Azure Spatial Anchor identifier you're looking for in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="e592a-236">Llame a **Create Watcher** (Crear monitor).</span><span class="sxs-lookup"><span data-stu-id="e592a-236">Call **Create Watcher**.</span></span>

![Plano técnico del evento personalizado de inicio del monitor de Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="e592a-238">Ahora, la aplicación comienza a buscar los Azure Spatial Anchors que conoce el servicio de Azure Spatial Anchors, lo que significa que los usuarios pueden localizar los Azure Spatial Anchors creados por sus pares.</span><span class="sxs-lookup"><span data-stu-id="e592a-238">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="e592a-239">Después de localizar el Azure Spatial Anchor, llame a **Stop Watcher** (Detener monitor) para detener Azure Spatial Anchors Watcher (Monitor de Azure Spatial Anchors) y limpie los recursos del monitor.</span><span class="sxs-lookup"><span data-stu-id="e592a-239">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Plano técnico de la llamada a la función de detención del monitor](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="e592a-241">El plano técnico Event Graph (Gráfico de eventos) final ahora debe ser similar a la siguiente captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="e592a-241">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Plano técnico del gráfico de eventos completo para controlar los eventos del delegado de anclaje](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="e592a-243">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="e592a-243">Next Development Checkpoint</span></span>

<span data-ttu-id="e592a-244">Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="e592a-244">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="e592a-245">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="e592a-245">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="e592a-246">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="e592a-246">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="e592a-247">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="e592a-247">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e592a-248">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="e592a-248">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="e592a-249">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="e592a-249">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="e592a-250">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="e592a-250">Next steps</span></span>
* [<span data-ttu-id="e592a-251">Anclajes espaciales locales</span><span class="sxs-lookup"><span data-stu-id="e592a-251">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="e592a-252">Documentación sobre anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="e592a-252">Spatial Anchors documentation</span></span>](/azure/spatial-anchors/)
* [<span data-ttu-id="e592a-253">Características de Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e592a-253">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="e592a-254">Instrucciones sobre una experiencia de anclaje efectiva</span><span class="sxs-lookup"><span data-stu-id="e592a-254">Effective anchor experience guidelines</span></span>](/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)