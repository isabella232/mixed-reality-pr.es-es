---
title: Creación de un proyecto de HoloLens
description: Aprenda a configurar correctamente un proyecto de Unreal con objetos de escena e interacciones de entrada para el desarrollo de realidad mixta de HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal editor, UE4, HoloLens, HoloLens 2, mixed reality, development, documentation, guides, features, mixed reality headset, windows mixed reality headset, virtual reality headset, porting, upgrading
ms.openlocfilehash: 3b2b88ac897a8791fec1ca2942d0db34efcee598
ms.sourcegitcommit: be33fcda10d1cb98df90b428a923289933d42c77
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2021
ms.locfileid: "98672742"
---
# <a name="creating-a-hololens-project"></a><span data-ttu-id="8f4a3-104">Creación de un proyecto de HoloLens</span><span class="sxs-lookup"><span data-stu-id="8f4a3-104">Creating a HoloLens project</span></span>

<span data-ttu-id="8f4a3-105">Lo primero que necesita es un proyecto con el que trabajar.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-105">The first thing you need is a project to work with.</span></span> <span data-ttu-id="8f4a3-106">Si es la primera vez que desarrolla una aplicación para Unreal, deberá [descargar los archivos auxiliares](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) desde el iniciador de Epic.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-106">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="8f4a3-107">Iniciar Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="8f4a3-107">Launch Unreal Engine</span></span>
2. <span data-ttu-id="8f4a3-108">En **New Project Categories** (Nuevas categorías de proyecto), seleccione **Games** (Juegos) y haga clic en **Next** (Siguiente).</span><span class="sxs-lookup"><span data-stu-id="8f4a3-108">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Ventana de proyectos recientes abierta con juegos resaltados](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="8f4a3-110">Seleccione una plantilla **Blank** (En blanco) y haga clic en **Next** (Siguiente):</span><span class="sxs-lookup"><span data-stu-id="8f4a3-110">Select the **Blank** template and click **Next**:</span></span>

![Ventana del explorador de proyectos de Unreal con plantilla en blanco resaltada](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="8f4a3-112">En **Project Settings** (Configuración del proyecto), defina **C++, Scalable 3D or 2D, Mobile/Tablet** (C++, 3D o 2D escalable, móvil/tableta) y **No Starter Content** (Sin contenido de inicio). A continuación, elija una ubicación para guardar y haga clic en **Create Project** (Crear proyecto).</span><span class="sxs-lookup"><span data-stu-id="8f4a3-112">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] <span data-ttu-id="8f4a3-113">Está usando un C++ en lugar de un proyecto de plano técnico para estar listo para usar el complemento OpenXR más adelante.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-113">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="8f4a3-114">En esta guía de inicio rápido se usa el complemento de OpenXR predeterminado que viene con Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-114">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="8f4a3-115">Sin embargo, se recomienda descargar y usar el complemento oficial OpenXR de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-115">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="8f4a3-116">Esto requiere que el proyecto sea un proyecto de C++.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-116">That requires the project to be a C++ project.</span></span>

![Ventana de configuración del proyecto con las opciones de proyecto, rendimiento, plataforma de destino y contenido de inicio resaltadas](images/unreal-quickstart-img-03.png)

<span data-ttu-id="8f4a3-118">El nuevo proyecto deberá abrirse automáticamente en el editor de Unreal, lo que significa que está listo para la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-118">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="8f4a3-119">Habilitación de los complementos necesarios</span><span class="sxs-lookup"><span data-stu-id="8f4a3-119">Enabling required plugins</span></span>

<span data-ttu-id="8f4a3-120">Deberá habilitar dos complementos antes de empezar a agregar objetos a la escena.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-120">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="8f4a3-121">Abra **Edit > Plugins** (Editar > Complementos) y seleccione **Augmented Reality** (Realidad aumentada) en la lista opciones integradas.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-121">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="8f4a3-122">Desplácese hacia abajo hasta **HoloLens** y marque **Enabled** (Habilitado).</span><span class="sxs-lookup"><span data-stu-id="8f4a3-122">Scroll down to **HoloLens** and check **Enabled**</span></span>

![Ventana de complementos con la sección de realidad aumentada abierta y HoloLens resaltado](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="8f4a3-124">Escriba **OpenXR** en el cuadro de búsqueda de la parte superior derecha y habilite los complementos **OpenXR** y **OpenXRMsftHandInteraction**:</span><span class="sxs-lookup"><span data-stu-id="8f4a3-124">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Ventana de complementos con OpenXR habilitado](images/unreal-quickstart-img-05.jpg)

![Ventana de complementos con Open XR Msft Hand Interaction habilitado](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="8f4a3-127">Reiniciar el editor</span><span class="sxs-lookup"><span data-stu-id="8f4a3-127">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="8f4a3-128">En este tutorial se usa OpenXR, pero los dos complementos que ha instalado anteriormente no proporcionan, actualmente, el conjunto completo de características para el desarrollo de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-128">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="8f4a3-129">El complemento HandInteraction será suficiente para el gesto de "reducir" que usará más adelante, pero, si quiere ir más allá de los aspectos básicos, necesitará [descargar el complemento OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="8f4a3-129">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="8f4a3-130">Con los complementos habilitados, puede centrarse en llenarlos de contenido.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-130">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="8f4a3-131">Creación de un nivel</span><span class="sxs-lookup"><span data-stu-id="8f4a3-131">Creating a level</span></span>

<span data-ttu-id="8f4a3-132">La siguiente tarea consiste en crear una configuración de un jugador con un punto inicial y un cubo para referencia y escala.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-132">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="8f4a3-133">Seleccione **File > New Level** (Archivo > Nuevo nivel) y elija **Empty Level** (Nivel vacío).</span><span class="sxs-lookup"><span data-stu-id="8f4a3-133">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="8f4a3-134">Ahora, la escena predeterminada en la ventanilla debería estar vacía.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-134">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="8f4a3-135">En la pestaña **Modes** (Modos), seleccione **Basic** (Básico) y arrastre **PlayerStart** a la escena.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-135">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="8f4a3-136">En la pestaña **Details** (Detalles), defina **Location** (Ubicación) en **X = 0, Y = 0,** and **Z = 0** para situar al usuario en el centro de la escena al iniciar la aplicación</span><span class="sxs-lookup"><span data-stu-id="8f4a3-136">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Escena del editor de Unreal con la ubicación y el inicio del jugador agregados](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="8f4a3-138">Desde la pestaña **Basic** (Básico), arrastre un elemento **Cube** (Cubo) a la escena.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-138">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="8f4a3-139">Establezca **Location** (Ubicación) en **X = 50, Y = 0** y **Z = 0** para situar el cubo a 50 cm del jugador al principio</span><span class="sxs-lookup"><span data-stu-id="8f4a3-139">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="8f4a3-140">Cambie el valor de **Scale** (Escala) del cubo a **X = 0,2, Y = 0,2** y **Z = 0,2**</span><span class="sxs-lookup"><span data-stu-id="8f4a3-140">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="8f4a3-141">No podrá ver el cubo a menos que agregue una luz a la escena, que es la última tarea antes de probar la escena.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-141">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="8f4a3-142">En el panel **Modes** (Modos), cambie a la pestaña **Lights** (Luces) y arrastre una **Directional Light** (Luz direccional) a la escena.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-142">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="8f4a3-143">Coloque la luz sobre **PlayerStart** para que pueda verlo.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-143">Position the light above **PlayerStart** so you can see it</span></span>

![Escena del editor de Unreal con un cubo y luz direccional agregada](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="8f4a3-145">Vaya a **File > Save Current** (Archivo > Guardar actual), asigne al nivel el nombre **Main** (Principal) y seleccione **Save** (Guardar).</span><span class="sxs-lookup"><span data-stu-id="8f4a3-145">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="8f4a3-146">Con la escena definida, presione **Play** (Jugar) en la barra de herramientas para ver el cubo en acción.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-146">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="8f4a3-147">Cuando haya terminado de admirar su trabajo, presione Esc para detener la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-147">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Escena en modo de juego con el cubo en el medio de la pantalla](images/unreal-quickstart-img-09.png)

<span data-ttu-id="8f4a3-149">Ahora que la escena está configurada, preparémosla para algunas interacciones básicas en AR.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-149">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="8f4a3-150">En primer lugar, debe crear una sesión de AR y puede agregar planos técnicos para habilitar la interacción con la mano.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-150">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="8f4a3-151">Adición de un recurso de sesión</span><span class="sxs-lookup"><span data-stu-id="8f4a3-151">Adding a session asset</span></span>

<span data-ttu-id="8f4a3-152">Las sesiones de AR en Unreal no aparecen por sí mismas.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-152">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="8f4a3-153">Para usar una sesión, necesita un recurso de datos ARSessionConfig con el que trabajar, que será la tarea siguiente:</span><span class="sxs-lookup"><span data-stu-id="8f4a3-153">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="8f4a3-154">En el **explorador de contenido**, seleccione **Add New > Miscellaneous > Data Asset** (Agregar nuevo > Varios > Recurso de datos) y asegúrese de estar en el nivel de la carpeta Content (Contenido)</span><span class="sxs-lookup"><span data-stu-id="8f4a3-154">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="8f4a3-155">Seleccione **ARSessionConfig**, haga clic en **Select** (Seleccionar) y asigne al recurso el nombre **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-155">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Ventana Pick data asset class (Seleccionar clase de recurso de datos) abierta con el recurso de configuración de sesión de AR resaltado](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="8f4a3-157">Haga doble clic en **ARSessionConfig** para abrirlo, seleccione **Save** (Guardar) con todas las opciones predeterminadas y vuelva a la ventana principal:</span><span class="sxs-lookup"><span data-stu-id="8f4a3-157">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Ventana de detalles del recurso de configuración de sesión de AR](images/unreal-quickstart-img-11.png)

<span data-ttu-id="8f4a3-159">Una vez hecho esto, el paso siguiente consiste en asegurarse de que la sesión de AR se inicia y se detiene cuando el nivel se carga y finaliza.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-159">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="8f4a3-160">Por suerte, Unreal tiene un plano técnico especial denominado **Plano técnico de nivel** que actúa como un gráfico de eventos global de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-160">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="8f4a3-161">La conexión del recurso ARSessionConfig en Level Blueprint (Plano técnico de nivel) garantiza que la sesión de AR se activará cuando se inicie la reproducción del juego.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-161">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="8f4a3-162">Desde la barra de herramientas del editor, seleccione **Blueprints > Open Level Blueprint** (Planos técnicos > Abrir plano técnico de nivel):</span><span class="sxs-lookup"><span data-stu-id="8f4a3-162">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Menú de plano técnico abierto con opción para abrir plano técnico de nivel resaltada](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="8f4a3-164">Arrastre el nodo de ejecución (icono de flecha hacia la izquierda) fuera de **Event BeginPlay** (Evento BeginPlay) y suéltelo.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-164">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="8f4a3-165">Busque el nodo **Start AR Session** (Iniciar sesión de AR) y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-165">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="8f4a3-166">Haga clic en la lista desplegable **Select Asset** (Seleccionar recurso) en **Session Config** (Configuración de sesión) y elija el recurso **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-166">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Gráfico del plano técnico con el evento BeginPlay conectado a la función de inicio de sesión de AR](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="8f4a3-168">Haga clic con el botón derecho en EventGraph y cree un nuevo nodo **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-168">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="8f4a3-169">Arrastre el marcador de ejecución,suéltelo y, a continuación, busque el nodo **Detener sesión de AR** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-169">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="8f4a3-170">Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-170">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f4a3-171">Si la sesión de AR aún está en ejecución cuando el nivel finaliza, algunas características pueden dejar de funcionar si reinicia la aplicación durante el streaming a un casco de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-171">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Nodo de juego final de evento asociado a la función de detención de sesión de AR](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="8f4a3-173">Configuración de entradas</span><span class="sxs-lookup"><span data-stu-id="8f4a3-173">Setting up inputs</span></span>

1. <span data-ttu-id="8f4a3-174">Seleccione **Edit > Project Settings** (Editar > Configuración del proyecto) y vaya a **Engine > Input** (Motor > Entrada).</span><span class="sxs-lookup"><span data-stu-id="8f4a3-174">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="8f4a3-175">Seleccione el icono **+** junto a **Action Mappings** (Asignaciones de acciones) y cree las acciones **RightPinch** y **LeftPinch**:</span><span class="sxs-lookup"><span data-stu-id="8f4a3-175">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Configuración de entrada de enlace con las asignaciones de acción de reducción derecha e izquierda resaltadas](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="8f4a3-177">Asigne las acciones **RightPinch** y **LeftPinch** a las respectivas acciones de **OpenXR Msft Hand Interaction**:</span><span class="sxs-lookup"><span data-stu-id="8f4a3-177">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Asignaciones de acciones con las opciones de Open XR Msft Hand interaction resaltadas](images/unreal-quickstart-img-16.jpg)

4. <span data-ttu-id="8f4a3-179">Abra el elemento **Level Blueprint** (Plano técnico de nivel) y agregue las acciones **InputAction RightPinch** y **InputAction LeftPinch**.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-179">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="8f4a3-180">Conecte el evento de reducción derecha a **AddActorLocalRotation** con el elemento **Cube** (Cubo) como destino y el valor de **Delta Rotation** (Rotación diferencial) definido como **X = 0, Y = 0** y **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-180">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="8f4a3-181">Ahora, el cubo girará 20 grados cada vez que se realice el gesto de reducir</span><span class="sxs-lookup"><span data-stu-id="8f4a3-181">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="8f4a3-182">Conectar el evento de reducción izquierda a **Quit Game** (Salir del juego)</span><span class="sxs-lookup"><span data-stu-id="8f4a3-182">Connect the left pinch event to **Quit Game**</span></span>

![Deje el plano técnico de nivel abierto con acciones de entrada para eventos de reducción izquierda y derecha.](images/unreal-quickstart-img-17.jpg)

5. <span data-ttu-id="8f4a3-184">En la configuración de **Transform** (Transformación) del cubo, establezca **Mobility** (Movilidad) como **Movable** (Móvil) para que se pueda mover de forma dinámica:</span><span class="sxs-lookup"><span data-stu-id="8f4a3-184">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Configuración de transformación con la propiedad de movilidad resaltada](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="8f4a3-186">En este punto, está listo para implementar y probar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8f4a3-186">At this point, you're ready to deply and test the application!</span></span>