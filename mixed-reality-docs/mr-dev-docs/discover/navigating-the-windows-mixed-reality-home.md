---
title: Desplazamiento por la página principal de Windows Mixed Reality
description: Obtenga información sobre cómo navegar por Windows Mixed Reality inicio en HoloLens y Windows Mixed Reality cascos.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: shell, os, platform, house, house, home, environment, start, start, start menu, home menu, pins, app, launch apps, place apps, teleport, move, navigate, mixed reality headset, virtual reality headset, what is virtual reality
ms.openlocfilehash: 39ca5e974e242019d7eb14fba0362151213c6558cce7f13328390712b3642901
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190278"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Desplazamiento por la página principal de Windows Mixed Reality

Al igual que la Windows del equipo de escritorio comienza con el escritorio, Windows Mixed Reality comienza con el inicio. La Windows Mixed Reality hogar usa nuestra capacidad innate para comprender y navegar por lugares 3D. Con HoloLens, su casa es su espacio físico, pero con cascos envolventes, su hogar es un lugar virtual.

La página principal también es donde usará el menú Inicio para abrir y colocar aplicaciones y contenido. Puede rellenar su casa con contenido de realidad mixta y multitarea mediante varias aplicaciones al mismo tiempo. Las cosas que coloque en su casa permanecerán allí, incluso si reinicia el dispositivo.

## <a name="start-menu"></a>Menú Inicio

![Menú Inicio en Microsoft HoloLens](images/start-500px.png)

El menú Inicio consta de:
* Información del sistema (estado de la red, porcentaje de batería, hora actual y volumen)
* Cortana (en cascos envolventes, un icono Iniciar; en HoloLens, en la parte superior de Inicio)
* Aplicaciones ancladas
* Botón Todas las aplicaciones (signo más)
* Botones de foto y vídeo [para la captura de realidad mixta](/hololens/holographic-photos-and-videos)

Cambie entre las aplicaciones ancladas y las vistas Todas las aplicaciones seleccionando los botones más o menos. Para abrir el menú Inicio en HoloLens, use el gesto de Bloom. En un casco envolvente, presione el botón Windows en el controlador.

## <a name="launching-apps"></a>Inicio de aplicaciones

Para iniciar una aplicación, selecciónelo en Inicio. El menú Inicio desaparecerá y la aplicación se abrirá en modo de selección de ubicación, ya sea como una ventana 2D o un modelo [3D](../distribute/implementing-3d-app-launchers.md).

Para ejecutar la aplicación, deberá colocarla en su casa:
1. Use la [mirada](../design/gaze-and-commit.md) o el controlador para colocar la aplicación donde quiera. Se ajustará automáticamente (en tamaño y posición) para ajustarse al espacio donde lo coloque.
2. Coloque la aplicación con pulsación en el aire (HoloLens) o el botón Seleccionar (cascos envolventes). Para cancelar y devolver el menú Inicio, use el gesto de Bloom o el Windows botón.

[Las aplicaciones 2D](../develop/porting-apps/building-2d-apps.md), creadas para escritorio, móviles o Xbox, se pueden modificar para que se ejecuten como aplicaciones envolventes de realidad mixta mediante [holographicSpace API](/uwp/api/Windows.Graphics.Holographic.HolographicSpace). Una aplicación inmersiva lleva al usuario fuera de casa y a una experiencia inmersiva. Los usuarios pueden volver a casa con el gesto de Bloom (HoloLens) o presionando el botón de Windows en el controlador (cascos envolventes).

Las aplicaciones también se pueden iniciar a través de una API de aplicación a aplicación o a través de Cortana.

![Aplicaciones de la página Windows Mixed Reality inicio](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Movimiento y ajuste de aplicaciones

Seleccione **Ajustar en** la barra de la aplicación para mostrar los controles que mueven, escalan y giran contenido de realidad mixta. Cuando haya terminado, seleccione **Listo.**

![Pizarra de la tienda en modo de ajuste (marco azul). Tenga en cuenta que la barra de la aplicación (parte superior) ha cambiado para incluir los botones "Listo" y "Quitar".](images/adjust-500px.png)

Las distintas aplicaciones pueden tener otras opciones en la barra de la aplicación. Por ejemplo, Microsoft Edge opciones *Desplazar,* *Arrastrar* *y Zoom.* 

![Barra de aplicaciones para aplicaciones 2D que se ejecutan en HoloLens](images/holobar-500px.png)

El **botón** Atrás vuelve a las pantallas vistas anteriormente en la aplicación. Se detendrá cuando llegue al principio de las experiencias que se muestran en la aplicación y no navegará a otras aplicaciones.

## <a name="getting-around-your-home"></a>Moverse por su casa

Con **HoloLens**, se desplaza por el espacio físico para moverse por su casa.

Con **los cascos envolventes,** puede moverse por el espacio de juego para moverse dentro de un área similar en el mundo virtual. Para desplazarse a través de distancias más largas, use el control de posición del controlador para "recorrer" virtualmente, o bien puede usar *la teleportación* para saltar inmediatamente distancias más largas.

![Teleportación en la Windows Mixed Reality inicio](images/teleportation-500px.png)

**Para teleportar:**
1. Abrir el reticle de teleportación.
   * Con [controladores de](../design/motion-controllers.md)movimiento: presione el control de posición hacia delante y mantén pulsado en esa posición.
   * Uso de un controlador de Xbox: presione el control de posición izquierdo hacia delante y sostenlo en esa posición.
   * Con un mouse: mantenga presionado el botón derecho del mouse (y use la rueda de desplazamiento para girar la dirección a la que desea dar la cara al teleportar).
2. Coloque el reticle donde desea teleportar.
   * Con [controladores de movimiento:](../design/motion-controllers.md)inclina el controlador (en el que mantienes el control hacia delante) para mover el reticle.
   * Uso de un controlador de Xbox: usa [la mirada](../design/gaze-and-commit.md) para mover el reticle.
   * Con un mouse: mueva el mouse para mover el reticle.
3. Suelte el botón para teleportar donde se colocó el reticle.

**Para "recorrer":**
* Con [controladores de](../design/motion-controllers.md)movimiento: haga clic en el botón de posición y mantenga presionado y, a continuación, mueva el control de posición en la dirección que desea "recorrer".
* Con un controlador de Xbox: haga clic en el botón de control izquierdo y mantenga presionado y, a continuación, mueva la chincheta en la dirección en la que desea "andar".

## <a name="immersive-headset-input-support"></a>Compatibilidad con la entrada de casco envolvente

[Windows Mixed Reality cascos envolventes](immersive-headset-hardware-details.md) admiten varios tipos de entrada para navegar por Windows Mixed Reality inicio. HoloLens no admite entradas de accesorios para la navegación, ya que se puede recorrer físicamente y ver el entorno. Sin embargo, HoloLens [admite entradas para](hardware-accessories.md) interactuar con las aplicaciones.

### <a name="motion-controllers"></a>Controladores de movimiento

La mejor Windows Mixed Reality experiencia será con controladores [](../design/motion-controllers.md) de movimiento de Windows Mixed Reality que admiten el seguimiento de seis grados de libertad mediante solo los sensores del casco, sin necesidad de cámaras ni marcadores externos.

Comandos de navegación próximamente.

### <a name="gamepad"></a>Controlador para juegos
* **Huella digital izquierda:**
  * Mantenga presionado el control de posición izquierdo hacia delante para abrir el [reticle de teleportación.](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
  * Pulse el botón de posición izquierdo, derecho o atrás para moverse a la izquierda, derecha o atrás en incrementos pequeños.
  * Haga clic en el botón de control izquierdo y mantenga presionado y, a continuación, mueva el control de posición en la dirección en la que [desea "recorrer" virtualmente.](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Pulse el **botón de posición derecho** a la izquierda o derecha para girar la dirección a la que se enfrenta 45 grados.
* Al presionar el **botón A,** se selecciona y actúa como el gesto [de pulsar en](../design/gaze-and-commit.md#composite-gestures) el aire.
* Al presionar **el botón** Guía, se abre [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu) y actúa como el gesto [de Bloom.](../design/system-gesture.md#bloom)
* Al presionar **los desencadenadores izquierdo y** derecho, puede acercar y alejar una aplicación de escritorio 2D con la que está interactuando en el hogar.

### <a name="keyboard-and-mouse"></a>Teclado y mouse

**Nota:** Use **Windows +Y para** cambiar el mouse entre controlar el escritorio del equipo y el Windows Mixed Reality inicio.

Dentro del Windows Mixed Reality inicio:
* Al presionar **el botón primario del** mouse, se selecciona y actúa como el gesto de pulsar [en](../design/gaze-and-commit.md#composite-gestures) el aire.
* Al mantener **presionado el botón derecho** del mouse, se abre el reticle [de](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportación.
* Al presionar **Windows** tecla en el teclado, se abre el menú [Inicio](navigating-the-windows-mixed-reality-home.md#start-menu) y actúa como el [gesto de bloom.](../design/system-gesture.md#bloom)
* Al [acceder](../design/gaze-and-commit.md) a una aplicación de escritorio  2D, puede hacer clic con el botón izquierdo  para **seleccionar,** hacer clic con el botón derecho para mostrar los menús contextuales y usar la rueda de desplazamiento para desplazarse (al igual que en el escritorio del equipo).

## <a name="cortana"></a>Cortana

[Cortana](../design/voice-input.md#hey-cortana) es su asistente personal en Windows Mixed Reality, al igual que en pc y teléfono. HoloLens tiene un micrófono integrado, pero los cascos envolventes pueden requerir hardware adicional. Use Cortana para abrir aplicaciones, reiniciar el dispositivo, buscar cosas en línea y mucho más. Los desarrolladores también pueden [optar por integrar Cortana](https://dev.windows.com/cortana) en sus experiencias.

También puede usar comandos de voz para moverse por su casa. Por ejemplo, apunte a un botón [(mediante](../design/gaze-and-commit.md) la mirada o un controlador, según el dispositivo) y diga "Seleccionar". Otros comandos de voz incluyen "Ir al inicio", "Más grande", "Más pequeño", "Cerrar" y "Orientar hacia mí".

## <a name="store-settings-and-system-apps"></a>Aplicaciones de almacenamiento, Configuración y del sistema

Windows Mixed Reality tiene varias aplicaciones integradas, como:
* **Microsoft Store** obtener aplicaciones y juegos
* **Centro de opiniones** enviar comentarios sobre las aplicaciones del sistema y del sistema
* **Configuración** configuración del sistema [(incluidas las redes y](/hololens/hololens-network) las actualizaciones del sistema)
* **Microsoft Edge** para examinar sitios web
* **Fotos** ver y compartir fotos y vídeos
* **Calibración** (HoloLens solo) para ajustar la experiencia HoloLens usuario actual
* **Aprenda gestos** (HoloLens) **o Descubrir la realidad mixta (cascos** envolventes) para obtener información sobre el uso del dispositivo.
* **Visor 3D** para decorar el mundo con contenido de realidad mixta
* **Portal de realidad mixta** (escritorio) para configurar y administrar los cascos envolventes y transmitir una vista previa en vivo de la vista en el casco para que otros usuarios puedan verlos.
* **Películas y televisión** para ver 360 vídeos y las películas y programas de televisión más recientes
* **Cortana** para todas las necesidades del asistente virtual
* **Escritorio** (cascos envolventes) para ver el monitor de escritorio mientras está en un casco envolvente
* **Explorador de archivos** Acceso a archivos y carpetas ubicados en el dispositivo

## <a name="see-also"></a>Consulte también
* [Vistas de aplicación](../design/app-views.md)
* [Controladores de movimiento](../design/motion-controllers.md)
* [Accesorios de hardware](hardware-accessories.md)
* [Consideraciones acerca del entorno en HoloLens](/hololens/hololens-environment-considerations)
* [Implementación de iniciadores de aplicaciones 3D](../distribute/implementing-3d-app-launchers.md)
* [Creación de modelos 3D para su uso en el Windows Mixed Reality principal](../distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)