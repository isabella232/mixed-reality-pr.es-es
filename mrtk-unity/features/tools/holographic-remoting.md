---
title: Control remoto de holografías
description: Documentación sobre la comunicación remota holográfica MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 0fbde863185a9f51b53192a338e9403dc79248db
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176642"
---
# <a name="holographic-remoting"></a><span data-ttu-id="1db64-104">Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="1db64-104">Holographic remoting</span></span>

<span data-ttu-id="1db64-105">La comunicación remota holográfica transmite contenido holográfico desde un equipo a la Microsoft HoloLens en tiempo real, mediante una conexión de Wi-Fi o USB.</span><span class="sxs-lookup"><span data-stu-id="1db64-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="1db64-106">Esta característica puede aumentar significativamente la productividad del desarrollador al desarrollar aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1db64-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="1db64-107">El SDK de XR, como se mencionó a continuación, hace referencia a la nueva canalización de XR de [Unity en Unity 2019.3](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)y más allá de .</span><span class="sxs-lookup"><span data-stu-id="1db64-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="1db64-108">Consulte [aquí](../../configuration/getting-started-with-mrtk-and-xrsdk.md) para obtener más información sobre el uso del SDK de XR con MRTK.</span><span class="sxs-lookup"><span data-stu-id="1db64-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="1db64-109">XR heredado hace referencia a la canalización XR existente que se incluye en Unity 2018, está en desuso en Unity 2019.3 y se ha quitado en Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="1db64-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="1db64-110">Instalación inicial</span><span class="sxs-lookup"><span data-stu-id="1db64-110">Initial setup</span></span>

<span data-ttu-id="1db64-111">Para habilitar la comunicación remota a HoloLens, es importante asegurarse de que el proyecto usa los componentes de comunicación remota más recientes.</span><span class="sxs-lookup"><span data-stu-id="1db64-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="1db64-112">Abrir **ventana > Administrador de paquetes**</span><span class="sxs-lookup"><span data-stu-id="1db64-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="1db64-113">Si usa XR heredado: compruebe que está instalada la versión más reciente Windows Mixed Reality **paquete.**</span><span class="sxs-lookup"><span data-stu-id="1db64-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="1db64-114">Si usa el SDK de XR: compruebe que está instalada la versión más Windows del paquete del complemento **XR.**</span><span class="sxs-lookup"><span data-stu-id="1db64-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="1db64-115">Asegúrese de que la aplicación holographic remoting más reciente está instalada, en la HoloLens, a través del Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="1db64-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="1db64-116">Continúe con las [instrucciones de instalación de XR heredadas](#legacy-xr-setup-instructions) o las instrucciones de configuración del SDK de [XR](#xr-sdk-setup-instructions) en función de la canalización que se utilice en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1db64-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="1db64-117">Instrucciones de configuración de XR heredadas</span><span class="sxs-lookup"><span data-stu-id="1db64-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="1db64-118">Las instrucciones siguientes solo se aplican a la comunicación remota con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1db64-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="1db64-119">Si solo realiza comunicación remota con HoloLens (1.ª generación), vaya directamente a Conexión al HoloLens [con Wi-Fi.](#connecting-to-the-hololens-with-wi-fi)</span><span class="sxs-lookup"><span data-stu-id="1db64-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="1db64-120">Al usar una HoloLens 2, se ha agregado compatibilidad con la comunicación remota de datos de seguimiento de la mano y los ojos articulados a MRTK.</span><span class="sxs-lookup"><span data-stu-id="1db64-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="1db64-121">Para habilitar estas características, siga los pasos documentados en [Importación de DotNetWinRT en el proyecto](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="1db64-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="1db64-122">Una vez importado, el paso siguiente consiste en seleccionar **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Windows Mixed Reality**  >  **Check Configuration (Comprobar configuración).**</span><span class="sxs-lookup"><span data-stu-id="1db64-122">Once imported, the next step is to select **Mixed Reality** > **Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="1db64-123">Este paso agrega una definición de scripting que habilita la dependencia DotNetWinRT.</span><span class="sxs-lookup"><span data-stu-id="1db64-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="1db64-124">Cuando se usa Unity 2019.4 y versiones posteriores, no es necesario ejecutar la utilidad Comprobar configuración.</span><span class="sxs-lookup"><span data-stu-id="1db64-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="1db64-125">Para habilitar el seguimiento de las uniones de manos y el seguimiento de los ojos, siga los pasos descritos en las secciones Depuración HoloLens 2 comunicación remota a través de la importación de paquetes de **Unity** y las secciones relacionadas.</span><span class="sxs-lookup"><span data-stu-id="1db64-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="1db64-126">Depuración de HoloLens 2 comunicación remota mediante la importación de paquetes de Unity</span><span class="sxs-lookup"><span data-stu-id="1db64-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="1db64-127">Si HoloLens 2 y el seguimiento de los ojos no funcionan con la comunicación remota, hay algunos puntos comunes de posibles problemas.</span><span class="sxs-lookup"><span data-stu-id="1db64-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="1db64-128">Se enumeran a continuación en el orden en que se deben comprobar.</span><span class="sxs-lookup"><span data-stu-id="1db64-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="1db64-129">Estos problemas son especialmente relevantes cuando se ejecutan **en Unity 2019.3** o posterior.</span><span class="sxs-lookup"><span data-stu-id="1db64-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="1db64-130">Importación de DotNetWinRT en el proyecto</span><span class="sxs-lookup"><span data-stu-id="1db64-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="1db64-131">Descargar la [herramienta Mixed Reality características](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="1db64-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="1db64-132">En la **vista Detectar características,** seleccione *Mixed Reality proyecciones de WinRT.*</span><span class="sxs-lookup"><span data-stu-id="1db64-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Selección del paquete DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="1db64-134">Haga **clic en Obtener** características y siga [importando el paquete](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="1db64-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="1db64-135">DOTNETWINRT_PRESENT en la configuración del reproductor</span><span class="sxs-lookup"><span data-stu-id="1db64-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="1db64-136">Cuando se usa Unity 2019.4 y versiones posteriores, el DOTNETWINRT_PRESENT define se encuentra dentro de los archivos .asmdef adecuados y no en el reproductor de Unity Configuración.</span><span class="sxs-lookup"><span data-stu-id="1db64-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="1db64-137">El paso Comprobar configuración no es necesario.</span><span class="sxs-lookup"><span data-stu-id="1db64-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="1db64-138">A partir de la versión 2.5.0 de MRTK, por motivos de rendimiento, este #define ya no se establece automáticamente.</span><span class="sxs-lookup"><span data-stu-id="1db64-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="1db64-139">Para habilitar esta marca, use el elemento de menú Mixed Reality Toolkit  >  **Utilities**  >  **Windows Mixed Reality**  >  **Check Configuration** (Comprobar configuración).</span><span class="sxs-lookup"><span data-stu-id="1db64-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="1db64-140">El elemento Comprobar configuración no muestra una confirmación.</span><span class="sxs-lookup"><span data-stu-id="1db64-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="1db64-141">Para confirmar que se ha establecido la definición, vaya a la página de Unity Player Configuración.</span><span class="sxs-lookup"><span data-stu-id="1db64-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="1db64-142">Desde allí, en la pestaña UWP, compruebe en Otros Configuración para definir símbolos de scripting.</span><span class="sxs-lookup"><span data-stu-id="1db64-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="1db64-143">Asegúrese de que DOTNETWINRT_PRESENT está escrito correctamente en esa lista.</span><span class="sxs-lookup"><span data-stu-id="1db64-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="1db64-144">Si está ahí, este paso se ha hecho correctamente.</span><span class="sxs-lookup"><span data-stu-id="1db64-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT Present](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="1db64-146">Eliminación de HoloLens 2 de comunicación remota específica</span><span class="sxs-lookup"><span data-stu-id="1db64-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="1db64-147">Si tiene conflictos u otros problemas debidos a la presencia del adaptador dotNetWinRT, póngase en contacto con uno de nuestros recursos [de ayuda.](../../index.md#getting-help)</span><span class="sxs-lookup"><span data-stu-id="1db64-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="1db64-148">Instrucciones de configuración del SDK de XR</span><span class="sxs-lookup"><span data-stu-id="1db64-148">XR SDK setup instructions</span></span>

<span data-ttu-id="1db64-149">Siga las instrucciones Windows Mixed Reality configuración en la página Introducción a [MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) y el SDK de XR y asegúrese de realizar el paso necesario para la comunicación remota en el editor HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1db64-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="1db64-150">Conexión al HoloLens con Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="1db64-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="1db64-151">Una vez configurado el proyecto, se puede establecer una conexión con el HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1db64-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="1db64-152">En **File > Build Configuración**, asegúrese de que el tipo de compilación del proyecto está establecido en Universal Windows **Platform**</span><span class="sxs-lookup"><span data-stu-id="1db64-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="1db64-153">En la HoloLens, inicie la **aplicación Holographic Remoting.**</span><span class="sxs-lookup"><span data-stu-id="1db64-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="1db64-154">En Unity, seleccione **Window > XR > Holographic Emulation (si usa XR heredado) o Windows XR Plugin Remoting (si** usa el SDK de XR).</span><span class="sxs-lookup"><span data-stu-id="1db64-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Iniciar emulación holográfica](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="1db64-156">Establezca **Modo de emulación** **en Remoto en Dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="1db64-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Establecer modo de emulación](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="1db64-158">(**_Solo se aplica a XR heredado)_** Seleccione la versión **del dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="1db64-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Selección de la versión del dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="1db64-160">Con la dirección IP mostrada por la aplicación Holographic Remoting Player, establezca el **campo Equipo** remoto.</span><span class="sxs-lookup"><span data-stu-id="1db64-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Escribir dirección IP](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="1db64-162">Haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="1db64-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="1db64-163">Si no puede conectarse, asegúrese de que el HoloLens 2 está conectado al equipo y reinicie Unity.</span><span class="sxs-lookup"><span data-stu-id="1db64-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="1db64-164">Conexión a la HoloLens cable USB</span><span class="sxs-lookup"><span data-stu-id="1db64-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="1db64-165">La conexión de cable USB proporciona una mejor calidad y estabilidad de la representación.</span><span class="sxs-lookup"><span data-stu-id="1db64-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="1db64-166">Para usar la conexión de cable USB, desconéctese de la HoloLens de Wi-Fi en la Configuración de HoloLens e inicie la aplicación Holographic Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="1db64-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="1db64-167">Se mostrará una dirección IP que comienza por 169.</span><span class="sxs-lookup"><span data-stu-id="1db64-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="1db64-168">Use esta dirección IP en la configuración de emulación holográfica de Unity para conectarse.</span><span class="sxs-lookup"><span data-stu-id="1db64-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="1db64-169">Una vez identificada la dirección IP del cable USB, es seguro conectar el HoloLens a Wi-Fi de nuevo.</span><span class="sxs-lookup"><span data-stu-id="1db64-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="1db64-170">Inicio de una sesión de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="1db64-170">Starting a remoting session</span></span>

<span data-ttu-id="1db64-171">Con Unity conectado al HoloLens, escriba el modo de reproducción en el editor.</span><span class="sxs-lookup"><span data-stu-id="1db64-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="1db64-172">Una vez completada la sesión, salga del modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="1db64-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="1db64-173">Hay un problema conocido con algunas versiones de Unity en las que el editor puede que se bloquee al entrar en modo de reproducción durante una sesión de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="1db64-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="1db64-174">Este problema puede manifestarse si la ventana Holográfica está abierta cuando se carga el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1db64-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="1db64-175">Para asegurarse de que este problema no se produce, cierre siempre el cuadro de diálogo Holográfico antes de salir de Unity.</span><span class="sxs-lookup"><span data-stu-id="1db64-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="1db64-176">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1db64-176">See also</span></span>

- [<span data-ttu-id="1db64-177">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="1db64-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="1db64-178">Términos de licencia de software de Microsoft Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1db64-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
