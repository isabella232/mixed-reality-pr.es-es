---
title: Designing Holograms
description: Obtenga información sobre la realidad mixta a través de la nueva aplicación de hologramas de diseño de Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, kit de herramientas de realidad mixta, hologramas, diseño de hologramas, aprendizaje, aplicación de ejemplo, auriculares de realidad mixta, auriculares de realidad virtual, qué es realidad virtual
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757763"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="6ef05-104">La realización del diseño de hologramas</span><span class="sxs-lookup"><span data-stu-id="6ef05-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="6ef05-105">Permita que una pequeña ventana de carga tenga en cuenta todos los archivos GIF y los vídeos insertados en esta página.</span><span class="sxs-lookup"><span data-stu-id="6ef05-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="6ef05-106">Aprender a diseñar una realidad mixta puede ser difícil, ya que el medio no siempre se convierte bien en procesos de diseño 2D.</span><span class="sxs-lookup"><span data-stu-id="6ef05-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="6ef05-107">Aquí, en Microsoft, hemos creado una aplicación gratuita para HoloLens 2 que le ayudará a conocer los aspectos básicos del diseño de la experiencia de usuario de realidad mixta de primera mano.</span><span class="sxs-lookup"><span data-stu-id="6ef05-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="6ef05-108">El enfoque único de la aplicación de diseño de hologramas se adentra en comportamientos de realidad mixta, sugerencias y recomendaciones para ayudarle a crear aplicaciones de HoloLens atractivas y increíbles propias.</span><span class="sxs-lookup"><span data-stu-id="6ef05-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="6ef05-109">Descargue la aplicación de forma gratuita desde el Microsoft Store y aprenda del equipo de diseño de la realidad mixta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6ef05-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6ef05-110">Descarga de la aplicación de diseño de hologramas</span><span class="sxs-lookup"><span data-stu-id="6ef05-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animado de la escena de seguimiento de cabeza en el salón de demostración del holograma de diseño](images/designing-holograms/demo-room.gif)

<span data-ttu-id="6ef05-112">*Diseñar el salón de demostración del holograma (también conocido como la casa de muñecas)*</span><span class="sxs-lookup"><span data-stu-id="6ef05-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="6ef05-113">Diseño para la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="6ef05-113">Designing for mixed reality</span></span>

<span data-ttu-id="6ef05-114">Al igual que muchos de los demás, se usa para diseñar aplicaciones móviles.</span><span class="sxs-lookup"><span data-stu-id="6ef05-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="6ef05-115">Desde un mundo de diseño 2D, pasar a todo en informática espacial, donde todo está ahora en todo el mundo, era un cambio significativo.</span><span class="sxs-lookup"><span data-stu-id="6ef05-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="6ef05-116">En realidad mixta, las aplicaciones ya no se limitan a una pantalla 2D; de hecho, son casi gratis, se colocan en el mundo real e interactúan con objetos reales.</span><span class="sxs-lookup"><span data-stu-id="6ef05-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="6ef05-117">Para mí, la conexión de experiencias 3D a procesos de diseño 2D convencionales es el aspecto más desafiante del desarrollo de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6ef05-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="6ef05-118">En conversaciones con los clientes, oigo cosas como "sé qué características incluir y cómo ponerlas en funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="6ef05-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="6ef05-119">Código, puedo seguir los documentos y tutoriales, pero la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ef05-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="6ef05-120">Muchas características, distintas opciones de entrada, diferentes escenarios y entornos físicos, son abrumadoras ".</span><span class="sxs-lookup"><span data-stu-id="6ef05-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="6ef05-121">![Imagen de la imagen de HoloLens 2 Design Workshop en San Francisco ](images/designing-holograms/workshop.jpeg)
 *del taller de diseño de hololens 2 en San Francisco*</span><span class="sxs-lookup"><span data-stu-id="6ef05-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="6ef05-122">Una oportunidad para enseñar</span><span class="sxs-lookup"><span data-stu-id="6ef05-122">An opportunity to teach</span></span>

<span data-ttu-id="6ef05-123">No resultó obvio al principio, pero se presentó una excelente oportunidad para usar la realidad mixta como medio para enseñarla.</span><span class="sxs-lookup"><span data-stu-id="6ef05-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="6ef05-124">El diseño de hologramas es una experiencia visual que explica los conceptos y las recomendaciones del diseño de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6ef05-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="6ef05-125">Simplemente usted y un profesor virtual muestran conceptos de diseño de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6ef05-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="6ef05-126">Todo está desde una perspectiva de tercera persona con la experiencia firmemente en su propio espacio.</span><span class="sxs-lookup"><span data-stu-id="6ef05-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="6ef05-127">*Vídeo de diseño de hologramas*</span><span class="sxs-lookup"><span data-stu-id="6ef05-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="6ef05-128">Exploración de la casa de muñecas</span><span class="sxs-lookup"><span data-stu-id="6ef05-128">Exploring the doll house</span></span>

<span data-ttu-id="6ef05-129">La casa de muñecas es el entorno virtual que usamos en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ef05-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="6ef05-130">El entorno es una habitación en miniatura de 80 x 60 x 40 cm que contiene los elementos básicos que la mayoría de los salones tienen en común, como las paredes, las lámparas, el mobiliario, una tabla y un televisor.</span><span class="sxs-lookup"><span data-stu-id="6ef05-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="6ef05-131">La casa de muñecas es el protagonist principal de la experiencia de la aplicación, por lo que es necesario asegurarse de que funcionaría bien en cualquier entorno.</span><span class="sxs-lookup"><span data-stu-id="6ef05-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="6ef05-132">Piense en ello como un pequeño salón de demostración para visualizar todo tipo de conceptos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6ef05-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="6ef05-133">*Vídeo del comportamiento de ajuste de dollhouse*</span><span class="sxs-lookup"><span data-stu-id="6ef05-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="6ef05-134">1:1 prototipos de vs 1:10</span><span class="sxs-lookup"><span data-stu-id="6ef05-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="6ef05-135">Nuestra suposición inicial era que las demostraciones de 1:1 serían increíbles, casi como mirar a un profesor real.</span><span class="sxs-lookup"><span data-stu-id="6ef05-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="6ef05-136">El usuario verá todo lo que ve el profesor en una escala de vida real.</span><span class="sxs-lookup"><span data-stu-id="6ef05-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="6ef05-137">Sin embargo, inmediatamente se ha dado cuenta de que hay algunos problemas:</span><span class="sxs-lookup"><span data-stu-id="6ef05-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="6ef05-138">La mayoría de los desarrolladores ejecutarán sus aplicaciones en oficinas o salas más pequeñas que el salón de demostración, por lo que no cabe.</span><span class="sxs-lookup"><span data-stu-id="6ef05-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="6ef05-139">Las pantallas son aditivas, lo que significa que todo el entorno virtual se superpone a la habitación de un usuario.</span><span class="sxs-lookup"><span data-stu-id="6ef05-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="6ef05-140">Esto puede resultar confuso con dos tablas, quizás bisofás y paredes que no se alinean.</span><span class="sxs-lookup"><span data-stu-id="6ef05-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="6ef05-141">Y el peor de los entornos virtuales están muy restringidos por un campo de vista.</span><span class="sxs-lookup"><span data-stu-id="6ef05-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="6ef05-142">Cuando se intentó una pequeña escala de 1:10, el resultado era una fantástica vista de pájaro de un salón realista.</span><span class="sxs-lookup"><span data-stu-id="6ef05-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="6ef05-143">Podría ver todo lo que estaba pasando desde cualquier ángulo al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="6ef05-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="6ef05-144">Lo más sorprendente es que la mayoría de los evaluadores lo encontraron mucho más envolventes para ver una versión pequeña y, después, nunca se han vuelto a la escala 1:1.</span><span class="sxs-lookup"><span data-stu-id="6ef05-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="6ef05-145">Por lo tanto, hemos decidido rechazar la versión 1:1 y evitar el trabajo adicional necesario para adaptar la interfaz de usuario y otros aspectos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ef05-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="6ef05-146">![Campo de vista con el ](images/designing-holograms/1-1-scale.png)
 *campo de escala 1:1 de la vista con la escala 1:1*</span><span class="sxs-lookup"><span data-stu-id="6ef05-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="6ef05-147">![Campo de vista con el ](images/designing-holograms/1-10-scale.png)
 *campo de escala 1:10 de la vista con la escala 1:10*</span><span class="sxs-lookup"><span data-stu-id="6ef05-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="6ef05-148">Uso de la captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="6ef05-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="6ef05-149">Una de las características más característicos de esta aplicación es el uso de la captura de realidad mixta para enseñar y demostrar conceptos de diseño de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6ef05-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="6ef05-150">Microsoft tiene un estudio de captura de realidad mixta en San Francisco.</span><span class="sxs-lookup"><span data-stu-id="6ef05-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="6ef05-151">Microsoft también concede licencias para esta tecnología a otros estudios, que incluyen la dimensión de Avatar en Washington D.C., metastage en los Ángeles, estudios de Dimension en Londres, SK Telecom en Seúl y Volucap en Berlín.</span><span class="sxs-lookup"><span data-stu-id="6ef05-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="6ef05-152">Puede encontrar más información sobre nuestros [estudios de captura de realidad mixta aquí](https://www.microsoft.com/mixed-reality/capture-studios).</span><span class="sxs-lookup"><span data-stu-id="6ef05-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="6ef05-153">*Material de estudio de Daniel escudero de una de las cámaras 106 en el estudio de captura de realidad mixta en San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="6ef05-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="6ef05-154">El proceso de captura genera una malla, normales y texturas fotogramas clave, que se pueden entregar como archivos OBJ/PNG para posteriores a la producción o listas para su reproducción como un archivo MP4 comprimido H. 264.</span><span class="sxs-lookup"><span data-stu-id="6ef05-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="6ef05-155">Estos archivos se pueden importar en proyectos Unity, no reales, nativos y WebXR.</span><span class="sxs-lookup"><span data-stu-id="6ef05-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="6ef05-156">Los archivos se pueden ejecutar en Windows, iOS, Mac, Android, Magic Leap y PlayStation VR.</span><span class="sxs-lookup"><span data-stu-id="6ef05-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="6ef05-157">*El reproductor de captura proporcionado para analizar MP4 que contienen vídeo con audio y mallas incrustadas.*</span><span class="sxs-lookup"><span data-stu-id="6ef05-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="6ef05-158">Manipular capturas y objetos virtuales</span><span class="sxs-lookup"><span data-stu-id="6ef05-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="6ef05-159">Las capturas de realidad mixta producen representaciones virtuales de personas o animales, pero en ocasiones puede que necesite esos caracteres para interactuar con otros objetos virtuales.</span><span class="sxs-lookup"><span data-stu-id="6ef05-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="6ef05-160">En los dos ejemplos siguientes se muestran distintas formas de manipular las escenas para lograr este efecto.</span><span class="sxs-lookup"><span data-stu-id="6ef05-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="6ef05-161">Ajuste de mira hacia abajo</span><span class="sxs-lookup"><span data-stu-id="6ef05-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="6ef05-162">El ajuste Headgaze permite trasladar el encabezado de una persona capturada en tiempo de ejecución, lo que significa que podría tener una superficie de captura hacia un usuario.</span><span class="sxs-lookup"><span data-stu-id="6ef05-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="6ef05-163">En nuestro caso, se usa para mostrar el campo de vista y el campo de interés.</span><span class="sxs-lookup"><span data-stu-id="6ef05-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="6ef05-164">Lo que se ve a continuación es un GameObject en movimiento que actúa como un destino para que la mirada mire.</span><span class="sxs-lookup"><span data-stu-id="6ef05-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="6ef05-165">A medida que se mueve el destino de lado a lado, se sigue el encabezado de la captura.</span><span class="sxs-lookup"><span data-stu-id="6ef05-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="6ef05-166">Usamos este truco para asegurarnos de que la captura inactiva siempre se encontraba en los hologramas colocados en distintas partes de la casa de muñecas.</span><span class="sxs-lookup"><span data-stu-id="6ef05-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![El encabezado de la captura se mueve en el tiempo de ejecución después de un GameObject de destino en Unity.](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="6ef05-168">*El encabezado de la captura se mueve en el tiempo de ejecución después de un GameObject de destino en Unity.*</span><span class="sxs-lookup"><span data-stu-id="6ef05-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="6ef05-169">Sincronizar objetos animados</span><span class="sxs-lookup"><span data-stu-id="6ef05-169">Syncing Animated Objects</span></span>

<span data-ttu-id="6ef05-170">El segundo, estaba animando objetos para sincronizar con el movimiento de una captura.</span><span class="sxs-lookup"><span data-stu-id="6ef05-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="6ef05-171">En diferentes partes de la aplicación, se han importado obj secuenciales de una captura específica cada cinco fotogramas.</span><span class="sxs-lookup"><span data-stu-id="6ef05-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="6ef05-172">Después, los obj se animaron en la escena para asegurarse de que coincidirían con el fotograma correspondiente de la captura.</span><span class="sxs-lookup"><span data-stu-id="6ef05-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="6ef05-173">Es un proceso tedioso de animación y fotogramas clave, pero el resultado es excelente.</span><span class="sxs-lookup"><span data-stu-id="6ef05-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="6ef05-174">Ahora puede ver una captura de realidad mixta que interactúa con objetos no capturados.</span><span class="sxs-lookup"><span data-stu-id="6ef05-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Animación sincronizada entre una captura de realidad mixta y un panel de interfaz de usuario](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="6ef05-176">*Animación sincronizada entre una captura de realidad mixta y un panel de interfaz de usuario*</span><span class="sxs-lookup"><span data-stu-id="6ef05-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="6ef05-177">Proceso de creación de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="6ef05-177">UI creative process</span></span>

<span data-ttu-id="6ef05-178">Cuando comenzamos el diseño de la interfaz de usuario, quisiéramos mostrar algunos de los casos de magia y la posibilidad de que los hologramas lo ofrezcan.</span><span class="sxs-lookup"><span data-stu-id="6ef05-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="6ef05-179">Simplemente mostrar ventanas 2D estáticas y cuadros de texto no se siente bien en el mundo 3D.</span><span class="sxs-lookup"><span data-stu-id="6ef05-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="6ef05-180">Muchas de las posibilidades que hay a mano no se muestran, así que desde el principio decidimos apartarse de eso y hacer uso completo del espacio 3D holográfica.</span><span class="sxs-lookup"><span data-stu-id="6ef05-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="6ef05-181">En primer lugar, empezamos por agregar cierto grosor a los paneles, iconos e información de texto.</span><span class="sxs-lookup"><span data-stu-id="6ef05-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="6ef05-182">Aún así, como usuario, lo que veo es un cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="6ef05-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="6ef05-183">Cuadros de texto con imágenes, pero no estamos ahí.</span><span class="sxs-lookup"><span data-stu-id="6ef05-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="6ef05-184">Hemos ido más lejos mediante el uso de los sombreadores de kit de herramientas de realidad mixta (MRTK).</span><span class="sxs-lookup"><span data-stu-id="6ef05-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="6ef05-185">Los sombreadores de MRTK se convierten en una herramienta eficaz y hicimos uso de sus características de estarcido para agregar profundidad negativa a los paneles.</span><span class="sxs-lookup"><span data-stu-id="6ef05-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="6ef05-186">Esto significa que, en lugar de agregar elementos delante de un cuadro de texto, los iconos aparecen ahora detrás de un panel transparente.</span><span class="sxs-lookup"><span data-stu-id="6ef05-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="6ef05-187">Lo que veo ahora como usuario es algo que simplemente no puedo replicar en el mundo real, y aquí es donde se empezó a producir holográfica mágica.</span><span class="sxs-lookup"><span data-stu-id="6ef05-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="6ef05-188">Además, como usuario realmente no me gustaría leer, hago mucho en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="6ef05-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="6ef05-189">Obviamente, los iconos funcionan mucho mejor que el texto sencillo, para proporcionar una guía aún más eficaz y, a continuación, empezaron a crear un conjunto de objetos animados y avatares, cada uno de ellos indicando una pequeña historia sobre lo que se hace en el escenario respectivo y cómo se usa.</span><span class="sxs-lookup"><span data-stu-id="6ef05-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![GIF animado de un sistema de menús de Holographic interactivo](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="6ef05-191">Conceptos principales</span><span class="sxs-lookup"><span data-stu-id="6ef05-191">Core concepts</span></span>

<span data-ttu-id="6ef05-192">**Marco holográfico**</span><span class="sxs-lookup"><span data-stu-id="6ef05-192">**Holographic frame**</span></span>

![GIF animado de un usuario que mira el dollhouse con el marco holográfica resaltado](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="6ef05-194">**Sistemas de coordenadas**</span><span class="sxs-lookup"><span data-stu-id="6ef05-194">**Coordinate systems**</span></span>

![GIF animado de un usuario que busca Dollhouse con los sistemas de coordenadas resaltados](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="6ef05-196">**Seguimiento de los ojos**</span><span class="sxs-lookup"><span data-stu-id="6ef05-196">**Eye tracking**</span></span>

![GIF animado de un usuario que mira los hologramas estacionales con el rayo ojo mirado](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="6ef05-198">**Visualización de detección de salón y asignación espacial**</span><span class="sxs-lookup"><span data-stu-id="6ef05-198">**Room scan visualization and spatial mapping**</span></span>

![GIF animado de todas las superficies dentro del dollhouse que se está asignando](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="6ef05-200">**Descripción de escenas**</span><span class="sxs-lookup"><span data-stu-id="6ef05-200">**Scene understanding**</span></span>

![GIF animado de objetos en el dollhouse que se está reconociendo](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="6ef05-202">**Punto y confirmación con rayos mano**</span><span class="sxs-lookup"><span data-stu-id="6ef05-202">**Point and commit with hand rays**</span></span>

![GIF animado de un usuario que levanta su mano con un rayo de mano resaltado](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="6ef05-204">Momentos "pruébelo"</span><span class="sxs-lookup"><span data-stu-id="6ef05-204">"Try it out" moments</span></span>

<span data-ttu-id="6ef05-205">El diseño de hologramas enseña conceptos de realidad mixta, pero también le permite probarlos en su habitación.</span><span class="sxs-lookup"><span data-stu-id="6ef05-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="6ef05-206">Después de algunas de esas explicaciones, se pone en pausa y sacamos de la casa de muñecas y en un momento interactivo.</span><span class="sxs-lookup"><span data-stu-id="6ef05-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="6ef05-207">Estos son algunos ejemplos de esos momentos interactivos:</span><span class="sxs-lookup"><span data-stu-id="6ef05-207">Here are some examples of those interactive moments:</span></span>

![GIF animado del marco de seguimiento de mano que se muestra cuando se detectan manos y cuando entran en el campo de la vista](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="6ef05-209">*El marco de seguimiento de mano que se muestra cuando se detectan manos y cuando entran en el campo de la vista.*</span><span class="sxs-lookup"><span data-stu-id="6ef05-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![GIF animado de interactuar con cristales en conflicto a través de la interacción Far](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="6ef05-211">*Interactuar con los cristales en conflicto a través de la interacción lejana*</span><span class="sxs-lookup"><span data-stu-id="6ef05-211">*Interacting with colliding crystals through far interaction*</span></span>

![GIF animado de explorar prestaciones de casi interacción](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="6ef05-213">*Exploración de las prestaciones de casi interacción*</span><span class="sxs-lookup"><span data-stu-id="6ef05-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="6ef05-214">Acerca del equipo</span><span class="sxs-lookup"><span data-stu-id="6ef05-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="6ef05-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="6ef05-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="6ef05-216"><i>Diseñador técnico líder</i></span><span class="sxs-lookup"><span data-stu-id="6ef05-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="6ef05-217">Dan es el director creativo sobre el diseño de hologramas y actualmente funciona como responsable de diseño de la Academia de la realidad mixta de Microsoft en San Francisco y antes era un diseñador en uno de los estudios de realidad mixta de Microsoft en Londres.</span><span class="sxs-lookup"><span data-stu-id="6ef05-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="6ef05-218"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="6ef05-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="6ef05-219"><i>Artista Senior en 3D</i></span><span class="sxs-lookup"><span data-stu-id="6ef05-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="6ef05-220">Martin lidera el diseño de la interfaz de usuario y la imagen en 3D al diseñar hologramas y antes era un artista Senior en 3D en uno de los estudios de realidad mixta de Microsoft en Berlín.</span><span class="sxs-lookup"><span data-stu-id="6ef05-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="6ef05-221">Le agradecemos enormemente el equipo de diseño de la realidad mixta con el fin de compartir tanto conocimiento como el increíble personal en [teoría de objetos](https://objecttheory.com/) para ser integrantes de los compañeros de equipo en cada paso del proyecto.</span><span class="sxs-lookup"><span data-stu-id="6ef05-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="6ef05-222">Gracias por su gran talento, por su pasión y una mirada excepcional para el diseño.</span><span class="sxs-lookup"><span data-stu-id="6ef05-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6ef05-223">Descarga de la aplicación de diseño de hologramas</span><span class="sxs-lookup"><span data-stu-id="6ef05-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)