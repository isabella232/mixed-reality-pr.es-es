---
title: 2. Inicialización de tu proyecto y primera aplicación
description: Parte 2 de 6 de una serie de tutoriales para compilar una aplicación de ajedrez con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: f7cf43e8f1c040660b6a2688e234a271bc071b00
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712658"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicialización de tu proyecto y primera aplicación

En el primer tutorial, comenzará con un nuevo proyecto de Unreal y habilitará el complemento de HoloLens, creará y activará un nivel, y agregará piezas de ajedrez. Usará nuestros recursos predefinidos para todos los materiales y objetos 3D, por lo que no deberá preocuparse por modelar nada. Al final de este tutorial tendrá un lienzo en blanco listo para la realidad mixta.

> [!IMPORTANT]
> Asegúrese de que tiene todos los requisitos previos de la página [Introducción](/windows/mixed-reality/unreal-uxt-ch1).

## <a name="objectives"></a>Objetivos

* Configuración de un proyecto de Unreal para el desarrollo de HoloLens
* Importación de recursos y configuración de una escena
* Creación de actores y eventos de nivel de script con planos técnicos

## <a name="creating-a-new-unreal-project"></a>Creación de un nuevo proyecto de Unreal

Lo primero que necesita es un proyecto con el que trabajar. Si es la primera vez que desarrolla una aplicación para Unreal, deberá [descargar los archivos auxiliares](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) desde el iniciador de Epic.

1. Iniciar Unreal Engine

2. En **Games** (Juegos), seleccione **New Project Categories** (Nuevas categorías de proyecto) y haga clic en **Next** (Siguiente). 

![Selección de la plantilla del proyecto Games](images/unreal-uxt/2-gamestemplate.png)

3. Seleccione una plantilla **Blank** (En blanco) y haga clic en **Next** (Siguiente). 

![Seleccionar la plantilla en blanco](images/unreal-uxt/2-template.PNG)

4. Defina **C++** , **Scalable 3D or 2D, Mobile/Tablet** (Móvil o tableta escalable 3D o 2D) y **No Starter Content** (Sin contenido de inicio) como **Project Settings** (Configuración del proyecto) y, a continuación, elija una ubicación para guardar y haga clic en **Create Project** (Crear proyecto). 

> [!NOTE]
> Debe seleccionar un proyecto de C++ en lugar de un proyecto de plano técnico para compilar el complemento de herramientas de la experiencia del usuario, que configurará más adelante en la sección 4.

![Configuración del proyecto inicial](images/unreal-uxt/2-project-settings.PNG)

El proyecto deberá abrirse automáticamente en el editor de Unreal, lo que significa que está listo para la sección siguiente.

## <a name="enabling-required-plugins"></a>Habilitación de los complementos necesarios

Para usar las características disponibles a través de la plataforma de realidad mixta de Microsoft, primero tendrá que instalar y habilitar el complemento Microsoft OpenXR. Para más información sobre el complemento, puede consultar el proyecto en [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).

1. Abra Epic Games Launcher. Vaya a Unreal Engine Marketplace y busque "[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)". Instale el complemento en el motor.

![Unreal Marketplace](images/unreal-uxt/2-openxr-plugin.PNG)

2. De vuelta en el editor de Unreal, vaya a **Project Settings** > **Plugins** (Configuración del proyecto > Complementos) y busque "Microsoft OpenXR". Asegúrese de que el complemento esté habilitado y reinicie el editor si se le solicita.

![Habilitación del complemento Microsoft OpenXR](images/unreal-uxt/2-enable-plugin.PNG)

Al habilitar el complemento Microsoft OpenXR, se habilitarán automáticamente todos los demás complementos necesarios para el desarrollo de realidad mixta. Tenga en cuenta que el complemento "Microsoft Windows Mixed Reality" debe estar deshabilitado para poder usar OpenXR. 

## <a name="creating-a-level"></a>Creación de un nivel
La siguiente tarea consiste en crear una configuración de un jugador con un punto inicial y un cubo para referencia y escala.

1. Seleccione **File > New Level** (Archivo > Nuevo nivel) y elija **Empty Level** (Nivel vacío). Ahora, la escena predeterminada en la ventanilla debe estar vacía.

2. Seleccione **Basic** (Básico) en la pestaña **Modes** (Modos) y arrastre **PlayerStart** a la escena. 
    * Establezca **Ubicación** en **X = 0**, **Y = 0** y **Z = 0** en la pestaña **Detalles** para colocar al usuario en el centro de la escena cuando se inicie la aplicación.

![Ventanilla con PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. Arrastre un **Cube** (Cubo) desde la pestaña **Basic** (Básico) a la escena. 
    * Establezca **Location** (Ubicación) en **X = 50**, **Y = 0** y **Z = 0**. Así, se coloca el cubo a 50 cm del jugador en el momento del inicio. 
    * Cambie **Scale** (Escala) a **X = 0,2**, **Y = 0,2** y **Z = 0,2** para reducir el cubo. 

No podrá ver el cubo a menos que agregue una luz a la escena, que es la última tarea antes de probar la escena.

4. Cambie a la pestaña **Ligths** (Luces) del panel **Modes** (Modos) y arrastre **Directional Light** (Luz direccional) a la escena. Coloque la luz sobre **PlayerStart** para que pueda verlo.

![Ventanilla con luz agregada](images/unreal-uxt/2-light.PNG)

5. Vaya a **Archivo > Guardar actual**, asigne al nivel el nombre **Principal** y seleccione **Guardar**. 

Con la escena definida, presione **Play** (Jugar) en la barra de herramientas para ver el cubo en acción. Cuando haya terminado de admirar su trabajo, presione **Esc** para detener la aplicación.

![Cubo en la ventanilla](images/unreal-uxt/2-cube.PNG)

Ahora que la escena está configurada, puede empezar a agregar el panel de ajedrez y la pieza para completar el entorno de la aplicación.

## <a name="importing-assets"></a>Importación de recursos
La escena está un poco vacía en este momento, pero se solucionará al importar los recursos ya preparados al proyecto.

1. Descargue y descomprima la carpeta de recursos de [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) mediante [7-zip](https://www.7-zip.org/).

2. Seleccione **Agregar nuevo > Nueva carpeta** en **Explorador de contenido** y asígnele el nombre **ChessAssets**. 
    * Haga doble clic en la nueva carpeta, donde importará los recursos 3D.

![Mostrar u ocultar el panel de orígenes](images/unreal-uxt/2-showhidesources.PNG)

3. Seleccione **Importar** en **Explorador de contenido**, seleccione todos los elementos de la carpeta de recursos descomprimidos y haga clic en **Abrir**. 
    * Los recursos incluyen las mallas de objetos 3D para el tablero de ajedrez, las piezas en formato FBX y los mapas de textura en formato TGA que usará para los materiales.  

4. Cuando aparezca la ventana de opciones de importación de FBX, expanda la sección **Material** y cambie **Material Import Method** (Método de importación de material) a **Do Not Create Material** (No crear material).
    * Seleccione **Importar todo**.

![Opciones de importación de FBX](images/unreal-uxt/2-nocreatemat.PNG)

Es todo lo que debe hacer para los recursos. El siguiente conjunto de tareas consiste en crear los bloques de creación de la aplicación con planos técnicos.

## <a name="adding-blueprints"></a>Adición de planos técnicos

1. Seleccione **Agregar nuevo > Nueva carpeta** en **Explorador de contenido** y asígnele el nombre **Planos técnicos**. 

> [!NOTE]
> Los [planos técnicos](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) son recursos especiales que proporcionan una interfaz basada en nodos para crear nuevos tipos de actores y eventos de nivel de script. 

2. Haga doble clic en la carpeta **Blueprints** (Planos técnicos), haga clic con el botón derecho y seleccione **Blueprint Class** (Clase de plano técnico).         
    * Seleccione **Actor** y asigne el nombre **Board** al nuevo plano técnico. 

![Selecciona una clase principal para el plano técnico](images/unreal-uxt/2-bpparent.PNG)

El nuevo plano técnico **Board** ahora aparece en la carpeta **Blueprints** (Planos técnicos) como se muestra en la captura de pantalla siguiente. 

![Nuevo plano técnico Board](images/unreal-uxt/2-bpboard.PNG)

Está listo para empezar a agregar materiales a los objetos creados.

## <a name="working-with-materials"></a>Utilización de materiales
Los objetos que ha creado son de color gris de forma predeterminada, lo que no es muy alegre. La adición de materiales y mallas a los objetos es el último conjunto de tareas de este tutorial.

1. Haga doble clic en **Board** para abrir el editor de planos técnicos. 

2. Seleccione **Agregar componente > Escena** en el panel **Componentes** y asígnele el nombre **Root**. Observe que **Root** se muestra como un elemento secundario de **DefaultSceneRoot** en la siguiente captura de pantalla:

![Reemplazo de la raíz en el plano técnico](images/unreal-uxt/2-root-blueprint.PNG)


3. Haga clic y arrastre **Root** a **DefaultSceneRoot** para reemplazarlo y eliminar la esfera en la ventanilla. 

![Reemplazar la raíz](images/unreal-uxt/2-root.PNG)


4. Seleccione **Agregar componente > Malla estática** en el panel **Componentes** y asígnele el nombre **SM_Board**. Aparecerá como un objeto secundario en **Root**.

![Adición de una malla estática](images/unreal-uxt/2-sm-board.PNG)

4. Seleccione **SM_Board**, desplácese hacia abajo hasta la sección **Malla estática** del panel **Detalles** y seleccione **ChessBoard** en la lista desplegable. 

![Malla del tablero en la ventanilla](images/unreal-uxt/2-sm-board-view.PNG)

5.  En el panel **Detalles**, expanda la sección **Materiales** y seleccione **Crear nuevo recurso > Material** en la lista desplegable. 
    * Asigne al material el nombre **M_ChessBoard** y guárdelo en la carpeta **ChessAssets**. 

![Crear un material nuevo](images/unreal-uxt/2-newmat.PNG)

6.  Haga doble clic en la imagen del material **M_ChessBoard** para abrir el editor de materiales. 

![Apertura del editor de materiales](images/unreal-uxt/2-material-editor.PNG)

7. En el editor de materiales, haga clic con el botón derecho y busque **Texture Sample** (Muestra de textura). 
    * Expanda la sección **Material Expression Texture Base** (Base de textura de expresión de material) del panel **Details** (Detalles) y defina **Texture** (Textura) en **ChessBoard_Albedo**. 
    * Arrastre la marca de salida de **RGB** a la marca de color base de **M_ChessBoard**. 

![Establecer el color de base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  Repita el paso anterior cuatro veces más para crear cuatro nodos de **Muestra de textura** con la siguiente configuración:
    * Establezca **Texture** (Textura) en **ChessBoard_AO** y vincule **RGB** a la marca de **Ambient Occlusion** (Oclusión ambiental).
    * Establezca **Texture** (Textura) en **ChessBoard_Metal** y vincule **RGB** a la marca de **Metallic** (Metálico). 
    * Establezca **Texture** (Textura) en **ChessBoard_Normal** y vincule **RGB** a la marca de **Normal**.
    * Establezca **Texture** (Textura) en **ChessBoard_Rough** y vincule **RGB** a la marca de **Roughness** (Rugosidad). 
    * Haga clic en **Guardar**. 

![Enlazar las texturas restantes](images/unreal-uxt/2-boardmat.PNG)

Asegúrese de que la configuración del material sea similar a la captura de pantalla anterior antes de continuar.

## <a name="populating-the-scene"></a>Rellenado de la escena
Si vuelve al plano técnico **Board**, verá que se ha aplicado el material que acaba de crear. Lo único que queda es configurar la escena. En primer lugar, cambie las siguientes propiedades para asegurarse de que el tablero tiene un tamaño razonable y que tiene el ángulo correcto cuando se coloca en la escena:
1.  Establezca **Scale** (Escala) en **(0,05, 0,05, 0,05)** y **Z Rotation** (Rotación Z) en **90**. 
    * Haga clic en **Compile** (Compilar) en la barra de herramientas superior, luego en **Save** (Guardar) y vuelva a la ventana principal. 

![Tablero de ajedrez con el material aplicado](images/unreal-uxt/2-chessboard.PNG)

2.  Haga clic con el botón derecho en **Cube > Edit > Delete** (Cubo > Editar > Eliminar) y arrastre **Board** desde **Content Browser** (Explorador de contenido) a la ventanilla. 
    * Establezca **Location** (Ubicación) en **X = 80**, **Y = 0** y **Z = 20**. 

3.  Seleccione el botón **Jugar** para ver el nuevo tablero en el nivel. Presiona **Esc** para volver al editor. 

Ahora seguirá los mismos pasos para crear una pieza de ajedrez como hizo con el tablero:

1. Vaya a la carpeta **Planos técnicos**, haga clic con el botón derecho, seleccione **Clase de plano técnico** y elija **Actor**. Asigne al actor el nombre **WhiteKing**.

2. Haga doble clic en **WhiteKing** para abrirlo en el editor de planos técnicos, seleccione **Agregar componente > Escena** y asígnele el nombre **Root**. 
    * Arrastre y coloque **Root** en **DefaultSceneRoot** para reemplazarlo. 

3. Haga clic en **Add Component > Static Mesh** (Agregar componente > Malla estática) y asígnele el nombre **SM_King**. 
    * Establezca **Static Mesh** (Malla estática) en **Chess_King** y **Material** en un nuevo material denominado **M_ChessWhite** en el panel de detalles. 

4. Abra **M_ChessWhite** en el editor de materiales y enlace los siguientes nodos de **Texture Sample** (Muestra de textura) a lo siguiente:
   * Establezca **Textura** en **ChessWhite_Albedo** y vincule **RGB** a la marca de **Base Color** (Color de base).
    * Establezca **Texture** (Textura) en **ChessWhite_AO** y vincule **RGB** a la marca de **Ambient Occlusion** (Oclusión ambiental).
    * Establezca **Texture** (Textura) en **ChessWhite_Metal** y vincule **RGB** a la marca de **Metallic** (Metálico). 
    * Establezca **Texture** (Textura) en **ChessWhite_Metal** y vincule **RGB** a la marca de **Normal**.
    * Establezca **Texture** (Textura) en **ChessWhite_Rough** y vincule **RGB** a la marca de **Roughness** (Rugosidad). 
    * Haga clic en **Guardar**. 

El material de **M_ChessKing** debe parecerse a la siguiente imagen antes de continuar.

![Crear el material para el rey del ajedrez](images/unreal-uxt/2-chesskingmat.PNG)

Casi está, solo tiene que agregar la nueva pieza de ajedrez a la escena: 

1. Abra el plano técnico **WhiteKing**, cambie el valor de **Scale** (Escala) a **(0,05, 0,05, 0,05)** y de **Z Rotation** (Rotación Z) a **90**.
    * Compile y guarde el plano técnico y, a continuación, vuelva a la ventana principal. 

2.  Arrastre **WhiteKing** a la ventanilla, cambie al panel **World Outliner** (Esquematizador del mundo), arrastre **WhiteKing** a **Board** para convertirlo en un objeto secundario.

![World Outliner (Esquematizador del mundo)](images/unreal-uxt/2-child.PNG)

3.  En el panel **Details** (Detalles) en **Transform** (Transformar), establezca el valor de **Location** (Ubicación) de **WhiteKing** en **X = -26**, **Y = 4** y **Z = 0**.

Ya está. Seleccione **Jugar** para ver el nivel rellenado en acción y presione **Esc** cuando esté listo para salir. Ha tratado una gran cantidad de información sobre la creación de un proyecto sencillo, pero ahora está listo para pasar a la siguiente parte de la serie: configuración de la realidad mixta. 

[Sección siguiente: 3. Configuración del proyecto para la realidad mixta](unreal-uxt-ch3.md)