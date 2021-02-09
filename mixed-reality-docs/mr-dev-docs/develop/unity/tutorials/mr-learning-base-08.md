---
title: Uso del seguimiento ocular
description: En este curso se muestra cómo usar el seguimiento ocular en las aplicaciones de realidad mixta con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, eye-tracking
ms.localizationpriority: high
ms.openlocfilehash: e4104dfd0d7b27425217c8cb92fa36c807053081
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590377"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="eb49f-104">8. Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="eb49f-104">8. Using eye-tracking</span></span>

<span data-ttu-id="eb49f-105">En este tutorial, aprenderá a habilitar el seguimiento ocular para HoloLens 2 y agregará el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.</span><span class="sxs-lookup"><span data-stu-id="eb49f-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="eb49f-106">Si también va a implementar este proyecto en HoloLens (primera generación), tenga en cuenta que el seguimiento ocular solo es compatible con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="eb49f-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="eb49f-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="eb49f-107">Objectives</span></span>

* <span data-ttu-id="eb49f-108">Aprender a habilitar el seguimiento ocular para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="eb49f-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="eb49f-109">Aprender a usar el seguimiento ocular para desencadenar la acción</span><span class="sxs-lookup"><span data-stu-id="eb49f-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="eb49f-110">Asegurarse de que está habilitada la funcionalidad de entrada de mirada</span><span class="sxs-lookup"><span data-stu-id="eb49f-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="eb49f-111">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Eye Gaze Input Capability** (Habilitar funcionalidad de entrada de mirada) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="eb49f-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="eb49f-113">La funcionalidad de entrada de mirada con los ojos debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](mr-learning-base-02.md#creating-and-configuring-the-scene) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="eb49f-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="eb49f-114">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="eb49f-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="eb49f-115">Habilitar la mirada con los ojos en el proveedor de mirada</span><span class="sxs-lookup"><span data-stu-id="eb49f-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="eb49f-116">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, seleccione la pestaña MixedRealityToolkit > **Input** (Entrada) y realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="eb49f-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="eb49f-117">Clone el perfil **DefaultHoloLens2InputSystemProfile** y asígnele un nombre adecuado; por ejemplo, _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="eb49f-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="eb49f-118">Expanda la sección **Punteros**.</span><span class="sxs-lookup"><span data-stu-id="eb49f-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="eb49f-119">Clone el perfil **DefaultMixedRealityPointerProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="eb49f-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="eb49f-120">Busque la sección **Gaze Settings** (Configuración de mirada) y active la casilla **Is Eye Tracking Enabled** (Está habilitado el seguimiento ocular).</span><span class="sxs-lookup"><span data-stu-id="eb49f-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Componente MixedRealityToolkit de Unity con los perfiles recién creados aplicados y el seguimiento ocular habilitado](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="eb49f-122">Para recibir un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="eb49f-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="eb49f-123">Habilitar el seguimiento ocular simulado para el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="eb49f-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="eb49f-124">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, navegue hasta la pestaña **Entrada** y, a continuación:</span><span class="sxs-lookup"><span data-stu-id="eb49f-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="eb49f-125">Expanda la sección **Input Data Providers** (Proveedores de datos de entrada)  > **Input Simulation Service** (Servicio de simulación de entrada).</span><span class="sxs-lookup"><span data-stu-id="eb49f-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="eb49f-126">Clone el perfil **DefaultMixedRealityInputSimulationProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="eb49f-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="eb49f-127">Busque **Eye Gaze Simulation** (Simulación de mirada) y establezca el valor de **Default Eye Gaze Simulation Mode** (Modo de simulación de mirada predeterminado) en **Camera Forward Axis** (Eje de cámara hacia adelante).</span><span class="sxs-lookup"><span data-stu-id="eb49f-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity con el objeto TextMeshPro seleccionado](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="eb49f-129">Agregar seguimiento ocular a los objetos</span><span class="sxs-lookup"><span data-stu-id="eb49f-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="eb49f-130">En la ventana Jerarquía, expanda el objeto RoverExplorer > **Botones** y, a continuación, para cada uno de los tres objetos de botón secundarios, expanda y seleccione el objeto SeeItSayItLabel > **TextMeshPro**:</span><span class="sxs-lookup"><span data-stu-id="eb49f-130">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![Unity con el objeto TextMeshPro seleccionado](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="eb49f-132">Con los tres objetos TextMeshPro todavía seleccionados, en la ventana Inspector, use el botón **Agregar componente** para agregar los siguientes componentes a todos los objetos seleccionados:</span><span class="sxs-lookup"><span data-stu-id="eb49f-132">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="eb49f-133">Componente **Colisionador de cuadro**</span><span class="sxs-lookup"><span data-stu-id="eb49f-133">**Box Collider** component</span></span>
* <span data-ttu-id="eb49f-134">Componente **EyeTrackingTarget**</span><span class="sxs-lookup"><span data-stu-id="eb49f-134">**EyeTrackingTarget** component</span></span>

![Unity con el objeto TextMeshPro seleccionado y componentes agregados](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="eb49f-136">En la ventana Jerarquía, seleccione el objeto **Hints** (Sugerencias) > SeeItSayItLabel > **TextMeshPro** y, a continuación, configure el componente **EyeTrackingTarget** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="eb49f-136">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="eb49f-137">En la sección de eventos **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="eb49f-137">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="eb49f-138">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="eb49f-138">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="eb49f-139">Asigne el propio objeto, es decir, el mismo objeto **TextMeshPro**, al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="eb49f-139">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="eb49f-140">En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="eb49f-140">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="eb49f-141">Establezca el argumento en **0,06** para aumentar el tamaño de fuente actual de 0,04 por el 50 %.</span><span class="sxs-lookup"><span data-stu-id="eb49f-141">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="eb49f-142">En la sección de eventos **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="eb49f-142">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="eb49f-143">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="eb49f-143">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="eb49f-144">Asigne el propio objeto, es decir, el mismo objeto **TextMeshPro**, al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="eb49f-144">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="eb49f-145">En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="eb49f-145">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="eb49f-146">Establezca el argumento en **0,04** para restablecer el tamaño de fuente en 0,04.</span><span class="sxs-lookup"><span data-stu-id="eb49f-146">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity con el objeto TextMeshPro de Hints seleccionado y el componente EyeTrackingTarget configurado](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="eb49f-148">**Repita** este paso para los objetos **Explode** (Explosión) > SeeItSayItLabel > **TextMeshPro** y **Reset** (Restablecer) > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="eb49f-148">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="eb49f-149">Ahora, si entra en el Modo de Juego y, a continuación, mantiene presionado el botón secundario del mouse mientras lo mueve hasta que la mirada entre en contacto con una de las etiquetas, verá cómo la fuente aumenta su tamaño en un 50 % y se restablece su tamaño original al apartar la mirada:</span><span class="sxs-lookup"><span data-stu-id="eb49f-149">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![Vista dividida del modo de reproducción de Unity con la mirada que en contacto con la etiqueta del botón Explode del destino de seguimiento ocular](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="eb49f-151">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="eb49f-151">Congratulations</span></span>

<span data-ttu-id="eb49f-152">En este tutorial, aprendió a habilitar el seguimiento ocular para HoloLens 2 y cómo agregar el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.</span><span class="sxs-lookup"><span data-stu-id="eb49f-152">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eb49f-153">Tutorial siguiente: 9. Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="eb49f-153">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
