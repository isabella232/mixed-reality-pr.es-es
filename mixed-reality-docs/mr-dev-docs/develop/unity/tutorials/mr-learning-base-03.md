---
title: 'Tutoriales de introducción: 3. Configuración de los perfiles de MRTK'
description: En este curso se muestra cómo configurar los perfiles Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, spatial awareness
ms.localizationpriority: high
ms.openlocfilehash: 8a45037f7a73d9e74cd714ae4af49b58f44ce297
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590477"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="33386-105">3. Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="33386-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="33386-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="33386-106">Overview</span></span>

<span data-ttu-id="33386-107">En este tutorial, aprenderá a personalizar y configurar los perfiles de MRTK.</span><span class="sxs-lookup"><span data-stu-id="33386-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="33386-108">Los <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">perfiles de MRTK</a> constituyen un árbol de perfiles anidados que componen la información de configuración sobre cómo se deben inicializar los sistemas y las características de MRTK.</span><span class="sxs-lookup"><span data-stu-id="33386-108">The <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="33386-109">El perfil de nivel superior, el perfil Configuration (Configuración), contiene perfiles anidados para cada uno de los sistemas básicos principales.</span><span class="sxs-lookup"><span data-stu-id="33386-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="33386-110">Cada perfil anidado está diseñado para configurar el comportamiento de su sistema correspondiente.</span><span class="sxs-lookup"><span data-stu-id="33386-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="33386-111">En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="33386-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="33386-112">Puedes seguir estos mismos principios para personalizar cualquier parámetro o valor de los perfiles de MRTK.</span><span class="sxs-lookup"><span data-stu-id="33386-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="33386-113">Como lo visto al implementar el proyecto en HoloLens 2 durante el [tutorial anterior](mr-learning-base-02.md#congratulations), la malla <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness</a> es una colección de mallas que representan la geometría del entorno.</span><span class="sxs-lookup"><span data-stu-id="33386-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="33386-114">Es una visualización útil para ver inicialmente, pero normalmente está desactivada para evitar la distracción visual y el impacto adicional en el rendimiento al tenerla activada.</span><span class="sxs-lookup"><span data-stu-id="33386-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="33386-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="33386-115">Objectives</span></span>

* <span data-ttu-id="33386-116">Obtener información sobre cómo personalizar y configurar los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="33386-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="33386-117">Ocultar la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="33386-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="33386-118">Cambio de la opción de visualización del reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="33386-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="33386-119">Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="33386-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="33386-120">Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="33386-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="33386-121">Habilitar el sistema de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="33386-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="33386-122">Clonar el perfil del sistema de reconocimiento espacial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="33386-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="33386-123">Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="33386-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="33386-124">Cambiar la visibilidad de la malla de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="33386-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="33386-125">De forma predeterminada, los perfiles de MRTK no son editables.</span><span class="sxs-lookup"><span data-stu-id="33386-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="33386-126">Estas son las plantillas de perfil predeterminadas que se deben clonar para poder editarse.</span><span class="sxs-lookup"><span data-stu-id="33386-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="33386-127">Hay varias capas anidadas de perfiles.</span><span class="sxs-lookup"><span data-stu-id="33386-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="33386-128">Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios parámetros.</span><span class="sxs-lookup"><span data-stu-id="33386-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="33386-129">1. Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="33386-129">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="33386-130">El perfil de configuración es el perfil de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="33386-130">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="33386-131">Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="33386-131">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="33386-132">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, cambie el valor del perfil de configuración **MixedRealityToolkit** a **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="33386-132">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit de Unity con DefaultHoloLens2ConfigurationProfile seleccionado](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="33386-134">Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="33386-134">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Botón Copy & Customize (Copiar y personalizar) del componente MixedRealityToolkit de Unity](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="33386-136">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_HoloLens2ConfigurationProfiley_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="33386-136">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Ventana emergente para clonar el perfil de configuración de MixedRealityToolkit de Unity](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="33386-138">El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:</span><span class="sxs-lookup"><span data-stu-id="33386-138">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit de Unity con HoloLens2ConfigurationProfile personalizado recién creado aplicado](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="33386-140">En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="33386-140">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="33386-141">Recuerde guardar el trabajo a lo largo del tutorial.</span><span class="sxs-lookup"><span data-stu-id="33386-141">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="33386-142">2. Habilitar el sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="33386-142">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="33386-143">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):</span><span class="sxs-lookup"><span data-stu-id="33386-143">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit de Unity con el sistema de reconocimiento espacial habilitado](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="33386-145">En el caso de los proyectos futuros, si la aplicación no necesita responder al entorno ni interactuar con él, se recomienda mantener el reconocimiento espacial desactivado para reducir el costo de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="33386-145">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="33386-146">3. Clonar el perfil del sistema de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="33386-146">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="33386-147">En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="33386-147">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit de Unity con la pestaña Spatial Awareness (Reconocimiento espacial) seleccionada](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="33386-149">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="33386-149">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Ventana emergente para clonar el perfil del sistema de reconocimiento espacial de MixedRealityToolkit de Unity](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="33386-151">Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:</span><span class="sxs-lookup"><span data-stu-id="33386-151">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessSystemProfile personalizado recién creado aplicado](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="33386-153">4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="33386-153">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="33386-154">Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expande la sección **Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality) y, a continuación, haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="33386-154">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit de Unity con la sección Windows Mixed Reality Spatial Mesh Observer (Observador de malla espacial de Windows Mixed Reality) expandida](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="33386-156">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="33386-156">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Ventana emergente para clonar el perfil del observador de la malla espacial de MixedRealityToolkit de Unity](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="33386-158">Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:</span><span class="sxs-lookup"><span data-stu-id="33386-158">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessMeshObserverProfile personalizado recién creado aplicado](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="33386-160">5. Cambiar la visibilidad de la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="33386-160">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="33386-161">En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:</span><span class="sxs-lookup"><span data-stu-id="33386-161">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente de MixedRealityToolkit de Unity con Display Option (Opción de visualización) de Spatial Mesh Observer (Observador de malla espacial) establecida en Occlusion (Oclusión)](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="33386-163">Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional.</span><span class="sxs-lookup"><span data-stu-id="33386-163">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="33386-164">Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.</span><span class="sxs-lookup"><span data-stu-id="33386-164">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="33386-165">Acabas de aprender a modificar una configuración en el perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="33386-165">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="33386-166">Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados.</span><span class="sxs-lookup"><span data-stu-id="33386-166">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="33386-167">Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada.</span><span class="sxs-lookup"><span data-stu-id="33386-167">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="33386-168">Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="33386-168">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="33386-169">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="33386-169">Congratulations</span></span>

<span data-ttu-id="33386-170">En este tutorial, aprendió a clonar, personalizar y configurar los perfiles de MRTK y sus opciones.</span><span class="sxs-lookup"><span data-stu-id="33386-170">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="33386-171">Tutorial siguiente: 4. Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="33386-171">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
