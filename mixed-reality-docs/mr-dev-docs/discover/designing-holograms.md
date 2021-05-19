---
title: Designing Holograms
description: Obtenga información Mixed Reality a través de la nueva aplicación Diseño de hologramas de Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, hologramas, diseño de hologramas, aprendizaje, aplicación de ejemplo, casco de realidad mixta, casco de realidad virtual, ¿qué es la realidad virtual?
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143634"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="5527f-104">La realización de diseño de hologramas</span><span class="sxs-lookup"><span data-stu-id="5527f-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="5527f-105">Permita que una pequeña ventana de carga tenga en cuenta todos los GIF es cool y los vídeos insertados en esta página.</span><span class="sxs-lookup"><span data-stu-id="5527f-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="5527f-106">Aprender a diseñar para la realidad mixta puede ser difícil porque el medio no siempre se traduce bien en procesos de diseño 2D.</span><span class="sxs-lookup"><span data-stu-id="5527f-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="5527f-107">Aquí, en Microsoft, hemos creado una aplicación gratuita para el HoloLens 2 que le ayudará a conocer de primera mano los aspectos básicos del diseño de la experiencia de usuario de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5527f-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="5527f-108">El enfoque único de la aplicación Diseño de hologramas se a profundizar en comportamientos de realidad mixta, sugerencias y recomendaciones para ayudarle a crear aplicaciones holoLens atractivas y sorprendentes propias.</span><span class="sxs-lookup"><span data-stu-id="5527f-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="5527f-109">Descargue la aplicación de forma gratuita desde el Microsoft Store y aprenda del equipo de diseño de Mixed Reality Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5527f-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5527f-110">Descarga de la aplicación Diseño de hologramas</span><span class="sxs-lookup"><span data-stu-id="5527f-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animado de la escena de seguimiento de la cabeza en la sala de demostración del holograma de diseño](images/designing-holograms/demo-room.gif)

<span data-ttu-id="5527f-112">*Diseño de la sala de demostración del holograma (también conocida como casa de las cámaras)*</span><span class="sxs-lookup"><span data-stu-id="5527f-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="5527f-113">Diseño para la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="5527f-113">Designing for mixed reality</span></span>

<span data-ttu-id="5527f-114">Al igual que muchos de los usuarios, solía diseñar aplicaciones móviles.</span><span class="sxs-lookup"><span data-stu-id="5527f-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="5527f-115">Procedente de un mundo de diseño 2D, saltar a la informática espacial, donde todo está ahora en el mundo, fue un cambio significativo.</span><span class="sxs-lookup"><span data-stu-id="5527f-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="5527f-116">En realidad mixta, las aplicaciones ya no se limitan a una pantalla 2D; de hecho, son casi gratis, se colocan en el mundo real e interactúan con objetos reales.</span><span class="sxs-lookup"><span data-stu-id="5527f-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="5527f-117">Para mí, la conexión de experiencias 3D a procesos de diseño 2D convencionales es el aspecto más complicado del desarrollo de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5527f-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="5527f-118">En las conversaciones con los clientes, oiría cosas como "Sé qué características incluir y cómo hacer que se ejecuten.</span><span class="sxs-lookup"><span data-stu-id="5527f-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="5527f-119">Es código, puedo seguir los documentos y tutoriales, pero ¿la experiencia del usuario?</span><span class="sxs-lookup"><span data-stu-id="5527f-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="5527f-120">Tantas características, distintas opciones de entrada, diferentes escenarios y entornos físicos, es abrumador".</span><span class="sxs-lookup"><span data-stu-id="5527f-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="5527f-121">![Imagen de HoloLens 2 Design Workshop en San Francisco Image from the HoloLens 2 Design Workshop in San Francisco (Imagen del taller de diseño de HoloLens 2 ](images/designing-holograms/workshop.jpeg)
 *en San Francisco)*</span><span class="sxs-lookup"><span data-stu-id="5527f-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="5527f-122">Una oportunidad para enseñar</span><span class="sxs-lookup"><span data-stu-id="5527f-122">An opportunity to teach</span></span>

<span data-ttu-id="5527f-123">Al principio no era obvio, pero se presentaba una excelente oportunidad para usar la realidad mixta como medio para enseñarla.</span><span class="sxs-lookup"><span data-stu-id="5527f-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="5527f-124">El diseño de hologramas es una experiencia visual que explica los conceptos y recomendaciones de diseño de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5527f-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="5527f-125">Solo usted y un profesor virtual muestran los conceptos de diseño de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5527f-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="5527f-126">Todo es desde una perspectiva de tercera persona con la experiencia en firme en su propio espacio.</span><span class="sxs-lookup"><span data-stu-id="5527f-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="5527f-127">*Vídeo del finalizador de diseño de hologramas*</span><span class="sxs-lookup"><span data-stu-id="5527f-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="5527f-128">Exploración de la casa del hogar</span><span class="sxs-lookup"><span data-stu-id="5527f-128">Exploring the doll house</span></span>

<span data-ttu-id="5527f-129">La casa del hogar es el entorno virtual que usamos en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5527f-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="5527f-130">El entorno es una sala de 80 x 60 x 40 cm que contiene los elementos básicos que la mayoría de las salas tienen en común, como las paredes, las luces, los suelos, una mesa y un televisor.</span><span class="sxs-lookup"><span data-stu-id="5527f-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="5527f-131">La casa de cámaras es la principal fuente de la experiencia de la aplicación, por lo que es necesario asegurarnos de que funcionaría bien en cualquier entorno.</span><span class="sxs-lookup"><span data-stu-id="5527f-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="5527f-132">Conséndalo como una pequeña sala de demostración para visualizar todo tipo de conceptos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5527f-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="5527f-133">*Vídeo del comportamiento de ajuste deHouse Desajuste*</span><span class="sxs-lookup"><span data-stu-id="5527f-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="5527f-134">Prototipos de 1:1 frente a 1:10</span><span class="sxs-lookup"><span data-stu-id="5527f-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="5527f-135">Nuestra suposición inicial era que las demostraciones de 1:1 serían increíbles, casi como mirar a un profesor de la vida real.</span><span class="sxs-lookup"><span data-stu-id="5527f-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="5527f-136">El usuario vería todo lo que el profesor ve a escala real.</span><span class="sxs-lookup"><span data-stu-id="5527f-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="5527f-137">Sin embargo, inmediatamente nos dimos cuenta de que habría algunos problemas:</span><span class="sxs-lookup"><span data-stu-id="5527f-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="5527f-138">La mayoría de los desarrolladores ejecutarán sus aplicaciones en oficinas o en salas más pequeñas que la sala de demostración, por lo que no cabría.</span><span class="sxs-lookup"><span data-stu-id="5527f-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="5527f-139">Las pantallas son aditivas, lo que significa que todo el entorno virtual se superará sobre la sala de un usuario.</span><span class="sxs-lookup"><span data-stu-id="5527f-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="5527f-140">Esto puede resultar confuso con dos tablas, quizás dobles y paredes que no se alinean.</span><span class="sxs-lookup"><span data-stu-id="5527f-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="5527f-141">Y lo peor de todo es que un entorno virtual está muy restringido por un campo de vista.</span><span class="sxs-lookup"><span data-stu-id="5527f-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="5527f-142">Cuando hemos probado una escala mini 1:10, el resultado fue una vista fantástica de una sala realista.</span><span class="sxs-lookup"><span data-stu-id="5527f-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="5527f-143">Podía ver todo lo que estaba pasando desde cualquier ángulo al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="5527f-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="5527f-144">Lo más sorprendente es que a la mayoría de los evaluadores les hizo mucho más envolvente ver una versión pequeña y, después, nunca cambiaron a la escala 1:1.</span><span class="sxs-lookup"><span data-stu-id="5527f-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="5527f-145">Por lo tanto, decidimos realmente desechar la versión 1:1 y evitar el trabajo adicional necesario para adaptar la interfaz de usuario y otros aspectos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5527f-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="5527f-146">![Campo de vista con escala 1:1 ](images/designing-holograms/1-1-scale.png)
 *Campo de vista con escala 1:1*</span><span class="sxs-lookup"><span data-stu-id="5527f-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="5527f-147">![Campo de vista con escala 1:10 ](images/designing-holograms/1-10-scale.png)
 *Campo de vista con escala 1:10*</span><span class="sxs-lookup"><span data-stu-id="5527f-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="5527f-148">Uso de Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="5527f-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="5527f-149">Una de las características más características de esta aplicación es el uso de Captura de realidad mixta para enseñar y demostrar conceptos de diseño de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5527f-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="5527f-150">Microsoft tiene un Captura de realidad mixta studio en San Francisco.</span><span class="sxs-lookup"><span data-stu-id="5527f-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="5527f-151">Microsoft también licencia esta tecnología a otros estudios, como Avatar Dimension en Washington D.C., Metastage en Los Ángeles, Dimension Studios en Londres, SK Telecom in London y Volucap en París.</span><span class="sxs-lookup"><span data-stu-id="5527f-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="5527f-152">Puede encontrar más información sobre nuestros [estudios de Captura de realidad mixta aquí.](https://www.microsoft.com/mixed-reality/capture-studios)</span><span class="sxs-lookup"><span data-stu-id="5527f-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="5527f-153">*Secuencia sin procesar de Daniel Escudero de una de las 106 cámaras del Captura de realidad mixta Studio en San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="5527f-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="5527f-154">El proceso de captura genera una malla con fotogramas clave, normales y texturas, que se pueden entregar como archivos OBJ/PNG para su posterior postproducción o listas para la reproducción como un archivo MP4 comprimido H.264.</span><span class="sxs-lookup"><span data-stu-id="5527f-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="5527f-155">Estos archivos se pueden importar en proyectos de Unity, Unreal, Native y WebXR.</span><span class="sxs-lookup"><span data-stu-id="5527f-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="5527f-156">Los archivos se pueden ejecutar en Windows, iOS, Mac, Android, Magic Leap y Playstation VR.</span><span class="sxs-lookup"><span data-stu-id="5527f-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="5527f-157">*Capture Player proporciona para analizar archivos MP4 que contienen vídeo con audio y mallas insertadas.*</span><span class="sxs-lookup"><span data-stu-id="5527f-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="5527f-158">Manipulación de capturas y objetos virtuales</span><span class="sxs-lookup"><span data-stu-id="5527f-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="5527f-159">Mixed Reality captures generan representaciones virtuales de personas o animales, pero en ocasiones es posible que necesite esos caracteres para interactuar con otros objetos virtuales.</span><span class="sxs-lookup"><span data-stu-id="5527f-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="5527f-160">En los dos ejemplos siguientes se muestran distintas formas de manipular las escenas para lograr este efecto.</span><span class="sxs-lookup"><span data-stu-id="5527f-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="5527f-161">Ajuste de la mirada con la cabeza</span><span class="sxs-lookup"><span data-stu-id="5527f-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="5527f-162">El ajuste de headgaze le permite mover la cabeza de una persona capturada en tiempo de ejecución, lo que significa que podría tener una cara de captura hacia un usuario.</span><span class="sxs-lookup"><span data-stu-id="5527f-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="5527f-163">En nuestro caso, lo hemos usado para mostrar el campo de vista y el campo de interés.</span><span class="sxs-lookup"><span data-stu-id="5527f-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="5527f-164">Lo que se ve a continuación es un objeto de juego en movimiento que actúa como destino para que la mirada con la cabeza la mire.</span><span class="sxs-lookup"><span data-stu-id="5527f-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="5527f-165">A medida que movemos el destino de lado a lado, el jefe de la captura sigue.</span><span class="sxs-lookup"><span data-stu-id="5527f-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="5527f-166">Hemos usado este truco para asegurarnos de que la captura inactiva siempre se enfrentaría a hologramas colocados en distintas partes de la casa de la cámara.</span><span class="sxs-lookup"><span data-stu-id="5527f-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![La cabeza de la captura se mueve en tiempo de ejecución después de un gameobject de destino en Unity](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="5527f-168">*La cabeza de la captura se mueve en tiempo de ejecución después de un gameobject de destino en Unity.*</span><span class="sxs-lookup"><span data-stu-id="5527f-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="5527f-169">Sincronizar objetos animados</span><span class="sxs-lookup"><span data-stu-id="5527f-169">Syncing Animated Objects</span></span>

<span data-ttu-id="5527f-170">La segunda, animaba objetos para sincronizar con el movimiento de una captura.</span><span class="sxs-lookup"><span data-stu-id="5527f-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="5527f-171">En diferentes partes de la aplicación, importamos OBJ secuenciales de una captura específica cada cinco fotogramas.</span><span class="sxs-lookup"><span data-stu-id="5527f-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="5527f-172">A continuación, los OBJETOSJ se animaron en la escena para asegurarse de que coincidirían con el fotograma correspondiente de la captura.</span><span class="sxs-lookup"><span data-stu-id="5527f-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="5527f-173">Se trata de un proceso tedioso de animar y defraudar claves, pero el resultado es excelente.</span><span class="sxs-lookup"><span data-stu-id="5527f-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="5527f-174">Ahora puede ver un Captura de realidad mixta interactuar con objetos no capturados.</span><span class="sxs-lookup"><span data-stu-id="5527f-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Animación sincronizada entre un panel Captura de realidad mixta interfaz de usuario](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="5527f-176">*Animación sincronizada entre un panel Captura de realidad mixta interfaz de usuario*</span><span class="sxs-lookup"><span data-stu-id="5527f-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="5527f-177">Proceso creativo de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="5527f-177">UI creative process</span></span>

<span data-ttu-id="5527f-178">Cuando iniciamos el diseño de la interfaz de usuario, queríamos mostrar parte de la magia y la posibilidad de que los hologramas tengan que ofrecer.</span><span class="sxs-lookup"><span data-stu-id="5527f-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="5527f-179">Mostrar ventanas 2D estáticas y cuadros de texto no es adecuado en el mundo 3D.</span><span class="sxs-lookup"><span data-stu-id="5527f-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="5527f-180">Muchas de las posibilidades disponibles no se muestran, por lo que, desde el principio, decidimos dejar de hacerlo y hacer un uso completo del espacio holográfico en 3D.</span><span class="sxs-lookup"><span data-stu-id="5527f-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="5527f-181">Al principio, empezamos con la adición de cierto grosor a los paneles, iconos e información de texto.</span><span class="sxs-lookup"><span data-stu-id="5527f-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="5527f-182">Aun así, como usuario, lo que veo es un cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="5527f-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="5527f-183">Cuadros de texto con imágenes, pero no estamos allí.</span><span class="sxs-lookup"><span data-stu-id="5527f-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="5527f-184">Hemos ido más allá haciendo uso de los sombreadores Mixed Reality Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="5527f-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="5527f-185">Los sombreadores MRTK se han convertido en una herramienta eficaz y hemos hecho uso de sus características de galería de símbolos para agregar profundidad negativa a los paneles.</span><span class="sxs-lookup"><span data-stu-id="5527f-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="5527f-186">Esto significa que, en lugar de agregar elementos delante de un cuadro de texto, los iconos ahora aparecen detrás de un panel transparente.</span><span class="sxs-lookup"><span data-stu-id="5527f-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="5527f-187">Lo que veo ahora como usuario es algo que ya no puedo replicar en el mundo real y aquí es donde comenzó a producirse la magia holográfica.</span><span class="sxs-lookup"><span data-stu-id="5527f-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="5527f-188">Además, como usuario no me gusta leer, ya hago muchas cosas en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="5527f-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="5527f-189">Obviamente, los iconos funcionan mucho mejor que el texto simple. Para proporcionar una guía aún más eficaz, he empezado a crear un conjunto de objetos animados y avatares, y cada uno de ellos cuenta una pequeña historia sobre lo que se hace en el escenario respectivo y cómo se usa.</span><span class="sxs-lookup"><span data-stu-id="5527f-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![GIF animado de un sistema interactivo de menús holográficos](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="5527f-191">Conceptos principales</span><span class="sxs-lookup"><span data-stu-id="5527f-191">Core concepts</span></span>

<span data-ttu-id="5527f-192">**Seguimiento de la cabeza y seguimiento de los ojos**</span><span class="sxs-lookup"><span data-stu-id="5527f-192">**Head Tracking and Eye Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="5527f-193">**Seguimiento de manos**</span><span class="sxs-lookup"><span data-stu-id="5527f-193">**Hand Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="5527f-194">**Reconocimiento espacial**</span><span class="sxs-lookup"><span data-stu-id="5527f-194">**Spatial Awareness**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="5527f-195">**Marco holográfico**</span><span class="sxs-lookup"><span data-stu-id="5527f-195">**Holographic frame**</span></span>

![GIF animado de un usuario que mira alrededor de la casa de fotos con el marco holográfico resaltado](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="5527f-197">**Sistemas de coordenadas**</span><span class="sxs-lookup"><span data-stu-id="5527f-197">**Coordinate systems**</span></span>

![GIF animado de un usuario que mira alrededor de la coordenada con los sistemas de coordenadas resaltados](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="5527f-199">**Seguimiento de los ojos**</span><span class="sxs-lookup"><span data-stu-id="5527f-199">**Eye tracking**</span></span>

![GIF animado de un usuario que mira hologramas estacionados con el rayo de mirada con los ojos resaltado](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="5527f-201">**Visualización del examen de sala y asignación espacial**</span><span class="sxs-lookup"><span data-stu-id="5527f-201">**Room scan visualization and spatial mapping**</span></span>

![GIF animado de todas las superficies dentro de la casa de seguridad que se está asignando](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="5527f-203">**Descripción de escenas**</span><span class="sxs-lookup"><span data-stu-id="5527f-203">**Scene understanding**</span></span>

![GIF animado de objetos en el centro de reuniones que se reconoce](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="5527f-205">**Apuntar y confirmar con rayos de mano**</span><span class="sxs-lookup"><span data-stu-id="5527f-205">**Point and commit with hand rays**</span></span>

![GIF animado de un usuario que eleva la mano con un rayo de mano resaltado](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="5527f-207">Momentos de "Pruébalo"</span><span class="sxs-lookup"><span data-stu-id="5527f-207">"Try it out" moments</span></span>

<span data-ttu-id="5527f-208">El diseño de hologramas enseña conceptos de realidad mixta, pero también permite probarlos en su habitación.</span><span class="sxs-lookup"><span data-stu-id="5527f-208">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="5527f-209">Después de algunas de esas explicaciones, se pone en pausa y se sale de la casa de la cocina y se entra en un momento interactivo.</span><span class="sxs-lookup"><span data-stu-id="5527f-209">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="5527f-210">Estos son algunos ejemplos de esos momentos interactivos:</span><span class="sxs-lookup"><span data-stu-id="5527f-210">Here are some examples of those interactive moments:</span></span>

![GIF animado del marco de seguimiento de manos que muestra cuándo se detectan las manos y cuándo entran en el campo de vista](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="5527f-212">*El marco de seguimiento de manos que muestra cuándo se detectan las manos y cuándo entran en el campo de vista.*</span><span class="sxs-lookup"><span data-stu-id="5527f-212">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![GIF animado de interacción con cristales en colisión a través de la interacción lejana](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="5527f-214">*Interacción con cristales en colisión a través de la interacción lejana*</span><span class="sxs-lookup"><span data-stu-id="5527f-214">*Interacting with colliding crystals through far interaction*</span></span>

![GIF animado de exploración de las asequibilidades de interacción cercana](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="5527f-216">*Exploración de las asequibilidades de interacción cercanas*</span><span class="sxs-lookup"><span data-stu-id="5527f-216">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="5527f-217">Acerca del equipo</span><span class="sxs-lookup"><span data-stu-id="5527f-217">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="5527f-218"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="5527f-218"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="5527f-219"><i>Diseñador técnico de cliente potencial</i></span><span class="sxs-lookup"><span data-stu-id="5527f-219"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="5527f-220">Dan es el director creativo de Diseño de hologramas y actualmente trabaja como responsable de diseño de la Academia Mixed Reality de Microsoft en San Francisco y anteriormente fue diseñador en uno de los estudios de Mixed Reality de Microsoft en Londres.</span><span class="sxs-lookup"><span data-stu-id="5527f-220">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="5527f-221"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="5527f-221"><b>Martin Wettig</b></span></span><br><span data-ttu-id="5527f-222"><i>Senior 3D Artist</i></span><span class="sxs-lookup"><span data-stu-id="5527f-222"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="5527f-223">Martin dirige 3D Art and UI Design on Designing Holograms (Diseño de hologramas en 3D Art y UI Designing Holograms) y anteriormente fue un autor sénior en 3D en uno de los estudios Mixed Reality De Microsoft en Alemania.</span><span class="sxs-lookup"><span data-stu-id="5527f-223">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="5527f-224">Un enorme gracias al equipo de diseño de Mixed Reality por compartir tantos conocimientos y a la increíble gente de Teoría de objetos por ser compañeros de equipo esenciales en cada paso del proyecto. [](https://objecttheory.com/)</span><span class="sxs-lookup"><span data-stu-id="5527f-224">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="5527f-225">Gracias a todos por su increíble actor, por su pasión y un ojo excepcional por el diseño.</span><span class="sxs-lookup"><span data-stu-id="5527f-225">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5527f-226">Descarga de la aplicación Diseño de hologramas</span><span class="sxs-lookup"><span data-stu-id="5527f-226">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)