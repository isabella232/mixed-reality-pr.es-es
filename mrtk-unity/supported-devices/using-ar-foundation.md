---
title: Uso de AR Foundation
description: Documentación para usar ARFoundation en Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, AR Core, AR Kit
ms.openlocfilehash: 1c39950e8b64968e182ddc551ef344dee42060e9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143940"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="a9ab4-104">Configuración de MRTK para iOS y Android [Experimental]</span><span class="sxs-lookup"><span data-stu-id="a9ab4-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="a9ab4-105">Instalación de los paquetes requeridos</span><span class="sxs-lookup"><span data-stu-id="a9ab4-105">Install required packages</span></span>

1. <span data-ttu-id="a9ab4-106">Descargue e importe el **paquete Microsoft.MixedReality.Toolkit.Unity.Foundation,** [desde GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o [el](../configuration/usingupm.md) Administrador de paquetes</span><span class="sxs-lookup"><span data-stu-id="a9ab4-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="a9ab4-107">En unity Administrador de paquetes (UPM), instale los siguientes paquetes:</span><span class="sxs-lookup"><span data-stu-id="a9ab4-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="a9ab4-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="a9ab4-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-109">**Android**</span></span> | <span data-ttu-id="a9ab4-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-110">**iOS**</span></span> | <span data-ttu-id="a9ab4-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="a9ab4-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="a9ab4-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="a9ab4-112">AR Foundation</span></span>  <br/> <span data-ttu-id="a9ab4-113">Versión: 1.5.0 - versión preliminar 6</span><span class="sxs-lookup"><span data-stu-id="a9ab4-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="a9ab4-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="a9ab4-114">AR Foundation</span></span>  <br/> <span data-ttu-id="a9ab4-115">Versión: 1.5.0 - versión preliminar 6</span><span class="sxs-lookup"><span data-stu-id="a9ab4-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="a9ab4-116">Para Unity 2018.4, este paquete se incluye como versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="a9ab4-117">Para ver el paquete: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="a9ab4-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="a9ab4-118">Complemento ARCore XR</span><span class="sxs-lookup"><span data-stu-id="a9ab4-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a9ab4-119">Versión: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="a9ab4-119">Version: 2.1.2</span></span> | <span data-ttu-id="a9ab4-120">Complemento ARKit XR</span><span class="sxs-lookup"><span data-stu-id="a9ab4-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a9ab4-121">Versión: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="a9ab4-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="a9ab4-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="a9ab4-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-123">**Android**</span></span> | <span data-ttu-id="a9ab4-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="a9ab4-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="a9ab4-125">AR Foundation</span></span>  <br/> <span data-ttu-id="a9ab4-126">Versión: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="a9ab4-126">Version: 2.1.8</span></span> |  <span data-ttu-id="a9ab4-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="a9ab4-127">AR Foundation</span></span>  <br/> <span data-ttu-id="a9ab4-128">Versión: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="a9ab4-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="a9ab4-129">Complemento ARCore XR</span><span class="sxs-lookup"><span data-stu-id="a9ab4-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a9ab4-130">Versión: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="a9ab4-130">Version: 2.1.11</span></span> | <span data-ttu-id="a9ab4-131">Complemento XR de ARKit</span><span class="sxs-lookup"><span data-stu-id="a9ab4-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a9ab4-132">Versión: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="a9ab4-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="a9ab4-133">**Unity 2020.1.x (actualmente no se admite formalmente, se incluye solo con fines informativos)**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="a9ab4-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-134">**Android**</span></span> | <span data-ttu-id="a9ab4-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="a9ab4-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="a9ab4-136">AR Foundation</span></span>  <br/> <span data-ttu-id="a9ab4-137">Versión: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="a9ab4-137">Version: 3.1.3</span></span> |  <span data-ttu-id="a9ab4-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="a9ab4-138">AR Foundation</span></span>  <br/> <span data-ttu-id="a9ab4-139">Versión: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="a9ab4-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="a9ab4-140">Complemento ARCore XR</span><span class="sxs-lookup"><span data-stu-id="a9ab4-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a9ab4-141">Versión: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="a9ab4-141">Version: 3.1.4</span></span> | <span data-ttu-id="a9ab4-142">Complemento XR de ARKit</span><span class="sxs-lookup"><span data-stu-id="a9ab4-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a9ab4-143">Versión: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="a9ab4-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="a9ab4-144">Actualice el scripting de UnityAR de MRTK invocando el elemento de menú: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span><span class="sxs-lookup"><span data-stu-id="a9ab4-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="a9ab4-145">Habilitación del proveedor de configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="a9ab4-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="a9ab4-146">En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="a9ab4-147">Los pasos necesarios para otros registradores de servicios pueden ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="a9ab4-148">Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Jerarquía de escena configurada de MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="a9ab4-150">Seleccione **Copiar y personalizar para** clonar el perfil de MRTK para habilitar la configuración personalizada.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clonación del perfil de MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="a9ab4-152">Seleccione **Clonar** junto al perfil de cámara.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Clonación del perfil de cámara de MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="a9ab4-154">Vaya al panel Inspector a la sección del sistema de cámara y expanda la **sección Proveedores de configuración de** cámara.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Expandir proveedores de configuración](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="a9ab4-156">Haga **clic en Agregar proveedor de configuración de** cámara y expanda la entrada Nueva configuración de cámara **recién** agregada.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Expansión del nuevo proveedor de configuración](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="a9ab4-158">Selección del proveedor de configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="a9ab4-158">Select the Unity AR Camera Settings provider</span></span>

    ![Selección del proveedor de configuración de AR de Unity](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="a9ab4-160">Para obtener más información sobre cómo configurar el proveedor de configuración de la cámara ar de Unity: [Proveedor de configuración de la cámara ar de Unity](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a9ab4-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a9ab4-161">Esta instalación comprueba (cuando se inicia la aplicación) si los componentes de AR Foundation están en la escena.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="a9ab4-162">Si no es así, se agregan automáticamente para que funcione con ARCore y ARKit.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="a9ab4-163">Si necesita establecer un comportamiento específico, debe agregar los componentes que necesita por sí mismo.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="a9ab4-164">Para obtener más información sobre los componentes e instalación de AR Foundation, consulte esta [documentación.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)</span><span class="sxs-lookup"><span data-stu-id="a9ab4-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="a9ab4-165">Creación de una escena para dispositivos Android e iOS</span><span class="sxs-lookup"><span data-stu-id="a9ab4-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="a9ab4-166">Asegúrese de que ha agregado el proveedor de configuración de cámara UnityAR a la escena.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="a9ab4-167">Cambie la plataforma a Android o iOS en la configuración de compilación de Unity.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="a9ab4-168">Al cambiar la plataforma, debería ver la ventana del configurador de proyectos de MRTK con la configuración de la plataforma elegida.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="a9ab4-169">Haga clic en Aplicar para habilitar la configuración específica de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="a9ab4-170">Configuración del configurador de proyectos de iOS</span><span class="sxs-lookup"><span data-stu-id="a9ab4-170">iOS Project Configurator Settings</span></span>

    ![Configurador de proyectos de iOS](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="a9ab4-172">No hay ningún paso adicional después de cambiar la plataforma para Android.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="a9ab4-173">Si la plataforma es iOS, Edit > Project Settings > Player > Other Settings (Editar la configuración del proyecto de > Player) > Other Settings (Otra configuración), en el encabezado **Optimización,** desactive Strip Engine Code (Quitar código del motor).</span><span class="sxs-lookup"><span data-stu-id="a9ab4-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Configuración de iOS](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="a9ab4-175">Desactivar el código del motor de banda es la solución a corto plazo a un error en Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="a9ab4-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="a9ab4-176">Estamos trabajando en una solución a largo plazo.</span><span class="sxs-lookup"><span data-stu-id="a9ab4-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="a9ab4-177">Compilación y ejecución de la escena</span><span class="sxs-lookup"><span data-stu-id="a9ab4-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="a9ab4-178">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9ab4-178">See also</span></span>

- [<span data-ttu-id="a9ab4-179">Configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="a9ab4-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
