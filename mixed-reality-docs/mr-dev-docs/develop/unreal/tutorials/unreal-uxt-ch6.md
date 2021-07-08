---
title: 6. Empaquetado e implementación en el dispositivo o emulador
description: Parte 6 de 6 de una serie de tutoriales para compilar una aplicación de ajedrez con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 7dbf72a477f376e338d346965b5276eba00ab543
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2021
ms.locfileid: "110711564"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="9f1fe-104">6. Empaquetado e implementación en el dispositivo o emulador</span><span class="sxs-lookup"><span data-stu-id="9f1fe-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="9f1fe-105">En el tutorial anterior, agregó un botón sencillo que restablece la pieza de ajedrez a su posición original.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="9f1fe-106">En esta última sección, preparará la aplicación para que se ejecute en HoloLens 2 o en un emulador.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="9f1fe-107">Si tiene HoloLens 2, puede transmitir en secuencias desde el equipo o el paquete la aplicación para ejecutarla directamente en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="9f1fe-108">Si no tiene un dispositivo, deberá empaquetar la aplicación para que se ejecute en el emulador.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="9f1fe-109">Al final de esta sección, tendrá una aplicación de realidad mixta implementada que se puede reproducir, terminada con interacciones e interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="9f1fe-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9f1fe-110">Objectives</span></span>

* <span data-ttu-id="9f1fe-111">[Solo dispositivo] Transmisión en secuencias a HoloLens 2 con el control remoto de holografías de la aplicación</span><span class="sxs-lookup"><span data-stu-id="9f1fe-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="9f1fe-112">Empaquetado e implementación de la aplicación en un dispositivo o emulador de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9f1fe-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="9f1fe-113">[Solo dispositivo] Transmisión en secuencias</span><span class="sxs-lookup"><span data-stu-id="9f1fe-113">[Device Only] Streaming</span></span>

<span data-ttu-id="9f1fe-114">El [control remoto de holografías](/windows/mixed-reality/add-holographic-remoting) significa la transmisión en secuencias de datos desde un equipo o dispositivo UWP independiente a HoloLens 2, sin cambiar el canal.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-114">[Holographic Remoting](/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="9f1fe-115">Una aplicación host de control remoto recibe una transmisión en secuencias de datos de entrada de HoloLens, representa el contenido en una vista envolvente virtual y vuelve a transmitir en secuencia los fotogramas de contenido a HoloLens a través de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="9f1fe-116">La transmisión en secuencias le permite agregar vistas envolventes remotas al software del equipo de escritorio existente y tener acceso a más recursos del sistema.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="9f1fe-117">Si va a realizar esta ruta con la aplicación de ajedrez, necesitará algunos elementos:</span><span class="sxs-lookup"><span data-stu-id="9f1fe-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="9f1fe-118">Instale **Holographic Remoting Player** desde Microsoft Store en HoloLens 2 y ejecute la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="9f1fe-119">Anote la dirección IP que se muestra en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-119">Note your IP address displayed in the app.</span></span>
    * <span data-ttu-id="9f1fe-120">Vaya a **Editar > Configuración del proyecto** y asegúrese de que **Default RHI** (RHI predeterminado) de Windows está establecido en **Predeterminado** o **D3D11**:</span><span class="sxs-lookup"><span data-stu-id="9f1fe-120">Go to **Edit > Project Settings** and sure the Windows **Default RHI** is set to **Default** or **D3D11**:</span></span>

![RHI predeterminado](../images/unreal/performance-recommendations-img-09.png)

2.  <span data-ttu-id="9f1fe-122">Cuando vuelva a estar en el editor de Unreal, vaya a **Edit > Project Settings** (Editar > Configuración del proyecto) y marque la opción **Enable Remoting** (Habilitar la comunicación remota) en la sección **Open XR Holographic Remoting** (Comunicación remota holográfica de OpenXR).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-122">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Open XR Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="9f1fe-123">Reinicie el editor y, a continuación, escriba la dirección IP del dispositivo (como se muestra en la aplicación Holographic Remoting Player) y haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-123">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="9f1fe-124">Una vez conectado, haga clic en la flecha desplegable situada a la derecha del botón **Play** (Jugar) y seleccione **VR Preview** (Vista previa de VR).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-124">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="9f1fe-125">La aplicación se ejecutará en la ventana Vista previa de VR, de la que se hace streaming al casco de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-125">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="9f1fe-126">Empaquetado e implementación de la aplicación mediante el Portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="9f1fe-126">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="9f1fe-127">Si esta es la primera vez que empaquetas una aplicación de Unreal para HoloLens, deberás descargar los archivos auxiliares desde el iniciador de Epic.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-127">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="9f1fe-128">Vaya a **Preferencias del editor > General > Código fuente > Editor de código fuente** y compruebe que se haya seleccionado Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-128">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="9f1fe-129">Vaya a la pestaña **Biblioteca** en Selector de juegos Epic, seleccione la flecha desplegable situada junto a **Lanzar** > y haga clic en **Opciones**.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-129">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="9f1fe-130">En **Target Platforms** (Plataformas de destino), selecciona **HoloLens 2** y haz clic en **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-130">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="9f1fe-131">![Cambio de la plataforma de destino en la configuración del proyecto](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="9f1fe-131">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="9f1fe-132">Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-132">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="9f1fe-133">Añada un nombre de proyecto en **Project > Description > About > Project Name** (Proyecto > Descripción > Acerca de > Nombre del proyecto).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-133">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="9f1fe-134">Añada **CN=NombreDeLaEmpresa** en **Project > Description > Publisher > Company Distinguished Name** (Proyecto > Descripción > Editor > Nombre distintivo de la empresa).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-134">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="9f1fe-135">Seleccione **Iniciar en VR** en **Proyecto > Descripción > Configuración**.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-135">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f1fe-136">Si deja alguno de estos campos en blanco, se producirá un error al intentar generar un nuevo certificado en el paso 3.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-136">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f1fe-137">El nombre del editor debe tener el [formato de nombres distintivos de LADPv3](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-137">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="9f1fe-138">Un nombre de editor con un formato incorrecto dará lugar al error "Signing key not found.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-138">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="9f1fe-139">The app could not be digitally signed." (Clave de firma no encontrada. No se pudo firmar digitalmente la aplicación.)</span><span class="sxs-lookup"><span data-stu-id="9f1fe-139">The app could not be digitally signed."</span></span> <span data-ttu-id="9f1fe-140">al realizar el empaquetado.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-140">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f1fe-141">Si no selecciona "Iniciar en VR", la aplicación intentará iniciarse en una claqueta.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-141">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![Configuración del proyecto: descripción](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="9f1fe-143">Habilite **Build for HoloLens Emulation** (Compilar para emulación de HoloLens) y/o **Build for HoloLens Device** (Compilar para dispositivo HoloLens) en **Platforms > HoloLens** (Plataformas > HoloLens).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-143">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="9f1fe-144">Haga clic en **Generate new** (Generar nuevo) en la sección **Packaging** (Empaquetado) [junto a **Signing Certificate** (Certificado de firma)].</span><span class="sxs-lookup"><span data-stu-id="9f1fe-144">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f1fe-145">Si utiliza un certificado ya generado, el nombre del editor del certificado debe ser el mismo que el nombre del editor de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-145">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="9f1fe-146">En caso contrario, se producirá el error "Signing key not found.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-146">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="9f1fe-147">The app could not be digitally signed." (Clave de firma no encontrada. No se pudo firmar digitalmente la aplicación.)</span><span class="sxs-lookup"><span data-stu-id="9f1fe-147">The app could not be digitally signed."</span></span> <span data-ttu-id="9f1fe-148">error.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-148">error.</span></span>

![Configuración del proyecto - Plataformas - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="9f1fe-150">Haga clic en **None** (Ninguno) con fines de prueba cuando se le pida que cree una contraseña de clave privada.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-150">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Generación de un nuevo certificado](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="9f1fe-152">Ve a **File > Package Project** (Archivo > Proyecto de paquete) y selecciona **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-152">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="9f1fe-153">Crea una nueva carpeta en la que guardar el paquete y haz clic en **Select Folder** (Seleccionar carpeta).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-153">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="9f1fe-154">Abra el [Portal de dispositivos Windows](/windows/mixed-reality/using-the-windows-device-portal) después de empaquetar la aplicación, vaya a **Vistas > Aplicaciones** y busque la sección **Implementar aplicación**.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-154">Open the [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="9f1fe-155">Haga clic en **Examinar...** , vaya al archivo **ChessApp.appxbundle** y haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-155">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="9f1fe-156">Active la casilla situada junto a **Permitirme seleccionar paquetes de marcos** si es la primera vez que instala la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-156">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="9f1fe-157">En el siguiente cuadro de diálogo, incluya los archivos **VCLibs** y **appx** adecuados (**arm64** para el dispositivo y **x64** para el emulador).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-157">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="9f1fe-158">Puede encontrar los archivos en **HoloLens** dentro de la carpeta donde ha guardado el paquete.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-158">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="9f1fe-159">Haz clic en **Instalar**</span><span class="sxs-lookup"><span data-stu-id="9f1fe-159">Click **Install**</span></span>
    * <span data-ttu-id="9f1fe-160">Ahora puede ir a **Todas las aplicaciones** y pulsar la aplicación recién instalada para ejecutarla, o inicie la aplicación directamente desde el **Portal de dispositivos Windows**.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-160">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="9f1fe-161">Enhorabuena.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-161">Congratulations!</span></span> <span data-ttu-id="9f1fe-162">La aplicación de realidad mixta de HoloLens está finalizada y lista para utilizarse.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-162">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="9f1fe-163">Sin embargo, esto no es todo.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-163">However, you're not at the end of the road.</span></span> <span data-ttu-id="9f1fe-164">MRTK tiene muchas características independientes que puede agregar a los proyectos, como el mapeo espacial, la entrada de mirada y voz, e incluso los códigos QR.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-164">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="9f1fe-165">Puede encontrar más información sobre estas características en [Introducción al desarrollo con Unreal](/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="9f1fe-165">More information on these features can be found in the [Unreal development overview](/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9f1fe-166">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="9f1fe-166">Next Development Checkpoint</span></span>

<span data-ttu-id="9f1fe-167">Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-167">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9f1fe-168">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="9f1fe-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f1fe-169">Entrada de mirada</span><span class="sxs-lookup"><span data-stu-id="9f1fe-169">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="9f1fe-170">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="9f1fe-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f1fe-171">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="9f1fe-171">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="9f1fe-172">Puede volver a los [puntos de control de desarrollo de Unreal](../unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="9f1fe-172">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>