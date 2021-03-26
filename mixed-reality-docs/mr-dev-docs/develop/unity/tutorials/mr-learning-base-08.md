---
title: Uso del seguimiento ocular
description: En este curso se muestra cómo usar el seguimiento ocular en las aplicaciones de realidad mixta con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, eye-tracking
ms.localizationpriority: high
ms.openlocfilehash: 08793622917ca977c51be56267d8710e5abb78e8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237185"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="64024-104">8. Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="64024-104">8. Using eye-tracking</span></span>

<span data-ttu-id="64024-105">En este tutorial, aprenderá a habilitar el seguimiento ocular para HoloLens 2 y agregará el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.</span><span class="sxs-lookup"><span data-stu-id="64024-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="64024-106">Si también va a implementar este proyecto en HoloLens (primera generación), tenga en cuenta que el seguimiento ocular solo es compatible con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="64024-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="64024-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="64024-107">Objectives</span></span>

* <span data-ttu-id="64024-108">Aprender a habilitar el seguimiento ocular para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="64024-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="64024-109">Aprender a usar el seguimiento ocular para desencadenar la acción</span><span class="sxs-lookup"><span data-stu-id="64024-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="64024-110">Asegurarse de que está habilitada la funcionalidad de entrada de mirada</span><span class="sxs-lookup"><span data-stu-id="64024-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="64024-111">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Eye Gaze Input Capability** (Habilitar funcionalidad de entrada de mirada) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="64024-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="64024-113">La funcionalidad de entrada de mirada con los ojos debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](mr-learning-base-02.md#creating-and-configuring-the-scene) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="64024-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="64024-114">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="64024-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="64024-115">Habilitar la mirada con los ojos en el proveedor de mirada</span><span class="sxs-lookup"><span data-stu-id="64024-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="64024-116">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, seleccione la pestaña MixedRealityToolkit > **Input** (Entrada) y realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="64024-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="64024-117">Clone el perfil **DefaultHoloLens2InputSystemProfile** y asígnele un nombre adecuado; por ejemplo, _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="64024-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="64024-118">Expanda la sección **Punteros**.</span><span class="sxs-lookup"><span data-stu-id="64024-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="64024-119">Clone el perfil **DefaultMixedRealityPointerProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="64024-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="64024-120">Busque la sección **Gaze Settings** (Configuración de mirada) y active la casilla **Is Eye Tracking Enabled** (Está habilitado el seguimiento ocular).</span><span class="sxs-lookup"><span data-stu-id="64024-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Componente MixedRealityToolkit de Unity con los perfiles recién creados aplicados y el seguimiento ocular habilitado](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="64024-122">Para recibir un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="64024-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="64024-123">Habilitar el seguimiento ocular simulado para el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="64024-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="64024-124">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, navegue hasta la pestaña **Entrada** y, a continuación:</span><span class="sxs-lookup"><span data-stu-id="64024-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="64024-125">Expanda la sección **Input Data Providers** (Proveedores de datos de entrada)  > **Input Simulation Service** (Servicio de simulación de entrada).</span><span class="sxs-lookup"><span data-stu-id="64024-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="64024-126">Clone el perfil **DefaultMixedRealityInputSimulationProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="64024-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="64024-127">Busque **Eye Gaze Simulation** (Simulación de mirada) y establezca el valor de **Default Eye Gaze Simulation Mode** (Modo de simulación de mirada predeterminado) en **Camera Forward Axis** (Eje de cámara hacia adelante).</span><span class="sxs-lookup"><span data-stu-id="64024-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity con el objeto TextMeshPro seleccionado](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="64024-129">Agregar seguimiento ocular a los objetos</span><span class="sxs-lookup"><span data-stu-id="64024-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="64024-130">En la ventana Hierarchy (Jerarquía), expanda **RoverExplorer** > **Buttons** y, a continuación, seleccione los tres objetos de botón secundarios:</span><span class="sxs-lookup"><span data-stu-id="64024-130">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Unity con el objeto Button seleccionado](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="64024-132">Con los tres objetos Button todavía seleccionados, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **EyeTrackingTarget** a todos los objetos seleccionados:</span><span class="sxs-lookup"><span data-stu-id="64024-132">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![Unity con el objeto TextMeshPro seleccionado y componentes agregados](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="64024-134">En la ventana Hierarchy (Jerarquía), expanda **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel**  >  **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="64024-134">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="64024-135">Luego, en la ventana Hierarchy (Jerarquía), seleccione el objeto de botón **Hints** (Sugerencias) y configure el componente **EyeTrackingTarget** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="64024-135">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="64024-136">En la sección de eventos **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="64024-136">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="64024-137">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="64024-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="64024-138">Asigne el objeto **TextMeshPro** del botón **Hints** al campo **None (Object)** (Ninguno [Objeto]).</span><span class="sxs-lookup"><span data-stu-id="64024-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="64024-139">En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="64024-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="64024-140">Establezca el argumento en **0,06** para aumentar el tamaño de fuente actual de 0,04 por el 50 %.</span><span class="sxs-lookup"><span data-stu-id="64024-140">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="64024-141">En la sección de eventos **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="64024-141">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="64024-142">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="64024-142">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="64024-143">Asigne el objeto **TextMeshPro** del botón **Hints** al campo **None (Object)** (Ninguno [Objeto]).</span><span class="sxs-lookup"><span data-stu-id="64024-143">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="64024-144">En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="64024-144">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="64024-145">Establezca el argumento en **0,04** para restablecer el tamaño de fuente en 0,04.</span><span class="sxs-lookup"><span data-stu-id="64024-145">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity con el objeto TextMeshPro de Hints seleccionado y el componente EyeTrackingTarget configurado](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="64024-147">**Repita** este paso para el objeto de botón **Explode** (Expandir) y **Reset** (Restablecer) para configurar el seguimiento ocular de los botones restantes.</span><span class="sxs-lookup"><span data-stu-id="64024-147">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="64024-148">Ahora, si entra en el Modo de Juego y, a continuación, mantiene presionado el botón derecho del mouse mientras lo mueve hasta que la mirada entre en contacto con uno de los botones, verá cómo la fuente aumenta su tamaño en un 50 % y se restablece su tamaño original al apartar la mirada:</span><span class="sxs-lookup"><span data-stu-id="64024-148">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![Vista dividida del modo de reproducción de Unity con la mirada que en contacto con la etiqueta del botón Explode del destino de seguimiento ocular](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="64024-150">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="64024-150">Congratulations</span></span>

<span data-ttu-id="64024-151">En este tutorial, aprendió a habilitar el seguimiento ocular para HoloLens 2 y cómo agregar el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.</span><span class="sxs-lookup"><span data-stu-id="64024-151">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="64024-152">Tutorial siguiente: 9. Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="64024-152">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
