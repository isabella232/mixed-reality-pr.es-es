---
title: 'HoloLens (1ª generación) y Azure 302B: visión personalizada'
description: Complete este curso para aprender a entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, visión personalizada, hololens, envolventes, VR, Windows 10, Visual Studio
ms.openlocfilehash: 97fd0ae72401b67a83752cb2cf6799fa2b1ccc0c
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730532"
---
# <a name="hololens-1st-gen-and-azure-302b-custom-vision"></a><span data-ttu-id="1fd6a-104">HoloLens (1ª generación) y Azure 302B: visión personalizada</span><span class="sxs-lookup"><span data-stu-id="1fd6a-104">HoloLens (1st gen) and Azure 302b: Custom vision</span></span>

<br>

>[!NOTE]
><span data-ttu-id="1fd6a-105">Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1fd6a-106">Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1fd6a-107">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1fd6a-108">Se mantendrán para que sigan funcionando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1fd6a-109">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1fd6a-110">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>


<span data-ttu-id="1fd6a-111">En este curso, aprenderá a reconocer el contenido visual personalizado dentro de una imagen proporcionada, con las funcionalidades de Azure Custom Vision en una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="1fd6a-112">Este servicio le permitirá entrenar un modelo de aprendizaje automático mediante imágenes de objeto.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="1fd6a-113">A continuación, usará el modelo entrenado para reconocer objetos similares, tal y como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara conectada a su equipo para auriculares envolvente (VR).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![resultado del curso](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="1fd6a-115">Azure Custom Vision es un servicio cognitivo de Microsoft que permite a los desarrolladores crear clasificadores de imágenes personalizados.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="1fd6a-116">Estos clasificadores se pueden usar con nuevas imágenes para reconocer o clasificar objetos dentro de la nueva imagen.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="1fd6a-117">El servicio proporciona un portal en línea sencillo y fácil de usar para simplificar el proceso.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="1fd6a-118">Para obtener más información, visite la [Página de Custom Vision Service de Azure](/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-118">For more information, visit the [Azure Custom Vision Service page](/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="1fd6a-119">Al finalizar este curso, tendrá una aplicación de realidad mixta que podrá trabajar en dos modos:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="1fd6a-120">**Modo de análisis**: configurar el Custom Vision Service manualmente mediante la carga de imágenes, la creación de etiquetas y el entrenamiento del servicio para reconocer objetos diferentes (en este caso, el mouse y el teclado).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="1fd6a-121">Después creará una aplicación de HoloLens que capturará imágenes mediante la cámara e intentará reconocer esos objetos en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="1fd6a-122">**Modo de entrenamiento**: implementará código que habilitará un "modo de entrenamiento" en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="1fd6a-123">El modo de entrenamiento le permitirá capturar imágenes mediante la cámara de HoloLens, cargar las imágenes capturadas en el servicio y entrenar el modelo de visión personalizada.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="1fd6a-124">Este curso le enseñará cómo obtener los resultados de la Custom Vision Service en una aplicación de ejemplo basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="1fd6a-125">Depende de usted que aplique estos conceptos a una aplicación personalizada que pueda estar compilando.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="1fd6a-126">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1fd6a-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1fd6a-127">Curso</span><span class="sxs-lookup"><span data-stu-id="1fd6a-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1fd6a-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1fd6a-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1fd6a-129"><a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="1fd6a-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1fd6a-130">Realidad mixta y Azure (302b): Custom Vision</span><span class="sxs-lookup"><span data-stu-id="1fd6a-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="1fd6a-131">✔️</span><span class="sxs-lookup"><span data-stu-id="1fd6a-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1fd6a-132">✔️</span><span class="sxs-lookup"><span data-stu-id="1fd6a-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1fd6a-133">Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a los auriculares con Windows Mixed Reality inmersivo (VR).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="1fd6a-134">Dado que los auriculares envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="1fd6a-135">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir auriculares envolventes (VR).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1fd6a-136">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="1fd6a-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1fd6a-137">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1fd6a-138">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="1fd6a-139">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](../../install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se enumera a continuación.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="1fd6a-140">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1fd6a-141">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="1fd6a-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1fd6a-142">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="1fd6a-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1fd6a-143">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="1fd6a-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1fd6a-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="1fd6a-144">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1fd6a-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1fd6a-145">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="1fd6a-146">Un [auricular de Windows Mixed Reality inmersivo (VR)](../../../discover/immersive-headset-hardware-details.md) o [Microsoft HoloLens](/hololens/hololens1-hardware) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="1fd6a-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="1fd6a-147">Una cámara conectada al equipo (para el desarrollo de auriculares envolvente)</span><span class="sxs-lookup"><span data-stu-id="1fd6a-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="1fd6a-148">Acceso a Internet para la instalación de Azure y Custom Vision la recuperación de API</span><span class="sxs-lookup"><span data-stu-id="1fd6a-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="1fd6a-149">Una serie de al menos cinco (5) imágenes (diez (10) recomendado) para cada objeto que desea que reconozca el Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="1fd6a-150">Si lo desea, puede usar [las imágenes que ya se proporcionan con este curso (un mouse de equipo y un teclado) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1fd6a-151">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="1fd6a-151">Before you start</span></span>

1.  <span data-ttu-id="1fd6a-152">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1fd6a-153">Configure y pruebe su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="1fd6a-154">Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="1fd6a-155">Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="1fd6a-156">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](/hololens/hololens-calibration#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="1fd6a-157">Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](/hololens/hololens-updates).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="1fd6a-158">Capítulo 1: portal de Custom Vision Service</span><span class="sxs-lookup"><span data-stu-id="1fd6a-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="1fd6a-159">Para usar el *Custom Vision Service* en Azure, debe configurar una instancia del servicio para que esté disponible para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="1fd6a-160">En primer lugar, [vaya a la Página principal de *Custom Vision Service*](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="1fd6a-161">Haga clic en **el botón introducción.**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-161">Click on the **Get Started** button.</span></span>

    ![Introducción a Custom Vision Service](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="1fd6a-163">Inicie sesión en el portal de *Custom Vision Service* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-163">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![Iniciar sesión en el portal](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="1fd6a-165">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-165">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1fd6a-166">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-166">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="1fd6a-167">Una vez iniciada la sesión por primera vez, se le solicitará el panel *de condiciones de servicio* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-167">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="1fd6a-168">Haga clic en la casilla para aceptar los términos.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-168">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="1fd6a-169">A continuación, haga clic en **acepto.**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-169">Then click on **I agree**.</span></span>

    ![Los términos del servicio](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="1fd6a-171">Una vez aceptados los términos, se le dirigirá a la sección *proyectos* del portal.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-171">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="1fd6a-172">Haga clic en **nuevo proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-172">Click on **New Project**.</span></span>

    ![Creación de un proyecto](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="1fd6a-174">Aparecerá una pestaña en el lado derecho, que le pedirá que especifique algunos campos para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-174">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="1fd6a-175">Inserte un *nombre* para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-175">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="1fd6a-176">Inserte una *Descripción* para el proyecto (*opcional*).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-176">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="1fd6a-177">Elija un *grupo de recursos* o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-177">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="1fd6a-178">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-178">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1fd6a-179">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-179">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="1fd6a-180">Establecer los *tipos de proyecto* en **clasificación**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-180">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="1fd6a-181">Establezca los *dominios* como **generales**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-181">Set the *Domains* as **General**.</span></span>

        ![Establecer los dominios](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="1fd6a-183">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-183">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="1fd6a-184">Cuando haya terminado, haga clic en **Create Project (crear proyecto**), se le redirigirá a la página Custom Vision Service, Project (proyecto).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-184">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="1fd6a-185">Capítulo 2: entrenar el proyecto de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="1fd6a-185">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="1fd6a-186">Una vez en el portal de Custom Vision, el objetivo principal es entrenar el proyecto para que reconozca objetos específicos en las imágenes.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-186">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="1fd6a-187">Necesita al menos cinco (5) imágenes, aunque se prefiere diez (10) para cada objeto que desea que reconozca la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-187">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="1fd6a-188">[Puede usar las imágenes proporcionadas con este curso (un mouse de equipo y un teclado)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-188">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="1fd6a-189">Para entrenar su proyecto de Custom Vision Service:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-189">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="1fd6a-190">Haga clic en el **+** botón situado junto a **etiquetas.**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-190">Click on the **+** button next to **Tags.**</span></span>

    ![Agregar nueva etiqueta](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="1fd6a-192">Agregue el **nombre** del objeto que desea reconocer.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-192">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="1fd6a-193">Haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-193">Click on **Save**.</span></span>

    ![Agregar nombre de objeto y guardar](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="1fd6a-195">Observará que se ha agregado la **etiqueta** (es posible que tenga que volver a cargar la página para que aparezca).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-195">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="1fd6a-196">Haga clic en la casilla junto a la nueva etiqueta, si aún no está activada.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-196">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![Habilitar nueva etiqueta](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="1fd6a-198">Haga clic en **Agregar imágenes** en el centro de la página.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-198">Click on **Add Images** in the center of the page.</span></span>

    ![Adición de imágenes](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="1fd6a-200">Haga clic en **examinar archivos locales** y busque y, a continuación, seleccione las imágenes que desea cargar y, como mínimo, cinco (5).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-200">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="1fd6a-201">Recuerde que todas estas imágenes deben contener el objeto al que va a entrenar.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-201">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="1fd6a-202">Puede seleccionar varias imágenes a la vez para cargarlas.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-202">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="1fd6a-203">Una vez que pueda ver las imágenes en la pestaña, seleccione la etiqueta adecuada en el cuadro **mis etiquetas** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-203">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![Seleccionar etiquetas](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="1fd6a-205">Haga clic en **cargar archivos**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-205">Click on **Upload files**.</span></span> <span data-ttu-id="1fd6a-206">Los archivos comenzarán a cargarse.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-206">The files will begin uploading.</span></span> <span data-ttu-id="1fd6a-207">Una vez que haya confirmado la carga, haga clic en **listo**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-207">Once you have confirmation of the upload, click **Done**.</span></span>

    ![Carga de archivos](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="1fd6a-209">Repita el mismo proceso para crear una nueva **etiqueta** denominada **teclado** y cargar las fotos adecuadas para ella.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-209">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="1fd6a-210">Asegúrese de **desactivar** el *mouse* una vez que haya creado las nuevas etiquetas para que se muestre la ventana *Agregar imágenes* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-210">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="1fd6a-211">Una vez que tenga ambas etiquetas configuradas, haga clic en **entrenar** y la primera iteración de entrenamiento comenzará a compilarse.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-211">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![Habilitar iteración de entrenamiento](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="1fd6a-213">Una vez compilada, podrá ver dos botones denominados establecer dirección URL **predeterminada** y de **predicción**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-213">Once it's built, you'll be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="1fd6a-214">Haga clic en **establecer como predeterminado** primero y luego haga clic en **dirección URL de predicción**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-214">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![Establecer la dirección URL predeterminada y de predicción](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="1fd6a-216">La dirección URL del punto de conexión que se proporciona a partir de este, se establece en la *iteración* que se haya marcado como predeterminada.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-216">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="1fd6a-217">Por lo tanto, si posteriormente realiza una nueva *iteración* y la actualiza como predeterminada, no necesitará cambiar el código.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-217">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="1fd6a-218">Una vez que haya hecho clic en *dirección URL de predicción*, Abra *el Bloc de notas* y copie y pegue la **dirección URL** y la **clave de predicción** para que pueda recuperarla cuando la necesite más adelante en el código.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-218">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![Copiar y pegar URL y Prediction-Key](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="1fd6a-220">Haga clic en el **engranaje** de la parte superior derecha de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-220">Click on the **Cog** at the top right of the screen.</span></span>

    ![Haga clic en el icono de engranaje para abrir configuración](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="1fd6a-222">Copie la **clave de entrenamiento** y péguela en un *Bloc de notas* para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-222">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![Copiar clave de entrenamiento](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="1fd6a-224">Copie también el **identificador del proyecto** y péguelo en el archivo del *Bloc de notas* para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-224">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![Copiar ID. de proyecto](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="1fd6a-226">Capítulo 3: configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="1fd6a-226">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="1fd6a-227">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-227">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1fd6a-228">Abra *Unity* y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-228">Open *Unity* and click **New**.</span></span>

    ![Crear un proyecto de Unity](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="1fd6a-230">Ahora tendrá que proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-230">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="1fd6a-231">Inserte **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-231">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="1fd6a-232">Asegúrese de que la plantilla de proyecto está establecida en **3D**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-232">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="1fd6a-233">Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-233">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1fd6a-234">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-234">Then, click **Create project**.</span></span>

    ![Configurar las opciones del proyecto](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="1fd6a-236">Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-236">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1fd6a-237">Vaya a **Editar*  >  *preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-237">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1fd6a-238">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-238">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1fd6a-239">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-239">Close the **Preferences** window.</span></span>

    ![Configurar herramientas externas](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="1fd6a-241">A continuación, vaya a **archivo > configuración de compilación** y seleccione **plataforma universal de Windows** y, después, haga clic en el botón **cambiar plataforma** para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-241">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![<span data-ttu-id="1fd6a-242">Configurar los valores de compilación</span><span class="sxs-lookup"><span data-stu-id="1fd6a-242">Configure build settings</span></span> ](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="1fd6a-243">Mientras sigue en el **archivo > la configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-243">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="1fd6a-244">El **dispositivo de destino** está establecido en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-244">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="1fd6a-245">Para los auriculares envolventes, establezca el **dispositivo de destino** en *cualquier dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-245">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="1fd6a-246">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-246">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="1fd6a-247">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-247">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="1fd6a-248">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-248">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="1fd6a-249">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-249">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="1fd6a-250">Guarde la escena y agréguela a la compilación.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-250">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="1fd6a-251">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-251">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1fd6a-252">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-252">A save window will appear.</span></span>

            ![Agregar abrir escena a la lista de compilación](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="1fd6a-254">Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-254">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de escenas](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="1fd6a-256">Abra la carpeta **Scenes** recién creada y, a continuación, en el campo *nombre de archivo:* , escriba **CustomVisionScene** y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-256">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![Nombre del nuevo archivo de escena](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="1fd6a-258">Tenga en cuenta que debe guardar las escenas de Unity dentro de la carpeta *assets* , ya que deben estar asociadas con el proyecto Unity.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-258">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="1fd6a-259">La creación de la carpeta Scenes (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-259">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="1fd6a-260">El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-260">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![Configuración de compilación predeterminada](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="1fd6a-262">En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-262">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="1fd6a-263">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-263">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="1fd6a-264">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-264">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="1fd6a-265">La **versión de scripting en tiempo de ejecución** debe ser **Experimental (.net 4,6 equivalente)**, lo que desencadenará una necesidad de reiniciar el editor.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-265">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="1fd6a-266">El **back-end de scripting** debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-266">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="1fd6a-267">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-267">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Establecer API compantiblity](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="1fd6a-269">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-269">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="1fd6a-270">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-270">**InternetClient**</span></span>

        2.  <span data-ttu-id="1fd6a-271">**Cámara web**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-271">**Webcam**</span></span>

        3. <span data-ttu-id="1fd6a-272">**Micrófono**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-272">**Microphone**</span></span>

        ![Configurar los valores de publicación](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="1fd6a-274">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-274">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![Configurar la configuración de XR](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="1fd6a-276">De nuevo en la *configuración de compilación* , los *\# proyectos de Unity C* ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-276">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="1fd6a-277">Cierre la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-277">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="1fd6a-278">Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-278">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="1fd6a-279">Capítulo 4: importar el archivo DLL de Newtonsoft en Unity</span><span class="sxs-lookup"><span data-stu-id="1fd6a-279">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1fd6a-280">Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [Azure-Mr-302B. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y después continúe en el [capítulo 6](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-280">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="1fd6a-281">Este curso requiere el uso de la biblioteca **Newtonsoft** , que se puede agregar como un archivo DLL a los recursos.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-281">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="1fd6a-282">El paquete que contiene [esta biblioteca se puede descargar desde este vínculo](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-282">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="1fd6a-283">Para importar la biblioteca de Newtonsoft en el proyecto, use el paquete de Unity que se incluía con este curso.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-283">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="1fd6a-284">Agregue el *. unitypackage Tools* a Unity mediante la opción de menú de \* >  *paquetes importar* *paquete*  >  *personalizado*\* de paquetes.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-284">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="1fd6a-285">En el cuadro **importar paquete Unity** que aparece, asegúrese de que todo lo que hay en **Complementos** (y incluido) está seleccionado.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-285">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importar todos los elementos del paquete](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="1fd6a-287">Haga clic en el botón **importar** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-287">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="1fd6a-288">Vaya a la carpeta **Newtonsoft** en **Complementos** en la vista de proyecto y seleccione el *Newtonsoft.Jsen el complemento*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-288">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![Seleccionar complemento de Newtonsoft](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="1fd6a-290">Con el *complementoNewtonsoft.Jsactivado* , asegúrese de que **cualquier plataforma** esté **desactivada**, asegúrese de que **WSAPlayer** también está **desactivado** y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-290">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="1fd6a-291">Esto es solo para confirmar que los archivos están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-291">This is just to confirm that the files are configured correctly.</span></span>

    ![Configuración del complemento Newtonsoft](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="1fd6a-293">Al marcar estos complementos, se configuran para que solo se usen en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-293">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="1fd6a-294">Hay un conjunto diferente de ellos en la carpeta WSA que se usará después de exportar el proyecto desde Unity.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-294">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="1fd6a-295">A continuación, debe abrir la carpeta **WSA** , dentro de la carpeta **Newtonsoft**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-295">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="1fd6a-296">Verá una copia del mismo archivo que acaba de configurar.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-296">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="1fd6a-297">Seleccione el archivo y, a continuación, en el inspector, asegúrese de que</span><span class="sxs-lookup"><span data-stu-id="1fd6a-297">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="1fd6a-298">**Cualquier plataforma** está **desactivada**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-298">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="1fd6a-299">**solo** se **comprueba** **WSAPlayer**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-299">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="1fd6a-300">No **procesar** está **activado**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-300">**Dont process** is **checked**</span></span>

    ![Configuración de la plataforma del complemento de Newtonsoft](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="1fd6a-302">Capítulo 5: configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="1fd6a-302">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="1fd6a-303">En el panel jerarquía, seleccione la *cámara principal*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-303">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="1fd6a-304">Una vez seleccionado, podrá ver todos los componentes de la *cámara principal* en el *panel del inspector*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-304">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="1fd6a-305">El objeto de *cámara* debe tener el nombre de la **cámara principal** (tenga en cuenta la ortografía).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-305">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="1fd6a-306">La **etiqueta** de cámara principal se debe establecer en **MainCamera** (tenga en cuenta la ortografía).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-306">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="1fd6a-307">Asegúrese de que la **posición de transformación** está establecida en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-307">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="1fd6a-308">Establezca **marcas de borrado** en **color sólido** (Ignore esto para los auriculares inmersivo).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-308">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="1fd6a-309">Establezca el color de **fondo** del componente de la cámara en **negro, alfa 0 (código hexadecimal: #00000000)** (no se tiene en cuenta para el casco inmersivo).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-309">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![Configurar las propiedades del componente de cámara](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="1fd6a-311">Capítulo 6: crear la clase CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-311">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="1fd6a-312">En este momento está listo para escribir código.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-312">At this point you are ready to write some code.</span></span>

<span data-ttu-id="1fd6a-313">Comenzará con la clase *CustomVisionAnalyser* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-313">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="1fd6a-314">Las llamadas a la **Custom Vision Service** realizada en el código que se muestra a continuación se realizan mediante la **API de REST de Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-314">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="1fd6a-315">Mediante este procedimiento, verá cómo implementar y usar esta API (útil para entender cómo implementar algo similar por su cuenta).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-315">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="1fd6a-316">Tenga en cuenta que Microsoft ofrece un **SDK de Custom Vision Service** que también se puede usar para realizar llamadas al servicio.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-316">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="1fd6a-317">Para obtener más información, visite el artículo [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-317">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="1fd6a-318">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-318">This class is responsible for:</span></span>

-   <span data-ttu-id="1fd6a-319">Cargar la imagen más reciente capturada como una matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-319">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="1fd6a-320">Envío de la matriz de bytes a la instancia de Azure *Custom Vision Service* para su análisis.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-320">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="1fd6a-321">Recibir la respuesta como una cadena JSON.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-321">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="1fd6a-322">Deserializar la respuesta y pasar la *predicción* resultante a la clase *SceneOrganiser* , que se encargará de cómo se debe mostrar la respuesta.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-322">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="1fd6a-323">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-323">To create this class:</span></span>

1.  <span data-ttu-id="1fd6a-324">Haga clic con el botón secundario en la *carpeta de recursos* que se encuentra en el *panel Proyecto* y, a continuación, haga clic en **crear > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-324">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="1fd6a-325">Llame a los **scripts** de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-325">Call the folder **Scripts**.</span></span>

    ![Crear carpeta de scripts](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="1fd6a-327">Haga doble clic en la carpeta que acaba de crear para abrirla.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-327">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="1fd6a-328">Haga clic con el botón derecho en la carpeta y luego haga clic en **crear**  >  **\# script de C**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-328">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1fd6a-329">Asigne al script el nombre *CustomVisionAnalyser*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-329">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="1fd6a-330">Haga doble clic en el nuevo script *CustomVisionAnalyser* para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-330">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="1fd6a-331">Actualice los espacios de nombres en la parte superior del archivo para que coincidan con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-331">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="1fd6a-332">En la clase *CustomVisionAnalyser* , agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-332">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="1fd6a-333">Asegúrese de insertar la **clave de predicción** en la variable **PredictionKey** y el **punto de conexión de predicción** en la variable **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-333">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="1fd6a-334">Los copió en el *Bloc de notas* anteriormente en el curso.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-334">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="1fd6a-335">Ahora es necesario agregar el código para **activo ()** para inicializar la variable de instancia:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-335">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="1fd6a-336">Elimine los métodos **Start ()** y **Update ()**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-336">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="1fd6a-337">A continuación, agregue la corutina (con el método estático **GetImageAsByteArray ()** debajo de ella), que obtendrá los resultados del análisis de la imagen capturada por la clase *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-337">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1fd6a-338">En la corutina **AnalyseImageCapture** , hay una llamada a la clase *SceneOrganiser* que se va a crear todavía.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-338">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="1fd6a-339">Por lo tanto, **deje las líneas comentadas por ahora**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-339">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="1fd6a-340">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-340">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="1fd6a-341">Capítulo 7: creación de la clase CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="1fd6a-341">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="1fd6a-342">La clase que creará ahora es la clase *CustomVisionObjects* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-342">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="1fd6a-343">Este script contiene una serie de objetos utilizados por otras clases para serializar y deserializar las llamadas realizadas a la *Custom Vision Service*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-343">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="1fd6a-344">Es importante tomar nota del punto de conexión que le proporciona el Custom Vision Service, ya que se ha configurado la siguiente estructura JSON para que funcione con [*Custom Vision predicción v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-344">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="1fd6a-345">Si tiene una versión diferente, puede que tenga que actualizar la siguiente estructura.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-345">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="1fd6a-346">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-346">To create this class:</span></span>

1.  <span data-ttu-id="1fd6a-347">Haga clic con el botón derecho en la carpeta **scripts** y luego haga clic en **crear**  >  **\# script de C**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-347">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1fd6a-348">Llame al script *CustomVisionObjects*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-348">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="1fd6a-349">Haga doble clic en el nuevo script **CustomVisionObjects** para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-349">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="1fd6a-350">Agregue los siguientes espacios de nombres al principio del archivo:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-350">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="1fd6a-351">Elimine los métodos **Start ()** y **Update ()** dentro de la clase *CustomVisionObjects* ; Esta clase debe estar ahora vacía.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-351">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="1fd6a-352">Agregue las siguientes clases **fuera** de la clase *CustomVisionObjects* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-352">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="1fd6a-353">La biblioteca *Newtonsoft* usa estos objetos para serializar y deserializar los datos de respuesta:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-353">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="1fd6a-354">Capítulo 8: creación de la clase VoiceRecognizer</span><span class="sxs-lookup"><span data-stu-id="1fd6a-354">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="1fd6a-355">Esta clase reconocerá la entrada de voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-355">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="1fd6a-356">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-356">To create this class:</span></span>

1.  <span data-ttu-id="1fd6a-357">Haga clic con el botón derecho en la carpeta **scripts** y luego haga clic en **crear**  >  **\# script de C**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-357">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1fd6a-358">Llame al script *VoiceRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-358">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="1fd6a-359">Haga doble clic en el nuevo script **VoiceRecognizer** para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-359">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="1fd6a-360">Agregue los siguientes espacios de nombres encima de la clase *VoiceRecognizer* :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-360">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="1fd6a-361">A continuación, agregue las siguientes variables dentro de la clase *VoiceRecognizer* , sobre el método *Start ()* :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-361">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="1fd6a-362">Agregue los métodos **activo ()** e **Inicio ()** , que configurarán las *palabras clave* del usuario para que se reconozcan al asociar una etiqueta a una imagen:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-362">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="1fd6a-363">Elimine el método **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-363">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="1fd6a-364">Agregue el siguiente controlador, al que se llama cada vez que se reconoce la entrada de voz:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-364">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="1fd6a-365">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-365">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="1fd6a-366">No se preocupe por el código que podría parecer que presenta un error, ya que proporcionaremos más clases pronto, lo que solucionará estos errores.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-366">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="1fd6a-367">Capítulo 9: creación de la clase CustomVisionTrainer</span><span class="sxs-lookup"><span data-stu-id="1fd6a-367">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="1fd6a-368">Esta clase encadenará una serie de llamadas web para entrenar el *Custom Vision Service*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-368">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="1fd6a-369">Cada llamada se explicará en detalle justo encima del código.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-369">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="1fd6a-370">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-370">To create this class:</span></span>

1.  <span data-ttu-id="1fd6a-371">Haga clic con el botón derecho en la carpeta **scripts** y luego haga clic en **crear**  >  **\# script de C**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-371">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1fd6a-372">Llame al script *CustomVisionTrainer*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-372">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="1fd6a-373">Haga doble clic en el nuevo script *CustomVisionTrainer* para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-373">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="1fd6a-374">Agregue los siguientes espacios de nombres encima de la clase *CustomVisionTrainer* :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-374">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="1fd6a-375">A continuación, agregue las siguientes variables dentro de la clase *CustomVisionTrainer* , sobre el método **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-375">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="1fd6a-376">La dirección URL de entrenamiento que se usa aquí se proporciona en la documentación de *Custom Vision training 1,2* y tiene una estructura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="1fd6a-376">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="1fd6a-377">Para obtener más información, visite la [*API de referencia de Custom Vision Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-377">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="1fd6a-378">Es importante tener en cuenta el punto de conexión que el Custom Vision Service proporciona para el modo de entrenamiento, ya que la estructura JSON usada (dentro de la clase **CustomVisionObjects** ) se ha configurado para funcionar con [*Custom Vision Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-378">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="1fd6a-379">Si tiene una versión diferente, puede que tenga que actualizar la estructura de *objetos* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-379">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="1fd6a-380">Asegúrese de agregar el valor de **clave de servicio** (clave de entrenamiento) y el valor de identificador de **proyecto** , que anotó anteriormente; Estos son los valores que [recopiló en el portal anteriormente en el curso (capítulo 2, paso 10 y posteriores)](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-380">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-project).</span></span>

5.  <span data-ttu-id="1fd6a-381">Agregue los siguientes métodos **Start ()** y Activate **()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-381">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="1fd6a-382">Estos métodos se llaman en la inicialización y contienen la llamada para configurar la interfaz de usuario:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-382">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="1fd6a-383">Elimine el método **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-383">Delete the **Update()** method.</span></span> <span data-ttu-id="1fd6a-384">Esta clase no la necesitará.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-384">This class will not need it.</span></span>

7.  <span data-ttu-id="1fd6a-385">Agregue el método **RequestTagSelection ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-385">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="1fd6a-386">Este método es el primero que se llama cuando se ha capturado una imagen y se ha almacenado en el dispositivo y ahora está lista para enviarse al *Custom Vision Service*, para entrenarla.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-386">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="1fd6a-387">Este método muestra, en la interfaz de usuario de entrenamiento, un conjunto de palabras clave que el usuario puede usar para etiquetar la imagen que se ha capturado.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-387">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="1fd6a-388">También alerta a la clase *VoiceRecognizer* para empezar a escuchar al usuario de la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-388">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="1fd6a-389">Agregue el método **VerifyTag ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-389">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="1fd6a-390">Este método recibirá la entrada de voz reconocida por la clase **VoiceRecognizer** y comprobará su validez y, a continuación, iniciará el proceso de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-390">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="1fd6a-391">Agregue el método **SubmitImageForTraining ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-391">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="1fd6a-392">Este método iniciará el proceso de aprendizaje de Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-392">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="1fd6a-393">El primer paso consiste en recuperar el **ID** . de etiqueta del servicio que está asociado a la entrada de voz validada del usuario.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-393">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="1fd6a-394">El **ID** . de etiqueta se cargará junto con la imagen.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-394">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="1fd6a-395">Agregue el método **TrainCustomVisionProject ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-395">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="1fd6a-396">Una vez que la imagen se haya enviado y etiquetado, se llamará a este método.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-396">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="1fd6a-397">Se creará una nueva iteración que se entrenará con todas las imágenes anteriores enviadas al servicio más la imagen que se acaba de cargar.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-397">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="1fd6a-398">Una vez que se haya completado el entrenamiento, este método llamará a un método para establecer la **iteración** recién creada como **predeterminada**, de modo que el punto de conexión que se usa para el análisis sea la iteración entrenada más reciente.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-398">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="1fd6a-399">Agregue el método **SetDefaultIteration ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-399">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="1fd6a-400">Este método establecerá la iteración previamente creada y entrenada como *predeterminada*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-400">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="1fd6a-401">Una vez completado, este método tendrá que eliminar la iteración anterior existente en el servicio.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-401">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="1fd6a-402">En el momento de redactar este curso, existe un límite de diez (10) iteraciones máximas que pueden existir al mismo tiempo en el servicio.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-402">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="1fd6a-403">Agregue el método **DeletePreviousIteration ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-403">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="1fd6a-404">Este método buscará y eliminará la iteración no predeterminada anterior:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-404">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="1fd6a-405">El último método que se va a agregar en esta clase es el método **GetImageAsByteArray ()** , que se utiliza en las llamadas web para convertir la imagen capturada en una matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-405">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="1fd6a-406">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-406">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="1fd6a-407">Capítulo 10: creación de la clase SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="1fd6a-407">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="1fd6a-408">Esta clase hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-408">This class will:</span></span>

-   <span data-ttu-id="1fd6a-409">Cree un objeto **cursor** para adjuntar a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-409">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="1fd6a-410">Cree un objeto de **etiqueta** que aparecerá cuando el servicio reconozca los objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-410">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="1fd6a-411">Configure la cámara principal adjuntando los componentes adecuados.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-411">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="1fd6a-412">En el **modo de análisis**, genere las etiquetas en tiempo de ejecución, en el espacio universal adecuado con respecto a la posición de la cámara principal, y muestre los datos recibidos de la Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-412">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="1fd6a-413">En el **modo de entrenamiento**, cree la interfaz de usuario que mostrará las distintas fases del proceso de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-413">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="1fd6a-414">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-414">To create this class:</span></span>

1.  <span data-ttu-id="1fd6a-415">Haga clic con el botón derecho en la carpeta **scripts** y luego haga clic en **crear**  >  **\# script de C**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-415">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1fd6a-416">Asigne al script el nombre *SceneOrganiser*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-416">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="1fd6a-417">Haga doble clic en el nuevo script *SceneOrganiser* para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-417">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="1fd6a-418">Solo necesitará un espacio de nombres, quite los otros de encima de la clase *SceneOrganiser* :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-418">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="1fd6a-419">A continuación, agregue las siguientes variables dentro de la clase *SceneOrganiser* , sobre el método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-419">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="1fd6a-420">Elimine los métodos **Start ()** y **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-420">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="1fd6a-421">Justo debajo de las variables, agregue el método **activo ()** , que inicializará la clase y configurará la escena.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-421">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="1fd6a-422">Ahora, agregue el método **CreateCameraCursor ()** que crea y coloca el cursor de cámara principal y el método **CreateLabel ()** , que crea el objeto de **etiqueta de análisis** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-422">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="1fd6a-423">Agregue el método **SetCameraStatus ()** , que controlará los mensajes destinados a la malla de texto que proporciona el estado de la cámara.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-423">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="1fd6a-424">Agregue los métodos **PlaceAnalysisLabel ()** y **SetTagsToLastLabel ()** , que generarán y mostrarán los datos del Custom Vision Service en la escena.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-424">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="1fd6a-425">Por último, agregue el método **CreateTrainingUI ()** , que generará la interfaz de usuario que muestra las distintas fases del proceso de entrenamiento cuando la aplicación está en modo de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-425">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="1fd6a-426">Este método también se utilizará para crear el objeto de estado de la cámara.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-426">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="1fd6a-427">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-427">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1fd6a-428">Antes de continuar, abra la clase **CustomVisionAnalyser** y, en el método **AnalyseLastImageCaptured ()** , *Quite las marcas de comentario* de las líneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-428">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="1fd6a-429">Capítulo 11: creación de la clase ImageCapture</span><span class="sxs-lookup"><span data-stu-id="1fd6a-429">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="1fd6a-430">La clase siguiente que va a crear es la clase *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-430">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="1fd6a-431">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-431">This class is responsible for:</span></span>

-   <span data-ttu-id="1fd6a-432">Captura de una imagen con la cámara de HoloLens y su almacenamiento en la carpeta de la *aplicación* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-432">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="1fd6a-433">Controlar los gestos de TAP del usuario.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-433">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="1fd6a-434">Mantener el valor de *enumeración* que determina si la aplicación se ejecutará en modo de *análisis* o en modo de *entrenamiento* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-434">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="1fd6a-435">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-435">To create this class:</span></span>

1.  <span data-ttu-id="1fd6a-436">Vaya a la carpeta **scripts** que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-436">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="1fd6a-437">Haga clic con el botón derecho en la carpeta y, a continuación, haga clic en **crear > \# script de C**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-437">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="1fd6a-438">Asigne al script el nombre *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-438">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="1fd6a-439">Haga doble clic en el nuevo script **ImageCapture** para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-439">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="1fd6a-440">Reemplace los espacios de nombres en la parte superior del archivo por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-440">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="1fd6a-441">A continuación, agregue las siguientes variables dentro de la clase *ImageCapture* , sobre el método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-441">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="1fd6a-442">Ahora es necesario agregar el código para los métodos **activo ()** e **Inicio ()** :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-442">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="1fd6a-443">Implemente un controlador que se llamará cuando se produzca un gesto de TAP.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-443">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="1fd6a-444">En el modo de *análisis* , el método **TapHandler** actúa como un modificador para iniciar o detener el bucle de captura de fotografías.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-444">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="1fd6a-445">En el modo de *entrenamiento* , capturará una imagen de la cámara.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-445">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="1fd6a-446">Cuando el cursor está en verde, significa que la cámara está disponible para tomar la imagen.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-446">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="1fd6a-447">Cuando el cursor está en rojo, significa que la cámara está ocupada.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-447">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="1fd6a-448">Agregue el método que utiliza la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-448">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="1fd6a-449">Agregue los controladores a los que se llamará cuando se haya capturado la foto y cuando esté listo para su análisis.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-449">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="1fd6a-450">A continuación, el resultado se pasa a *CustomVisionAnalyser* o *CustomVisionTrainer* , en función del modo en el que se establece el código.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-450">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="1fd6a-451">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-451">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="1fd6a-452">Ahora que todos los scripts se han completado, vuelva al editor de Unity, haga clic y arrastre la clase **SceneOrganiser** desde la carpeta **scripts** hasta el objeto de **cámara principal** en el *Panel de jerarquías*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-452">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="1fd6a-453">Capítulo 12: antes de la compilación</span><span class="sxs-lookup"><span data-stu-id="1fd6a-453">Chapter 12 - Before building</span></span>

<span data-ttu-id="1fd6a-454">Para realizar una prueba exhaustiva de la aplicación, debe transferirla a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-454">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="1fd6a-455">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-455">Before you do, ensure that:</span></span>

- <span data-ttu-id="1fd6a-456">Toda la configuración mencionada en el [capítulo 2](#chapter-2---training-your-custom-vision-project) se establece correctamente.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-456">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="1fd6a-457">Todos los campos de la **cámara principal**, el panel Inspector, se asignan correctamente.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-457">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="1fd6a-458">El script **SceneOrganiser** se adjunta al objeto de **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-458">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="1fd6a-459">Asegúrese de insertar la **clave de predicción** en la variable **predictionKey** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-459">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="1fd6a-460">Ha insertado el **punto de conexión de predicción** en la variable **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-460">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="1fd6a-461">Ha insertado la **clave de entrenamiento** en la variable **trainingKey** de la clase *CustomVisionTrainer* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-461">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="1fd6a-462">Ha insertado el **identificador del proyecto** en la variable **Projectid** de la clase *CustomVisionTrainer* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-462">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="1fd6a-463">Capítulo 13: compilar y transferir localmente la aplicación</span><span class="sxs-lookup"><span data-stu-id="1fd6a-463">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="1fd6a-464">Para comenzar el proceso de *compilación* :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-464">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="1fd6a-465">Vaya a **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-465">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="1fd6a-466">Marque **\# proyectos de Unity C**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-466">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="1fd6a-467">Haga clic en **Generar**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-467">Click **Build**.</span></span> <span data-ttu-id="1fd6a-468">Unity iniciará una ventana del **Explorador de archivos** , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-468">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="1fd6a-469">Cree esa carpeta ahora y asígnele el nombre **App**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-469">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="1fd6a-470">Después, con la carpeta de la **aplicación** seleccionada, haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-470">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="1fd6a-471">Unity comenzará a compilar el proyecto en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-471">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="1fd6a-472">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-472">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="1fd6a-473">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-473">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="1fd6a-474">Necesitará la dirección IP de HoloLens (para la implementación remota) y para asegurarse de que HoloLens está en **modo de desarrollador**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-474">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="1fd6a-475">Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-475">To do this:</span></span>

    1.  <span data-ttu-id="1fd6a-476">Mientras se contenga HoloLens, abra la **configuración**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-476">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="1fd6a-477">Vaya a **red &**  >  Opciones avanzadas **de Wi-Fi de**  >   Internet</span><span class="sxs-lookup"><span data-stu-id="1fd6a-477">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="1fd6a-478">Anote la dirección **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-478">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="1fd6a-479">A continuación, vuelva a **configuración** y, a continuación, **actualice & Security**  >  **para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="1fd6a-479">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="1fd6a-480">Establezca el **modo de Desarrollador en**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-480">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="1fd6a-481">Vaya a la nueva compilación de Unity (la carpeta de la **aplicación** ) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-481">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="1fd6a-482">En la *configuración de soluciones* , seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-482">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="1fd6a-483">En la *plataforma* de la solución, seleccione **x86, equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-483">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="1fd6a-484">Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (HoloLens, en este caso, que anotó).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-484">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![Establecer dirección IP](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="1fd6a-486">Vaya al menú **compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-486">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="1fd6a-487">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en HoloLens, lista para su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-487">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="1fd6a-488">Para implementar en auriculares inmersivo, establezca la **plataforma** de la solución en el *equipo local* y establezca la **configuración** en *depurar*, con *x86* como **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-488">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="1fd6a-489">A continuación, implemente en el equipo local mediante el elemento de menú **compilar** y seleccione *implementar solución*.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-489">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="1fd6a-490">Para usar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-490">To use the application:</span></span>

<span data-ttu-id="1fd6a-491">Para cambiar la funcionalidad de la aplicación entre el modo de *entrenamiento* y el modo de *predicción* , debe actualizar la variable **AppMode** , ubicada en el método **activo ()** ubicado dentro de la clase *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="1fd6a-491">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="1fd6a-492">or</span><span class="sxs-lookup"><span data-stu-id="1fd6a-492">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="1fd6a-493">En modo de *entrenamiento* :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-493">In *Training* mode:</span></span>

- <span data-ttu-id="1fd6a-494">Fíjese en **mouse** o **teclado** y use el **gesto de puntear**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-494">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="1fd6a-495">A continuación, aparecerá texto en el que se le pedirá que proporcione una etiqueta.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-495">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="1fd6a-496">Por ejemplo, el **mouse** o el **teclado**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-496">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="1fd6a-497">En modo de *predicción* :</span><span class="sxs-lookup"><span data-stu-id="1fd6a-497">In *Prediction* mode:</span></span>

- <span data-ttu-id="1fd6a-498">Mire un objeto y use el **gesto de puntear**.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-498">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="1fd6a-499">Aparecerá el texto proporcionando el objeto detectado, con la probabilidad más alta (se normaliza).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-499">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="1fd6a-500">Capítulo 14: evaluación y mejora del modelo de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="1fd6a-500">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="1fd6a-501">Para que el servicio sea más preciso, debe seguir entrenar el modelo usado para la predicción.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-501">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="1fd6a-502">Esto se logra mediante el uso de la nueva aplicación, con los modos de *entrenamiento* y *predicción* , con los que se necesitan para visitar el portal, que es lo que se trata en este capítulo.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-502">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="1fd6a-503">Esté preparado para volver a visitar su portal muchas veces, para mejorar continuamente el modelo.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-503">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="1fd6a-504">Vuelva al portal de Azure Custom Vision y, una vez que esté en el proyecto, seleccione la pestaña *predicciones* (en el centro superior de la página):</span><span class="sxs-lookup"><span data-stu-id="1fd6a-504">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![Seleccionar la pestaña predicciones](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="1fd6a-506">Verá todas las imágenes que se enviaron al servicio mientras se ejecutaba la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-506">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="1fd6a-507">Si mantiene el mouse sobre las imágenes, le proporcionará las predicciones que se realizaron para esa imagen:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-507">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![Lista de imágenes de predicción](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="1fd6a-509">Seleccione una de las imágenes para abrirla.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-509">Select one of your images to open it.</span></span> <span data-ttu-id="1fd6a-510">Una vez abierta, verá las predicciones realizadas para esa imagen a la derecha.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-510">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="1fd6a-511">Si las predicciones son correctas y desea agregar esta imagen al modelo de entrenamiento del servicio, haga clic en el cuadro de entrada *mis etiquetas* y seleccione la etiqueta que desea asociar.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-511">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="1fd6a-512">Cuando haya terminado, haga clic en el botón *Guardar y cerrar* situado en la parte inferior derecha y continúe con la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-512">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![Seleccionar la imagen que se va a abrir](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="1fd6a-514">Una vez que vuelva a la cuadrícula de imágenes, observará que se quitarán las imágenes que haya agregado etiquetas (y guardado).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-514">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="1fd6a-515">Si encuentra alguna imagen que cree que no tiene el elemento etiquetado, puede eliminarlas haciendo clic en la marca de la imagen (puede hacer esto para varias imágenes) y, a continuación, hacer clic en *eliminar* en la esquina superior derecha de la página de cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-515">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="1fd6a-516">En el menú emergente que aparece a continuación, puede hacer clic en *sí, eliminar* o *no*, para confirmar la eliminación o cancelarla, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-516">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![Eliminación de imágenes](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="1fd6a-518">Cuando esté listo para continuar, haga clic en el botón verde *entrenar* situado en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-518">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="1fd6a-519">El modelo de servicio se entrenará con todas las imágenes que ya ha proporcionado (lo que hará que sea más preciso).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-519">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="1fd6a-520">Una vez completado el entrenamiento, asegúrese de hacer clic en el botón *establecer como predeterminado* una vez más para que la *dirección URL de predicción* siga usando la iteración más actualizada del servicio.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-520">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="1fd6a-521">![Iniciar el modelo de servicio de entrenamiento ](images/AzureLabs-Lab302b-39.png) ![ seleccionar la opción establecer como predeterminada](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="1fd6a-521">![Start training service model](images/AzureLabs-Lab302b-39.png) ![Select make default option](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="1fd6a-522">Su aplicación de API de Custom Vision finalizada</span><span class="sxs-lookup"><span data-stu-id="1fd6a-522">Your finished Custom Vision API application</span></span>

<span data-ttu-id="1fd6a-523">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Custom Vision API para reconocer objetos reales, entrenar el modelo de servicio y mostrar la confianza de lo que se ha detectado.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-523">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![Ejemplo de proyecto terminado](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1fd6a-525">Ejercicios extra</span><span class="sxs-lookup"><span data-stu-id="1fd6a-525">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1fd6a-526">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="1fd6a-526">Exercise 1</span></span>

<span data-ttu-id="1fd6a-527">Entrenar el **Custom Vision Service** para reconocer más objetos.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-527">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1fd6a-528">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="1fd6a-528">Exercise 2</span></span>

<span data-ttu-id="1fd6a-529">Para ampliar la información que ha aprendido, complete los siguientes ejercicios:</span><span class="sxs-lookup"><span data-stu-id="1fd6a-529">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="1fd6a-530">Reproducir un sonido cuando se reconoce un objeto.</span><span class="sxs-lookup"><span data-stu-id="1fd6a-530">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="1fd6a-531">Ejercicio 3</span><span class="sxs-lookup"><span data-stu-id="1fd6a-531">Exercise 3</span></span>

<span data-ttu-id="1fd6a-532">Use la API para volver a entrenar su servicio con las mismas imágenes que está analizando la aplicación, para que el servicio sea más preciso (realice la predicción y el entrenamiento simultáneamente).</span><span class="sxs-lookup"><span data-stu-id="1fd6a-532">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>