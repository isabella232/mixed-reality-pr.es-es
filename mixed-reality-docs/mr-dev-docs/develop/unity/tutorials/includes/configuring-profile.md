---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097821"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="5f8a6-101">Complemento XR para Unity 2019/2020 y Windows</span><span class="sxs-lookup"><span data-stu-id="5f8a6-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="5f8a6-102">1. Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="5f8a6-103">El perfil de configuración es el perfil de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="5f8a6-104">Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="5f8a6-105">En la ventana Hierarchy (Jerarquía), seleccione el objeto **MixedRealityToolkit**. Después, en la ventana Inspector, compruebe que el perfil de configuración de **MixedRealityToolkit** esté definido como **DefaultXRSDKConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit de Unity con DefaultHoloLens2ConfigurationProfile seleccionado](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="5f8a6-107">Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Botón Copy & Customize (Copiar y personalizar) del componente MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="5f8a6-109">En la ventana Clone Profile (Clonar perfil), escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_XRSDKConfigurationProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultXRSDKConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Ventana emergente para clonar el perfil de configuración de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="5f8a6-111">El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit de Unity con HoloLens2ConfigurationProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="5f8a6-113">En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="5f8a6-114">Recuerde guardar el trabajo a lo largo del tutorial.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="5f8a6-115">2. Habilitar el sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="5f8a6-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="5f8a6-116">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit de Unity con el sistema de reconocimiento espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="5f8a6-118">En el caso de los proyectos futuros, si la aplicación no necesita responder al entorno ni interactuar con él, se recomienda mantener el reconocimiento espacial desactivado para reducir el costo de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="5f8a6-119">3. Clonar el perfil del sistema de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="5f8a6-120">En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit de Unity con la pestaña Spatial Awareness (Reconocimiento espacial) seleccionada](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="5f8a6-122">En la ventana Clone Profile (Clonar perfil), escriba un valor de **Profile Name** (Nombre de perfil) adecuado; por ejemplo, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Ventana emergente para clonar el perfil del sistema de reconocimiento espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="5f8a6-124">Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessSystemProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="5f8a6-126">4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="5f8a6-127">Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expanda la sección **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality del SDK de XR) y, a continuación, haga clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit de Unity con la sección Windows Mixed Reality Spatial Mesh Observer (Observador de malla espacial de Windows Mixed Reality) expandida](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="5f8a6-129">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Ventana emergente para clonar el perfil del observador de la malla espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="5f8a6-131">Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessMeshObserverProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="5f8a6-133">5. Cambiar la visibilidad de la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="5f8a6-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="5f8a6-134">En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente de MixedRealityToolkit de Unity con Display Option (Opción de visualización) de Spatial Mesh Observer (Observador de malla espacial) establecida en Occlusion (Oclusión)](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="5f8a6-136">Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="5f8a6-137">Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="5f8a6-138">Acabas de aprender a modificar una configuración en el perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="5f8a6-139">Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="5f8a6-140">Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="5f8a6-141">Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) en el [portal de documentación de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="5f8a6-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="5f8a6-142">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="5f8a6-142">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="5f8a6-143">1. Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="5f8a6-144">El perfil de configuración es el perfil de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="5f8a6-145">Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="5f8a6-146">En la ventana Hierarchy (Jerarquía), seleccione el objeto **MixedRealityToolkit**. Después, en la ventana Inspector, compruebe que el perfil de configuración de **MixedRealityToolkit** esté definido como **DefaultOpenXRConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultOpenXRConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit de Unity con el perfil de OpenXR predeterminado seleccionado](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

<span data-ttu-id="5f8a6-148">Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Botón Copy & Customize (Copiar y personalizar) del componente MixedRealityToolkit de Unity para el perfil de OpenXR](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

<span data-ttu-id="5f8a6-150">En la ventana Clone Profile (Clonar perfil), escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_OpenXRConfigurationProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultOpenXRConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_OpenXRConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultOpenXRConfigurationProfile**:</span></span>

![Ventana emergente para clonar el perfil de configuración de MixedRealityToolkit de Unity para el perfil de OpenXR](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

<span data-ttu-id="5f8a6-152">El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit de Unity con OpenXR personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

<span data-ttu-id="5f8a6-154">En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="5f8a6-155">Recuerde guardar el trabajo a lo largo del tutorial.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="5f8a6-156">2. Habilitar el sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="5f8a6-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="5f8a6-157">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit de Unity con el sistema de reconocimiento espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="5f8a6-159">En el caso de los proyectos futuros, si la aplicación no necesita responder al entorno ni interactuar con él, se recomienda mantener el reconocimiento espacial desactivado para reducir el costo de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="5f8a6-160">3. Clonar el perfil del sistema de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="5f8a6-161">En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit de Unity con la pestaña Spatial Awareness (Reconocimiento espacial) seleccionada](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="5f8a6-163">En la ventana Clone Profile (Clonar perfil), escriba un valor de **Profile Name** (Nombre de perfil) adecuado; por ejemplo, GettingStarted_OpenXRSpatialAwarenessSystemProfile. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, GettingStarted_OpenXRSpatialAwarenessSystemProfile, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Ventana emergente para clonar el perfil del sistema de reconocimiento espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="5f8a6-165">Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessSystemProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="5f8a6-167">4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="5f8a6-168">Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expanda la sección **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality del SDK de XR) y, a continuación, haga clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-168">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit de Unity con la sección Windows Mixed Reality Spatial Mesh Observer (Observador de malla espacial de Windows Mixed Reality) expandida](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="5f8a6-170">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Ventana emergente para clonar el perfil del observador de la malla espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="5f8a6-172">Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessMeshObserverProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="5f8a6-174">5. Cambiar la visibilidad de la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="5f8a6-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="5f8a6-175">En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente de MixedRealityToolkit de Unity con Display Option (Opción de visualización) de Spatial Mesh Observer (Observador de malla espacial) establecida en Occlusion (Oclusión)](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="5f8a6-177">Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="5f8a6-178">Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="5f8a6-179">Acabas de aprender a modificar una configuración en el perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="5f8a6-180">Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="5f8a6-181">Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="5f8a6-182">Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) en el [portal de documentación de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="5f8a6-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="5f8a6-183">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-183">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="5f8a6-184">1. Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-184">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="5f8a6-185">El perfil de configuración es el perfil de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-185">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="5f8a6-186">Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-186">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="5f8a6-187">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, cambie el valor del perfil de configuración **MixedRealityToolkit** a **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-187">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit de Unity con DefaultHoloLens2ConfigurationProfile seleccionado](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="5f8a6-189">Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-189">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Botón Copy & Customize (Copiar y personalizar) del componente MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="5f8a6-191">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_HoloLens2ConfigurationProfiley_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-191">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Ventana emergente para clonar el perfil de configuración de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="5f8a6-193">El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-193">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit de Unity con HoloLens2ConfigurationProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="5f8a6-195">En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-195">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="5f8a6-196">Recuerde guardar el trabajo a lo largo del tutorial.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-196">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="5f8a6-197">2. Habilitar el sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="5f8a6-197">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="5f8a6-198">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-198">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit de Unity con el sistema de reconocimiento espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="5f8a6-200">En el caso de los proyectos futuros, si la aplicación no necesita responder al entorno ni interactuar con él, se recomienda mantener el reconocimiento espacial desactivado para reducir el costo de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-200">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="5f8a6-201">3. Clonar el perfil del sistema de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-201">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="5f8a6-202">En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-202">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit de Unity con la pestaña Spatial Awareness (Reconocimiento espacial) seleccionada](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="5f8a6-204">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-204">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Ventana emergente para clonar el perfil del sistema de reconocimiento espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="5f8a6-206">Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-206">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessSystemProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="5f8a6-208">4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="5f8a6-208">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="5f8a6-209">Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expande la sección **Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality) y, a continuación, haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="5f8a6-209">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit de Unity con la sección Windows Mixed Reality Spatial Mesh Observer (Observador de malla espacial de Windows Mixed Reality) expandida](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="5f8a6-211">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-211">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Ventana emergente para clonar el perfil del observador de la malla espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="5f8a6-213">Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-213">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessMeshObserverProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="5f8a6-215">5. Cambiar la visibilidad de la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="5f8a6-215">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="5f8a6-216">En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:</span><span class="sxs-lookup"><span data-stu-id="5f8a6-216">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente de MixedRealityToolkit de Unity con Display Option (Opción de visualización) de Spatial Mesh Observer (Observador de malla espacial) establecida en Occlusion (Oclusión)](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="5f8a6-218">Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-218">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="5f8a6-219">Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-219">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="5f8a6-220">Acabas de aprender a modificar una configuración en el perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-220">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="5f8a6-221">Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-221">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="5f8a6-222">Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5f8a6-222">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="5f8a6-223">Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) en el [portal de documentación de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="5f8a6-223">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>
