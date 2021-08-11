---
title: Vistas de aplicación
description: 'Obtenga información sobre cómo usar los dos tipos de vistas en Windows Mixed Reality aplicaciones: vistas inmersivas y vistas 2D.'
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: vista envolvente, vista 2D, pizarra, aplicación, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 1f779749938bfc8893f0e1f1f60c97549d30a24075b5b0926af61e2f88625b9c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191520"
---
# <a name="app-views"></a>Vistas de aplicación

Windows aplicaciones pueden contener dos tipos de vistas: vistas **inmersivas** y **vistas 2D**. Las aplicaciones pueden cambiar entre sus distintas vistas envolventes y 2D, mostrando sus vistas 2D en un monitor como una ventana o en un casco como una pizarra. Las aplicaciones que tienen al menos una vista inmersiva se clasifican como **aplicaciones de realidad mixta.** Las aplicaciones que nunca tienen una vista envolvente son **aplicaciones 2D**.

## <a name="immersive-views"></a>Vistas inmersivas

Una vista envolvente ofrece a la aplicación la posibilidad de crear hologramas en el mundo que rodea al usuario o sumergirlo en un entorno virtual. Cuando una aplicación dibuja en la vista inmersiva, ninguna otra aplicación está dibujando al mismo tiempo hologramas de varias aplicaciones que no se &mdash; han compuesto juntos. Al ajustar continuamente la [](../develop/platform-capabilities-and-apis/rendering.md) perspectiva desde la que la aplicación representa su escena para [](coordinate-systems.md) que coincida con los movimientos de la cabeza del usuario, la aplicación puede representar hologramas bloqueados por el mundo. Los hologramas bloqueados por el mundo permanecen en un punto fijo del mundo real o pueden representar un mundo virtual que mantiene su posición a medida que se mueve un usuario.

![Cuando se encuentra en una vista inmersiva, los hologramas se pueden colocar en el mundo que le rodea.](images/designoverview-940px.jpg)<br>
*Cuando se encuentra en una vista inmersiva, los hologramas se pueden colocar en el mundo que le rodea.*

En [HoloLens](/hololens/hololens1-hardware), la aplicación representa sus hologramas sobre el entorno real del usuario. En un [Windows Mixed Reality casco](../discover/immersive-headset-hardware-details.md)envolvente, el usuario no puede ver el mundo real, por lo que la aplicación debe representar todo lo que el usuario verá.

La [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) principal (incluidos los menú Inicio y los hologramas que ha colocado alrededor del entorno) tampoco se representa mientras se encuentra en una vista inmersiva. En HoloLens, Cortana las notificaciones del sistema que se producen mientras se muestra una vista inmersiva, a la que el usuario puede responder con la entrada de voz.

Mientras se encuentra en una vista inmersiva, la aplicación también es responsable de controlar todas las entradas. La entrada en Windows Mixed Reality se forma de [mirada,](gaze-and-commit.md)gesto [(solo](gaze-and-commit.md#composite-gestures) HoloLens), [controladores de voz y movimiento [(solo](motion-controllers.md) cascos envolventes).

## <a name="2d-views"></a>Vistas 2D

![Varias vistas 2D en torno a la Windows Mixed Reality principal](images/teleportation-940px.png)<br>
*Varias aplicaciones con una vista 2D colocada alrededor del Windows Mixed Reality principal*

Una aplicación con una vista 2D aparece en la página principal de [Windows Mixed Reality (a](../discover/navigating-the-windows-mixed-reality-home.md) veces denominada "shell") como una pizarra virtual, que se representa junto con los iniciadores de la aplicación y otros hologramas que el usuario ha colocado en su mundo. El usuario puede ajustar esta pizarra para moverla y escalarla, aunque permanece en una resolución fija independientemente de su tamaño. Si la primera vista de la aplicación es una vista 2D, el contenido 2D rellenará la misma pizarra que se usa para iniciar la aplicación.

En un casco de escritorio, puede ejecutar cualquier aplicación de plataforma Windows universal (UWP) que se ejecute actualmente en el monitor de escritorio. Estas aplicaciones ya están representando vistas 2D en la actualidad y su contenido aparecerá automáticamente en una pizarra en el mundo del usuario cuando se inicie. Las aplicaciones para UWP 2D pueden tener como **destino Windows. Familia** de dispositivos universal para ejecutarse en cascos de escritorio y HoloLens como pizarras.

Un uso clave de las vistas 2D es mostrar un formulario de entrada de texto que usa el teclado del sistema. Dado que el shell no se puede representar sobre una vista inmersiva, la aplicación tiene que cambiar a una vista 2D para mostrar el teclado del sistema. Las aplicaciones que quieran aceptar la entrada de texto deben cambiar a una vista 2D con un cuadro de texto. Aunque ese cuadro de texto tiene el foco, el sistema mostrará el teclado del sistema, lo que permite al usuario escribir texto.

Una aplicación puede tener vistas 2D en el monitor de escritorio y en un casco conectado en un equipo de escritorio. Por ejemplo, puede examinar Edge en el monitor de escritorio mediante su vista 2D principal para encontrar un vídeo de 360 grados. Al reproducir ese vídeo, Edge iniciará una vista inmersiva secundaria dentro del casco para mostrar el contenido del vídeo inmersivo.

## <a name="see-also"></a>Consulte también

* [Modelo de aplicaciones](app-model.md)
* [Actualización de aplicaciones para UWP bidimensionales para la realidad mixta](../develop/porting-apps/building-2d-apps.md)
* [Obtención de HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)
* [Tipos de aplicaciones de realidad mixta](types-of-mixed-reality-apps.md)