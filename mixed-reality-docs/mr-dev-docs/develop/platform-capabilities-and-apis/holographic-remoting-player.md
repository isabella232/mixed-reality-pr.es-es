---
title: Holographic Remoting Player
description: Obtenga información sobre Holographic Remoting Player y el streaming de contenido holográfico desde un equipo a su HoloLens en tiempo real a través de Wi-Fi.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/27/2021
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, diagnóstico, rendimiento
ms.openlocfilehash: 1e286612035a34c1bac174a620c350a91eb2b0fd59c3e808fe3a99368e03f43c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217154"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting Player

[Aprenda los conceptos básicos de la comunicación remota holográfica.](platform-capabilities-and-apis/holographic-remoting-overview.md)

>[!IMPORTANT]
>La comunicación remota holográfica HoloLens 2 es un cambio de versión principal. Las aplicaciones remotas [ **para HoloLens (1ª generación)**](add-holographic-remoting.md) deben usar la versión **1.x.x** del paquete de NuGet y las aplicaciones remotas para [ **HoloLens 2**](holographic-remoting-create-remote-wmr.md) deben usar **2.x.x**. Esto implica que las aplicaciones remotas escritas para HoloLens 2 no son compatibles con HoloLens (1.ª generación) y viceversa.

Holographic [Remoting Player](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) es una aplicación complementaria que se conecta a aplicaciones de PC y juegos que admiten la comunicación remota holográfica. El reproductor está disponible para HoloLens (primera generación) y HoloLens 2.  Las aplicaciones de PC que admiten la comunicación remota holográfica HoloLens deben actualizarse para admitir la comunicación remota holográfica con HoloLens 2. Póngase en contacto con el proveedor de aplicaciones si tiene alguna pregunta sobre qué versiones se admiten.

>[!TIP]
>A partir de la [versión 2.2.0,](holographic-remoting-version-history.md#v2.2.0) el reproductor de comunicación remota holográfica también está disponible para Windows equipos que ejecutan [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md).

>[!TIP]
>A partir de la [versión 2.4.0,](holographic-remoting-version-history.md#v2.4.0) se pueden crear aplicaciones remotas mediante [la API de OpenXR.](../native/openxr.md) Para empezar, consulte [Writing a Holographic Remoting remote app using OpenXR APIs](holographic-remoting-create-remote-openxr.md)(Escritura de una aplicación remota de comunicación remota holográfica mediante las API de OpenXR).

## <a name="connecting-to-the-holographic-remoting-player"></a>Conexión al reproductor de comunicación remota holográfica

Siga las instrucciones de la aplicación para conectarse a Holographic Remoting Player. Deberá escribir la dirección IP del dispositivo HoloLens, que puede ver en la pantalla principal del reproductor de comunicación remota, como se muestra a continuación:

![Holographic Remoting Player](images/holographicremotingplayer.png)

Cada vez que vea la pantalla principal, sabrá que no tiene una aplicación conectada.

La conexión remota holográfica no **está cifrada.** Siempre debe usar la comunicación remota holográfica a través de una conexión Wi-Fi segura en la que confíe.

## <a name="quality-and-performance"></a>Calidad y rendimiento

La calidad y el rendimiento de su experiencia variarán en función de tres factores:
* **La experiencia holográfica que** está ejecutando: las aplicaciones que representan contenido altamente detallado o de alta resolución pueden requerir un equipo más rápido o una conexión inalámbrica más rápida.
* **Hardware del equipo:** el equipo debe poder ejecutar y codificar la experiencia holográfica a 60 fotogramas por segundo. En el caso de una tarjeta gráfica, generalmente se recomienda geforce GTX 970 o AMD Radeon R9 290 o una versión más alta. Una vez más, su experiencia determinada puede requerir una tarjeta de nivel superior o inferior.
* **Su Wi-Fi conexión:** la experiencia holográfica se transmite a través de Wi-Fi. Use una red rápida con congestión baja para maximizar la calidad. El uso de un equipo conectado a través de un cable Ethernet, en lugar de Wi-Fi, también puede mejorar la calidad.

## <a name="diagnostics"></a>Diagnóstico

Para medir la calidad de la conexión, diga **"habilitar diagnósticos"** en la pantalla principal del reproductor de comunicación remota holográfica. Cuando se habilitan los diagnósticos, **HoloLens (primera generación)** la aplicación le mostrará:

* **FPS:** el número medio de fotogramas representados que el reproductor de comunicación remota recibe y representa por segundo. Lo ideal es 60 FPS.
* **Latencia:** la cantidad media de tiempo que tarda un fotograma en pasar del equipo al HoloLens. A menor, mejor. Esto depende en gran medida de la Wi-Fi red.

En **HoloLens 2** la aplicación le mostrará:

![Diagnósticos del reproductor de comunicación remota holográfica](images/holographicremotingplayer-diag.png)

* **Render:** número de fotogramas que el reproductor de comunicación remota representó durante el último segundo. Tenga en cuenta que esto es independiente del número de fotogramas que llegaron a través de la red (consulte **Fotogramas de vídeo).** Se muestra el tiempo delta de representación medio/máximo en milisegundos durante el último segundo entre fotogramas representados.

* **Fotogramas de** vídeo: el primer número que se muestra son fotogramas de vídeo omitido, el segundo fotogramas de vídeo reutilizados y el tercero fotogramas de vídeo recibidos. Todos los números representan el recuento en el último segundo.
    * ```Received frames``` es el número de fotogramas de vídeo que llegaron en el último segundo. En condiciones normales, debe ser 60, pero si no es así, es un indicador de que cualquiera de los fotogramas se descarta debido a problemas de red o el lado remoto o remoto no genera fotogramas con la velocidad esperada.
    * ```Reused frames``` es el recuento de fotogramas de vídeo usados más de una vez en el último segundo. Por ejemplo, si los fotogramas de vídeo llegan tarde, el  bucle de representación del reproductor sigue representando un fotograma, pero debe volver a usar el fotograma de vídeo que ya usó para el fotograma anterior.
    * ```Skipped frames``` es el recuento de fotogramas de vídeo, que el bucle de representación del reproductor no ha usado. Por ejemplo, la vibración de red puede tener el efecto de que los fotogramas de vídeo que llegan ya no se distribuyen uniformemente. Por ejemplo, si algunos llegan tarde y otros llegan a tiempo con el resultado de que ya no tienen una diferencia de 16,66 milisegundos cuando se ejecutan en 60 Hz. Puede ocurrir que llegue más de un fotograma entre dos pasos del bucle de representación del reproductor. En este caso, el reproductor omite uno o varios *fotogramas,* ya que se supone que siempre debe mostrar el fotograma de vídeo recibido más reciente.

    >[!NOTE]
    >Cuando se enfrenta a la vibración de la red, los fotogramas omitido y reutilizado suelen ser aproximadamente iguales. En cambio, si solo ve fotogramas omitido, esto es un indicador de que el reproductor no alcanza su velocidad de fotogramas objetivo. En este caso, debe estar atento al tiempo diferencial de representación máximo al diagnosticar problemas.

* **Diferencia de fotogramas de** vídeo: la diferencia mínima o máxima entre los fotogramas de vídeo recibidos en el último segundo. Este número normalmente se correlaciona con fotogramas omitido o reutilizado en caso de problemas causados por la vibración de la red.
* **Latencia:** el tiempo medio de respuesta en milisegundos en el último segundo. La respuesta en este contexto significa el tiempo desde el envío de datos de posición o sensor desde el HoloLens al lado remoto o remoto hasta que se muestra el fotograma de vídeo para los datos de posición o telemetría en la pantalla HoloLens pantalla.
* **Fotogramas de vídeo descartados:** el número de fotogramas de vídeo descartados en el último segundo y desde que se ha establecido una conexión. La causa principal de los fotogramas de vídeo descartados es cuando un fotograma de vídeo no llega en orden y, por ese motivo, debe descartarse, ya que ya hay uno más reciente. Esto es similar a *los fotogramas descartados,* pero la causa está en un nivel inferior en la pila de comunicación remota. Los fotogramas de vídeo descartados solo se esperan en condiciones de red no adecuadas.

Mientras se encuentra en la pantalla principal, puede decir **"deshabilitar diagnósticos"** para desactivar los diagnósticos.

## <a name="pc-system-requirements"></a>Requisitos del sistema de PC
* El equipo **debe ejecutar** la actualización Windows 10 aniversario o una versión más reciente.
* Se recomienda una tarjeta gráfica GeForce GTX 970 o AMD Radeon R9 290 o una mejor.
* Se recomienda conectar el equipo a la red a través de Ethernet para reducir el número de saltos inalámbricos.

## <a name="see-also"></a>Consulte también
* [HoloLens (primera generación): Agregar comunicación remota holográfica](add-holographic-remoting.md)
* [Escritura de una aplicación remota de Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de Holographic Remoting mediante las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Términos de licencia del software de control remoto de holografías](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)