---
title: 4. Creación de escenas interactivas
description: Parte 4 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 08/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: dc17b878255a3d6a8e0efc3a4c5bd7aa7d57373d
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679854"
---
# <a name="4-making-your-scene-interactive"></a>4. Creación de escenas interactivas

## <a name="overview"></a>Introducción

En el tutorial anterior, agregó ARSession, un peón y un modo de juego para completar la configuración de la realidad mixta de la aplicación de ajedrez. Esta sección se centra en el uso del complemento de código abierto [UX Tools de Mixed Reality Toolkit](https://github.com/microsoft/MixedReality-UXTools-Unreal), que proporciona herramientas para hacer que la escena sea interactiva. Al final de esta sección podrá mover las piezas de ajedrez con la entrada del usuario. 

## <a name="objectives"></a>Objetivos

* Descarga del complemento UX Tools de Mixed Reality Toolkit 
* Adición de actores de interacción con la mano a las puntas de los dedos
* Creación y adición de manipuladores a objetos de la escena
* Uso de la simulación de entrada para validar el proyecto

## <a name="downloading-the-mrtk-ux-tools-plugin"></a>Descarga del complemento UX Tools de MRTK
Antes de empezar a trabajar con la entrada del usuario, debe agregar el complemento al proyecto.

1.  En la [página de versiones](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) de Mixed Reality UX Tools de GitHub, vaya a la versión v0.9.0 de UX Tools for Unreal y descargue **UXTools.0.9.0.zip**. Descomprima el archivo.

2.  Cree una nueva carpeta denominada **Plugins** en la carpeta del proyecto. Copie el complemento UXTools descomprimido en esta carpeta y reinicie el editor de Unreal. 

![Crear una carpeta de complementos del proyecto](images/unreal-uxt/4-plugins.PNG)

3.  El complemento UXTools incluye una carpeta de contenido con subcarpetas para los componentes, como **botones**, la **simulación de entrada** y **punteros**, así como una carpeta de clases en C++ con código adicional.  

> [!NOTE]
> Si no ve la sección **UXTools Content** (Contenido de UXTools) en **Content Browser** (Explorador de contenido), haga clic en **View Options > Show Plugin Content** (Opciones de vista > Mostrar contenido del complemento). 

![Mostrar el contenido del complemento](images/unreal-uxt/4-showplugincontent.PNG)

Una vez que el complemento esté instalado, estará listo para empezar a usar las herramientas que ofrece, comenzando por los actores de interacción con la mano.

## <a name="spawning-hand-interaction-actors"></a>Generar actores de interacción con la mano
La interacción con la mano con elementos UX se realiza mediante actores de interacción con la mano, que crean y controlan los punteros y los objetos visuales para las interacciones cercanas y lejanas.
- Las *interacciones cercanas* se llevan a cabo reduciendo los elementos entre los dedos índice y pulgar o bien tocándolos con la punta del dedo. 
- Las *interacciones lejanas* se realizan apuntando un haz desde la mano virtual en un elemento y presionando los dedos índice y pulgar.

En nuestro caso, la adición de un actor de interacción con la mano a **MRPawn** hará lo siguiente:
- Agregar un cursor a las puntas de los dedos índice del peón.
- Proporcionar eventos de entrada con la mano articulada que se pueden manipular a través del peón.
- Permitir eventos de entrada de interacción lejana a través de haces de mano que se extienden desde las palmas de las manos virtuales.

Para controlar estos conceptos, le recomendamos que lea la [documentación](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.9.x/Docs/HandInteraction.md) de interacciones con la mano antes de continuar. 

Cuando esté listo, abra el plano técnico **MRPawn** y vaya a **Event Graph** (Gráfico de eventos). 

1. Arrastre la marca de ejecución de **Event BeginPlay** (Evento BeginPlay) y suéltela para colocar un nuevo nodo. 
    * Seleccione **Spawn Actor from Class** (Generar actor a partir de clase), haga clic en el menú desplegable situado junto a la marca de **Class (Clase)** y busque **Uxt Hand Interaction Actor** (Actor de interacción con la mano de UXT).  

2. Genere un segundo valor de **Uxt Hand Interaction Actor** (Actor de interacción con la mano de UXT), pero esta vez establezca la **mano** en **Derecha**. Cuando se inicia el evento, se generará un actor de interacción con la mano de UXT en cada mano. 

**Event Graph** (Gráfico de eventos) debe coincidir con la captura de pantalla siguiente:

![Generar actores de interacción con la mano de UXT](images/unreal-uxt/4-spawnactor.PNG)

Ambos actores de interacción con la mano de UXT necesitan propietarios y ubicaciones de transformación inicial. La transformación inicial no importa, ya que los actores de interacción con la mano saltarán a las manos virtuales en cuanto estén visibles (este comportamiento se incluye en el complemento UX Tools). Sin embargo, la función `SpawnActor` requiere una entrada de transformación para evitar un error del compilador, por lo que se usarán los valores predeterminados. 

1. Arrastre una de las marcas de **Spawn Transform** (Generar transformación) y suéltela para colocar un nuevo nodo. 
    * Busque el nodo **Make Transform** (Realizar transformación) y, a continuación, arrastre **Return Value** (Valor devuelto) a **Spawn Transform** (Generar transformación) de la otra mano para que ambos nodos **SpawnActor** estén conectados. 

2.  Haga clic en la **flecha hacia abajo** en la parte inferior de los nodos **SpawnActor** para revelar la marca **Owner** (Propietario).    
    * Arrastra la marca de las marcas de **Owner** (Propietario) y suéltala para colocar un nuevo nodo. 
    * Busque **self** (propio) y seleccione la variable **Get a reference to self** (Obtener una autoreferencia) y, a continuación, cree un vínculo entre el nodo de referencia de objeto **Self** (Propio) y la marca de **Owner** (Propietario) del actor de interacción con la mano de la otra mano. 
3. Por último , active el cuadro **Show Near Cursor on Grab Targets** (Mostrar el cursor cercano en los destinos de agarre) de ambos actores de interacción de mano. De este modo, se mostrará un cursor en el destino del agarre a medida que el dedo del índice se aproxime a este, lo que permitirá ver mejor dónde está el dedo en relación con el destino.
    * **Compila**, **guarda** y vuelve a la ventana principal. 

Asegúrese de que las conexiones coinciden con la siguiente captura de pantalla, pero no dude en arrastrar los nodos para que el plano técnico sea más legible.

![Completar la configuración del actor de interacción con la mano de UXT](images/unreal-uxt/4-fingerptrs.PNG) 

Puede encontrar más información sobre el actor de interacción con la mano proporcionado en el complemento UX Tools de MRTK en la [documentación](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html).

Ahora, las manos virtuales del proyecto tienen una forma de seleccionar objetos, pero todavía no pueden manipularlos. La última tarea antes de probar la aplicación es agregar componentes de manipulador a los actores de la escena.

## <a name="attaching-manipulators"></a>Asociación de manipuladores

Un manipulador es un componente que responde a la entrada con la mano articulada y se puede capturar, girar y trasladar. Aplicar la transformación del manipulador a una transformación de actor permite la manipulación directa del actor. 

1. Abra el panel técnico **Board** (Tablero), haga clic en **Add Component** (Agregar componente) y busque **Uxt Generic Manipulator** (Manipulador genérico de UXT) en el panel **Components** (Componentes).

![Agregar un manipulador genérico](images/unreal-uxt/4-addmanip.PNG)

2. Expanda la sección **Generic Manipulator** (Manipulador genérico) en el panel **Details** (Detalles). Puede establecer una manipulación con una o dos manos, el modo de rotación y el suavizado desde aquí. No dudes en seleccionar los modos que quieras y, a continuación, **compila** y **guarda** el tablero. 

![Establecer el modo](images/unreal-uxt/4-setrotmode.PNG)

3. Repita los pasos anteriores para el actor **WhiteKing**.

Puede encontrar más información sobre los componentes del manipulador proporcionados con el complemento UX Tools de MRTK en la [documentación](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html).

## <a name="testing-the-scene"></a>Prueba de la escena
Buenas noticias para todos. Está listo para probar la aplicación con sus nuevas manos virtuales y la entrada del usuario. Pulse en **Play** (Jugar) en la ventana principal y verá dos manos de malla que proporciona el complemento UX Tools de MRTK, con haces de mano que se extienden desde la palma de cada mano. Puede controlar las manos y sus interacciones de la manera siguiente:
- Mantenga presionada la tecla **Alt izquierda** para controlar la **mano izquierda** y la tecla **Mayús izquierda** para controlar la **mano derecha**. 
- Mueva el ratón para mover la mano y desplácese con la **rueda del mouse** para mover la mano **hacia adelante** o **hacia atrás**. 
- Haga clic con el botón primario del mouse para **reducir** o haga clic en el botón central del ratón para **tocar**. 

> [!NOTE]
> Es posible que la simulación de entrada no funcione si tiene varios cascos conectados al equipo. Si tiene problemas, pruebe a desconectar los otros casos. 

![Manos simuladas en la ventanilla](images/unreal-uxt/4-handsim.PNG)

Pruebe a usar las manos simuladas para seleccionar, mover y colocar el rey blanco del ajedrez y manipular el tablero. Experimente con la interacción cercana y lejana: observe que, cuando las manos se acercan lo suficiente como para agarrar el tablero y el rey directamente, el haz de mano desaparece y se reemplaza con un cursor en forma de dedo en la punta del índice. 

Puede encontrar más información sobre la característica de manos simuladas que ofrece el complemento UX Tools de MRTK en la [documentación](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/InputSimulation.html).

Ahora que las manos virtuales pueden interactuar con objetos, está listo para pasar al siguiente tutorial y agregar interfaces de usuario y eventos.

[Sección siguiente: 5. Adición de un botón y restablecimiento de las ubicaciones de las piezas](unreal-uxt-ch5.md)
