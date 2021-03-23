---
title: 3. Configuración del proyecto para la realidad mixta
description: Parte 3 de 6 de una serie de tutoriales para compilar una aplicación de ajedrez con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 26bb874578e56b21d319741b8b1c1ff6decebe4b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609706"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="42180-104">3. Configuración del proyecto para la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="42180-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="42180-105">En el tutorial anterior, ha dedicado tiempo a configurar el proyecto de aplicación de ajedrez.</span><span class="sxs-lookup"><span data-stu-id="42180-105">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="42180-106">En esta sección se le guiará en la configuración de la aplicación para el desarrollo de realidad mixta, lo que significa la adición de una sesión de AR.</span><span class="sxs-lookup"><span data-stu-id="42180-106">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="42180-107">Usará un recurso de datos ARSessionConfig para esta tarea, que dispone de opciones útiles de AR, como el mapeo espacial y la oclusión.</span><span class="sxs-lookup"><span data-stu-id="42180-107">You'll be using an ARSessionConfig data asset for this task, which has useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="42180-108">Puede encontrar más detalles sobre el recurso [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) y la clase [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) en la documentación de Unreal.</span><span class="sxs-lookup"><span data-stu-id="42180-108">You can find more details about the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class in Unreal's documentation.</span></span>

## <a name="objectives"></a><span data-ttu-id="42180-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="42180-109">Objectives</span></span>

* <span data-ttu-id="42180-110">Trabajo con la configuración de AR de Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="42180-110">Working with Unreal Engine's AR settings</span></span>
* <span data-ttu-id="42180-111">Uso de un recurso de datos ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="42180-111">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="42180-112">Configuración de un peón y el modo de juego</span><span class="sxs-lookup"><span data-stu-id="42180-112">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="42180-113">Adición del recurso de sesión</span><span class="sxs-lookup"><span data-stu-id="42180-113">Adding the session asset</span></span>

<span data-ttu-id="42180-114">Las sesiones de AR en Unreal no aparecen por sí mismas.</span><span class="sxs-lookup"><span data-stu-id="42180-114">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="42180-115">Para usar una sesión, necesita un recurso de datos ARSessionConfig con el que trabajar, que será la tarea siguiente:</span><span class="sxs-lookup"><span data-stu-id="42180-115">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="42180-116">Haga clic en **Add New > Miscellaneous > Data Asset** (Agregar nuevo > Varios > Recursos de datos) en **Content Browser** (Explorador de contenido).</span><span class="sxs-lookup"><span data-stu-id="42180-116">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="42180-117">Asegúrese de que se encuentra en el nivel raíz de la carpeta **Content** (Contenido).</span><span class="sxs-lookup"><span data-stu-id="42180-117">Make sure you're at the root **Content** folder level.</span></span>
    * <span data-ttu-id="42180-118">Seleccione **ARSessionConfig**, haga clic en **Select** (Seleccionar) y asigne al recurso el nombre **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="42180-118">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Crear un recurso de datos](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="42180-120">Haga doble clic en **ARSessionConfig** para abrirlo, deje la configuración predeterminada y haga clic en **Save** (Guardar).</span><span class="sxs-lookup"><span data-stu-id="42180-120">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="42180-121">Vuelve a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="42180-121">Return to the Main window.</span></span>

![Configuración de sesión de AR](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="42180-123">Una vez hecho esto, el paso siguiente consiste en asegurarse de que la sesión de AR se inicia y se detiene cuando el nivel se carga y finaliza.</span><span class="sxs-lookup"><span data-stu-id="42180-123">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="42180-124">Por suerte, Unreal tiene un plano técnico especial denominado **Plano técnico de nivel** que actúa como un gráfico de eventos global de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="42180-124">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="42180-125">La conexión del recurso ARSessionConfig en **Level Blueprint** (Plano técnico de nivel) garantiza que la sesión de AR se activará cuando se inicie la reproducción del juego.</span><span class="sxs-lookup"><span data-stu-id="42180-125">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="42180-126">Haga clic en **Blueprints > Open Level Blueprint** (Planos técnicos > Abrir plano técnico de nivel) en la barra de herramientas del editor:</span><span class="sxs-lookup"><span data-stu-id="42180-126">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span>

![Abrir plano técnico de nivel](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="42180-128">Arrastre el nodo de ejecución (icono de flecha hacia la izquierda) **Evento BeginPlay**, suéltelo y, a continuación, busque el nodo **Iniciar sesión de AR** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="42180-128">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release, then search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="42180-129">Haga clic en la lista desplegable **Select Asset** (Seleccionar recurso) en **Session Config** (Configuración de sesión) y elija el recurso **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="42180-129">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span>

![Iniciar sesión de AR](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="42180-131">Haga clic con el botón derecho en EventGraph y cree un nuevo nodo **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="42180-131">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="42180-132">Arrastre la chincheta de ejecución,suéltela y, a continuación, busque el nodo **Detener sesión de AR** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="42180-132">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="42180-133">Si la sesión de AR aún está en ejecución cuando el nivel finaliza, algunas características pueden dejar de funcionar si reinicia la aplicación durante el streaming a un casco de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="42180-133">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>
    * <span data-ttu-id="42180-134">Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="42180-134">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Detener sesión de AR](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="42180-136">Creación de un peón</span><span class="sxs-lookup"><span data-stu-id="42180-136">Create a Pawn</span></span>

<span data-ttu-id="42180-137">En este punto, el proyecto todavía necesita un objeto que sea el jugador.</span><span class="sxs-lookup"><span data-stu-id="42180-137">At this point, the project still needs a player object.</span></span> <span data-ttu-id="42180-138">En Unreal, **Pawn** (Peón) representa al usuario del juego; pero, en este caso, será la experiencia de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="42180-138">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="42180-139">Haga clic en **Add New > Blueprint Class** (Agregar nuevo > Clase de plano técnico) en la carpeta **Content** (Contenido) y expanda la sección **All Classes** (Todas las clases) en la parte inferior.</span><span class="sxs-lookup"><span data-stu-id="42180-139">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span>
    * <span data-ttu-id="42180-140">Busque **DefaultPawn**, haga clic en **Select** (Seleccionar), asígnele el nombre **MRPawn** y haga doble clic en el recurso para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="42180-140">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span>

![Crear un nuevo peón que herede de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

2. <span data-ttu-id="42180-142">Haga clic en **Add Component > Camera**  (Agregar componente > Cámara) en el panel **Components** (Componentes) y asígnele el nombre **Camera**.</span><span class="sxs-lookup"><span data-stu-id="42180-142">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="42180-143">Asegúrese de que el componente **Camera** (Cámara) sea un elemento secundario directo del elemento raíz (**CollisionComponent**).</span><span class="sxs-lookup"><span data-stu-id="42180-143">Make sure that the **Camera** component is a direct child of the root (**CollisionComponent**).</span></span> <span data-ttu-id="42180-144">Esto permite que la cámara del reproductor se mueva con el dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="42180-144">This allows the player camera to move with the HoloLens 2 device.</span></span>

> [!NOTE]
> <span data-ttu-id="42180-145">De forma predeterminada, los peones tienen componentes de malla y colisión.</span><span class="sxs-lookup"><span data-stu-id="42180-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="42180-146">En la mayoría de los proyectos de Unreal, los peones son objetos sólidos que pueden colisionar con otros componentes.</span><span class="sxs-lookup"><span data-stu-id="42180-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="42180-147">Dado que el peón y el usuario son los mismos en la realidad mixta, querrá poder pasar a través de hologramas sin colisiones.</span><span class="sxs-lookup"><span data-stu-id="42180-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span>

3. <span data-ttu-id="42180-148">Seleccione **CollisionComponent** en el panel **Components** (Componentes) y desplácese hacia abajo hasta la sección **Collision** (Colisión) del panel **Details** (Detalles).</span><span class="sxs-lookup"><span data-stu-id="42180-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span>
    * <span data-ttu-id="42180-149">Haga clic en la lista desplegable **Collision Presets** (Valores preestablecidos de colisión) y cambie el valor a **NoCollision**.</span><span class="sxs-lookup"><span data-stu-id="42180-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span>
    * <span data-ttu-id="42180-150">Haga lo mismo con **MeshComponent**.</span><span class="sxs-lookup"><span data-stu-id="42180-150">Do the same for the **MeshComponent**</span></span>

![Ajustar los valores preestablecidos de colisión del peón](images/unreal-uxt/3-nocollision.PNG)

4. <span data-ttu-id="42180-152">**Compile** y **guarde** el plano técnico.</span><span class="sxs-lookup"><span data-stu-id="42180-152">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="42180-153">Con el trabajo que ha realizado aquí, vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="42180-153">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="42180-154">Creación de un modo de juego</span><span class="sxs-lookup"><span data-stu-id="42180-154">Create a Game Mode</span></span>

<span data-ttu-id="42180-155">La última pieza del rompecabezas de la configuración de la realidad mixta es el modo de juego.</span><span class="sxs-lookup"><span data-stu-id="42180-155">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="42180-156">El modo de juego determina una serie de opciones de configuración para el juego o la experiencia, incluido el peón predeterminado que se usará.</span><span class="sxs-lookup"><span data-stu-id="42180-156">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="42180-157">Haga clic en **Agregar nuevo > Clase de plano técnico** en la carpeta **Contenido** y seleccione **Base de modo de juego** como clase primaria.</span><span class="sxs-lookup"><span data-stu-id="42180-157">Click **Add New > Blueprint Class** in the **Content** folder and select **Game Mode Base** as the parent class.</span></span> <span data-ttu-id="42180-158">Asígnele el nombre **MRGameMode** y haga doble clic en él para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="42180-158">Name it **MRGameMode** and double-click to open.</span></span>

![MRGameMode en el explorador de contenido](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="42180-160">Vaya a la sección **Classes** (Clases) en el panel **Details** (Detalles) y cambie **Default Pawn Class** (Clase de peón predeterminado) a **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="42180-160">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span>
    * <span data-ttu-id="42180-161">Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="42180-161">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Establecer la clase de peón predeterminada](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="42180-163">Seleccione **Edit > Projects Settings** (Editar > Configuración de proyectos) y haga clic en **Maps & Modes** (Mapas y modos) en la lista de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="42180-163">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span>
    * <span data-ttu-id="42180-164">Expanda **Default Modes** (Modos predeterminados) y cambie **Default Game Mode** (Modo de juego predeterminado) a **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="42180-164">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span>
    * <span data-ttu-id="42180-165">Expanda **Default Maps** (Mapas predeterminados) y cambie **EditorStartupMap** y **GameDefaultMap** a **Main** (Principal).</span><span class="sxs-lookup"><span data-stu-id="42180-165">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="42180-166">Cuando cierre el editor y vuelva a abrirlo o cuando juegue una partida, se seleccionará el mapa principal de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="42180-166">When you close and reopen the editor or play the game, the Main map will now be selected by default.</span></span>

![Configuración del proyecto: mapas y modos](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="42180-168">Una vez que el proyecto se haya configurado completamente para la realidad mixta, está listo para pasar al siguiente tutorial y empezar a agregar datos proporcionados por el usuario a la escena.</span><span class="sxs-lookup"><span data-stu-id="42180-168">With the project fully set up for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span>

[<span data-ttu-id="42180-169">Sección siguiente: 4. Creación de escenas interactivas</span><span class="sxs-lookup"><span data-stu-id="42180-169">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
