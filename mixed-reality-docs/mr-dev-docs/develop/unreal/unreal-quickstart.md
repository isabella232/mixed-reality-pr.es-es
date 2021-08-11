---
title: Creación de la primera aplicación de Unreal para HoloLens
description: Aprenda a configurar correctamente un proyecto de Unreal con objetos de escena e interacciones de entrada para el desarrollo de realidad mixta de HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal editor, UE4, HoloLens, HoloLens 2, mixed reality, development, documentation, guides, features, mixed reality headset, windows mixed reality headset, virtual reality headset, porting, upgrading
ms.openlocfilehash: 07ec2760d691938015619d097d214d205cdbab78f250ff9dd8a793dd27f10c4a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209687"
---
# <a name="creating-your-first-hololens-unreal-application"></a>Creación de la primera aplicación de Unreal para HoloLens

Esta guía le guiará por el proceso para poner en ejecución su primera aplicación de Mixed Reality en HoloLens con Unreal Engine. Siguiendo la tradición de "Hola mundo", creará una aplicación sencilla que muestra un cubo en la pantalla. Para que le resulte más útil, también creará el primer gesto para girar el cubo y salir de la aplicación. 

## <a name="objectives"></a>Objetivos

* Iniciar un proyecto de HoloLens
* Habilitar los complementos correctos
* Crear un recurso de datos ARSessionConfig
* Configurar entradas de gestos
* Crear un nivel básico
* Implementar un gesto de reducir

## <a name="creating-a-new-project"></a>Creación de un nuevo proyecto

Lo primero que necesita es un proyecto con el que trabajar. Si es la primera vez que desarrolla una aplicación para Unreal, deberá [descargar los archivos auxiliares](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) desde el iniciador de Epic.

1. Iniciar Unreal Engine
2. En **New Project Categories** (Nuevas categorías de proyecto), seleccione **Games** (Juegos) y haga clic en **Next** (Siguiente).

![Ventana de proyectos recientes abierta con juegos resaltados](images/unreal-quickstart-img-01.png)

3. Seleccione una plantilla **Blank** (En blanco) y haga clic en **Next** (Siguiente):

![Ventana del explorador de proyectos de Unreal con plantilla en blanco resaltada](images/unreal-quickstart-img-02.png)

4. En **Project Settings** (Configuración del proyecto), defina **C++, Scalable 3D or 2D, Mobile/Tablet** (C++, 3D o 2D escalable, móvil/tableta) y **No Starter Content** (Sin contenido de inicio). A continuación, elija una ubicación para guardar y haga clic en **Create Project** (Crear proyecto).

> [!NOTE] 
> Está usando un C++ en lugar de un proyecto de plano técnico para estar listo para usar el complemento OpenXR más adelante. En esta guía de inicio rápido se usa el complemento de OpenXR predeterminado que viene con Unreal Engine. Sin embargo, se recomienda descargar y usar el complemento oficial OpenXR de Microsoft. Esto requiere que el proyecto sea un proyecto de C++.

![Ventana de configuración del proyecto con las opciones de proyecto, rendimiento, plataforma de destino y contenido de inicio resaltadas](images/unreal-quickstart-img-03.png)

El nuevo proyecto deberá abrirse automáticamente en el editor de Unreal, lo que significa que está listo para la sección siguiente.

## <a name="enabling-required-plugins"></a>Habilitación de los complementos necesarios

Deberá habilitar dos complementos antes de empezar a agregar objetos a la escena.

1. Abra **Edit > Plugins** (Editar > Complementos) y seleccione **Augmented Reality** (Realidad aumentada) en la lista opciones integradas.
* Desplácese hacia abajo hasta **HoloLens** y marque **Enabled** (Habilitado).

![Ventana de complementos con la sección de realidad aumentada abierta y HoloLens resaltado](images/unreal-quickstart-img-04.png)

2. Escriba **OpenXR** en el cuadro de búsqueda de la parte superior derecha y habilite los complementos **OpenXR** y **OpenXRMsftHandInteraction**:

![Ventana de complementos con OpenXR habilitado](images/unreal-quickstart-img-05.jpg)

![Ventana de complementos con Open XR Msft Hand Interaction habilitado](images/unreal-quickstart-img-06.jpg)

3. Reiniciar el editor

> [!NOTE]
> En este tutorial se usa OpenXR, pero los dos complementos que ha instalado anteriormente no proporcionan, actualmente, el conjunto completo de características para el desarrollo de HoloLens. El complemento HandInteraction será suficiente para el gesto de "reducir" que usará más adelante, pero, si quiere ir más allá de los aspectos básicos, necesitará [descargar el complemento OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).

Con los complementos habilitados, puede centrarse en llenarlos de contenido.

## <a name="creating-a-level"></a>Creación de un nivel

La siguiente tarea consiste en crear una configuración de un jugador con un punto inicial y un cubo para referencia y escala.

1. Seleccione **File > New Level** (Archivo > Nuevo nivel) y elija **Empty Level** (Nivel vacío). Ahora, la escena predeterminada en la ventanilla debería estar vacía.
2. En la pestaña **Modes** (Modos), seleccione **Basic** (Básico) y arrastre **PlayerStart** a la escena.
* En la pestaña **Details** (Detalles), defina **Location** (Ubicación) en **X = 0, Y = 0,** and **Z = 0** para situar al usuario en el centro de la escena al iniciar la aplicación

![Escena del editor de Unreal con la ubicación y el inicio del jugador agregados](images/unreal-quickstart-img-07.png)

3. Desde la pestaña **Basic** (Básico), arrastre un elemento **Cube** (Cubo) a la escena.
* Establezca **Location** (Ubicación) en **X = 50, Y = 0** y **Z = 0** para situar el cubo a 50 cm del jugador al principio
* Cambie el valor de **Scale** (Escala) del cubo a **X = 0,2, Y = 0,2** y **Z = 0,2** 

No podrá ver el cubo a menos que agregue una luz a la escena, que es la última tarea antes de probar la escena.

4. En el panel **Modes** (Modos), cambie a la pestaña **Lights** (Luces) y arrastre una **Directional Light** (Luz direccional) a la escena.
* Coloque la luz sobre **PlayerStart** para que pueda verlo.

![Escena del editor de Unreal con un cubo y luz direccional agregada](images/unreal-quickstart-img-08.png)

5. Vaya a **File > Save Current** (Archivo > Guardar actual), asigne al nivel el nombre **Main** (Principal) y seleccione **Save** (Guardar).

Con la escena definida, presione **Play** (Jugar) en la barra de herramientas para ver el cubo en acción. Cuando haya terminado de admirar su trabajo, presione Esc para detener la aplicación.

![Escena en modo de juego con el cubo en el medio de la pantalla](images/unreal-quickstart-img-09.png)

Ahora que la escena está configurada, preparémosla para algunas interacciones básicas en AR. En primer lugar, debe crear una sesión de AR y puede agregar planos técnicos para habilitar la interacción con la mano.

## <a name="adding-a-session-asset"></a>Adición de un recurso de sesión

Las sesiones de AR en Unreal no aparecen por sí mismas. Para usar una sesión, necesita un recurso de datos ARSessionConfig con el que trabajar, que será la tarea siguiente:

1. En el **explorador de contenido**, seleccione **Add New > Miscellaneous > Data Asset** (Agregar nuevo > Varios > Recurso de datos) y asegúrese de estar en el nivel de la carpeta Content (Contenido)
2. Seleccione **ARSessionConfig**, haga clic en **Select** (Seleccionar) y asigne al recurso el nombre **ARSessionConfig**.

![Ventana Pick data asset class (Seleccionar clase de recurso de datos) abierta con el recurso de configuración de sesión de AR resaltado](images/unreal-quickstart-img-10.png)

2. Haga doble clic en **ARSessionConfig** para abrirlo, seleccione **Save** (Guardar) con todas las opciones predeterminadas y vuelva a la ventana principal:

![Ventana de detalles del recurso de configuración de sesión de AR](images/unreal-quickstart-img-11.png)

Una vez hecho esto, el paso siguiente consiste en asegurarse de que la sesión de AR se inicia y se detiene cuando el nivel se carga y finaliza. Por suerte, Unreal tiene un plano técnico especial denominado **Plano técnico de nivel** que actúa como un gráfico de eventos global de nivel superior. La conexión del recurso ARSessionConfig en Level Blueprint (Plano técnico de nivel) garantiza que la sesión de AR se activará cuando se inicie la reproducción del juego.

3. Desde la barra de herramientas del editor, seleccione **Blueprints > Open Level Blueprint** (Planos técnicos > Abrir plano técnico de nivel):

![Menú de plano técnico abierto con opción para abrir plano técnico de nivel resaltada](images/unreal-quickstart-img-12.png)

4. Arrastre el nodo de ejecución (icono de flecha hacia la izquierda) fuera de **Event BeginPlay** (Evento BeginPlay) y suéltelo.
* Busque el nodo **Start AR Session** (Iniciar sesión de AR) y presione Entrar.
* Haga clic en la lista desplegable **Select Asset** (Seleccionar recurso) en **Session Config** (Configuración de sesión) y elija el recurso **ARSessionConfig**.

![Gráfico del plano técnico con el evento BeginPlay conectado a la función de inicio de sesión de AR](images/unreal-quickstart-img-13.png)

5. Haga clic con el botón derecho en EventGraph y cree un nuevo nodo **Event EndPlay**. 
* Arrastre el marcador de ejecución,suéltelo y, a continuación, busque el nodo **Detener sesión de AR** y presione ENTRAR. 
* Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal.

> [!IMPORTANT]
> Si la sesión de AR aún está en ejecución cuando el nivel finaliza, algunas características pueden dejar de funcionar si reinicia la aplicación durante el streaming a un casco de realidad mixta.

![Nodo de juego final de evento asociado a la función de detención de sesión de AR](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>Configuración de entradas

1. Seleccione **Edit > Project Settings** (Editar > Configuración del proyecto) y vaya a **Engine > Input** (Motor > Entrada).
2. Seleccione el icono **+** junto a **Action Mappings** (Asignaciones de acciones) y cree las acciones **RightPinch** y **LeftPinch**:

![Configuración de entrada de enlace con las asignaciones de acción de reducción derecha e izquierda resaltadas](images/unreal-quickstart-img-15.jpg)

3. Asigne las acciones **RightPinch** y **LeftPinch** a las respectivas acciones de **OpenXR Msft Hand Interaction**:

![Asignaciones de acciones con las opciones de Open XR Msft Hand interaction resaltadas](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a>Configuración de gestos

Ahora que hemos configurado las entradas, pasaremos a la parte emocionante: la incorporación de gestos. Vamos a girar el cubo con el gesto de reducir de la mano derecha y saldremos de la aplicación con el gesto de reducir de la mano izquierda.

1. Abra el elemento **Level Blueprint** (Plano técnico de nivel) y agregue las acciones **InputAction RightPinch** y **InputAction LeftPinch**.
* Conecte el evento de reducción derecha a **AddActorLocalRotation** con el elemento **Cube** (Cubo) como destino y el valor de **Delta Rotation** (Rotación diferencial) definido como **X = 0, Y = 0** y **Z = 20**. Ahora, el cubo girará 20 grados cada vez que se realice el gesto de reducir
* Conectar el evento de reducción izquierda a **Quit Game** (Salir del juego)

![Deje el plano técnico de nivel abierto con acciones de entrada para eventos de reducción izquierda y derecha.](images/unreal-quickstart-img-17.jpg)

2. En la configuración de **Transform** (Transformación) del cubo, establezca **Mobility** (Movilidad) como **Movable** (Móvil) para que se pueda mover de forma dinámica:

![Configuración de transformación con la propiedad de movilidad resaltada](images/unreal-quickstart-img-18.jpg)

En este punto, estará listo para implementar y probar la aplicación.