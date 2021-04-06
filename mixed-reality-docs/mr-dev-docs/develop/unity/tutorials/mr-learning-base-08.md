---
title: Uso del seguimiento ocular
description: En este curso se muestra cómo usar el seguimiento ocular en las aplicaciones de realidad mixta con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, eye-tracking
ms.localizationpriority: high
ms.openlocfilehash: bf7bd266eb471193979c588d97d14dd37aed175e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982905"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="c63a2-104">8. Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="c63a2-104">8. Using eye-tracking</span></span>

<span data-ttu-id="c63a2-105">En este tutorial, aprenderá a habilitar el seguimiento ocular para HoloLens 2 y agregará el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.</span><span class="sxs-lookup"><span data-stu-id="c63a2-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="c63a2-106">Si también va a implementar este proyecto en HoloLens (primera generación), tenga en cuenta que el seguimiento ocular solo es compatible con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c63a2-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="c63a2-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c63a2-107">Objectives</span></span>

* <span data-ttu-id="c63a2-108">Aprender a habilitar el seguimiento ocular para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c63a2-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="c63a2-109">Aprender a usar el seguimiento ocular para desencadenar la acción</span><span class="sxs-lookup"><span data-stu-id="c63a2-109">Learn how to use eye-tracking to trigger action</span></span>

[!INCLUDE[](includes/ensuring-eye-gaze-capabality.md)]

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="c63a2-110">Habilitar la mirada con los ojos en el proveedor de mirada</span><span class="sxs-lookup"><span data-stu-id="c63a2-110">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="c63a2-111">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, seleccione la pestaña MixedRealityToolkit > **Input** (Entrada) y realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="c63a2-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="c63a2-112">Clone el perfil **DefaultHoloLens2InputSystemProfile** y asígnele un nombre adecuado; por ejemplo, _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="c63a2-112">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="c63a2-113">Expanda la sección **Punteros**.</span><span class="sxs-lookup"><span data-stu-id="c63a2-113">Expand the **Pointers** section</span></span>
* <span data-ttu-id="c63a2-114">Clone el perfil **DefaultMixedRealityPointerProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="c63a2-114">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="c63a2-115">Busque la sección **Gaze Settings** (Configuración de mirada) y active la casilla **Is Eye Tracking Enabled** (Está habilitado el seguimiento ocular).</span><span class="sxs-lookup"><span data-stu-id="c63a2-115">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Componente MixedRealityToolkit de Unity con los perfiles recién creados aplicados y el seguimiento ocular habilitado](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="c63a2-117">Para recibir un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="c63a2-117">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="c63a2-118">Habilitar el seguimiento ocular simulado para el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="c63a2-118">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="c63a2-119">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, navegue hasta la pestaña **Entrada** y, a continuación:</span><span class="sxs-lookup"><span data-stu-id="c63a2-119">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="c63a2-120">Expanda la sección **Input Data Providers** (Proveedores de datos de entrada)  > **Input Simulation Service** (Servicio de simulación de entrada).</span><span class="sxs-lookup"><span data-stu-id="c63a2-120">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="c63a2-121">Clone el perfil **DefaultMixedRealityInputSimulationProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="c63a2-121">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="c63a2-122">Busque **Eye Gaze Simulation** (Simulación de mirada) y establezca el valor de **Default Eye Gaze Simulation Mode** (Modo de simulación de mirada predeterminado) en **Camera Forward Axis** (Eje de cámara hacia adelante).</span><span class="sxs-lookup"><span data-stu-id="c63a2-122">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity con el objeto TextMeshPro seleccionado](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="c63a2-124">Agregar seguimiento ocular a los objetos</span><span class="sxs-lookup"><span data-stu-id="c63a2-124">Adding eye-tracking to objects</span></span>

<span data-ttu-id="c63a2-125">En la ventana Hierarchy (Jerarquía), expanda **RoverExplorer** > **Buttons** y, a continuación, seleccione los tres objetos de botón secundarios:</span><span class="sxs-lookup"><span data-stu-id="c63a2-125">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Unity con el objeto Button seleccionado](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="c63a2-127">Con los tres objetos Button todavía seleccionados, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **EyeTrackingTarget** a todos los objetos seleccionados:</span><span class="sxs-lookup"><span data-stu-id="c63a2-127">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![Unity con el objeto TextMeshPro seleccionado y componentes agregados](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="c63a2-129">En la ventana Hierarchy (Jerarquía), expanda **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel**  >  **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="c63a2-129">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="c63a2-130">Luego, en la ventana Hierarchy (Jerarquía), seleccione el objeto de botón **Hints** (Sugerencias) y configure el componente **EyeTrackingTarget** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="c63a2-130">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="c63a2-131">En la sección de eventos **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="c63a2-131">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="c63a2-132">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="c63a2-132">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="c63a2-133">Asigne el objeto **TextMeshPro** del botón **Hints** al campo **None (Object)** (Ninguno [Objeto]).</span><span class="sxs-lookup"><span data-stu-id="c63a2-133">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="c63a2-134">En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="c63a2-134">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="c63a2-135">Establezca el argumento en **0,06** para aumentar el tamaño de fuente actual de 0,04 por el 50 %.</span><span class="sxs-lookup"><span data-stu-id="c63a2-135">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="c63a2-136">En la sección de eventos **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="c63a2-136">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="c63a2-137">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="c63a2-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="c63a2-138">Asigne el objeto **TextMeshPro** del botón **Hints** al campo **None (Object)** (Ninguno [Objeto]).</span><span class="sxs-lookup"><span data-stu-id="c63a2-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="c63a2-139">En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="c63a2-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="c63a2-140">Establezca el argumento en **0,04** para restablecer el tamaño de fuente en 0,04.</span><span class="sxs-lookup"><span data-stu-id="c63a2-140">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity con el objeto TextMeshPro de Hints seleccionado y el componente EyeTrackingTarget configurado](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="c63a2-142">**Repita** este paso para el objeto de botón **Explode** (Expandir) y **Reset** (Restablecer) para configurar el seguimiento ocular de los botones restantes.</span><span class="sxs-lookup"><span data-stu-id="c63a2-142">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="c63a2-143">Ahora, si entra en el Modo de Juego y, a continuación, mantiene presionado el botón derecho del mouse mientras lo mueve hasta que la mirada entre en contacto con uno de los botones, verá cómo la fuente aumenta su tamaño en un 50 % y se restablece su tamaño original al apartar la mirada:</span><span class="sxs-lookup"><span data-stu-id="c63a2-143">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![Vista dividida del modo de reproducción de Unity con la mirada que en contacto con la etiqueta del botón Explode del destino de seguimiento ocular](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="c63a2-145">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="c63a2-145">Congratulations</span></span>

<span data-ttu-id="c63a2-146">En este tutorial, aprendió a habilitar el seguimiento ocular para HoloLens 2 y cómo agregar el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.</span><span class="sxs-lookup"><span data-stu-id="c63a2-146">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c63a2-147">Tutorial siguiente: 9. Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="c63a2-147">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
