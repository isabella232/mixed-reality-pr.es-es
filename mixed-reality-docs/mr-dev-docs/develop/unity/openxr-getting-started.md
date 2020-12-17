---
title: Uso del complemento OpenXR de realidad mixta para Unity
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: adb678d168d86dc2376ac46caa690e5db036099c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97623017"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="d4d77-104">Uso del complemento OpenXR de realidad mixta para Unity</span><span class="sxs-lookup"><span data-stu-id="d4d77-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="d4d77-105">A partir de la versión 2020,2 de Unity, el paquete de complementos de OpenXR mixed reality de Microsoft está disponible mediante el administrador de paquetes de Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="d4d77-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4d77-106">Prerrequisitos</span><span class="sxs-lookup"><span data-stu-id="d4d77-106">Prerequisites</span></span>

*   <span data-ttu-id="d4d77-107">Unity 2020,2 o posterior</span><span class="sxs-lookup"><span data-stu-id="d4d77-107">Unity 2020.2 or later</span></span>
*   <span data-ttu-id="d4d77-108">Complemento de Unity OpenXR 0.1.1 o posterior</span><span class="sxs-lookup"><span data-stu-id="d4d77-108">Unity OpenXR plugin 0.1.1 or later</span></span>
*   <span data-ttu-id="d4d77-109">Visual Studio 2019 o posterior</span><span class="sxs-lookup"><span data-stu-id="d4d77-109">Visual Studio 2019 or later</span></span>
*   <span data-ttu-id="d4d77-110">Instalación de la compatibilidad con la plataforma **UWP** en Unity para aplicaciones de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d4d77-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="d4d77-111">Si va a compilar aplicaciones de VR en el equipo con Windows, el complemento OpenXR de realidad mixta no es necesariamente necesario.</span><span class="sxs-lookup"><span data-stu-id="d4d77-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="d4d77-112">Sin embargo, querrá instalar el complemento si está personalizando la asignación de controladores para los controladores de HP reverberación G2 o la creación de aplicaciones que funcionan en los auriculares de HoloLens 2 y VR.</span><span class="sxs-lookup"><span data-stu-id="d4d77-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="d4d77-113">Instalación del complemento OpenXR de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="d4d77-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="d4d77-114">Antes de usar el complemento Mixed Reality OpenXR, debe instalar los paquetes de **Administración de complementos** de Unity y del complemento de **OpenXR** :</span><span class="sxs-lookup"><span data-stu-id="d4d77-114">Before using the Mixed Reality OpenXR Plugin, you need to install Unity’s **OpenXR Plugin** and **XR Plugin Management** packages:</span></span>

1. <span data-ttu-id="d4d77-115">En el editor de Unity, vaya a **editar > configuración del proyecto > administrador de paquetes** .</span><span class="sxs-lookup"><span data-stu-id="d4d77-115">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="d4d77-116">Expanda la sección **registros de ámbito** , escriba la información siguiente y seleccione **Guardar**:</span><span class="sxs-lookup"><span data-stu-id="d4d77-116">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>   
    * <span data-ttu-id="d4d77-117">Establecer **nombre** en **Microsoft Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="d4d77-117">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="d4d77-118">Establecer **dirección URL** en **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="d4d77-118">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="d4d77-119">Establezca **ámbitos** en **com. Microsoft. mixedreality**</span><span class="sxs-lookup"><span data-stu-id="d4d77-119">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="d4d77-120">En **Configuración avanzada**, seleccione **Habilitar paquetes de vista previa** .</span><span class="sxs-lookup"><span data-stu-id="d4d77-120">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![Captura de pantalla de la ventana Administrador de paquetes de Unity abierta en configuración del proyecto](images/openxr-img-01.png)

<span data-ttu-id="d4d77-122">El administrador de paquetes de Unity usa un archivo *de manifiesto denominadomanifest.jsen* para determinar qué paquetes se deben instalar y los registros desde los que se pueden instalar.</span><span class="sxs-lookup"><span data-stu-id="d4d77-122">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4d77-123">OpenXR sigue siendo experimental en Unity y este proceso puede cambiar con el tiempo a medida que trabajamos para optimizar la experiencia del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="d4d77-123">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="d4d77-124">Registrar la dependencia de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="d4d77-124">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="d4d77-125">Una vez que se ha agregado el registro de ámbito de Microsoft Mixed Reality al manifiesto, se puede especificar el paquete OpenXR.</span><span class="sxs-lookup"><span data-stu-id="d4d77-125">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="d4d77-126">Para agregar el paquete OpenXR:</span><span class="sxs-lookup"><span data-stu-id="d4d77-126">To add the OpenXR package:</span></span>

1. <span data-ttu-id="d4d77-127">Abra **<projectRoot> /Packages/manifest.jsen** un editor de texto como Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d4d77-127">Open **<projectRoot>/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
2. <span data-ttu-id="d4d77-128">Modifique la sección de dependencias de los *paquetes/manifest.jsen* el archivo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="d4d77-128">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4d77-129">Puede haber más dependencias en el archivo de manifiesto de las que se muestran aquí.</span><span class="sxs-lookup"><span data-stu-id="d4d77-129">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="d4d77-130">No elimine ninguno de ellos, simplemente agregue la dependencia OpenXR a la lista.</span><span class="sxs-lookup"><span data-stu-id="d4d77-130">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.openxr": "0.1.0",
  }
```

3. <span data-ttu-id="d4d77-131">Guarde el archivo, vuelva al editor de Unity y abra el administrador de **paquetes** para confirmar que el complemento está instalado:</span><span class="sxs-lookup"><span data-stu-id="d4d77-131">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span> 

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con el complemento OpenXR de realidad mixta resaltado](images/openxr-img-03.png)

> [!Note] 
> <span data-ttu-id="d4d77-133">Si se quita el paquete OpenXR mediante el administrador de paquetes de Unity, tendrá que volver a agregarlo mediante los pasos descritos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d4d77-133">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="d4d77-134">Configuración de administración de complementos de XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="d4d77-134">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="d4d77-135">Para establecer OpenXR como el tiempo de ejecución en Unity:</span><span class="sxs-lookup"><span data-stu-id="d4d77-135">To set OpenXR as the the runtime in Unity:</span></span> 

1. <span data-ttu-id="d4d77-136">En el editor de Unity, vaya a **editar > configuración del proyecto** .</span><span class="sxs-lookup"><span data-stu-id="d4d77-136">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="d4d77-137">En la lista de opciones, seleccione **Administración de complementos de XR**</span><span class="sxs-lookup"><span data-stu-id="d4d77-137">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="d4d77-138">Active las casillas **inicializar XR en el inicio** y **OpenXR (versión preliminar)**</span><span class="sxs-lookup"><span data-stu-id="d4d77-138">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="d4d77-139">Si el destino es HoloLens 2, asegúrese de que está en la plataforma UWP y seleccione **conjunto de características de Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="d4d77-139">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="d4d77-141">Si ve un icono de advertencia rojo junto al **complemento OpenXR (versión preliminar)**, haga clic en el icono y seleccione **corregir todo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d4d77-141">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="d4d77-142">Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="d4d77-142">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de pantalla de la ventana de validación del proyecto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="d4d77-144">Ahora está listo para empezar a desarrollar con OpenXR en Unity.</span><span class="sxs-lookup"><span data-stu-id="d4d77-144">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="d4d77-145">Continúe con la siguiente sección para aprender a usar los ejemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="d4d77-145">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="d4d77-146">Optimization</span><span class="sxs-lookup"><span data-stu-id="d4d77-146">Optimization</span></span>

<span data-ttu-id="d4d77-147">Si está desarrollando para HoloLens 2, vaya a **Mixed Reality> OpenXR > aplicar la configuración de proyecto recomendada para hololens 2** para obtener un mejor rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d4d77-147">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de pantalla del elemento de menú de realidad mixta abrir con OpenXR seleccionado](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="d4d77-149">Pruebe las escenas de ejemplo de Unity</span><span class="sxs-lookup"><span data-stu-id="d4d77-149">Try out the Unity sample scenes</span></span>

<span data-ttu-id="d4d77-150">Para el uso de uno o varios de los ejemplos, instale [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) desde el **Administrador de paquete**:</span><span class="sxs-lookup"><span data-stu-id="d4d77-150">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Pacakage Manager**:</span></span>

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con AR Foundation resaltado](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="d4d77-152">Ejemplos de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d4d77-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="d4d77-153">En el editor de Unity, navegue a la **ventana > administrador de paquetes**</span><span class="sxs-lookup"><span data-stu-id="d4d77-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="d4d77-154">En la lista de paquetes, seleccione **Mixed Reality OpenXR plugin** .</span><span class="sxs-lookup"><span data-stu-id="d4d77-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="d4d77-155">Busque el ejemplo en la lista de **ejemplos** y seleccione **importar** .</span><span class="sxs-lookup"><span data-stu-id="d4d77-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con el complemento OpenXR de realidad mixta seleccionado y el botón de importación de ejemplos resaltado](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
>  <span data-ttu-id="d4d77-157">Cuando se actualiza un paquete, Unity ofrece la opción de actualizar los ejemplos importados.</span><span class="sxs-lookup"><span data-stu-id="d4d77-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="d4d77-158">Al actualizar un ejemplo importado se sobrescribirán los cambios realizados en el ejemplo y los recursos asociados.</span><span class="sxs-lookup"><span data-stu-id="d4d77-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d4d77-159">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="d4d77-159">Next steps</span></span> 

<span data-ttu-id="d4d77-160">Ahora que ha configurado el proyecto para OpenXR y tiene acceso a los ejemplos, consulte [las características](openxr-supported-features.md) que se admiten actualmente en nuestro complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="d4d77-160">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4d77-161">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d4d77-161">See also</span></span>
* [<span data-ttu-id="d4d77-162">Configurar el proyecto sin MRTK</span><span class="sxs-lookup"><span data-stu-id="d4d77-162">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="d4d77-163">Configuración recomendada para Unity</span><span class="sxs-lookup"><span data-stu-id="d4d77-163">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="d4d77-164">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="d4d77-164">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)