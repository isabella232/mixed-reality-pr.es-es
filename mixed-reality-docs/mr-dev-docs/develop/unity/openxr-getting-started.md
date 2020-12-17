---
title: Uso del complemento OpenXR de realidad mixta para Unity
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: 05adee2d88bc90dcfb5cf8b780212c7622aff786
ms.sourcegitcommit: ce4975f584bb62075bcb66349237b77081fb982b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97644922"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="5de79-104">Uso del complemento OpenXR de realidad mixta para Unity</span><span class="sxs-lookup"><span data-stu-id="5de79-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="5de79-105">A partir de la versión 2020,2 de Unity, el paquete de complementos de OpenXR mixed reality de Microsoft está disponible mediante el administrador de paquetes de Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="5de79-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5de79-106">Prerrequisitos</span><span class="sxs-lookup"><span data-stu-id="5de79-106">Prerequisites</span></span>

*   <span data-ttu-id="5de79-107">Unity 2020,2 o posterior</span><span class="sxs-lookup"><span data-stu-id="5de79-107">Unity 2020.2 or later</span></span>
*   <span data-ttu-id="5de79-108">Complemento de Unity OpenXR 0.1.1 o posterior</span><span class="sxs-lookup"><span data-stu-id="5de79-108">Unity OpenXR plugin 0.1.1 or later</span></span>
*   <span data-ttu-id="5de79-109">Visual Studio 2019 o posterior</span><span class="sxs-lookup"><span data-stu-id="5de79-109">Visual Studio 2019 or later</span></span>
*   <span data-ttu-id="5de79-110">Instalación de la compatibilidad con la plataforma **UWP** en Unity para aplicaciones de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5de79-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="5de79-111">Si va a compilar aplicaciones de VR en el equipo con Windows, el complemento OpenXR de realidad mixta no es necesariamente necesario.</span><span class="sxs-lookup"><span data-stu-id="5de79-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="5de79-112">Sin embargo, querrá instalar el complemento si está personalizando la asignación de controladores para los controladores de HP reverberación G2 o la creación de aplicaciones que funcionan en los auriculares de HoloLens 2 y VR.</span><span class="sxs-lookup"><span data-stu-id="5de79-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="5de79-113">Instalación del complemento OpenXR de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="5de79-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="5de79-114">El proyecto debe instalar los paquetes de administración de **Complementos** de **OpenXR** y XR antes de usar el complemento Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5de79-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="5de79-115">Si ya las ha instalado, ¡ genial!</span><span class="sxs-lookup"><span data-stu-id="5de79-115">If you've already installed them, great!</span></span> <span data-ttu-id="5de79-116">Si no es así, al instalar el complemento OpenXR de realidad mixta se instalarán automáticamente como dependencias:</span><span class="sxs-lookup"><span data-stu-id="5de79-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="5de79-117">En el editor de Unity, vaya a **editar > configuración del proyecto > administrador de paquetes** .</span><span class="sxs-lookup"><span data-stu-id="5de79-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="5de79-118">Expanda la sección **registros de ámbito** , escriba la información siguiente y seleccione **Guardar**:</span><span class="sxs-lookup"><span data-stu-id="5de79-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>   
    * <span data-ttu-id="5de79-119">Establecer **nombre** en **Microsoft Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="5de79-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="5de79-120">Establecer **dirección URL** en **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="5de79-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="5de79-121">Establezca **ámbitos** en **com. Microsoft. mixedreality**</span><span class="sxs-lookup"><span data-stu-id="5de79-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="5de79-122">En **Configuración avanzada**, seleccione **Habilitar paquetes de vista previa** .</span><span class="sxs-lookup"><span data-stu-id="5de79-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![Captura de pantalla de la ventana Administrador de paquetes de Unity abierta en configuración del proyecto](images/openxr-img-01.png)

<span data-ttu-id="5de79-124">El administrador de paquetes de Unity usa un archivo *de manifiesto denominadomanifest.jsen* para determinar qué paquetes se deben instalar y los registros desde los que se pueden instalar.</span><span class="sxs-lookup"><span data-stu-id="5de79-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5de79-125">OpenXR sigue siendo experimental en Unity y este proceso puede cambiar con el tiempo a medida que trabajamos para optimizar la experiencia del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="5de79-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="5de79-126">Registrar la dependencia de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="5de79-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="5de79-127">Una vez que se ha agregado el registro de ámbito de Microsoft Mixed Reality al manifiesto, se puede especificar el paquete OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5de79-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="5de79-128">Para agregar el paquete OpenXR:</span><span class="sxs-lookup"><span data-stu-id="5de79-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="5de79-129">Abra **<projectRoot> /Packages/manifest.jsen** un editor de texto como Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5de79-129">Open **<projectRoot>/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
2. <span data-ttu-id="5de79-130">Modifique la sección de dependencias de los *paquetes/manifest.jsen* el archivo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="5de79-130">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5de79-131">Puede haber más dependencias en el archivo de manifiesto de las que se muestran aquí.</span><span class="sxs-lookup"><span data-stu-id="5de79-131">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="5de79-132">No elimine ninguno de ellos, simplemente agregue la dependencia OpenXR a la lista.</span><span class="sxs-lookup"><span data-stu-id="5de79-132">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.openxr": "0.1.0",
  }
```

3. <span data-ttu-id="5de79-133">Guarde el archivo, vuelva al editor de Unity y abra el administrador de **paquetes** para confirmar que el complemento está instalado:</span><span class="sxs-lookup"><span data-stu-id="5de79-133">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span> 

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con el complemento OpenXR de realidad mixta resaltado](images/openxr-img-03.png)

> [!Note] 
> <span data-ttu-id="5de79-135">Si se quita el paquete OpenXR mediante el administrador de paquetes de Unity, tendrá que volver a agregarlo mediante los pasos descritos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5de79-135">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="5de79-136">Configuración de administración de complementos de XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="5de79-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="5de79-137">Para establecer OpenXR como el tiempo de ejecución en Unity:</span><span class="sxs-lookup"><span data-stu-id="5de79-137">To set OpenXR as the the runtime in Unity:</span></span> 

1. <span data-ttu-id="5de79-138">En el editor de Unity, vaya a **editar > configuración del proyecto** .</span><span class="sxs-lookup"><span data-stu-id="5de79-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="5de79-139">En la lista de opciones, seleccione **Administración de complementos de XR**</span><span class="sxs-lookup"><span data-stu-id="5de79-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="5de79-140">Active las casillas **inicializar XR en el inicio** y **OpenXR (versión preliminar)**</span><span class="sxs-lookup"><span data-stu-id="5de79-140">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="5de79-141">Si el destino es HoloLens 2, asegúrese de que está en la plataforma UWP y seleccione **conjunto de características de Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="5de79-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="5de79-143">Si ve un icono de advertencia rojo junto al **complemento OpenXR (versión preliminar)**, haga clic en el icono y seleccione **corregir todo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5de79-143">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="5de79-144">Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="5de79-144">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de pantalla de la ventana de validación del proyecto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="5de79-146">Ahora está listo para empezar a desarrollar con OpenXR en Unity.</span><span class="sxs-lookup"><span data-stu-id="5de79-146">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="5de79-147">Continúe con la siguiente sección para aprender a usar los ejemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5de79-147">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="5de79-148">Optimization</span><span class="sxs-lookup"><span data-stu-id="5de79-148">Optimization</span></span>

<span data-ttu-id="5de79-149">Si está desarrollando para HoloLens 2, vaya a **Mixed Reality> OpenXR > aplicar la configuración de proyecto recomendada para hololens 2** para obtener un mejor rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5de79-149">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de pantalla del elemento de menú de realidad mixta abrir con OpenXR seleccionado](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="5de79-151">Pruebe las escenas de ejemplo de Unity</span><span class="sxs-lookup"><span data-stu-id="5de79-151">Try out the Unity sample scenes</span></span>

<span data-ttu-id="5de79-152">Para el uso de uno o varios de los ejemplos, instale [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) desde el **Administrador de paquete**:</span><span class="sxs-lookup"><span data-stu-id="5de79-152">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Pacakage Manager**:</span></span>

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con AR Foundation resaltado](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="5de79-154">Ejemplos de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5de79-154">HoloLens 2 samples</span></span>

1. <span data-ttu-id="5de79-155">En el editor de Unity, navegue a la **ventana > administrador de paquetes**</span><span class="sxs-lookup"><span data-stu-id="5de79-155">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="5de79-156">En la lista de paquetes, seleccione **Mixed Reality OpenXR plugin** .</span><span class="sxs-lookup"><span data-stu-id="5de79-156">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="5de79-157">Busque el ejemplo en la lista de **ejemplos** y seleccione **importar** .</span><span class="sxs-lookup"><span data-stu-id="5de79-157">Locate the sample in the **Samples** list and select **Import**</span></span>

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con el complemento OpenXR de realidad mixta seleccionado y el botón de importación de ejemplos resaltado](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
>  <span data-ttu-id="5de79-159">Cuando se actualiza un paquete, Unity ofrece la opción de actualizar los ejemplos importados.</span><span class="sxs-lookup"><span data-stu-id="5de79-159">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="5de79-160">Al actualizar un ejemplo importado se sobrescribirán los cambios realizados en el ejemplo y los recursos asociados.</span><span class="sxs-lookup"><span data-stu-id="5de79-160">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5de79-161">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="5de79-161">Next steps</span></span> 

<span data-ttu-id="5de79-162">Ahora que ha configurado el proyecto para OpenXR y tiene acceso a los ejemplos, consulte [las características](openxr-supported-features.md) que se admiten actualmente en nuestro complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5de79-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="5de79-163">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5de79-163">See also</span></span>
* [<span data-ttu-id="5de79-164">Configurar el proyecto sin MRTK</span><span class="sxs-lookup"><span data-stu-id="5de79-164">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="5de79-165">Configuración recomendada para Unity</span><span class="sxs-lookup"><span data-stu-id="5de79-165">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="5de79-166">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="5de79-166">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)