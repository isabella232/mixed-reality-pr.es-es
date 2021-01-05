---
title: Instalación de PIX para HoloLens 2
description: Obtenga información sobre cómo instalar PIX para dispositivos HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, captura, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 598a6b891798be7059eae2eff578c6bbbae442f6
ms.sourcegitcommit: 9d79aaa313f003dd42d5610d458031890776ee8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/30/2020
ms.locfileid: "97822922"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="feaab-104">Instalación de PIX para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="feaab-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="feaab-105">[PIX](https://devblogs.microsoft.com/pix) es una herramienta de optimización y depuración del rendimiento para aplicaciones DirectX 12 en Windows.</span><span class="sxs-lookup"><span data-stu-id="feaab-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="feaab-106">Configurar</span><span class="sxs-lookup"><span data-stu-id="feaab-106">Setup</span></span>

1. <span data-ttu-id="feaab-107">Grabe la última [versión]( https://devblogs.microsoft.com/pix/download) de PIX del equipo host y conecte HoloLens 2 a su PC a través de un cable USB.</span><span class="sxs-lookup"><span data-stu-id="feaab-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="feaab-108">Si HoloLens 2 está en una [compilación de Windows Insider](https://insider.windows.com) o tiene una configuración que interrumpe pix, reproduzca  [el dispositivo](https://docs.microsoft.com/hololens/hololens-recovery) para borrar todos los datos.</span><span class="sxs-lookup"><span data-stu-id="feaab-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [reflash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="feaab-109">Habilite el **modo de desarrollador** y el portal de **dispositivos**:</span><span class="sxs-lookup"><span data-stu-id="feaab-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="feaab-110">Abra **configuración** desde la Página principal de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="feaab-110">Open **Settings** from Mixed Reality Home:</span></span>

![Captura de pantalla del menú de HoloLens con el botón configuración resaltado](images/pix-img-01.jpg)

* <span data-ttu-id="feaab-112">Seleccione **actualizar & seguridad**:</span><span class="sxs-lookup"><span data-stu-id="feaab-112">Select **Update & Security**:</span></span>

![Captura de pantalla de la ventana de configuración abierta en HoloLens con el botón actualizar y seguridad resaltado](images/pix-img-02.jpg)

* <span data-ttu-id="feaab-114">Seleccione **para desarrolladores**:</span><span class="sxs-lookup"><span data-stu-id="feaab-114">Select **For Developers**:</span></span>

![Captura de pantalla de la ventana de seguridad y actualizaciones abierto con para desarrolladores botón resaltado](images/pix-img-03.jpg)

* <span data-ttu-id="feaab-116">Activar **usar características de desarrollador** y **Habilitar el portal de dispositivos**</span><span class="sxs-lookup"><span data-stu-id="feaab-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![Captura de pantalla de la ventana para desarrolladores abierta en configuración con el botón habilitar el portal de dispositivos resaltado](images/pix-img-04.jpg)

![Captura de pantalla de la ventana para desarrolladores abierta en configuración con la opción usar desarrollo de características alternancia resaltada](images/pix-img-05.jpg)

* <span data-ttu-id="feaab-119">Con el dispositivo todavía conectado, activo y con el usuario que ha iniciado sesión, inicie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="feaab-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="feaab-120">Asegúrese de que el dispositivo no está en modo de espera o en suspensión.</span><span class="sxs-lookup"><span data-stu-id="feaab-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="feaab-121">Si tiene problemas con este paso, consulte las [instrucciones del portal de dispositivos de Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span><span class="sxs-lookup"><span data-stu-id="feaab-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="feaab-122">Preparación para la implementación</span><span class="sxs-lookup"><span data-stu-id="feaab-122">Preparing for deployment</span></span>

1. <span data-ttu-id="feaab-123">En Visual Studio, establezca **ARM64** como la plataforma y el **dispositivo** como el dispositivo:</span><span class="sxs-lookup"><span data-stu-id="feaab-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![Captura de pantalla de la solución de Visual Studio con la configuración de plataforma y de dispositivo resaltada](images/pix-img-06.png)

2. <span data-ttu-id="feaab-125">Cuando Visual Studio le pide un **PIN** del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="feaab-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Captura de pantalla de la ventana emergente de Visual Studio que solicita el PIN](images/pix-img-07.png)

* <span data-ttu-id="feaab-127">Seleccionar **configuración** de Shell</span><span class="sxs-lookup"><span data-stu-id="feaab-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="feaab-128">Seleccionar **Actualizar seguridad de &**</span><span class="sxs-lookup"><span data-stu-id="feaab-128">Select **Update & Security**</span></span>
* <span data-ttu-id="feaab-129">Seleccione **para desarrolladores** y pulse emparejar en **detección de dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="feaab-129">Select **For Developers** and press Pair under **Device Discovery**</span></span> 

![Captura de pantalla de la ventana para desarrolladores abierta en configuración con la detección de dispositivos resaltada](images/pix-img-08.jpg)

![Captura de pantalla del elemento emergente del dispositivo de pago con código de registro resaltado](images/pix-img-09.jpg)

* <span data-ttu-id="feaab-132">Escriba el número de PIN generado en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="feaab-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="feaab-133">Visual Studio implementará la aplicación en la HoloLens conectada, que puede tardar unos minutos en función de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="feaab-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="feaab-134">Iniciar PIX</span><span class="sxs-lookup"><span data-stu-id="feaab-134">Launching PIX</span></span>

<span data-ttu-id="feaab-135">En primer lugar, use el portal de dispositivos para comprobar que la aplicación no se está ejecutando en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="feaab-135">First, use Device Portal to verify the app isn't running on the HoloLens 2.</span></span> <span data-ttu-id="feaab-136">Después, inicie PIX, conéctese al dispositivo y seleccione **Inicio**:</span><span class="sxs-lookup"><span data-stu-id="feaab-136">Then, launch PIX, connect to your device, and select **Home**:</span></span>

![Captura de pantalla de la pantalla principal de la aplicación PIX](images/pix-img-10.png)

* <span data-ttu-id="feaab-138">Seleccione **conectar** en el menú de la izquierda:</span><span class="sxs-lookup"><span data-stu-id="feaab-138">Select **Connect** from the left-side menu:</span></span>

![Captura de pantalla del menú de la izquierda de la aplicación PIX con el botón conectar resaltado](images/pix-img-11.png)

2. <span data-ttu-id="feaab-140">En la pestaña **equipo** , seleccione **Agregar** y escriba las siguientes credenciales:</span><span class="sxs-lookup"><span data-stu-id="feaab-140">From the **Computer** tab, select **Add**, and enter the following credentials:</span></span>
    * <span data-ttu-id="feaab-141">Alias: según el criterio del usuario</span><span class="sxs-lookup"><span data-stu-id="feaab-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="feaab-142">Nombre de host o dirección IP: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="feaab-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="feaab-143">Seleccione **conectar** en la parte inferior derecha de la pestaña **equipo** :</span><span class="sxs-lookup"><span data-stu-id="feaab-143">Select **Connect** in the lower right of the **Computer** tab:</span></span>

![Captura de pantalla de la ventana conectar aplicación PIX con el alias, el nombre de host, la dirección IP y el botón Agregar resaltados](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="feaab-145">La primera conexión siempre es más lenta porque se están copiando los archivos binarios.</span><span class="sxs-lookup"><span data-stu-id="feaab-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="feaab-146">Cuando PIX se haya conectado a HoloLens 2, busque la aplicación en la sección **seleccionar el proceso de destino** en la pestaña iniciar UWP y seleccione **iniciar**:</span><span class="sxs-lookup"><span data-stu-id="feaab-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and select **Launch**:</span></span>

![Captura de pantalla de la aplicación PIX con la ventana seleccionar el proceso de destino y el botón Launch resaltado](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="feaab-148">GPU capturada</span><span class="sxs-lookup"><span data-stu-id="feaab-148">GPU captured</span></span>

1. <span data-ttu-id="feaab-149">Inicie la captura de GPU; para ello, haga clic en **Photo** en la sección **captura de GPU** :</span><span class="sxs-lookup"><span data-stu-id="feaab-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![Captura de pantalla de la aplicación PIX con el panel de conexión de PC abierto con captura de GPU resaltada](images/pix-img-14.png)

2. <span data-ttu-id="feaab-151">Abra la captura para el análisis; para ello, haga clic en la captura de pantalla generada en el panel **captura de GPU** :</span><span class="sxs-lookup"><span data-stu-id="feaab-151">Open the capture for analysis by clicking on the generated screenshot in the **GPU Capture** panel:</span></span>

![Captura de pantalla de la aplicación PIX con la sección captura de GPU abierta con el panel de captura de GPU resaltado](images/pix-img-15.png)

3. <span data-ttu-id="feaab-153">Presione **Inicio** para iniciar el análisis:</span><span class="sxs-lookup"><span data-stu-id="feaab-153">Press **Start** to begin the analysis:</span></span>

![Captura de pantalla de la aplicación PIX resaltada en el botón Inicio](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="feaab-155">Si recopila datos de control de tiempo después de realizar una captura de GPU, deberá reiniciar el casco.</span><span class="sxs-lookup"><span data-stu-id="feaab-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="feaab-156">Se trata de un reinicio único del dispositivo y es necesario para la recopilación de datos de control de tiempo.</span><span class="sxs-lookup"><span data-stu-id="feaab-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="feaab-157">PIX ya está listo para su uso.</span><span class="sxs-lookup"><span data-stu-id="feaab-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="feaab-158">Consulte también</span><span class="sxs-lookup"><span data-stu-id="feaab-158">See also</span></span>
* [<span data-ttu-id="feaab-159">Página principal de PIX</span><span class="sxs-lookup"><span data-stu-id="feaab-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)