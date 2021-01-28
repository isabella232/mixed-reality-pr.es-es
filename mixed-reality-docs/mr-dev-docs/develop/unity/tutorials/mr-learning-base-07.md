---
title: Interacción con objetos 3D
description: En este curso se muestra cómo usar Mixed Reality Toolkit (MRTK) para interactuar con objetos 3D y manipularlos en aplicaciones de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, object interactions, bounding boxes
ms.localizationpriority: high
ms.openlocfilehash: 23cfe3d3746d6ab6dbc0757f32b95ddc8637a366
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578763"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="e7f6f-104">7. Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="e7f6f-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="e7f6f-105">En este tutorial, aprenderá a habilitar la manipulación cercana y lejana de objetos 3D y a limitar los tipos de manipulación permitidos.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="e7f6f-106">También aprenderá a agregar controles de límites alrededor de objetos 3D para facilitar el control de la manipulación de objetos.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-106">You will also learn how to add bounds control around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="e7f6f-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e7f6f-107">Objectives</span></span>

* <span data-ttu-id="e7f6f-108">Aprender a configurar objetos 3D para poder interactuar con ellos</span><span class="sxs-lookup"><span data-stu-id="e7f6f-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="e7f6f-109">Aprender a agregar un control de límites a objetos 3D</span><span class="sxs-lookup"><span data-stu-id="e7f6f-109">Learn how to add bounds control to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="e7f6f-110">Manipulación de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="e7f6f-110">Manipulating 3D objects</span></span>

<span data-ttu-id="e7f6f-111">En esta sección, agregará la capacidad de manipular todas las partes del róver que organizó en la tabla durante el tutorial [Posicionamiento de los objetos en la escena](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="e7f6f-112">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e7f6f-113">Agregar el componente Object Manipulator (Script) (Manipulador de objetos [script]) a todos los objetos de las partes</span><span class="sxs-lookup"><span data-stu-id="e7f6f-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="e7f6f-114">Agregar el componente NearInteractionGrabbable a todos los objetos de las partes</span><span class="sxs-lookup"><span data-stu-id="e7f6f-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="e7f6f-115">Configurar el componente Object Manipulator (Script) (Manipulador de objetos [script])</span><span class="sxs-lookup"><span data-stu-id="e7f6f-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="e7f6f-116">Para poder **manipular un objeto**, el objeto debe tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="e7f6f-117">Componente **Collider**; por ejemplo, un colisionador de cuadro</span><span class="sxs-lookup"><span data-stu-id="e7f6f-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="e7f6f-118">Componente **Object Manipulator (Script)** (Manipulador de objetos [script])</span><span class="sxs-lookup"><span data-stu-id="e7f6f-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="e7f6f-119">Para poder **manipular** y **agarrar un objeto con seguimiento de manos**, el objeto debe tener los componentes siguientes:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="e7f6f-120">Componente **Collider**; por ejemplo, un colisionador de cuadro</span><span class="sxs-lookup"><span data-stu-id="e7f6f-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="e7f6f-121">Componente **Object Manipulator (Script)** (Manipulador de objetos [script])</span><span class="sxs-lookup"><span data-stu-id="e7f6f-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="e7f6f-122">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="e7f6f-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="e7f6f-123">Además, configurará el explorador del róver a fin de poder colocarle las partes y crear un ensamblado completo.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="e7f6f-124">En la ventana Hierarchy (Jerarquía), expanda el objeto RoverExplorer > **RoverParts** y seleccione todos los objetos secundarios de la parte, así como el objeto **RoverAssembly**, y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar los siguientes componentes a todos los objetos seleccionados:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="e7f6f-125">Componente **Object Manipulator (Script)** (Manipulador de objetos [script])</span><span class="sxs-lookup"><span data-stu-id="e7f6f-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="e7f6f-126">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="e7f6f-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="e7f6f-127">Componente **Part Assembly Controller (Script)** (Controlador de ensamblado de partes [script])</span><span class="sxs-lookup"><span data-stu-id="e7f6f-127">**Part Assembly Controller (Script)** component</span></span>

![Unity con RoverAssembly y todos los objetos de partes del róver seleccionados y los componentes agregados](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="e7f6f-129">Para seleccionar varios objetos que no estén juntos entre sí, mantenga presionada la tecla Control mientras usa el mouse para seleccionar cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="e7f6f-130">Cuando se agrega un manipulador de objetos (script), en este caso, se agrega automáticamente el administrador de restricciones (script) porque el manipulador de objetos (script) depende de él.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-130">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="e7f6f-131">Para los fines de este tutorial, los colisionadores ya se han agregado a las partes del róver.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="e7f6f-132">Para obtener más información sobre los colisionadores, visita la documentación sobre <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">colisionadores</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="e7f6f-133">El controlador Part Assembly Controller (Script) (Controlador de ensamblado de partes [script]) no forma parte de MRTK, pero se incluyó con los recursos del tutorial.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="e7f6f-134">Con todos los objetos de las partes de róver y el objeto RoverAssembly todavía seleccionados, en la ventana Inspector, configure el componente **Object Manipulator (Script)** (Manipulador de objetos [script]) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="e7f6f-135">En la lista desplegable **Two Handed Manipulation Type** (Tipo de manipulación con dos manos), desactive la escala, de modo que solo queden habilitadas las opciones **Mover** y **Girar**.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![Unity con Two Handed Manipulation Type (Tipo de manipulación con dos manos) configurado](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="e7f6f-137">En este punto, ha habilitado la manipulación de objetos para todos los objetos de las piezas de Rover y el objeto RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="e7f6f-138">En la ventana Proyecto, navegue hasta **Recursos** > **MRTK** > **StandardAssets** >  carpeta **Audio** para buscar los clips de audio:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-138">In the Project window, navigate to the **Assets** > **MRTK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![Ventana Project (Proyecto) de Unity con la carpeta Audio seleccionada](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="e7f6f-140">En la ventana Hierarchy (Jerarquía), seleccione todos los **objetos de las partes del róver** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **Audio sources** (Orígenes de audio) y configurarlo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="e7f6f-141">Asigne el clip de audio **MRTK_Scale_Start** al campo **AudioClip**.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="e7f6f-142">Desactive la casilla **Play On Awake** (Reproducir al reactivar).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="e7f6f-143">Cambie **Spatial Blend** a 1.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-143">Change **Spatial Blend** to 1</span></span>

![Unity con todas las partes del róver seleccionadas y el componente Audio Source (Origen de audio) agregado y configurado](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="e7f6f-145">En la ventana Hierarchy (Jerarquía), expanda el objeto RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** para mostrar todos los objetos de sugerencia de selección de ubicación y, a continuación, seleccione la primera parte de róver, RoverParts > **Camera_Part** y configure el componente **Part Assembly Controller (Script)** (Controlador de ensamblado de partes [script]) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="e7f6f-146">Asigne el objeto **Camera_PlacementHint** al campo **Location To Place** (Ubicación de colocación).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Unity con el componente Camera_Part PartAssemblyController configurado](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="e7f6f-148">**Repita** este paso para cada uno de los objetos de las partes de róver restantes y el objeto RoverAssembly con tal de configurar el componente **Part Assembly Controller (Script)** (Controlador de ensamblado de partes [script]) de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="e7f6f-149">Para la parte **Generator_Part**, asigne el objeto **Generator_PlacementHint** al campo **Location To Place** (Ubicación de colocación).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="e7f6f-150">Para la parte **Lights_Partt**, asigne el objeto **Lights_PlacementHint** al campo **Location To Place** (Ubicación de colocación).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="e7f6f-151">Para la parte **UHFAntenna_Part**, asigne el objeto **UHFAntenna_PlacementHint** al campo **Location To Place** (Ubicación de colocación).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="e7f6f-152">Para la parte **Spectrometer_Part**, asigne el objeto **Spectrometer_PlacementHint** al campo **Location To Place** (Ubicación de colocación).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="e7f6f-153">Para el elemento **RoverAssembly**, asigne el propio objeto, es decir, el mismo objeto **RoverAssembly**, en el campo **Location To Place** (Ubicación de colocación).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="e7f6f-154">En la ventana Hierarchy (Jerarquía), seleccione el objeto del botón RoverExplorer > Buttons > **Reset** (RoverExplorer > Botones > Restablecer) y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de interacción de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e7f6f-155">Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7f6f-156">En la lista desplegable **No Function** (Ninguna función), seleccione **PartAssemblyController** > **ResetPlacement ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del objeto de botón Reset configurado](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="e7f6f-158">Si ahora entra en el Modo Juego, podrá usar la interacción cercana o lejana para colocar las partes en el róver.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="e7f6f-159">Una vez que la parte esté cerca de la sugerencia de ubicación correspondiente, se ajustará en su lugar y pasará a ser una parte del róver.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="e7f6f-160">Para restablecer las ubicaciones, puede presionar el botón Restablecer:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-160">To reset the placements, you can press the Reset button:</span></span>

![Vista dividida del modo de reproducción de Unity con el botón Reset presionado](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="e7f6f-162">Para obtener más información sobre el componente Object Manipulator (Manipulador de objetos) y sus propiedades asociadas, consulte la guía [Manipulador de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="e7f6f-163">Adición de cuadros de límite</span><span class="sxs-lookup"><span data-stu-id="e7f6f-163">Adding bounding boxes</span></span>

<span data-ttu-id="e7f6f-164">Los cuadros de límite hacen que manipular objetos con una mano sea más sencillo e intuitivo tanto para la interacción próxima como remota, ya que proporcionan controladores que se pueden usar para el escalado y la rotación.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-164">Bounding boxes makes it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="e7f6f-165">En este ejemplo, agregará un cuadro de límite al objeto RoverExplorer para que toda la experiencia se pueda desplazar, girar y escalar fácilmente.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-165">In this example, you will add a Bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="e7f6f-166">Además, configurará el menú para poder activar y desactivar el cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-166">Additionally, you will configure the Menu so you can turn the Bounding box on and off.</span></span>

<span data-ttu-id="e7f6f-167">En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverExplorer** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar los componentes siguientes:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="e7f6f-168">Componente **BoundingBox**</span><span class="sxs-lookup"><span data-stu-id="e7f6f-168">**BoundingBox** component</span></span>
* <span data-ttu-id="e7f6f-169">Componente **Object Manipulator (Script)** (Manipulador de objetos [script])</span><span class="sxs-lookup"><span data-stu-id="e7f6f-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="e7f6f-170">A continuación, **desactive** la casilla situada junto a todos los componentes para que **estén deshabilitados** de forma predeterminada:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-170">Then **uncheck** the checkbox next to all the components to make them **disabled** by default:</span></span>

![Unity con el objeto RoverExplorer seleccionado y los componentes agregados y deshabilitados](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e7f6f-172">La visualización del cuadro de límite se crea en tiempo de ejecución y, por tanto, no está visible antes de entrar en el modo de juego.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-172">The Bounding box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
><span data-ttu-id="e7f6f-173">El componente BoundingBox agregará automáticamente el componente NearInteractionGrabbable en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-173">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="e7f6f-174">Por lo tanto, no es necesario agregar este componente para agarrar los objetos delimitados con las manos con seguimiento.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-174">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

> [!NOTE]
><span data-ttu-id="e7f6f-175">El manipulador de objetos (script) agrega automáticamente el administrador de restricciones (script)</span><span class="sxs-lookup"><span data-stu-id="e7f6f-175">The Object Manipulator (Script) automatically adds Constraint Manager (Script)</span></span>

<span data-ttu-id="e7f6f-176">En la ventana Hierarchy (Jerarquía), expanda el objeto Menu (Menú) > **ButtonCollection** para mostrar los cuatro botones. Cambie el nombre del tercer botón a **BoundingBox_Enable** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-176">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="e7f6f-177">Cambie el valor **Main Label Text** (Texto de la etiqueta principal) a **Habilitar**.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-177">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="e7f6f-178">Asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-178">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7f6f-179">En la lista desplegable **No Function** (Ninguna función), seleccione **BoundingBox** > **bool Enabled** (Booleano habilitado) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-179">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7f6f-180">Verifique que la casilla del argumento esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-180">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="e7f6f-181">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-181">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="e7f6f-182">Asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-182">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7f6f-183">En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool Enabled** (Booleano habilitado) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-183">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7f6f-184">Verifique que la casilla del argumento esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-184">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="e7f6f-185">Deje el **Icono** como el icono "cubo con control de límites".</span><span class="sxs-lookup"><span data-stu-id="e7f6f-185">Leave the **Icon** as the 'cube with bounds control' icon</span></span>

![Unity con el objeto de botón BoundingBox_Enable seleccionado y el componente Button Config Helper (Asistente de configuración del botón) configurado](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="e7f6f-187">Cambie el nombre del cuarto y el último botón por **BoundingBox_Disable** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-187">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="e7f6f-188">Cambie el valor **Main Label Text** (Texto de la etiqueta principal) a **Deshabilitar**.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-188">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="e7f6f-189">Asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-189">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7f6f-190">En la lista desplegable **No Function** (Ninguna función), seleccione **BoundingBox** > **bool Enabled** (Booleano habilitado) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-190">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7f6f-191">Verifique que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-191">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="e7f6f-192">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-192">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="e7f6f-193">Asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-193">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7f6f-194">En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool Enabled** (Booleano habilitado) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-194">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7f6f-195">Verifique que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-195">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="e7f6f-196">Deje el **Icono** al icono "cubo con control de límites".</span><span class="sxs-lookup"><span data-stu-id="e7f6f-196">Change the **Icon** to the 'cube with bounds control" icon</span></span>

![Unity con el objeto de botón BoundingBox_Disable seleccionado y el componente Button Config Helper (Asistente de configuración del botón) configurado](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="e7f6f-198">Si ahora entra en el modo de juego y habilita el control de límites haciendo clic en el botón Habilitar, podrá usar la interacción cercana o lejana para desplazar, girar y escalar el cuadro de límite, así como usar el botón Deshabilitar para deshabilitar de nuevo el cuadro de límite:</span><span class="sxs-lookup"><span data-stu-id="e7f6f-198">If you now enter Game mode and enable the Bounds Control by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![Vista dividida del modo de reproducción de Unity con el cuadro de límite manipulado](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="e7f6f-200">Para obtener más información sobre el componente de cuadro de límite y sus propiedades asociadas, puede visitar la guía sobre el [cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e7f6f-200">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding Box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="e7f6f-201">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="e7f6f-201">Congratulations</span></span>

<span data-ttu-id="e7f6f-202">En este tutorial, aprendió a habilitar la manipulación cercana y lejana de objetos 3D y a limitar los tipos de manipulación permitidos.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-202">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="e7f6f-203">También aprendió a agregar un cuadro de límite alrededor de objetos 3D para facilitar el control de la manipulación de objetos.</span><span class="sxs-lookup"><span data-stu-id="e7f6f-203">You also learned how to add bounding box around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e7f6f-204">Tutorial siguiente: 8. Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="e7f6f-204">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
