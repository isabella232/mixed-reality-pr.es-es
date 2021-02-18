---
title: Uso de Visual Studio para implementaciones y depuraciones
description: Obtén información sobre cómo crear, depurar e implementar aplicaciones para HoloLens y Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realidad mixta, depurar, implementar
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496102"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="22010-104">Uso de Visual Studio para implementaciones y depuraciones</span><span class="sxs-lookup"><span data-stu-id="22010-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="22010-105">Tanto si usa DirectX como Unity para desarrollar su aplicación de realidad mixta, Visual Studio será una herramienta imprescindible para realizar la depuración y la implementación.</span><span class="sxs-lookup"><span data-stu-id="22010-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="22010-106">En esta sección, aprenderás a:</span><span class="sxs-lookup"><span data-stu-id="22010-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="22010-107">Implementar aplicaciones en tu casco envolvente de HoloLens o Windows Mixed Reality a través de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22010-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="22010-108">Usar el emulador de HoloLens integrado en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22010-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="22010-109">Depurar aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="22010-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22010-110">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="22010-110">Prerequisites</span></span>

1. <span data-ttu-id="22010-111">Consulta [Instalar las herramientas](../../develop/install-the-tools.md#installation-checklist) para obtener instrucciones de instalación.</span><span class="sxs-lookup"><span data-stu-id="22010-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="22010-112">Crea un proyecto de aplicación universal de Windows en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22010-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="22010-113">Para HoloLens (1.ª generación), usa Visual Studio 2017 o una versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="22010-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="22010-114">Para Hololens 2, use Visual Studio 2019 16.2 o una versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="22010-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="22010-115">Se admiten los lenguajes C# y C++.</span><span class="sxs-lookup"><span data-stu-id="22010-115">C# and C++ are supported.</span></span> <span data-ttu-id="22010-116">(También puedes seguir las instrucciones para [crear una aplicación en Unity](../../develop/unity/tutorials/holograms-100.md)).</span><span class="sxs-lookup"><span data-stu-id="22010-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="22010-117">Habilitar el modo de desarrollador</span><span class="sxs-lookup"><span data-stu-id="22010-117">Enabling Developer Mode</span></span>

<span data-ttu-id="22010-118">Para empezar, habilita el **Modo de desarrollador** en tu dispositivo, para que Visual Studio pueda conectarse a él.</span><span class="sxs-lookup"><span data-stu-id="22010-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="22010-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="22010-119">HoloLens</span></span>

1. <span data-ttu-id="22010-120">Enciende tu HoloLens y colócate el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="22010-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="22010-121">Realice el [gesto de inicio](../../design/system-gesture.md) para iniciar el menú principal.</span><span class="sxs-lookup"><span data-stu-id="22010-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="22010-122">Selecciona el icono **Configuración** para iniciar la aplicación en tu entorno.</span><span class="sxs-lookup"><span data-stu-id="22010-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="22010-123">Selecciona el elemento de menú **Actualizar**.</span><span class="sxs-lookup"><span data-stu-id="22010-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="22010-124">Selecciona el elemento de menú **Para desarrolladores**.</span><span class="sxs-lookup"><span data-stu-id="22010-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="22010-125">Habilite el **Modo de desarrollador** para implementar aplicaciones de Visual Studio en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="22010-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="22010-126">Opcional: Desplácese hacia abajo y habilite el **Portal de dispositivos**, que le permitirá conectarse al [Portal de dispositivos Windows](using-the-windows-device-portal.md) en HoloLens desde un explorador web.</span><span class="sxs-lookup"><span data-stu-id="22010-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="22010-127">Equipo Windows</span><span class="sxs-lookup"><span data-stu-id="22010-127">Windows PC</span></span>

<span data-ttu-id="22010-128">Si trabaja con un casco de Windows Mixed Reality conectado al equipo, debe habilitar el **Modo de desarrollador** en el equipo.</span><span class="sxs-lookup"><span data-stu-id="22010-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="22010-129">Ve a **Configuración**.</span><span class="sxs-lookup"><span data-stu-id="22010-129">Go to **Settings**</span></span>
2. <span data-ttu-id="22010-130">Selecciona **Actualización y seguridad**.</span><span class="sxs-lookup"><span data-stu-id="22010-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="22010-131">Selecciona **Para desarrolladores**.</span><span class="sxs-lookup"><span data-stu-id="22010-131">Select **For developers**</span></span>
4. <span data-ttu-id="22010-132">Habilite el **Modo de desarrollador**, lea el aviso de declinación de responsabilidades para la configuración elegida y, a continuación, haga clic en Sí para aceptar el cambio.</span><span class="sxs-lookup"><span data-stu-id="22010-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="22010-133">Implementación de una aplicación de HoloLens a través de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="22010-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="22010-134">Configure el proyecto de Visual Studio con las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="22010-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="22010-135">Seleccione las opciones de compilación de las aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="22010-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="22010-136">En el caso de los proyectos de Unity, elija **Versión** o **Maestro**.</span><span class="sxs-lookup"><span data-stu-id="22010-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="22010-137">Para todos los demás proyectos, elija **Versión**.</span><span class="sxs-lookup"><span data-stu-id="22010-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="22010-138">Puede encontrar definiciones completas para cada opción de compilación en [Exportación y creación de soluciones de Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="22010-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="22010-139">Seleccione la configuración de compilación en función del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="22010-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="22010-140">Selecciona **Máquina remota** en el menú desplegable de destino de la implementación.</span><span class="sxs-lookup"><span data-stu-id="22010-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Destino de implementación de la máquina remota en Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="22010-142">A continuación, debe establecer la conexión remota.</span><span class="sxs-lookup"><span data-stu-id="22010-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="22010-143">Para proyectos de C++ y JavaScript, ve a **Proyecto > Propiedades > Propiedades de configuración > Depuración**.</span><span class="sxs-lookup"><span data-stu-id="22010-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="22010-144">Si está trabajando en un proyecto de C#, debe aparecer automáticamente un cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="22010-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="22010-145">Si el cuadro de diálogo de conexión remota no aparece en el proyecto de C#, puede abrirlo manualmente desde **Propiedades > Depurar**.</span><span class="sxs-lookup"><span data-stu-id="22010-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="22010-146">Escribe la dirección IP del dispositivo en el campo **Dirección** o **Nombre de la máquina**.</span><span class="sxs-lookup"><span data-stu-id="22010-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="22010-147">Puede encontrar la dirección IP de su dispositivo HoloLens en **Configuración > Red e Internet > Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="22010-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="22010-148">Siempre se recomienda especificar manualmente la dirección IP en lugar de depender de la característica Detección automática.</span><span class="sxs-lookup"><span data-stu-id="22010-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="22010-149">Establezca **Modo de autenticación** en **Universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="22010-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Cuadro de diálogo de conexión remota en Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="22010-151">Compile, implemente y depure la aplicación en función de sus necesidades:</span><span class="sxs-lookup"><span data-stu-id="22010-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="22010-152">Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="22010-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="22010-153">Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.</span><span class="sxs-lookup"><span data-stu-id="22010-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="22010-155">La primera vez que implemente una aplicación en HoloLens desde el equipo, deberá escribir un PIN.</span><span class="sxs-lookup"><span data-stu-id="22010-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="22010-156">Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.</span><span class="sxs-lookup"><span data-stu-id="22010-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="22010-157">Implementación de una aplicación de HoloLens a través de USB</span><span class="sxs-lookup"><span data-stu-id="22010-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="22010-158">Seleccione las opciones de compilación de las aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="22010-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="22010-159">En el caso de los proyectos de Unity, elija **Versión** o **Maestro**.</span><span class="sxs-lookup"><span data-stu-id="22010-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="22010-160">Para todos los demás proyectos, elija **Versión**.</span><span class="sxs-lookup"><span data-stu-id="22010-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="22010-161">Puede encontrar definiciones completas para cada opción de compilación en [Exportación y creación de soluciones de Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="22010-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="22010-162">Seleccione la configuración de compilación en función del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="22010-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="22010-163">Selecciona **Dispositivo** en el menú desplegable de destino de la implementación.</span><span class="sxs-lookup"><span data-stu-id="22010-163">Select **Device** in the deployment target drop-down menu</span></span>

![Implementación de dispositivos en Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="22010-165">Compile, implemente y depure la aplicación en función de sus necesidades:</span><span class="sxs-lookup"><span data-stu-id="22010-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="22010-166">Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="22010-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="22010-167">Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.</span><span class="sxs-lookup"><span data-stu-id="22010-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="22010-169">La primera vez que implemente una aplicación en HoloLens desde el equipo, deberá escribir un PIN.</span><span class="sxs-lookup"><span data-stu-id="22010-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="22010-170">Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.</span><span class="sxs-lookup"><span data-stu-id="22010-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="22010-171">Si observa un tiempo de retardo considerable en la implementación de aplicaciones a través de USB, se recomienda usar las [instrucciones para la máquina remota](#deploying-a-hololens-app-over-wi-fi) de la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="22010-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="22010-172">Implementación de una aplicación en el emulador de HoloLens</span><span class="sxs-lookup"><span data-stu-id="22010-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="22010-173">Asegúrese de haber **[instalado el emulador de HoloLens 2 o HoloLens (1.ª generación)](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="22010-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="22010-174">Seleccione la configuración de compilación y el emulador en función del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="22010-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="22010-175">Compile, implemente y depure la aplicación en función de sus necesidades:</span><span class="sxs-lookup"><span data-stu-id="22010-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="22010-176">Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="22010-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="22010-177">Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.</span><span class="sxs-lookup"><span data-stu-id="22010-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="22010-179">Implementación de una aplicación de VR en el equipo local</span><span class="sxs-lookup"><span data-stu-id="22010-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="22010-180">A la hora de usar un casco envolvente de Windows Mixed Reality que se conecte al equipo o al [simulador de Mixed Reality](using-the-windows-mixed-reality-simulator.md):</span><span class="sxs-lookup"><span data-stu-id="22010-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="22010-181">Selecciona una configuración de compilación **x86** o **x64** para tu aplicación.</span><span class="sxs-lookup"><span data-stu-id="22010-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="22010-182">Selecciona **Máquina local** en el menú desplegable de destino de la implementación.</span><span class="sxs-lookup"><span data-stu-id="22010-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="22010-183">Compile, implemente y depure la aplicación en función de sus necesidades:</span><span class="sxs-lookup"><span data-stu-id="22010-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="22010-184">Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="22010-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="22010-185">Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.</span><span class="sxs-lookup"><span data-stu-id="22010-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="22010-186">Emparejamiento del dispositivo</span><span class="sxs-lookup"><span data-stu-id="22010-186">Pairing your device</span></span>

<span data-ttu-id="22010-187">La primera vez que implemente una aplicación desde Visual Studio en HoloLens, deberá escribir un PIN.</span><span class="sxs-lookup"><span data-stu-id="22010-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="22010-188">Para generar un PIN en HoloLens, inicie la aplicación Configuración, vaya a **Actualizar > Para desarrolladores** y pulse **Emparejar**.</span><span class="sxs-lookup"><span data-stu-id="22010-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="22010-189">Cuando el PIN se muestre en HoloLens, escríbalo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22010-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="22010-190">Una vez completado el emparejamiento, pulsa **Listo** en HoloLens para descartar el cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="22010-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="22010-191">En ese momento, el equipo estará emparejado con HoloLens y podrá implementar aplicaciones automáticamente.</span><span class="sxs-lookup"><span data-stu-id="22010-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="22010-192">Repita estos pasos para todos los equipos que se usen para implementar aplicaciones en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="22010-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="22010-193">Para desemparejar HoloLens de todos los equipos emparejados:</span><span class="sxs-lookup"><span data-stu-id="22010-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="22010-194">Inicie la aplicación de **Configuración**, vaya a **Actualizar > Para desarrolladores** y pulse **Borrar**.</span><span class="sxs-lookup"><span data-stu-id="22010-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="22010-195">Depurador de gráficos para HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="22010-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="22010-196">Las herramientas de Diagnóstico de gráficos de Visual Studio son muy útiles a la hora de escribir y optimizar una aplicación holográfica.</span><span class="sxs-lookup"><span data-stu-id="22010-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="22010-197">Consulta [Diagnóstico de gráficos de Visual Studio en MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) para obtener todos los detalles.</span><span class="sxs-lookup"><span data-stu-id="22010-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="22010-198">**Para iniciar el depurador de gráficos**</span><span class="sxs-lookup"><span data-stu-id="22010-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="22010-199">Sigue las instrucciones anteriores para usar un dispositivo o un emulador como destino.</span><span class="sxs-lookup"><span data-stu-id="22010-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="22010-200">Ve a **Depurar > Gráficos > Iniciar diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="22010-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="22010-201">Es posible que la primera vez que realice un diagnóstico con HoloLens obtenga un error de tipo "Acceso denegado".</span><span class="sxs-lookup"><span data-stu-id="22010-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="22010-202">Reinicie HoloLens para permitir que se apliquen los permisos actualizados y vuelva a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="22010-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="22010-203">Generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="22010-203">Profiling</span></span>

<span data-ttu-id="22010-204">Las herramientas de generación de perfiles de Visual Studio te permiten analizar el rendimiento y el uso de recursos de tu aplicación.</span><span class="sxs-lookup"><span data-stu-id="22010-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="22010-205">Esto incluye herramientas para optimizar el uso de la CPU, la memoria, los gráficos y la red.</span><span class="sxs-lookup"><span data-stu-id="22010-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="22010-206">Consulta [Ejecutar las herramientas de diagnóstico sin depuración en MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) para obtener todos los detalles.</span><span class="sxs-lookup"><span data-stu-id="22010-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="22010-207">**Para iniciar las herramientas de generación de perfiles con HoloLens**</span><span class="sxs-lookup"><span data-stu-id="22010-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="22010-208">Sigue las instrucciones anteriores para usar un dispositivo o un emulador como destino.</span><span class="sxs-lookup"><span data-stu-id="22010-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="22010-209">Ve a **Depurar > Iniciar herramientas de diagnóstico sin depuración...** .</span><span class="sxs-lookup"><span data-stu-id="22010-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="22010-210">Selecciona las herramientas que quieres utilizar.</span><span class="sxs-lookup"><span data-stu-id="22010-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="22010-211">Seleccione **Inicio**.</span><span class="sxs-lookup"><span data-stu-id="22010-211">Select **Start**</span></span>
5. <span data-ttu-id="22010-212">Es posible que la primera vez que realice un diagnóstico sin depuración con HoloLens obtenga un error de tipo "Acceso denegado".</span><span class="sxs-lookup"><span data-stu-id="22010-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="22010-213">Reinicie HoloLens para permitir que se apliquen los permisos actualizados y vuelva a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="22010-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="22010-214">Depuración de una aplicación instalada o en ejecución</span><span class="sxs-lookup"><span data-stu-id="22010-214">Debugging an installed or running app</span></span>

<span data-ttu-id="22010-215">Puede usar Visual Studio para depurar una aplicación universal de Windows instalada sin implementarla desde un proyecto de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22010-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="22010-216">Esto resulta útil si quiere depurar un paquete de la aplicación instalado o si quiere depurar una aplicación que ya se esté ejecutando.</span><span class="sxs-lookup"><span data-stu-id="22010-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="22010-217">Ve a **Depurar > Otros destinos de depuración > Depurar paquete de aplicaciones instalado**.</span><span class="sxs-lookup"><span data-stu-id="22010-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="22010-218">Selecciona el destino **Máquina remota** para HoloLens o **Máquina local** para los cascos envolventes.</span><span class="sxs-lookup"><span data-stu-id="22010-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="22010-219">Escribe la **dirección IP** de tu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="22010-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="22010-220">Selecciona el modo de autenticación **Universal**.</span><span class="sxs-lookup"><span data-stu-id="22010-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="22010-221">En la ventana se muestran las aplicaciones en ejecución e inactivas.</span><span class="sxs-lookup"><span data-stu-id="22010-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="22010-222">Elige la que quieras depurar.</span><span class="sxs-lookup"><span data-stu-id="22010-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="22010-223">Elige el tipo de código que quieras depurar (administrado, nativo, mixto).</span><span class="sxs-lookup"><span data-stu-id="22010-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="22010-224">Seleccione **Adjuntar** o **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="22010-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="22010-225">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="22010-225">Next Development Checkpoint</span></span>

<span data-ttu-id="22010-226">Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, significa que ya se encuentra a la mitad de la fase de implementación.</span><span class="sxs-lookup"><span data-stu-id="22010-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="22010-227">Desde aquí, puede continuar con el siguiente tema:</span><span class="sxs-lookup"><span data-stu-id="22010-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22010-228">Implementación en el emulador de HoloLens</span><span class="sxs-lookup"><span data-stu-id="22010-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="22010-229">O bien puede ir directamente a agregar servicios avanzados:</span><span class="sxs-lookup"><span data-stu-id="22010-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22010-230">Servicios avanzados</span><span class="sxs-lookup"><span data-stu-id="22010-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="22010-231">Puede volver a los [puntos de control de desarrollo de Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="22010-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="22010-232">Consulta también</span><span class="sxs-lookup"><span data-stu-id="22010-232">See also</span></span>
* [<span data-ttu-id="22010-233">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="22010-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="22010-234">Uso del emulador de HoloLens</span><span class="sxs-lookup"><span data-stu-id="22010-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="22010-235">Implementación y depuración de aplicaciones para la Plataforma universal de Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="22010-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="22010-236">Habilitar el dispositivo para el desarrollo</span><span class="sxs-lookup"><span data-stu-id="22010-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)