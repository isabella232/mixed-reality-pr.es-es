---
title: Creación de la primera aplicación de Unreal para HoloLens
description: Aprenda a configurar correctamente un proyecto de Unreal con objetos de escena e interacciones de entrada para el desarrollo de realidad mixta de HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal editor, UE4, HoloLens, HoloLens 2, mixed reality, development, documentation, guides, features, mixed reality headset, windows mixed reality headset, virtual reality headset, porting, upgrading
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421434"
---
# <a name="creating-your-first-hololens-unreal-application"></a><span data-ttu-id="9b835-104">Creación de la primera aplicación de Unreal para HoloLens</span><span class="sxs-lookup"><span data-stu-id="9b835-104">Creating your first HoloLens Unreal application</span></span>

<span data-ttu-id="9b835-105">Esta guía le guiará por el proceso para poner en ejecución su primera aplicación de Mixed Reality en HoloLens con Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="9b835-105">This guide will walk you through getting your first Mixed Reality app running on the HoloLens in Unreal Engine.</span></span> <span data-ttu-id="9b835-106">Siguiendo la tradición de "Hola mundo", creará una aplicación sencilla que muestra un cubo en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="9b835-106">In the tradition of "Hello World", you'll create a simple app that displays a cube on the screen.</span></span> <span data-ttu-id="9b835-107">Para que le resulte más útil, también creará el primer gesto para girar el cubo y salir de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9b835-107">To make it more useful, you'll also create your first gesture to rotate the cube and quit the application.</span></span> 

## <a name="objectives"></a><span data-ttu-id="9b835-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9b835-108">Objectives</span></span>

* <span data-ttu-id="9b835-109">Iniciar un proyecto de HoloLens</span><span class="sxs-lookup"><span data-stu-id="9b835-109">Start a HoloLens Project</span></span>
* <span data-ttu-id="9b835-110">Habilitar los complementos correctos</span><span class="sxs-lookup"><span data-stu-id="9b835-110">Enable the correct plugins</span></span>
* <span data-ttu-id="9b835-111">Crear un recurso de datos ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="9b835-111">Create an ARSessionConfig Data Asset</span></span>
* <span data-ttu-id="9b835-112">Configurar entradas de gestos</span><span class="sxs-lookup"><span data-stu-id="9b835-112">Set up gesture inputs</span></span>
* <span data-ttu-id="9b835-113">Crear un nivel básico</span><span class="sxs-lookup"><span data-stu-id="9b835-113">Build a basic level</span></span>
* <span data-ttu-id="9b835-114">Implementar un gesto de reducir</span><span class="sxs-lookup"><span data-stu-id="9b835-114">Implement a pinch gesture</span></span>

## <a name="creating-a-new-project"></a><span data-ttu-id="9b835-115">Creación de un nuevo proyecto</span><span class="sxs-lookup"><span data-stu-id="9b835-115">Creating a new project</span></span>

<span data-ttu-id="9b835-116">Lo primero que necesita es un proyecto con el que trabajar.</span><span class="sxs-lookup"><span data-stu-id="9b835-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="9b835-117">Si es la primera vez que desarrolla una aplicación para Unreal, deberá [descargar los archivos auxiliares](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) desde el iniciador de Epic.</span><span class="sxs-lookup"><span data-stu-id="9b835-117">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="9b835-118">Iniciar Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="9b835-118">Launch Unreal Engine</span></span>
2. <span data-ttu-id="9b835-119">En **New Project Categories** (Nuevas categorías de proyecto), seleccione **Games** (Juegos) y haga clic en **Next** (Siguiente).</span><span class="sxs-lookup"><span data-stu-id="9b835-119">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Ventana de proyectos recientes abierta con juegos resaltados](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="9b835-121">Seleccione una plantilla **Blank** (En blanco) y haga clic en **Next** (Siguiente):</span><span class="sxs-lookup"><span data-stu-id="9b835-121">Select the **Blank** template and click **Next**:</span></span>

![Ventana del explorador de proyectos de Unreal con plantilla en blanco resaltada](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="9b835-123">En **Project Settings** (Configuración del proyecto), defina **C++, Scalable 3D or 2D, Mobile/Tablet** (C++, 3D o 2D escalable, móvil/tableta) y **No Starter Content** (Sin contenido de inicio). A continuación, elija una ubicación para guardar y haga clic en **Create Project** (Crear proyecto).</span><span class="sxs-lookup"><span data-stu-id="9b835-123">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] 
> <span data-ttu-id="9b835-124">Está usando un C++ en lugar de un proyecto de plano técnico para estar listo para usar el complemento OpenXR más adelante.</span><span class="sxs-lookup"><span data-stu-id="9b835-124">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="9b835-125">En esta guía de inicio rápido se usa el complemento de OpenXR predeterminado que viene con Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="9b835-125">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="9b835-126">Sin embargo, se recomienda descargar y usar el complemento oficial OpenXR de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b835-126">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="9b835-127">Esto requiere que el proyecto sea un proyecto de C++.</span><span class="sxs-lookup"><span data-stu-id="9b835-127">That requires the project to be a C++ project.</span></span>

![Ventana de configuración del proyecto con las opciones de proyecto, rendimiento, plataforma de destino y contenido de inicio resaltadas](images/unreal-quickstart-img-03.png)

<span data-ttu-id="9b835-129">El nuevo proyecto deberá abrirse automáticamente en el editor de Unreal, lo que significa que está listo para la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="9b835-129">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="9b835-130">Habilitación de los complementos necesarios</span><span class="sxs-lookup"><span data-stu-id="9b835-130">Enabling required plugins</span></span>

<span data-ttu-id="9b835-131">Deberá habilitar dos complementos antes de empezar a agregar objetos a la escena.</span><span class="sxs-lookup"><span data-stu-id="9b835-131">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="9b835-132">Abra **Edit > Plugins** (Editar > Complementos) y seleccione **Augmented Reality** (Realidad aumentada) en la lista opciones integradas.</span><span class="sxs-lookup"><span data-stu-id="9b835-132">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="9b835-133">Desplácese hacia abajo hasta **HoloLens** y marque **Enabled** (Habilitado).</span><span class="sxs-lookup"><span data-stu-id="9b835-133">Scroll down to **HoloLens** and check **Enabled**</span></span>

![Ventana de complementos con la sección de realidad aumentada abierta y HoloLens resaltado](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="9b835-135">Escriba **OpenXR** en el cuadro de búsqueda de la parte superior derecha y habilite los complementos **OpenXR** y **OpenXRMsftHandInteraction**:</span><span class="sxs-lookup"><span data-stu-id="9b835-135">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Ventana de complementos con OpenXR habilitado](images/unreal-quickstart-img-05.jpg)

![Ventana de complementos con Open XR Msft Hand Interaction habilitado](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="9b835-138">Reiniciar el editor</span><span class="sxs-lookup"><span data-stu-id="9b835-138">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="9b835-139">En este tutorial se usa OpenXR, pero los dos complementos que ha instalado anteriormente no proporcionan, actualmente, el conjunto completo de características para el desarrollo de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9b835-139">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="9b835-140">El complemento HandInteraction será suficiente para el gesto de "reducir" que usará más adelante, pero, si quiere ir más allá de los aspectos básicos, necesitará [descargar el complemento OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="9b835-140">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="9b835-141">Con los complementos habilitados, puede centrarse en llenarlos de contenido.</span><span class="sxs-lookup"><span data-stu-id="9b835-141">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="9b835-142">Creación de un nivel</span><span class="sxs-lookup"><span data-stu-id="9b835-142">Creating a level</span></span>

<span data-ttu-id="9b835-143">La siguiente tarea consiste en crear una configuración de un jugador con un punto inicial y un cubo para referencia y escala.</span><span class="sxs-lookup"><span data-stu-id="9b835-143">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="9b835-144">Seleccione **File > New Level** (Archivo > Nuevo nivel) y elija **Empty Level** (Nivel vacío).</span><span class="sxs-lookup"><span data-stu-id="9b835-144">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="9b835-145">Ahora, la escena predeterminada en la ventanilla debería estar vacía.</span><span class="sxs-lookup"><span data-stu-id="9b835-145">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="9b835-146">En la pestaña **Modes** (Modos), seleccione **Basic** (Básico) y arrastre **PlayerStart** a la escena.</span><span class="sxs-lookup"><span data-stu-id="9b835-146">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="9b835-147">En la pestaña **Details** (Detalles), defina **Location** (Ubicación) en **X = 0, Y = 0,** and **Z = 0** para situar al usuario en el centro de la escena al iniciar la aplicación</span><span class="sxs-lookup"><span data-stu-id="9b835-147">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Escena del editor de Unreal con la ubicación y el inicio del jugador agregados](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="9b835-149">Desde la pestaña **Basic** (Básico), arrastre un elemento **Cube** (Cubo) a la escena.</span><span class="sxs-lookup"><span data-stu-id="9b835-149">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="9b835-150">Establezca **Location** (Ubicación) en **X = 50, Y = 0** y **Z = 0** para situar el cubo a 50 cm del jugador al principio</span><span class="sxs-lookup"><span data-stu-id="9b835-150">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="9b835-151">Cambie el valor de **Scale** (Escala) del cubo a **X = 0,2, Y = 0,2** y **Z = 0,2**</span><span class="sxs-lookup"><span data-stu-id="9b835-151">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="9b835-152">No podrá ver el cubo a menos que agregue una luz a la escena, que es la última tarea antes de probar la escena.</span><span class="sxs-lookup"><span data-stu-id="9b835-152">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="9b835-153">En el panel **Modes** (Modos), cambie a la pestaña **Lights** (Luces) y arrastre una **Directional Light** (Luz direccional) a la escena.</span><span class="sxs-lookup"><span data-stu-id="9b835-153">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="9b835-154">Coloque la luz sobre **PlayerStart** para que pueda verlo.</span><span class="sxs-lookup"><span data-stu-id="9b835-154">Position the light above **PlayerStart** so you can see it</span></span>

![Escena del editor de Unreal con un cubo y luz direccional agregada](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="9b835-156">Vaya a **File > Save Current** (Archivo > Guardar actual), asigne al nivel el nombre **Main** (Principal) y seleccione **Save** (Guardar).</span><span class="sxs-lookup"><span data-stu-id="9b835-156">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="9b835-157">Con la escena definida, presione **Play** (Jugar) en la barra de herramientas para ver el cubo en acción.</span><span class="sxs-lookup"><span data-stu-id="9b835-157">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="9b835-158">Cuando haya terminado de admirar su trabajo, presione Esc para detener la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9b835-158">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Escena en modo de juego con el cubo en el medio de la pantalla](images/unreal-quickstart-img-09.png)

<span data-ttu-id="9b835-160">Ahora que la escena está configurada, preparémosla para algunas interacciones básicas en AR.</span><span class="sxs-lookup"><span data-stu-id="9b835-160">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="9b835-161">En primer lugar, debe crear una sesión de AR y puede agregar planos técnicos para habilitar la interacción con la mano.</span><span class="sxs-lookup"><span data-stu-id="9b835-161">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="9b835-162">Adición de un recurso de sesión</span><span class="sxs-lookup"><span data-stu-id="9b835-162">Adding a session asset</span></span>

<span data-ttu-id="9b835-163">Las sesiones de AR en Unreal no aparecen por sí mismas.</span><span class="sxs-lookup"><span data-stu-id="9b835-163">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="9b835-164">Para usar una sesión, necesita un recurso de datos ARSessionConfig con el que trabajar, que será la tarea siguiente:</span><span class="sxs-lookup"><span data-stu-id="9b835-164">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="9b835-165">En el **explorador de contenido**, seleccione **Add New > Miscellaneous > Data Asset** (Agregar nuevo > Varios > Recurso de datos) y asegúrese de estar en el nivel de la carpeta Content (Contenido)</span><span class="sxs-lookup"><span data-stu-id="9b835-165">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="9b835-166">Seleccione **ARSessionConfig**, haga clic en **Select** (Seleccionar) y asigne al recurso el nombre **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="9b835-166">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Ventana Pick data asset class (Seleccionar clase de recurso de datos) abierta con el recurso de configuración de sesión de AR resaltado](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="9b835-168">Haga doble clic en **ARSessionConfig** para abrirlo, seleccione **Save** (Guardar) con todas las opciones predeterminadas y vuelva a la ventana principal:</span><span class="sxs-lookup"><span data-stu-id="9b835-168">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Ventana de detalles del recurso de configuración de sesión de AR](images/unreal-quickstart-img-11.png)

<span data-ttu-id="9b835-170">Una vez hecho esto, el paso siguiente consiste en asegurarse de que la sesión de AR se inicia y se detiene cuando el nivel se carga y finaliza.</span><span class="sxs-lookup"><span data-stu-id="9b835-170">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="9b835-171">Por suerte, Unreal tiene un plano técnico especial denominado **Plano técnico de nivel** que actúa como un gráfico de eventos global de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="9b835-171">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="9b835-172">La conexión del recurso ARSessionConfig en Level Blueprint (Plano técnico de nivel) garantiza que la sesión de AR se activará cuando se inicie la reproducción del juego.</span><span class="sxs-lookup"><span data-stu-id="9b835-172">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="9b835-173">Desde la barra de herramientas del editor, seleccione **Blueprints > Open Level Blueprint** (Planos técnicos > Abrir plano técnico de nivel):</span><span class="sxs-lookup"><span data-stu-id="9b835-173">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Menú de plano técnico abierto con opción para abrir plano técnico de nivel resaltada](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="9b835-175">Arrastre el nodo de ejecución (icono de flecha hacia la izquierda) fuera de **Event BeginPlay** (Evento BeginPlay) y suéltelo.</span><span class="sxs-lookup"><span data-stu-id="9b835-175">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="9b835-176">Busque el nodo **Start AR Session** (Iniciar sesión de AR) y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="9b835-176">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="9b835-177">Haga clic en la lista desplegable **Select Asset** (Seleccionar recurso) en **Session Config** (Configuración de sesión) y elija el recurso **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="9b835-177">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Gráfico del plano técnico con el evento BeginPlay conectado a la función de inicio de sesión de AR](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="9b835-179">Haga clic con el botón derecho en EventGraph y cree un nuevo nodo **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="9b835-179">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="9b835-180">Arrastre el marcador de ejecución,suéltelo y, a continuación, busque el nodo **Detener sesión de AR** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="9b835-180">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="9b835-181">Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="9b835-181">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9b835-182">Si la sesión de AR aún está en ejecución cuando el nivel finaliza, algunas características pueden dejar de funcionar si reinicia la aplicación durante el streaming a un casco de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="9b835-182">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Nodo de juego final de evento asociado a la función de detención de sesión de AR](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="9b835-184">Configuración de entradas</span><span class="sxs-lookup"><span data-stu-id="9b835-184">Setting up inputs</span></span>

1. <span data-ttu-id="9b835-185">Seleccione **Edit > Project Settings** (Editar > Configuración del proyecto) y vaya a **Engine > Input** (Motor > Entrada).</span><span class="sxs-lookup"><span data-stu-id="9b835-185">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="9b835-186">Seleccione el icono **+** junto a **Action Mappings** (Asignaciones de acciones) y cree las acciones **RightPinch** y **LeftPinch**:</span><span class="sxs-lookup"><span data-stu-id="9b835-186">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Configuración de entrada de enlace con las asignaciones de acción de reducción derecha e izquierda resaltadas](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="9b835-188">Asigne las acciones **RightPinch** y **LeftPinch** a las respectivas acciones de **OpenXR Msft Hand Interaction**:</span><span class="sxs-lookup"><span data-stu-id="9b835-188">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Asignaciones de acciones con las opciones de Open XR Msft Hand interaction resaltadas](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a><span data-ttu-id="9b835-190">Configuración de gestos</span><span class="sxs-lookup"><span data-stu-id="9b835-190">Setting up gestures</span></span>

<span data-ttu-id="9b835-191">Ahora que hemos configurado las entradas, pasaremos a la parte emocionante: la incorporación de gestos.</span><span class="sxs-lookup"><span data-stu-id="9b835-191">Now that we have setup the inputs, we can get to the exciting part: Adding gestures!</span></span> <span data-ttu-id="9b835-192">Vamos a girar el cubo con el gesto de reducir de la mano derecha y saldremos de la aplicación con el gesto de reducir de la mano izquierda.</span><span class="sxs-lookup"><span data-stu-id="9b835-192">Lets rotate the cube on the right pinch and quit the application on left pinch.</span></span>

1. <span data-ttu-id="9b835-193">Abra el elemento **Level Blueprint** (Plano técnico de nivel) y agregue las acciones **InputAction RightPinch** y **InputAction LeftPinch**.</span><span class="sxs-lookup"><span data-stu-id="9b835-193">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="9b835-194">Conecte el evento de reducción derecha a **AddActorLocalRotation** con el elemento **Cube** (Cubo) como destino y el valor de **Delta Rotation** (Rotación diferencial) definido como **X = 0, Y = 0** y **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="9b835-194">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="9b835-195">Ahora, el cubo girará 20 grados cada vez que se realice el gesto de reducir</span><span class="sxs-lookup"><span data-stu-id="9b835-195">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="9b835-196">Conectar el evento de reducción izquierda a **Quit Game** (Salir del juego)</span><span class="sxs-lookup"><span data-stu-id="9b835-196">Connect the left pinch event to **Quit Game**</span></span>

![Deje el plano técnico de nivel abierto con acciones de entrada para eventos de reducción izquierda y derecha.](images/unreal-quickstart-img-17.jpg)

2. <span data-ttu-id="9b835-198">En la configuración de **Transform** (Transformación) del cubo, establezca **Mobility** (Movilidad) como **Movable** (Móvil) para que se pueda mover de forma dinámica:</span><span class="sxs-lookup"><span data-stu-id="9b835-198">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Configuración de transformación con la propiedad de movilidad resaltada](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="9b835-200">En este punto, estará listo para implementar y probar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9b835-200">At this point, you're ready to deploy and test the application!</span></span>