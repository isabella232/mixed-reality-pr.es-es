---
title: Creación de una aplicación para equipos de comunicación remota holográfica
description: Siga este curso para aprender cómo crear una aplicación de PC para la comunicación remota de una experiencia de realidad mixta remota del equipo a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, PC holographic remoting, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392627"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="12e4f-104">2. Creación de una aplicación para PC de comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="12e4f-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="12e4f-105">En este tutorial, aprenderá cómo crear una aplicación de PC para la comunicación remota holográfica y a conectarse a HoloLens 2 en cualquier momento, lo que proporciona una manera de visualizar contenido 3D en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="12e4f-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="12e4f-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="12e4f-106">Objectives</span></span>

* <span data-ttu-id="12e4f-107">Configurar Unity para la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="12e4f-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="12e4f-108">Aprender a compilar e implementar la aplicación con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="12e4f-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="12e4f-109">Desarrollar una aplicación de comunicación remota holográfica y conectarla a HoloLens</span><span class="sxs-lookup"><span data-stu-id="12e4f-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="12e4f-110">Configuración de las funcionalidades</span><span class="sxs-lookup"><span data-stu-id="12e4f-110">Configuring the capabilities</span></span>

<span data-ttu-id="12e4f-111">En la ventana **Project Settings** (Configuración del proyecto), expanda **Publishing Settings** (Configuración de la publicación), desplácese hacia abajo a la sección Capabilities (Funcionalidades) y seleccione la casilla de funcionalidad que aparece a continuación además de las funcionalidades ya existentes.</span><span class="sxs-lookup"><span data-stu-id="12e4f-111">In the **Project Settings** window, expand the **Publishing Settings**, scroll down to the Capabilities section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="12e4f-112">Servidor cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="12e4f-112">Internet Clint server</span></span>
* <span data-ttu-id="12e4f-113">Servidor cliente de red privada</span><span class="sxs-lookup"><span data-stu-id="12e4f-113">Private Network Client Server</span></span>

![Habilitación de funcionalidades](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a><span data-ttu-id="12e4f-115">Compilación de la aplicación para PC</span><span class="sxs-lookup"><span data-stu-id="12e4f-115">Build your application to PC</span></span>

<span data-ttu-id="12e4f-116">La aplicación de comunicación remota holográfica ya está lista para compilarse en su PC.</span><span class="sxs-lookup"><span data-stu-id="12e4f-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="12e4f-117">Siga los pasos que se indican a continuación y realice estos cambios para compilar esta aplicación en su PC.</span><span class="sxs-lookup"><span data-stu-id="12e4f-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="12e4f-118">Prueba de la aplicación remota de comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="12e4f-118">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="12e4f-119">Para conectar la aplicación de PC a HoloLens 2, siga el proceso siguiente:</span><span class="sxs-lookup"><span data-stu-id="12e4f-119">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="12e4f-120">1. Instalación de la aplicación Remoting Player en el dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="12e4f-120">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="12e4f-121">En HoloLens 2, visite la aplicación Store y busque "**Remoting Player**".</span><span class="sxs-lookup"><span data-stu-id="12e4f-121">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="12e4f-122">Seleccione la aplicación **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="12e4f-122">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="12e4f-123">Pulse **Instalar** una vez para descargar e instalar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="12e4f-123">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="12e4f-124">2. Conexión de la aplicación de comunicación remota holográfica para PC a Remoting Player</span><span class="sxs-lookup"><span data-stu-id="12e4f-124">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="12e4f-125">Inicie **Remoting Player** en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="12e4f-125">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="12e4f-126">Tome nota de la **dirección IP** de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="12e4f-126">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="12e4f-127">**Remoting Player** la mostrará como un holograma en cuanto se inicie.</span><span class="sxs-lookup"><span data-stu-id="12e4f-127">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="12e4f-128">Abra la aplicación de comunicación remota holográfica para PC en su PC.</span><span class="sxs-lookup"><span data-stu-id="12e4f-128">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="12e4f-129">Una vez iniciada la aplicación, escriba la **dirección IP** y haga clic en el botón **Conectar** para conectarse.</span><span class="sxs-lookup"><span data-stu-id="12e4f-129">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="12e4f-130">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="12e4f-130">Congratulations</span></span>

<span data-ttu-id="12e4f-131">En este tutorial, aprendió cómo crear una aplicación para la comunicación remota holográfica y a conectarse a HoloLens 2 en cualquier momento, lo que proporciona una manera de visualizar contenido 3D en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="12e4f-131">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="12e4f-132">Una vez que HoloLens esté conectado a la aplicación de comunicación remota holográfica para PC, debería ver la experiencia de realidad mixta transmitida en el dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="12e4f-132">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
