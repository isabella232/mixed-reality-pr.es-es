---
title: UMG y teclado en Unreal
description: Obtenga información sobre cómo usar gráficos de movimiento de Unrealm para crear un sistema de interfaz de usuario fuera de widgets.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento de los ojos, entrada de mirada, pantalla montada con la cabeza, motor de Unreal, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, widgets, interfaz de usuario, UMG, gráficos de movimiento de Unreal, Unreal Engine, UE, UE4
ms.openlocfilehash: 8cb1c804757332ce7b78f0cb92cf895b873c1835208962b20d5bbbfae4684785
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212846"
---
# <a name="umg-and-keyboard-in-unreal"></a>UMG y teclado en Unreal

Unreal Motion Graphics (UMG) es el sistema de interfaz de usuario integrado de Unreal Engine, que se usa para crear interfaces como menús y cuadros de texto. Las interfaces de usuario creadas con UMG constan de widgets. Le guiaremos a través de la creación de un nuevo widget, su incorporación al espacio mundial y la habilitación de la interacción mediante el teclado del sistema como ejemplo. Puede obtener más información sobre UMG en la documentación oficial de Unreal [Engine](https://docs.unrealengine.com/en-US/Engine/UMG/index.html). 

## <a name="create-a-new-widget"></a>Creación de un widget

- Cree un plano técnico de widget para crear la interfaz de usuario del juego:

![Captura de pantalla de la adición de un plano técnico de widget desde el menú de Unreal](images/unreal-umg-img-01.png)

- Abra el nuevo plano técnico y agregue componentes desde la paleta al lienzo.  En este caso, hemos agregado dos componentes de Cuadro de texto desde la sección "Entrada":

![Captura de pantalla de la ventana de jerarquía con el componente de widget de texto resaltado y expandido](images/unreal-umg-img-02.png)

- Seleccione un widget en la ventana Jerarquía o Diseñador y modifique los parámetros en el panel de detalles.  En este caso, hemos agregado algunos "Texto de sugerencia" predeterminados y un color de tono que aparece al mantener el puntero sobre el cuadro de texto.  Un cuadro de texto mostrará un teclado virtual en HoloLens cuando interactúe con:

![Captura de pantalla de los parámetros modificados en la ventana de jerarquía](images/unreal-umg-img-03.png)

- Los eventos también se pueden suscribir a en el panel de detalles:

![Captura de pantalla de los eventos en el panel de detalles](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>Agregar un widget a World Space

- Cree un nuevo actor, agregue un componente widget y agregue el actor a la escena:

![Captura de pantalla de un actor con un widget adjunto](images/unreal-umg-img-05.png)

- En el panel de detalles del widget, establezca La **clase de widget** en el plano técnico del widget creado anteriormente:

![Captura de pantalla del panel de detalles del plano técnico con el conjunto de clases de widget](images/unreal-umg-img-06.png)

- En el caso de un widget de texto, asegúrese de que la opción **Recibir entrada de hardware** está desactivada, por lo que solo actualizamos su texto desde el teclado virtual:

![Captura de pantalla de la sección de interacción con la entrada de hardware de recepción desactivada](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Interacción del widget

Normalmente, los widgets UMG reciben entradas de un mouse.  En HoloLens o VR, es necesario simular un mouse con un componente de interacción de widget para obtener los mismos eventos.

- Cree un nuevo actor, agregue un **componente Interacción de** widget y agregue el actor a la escena:

![Captura de pantalla de un nuevo actor con un componente de interacción de widget resaltado](images/unreal-umg-img-08.png)

- En el panel de detalles del componente Interacción de widget:
    - Establezca la distancia de interacción en el valor de distancia que desea.
    - Establecer el origen **de interacción** en **personalizado**
    - Para el desarrollo, establezca **Mostrar depuración** en **true:**

![Captura de pantalla de las propiedades del componente de interacción y depuración del widget](images/unreal-umg-img-09.png)

El valor predeterminado de Origen de interacción es "Mundo", que debe enviar raycasts en función de la posición mundial del componente Interacción del widget. En AR y VR, ese no es el caso.  Es importante habilitar "Mostrar depuración" y agregar un tono con el mouse a los widgets para comprobar que el componente de interacción del widget está haciendo lo que espera.  La solución alternativa consiste en usar un origen personalizado y establecer el raycast en el gráfico de eventos a partir del rayo de mano.  

Aquí llamamos a esto desde Event Tick:

![Plano técnico de la marca de evento](images/unreal-umg-img-10.png)

A continuación, agregue eventos de puntero del mouse virtual al componente de interacción del widget que reacciona HoloLens entrada.  En este caso, envíe un evento de presión del mouse izquierdo cuando se sujete la mano y un evento de liberación del mouse izquierdo cuando no esté comprendido:

![Plano técnico con eventos de puntero del mouse virtuales agregados](images/unreal-umg-img-13.png)

Ahora, al implementar la aplicación en el HoloLens 2, verá un rayo de mano que se extiende desde la mano derecha. Si lo dirige a uno de los cuadros de texto editables y pulsación en el aire, el teclado del sistema aparecerá delante de usted y le permitirá escribir texto. 
 
> [!NOTE]
> El teclado HoloLens sistema requiere Unreal Engine 4.26 o posterior. Además, el teclado no aparecerá cuando la aplicación se transmita desde el editor de Unreal al casco, solo cuando la aplicación se ejecuta en el dispositivo.

## <a name="see-also"></a>Ver también:
* [Documentación de UMG de Unreal](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Tutoriales de UMG de Unreal](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
