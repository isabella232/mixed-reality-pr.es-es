---
title: Configuración básica de seguimiento ocular
description: Configuración del seguimiento de los ojos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Eye Tracking,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144098"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="bb1b0-104">Introducción al seguimiento de los ojos en MRTK</span><span class="sxs-lookup"><span data-stu-id="bb1b0-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="bb1b0-105">En esta página se explica cómo configurar la escena de MRTK de Unity para usar el seguimiento de los ojos en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="bb1b0-106">A continuación se da por supuesto que está empezando con una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="bb1b0-107">Como alternativa, puede consultar nuestros ejemplos de seguimiento ocular [de MRTK](../../example-scenes/eye-tracking-examples-overview.md) ya configurados con montones de excelentes ejemplos sobre los que puede basar directamente.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="bb1b0-108">Lista de comprobación de los requisitos de seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="bb1b0-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="bb1b0-109">Para que el seguimiento de los ojos funcione correctamente, deben cumplirse los siguientes requisitos.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="bb1b0-110">Si no está nuevo en el seguimiento de los HoloLens 2 y en cómo se configura el seguimiento de los ojos en MRTK, no se preocupe.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="bb1b0-111">A continuación se detallará cómo abordar cada uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="bb1b0-112">Se _debe agregar un "proveedor de datos de mirada_ con los ojos" al sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="bb1b0-113">Esto proporciona datos de seguimiento de los ojos de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="bb1b0-114">La _funcionalidad "GazeInput"_ debe estar habilitada en el manifiesto de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="bb1b0-115">**Esta funcionalidad se puede establecer en Unity 2019, pero en Unity 2018 y versiones anteriores esta funcionalidad solo está disponible en Visual Studio y a través de la herramienta de compilación MRTK.**</span><span class="sxs-lookup"><span data-stu-id="bb1b0-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="bb1b0-116">HoloLens debe **calibrarse** con los ojos para el usuario actual.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="bb1b0-117">Consulte nuestro ejemplo para detectar si un usuario está calibrado con los [ojos o no.](eye-tracking-is-user-calibrated.md)</span><span class="sxs-lookup"><span data-stu-id="bb1b0-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="bb1b0-118">Una nota sobre la funcionalidad GazeInput</span><span class="sxs-lookup"><span data-stu-id="bb1b0-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="bb1b0-119">Las herramientas de compilación proporcionadas por MRTK (es decir, Mixed Reality Toolkit -> Utilities -> Build Window) pueden habilitar automáticamente la funcionalidad GazeInput.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="bb1b0-120">Para ello, debe asegurarse de que la "Funcionalidad de entrada de mirada" está activada en la pestaña "Opciones de compilación de Appx":</span><span class="sxs-lookup"><span data-stu-id="bb1b0-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![Herramientas de compilación de MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="bb1b0-122">Esta herramienta encontrará el manifiesto de AppX una vez completada la compilación de Unity y agregará manualmente la funcionalidad GazeInput.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="bb1b0-123">**Antes de Unity 2019,** estas herramientas NO están activas cuando se usa la ventana de compilación integrada de Unity (es decir, archivo -> configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="bb1b0-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="bb1b0-124">Antes de Unity 2019, al usar la ventana de compilación de Unity, la funcionalidad deberá agregarse manualmente después de la compilación de Unity, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="bb1b0-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="bb1b0-125">Abra el proyecto Visual Studio compilado y, a continuación, abra _"Package.appxmanifest"_ en la solución.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="bb1b0-126">Asegúrese de activar la casilla _"GazeInput"_ en _Funcionalidades._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="bb1b0-127">Si no ve una funcionalidad _"GazeInput",_ compruebe que el sistema cumple los [requisitos previos](/windows/mixed-reality/develop/install-the-tools) para usar MRTK (en particular, la versión Windows SDK).</span><span class="sxs-lookup"><span data-stu-id="bb1b0-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="bb1b0-128">_Tenga en cuenta lo siguiente:_ Solo tiene que hacerlo si compila en una nueva carpeta de compilación.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="bb1b0-129">Esto significa que si ya había creado el proyecto de Unity y configurado appxmanifest antes y ahora se ha dirigido de nuevo a la misma carpeta, no tendrá que volver a aplicar los cambios.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="bb1b0-130">Configuración paso a paso del seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="bb1b0-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="bb1b0-131">Configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="bb1b0-131">Setting up the scene</span></span>

<span data-ttu-id="bb1b0-132">Para configurar _MixedRealityToolkit,_ basta con hacer clic en _"Mixed Reality Toolkit -> Configure..."_</span><span class="sxs-lookup"><span data-stu-id="bb1b0-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="bb1b0-133">en la barra de menús.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-133">in the menu bar.</span></span>

![Configuración de MRTK](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="bb1b0-135">Configuración de los perfiles de MRTK necesarios para el seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="bb1b0-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="bb1b0-136">Después de configurar la escena de MRTK, se le pedirá que elija un perfil para MRTK.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="bb1b0-137">Simplemente puede seleccionar _DefaultMixedRealityToolkitConfigurationProfile_ y, a continuación, seleccionar la _opción "Copiar & Personalizar"._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![Perfil de MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider&quot;></a><span data-ttu-id=&quot;bb1b0-139&quot;>Creación de un &quot;proveedor de datos de mirada con los ojos&quot;</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;bb1b0-139&quot;>Create an &quot;eye gaze data provider&quot;</span></span>

- <span data-ttu-id=&quot;bb1b0-140&quot;>Haga clic en _la pestaña &quot;Entrada&quot;_ en el perfil de MRTK.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;bb1b0-140&quot;>Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id=&quot;bb1b0-141&quot;>Para editar el valor predeterminado ( _&quot;DefaultMixedRealityInputSystemProfile"),_ haga clic en el _botón "Clone" (Clonar)_ situado junto a él.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="bb1b0-142">Aparece _el menú "Clonar_ perfil".</span><span class="sxs-lookup"><span data-stu-id="bb1b0-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="bb1b0-143">Simplemente haga clic _en "Clonar"_ en la parte inferior de ese menú.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="bb1b0-144">Haga doble clic en el nuevo perfil de entrada, expanda _"Proveedores de_ datos de entrada" y seleccione _"+ Agregar proveedor de datos"._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="bb1b0-145">Cree un nuevo proveedor de datos:</span><span class="sxs-lookup"><span data-stu-id="bb1b0-145">Create a new data provider:</span></span>
  - <span data-ttu-id="bb1b0-146">En **Tipo,** seleccione _"Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input"_  ->  _"WindowsMixedRealityEyeGazeDataProvider"._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="bb1b0-147">En **Plataformas,** seleccione _"Windows Universal"._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![Proveedor de datos MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="bb1b0-149">Simulación del seguimiento de los ojos en el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="bb1b0-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="bb1b0-150">Puede simular la entrada de seguimiento de los ojos en el Editor de Unity para asegurarse de que los eventos se desencadenan correctamente antes de implementar la aplicación en el HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="bb1b0-151">La señal de mirada con los ojos se simula simplemente usando la ubicación de la cámara como origen de la mirada con los ojos y el vector hacia delante de la cámara como dirección de la mirada con los ojos.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="bb1b0-152">Aunque esto es excelente para las pruebas iniciales, tenga en cuenta que no es una buena imitación para los movimientos rápidos de los ojos.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="bb1b0-153">Para ello, es mejor asegurarse de realizar pruebas frecuentes de las interacciones basadas en los ojos en el HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="bb1b0-154">**Habilite el seguimiento de los ojos simulados:**</span><span class="sxs-lookup"><span data-stu-id="bb1b0-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="bb1b0-155">Haga clic en la _pestaña "Entrada"_ en el perfil de configuración de MRTK.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="bb1b0-156">Desde allí, vaya a _"Input Data Providers" (Proveedores de datos de_  ->  _entrada) "Input Simulation Service" (Servicio de simulación de entrada)._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="bb1b0-157">Clone _"DefaultMixedRealityInputSimpulationProfile"_ para realizar cambios en él.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="bb1b0-158">Active la _casilla "Simular posición de los ojos"._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![Simulación de ojos MRTK](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="bb1b0-160">**Deshabilitar cursor de mirada con** la cabeza predeterminado: en general, se recomienda evitar mostrar un cursor de mirada con los ojos o si es absolutamente necesario para que sea muy _sutil._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="bb1b0-161">Se recomienda ocultar el cursor de mirada con la cabeza predeterminado asociado al perfil de puntero de mirada DE MRTK de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="bb1b0-162">Vaya al perfil de configuración de MRTK -> _"Input"_  ->  _'Pointers' (Punteros de entrada)._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="bb1b0-163">Clone _"DefaultMixedRealityInputPointerProfile"_ para realizar cambios en él.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="bb1b0-164">En la parte superior de _"Configuración_ del puntero", debe asignar un cursor invisible prefab a _"GazeCursor"._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="bb1b0-165">Para ello, seleccione el prefab _"EyeGazeCursor"_ de MRTK Foundation.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="bb1b0-166">Habilitación de la mirada con los ojos en el proveedor de mirada</span><span class="sxs-lookup"><span data-stu-id="bb1b0-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="bb1b0-167">En HoloLens v1, la mirada con la cabeza se usó como técnica de apuntar principal.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="bb1b0-168">Aunque la mirada con la cabeza sigue estando disponible a través de _GazeProvider_ en MRTK, que está conectado a la [cámara,](https://docs.unity3d.com/ScriptReference/Camera.html)puede comprobar el uso de la mirada con los ojos activando la casilla _"IsEyeTrackingEnabled"_ en la configuración de mirada del perfil de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="bb1b0-169">Los desarrolladores pueden alternar entre la mirada con los ojos y la mirada basada en la cabeza en el código cambiando la propiedad _"IsEyeTrackingEnabled"_ de _"GazeProvider"._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="bb1b0-170">Si no se cumple alguno de los requisitos de seguimiento de los ojos, la aplicación volverá automáticamente a la mirada basada en la cabeza.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="bb1b0-171">Acceso a los datos de mirada con los ojos</span><span class="sxs-lookup"><span data-stu-id="bb1b0-171">Accessing eye gaze data</span></span>

<span data-ttu-id="bb1b0-172">Ahora que la escena está configurada para usar el seguimiento de los ojos, echemos un vistazo a cómo acceder a ella en los scripts: Acceso a los datos de seguimiento de los ojos a través de [EyeGazeProvider](eye-tracking-eye-gaze-provider.md) y [selecciones](eye-tracking-target-selection.md)de destino compatibles con los ojos.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="bb1b0-173">Prueba de la aplicación unity en un HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bb1b0-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="bb1b0-174">La compilación de la aplicación con el seguimiento de los ojos debe ser similar a cómo compilaría otras aplicaciones HoloLens 2 MRTK.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="bb1b0-175">Asegúrese de que ha habilitado la funcionalidad *"Entrada* de mirada", como se ha descrito anteriormente en la sección [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability)( Nota sobre la funcionalidad GazeInput).</span><span class="sxs-lookup"><span data-stu-id="bb1b0-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="bb1b0-176">Calibración de los ojos</span><span class="sxs-lookup"><span data-stu-id="bb1b0-176">Eye calibration</span></span>

<span data-ttu-id="bb1b0-177">Por último, no olvide realizar la calibración de los ojos en el HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="bb1b0-178">El sistema de seguimiento de los ojos no devolverá ninguna entrada si el usuario no está calibrado.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="bb1b0-179">La manera más fácil de llegar a la calibración es volteando hacia arriba el visor y hacia atrás.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="bb1b0-180">Debería aparecer una notificación del sistema que le da la bienvenida como nuevo usuario y le pide que pase por la calibración de los ojos.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="bb1b0-181">También puede encontrar la calibración de los ojos en la configuración del sistema: Configuración > sistema > calibración > calibración de los ojos.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="bb1b0-182">Permiso de seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="bb1b0-182">Eye tracking permission</span></span>

<span data-ttu-id="bb1b0-183">Al iniciar la aplicación en el HoloLens 2 por primera vez, aparecerá un mensaje en el que se le pedirá al usuario permiso para usar el seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="bb1b0-184">Si no aparece, suele ser una indicación de que no se estableció la funcionalidad _"GazeInput"._</span><span class="sxs-lookup"><span data-stu-id="bb1b0-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="bb1b0-185">Después de que el símbolo del sistema de permisos se muestre una vez, no se volverá a mostrar automáticamente.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="bb1b0-186">Si _"ha denegado el permiso de seguimiento ocular",_ puede restablecerlo en Configuración -> Privacidad -> Aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="bb1b0-187">Esto debería comenzar a usar el seguimiento ocular en la aplicación mrtk de Unity.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="bb1b0-188">No olvide consultar nuestros tutoriales y ejemplos de seguimiento ocular de [MRTK](../../example-scenes/eye-tracking-examples-overview.md) que muestran cómo usar la entrada de seguimiento ocular y proporcionar scripts que puede reutilizar en sus proyectos.</span><span class="sxs-lookup"><span data-stu-id="bb1b0-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="bb1b0-189">Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit).</span><span class="sxs-lookup"><span data-stu-id="bb1b0-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)