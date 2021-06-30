---
title: Windows Mixed Reality configuración de la cámara
description: Documentación para usar la Windows Mixed Reality de la cámara en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, cámara,
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121643"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="71198-104">Windows Mixed Reality de configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="71198-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="71198-105">El Windows Mixed Reality configuración de la cámara determina el tipo de dispositivo en el que se ejecuta la aplicación y aplica las opciones de configuración adecuadas en función de la pantalla (transparente u opaca).</span><span class="sxs-lookup"><span data-stu-id="71198-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="71198-106">Habilitación del proveedor Windows Mixed Reality configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="71198-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="71198-107">En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="71198-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="71198-108">Los pasos necesarios para otros registradores de servicios pueden ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="71198-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="71198-109">Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="71198-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="71198-111">Vaya al panel Inspector a la sección sistema de cámara y expanda la **sección Proveedores de configuración de cámara.**</span><span class="sxs-lookup"><span data-stu-id="71198-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Expandir proveedores de configuración](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="71198-113">Haga clic **en Agregar proveedor de configuración de cámara** y expanda la entrada Nueva configuración de cámara **recién** agregada.</span><span class="sxs-lookup"><span data-stu-id="71198-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Expansión del nuevo proveedor de configuración](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="71198-115">Seleccione el proveedor Windows Mixed Reality configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="71198-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![Selección del Windows Mixed Reality configuración de configuración](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="71198-117">Al usar los perfiles predeterminados de Microsoft Mixed Reality Toolkit, el proveedor Windows Mixed Reality configuración de la cámara ya estará habilitado y configurado.</span><span class="sxs-lookup"><span data-stu-id="71198-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="71198-118">Configuración del proveedor de Windows Mixed Reality de configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="71198-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="71198-119">La Windows Mixed Reality configuración de la cámara también admite un perfil.</span><span class="sxs-lookup"><span data-stu-id="71198-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="71198-120">Este perfil proporciona las siguientes opciones:</span><span class="sxs-lookup"><span data-stu-id="71198-120">This profile provides the following options:</span></span>

![Windows Mixed Reality configuración de la cámara](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="71198-122">Representación de la captura de realidad mixta desde la cámara de fotos y vídeos</span><span class="sxs-lookup"><span data-stu-id="71198-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="71198-123">Con esta configuración en HoloLens 2, puede habilitar la alineación de hologramas en las capturas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="71198-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="71198-124">Si está habilitada, la plataforma proporcionará una holographicCamera adicional a la aplicación cuando se toma una foto o un vídeo de captura de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="71198-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="71198-125">HolographicCamera proporciona matrices de vistas correspondientes a la ubicación de la cámara de fotos y vídeos, y proporciona matrices de proyección mediante el campo de vista de la cámara de fotos y vídeos.</span><span class="sxs-lookup"><span data-stu-id="71198-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="71198-126">Esto garantizará que los hologramas, como las mallas de mano, permanezcan visiblemente alineados en la salida del vídeo.</span><span class="sxs-lookup"><span data-stu-id="71198-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="71198-127">HoloLens 2 método de reproducción</span><span class="sxs-lookup"><span data-stu-id="71198-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="71198-128">Establece el método inicial para la HoloLens 2 proyecto.</span><span class="sxs-lookup"><span data-stu-id="71198-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="71198-129">La recomendación predeterminada es usar la reproducción de profundidad, ya que todas las partes de la escena se estabilizarán de forma independiente en función de su distancia con respecto al usuario.</span><span class="sxs-lookup"><span data-stu-id="71198-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="71198-130">Si los hologramas siguen apareciendo inestables, intente asegurarse de que todos los objetos han enviado correctamente su profundidad al búfer de profundidad.</span><span class="sxs-lookup"><span data-stu-id="71198-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="71198-131">A veces se trata de una configuración de sombreador.</span><span class="sxs-lookup"><span data-stu-id="71198-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="71198-132">Si la profundidad parece enviarse correctamente y la inestabilidad sigue estando presente, pruebe la estabilización autoplanar, que usa el búfer de profundidad para calcular un plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="71198-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="71198-133">Si una aplicación no puede enviar datos de profundidad suficientes para que cualquiera de esas opciones se pueda usar, se proporciona una reproducción plana como reserva.</span><span class="sxs-lookup"><span data-stu-id="71198-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="71198-134">Este método se basará en los datos del punto de enfoque proporcionados por una aplicación a través [de SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span><span class="sxs-lookup"><span data-stu-id="71198-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="71198-135">Para actualizar el método de reproyecto en tiempo de ejecución, acceda al `WindowsMixedRealityReprojectionUpdater` siguiente:</span><span class="sxs-lookup"><span data-stu-id="71198-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="71198-136">Esto solo debe actualizarse una vez y el valor se reutiliza para todos los fotogramas posteriores.</span><span class="sxs-lookup"><span data-stu-id="71198-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="71198-137">Si el método se actualizará con frecuencia, se recomienda almacenar en caché el resultado de en `EnsureComponent` lugar de llamarlo a menudo.</span><span class="sxs-lookup"><span data-stu-id="71198-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="71198-138">Consulte también</span><span class="sxs-lookup"><span data-stu-id="71198-138">See also</span></span>

- [<span data-ttu-id="71198-139">Información general del sistema de cámara</span><span class="sxs-lookup"><span data-stu-id="71198-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="71198-140">Crear un proveedor de configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="71198-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="71198-141">Representación Captura de realidad mixta desde la cámara PV</span><span class="sxs-lookup"><span data-stu-id="71198-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="71198-142">Reproducción holográfica</span><span class="sxs-lookup"><span data-stu-id="71198-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)