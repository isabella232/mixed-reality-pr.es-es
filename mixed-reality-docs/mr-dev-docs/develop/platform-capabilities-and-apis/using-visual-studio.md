---
title: Uso de Visual Studio para implementaciones y depuraciones
description: Obtén información sobre cómo crear, depurar e implementar aplicaciones para HoloLens y Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realidad mixta, depurar, implementar
ms.openlocfilehash: 5510646c058f683babff5e9e34dd296f88cd06c3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543231"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="acc93-104">Uso de Visual Studio para implementaciones y depuraciones</span><span class="sxs-lookup"><span data-stu-id="acc93-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="acc93-105">Tanto si usa DirectX como Unity para desarrollar su aplicación de realidad mixta, Visual Studio será una herramienta imprescindible para realizar la depuración y la implementación.</span><span class="sxs-lookup"><span data-stu-id="acc93-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="acc93-106">En esta sección, aprenderás a:</span><span class="sxs-lookup"><span data-stu-id="acc93-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="acc93-107">Implementar aplicaciones en tu casco envolvente de HoloLens o Windows Mixed Reality a través de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="acc93-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="acc93-108">Usar el emulador de HoloLens integrado en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="acc93-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="acc93-109">Depurar aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="acc93-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="acc93-110">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="acc93-110">Prerequisites</span></span>

1. <span data-ttu-id="acc93-111">Consulta [Instalar las herramientas](../../develop/install-the-tools.md#installation-checklist) para obtener instrucciones de instalación.</span><span class="sxs-lookup"><span data-stu-id="acc93-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="acc93-112">Crea un proyecto de aplicación universal de Windows en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="acc93-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="acc93-113">Para HoloLens (1.ª generación), usa Visual Studio 2017 o una versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="acc93-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="acc93-114">Para Hololens 2, use Visual Studio 2019 16.2 o una versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="acc93-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="acc93-115">Se admiten los lenguajes C# y C++.</span><span class="sxs-lookup"><span data-stu-id="acc93-115">C# and C++ are supported.</span></span> <span data-ttu-id="acc93-116">(También puedes seguir las instrucciones para [crear una aplicación en Unity](../../develop/unity/tutorials/holograms-100.md)).</span><span class="sxs-lookup"><span data-stu-id="acc93-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="acc93-117">Habilitar el modo de desarrollador</span><span class="sxs-lookup"><span data-stu-id="acc93-117">Enabling Developer Mode</span></span>

<span data-ttu-id="acc93-118">Para empezar, habilita el **Modo de desarrollador** en tu dispositivo, para que Visual Studio pueda conectarse a él.</span><span class="sxs-lookup"><span data-stu-id="acc93-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="acc93-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="acc93-119">HoloLens</span></span>

1. <span data-ttu-id="acc93-120">Enciende tu HoloLens y colócate el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="acc93-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="acc93-121">Realice el [gesto de inicio](../../design/system-gesture.md) para iniciar el menú principal.</span><span class="sxs-lookup"><span data-stu-id="acc93-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="acc93-122">Selecciona el icono **Configuración** para iniciar la aplicación en tu entorno.</span><span class="sxs-lookup"><span data-stu-id="acc93-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="acc93-123">Selecciona el elemento de menú **Actualizar**.</span><span class="sxs-lookup"><span data-stu-id="acc93-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="acc93-124">Selecciona el elemento de menú **Para desarrolladores**.</span><span class="sxs-lookup"><span data-stu-id="acc93-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="acc93-125">Habilite **Usar las funciones de desarrollador** para implementar aplicaciones de Visual Studio en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="acc93-125">Enable **Use developer features** to deploy apps from Visual Studio to your HoloLens.</span></span> <span data-ttu-id="acc93-126">Si el dispositivo ejecuta Windows Holographic, versión 21H1 o posterior, habilite también **Detección de dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="acc93-126">If your device is running Windows Holographic version 21H1 or newer, also enable **Device discovery**.</span></span>
7. <span data-ttu-id="acc93-127">Opcional: Desplácese hacia abajo y habilite el **Portal de dispositivos**, que le permitirá conectarse al [Portal de dispositivos Windows](using-the-windows-device-portal.md) en HoloLens desde un explorador web.</span><span class="sxs-lookup"><span data-stu-id="acc93-127">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="acc93-128">Equipo Windows</span><span class="sxs-lookup"><span data-stu-id="acc93-128">Windows PC</span></span>

<span data-ttu-id="acc93-129">Si trabaja con un casco de Windows Mixed Reality conectado al equipo, debe habilitar el **Modo de desarrollador** en el equipo.</span><span class="sxs-lookup"><span data-stu-id="acc93-129">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="acc93-130">Ve a **Configuración**.</span><span class="sxs-lookup"><span data-stu-id="acc93-130">Go to **Settings**</span></span>
2. <span data-ttu-id="acc93-131">Selecciona **Actualización y seguridad**.</span><span class="sxs-lookup"><span data-stu-id="acc93-131">Select **Update and Security**</span></span>
3. <span data-ttu-id="acc93-132">Selecciona **Para desarrolladores**.</span><span class="sxs-lookup"><span data-stu-id="acc93-132">Select **For developers**</span></span>
4. <span data-ttu-id="acc93-133">Habilite el **Modo de desarrollador**, lea el aviso de declinación de responsabilidades para la configuración elegida y, a continuación, haga clic en Sí para aceptar el cambio.</span><span class="sxs-lookup"><span data-stu-id="acc93-133">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="acc93-134">Implementación de una aplicación de HoloLens a través de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="acc93-134">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="acc93-135">Configure el proyecto de Visual Studio con las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="acc93-135">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="acc93-136">Seleccione las opciones de compilación de las aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="acc93-136">Select your apps compilation options</span></span>
    * <span data-ttu-id="acc93-137">En el caso de los proyectos de Unity, elija **Versión** o **Maestro**.</span><span class="sxs-lookup"><span data-stu-id="acc93-137">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="acc93-138">Para todos los demás proyectos, elija **Versión**.</span><span class="sxs-lookup"><span data-stu-id="acc93-138">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="acc93-139">Puede encontrar definiciones completas para cada opción de compilación en [Exportación y creación de soluciones de Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="acc93-139">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="acc93-140">Seleccione la configuración de compilación en función del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="acc93-140">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="acc93-141">Selecciona **Máquina remota** en el menú desplegable de destino de la implementación.</span><span class="sxs-lookup"><span data-stu-id="acc93-141">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Destino de implementación de la máquina remota en Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="acc93-143">A continuación, debe establecer la conexión remota.</span><span class="sxs-lookup"><span data-stu-id="acc93-143">Next, you need to set your remote connection.</span></span> <span data-ttu-id="acc93-144">Para proyectos de C++ y JavaScript, ve a **Proyecto > Propiedades > Propiedades de configuración > Depuración**.</span><span class="sxs-lookup"><span data-stu-id="acc93-144">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="acc93-145">Si está trabajando en un proyecto de C#, debe aparecer automáticamente un cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="acc93-145">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="acc93-146">Si el cuadro de diálogo de conexión remota no aparece en el proyecto de C#, puede abrirlo manualmente desde **Propiedades > Depurar**.</span><span class="sxs-lookup"><span data-stu-id="acc93-146">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="acc93-147">Escribe la dirección IP del dispositivo en el campo **Dirección** o **Nombre de la máquina**.</span><span class="sxs-lookup"><span data-stu-id="acc93-147">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="acc93-148">Puede encontrar la dirección IP de su dispositivo HoloLens en **Configuración > Red e Internet > Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="acc93-148">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="acc93-149">Siempre se recomienda especificar manualmente la dirección IP en lugar de depender de la característica Detección automática.</span><span class="sxs-lookup"><span data-stu-id="acc93-149">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="acc93-150">Establezca **Modo de autenticación** en **Universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="acc93-150">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Cuadro de diálogo de conexión remota en Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="acc93-152">Compile, implemente y depure la aplicación en función de sus necesidades:</span><span class="sxs-lookup"><span data-stu-id="acc93-152">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="acc93-153">Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="acc93-153">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="acc93-154">Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.</span><span class="sxs-lookup"><span data-stu-id="acc93-154">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="acc93-156">La primera vez que implemente una aplicación en HoloLens desde el equipo, deberá escribir un PIN.</span><span class="sxs-lookup"><span data-stu-id="acc93-156">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="acc93-157">Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.</span><span class="sxs-lookup"><span data-stu-id="acc93-157">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="acc93-158">Implementación de una aplicación de HoloLens a través de USB</span><span class="sxs-lookup"><span data-stu-id="acc93-158">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="acc93-159">Seleccione las opciones de compilación de las aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="acc93-159">Select your apps compilation options</span></span>
    * <span data-ttu-id="acc93-160">En el caso de los proyectos de Unity, elija **Versión** o **Maestro**.</span><span class="sxs-lookup"><span data-stu-id="acc93-160">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="acc93-161">Para todos los demás proyectos, elija **Versión**.</span><span class="sxs-lookup"><span data-stu-id="acc93-161">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="acc93-162">Puede encontrar definiciones completas para cada opción de compilación en [Exportación y creación de soluciones de Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="acc93-162">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="acc93-163">Seleccione la configuración de compilación en función del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="acc93-163">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="acc93-164">Selecciona **Dispositivo** en el menú desplegable de destino de la implementación.</span><span class="sxs-lookup"><span data-stu-id="acc93-164">Select **Device** in the deployment target drop-down menu</span></span>

![Implementación de dispositivos en Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="acc93-166">Compile, implemente y depure la aplicación en función de sus necesidades:</span><span class="sxs-lookup"><span data-stu-id="acc93-166">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="acc93-167">Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="acc93-167">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="acc93-168">Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.</span><span class="sxs-lookup"><span data-stu-id="acc93-168">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="acc93-170">La primera vez que implemente una aplicación en HoloLens desde el equipo, deberá escribir un PIN.</span><span class="sxs-lookup"><span data-stu-id="acc93-170">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="acc93-171">Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.</span><span class="sxs-lookup"><span data-stu-id="acc93-171">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="acc93-172">Si observa un tiempo de retardo considerable en la implementación de aplicaciones a través de USB, se recomienda usar las [instrucciones para la máquina remota](#deploying-a-hololens-app-over-wi-fi) de la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="acc93-172">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="acc93-173">Implementación de una aplicación en el emulador de HoloLens</span><span class="sxs-lookup"><span data-stu-id="acc93-173">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="acc93-174">Asegúrese de haber **[instalado el emulador de HoloLens 2 o HoloLens (1.ª generación)](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="acc93-174">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="acc93-175">Seleccione la configuración de compilación y el emulador en función del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="acc93-175">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="acc93-176">Compile, implemente y depure la aplicación en función de sus necesidades:</span><span class="sxs-lookup"><span data-stu-id="acc93-176">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="acc93-177">Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="acc93-177">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="acc93-178">Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.</span><span class="sxs-lookup"><span data-stu-id="acc93-178">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="acc93-180">Implementación de una aplicación de VR en el equipo local</span><span class="sxs-lookup"><span data-stu-id="acc93-180">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="acc93-181">A la hora de usar un casco envolvente de Windows Mixed Reality que se conecte al equipo o al [simulador de Mixed Reality](using-the-windows-mixed-reality-simulator.md):</span><span class="sxs-lookup"><span data-stu-id="acc93-181">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="acc93-182">Selecciona una configuración de compilación **x86** o **x64** para tu aplicación.</span><span class="sxs-lookup"><span data-stu-id="acc93-182">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="acc93-183">Selecciona **Máquina local** en el menú desplegable de destino de la implementación.</span><span class="sxs-lookup"><span data-stu-id="acc93-183">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="acc93-184">Compile, implemente y depure la aplicación en función de sus necesidades:</span><span class="sxs-lookup"><span data-stu-id="acc93-184">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="acc93-185">Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="acc93-185">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="acc93-186">Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.</span><span class="sxs-lookup"><span data-stu-id="acc93-186">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="acc93-187">Emparejamiento del dispositivo</span><span class="sxs-lookup"><span data-stu-id="acc93-187">Pairing your device</span></span>

<span data-ttu-id="acc93-188">La primera vez que implemente una aplicación desde Visual Studio en HoloLens, deberá escribir un PIN.</span><span class="sxs-lookup"><span data-stu-id="acc93-188">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="acc93-189">Para generar un PIN en HoloLens, inicie la aplicación Configuración, vaya a **Actualizar > Para desarrolladores** y pulse **Emparejar**.</span><span class="sxs-lookup"><span data-stu-id="acc93-189">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="acc93-190">Cuando el PIN se muestre en HoloLens, escríbalo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="acc93-190">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="acc93-191">Una vez completado el emparejamiento, pulsa **Listo** en HoloLens para descartar el cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="acc93-191">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="acc93-192">En ese momento, el equipo estará emparejado con HoloLens y podrá implementar aplicaciones automáticamente.</span><span class="sxs-lookup"><span data-stu-id="acc93-192">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="acc93-193">Repita estos pasos para todos los equipos que se usen para implementar aplicaciones en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="acc93-193">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="acc93-194">Para desemparejar HoloLens de todos los equipos emparejados:</span><span class="sxs-lookup"><span data-stu-id="acc93-194">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="acc93-195">Inicie la aplicación de **Configuración**, vaya a **Actualizar > Para desarrolladores** y pulse **Borrar**.</span><span class="sxs-lookup"><span data-stu-id="acc93-195">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="acc93-196">Depurador de gráficos para HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="acc93-196">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="acc93-197">Las herramientas de Diagnóstico de gráficos de Visual Studio son muy útiles a la hora de escribir y optimizar una aplicación holográfica.</span><span class="sxs-lookup"><span data-stu-id="acc93-197">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="acc93-198">Consulta [Diagnóstico de gráficos de Visual Studio en MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) para obtener todos los detalles.</span><span class="sxs-lookup"><span data-stu-id="acc93-198">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="acc93-199">**Para iniciar el depurador de gráficos**</span><span class="sxs-lookup"><span data-stu-id="acc93-199">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="acc93-200">Sigue las instrucciones anteriores para usar un dispositivo o un emulador como destino.</span><span class="sxs-lookup"><span data-stu-id="acc93-200">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="acc93-201">Ve a **Depurar > Gráficos > Iniciar diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="acc93-201">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="acc93-202">Es posible que la primera vez que realice un diagnóstico con HoloLens obtenga un error de tipo "Acceso denegado".</span><span class="sxs-lookup"><span data-stu-id="acc93-202">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="acc93-203">Reinicie HoloLens para permitir que se apliquen los permisos actualizados y vuelva a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="acc93-203">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="acc93-204">Generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="acc93-204">Profiling</span></span>

<span data-ttu-id="acc93-205">Las herramientas de generación de perfiles de Visual Studio te permiten analizar el rendimiento y el uso de recursos de tu aplicación.</span><span class="sxs-lookup"><span data-stu-id="acc93-205">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="acc93-206">Esto incluye herramientas para optimizar el uso de la CPU, la memoria, los gráficos y la red.</span><span class="sxs-lookup"><span data-stu-id="acc93-206">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="acc93-207">Consulta [Ejecutar las herramientas de diagnóstico sin depuración en MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) para obtener todos los detalles.</span><span class="sxs-lookup"><span data-stu-id="acc93-207">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="acc93-208">**Para iniciar las herramientas de generación de perfiles con HoloLens**</span><span class="sxs-lookup"><span data-stu-id="acc93-208">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="acc93-209">Sigue las instrucciones anteriores para usar un dispositivo o un emulador como destino.</span><span class="sxs-lookup"><span data-stu-id="acc93-209">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="acc93-210">Ve a **Depurar > Iniciar herramientas de diagnóstico sin depuración...** .</span><span class="sxs-lookup"><span data-stu-id="acc93-210">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="acc93-211">Selecciona las herramientas que quieres utilizar.</span><span class="sxs-lookup"><span data-stu-id="acc93-211">Select the tools you want to use</span></span>
4. <span data-ttu-id="acc93-212">Seleccione **Inicio**.</span><span class="sxs-lookup"><span data-stu-id="acc93-212">Select **Start**</span></span>
5. <span data-ttu-id="acc93-213">Es posible que la primera vez que realice un diagnóstico sin depuración con HoloLens obtenga un error de tipo "Acceso denegado".</span><span class="sxs-lookup"><span data-stu-id="acc93-213">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="acc93-214">Reinicie HoloLens para permitir que se apliquen los permisos actualizados y vuelva a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="acc93-214">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="acc93-215">Depuración de una aplicación instalada o en ejecución</span><span class="sxs-lookup"><span data-stu-id="acc93-215">Debugging an installed or running app</span></span>

<span data-ttu-id="acc93-216">Puede usar Visual Studio para depurar una aplicación universal de Windows instalada sin implementarla desde un proyecto de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="acc93-216">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="acc93-217">Esto resulta útil si quiere depurar un paquete de la aplicación instalado o si quiere depurar una aplicación que ya se esté ejecutando.</span><span class="sxs-lookup"><span data-stu-id="acc93-217">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="acc93-218">Ve a **Depurar > Otros destinos de depuración > Depurar paquete de aplicaciones instalado**.</span><span class="sxs-lookup"><span data-stu-id="acc93-218">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="acc93-219">Selecciona el destino **Máquina remota** para HoloLens o **Máquina local** para los cascos envolventes.</span><span class="sxs-lookup"><span data-stu-id="acc93-219">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="acc93-220">Escribe la **dirección IP** de tu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="acc93-220">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="acc93-221">Selecciona el modo de autenticación **Universal**.</span><span class="sxs-lookup"><span data-stu-id="acc93-221">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="acc93-222">En la ventana se muestran las aplicaciones en ejecución e inactivas.</span><span class="sxs-lookup"><span data-stu-id="acc93-222">The window shows both running and inactive apps.</span></span> <span data-ttu-id="acc93-223">Elige la que quieras depurar.</span><span class="sxs-lookup"><span data-stu-id="acc93-223">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="acc93-224">Elige el tipo de código que quieras depurar (administrado, nativo, mixto).</span><span class="sxs-lookup"><span data-stu-id="acc93-224">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="acc93-225">Seleccione **Adjuntar** o **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="acc93-225">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="acc93-226">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="acc93-226">Next Development Checkpoint</span></span>

<span data-ttu-id="acc93-227">Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, significa que ya se encuentra a la mitad de la fase de implementación.</span><span class="sxs-lookup"><span data-stu-id="acc93-227">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="acc93-228">Desde aquí, puede continuar con el siguiente tema:</span><span class="sxs-lookup"><span data-stu-id="acc93-228">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="acc93-229">Implementación en el emulador de HoloLens</span><span class="sxs-lookup"><span data-stu-id="acc93-229">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="acc93-230">O bien puede ir directamente a agregar servicios avanzados:</span><span class="sxs-lookup"><span data-stu-id="acc93-230">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="acc93-231">Servicios avanzados</span><span class="sxs-lookup"><span data-stu-id="acc93-231">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="acc93-232">Puede volver a los [puntos de control de desarrollo de Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="acc93-232">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="acc93-233">Consulta también</span><span class="sxs-lookup"><span data-stu-id="acc93-233">See also</span></span>
* [<span data-ttu-id="acc93-234">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="acc93-234">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="acc93-235">Uso del emulador de HoloLens</span><span class="sxs-lookup"><span data-stu-id="acc93-235">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="acc93-236">Implementación y depuración de aplicaciones para la Plataforma universal de Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="acc93-236">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="acc93-237">Habilitar el dispositivo para el desarrollo</span><span class="sxs-lookup"><span data-stu-id="acc93-237">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)
