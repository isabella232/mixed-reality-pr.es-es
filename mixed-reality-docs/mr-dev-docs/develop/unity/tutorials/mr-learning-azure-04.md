---
title: Integración de Azure Spatial Anchors
description: Siga este curso para aprender a implementar Azure Spatial Anchors dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, hololens 2, Azure spatial anchors, azure cloud services, azure custom vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 50e5bccf09e03ebda8057dbb3ca9d83fc01694bd
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008175"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="ad717-104">4. Integración de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ad717-104">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="ad717-105">En este tutorial, aprenderá a usar **Azure Spatial Anchors**.</span><span class="sxs-lookup"><span data-stu-id="ad717-105">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="ad717-106">Almacenará la ubicación de un **objeto del que realiza un seguimiento** como un anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="ad717-106">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="ad717-107">Una vez que haya consultado el anclaje, aparecerá una flecha que le guiará hacia la ubicación.</span><span class="sxs-lookup"><span data-stu-id="ad717-107">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="ad717-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ad717-108">Objectives</span></span>

* <span data-ttu-id="ad717-109">Conocer los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="ad717-109">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="ad717-110">Aprender a configurar la escena para usar Azure Spatial Anchors en este proyecto.</span><span class="sxs-lookup"><span data-stu-id="ad717-110">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="ad717-111">Aprender a integrar el almacenamiento y la consulta de ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="ad717-111">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="ad717-112">Descripción de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ad717-112">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="ad717-113">**Azure Spatial Anchors** forma parte de la familia de servicios en la nube de Azure y se usa para guardar las ubicaciones de anclaje.</span><span class="sxs-lookup"><span data-stu-id="ad717-113">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="ad717-114">Las ubicaciones de anclaje guardadas se pueden recuperar en función del *identificador de anclaje* de la nube.</span><span class="sxs-lookup"><span data-stu-id="ad717-114">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="ad717-115">Para compartir y acceder a dicha ubicación de anclaje, se pueden usar dispositivos multiplataforma, como HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="ad717-115">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="ad717-116">Obtenga más información sobre [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="ad717-116">Learn more about [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="ad717-117">Preparación de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ad717-117">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="ad717-118">Antes de empezar, tiene que crear un recurso de anclaje espacial en Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="ad717-118">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="ad717-119">Obtenga información sobre cómo crear un [recurso de anclaje espacial](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span><span class="sxs-lookup"><span data-stu-id="ad717-119">Learn how to make a [spatial anchor resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ad717-120">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="ad717-120">Preparing the scene</span></span>

<span data-ttu-id="ad717-121">En esta sección, aprenderá a configurar la escena y realizar los cambios necesarios.</span><span class="sxs-lookup"><span data-stu-id="ad717-121">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="ad717-122">En la ventana Proyecto, navegue a **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager** (Recursos > MRTK.Tutorials.AzureCloudServices > Objetos prefabricados > Administrador).</span><span class="sxs-lookup"><span data-stu-id="ad717-122">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![Unity con el objeto prefabricado AnchorManager seleccionado](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="ad717-124">En la carpeta **Manager** (Administrador), arrastre y coloque el objeto prefabricado **Anchor Manager** (Administrador de anclajes) en la jerarquía de la escena.</span><span class="sxs-lookup"><span data-stu-id="ad717-124">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="ad717-125">Seleccione el objeto Game (Juego) de **Anchor Manager** (Administrador de anclajes) en la jerarquía y, en la sección Inspector, encontrará la opción **Spatial Anchor Manager** (Script) (Administrador de anclajes espacial [script]).</span><span class="sxs-lookup"><span data-stu-id="ad717-125">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="ad717-126">Busque el campo del identificador de la cuenta y la clave y agregue las credenciales que creó en el requisito previo de la fase anterior.</span><span class="sxs-lookup"><span data-stu-id="ad717-126">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![Unity con el objeto prefabricado AnchorManager recién agregado aún seleccionado](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="ad717-128">Ahora, busque el objeto **Scene Controller** (Controlador de escenas) en la jerarquía de escenas y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="ad717-128">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="ad717-129">Verá **Scene Controller** (Controlador de escenas) en la sección de Inspector.</span><span class="sxs-lookup"><span data-stu-id="ad717-129">You will see the **Scene Controller** Inspector.</span></span>

![Unity con el componente de script SceneController configurado](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="ad717-131">Observará que el campo **Anchor Manager** (Administrador de anclajes) del componente **Scene Controller** (Controlador de escenas) está vacío. Arrastre y coloque el elemento **Anchor Manager** (Administrador de anclajes) de la jerarquía de escenas en ese campo y guarde la escena.</span><span class="sxs-lookup"><span data-stu-id="ad717-131">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="ad717-132">Compilación e implementación de la aplicación en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ad717-132">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="ad717-133">Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad Azure Spatial Anchors, debes implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ad717-133">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="ad717-134">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación a HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="ad717-134">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="ad717-135">Ejecutar la aplicación en HoloLens 2 y seguir las instrucciones desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="ad717-135">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="ad717-136">Creación de un anclaje para almacenar una ubicación</span><span class="sxs-lookup"><span data-stu-id="ad717-136">Create an anchor to store a location</span></span>

<span data-ttu-id="ad717-137">En esta sección, verá cómo guardar la ubicación del objeto.</span><span class="sxs-lookup"><span data-stu-id="ad717-137">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="ad717-138">Ejecute la aplicación y haga clic en **Set Object** (Establecer objeto) en el menú principal de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="ad717-138">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="ad717-139">Asigne el **nombre** del objeto que quiera guardar y haga clic en **Set Object** (Establecer objeto) para continuar.</span><span class="sxs-lookup"><span data-stu-id="ad717-139">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="ad717-140">Para agregar más información sobre el objeto, seleccione la **imagen** y describa el objeto.</span><span class="sxs-lookup"><span data-stu-id="ad717-140">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="ad717-141">Para guardar la ubicación, haga clic en **Sabe Location** (Guardar ubicación).</span><span class="sxs-lookup"><span data-stu-id="ad717-141">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="ad717-142">Verá un **puntero de anclaje** que puede desplazar y colocar en la ubicación que quiera guardar.</span><span class="sxs-lookup"><span data-stu-id="ad717-142">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="ad717-143">Después, se le mostrará una ventana emergente de confirmación.</span><span class="sxs-lookup"><span data-stu-id="ad717-143">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="ad717-144">Si quiere confirmar y guardar la ubicación, haga clic en **Sí**. De lo contrario, puede cambiar la ubicación haciendo clic en **No** y seleccionándola de nuevo.</span><span class="sxs-lookup"><span data-stu-id="ad717-144">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="ad717-145">Una vez haya hecho clic en **Sí** para confirmar la ubicación, dicha ubicación y el identificador de anclaje se guardarán en el almacenamiento en la nube de Azure.</span><span class="sxs-lookup"><span data-stu-id="ad717-145">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="ad717-146">Una vez guardados, verá la **etiqueta del objeto** en el anclaje con el nombre del objeto.</span><span class="sxs-lookup"><span data-stu-id="ad717-146">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="ad717-147">Ahora la ubicación del objeto se ha guardado correctamente.</span><span class="sxs-lookup"><span data-stu-id="ad717-147">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="ad717-148">Consulta para buscar una ubicación de anclaje</span><span class="sxs-lookup"><span data-stu-id="ad717-148">Query for finding an anchor location</span></span>

<span data-ttu-id="ad717-149">Una vez que haya guardado correctamente la ubicación del anclaje, podrá buscar su ubicación. Para ello, seleccione **Search Object** (Buscar objeto) en el menú principal.</span><span class="sxs-lookup"><span data-stu-id="ad717-149">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="ad717-150">Después de hacer clic en **Search Object** (Buscar objeto), aparecerá una nueva ventana en la que deberá proporcionar el nombre del objeto que quiere buscar.</span><span class="sxs-lookup"><span data-stu-id="ad717-150">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="ad717-151">Escríbalo y haga clic en **Search Object** (Buscar objeto).</span><span class="sxs-lookup"><span data-stu-id="ad717-151">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="ad717-152">Si el objeto se guarda previamente y se encuentra en la base de datos, obtendrá la tarjeta del objeto con todos los detalles de este que haya guardado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ad717-152">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="ad717-153">Ahora puede hacer clic en **Show Location** (Mostrar ubicación) para buscar el objeto.</span><span class="sxs-lookup"><span data-stu-id="ad717-153">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="ad717-154">Una vez que haga clic en **Show Location** (Mostrar ubicación) , el sistema consultará la dirección del objeto en el almacenamiento en la nube.</span><span class="sxs-lookup"><span data-stu-id="ad717-154">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="ad717-155">Después de recuperar correctamente la ubicación, una **flecha** le dirigirá hacia la ubicación del objeto.</span><span class="sxs-lookup"><span data-stu-id="ad717-155">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="ad717-156">Siga la marca de la flecha hasta que encuentre la ubicación del objeto.</span><span class="sxs-lookup"><span data-stu-id="ad717-156">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="ad717-157">Una vez que lo encuentre, su nombre aparecerá en la parte superior y la marca de la flecha desaparecerá. A continuación, podrá hacer clic en la **etiqueta del objeto** para ver sus detalles.</span><span class="sxs-lookup"><span data-stu-id="ad717-157">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ad717-158">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="ad717-158">Congratulations</span></span>

<span data-ttu-id="ad717-159">En este tutorial, ha aprendido a guardar y recuperar la ubicación del objeto con Azure Spatial Anchors en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ad717-159">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="ad717-160">En el tutorial final, aprenderá a usar **Azure Bot Service** para agregar lenguaje natural como un nuevo método de interacción para nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="ad717-160">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ad717-161">Tutorial siguiente: 5. Integración de Azure Bot Service con LUIS</span><span class="sxs-lookup"><span data-stu-id="ad717-161">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
