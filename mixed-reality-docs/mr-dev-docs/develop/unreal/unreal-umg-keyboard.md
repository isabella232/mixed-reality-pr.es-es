---
title: UMG y teclado en no real
description: Obtenga información sobre cómo usar gráficos de movimiento sin territorio para crear un sistema de interfaz de usuario fuera de los widgets.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, widgets, interfaz de usuario, UMG, gráficos de movimiento inreal, no real Engine, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355405"
---
# <a name="umg-and-keyboard-in-unreal"></a>UMG y teclado en no real

No real Motion Graphics (UMG) es un sistema de interfaz de usuario integrado del motor, que se usa para crear interfaces como menús y cuadros de texto. Las interfaces de usuario compiladas con UMG se componen de widgets. En esta guía se muestra cómo crear un nuevo widget, agregarlo a un espacio universal y habilitar la interacción con ese widget en realidad mixta, mediante el teclado del sistema como ejemplo. Puede obtener más información sobre UMG en la [documentación](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)oficial del motor no real. 

## <a name="create-a-new-widget"></a>Crear un nuevo widget

- Cree un Blueprint de widget para diseñar la interfaz de usuario del juego:

![Captura de pantalla de la adición de un Blueprint de widget desde el menú no real](images/unreal-umg-img-01.png)

- Abra el nuevo plano y agregue componentes de la paleta al lienzo.  En este caso, hemos agregado dos componentes de cuadro de texto de la sección "entrada":

![Captura de pantalla de la ventana de jerarquía con el componente widget de texto resaltado y expandido](images/unreal-umg-img-02.png)

- Seleccione un widget en la ventana jerarquía o diseñador y modifique los parámetros en el panel detalles.  En este caso, hemos agregado algunos valores predeterminados de "sugerencia" y un color de matiz cuando el cursor se mantiene sobre el cuadro de texto para proporcionar comentarios sobre los que el widget está listo para interactuar.  Un cuadro de texto mostrará un teclado virtual en HoloLens cuando se interactúe con:

![Captura de pantalla de los parámetros modificados en la ventana jerarquía](images/unreal-umg-img-03.png)

- También se puede suscribir a eventos en el panel de detalles:

![Captura de pantalla de los eventos en el panel de detalles](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>Agregar un widget a un espacio universal

- Cree un nuevo actor, agregue un componente de widget y agregue el actor a la escena:

![Captura de pantalla de un actor con un widget adjunto](images/unreal-umg-img-05.png)

- En el panel de detalles del widget, establezca la **clase widget** en el Blueprint de widget creado anteriormente:

![Captura de pantalla del panel de detalles del Blueprint con la clase de widget establecida](images/unreal-umg-img-06.png)

- Para un widget de texto, asegúrese de que la casilla **recibir entrada de hardware** está desactivada, por lo que solo actualizaremos su texto desde el teclado virtual:

![Captura de pantalla de la sección de interacción con la entrada de hardware de recepción desactivada](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Interacción del widget

Los widgets UMG suelen recibir la entrada de un mouse.  En HoloLens o VR, es necesario simular un mouse con un componente de interacción de widget para obtener los mismos eventos.

- Cree un nuevo actor, agregue un componente de **interacción de widget** y agregue el actor a la escena:

![Captura de pantalla de un nuevo actor con un componente de interacción widget resaltado](images/unreal-umg-img-08.png)

- En el panel de detalles del componente de interacción widget, establezca la distancia de interacción en la distancia deseada, establezca el **origen de interacción** en **personalizado** y, en desarrollo, establezca **Mostrar depurar** en **true**:

![Captura de pantalla de las propiedades de componente de interacción y depuración de widgets](images/unreal-umg-img-09.png)

El valor predeterminado para el origen de interacción es "World", que debe enviar raycasts basándose en la posición mundial del componente de interacción del widget, pero en AR y VR esto no parece ser el caso.  Habilitar "Mostrar depuración" y agregar un matiz de desplazamiento a los widgets mientras se desarrollan es importante para comprobar que el componente de interacción del widget está haciendo lo esperado.  La solución consiste en usar un origen personalizado y establecer el Raycast en el gráfico de eventos a partir del rayo de mano.  

Aquí nos llamaremos desde el paso del evento:

![Plano del paso de evento](images/unreal-umg-img-10.png)

A continuación, agregue eventos del puntero del mouse virtual al componente de interacción de widget que reacciona a la entrada de HoloLens.  En este caso, enviar un evento de presionar el botón primario cuando se agarre la mano y un evento de liberación del mouse cuando no se agarre:

![Blueprint con eventos del puntero del mouse virtual agregados](images/unreal-umg-img-13.png)

Ahora, cuando implemente la aplicación en HoloLens 2, verá un rayo de mano que se extiende desde la mano derecha. Si lo dirige a uno de los cuadros de texto editables y a la pulsación aérea, el teclado del sistema aparecerá delante de usted y le permitirá escribir texto. 
 
> [!NOTE]
> El teclado del sistema HoloLens requiere un motor inreal 4,26 o posterior. Además, el teclado no aparecerá cuando la aplicación se transmita desde el editor no real al casco, solo cuando la aplicación se ejecuta en el dispositivo.

## <a name="see-also"></a>Ver también:
* [Documentación de UMG](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Tutoriales de UMG de los no reales](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
