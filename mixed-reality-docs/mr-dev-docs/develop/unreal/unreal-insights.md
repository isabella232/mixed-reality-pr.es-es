---
title: Generación de perfiles con información inreal
description: Obtenga información sobre cómo usar información no real en HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, desarrollo, Prof., información inreal, documentación, guías, características, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486429"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="0f4af-104">Generación de perfiles con información inreal</span><span class="sxs-lookup"><span data-stu-id="0f4af-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="0f4af-105">La [información inreal](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) es un sistema de generación de perfiles que recopila, analiza y visualiza datos de un motor inreal.</span><span class="sxs-lookup"><span data-stu-id="0f4af-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="0f4af-106">El sistema de generación de perfiles puede ayudarle a encontrar cuellos de botella y áreas de optimización donde el rendimiento de las aplicaciones podría usar un aumento.</span><span class="sxs-lookup"><span data-stu-id="0f4af-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="0f4af-107">Normalmente, se habilita la información no real directamente desde el editor, pero para HoloLens 2 deberá usar la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="0f4af-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="0f4af-108">Configurar</span><span class="sxs-lookup"><span data-stu-id="0f4af-108">Setup</span></span>

<span data-ttu-id="0f4af-109">No real le permite crear y configurar un "perfil personalizado" en el iniciador de HoloLens con los parámetros de la línea de comandos que permiten obtener información inreal.</span><span class="sxs-lookup"><span data-stu-id="0f4af-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="0f4af-110">Busque la dirección IP del equipo mediante el comando **ipconfig** en el símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="0f4af-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="0f4af-111">La dirección IP es la dirección IPv4 que se muestra en ipconfig.</span><span class="sxs-lookup"><span data-stu-id="0f4af-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="0f4af-112">Tenga esto en cuenta para más adelante al establecer los parámetros de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="0f4af-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f4af-113">Si está detrás de una VPN, puede que necesite proporcionar la dirección IP proporcionada a través de la VPN en su lugar.</span><span class="sxs-lookup"><span data-stu-id="0f4af-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Captura de pantalla de los resultados de la línea de comandos para el comando ipconfig](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="0f4af-115">Vaya a la parte superior del panel de inreal Engine y Abra **Device Manager** en el botón **Launch (iniciar** ):</span><span class="sxs-lookup"><span data-stu-id="0f4af-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![Captura de pantalla de las opciones de inicio con el administrador de dispositivos resaltado](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="0f4af-117">En el Device Manager, seleccione **Agregar un dispositivo** que no está en la lista:</span><span class="sxs-lookup"><span data-stu-id="0f4af-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![Captura de pantalla del administrador de dispositivos abierto en el motor inreal](images/unreal-insights-img-03.png)

4. <span data-ttu-id="0f4af-119">Haga clic en **seleccionar una plataforma** y elija **HoloLens**:</span><span class="sxs-lookup"><span data-stu-id="0f4af-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![Captura de pantalla de la lista desplegable Agregar dispositivo no enumerado con HoloLens resaltado](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="0f4af-121">Si utiliza IPoverUSB, escriba 127.0.0.1:10080 como identificador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0f4af-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="0f4af-122">Escriba el usuario y la contraseña de HoloLens en sus respectivos campos y rellene **el nombre para mostrar** como desee.</span><span class="sxs-lookup"><span data-stu-id="0f4af-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f4af-123">El identificador de dispositivo es la dirección IP de HoloLens, no el equipo que ejecuta información inreal que encontró en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="0f4af-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![Captura de pantalla de los detalles del dispositivo HoloLens en el administrador de dispositivos](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="0f4af-125">Seleccione **Agregar** y la HoloLens debe aparecer en la lista de dispositivos del administrador de dispositivos:</span><span class="sxs-lookup"><span data-stu-id="0f4af-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![Captura de pantalla de HoloLens agregada a la lista de dispositivos](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="0f4af-127">Launch</span><span class="sxs-lookup"><span data-stu-id="0f4af-127">Launch</span></span>

1. <span data-ttu-id="0f4af-128">Abra el **iniciador del proyecto** desde el panel de UE4 en el botón **Launch (iniciar** ):</span><span class="sxs-lookup"><span data-stu-id="0f4af-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![Captura de pantalla de opciones de inicio con el iniciador de proyecto resaltado](images/unreal-insights-img-07.png)

2. <span data-ttu-id="0f4af-130">Seleccione el **+** botón para crear un perfil personalizado en **perfiles de inicio personalizados**.</span><span class="sxs-lookup"><span data-stu-id="0f4af-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="0f4af-131">Una vez creada, siempre puede editar este perfil más adelante:</span><span class="sxs-lookup"><span data-stu-id="0f4af-131">Once created, you can always edit this profile later:</span></span>

![Captura de pantalla del iniciador del proyecto con perfiles de inicio personalizados resaltados](images/unreal-insights-img-08.png)

3. <span data-ttu-id="0f4af-133">Seleccione el botón **Editar perfil** en el perfil de inicio personalizado de HoloLens y configure:</span><span class="sxs-lookup"><span data-stu-id="0f4af-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="0f4af-134">Seleccione **Cook** en **el libro** para habilitar la copia en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="0f4af-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="0f4af-135">Es posible que desee comprobar **¿desea archivar?** en la sección **archivar** para conservar el archivo. appxbundle generado en lugar de eliminarlo y ahorrar espacio en disco.</span><span class="sxs-lookup"><span data-stu-id="0f4af-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="0f4af-136">Especifique una ubicación para el. appxbundle y cambie a una compilación de desarrollo si lo desea</span><span class="sxs-lookup"><span data-stu-id="0f4af-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![Captura de pantalla de las opciones de Cook en configuración de perfil con Cook en el libro y HoloLens resaltados](images/unreal-insights-img-09.png)

4. <span data-ttu-id="0f4af-138">Establezca **Cómo desea implementar la compilación** para **Copiar en el dispositivo** y activar la sección Launch ( **iniciar** ) de la interfaz de usuario:</span><span class="sxs-lookup"><span data-stu-id="0f4af-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![Captura de pantalla del iniciador del proyecto con opciones de implementación con la opción copiar en el dispositivo resaltada](images/unreal-insights-img-10.png)

5. <span data-ttu-id="0f4af-140">Establezca **parámetros adicionales** de la línea de comandos en la sección **Launch (iniciar** ).</span><span class="sxs-lookup"><span data-stu-id="0f4af-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="0f4af-141">Los parámetros se escribirán en un archivo ue4commandline.txt, empaquetado en la agrupación y se usarán en el inicio.</span><span class="sxs-lookup"><span data-stu-id="0f4af-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="0f4af-142">Pruébelos para los iniciadores: **-tracehost = IP_OF_YOUR_PC-Trace = registro, marcador, fotograma, CPU, GPU, LoadTime, archivo, red**</span><span class="sxs-lookup"><span data-stu-id="0f4af-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="0f4af-143">Puede encontrar una lista completa de los parámetros de inicio disponibles en la [documentación de referencia de Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span><span class="sxs-lookup"><span data-stu-id="0f4af-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="0f4af-144">"IP_OF_YOUR_PC" es la dirección IP que encontramos en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="0f4af-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="0f4af-145">Esta es la dirección IP del equipo que ejecuta información inreal, no la dirección IP de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0f4af-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f4af-146">Los seguimientos pueden llegar a ser grandes muy rápidamente.</span><span class="sxs-lookup"><span data-stu-id="0f4af-146">Traces can get large very quickly.</span></span> <span data-ttu-id="0f4af-147">Habilite solo los canales que necesita para mantener un tamaño de seguimiento bajo.</span><span class="sxs-lookup"><span data-stu-id="0f4af-147">Enable only those channels you need to keep trace size low.</span></span>

![Captura de pantalla de las opciones de configuración de inicio](images/unreal-insights-img-11.png)

6. <span data-ttu-id="0f4af-149">Inicie información no real antes del inicio de la aplicación, de lo contrario, la información no real no podrá inicializarse correctamente antes de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="0f4af-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="0f4af-150">El ejecutable de Insights no real se almacena en la carpeta del motor de archivos binarios, normalmente de la siguiente manera: "C:\Archivos de Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span><span class="sxs-lookup"><span data-stu-id="0f4af-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![Captura de pantalla del ejecutable inreal de Insights en ejecución](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="0f4af-152">Seleccione **atrás** para volver a la raíz del cuadro de diálogo del **iniciador del proyecto** .</span><span class="sxs-lookup"><span data-stu-id="0f4af-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="0f4af-153">De nuevo en el editor, haga clic en **iniciar** en el perfil de inicio personalizado.</span><span class="sxs-lookup"><span data-stu-id="0f4af-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![Captura de pantalla de perfiles de inicio personalizados](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="0f4af-155">Observe que el proyecto está empaquetado, instalado en el dispositivo e iniciado</span><span class="sxs-lookup"><span data-stu-id="0f4af-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="0f4af-156">Generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="0f4af-156">Profiling</span></span>

<span data-ttu-id="0f4af-157">De nuevo en información no real, seleccione la conexión **dinámica** al dispositivo para iniciar la generación de perfiles.</span><span class="sxs-lookup"><span data-stu-id="0f4af-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="0f4af-158">El perfil personalizado se comparte entre proyectos.</span><span class="sxs-lookup"><span data-stu-id="0f4af-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="0f4af-159">Desde aquí, puede usar el perfil personalizado que creó en lugar de tener que hacerlo cada vez.</span><span class="sxs-lookup"><span data-stu-id="0f4af-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="0f4af-160">Solo tiene que volver a crear la conexión con el dispositivo cada vez que se inicia de un momento dado con los pasos 3 a 6 de la [sección de configuración](#setup).</span><span class="sxs-lookup"><span data-stu-id="0f4af-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f4af-161">Vea también</span><span class="sxs-lookup"><span data-stu-id="0f4af-161">See also</span></span>
* [<span data-ttu-id="0f4af-162">Documentación de Insights no real</span><span class="sxs-lookup"><span data-stu-id="0f4af-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

