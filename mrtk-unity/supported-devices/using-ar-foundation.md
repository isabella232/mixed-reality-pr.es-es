---
title: Uso de AR Foundation
description: Documentación para usar ARFoundation en Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 0f02eb94d95c2900348adaa9e1a02c3e54832a96
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207461"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="2532d-104">Configuración de MRTK para iOS y Android [Experimental]</span><span class="sxs-lookup"><span data-stu-id="2532d-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="2532d-105">Instalación de los paquetes requeridos</span><span class="sxs-lookup"><span data-stu-id="2532d-105">Install required packages</span></span>

1. <span data-ttu-id="2532d-106">Descargue e importe el **paquete Microsoft.MixedReality.Toolkit.Unity.Foundation,** [desde GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o [el](../configuration/usingupm.md) Administrador de paquetes</span><span class="sxs-lookup"><span data-stu-id="2532d-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="2532d-107">En unity Administrador de paquetes (UPM), instale los siguientes paquetes:</span><span class="sxs-lookup"><span data-stu-id="2532d-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="2532d-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="2532d-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="2532d-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="2532d-109">**Android**</span></span> | <span data-ttu-id="2532d-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2532d-110">**iOS**</span></span> | <span data-ttu-id="2532d-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="2532d-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="2532d-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2532d-112">AR Foundation</span></span>  <br/> <span data-ttu-id="2532d-113">Versión: 1.5.0 - versión preliminar 6</span><span class="sxs-lookup"><span data-stu-id="2532d-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="2532d-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2532d-114">AR Foundation</span></span>  <br/> <span data-ttu-id="2532d-115">Versión: 1.5.0 - versión preliminar 6</span><span class="sxs-lookup"><span data-stu-id="2532d-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="2532d-116">Para Unity 2018.4, este paquete se incluye como versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="2532d-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="2532d-117">Para ver el paquete: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="2532d-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="2532d-118">Complemento ARCore XR</span><span class="sxs-lookup"><span data-stu-id="2532d-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2532d-119">Versión: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="2532d-119">Version: 2.1.2</span></span> | <span data-ttu-id="2532d-120">Complemento ARKit XR</span><span class="sxs-lookup"><span data-stu-id="2532d-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2532d-121">Versión: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="2532d-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="2532d-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="2532d-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="2532d-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="2532d-123">**Android**</span></span> | <span data-ttu-id="2532d-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2532d-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="2532d-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2532d-125">AR Foundation</span></span>  <br/> <span data-ttu-id="2532d-126">Versión: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="2532d-126">Version: 2.1.8</span></span> |  <span data-ttu-id="2532d-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2532d-127">AR Foundation</span></span>  <br/> <span data-ttu-id="2532d-128">Versión: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="2532d-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="2532d-129">Complemento ARCore XR</span><span class="sxs-lookup"><span data-stu-id="2532d-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2532d-130">Versión: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="2532d-130">Version: 2.1.11</span></span> | <span data-ttu-id="2532d-131">Complemento XR de ARKit</span><span class="sxs-lookup"><span data-stu-id="2532d-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2532d-132">Versión: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="2532d-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="2532d-133">**Unity 2020.1.x (actualmente no se admite formalmente, se incluye solo con fines informativos)**</span><span class="sxs-lookup"><span data-stu-id="2532d-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="2532d-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="2532d-134">**Android**</span></span> | <span data-ttu-id="2532d-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2532d-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="2532d-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2532d-136">AR Foundation</span></span>  <br/> <span data-ttu-id="2532d-137">Versión: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="2532d-137">Version: 3.1.3</span></span> |  <span data-ttu-id="2532d-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2532d-138">AR Foundation</span></span>  <br/> <span data-ttu-id="2532d-139">Versión: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="2532d-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="2532d-140">Complemento ARCore XR</span><span class="sxs-lookup"><span data-stu-id="2532d-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2532d-141">Versión: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="2532d-141">Version: 3.1.4</span></span> | <span data-ttu-id="2532d-142">Complemento XR de ARKit</span><span class="sxs-lookup"><span data-stu-id="2532d-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2532d-143">Versión: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="2532d-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="2532d-144">Actualice el scripting de UnityAR de MRTK mediante la invocación del elemento de menú: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span><span class="sxs-lookup"><span data-stu-id="2532d-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Actualizar scripting define](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="2532d-146">Habilitación del proveedor de configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="2532d-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="2532d-147">En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="2532d-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="2532d-148">Los pasos necesarios para otros registradores de servicios pueden ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="2532d-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="2532d-149">Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="2532d-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Jerarquía de escena configurada de MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="2532d-151">Seleccione **Copiar y personalizar para** clonar el perfil de MRTK para habilitar la configuración personalizada.</span><span class="sxs-lookup"><span data-stu-id="2532d-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clonación del perfil de MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="2532d-153">Seleccione **Clonar** junto al perfil de cámara.</span><span class="sxs-lookup"><span data-stu-id="2532d-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Clonación del perfil de cámara de MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="2532d-155">Vaya al panel Inspector a la sección del sistema de cámara y expanda la **sección Proveedores de configuración de** cámara.</span><span class="sxs-lookup"><span data-stu-id="2532d-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Expandir proveedores de configuración](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="2532d-157">Haga **clic en Agregar proveedor de configuración de** cámara y expanda la entrada Nueva configuración de cámara **recién** agregada.</span><span class="sxs-lookup"><span data-stu-id="2532d-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Expansión del nuevo proveedor de configuración](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="2532d-159">Selección del proveedor de configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="2532d-159">Select the Unity AR Camera Settings provider</span></span>

    ![Selección del proveedor de configuración de AR de Unity](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="2532d-161">Para obtener más información sobre cómo configurar el proveedor de configuración de la cámara ar de Unity: [Proveedor de configuración de la cámara ar de Unity](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="2532d-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2532d-162">Esta instalación comprueba (cuando se inicia la aplicación) si los componentes de AR Foundation están en la escena.</span><span class="sxs-lookup"><span data-stu-id="2532d-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="2532d-163">Si no es así, se agregan automáticamente para que funcione con ARCore y ARKit.</span><span class="sxs-lookup"><span data-stu-id="2532d-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="2532d-164">Si necesita establecer un comportamiento específico, debe agregar los componentes que necesita por sí mismo.</span><span class="sxs-lookup"><span data-stu-id="2532d-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="2532d-165">Para obtener más información sobre los componentes e instalación de AR Foundation, consulte esta [documentación.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)</span><span class="sxs-lookup"><span data-stu-id="2532d-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="2532d-166">Creación de una escena para dispositivos Android e iOS</span><span class="sxs-lookup"><span data-stu-id="2532d-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="2532d-167">Asegúrese de que ha agregado el proveedor de configuración de cámara UnityAR a la escena.</span><span class="sxs-lookup"><span data-stu-id="2532d-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="2532d-168">Cambie la plataforma a Android o iOS en la configuración de compilación de Unity.</span><span class="sxs-lookup"><span data-stu-id="2532d-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="2532d-169">Asegúrese de que el proveedor de administración del complemento XR asociado está habilitado.</span><span class="sxs-lookup"><span data-stu-id="2532d-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="2532d-170">Administración de complementos XR de iOS:  ![ Administración de complementos XR para iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="2532d-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="2532d-171">Compilación y ejecución de la escena</span><span class="sxs-lookup"><span data-stu-id="2532d-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="2532d-172">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2532d-172">See also</span></span>

- [<span data-ttu-id="2532d-173">Configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="2532d-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
