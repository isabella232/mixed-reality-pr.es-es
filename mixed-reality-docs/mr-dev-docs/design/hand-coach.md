---
title: Asesor manual
description: Obtenga información sobre cómo se desencadenan las manos 3D mediante el autocar cuando el sistema no detecta las manos del usuario para ayudarles.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, manual, casco envolvente, MRTK, manos, manos de ayuda, cascos de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0fe0d87e26d06838c0d1b7935573d9bd8ce258ee
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600434"
---
# <a name="hand-coach"></a><span data-ttu-id="47e27-104">Asesor manual</span><span class="sxs-lookup"><span data-stu-id="47e27-104">Hand coach</span></span>

![Ejemplo: Hand coach](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="47e27-106">Hand Coach desencadena las manos modeladas en 3D cuando el sistema no detecta las manos del usuario.</span><span class="sxs-lookup"><span data-stu-id="47e27-106">Hand coach triggers 3D modeled hands when the system doesn't detect the user’s hands.</span></span> <span data-ttu-id="47e27-107">Esta característica es un componente de "enseñanza" que ayuda a guiar al usuario cuando no se ha aprendido el gesto.</span><span class="sxs-lookup"><span data-stu-id="47e27-107">This feature is a “teaching” component that helps guide the user when the gesture hasn't been taught.</span></span> <span data-ttu-id="47e27-108">Si los usuarios no han realizado el gesto especificado durante un período, las manos se pondrán en bucle con un retraso.</span><span class="sxs-lookup"><span data-stu-id="47e27-108">If users haven't done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="47e27-109">El carro de la mano se puede usar para representar la pulsación de un botón o la selección de un holograma.</span><span class="sxs-lookup"><span data-stu-id="47e27-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="47e27-110">Hand coach provided (Preparador de mano proporcionado)</span><span class="sxs-lookup"><span data-stu-id="47e27-110">Hand coach provided</span></span>

<span data-ttu-id="47e27-111">El modelo de interacción actual representa una amplia variedad de controles de gestos, como desplazamiento, selección lejana y pulsación cercana.</span><span class="sxs-lookup"><span data-stu-id="47e27-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="47e27-112">A continuación se muestra una lista completa de los gestos de mano existentes que se proporcionan<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> en MRTK:</a></span><span class="sxs-lookup"><span data-stu-id="47e27-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="47e27-113">![Ejemplo de selección próxima](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="47e27-114">**Ejemplo de selección cercana: se usa para mostrar cómo seleccionar botones o cerrar objetos interactuables**</span><span class="sxs-lookup"><span data-stu-id="47e27-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47e27-115">![Ejemplo de pulsación en el aire](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="47e27-116">**Ejemplo de pulsación en el aire: se usa para mostrar cómo seleccionar objetos que están lejos**</span><span class="sxs-lookup"><span data-stu-id="47e27-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47e27-117">![Ejemplo de movimiento](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="47e27-118">**Ejemplo de movimiento de un objeto en el espacio: se usa para mostrar cómo mover un holograma en el espacio**</span><span class="sxs-lookup"><span data-stu-id="47e27-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47e27-119">![Ejemplo de rotación](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="47e27-120">**Ejemplo de Rotate-Used para mostrar cómo girar hologramas u objetos**</span><span class="sxs-lookup"><span data-stu-id="47e27-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="47e27-121">![Ejemplo de escala](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="47e27-122">**Ejemplo de escala: se usa para mostrar cómo manipular hologramas para que sean más grandes o más pequeños.**</span><span class="sxs-lookup"><span data-stu-id="47e27-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47e27-123">![Ejemplo de Palm Up](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="47e27-124">**Ejemplo de Pie arriba: uso sugerido para mostrar menús de mano**</span><span class="sxs-lookup"><span data-stu-id="47e27-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47e27-125">![Ejemplo de HandFlip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="47e27-126">**Exmaple de Hand Flip: otra manera de mostrar menús de mano**</span><span class="sxs-lookup"><span data-stu-id="47e27-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47e27-127">![Ejemplo de desplazamiento](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="47e27-128">**Ejemplo de desplazamiento: se usa para desplazar una lista o un documento largo**</span><span class="sxs-lookup"><span data-stu-id="47e27-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="47e27-129">Conceptos de diseño</span><span class="sxs-lookup"><span data-stu-id="47e27-129">Design concepts</span></span>

<span data-ttu-id="47e27-130">Para Hololens2, hemos diseñado interacciones a mano basadas en gestos instintivo y naturales de la mano.</span><span class="sxs-lookup"><span data-stu-id="47e27-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="47e27-131">Creemos que son intuitivas para la mayoría de los usuarios, por lo que no creamos momentos de aprendizaje de gestos dedicados.</span><span class="sxs-lookup"><span data-stu-id="47e27-131">We believe these to be intuitive to most users, so we didn't create dedicated gesture learning moments.</span></span> <span data-ttu-id="47e27-132">En su lugar, creamos el carro de la mano para ayudar a los usuarios a aprender sobre estos gestos si se atasca o no están familiarizados con las interacciones del holograma.</span><span class="sxs-lookup"><span data-stu-id="47e27-132">Instead, we created the hand coach to help users learn about these gestures if they get stuck or are unfamiliar with hologram interactions.</span></span> <span data-ttu-id="47e27-133">Sin un momento de aprendizaje, creemos que mostrar a los usuarios cómo realizar una acción demostrando que sería la mejor opción.</span><span class="sxs-lookup"><span data-stu-id="47e27-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="47e27-134">Hemos descubierto que los usuarios pudieron averiguar el gesto, pero necesitaron un poco de guía.</span><span class="sxs-lookup"><span data-stu-id="47e27-134">We found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="47e27-135">Si detectamos que un usuario no interactúa con un objeto durante un período, se desencadenaría un autocar de mano que demostrara la colocación correcta de la mano y el dedo.</span><span class="sxs-lookup"><span data-stu-id="47e27-135">If we detect a user doesn't interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="47e27-136">Intuitiva</span><span class="sxs-lookup"><span data-stu-id="47e27-136">Intuitive</span></span>

<span data-ttu-id="47e27-137">Al animar las manos, debe ser obvio y no debe causar confusión.</span><span class="sxs-lookup"><span data-stu-id="47e27-137">When animating hands, it should be obvious and shouldn't cause any confusion.</span></span> <span data-ttu-id="47e27-138">La animación de la mano es una representación del gesto que está intentando pedir al usuario que entienda.</span><span class="sxs-lookup"><span data-stu-id="47e27-138">The hand animation is a representation of the gesture you're trying to prompt the user to understand.</span></span> 

<span data-ttu-id="47e27-139">Por ejemplo, si desea que un usuario presione un botón, se desencadenaría una pulsación con la mano de un botón.</span><span class="sxs-lookup"><span data-stu-id="47e27-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="47e27-140">![Ejemplo: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="47e27-141">*Hand Coach que muestra cerca de pulsar una gema*</span><span class="sxs-lookup"><span data-stu-id="47e27-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="47e27-142">Escala de la mano</span><span class="sxs-lookup"><span data-stu-id="47e27-142">Hand scale</span></span>

<span data-ttu-id="47e27-143">Hemos probado varios tamaños de mano con los menús de la interfaz de usuario y sentimos que, si las manos eran verdaderas para el tamaño, nos dio una sensación amenazante.</span><span class="sxs-lookup"><span data-stu-id="47e27-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling.</span></span> <span data-ttu-id="47e27-144">Si eran demasiado pequeños, era difícil ver y comprender el gesto.</span><span class="sxs-lookup"><span data-stu-id="47e27-144">If they were too small, it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="47e27-145">**Voz sobre y manos**</span><span class="sxs-lookup"><span data-stu-id="47e27-145">**Voice over and hands**</span></span>

<span data-ttu-id="47e27-146">No espere que los usuarios puedan escuchar un conjunto de instrucciones a través de la voz y ver instrucciones diferentes a través de Hand coach.</span><span class="sxs-lookup"><span data-stu-id="47e27-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="47e27-147">Secuenciar las instrucciones para ayudar a los usuarios a centrarse frente a competir por su atención para reducir la sobrecarga sensoría.</span><span class="sxs-lookup"><span data-stu-id="47e27-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="47e27-148">¿Puedo crear los suyos propios?</span><span class="sxs-lookup"><span data-stu-id="47e27-148">Can I create my own?</span></span>

<span data-ttu-id="47e27-149">Sí.</span><span class="sxs-lookup"><span data-stu-id="47e27-149">Yes!</span></span> <span data-ttu-id="47e27-150">Le animamos a crear su propio gesto único para su juego y contribuir de nuevo a la comunidad.</span><span class="sxs-lookup"><span data-stu-id="47e27-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="47e27-151">Se ha proporcionado un archivo Maya de una mano desasistido que se puede usar para la aplicación, que se puede descargar aquí: <a href="files/HandCoach_MRTK.zip"> Descargar HandCoach_MRTK.zip </a></span><span class="sxs-lookup"><span data-stu-id="47e27-151">We've provided a Maya file of a Rigged hand that can be used for your app, which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip </a></span></span>

<span data-ttu-id="47e27-152">![Ejemplo de manos animadas en Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="47e27-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="47e27-153">*Ejemplo de afición a mano animada de un cuadro en Maya*</span><span class="sxs-lookup"><span data-stu-id="47e27-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="47e27-154">**Herramienta de creación recomendada**</span><span class="sxs-lookup"><span data-stu-id="47e27-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="47e27-155">Entre los intérpretes en 3D, muchos deciden usar Maya de Autodesk, que puede usar [HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar la forma en que se crean los recursos.</span><span class="sxs-lookup"><span data-stu-id="47e27-155">Among 3D artists, many choose to use [Autodesk’s Maya, which can use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="47e27-156">El archivo de manos proporcionado es un archivo binario maya, por lo que se recomienda usar Maya para animar y exportar las manos.</span><span class="sxs-lookup"><span data-stu-id="47e27-156">The hands file provided is a Maya Binary File, so it's recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="47e27-157">Si prefiere usar otro programa 3D, este es un <b>. FBX:</b> <a href="files/HandCoachMRTK_FBX.zip"> descargue HandCoachMRTK_FBX.zip </a> para crear su propia configuración de controlador.</span><span class="sxs-lookup"><span data-stu-id="47e27-157">If you prefer to use another 3D program, here's a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Download HandCoachMRTK_FBX.zip </a> to create your own controller setup.</span></span> 

<span data-ttu-id="47e27-158">Si usa el archivo de mano maya descargable proporcionado, se recomienda reducir verticalmente las manos en Unity a 0,6.</span><span class="sxs-lookup"><span data-stu-id="47e27-158">If using the downloadable maya Hand File provided, it's suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="47e27-159">![Ejemplo: carro de carro de mano en Maya](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="47e27-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="47e27-160">*Manos desapareadas*</span><span class="sxs-lookup"><span data-stu-id="47e27-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="47e27-161">Especificaciones técnicas</span><span class="sxs-lookup"><span data-stu-id="47e27-161">Technical Specs</span></span>

*   <span data-ttu-id="47e27-162">El archivo con dos manos está disponible en formato Maya Ascii</span><span class="sxs-lookup"><span data-stu-id="47e27-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="47e27-163">La mano derecha e izquierda está disponible en formato binario maya</span><span class="sxs-lookup"><span data-stu-id="47e27-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="47e27-164">Establecer el archivo Maya en 24 FPS</span><span class="sxs-lookup"><span data-stu-id="47e27-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="47e27-165">Dentro del archivo, hay una mano izquierda y derecha, que se puede usar para dos gestos con una sola mano o con una sola mano.</span><span class="sxs-lookup"><span data-stu-id="47e27-165">Within the file, there's a left and right hand, which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="47e27-166">La mano derecha solo estará visible de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="47e27-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="47e27-167">Se recomienda dejar un búfer de unos 10 fotogramas al principio y al final para atenuaciones.</span><span class="sxs-lookup"><span data-stu-id="47e27-167">It's suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="47e27-168">Si anima un objeto con un destino especificado, su procedimiento recomendado para animar a un cuadro Predeterminado o Null.</span><span class="sxs-lookup"><span data-stu-id="47e27-168">If animating an object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="47e27-169">Si la mano anima un objeto físico como un cuadro, su procedimiento recomendado es no animar la traducción en Maya, pero esperar a animarlo en Unity o en código.</span><span class="sxs-lookup"><span data-stu-id="47e27-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="47e27-170">La animación visible debe ser de 1,5 segundos para que se transmita cualquier información significativa.</span><span class="sxs-lookup"><span data-stu-id="47e27-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="47e27-171">Cuando se sienta satisfecho con la animación:</span><span class="sxs-lookup"><span data-stu-id="47e27-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="47e27-172">Selección de todas las uniones y bake key frames</span><span class="sxs-lookup"><span data-stu-id="47e27-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="47e27-173">Eliminar los controladores, seleccionar las uniones y la malla y exportar como FBX</span><span class="sxs-lookup"><span data-stu-id="47e27-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="47e27-174">Si hay varias animaciones, puede usar el exportador de juegos integrado de Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="47e27-174">If there are Multiple Animations, you can use Maya’s built-in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="47e27-175">Exportación desde Maya</span><span class="sxs-lookup"><span data-stu-id="47e27-175">Exporting from Maya</span></span>

<span data-ttu-id="47e27-176">Una vez que esté satisfecho con la animación</span><span class="sxs-lookup"><span data-stu-id="47e27-176">After you're satisfied with your animation</span></span>
* <span data-ttu-id="47e27-177">Seleccionar todas las uniones: seleccione > jerarquía</span><span class="sxs-lookup"><span data-stu-id="47e27-177">Select all joints: Select > Hierarchy</span></span>

     ![Ejemplo: Jerarquía en el menú](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="47e27-179">Bake out your animation (Bake out your animation: cambiar a Animation > Key > Bake Animation</span><span class="sxs-lookup"><span data-stu-id="47e27-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Ejemplo: Ubicación del menú Bake Animation](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="47e27-181">Eliminar el equipo del controlador: esquema > MainR_Grp o MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="47e27-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Ejemplo: Ubicación del menú De la plataforma del controlador](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="47e27-183">Exportar como FBX: Seleccione JNT + Malla: Selección > exportar archivos (cuadro de opciones) > Exportar selección</span><span class="sxs-lookup"><span data-stu-id="47e27-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Ejemplo: Exportación de la ubicación del menú de selección](images/HandCoach/OptionBox.png)<br>

     ![Ejemplo: Ubicación del menú](images/HandCoach/SelectionExport.png)<br>

     ![Ejemplo: Ubicación del menú Opciones de exportación](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="47e27-187">Al exportar como FBX y pasar a Unity, escale las manos hacia abajo a 0,6.</span><span class="sxs-lookup"><span data-stu-id="47e27-187">When exporting as an FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="47e27-188">Encontramos que esto era un equilibrio perfecto para mostrar las manos.</span><span class="sxs-lookup"><span data-stu-id="47e27-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="47e27-189">![Ejemplo: Configuración de Unity](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="47e27-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="47e27-190">*Configuración de Unity HandCoach_R se encuentra en MRTK*</span><span class="sxs-lookup"><span data-stu-id="47e27-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="47e27-191">Implementación de manos en el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="47e27-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="47e27-192">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="47e27-192">Best practices</span></span>

* <span data-ttu-id="47e27-193">Se recomienda reducir verticalmente las manos en Unity a 0,6.</span><span class="sxs-lookup"><span data-stu-id="47e27-193">It's suggested to scale down the hands in unity to 0.6</span></span>
* <span data-ttu-id="47e27-194">Las manos se deben reproducir dos veces y, si no se completan, se buclen continuamente hasta que se complete el gesto.</span><span class="sxs-lookup"><span data-stu-id="47e27-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="47e27-195">Las manos deben estar en bucle dos veces para asegurarse de que el usuario tiene tiempo para registrarse y ver el gesto.</span><span class="sxs-lookup"><span data-stu-id="47e27-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="47e27-196">Las manos deben atenuarse entre bucles.</span><span class="sxs-lookup"><span data-stu-id="47e27-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="47e27-197">Si las manos del usuario son visibles por las cámaras HL2, pero los usuarios no están realizando la interacción necesaria para ellas, las manos aparecerán después de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="47e27-197">If user’s hands are visible by HL2 cameras but users aren't doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="47e27-198">Si las manos del usuario NO son visibles por las cámaras HL2, las manos aparecerán después de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="47e27-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="47e27-199">Si las cámaras HL2 del centro de la animación realiza un seguimiento visible de las manos del usuario, la animación se completará y se atenuará.</span><span class="sxs-lookup"><span data-stu-id="47e27-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="47e27-200">Si va a incluir la voz en exceso, se recomienda que se corresponda con el gesto de la mano.</span><span class="sxs-lookup"><span data-stu-id="47e27-200">If you're including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="47e27-201">Si ha enseñado las manos al menos una vez, repita el gesto solo si se detecta que el usuario está atascado.</span><span class="sxs-lookup"><span data-stu-id="47e27-201">If you've taught the hands at least once, only repeat the gesture if it's detected that the user is stuck.</span></span>
*   <span data-ttu-id="47e27-202">Si las posiciones específicas de los dedos y las manos son críticas, asegúrese de que los usuarios puedan ver claramente estos matices en la animación.</span><span class="sxs-lookup"><span data-stu-id="47e27-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="47e27-203">Pruebe a usar las manos para que las partes más importantes sean claramente visibles.</span><span class="sxs-lookup"><span data-stu-id="47e27-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="47e27-204">Si observa distorsión en las manos, debe ir a La configuración de calidad de Unity aumenta el número de pies.</span><span class="sxs-lookup"><span data-stu-id="47e27-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the number of bones.</span></span> 
 <span data-ttu-id="47e27-205">Vaya a Editar la configuración del proyecto > de Unity > calidad > otras > blend weights(Pesos de blend).</span><span class="sxs-lookup"><span data-stu-id="47e27-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="47e27-206">Asegúrese de que se seleccionan "4 esqueletos" para ver Smooth Joints (Juntas suavizadas).</span><span class="sxs-lookup"><span data-stu-id="47e27-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span>

   ![Ejemplo: Ventana Configuración del proyecto](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a><span data-ttu-id="47e27-208">Qué evitar</span><span class="sxs-lookup"><span data-stu-id="47e27-208">What to avoid</span></span>

* <span data-ttu-id="47e27-209">Escalado de las manos demasiado grandes</span><span class="sxs-lookup"><span data-stu-id="47e27-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="47e27-210">colocar las manos demasiado cerca del usuario</span><span class="sxs-lookup"><span data-stu-id="47e27-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="47e27-211">Las manos solo se deben enseñar una vez.</span><span class="sxs-lookup"><span data-stu-id="47e27-211">Hands should only be taught once.</span></span> <span data-ttu-id="47e27-212">La enseñanza excesiva puede provocar confusión y desorden</span><span class="sxs-lookup"><span data-stu-id="47e27-212">Over teaching can cause confusion and messiness</span></span>
* <span data-ttu-id="47e27-213">Para incorporarlo a Unity, descargue la versión más reciente de MRTK aquí: https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="47e27-213">Bringing it into Unity, download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
  * <span data-ttu-id="47e27-214">Material: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="47e27-214">Material: Teaching_Hand2</span></span>
  * <span data-ttu-id="47e27-215">Scripts: consulte las directrices de MRTK para <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> el técnico de MRTK. </a></span><span class="sxs-lookup"><span data-stu-id="47e27-215">Scripts: Refer to MRTK guidelines for <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> MRTK hand coach </a></span></span>
  * <span data-ttu-id="47e27-216">Configuración por proyecto</span><span class="sxs-lookup"><span data-stu-id="47e27-216">Per- project setting</span></span>
    * <span data-ttu-id="47e27-217">Escena establecida en UWP: la instrucción se puede encontrar en [configurar el proyecto de Unity](../develop/unity/Configure-Unity-Project.md) para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="47e27-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](../develop/unity/Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="47e27-218">Vea también</span><span class="sxs-lookup"><span data-stu-id="47e27-218">See also</span></span>

* [<span data-ttu-id="47e27-219">Aspectos básicos de la interacción</span><span class="sxs-lookup"><span data-stu-id="47e27-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="47e27-220">Proceso de creación de recursos</span><span class="sxs-lookup"><span data-stu-id="47e27-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="47e27-221">Gestos</span><span class="sxs-lookup"><span data-stu-id="47e27-221">Gestures</span></span>](./interaction-fundamentals.md)
* [<span data-ttu-id="47e27-222">Instalar las herramientas</span><span class="sxs-lookup"><span data-stu-id="47e27-222">Install the Tools</span></span>](../develop/install-the-tools.md)
* [<span data-ttu-id="47e27-223">Configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="47e27-223">Configure Unity Project</span></span>](../develop/unity/Configure-Unity-Project.md)
* [<span data-ttu-id="47e27-224">Introducción al desarrollo de Unity</span><span class="sxs-lookup"><span data-stu-id="47e27-224">Unity development overview</span></span>](../develop/unity/unity-development-overview.md)
* [<span data-ttu-id="47e27-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="47e27-225">MRTK 101</span></span>](/windows/mixed-reality/mrtk-unity/)