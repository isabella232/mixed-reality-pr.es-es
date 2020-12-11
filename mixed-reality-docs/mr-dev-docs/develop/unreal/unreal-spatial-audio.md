---
title: Audio espacial en Unreal
description: Aprenda los pormenores del complemento de audio espacial de Unreal Engine.
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development, mixed reality headset, windows mixed reality headset, virtual reality headset, spatial audio
ms.openlocfilehash: fa87862f6a6af456ea344b67e22f1640c9cfafb4
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609546"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="df861-104">Audio espacial en Unreal</span><span class="sxs-lookup"><span data-stu-id="df861-104">Spatial Audio in Unreal</span></span>

<span data-ttu-id="df861-105">A diferencia de la visión, los seres humanos escuchan el sonido envolvente en 360 grados.</span><span class="sxs-lookup"><span data-stu-id="df861-105">Unlike vision, humans hear in 360-degree surround sound.</span></span> <span data-ttu-id="df861-106">El sonido espacial emula el funcionamiento de la audición humana y proporciona las indicaciones necesarias para identificar las ubicaciones del sonido en el espacio real.</span><span class="sxs-lookup"><span data-stu-id="df861-106">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="df861-107">Al agregar sonido espacial en las aplicaciones de realidad mixta, mejora el nivel de inmersión de la experiencia de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="df861-107">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your user's experience.</span></span>  

<span data-ttu-id="df861-108">El procesamiento de sonido espacial de alta calidad es complejo, por lo que HoloLens 2 incluye hardware dedicado para procesar esos objetos de sonido.</span><span class="sxs-lookup"><span data-stu-id="df861-108">High-quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="df861-109">Para poder acceder a este soporte de procesamiento de hardware, debe instalar el complemento **MicrosoftSpatialSound** en su proyecto de Unreal.</span><span class="sxs-lookup"><span data-stu-id="df861-109">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="df861-110">Este artículo le guiará a través de la instalación y configuración de ese complemento y le indicará recursos más detallados.</span><span class="sxs-lookup"><span data-stu-id="df861-110">This article will walk you through the installation and configuration of the plugin and point you towards more in-depth resources.</span></span>

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="df861-111">Instalación del complemento de sonido espacial de Microsoft</span><span class="sxs-lookup"><span data-stu-id="df861-111">Installing the Microsoft Spatial Sound plugin</span></span>

<span data-ttu-id="df861-112">El primer paso para agregar sonido espacial a su proyecto es instalar el complemento de sonido espacial de Microsoft, que puede buscar de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="df861-112">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span>

1. <span data-ttu-id="df861-113">Haga clic en **Editar > Complementos** y busque **MicrosoftSpatialSound** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="df861-113">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span>
2. <span data-ttu-id="df861-114">Active la casilla **Habilitado** en el complemento **MicrosoftSpatialSound**.</span><span class="sxs-lookup"><span data-stu-id="df861-114">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span>
3. <span data-ttu-id="df861-115">Reinicie el editor de Unreal mediante la opción **Reiniciar ahora** desde la página de complementos.</span><span class="sxs-lookup"><span data-stu-id="df861-115">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span>

> [!NOTE]
> <span data-ttu-id="df861-116">Si todavía no lo ha hecho, deberá instalar los complementos de **Microsoft Windows Mixed Reality** y **HoloLens** siguiendo las instrucciones de la sección **[Inicialización del proyecto](tutorials/unreal-uxt-ch2.md)** de nuestra serie de tutoriales de Unreal.</span><span class="sxs-lookup"><span data-stu-id="df861-116">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](tutorials/unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Complemento de audio espacial de Unreal](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="df861-118">Cuando se reinicia el editor, el proyecto ya está preparado.</span><span class="sxs-lookup"><span data-stu-id="df861-118">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="df861-119">Configuración del complemento de espacialización para la plataforma HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="df861-119">Setting the spatialization plugin for HoloLens 2 platform</span></span>

<span data-ttu-id="df861-120">La configuración del complemento de espacialización se realiza por plataforma.</span><span class="sxs-lookup"><span data-stu-id="df861-120">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="df861-121">Puede habilitar el complemento de sonido espacial de Microsoft para HoloLens 2 de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="df861-121">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="df861-122">Seleccione **Editar > Configuración del proyecto**, desplácese a \*\*Plataformas y haga clic en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="df861-122">Selecting **Edit > Project Settings**, scrolling to \*\*Platforms, and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="df861-123">Expanda las propiedades **Audio** y establezca el campo **Spatialization Plugin** (Complemento de la espacialización) en **Microsoft Spatial Sound** (Sonido espacial de Microsoft).</span><span class="sxs-lookup"><span data-stu-id="df861-123">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![Complemento de espacialización para la plataforma HoloLens](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="df861-125">Si va a obtener una vista previa de la aplicación en el editor de Unreal en un equipo de escritorio, deberá repetir los pasos anteriores para la plataforma **Windows**:</span><span class="sxs-lookup"><span data-stu-id="df861-125">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Complemento de espacialización para la plataforma Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="df861-127">Habilitación del audio espacial en la estación de trabajo</span><span class="sxs-lookup"><span data-stu-id="df861-127">Enabling spatial audio on your workstation</span></span>

<span data-ttu-id="df861-128">El audio espacial está deshabilitado de forma predeterminada en las versiones de escritorio de Windows.</span><span class="sxs-lookup"><span data-stu-id="df861-128">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="df861-129">Puede habilitarlo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="df861-129">You can enable it by:</span></span>
* <span data-ttu-id="df861-130">Haga clic con el botón derecho en el icono de **volumen** de la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="df861-130">Right-clicking on the **volume** icon in the task bar.</span></span>
    + <span data-ttu-id="df861-131">Elija **Sonido espacial > Windows Sonic para auriculares** para obtener la mejor representación de lo que escuchará en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="df861-131">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![Complemento de espacialización](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="df861-133">Esta opción solo es necesaria si tiene previsto probar el proyecto en el editor de Unreal.</span><span class="sxs-lookup"><span data-stu-id="df861-133">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="df861-134">Creación de objetos de atenuación</span><span class="sxs-lookup"><span data-stu-id="df861-134">Creating Attenuation objects</span></span>

<span data-ttu-id="df861-135">Después de instalar y configurar los complementos necesarios:</span><span class="sxs-lookup"><span data-stu-id="df861-135">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="df861-136">Busque un actor de **Ambient Sound** (Sonido ambiental) actor en la ventana **Place Actors** (Colocar actores) y arrástrelo a la ventana **Scene** (Escena).</span><span class="sxs-lookup"><span data-stu-id="df861-136">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![Adición de un actor de sonido ambiental](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="df861-138">Convierta el actor de **Ambient Sound** (Sonido ambiental) en un elemento secundario de un elemento visual de la escena.</span><span class="sxs-lookup"><span data-stu-id="df861-138">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span>
    * <span data-ttu-id="df861-139">Un actor de sonido ambiental no tiene ninguna representación visual de forma predeterminada, por lo que solo oirá un sonido de su posición en la escena.</span><span class="sxs-lookup"><span data-stu-id="df861-139">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="df861-140">Al adjuntarlo a un elemento visual, el actor se muestra y se mueve como cualquier otro recurso.</span><span class="sxs-lookup"><span data-stu-id="df861-140">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="df861-141">Haga clic con el botón derecho en **Content Browser** (Explorador de contenido) y seleccione **Create Advanced Asset -> Sounds -> Sound Attenuation** (Crear recurso avanzado -> Sonidos -> Atenuación de sonido):</span><span class="sxs-lookup"><span data-stu-id="df861-141">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![Creación de un recurso de atenuación de sonido](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="df861-143">Haga clic con el botón derecho en el recurso **Sound Attenuation** (Atenuación de sonido) en la ventana **Content Browser** (Explorador de contenido) y seleccione la opción **Edit** (Editar) para abrir la ventana de propiedades.</span><span class="sxs-lookup"><span data-stu-id="df861-143">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="df861-144">Cambie el valor de **Spatialization Method** (Método de espacialización) a **Binaural**.</span><span class="sxs-lookup"><span data-stu-id="df861-144">Switch the **Spatialization Method** to **Binaural**.</span></span>

![Establecimiento del método de espacialización](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="df861-146">Seleccione el actor de **Ambient Sound** (Sonido ambiental) y desplácese hacia abajo hasta la sección **Attenuation** (Atenuación) del panel **Details** (Detalles).</span><span class="sxs-lookup"><span data-stu-id="df861-146">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span>
    * <span data-ttu-id="df861-147">Establezca la propiedad **Attenuation Settings** (Configuración de atenuación) en el recurso de **Sound Attenuation** (Atenuación de sonido) que creó.</span><span class="sxs-lookup"><span data-stu-id="df861-147">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![Establecimiento de la configuración de atenuación](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="df861-149">Establezca el **recurso de sonido** que quiere conectar al actor de sonido ambiental:</span><span class="sxs-lookup"><span data-stu-id="df861-149">Set the **Sound Asset** you want to attach to the Ambient Sound actor:</span></span>
    * <span data-ttu-id="df861-150">Actualice la propiedad de **sonido** del actor de sonido ambiental para especificar el archivo SoundAsset que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="df861-150">Update the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![Establecimiento del recurso de sonido](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> <span data-ttu-id="df861-152">El archivo SoundAsset debe ser monoaural para que se pueda espacializar con el complemento de sonido espacial de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df861-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="df861-153">Para buscar las propiedades del archivo de sonido, puede mantener el puntero sobre el recurso en la ventana Content Browser (Explorador de contenido), tal como se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="df861-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![Nuevo recurso de atenuación de sonido](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="df861-155">Una vez configurado el recurso de sonido, el sonido ambiental se puede espacializar con el soporte de descarga de hardware dedicado en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="df861-155">When the sound asset is configured, the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="df861-156">Configuración de objetos para la espacialización</span><span class="sxs-lookup"><span data-stu-id="df861-156">Configuring objects for spatialization</span></span>

<span data-ttu-id="df861-157">Trabajar con audio espacial significa responsabilizarse de administrar el comportamiento del sonido en un entorno virtual.</span><span class="sxs-lookup"><span data-stu-id="df861-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="df861-158">El enfoque principal es crear objetos de sonido que parezcan más altos cuando el usuario esté cerca y más silenciosos cuando el usuario esté lejos.</span><span class="sxs-lookup"><span data-stu-id="df861-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="df861-159">Esto se conoce como atenuación de sonido y hace que los sonidos se oigan como si estuvieran en una posición fija.</span><span class="sxs-lookup"><span data-stu-id="df861-159">This is referred to as sound attenuation, making sounds appear as if they're positioned in a fixed spot.</span></span>

<span data-ttu-id="df861-160">Todos los objetos de atenuación tienen valores modificables de:</span><span class="sxs-lookup"><span data-stu-id="df861-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="df861-161">Distancia</span><span class="sxs-lookup"><span data-stu-id="df861-161">Distance</span></span>
* <span data-ttu-id="df861-162">Espacialización</span><span class="sxs-lookup"><span data-stu-id="df861-162">Spatialization</span></span>
* <span data-ttu-id="df861-163">Absorción de aire</span><span class="sxs-lookup"><span data-stu-id="df861-163">Air Absorption</span></span>
* <span data-ttu-id="df861-164">Foco del agente de escucha</span><span class="sxs-lookup"><span data-stu-id="df861-164">Listener Focus</span></span>
* <span data-ttu-id="df861-165">Envío de reverberación</span><span class="sxs-lookup"><span data-stu-id="df861-165">Reverb Send</span></span>
* <span data-ttu-id="df861-166">Oclusión</span><span class="sxs-lookup"><span data-stu-id="df861-166">Occlusion</span></span>

<span data-ttu-id="df861-167">La [atenuación de sonido en Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) tiene detalles e información específica de la implementación en cada uno de estos temas.</span><span class="sxs-lookup"><span data-stu-id="df861-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="df861-168">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="df861-168">Next Development Checkpoint</span></span>

<span data-ttu-id="df861-169">Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="df861-169">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="df861-170">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="df861-170">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df861-171">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="df861-171">Voice input</span></span>](unreal-voice-input.md)

<span data-ttu-id="df861-172">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="df861-172">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df861-173">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="df861-173">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="df861-174">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="df861-174">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="df861-175">Consulta también</span><span class="sxs-lookup"><span data-stu-id="df861-175">See also</span></span>
* [<span data-ttu-id="df861-176">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="df861-176">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="df861-177">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="df861-177">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="df861-178">MR Spatial 220: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="df861-178">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
