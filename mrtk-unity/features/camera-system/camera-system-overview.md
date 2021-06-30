---
title: Introducción al sistema de cámara
description: Página de aterrizaje del sistema de cámara en MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, cámara,
ms.openlocfilehash: e3b7caacaa9baa67fd81f6d32f3fd8c9f123e66d
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121293"
---
# <a name="camera-system"></a><span data-ttu-id="213c9-104">Sistema de cámara</span><span class="sxs-lookup"><span data-stu-id="213c9-104">Camera system</span></span>

<span data-ttu-id="213c9-105">El sistema de cámara permite que Microsoft Mixed Reality Toolkit configure y optimice la cámara de la aplicación para su uso en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="213c9-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="213c9-106">Con el sistema de cámara, las aplicaciones se pueden escribir para admitir dispositivos opacos (por ejemplo, de realidad virtual) y transparentes (por ejemplo, Microsoft HoloLens) sin necesidad de escribir código para distinguir y adaptarse a cada tipo de pantalla.</span><span class="sxs-lookup"><span data-stu-id="213c9-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="213c9-107">Habilitación del sistema de cámara</span><span class="sxs-lookup"><span data-stu-id="213c9-107">Enabling the camera system</span></span>

<span data-ttu-id="213c9-108">El sistema de cámaras se administra mediante el objeto MixedRealityToolkit (u otro componente registrador de servicios).</span><span class="sxs-lookup"><span data-stu-id="213c9-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="213c9-109">En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="213c9-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="213c9-110">Los pasos necesarios para otros registradores de servicios pueden ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="213c9-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="213c9-111">Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="213c9-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="213c9-113">Vaya al panel Inspector a la sección del sistema de cámara y asegúrese de **que habilitar el sistema de cámara** está activado.</span><span class="sxs-lookup"><span data-stu-id="213c9-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![Habilitación del sistema de cámara](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="213c9-115">Seleccione la implementación del sistema de cámara.</span><span class="sxs-lookup"><span data-stu-id="213c9-115">Select the camera system implementation.</span></span> <span data-ttu-id="213c9-116">La implementación de clase predeterminada proporcionada por MRTK es `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="213c9-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![Selección de la implementación del sistema de cámara](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="213c9-118">Selección del perfil de configuración deseado</span><span class="sxs-lookup"><span data-stu-id="213c9-118">Select the desired configuration profile</span></span>

    ![Selección del perfil del sistema de cámara](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="213c9-120">Configuración del sistema de cámara</span><span class="sxs-lookup"><span data-stu-id="213c9-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="213c9-121">Proveedores de configuración</span><span class="sxs-lookup"><span data-stu-id="213c9-121">Settings providers</span></span>

![Proveedores de configuración de cámara](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="213c9-123">Los proveedores de configuración de cámara habilitan la configuración específica de la plataforma de la cámara.</span><span class="sxs-lookup"><span data-stu-id="213c9-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="213c9-124">Esta configuración puede incluir pasos de configuración personalizados o componentes.</span><span class="sxs-lookup"><span data-stu-id="213c9-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="213c9-125">Los proveedores se pueden agregar haciendo clic en el **botón Agregar proveedor de configuración de** cámara.</span><span class="sxs-lookup"><span data-stu-id="213c9-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="213c9-126">Se pueden quitar haciendo clic en **-** el botón situado a la derecha del nombre del proveedor.</span><span class="sxs-lookup"><span data-stu-id="213c9-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="213c9-127">No todas las plataformas requerirán un proveedor de configuración de cámara.</span><span class="sxs-lookup"><span data-stu-id="213c9-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="213c9-128">Si no hay ningún proveedor que sea compatible con la plataforma en la que se ejecuta la aplicación, Microsoft Mixed Reality Toolkit aplicará los valores predeterminados básicos.</span><span class="sxs-lookup"><span data-stu-id="213c9-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="213c9-129">Configuración de pantalla</span><span class="sxs-lookup"><span data-stu-id="213c9-129">Display settings</span></span>

![Configuración de la pantalla de la cámara](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="213c9-131">La configuración de pantalla se especifica para las pantallas opacas (por ejemplo, virtual) y transparentes (por ejemplo, Microsoft HoloLens).</span><span class="sxs-lookup"><span data-stu-id="213c9-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="213c9-132">La cámara se configura, en tiempo de ejecución, con esta configuración.</span><span class="sxs-lookup"><span data-stu-id="213c9-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="213c9-133">**Near Clip**</span><span class="sxs-lookup"><span data-stu-id="213c9-133">**Near Clip**</span></span>

<span data-ttu-id="213c9-134">El plano de recorte cercano es el más cercano, en metros, que un objeto virtual puede estar en la cámara y seguir representando.</span><span class="sxs-lookup"><span data-stu-id="213c9-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="213c9-135">Para mayor comodidad del usuario, se recomienda que este valor sea mayor que cero.</span><span class="sxs-lookup"><span data-stu-id="213c9-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="213c9-136">La imagen anterior contiene valores que se han encontrado cómodos en diversos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="213c9-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="213c9-137">**Recorte lejano**</span><span class="sxs-lookup"><span data-stu-id="213c9-137">**Far Clip**</span></span>

<span data-ttu-id="213c9-138">El plano de recorte lejano es el más alejado, en metros, que un objeto virtual puede estar en la cámara y seguir representando.</span><span class="sxs-lookup"><span data-stu-id="213c9-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="213c9-139">En el caso de los dispositivos transparentes, se recomienda que este valor sea relativamente cercano a no superar demasiado el espacio real y interrumpir las calidades inmersivas de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="213c9-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="213c9-140">**Borrar marcas**</span><span class="sxs-lookup"><span data-stu-id="213c9-140">**Clear Flags**</span></span>

<span data-ttu-id="213c9-141">El valor clear flags indica cómo se borra la presentación a medida que se dibuja.</span><span class="sxs-lookup"><span data-stu-id="213c9-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="213c9-142">En el caso de las experiencias de realidad virtual, este valor suele establecerse en Skybox.</span><span class="sxs-lookup"><span data-stu-id="213c9-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="213c9-143">En el caso de las pantallas transparentes, se recomienda establecer esta opción en Color.</span><span class="sxs-lookup"><span data-stu-id="213c9-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="213c9-144">**Color de fondo**</span><span class="sxs-lookup"><span data-stu-id="213c9-144">**Background Color**</span></span>

<span data-ttu-id="213c9-145">Si las marcas sin borrar no están establecidas en Skybox, se mostrará la propiedad de color de fondo.</span><span class="sxs-lookup"><span data-stu-id="213c9-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="213c9-146">**Configuración de calidad**</span><span class="sxs-lookup"><span data-stu-id="213c9-146">**Quality Settings**</span></span>

<span data-ttu-id="213c9-147">El valor de configuración de calidad indica la calidad de los gráficos que Unity debe usar al representar la escena.</span><span class="sxs-lookup"><span data-stu-id="213c9-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="213c9-148">El nivel de calidad es una configuración de nivel de proyecto y no es específico de ninguna cámara.</span><span class="sxs-lookup"><span data-stu-id="213c9-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="213c9-149">Para más información, consulte el artículo [Calidad en](https://docs.unity3d.com/Manual/class-QualitySettings.html) la documentación de Unity.</span><span class="sxs-lookup"><span data-stu-id="213c9-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="213c9-150">Consulte también</span><span class="sxs-lookup"><span data-stu-id="213c9-150">See also</span></span>

- [<span data-ttu-id="213c9-151">Documentación de la API del sistema de cámara</span><span class="sxs-lookup"><span data-stu-id="213c9-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="213c9-152">Crear un proveedor de configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="213c9-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
