---
title: Introducción al desarrollo con Native
description: Obtenga información sobre cómo crear un motor de realidad mixta basado en DirectX mediante Windows Mixed Reality API directamente.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, representación holográfica, aplicación nativa, nativa, WinRT, aplicación WinRT, API de plataforma, motor personalizado, middleware, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 056cb0c07002cb319e8acadf66e7f59650f5e00413440d6ad0103aa8ee936400
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200183"
---
# <a name="native-development-overview"></a>Introducción al desarrollo con Native

![Logotipo de banner nativo](../images/native_logo_banner.png)

Los motores 3D como [Unity](../unity/unity-development-overview.md) o [Unreal](../unreal/unreal-development-overview.md) no son las únicas rutas Mixed Reality desarrollo abiertas. También puede crear aplicaciones Mixed Reality mediante Windows Mixed Reality API con DirectX 11 o DirectX 12. Al ir al origen de la plataforma, básicamente está creando su propio middleware o marco de trabajo. 

> [!IMPORTANT]
> Si tienes un proyecto de WinRT existente que te gustaría mantener, ve a nuestra documentación [principal de WinRT.](creating-a-holographic-directx-project.md) 

## <a name="development-checkpoints"></a>Puntos de control de desarrollo

Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unity en el mundo de la realidad mixta.

### <a name="1-getting-started"></a>1. Introducción

Windows Mixed Reality admite [dos tipos de aplicaciones:](../../design/app-views.md)
* UWP o Win32 **Mixed Reality** aplicaciones que usan [HolographicSpace API](getting-a-holographicspace.md) o [](../../design/app-views.md) [OpenXR API](openxr.md) para representar una vista inmersiva que llena la pantalla del casco
* **Aplicaciones 2D** (UWP) que usan DirectX, XAML u otro marco para representar vistas [2D](../../design/app-views.md#2d-views) en pizarras en el Windows Mixed Reality principal

Las diferencias entre el desarrollo de DirectX para [vistas 2D](../../design/app-views.md) y vistas inmersivas se refieren principalmente a la representación holográfica y la entrada espacial. El elemento [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) de la aplicación para UWP o el HWND de la aplicación Win32 son necesarios y permanecen prácticamente iguales. Lo mismo sucede con las API de WinRT que están disponibles para la aplicación. Pero debe usar un subconjunto diferente de estas API para aprovechar las características holográficas. Por ejemplo, el sistema para aplicaciones holográficas administra la cadena de intercambio y el marco presentes para habilitar un bucle de marco predicho.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Bloques de creación principales

Windows Mixed Reality aplicaciones usan las siguientes API para crear [experiencias](../../discover/mixed-reality.md) de realidad mixta para HoloLens y otros cascos envolventes:

|  Característica  |  Funcionalidad  |
| --- | --- |
| [Gaze](../../design/gaze-and-commit.md) | Permite que los usuarios se dirijan a los hologramas mediante su mirada. |
| [Gesto](../../design/gaze-and-commit.md#composite-gestures) | Adición de acciones espaciales a las aplicaciones |
| [Representación de holografías](../platform-capabilities-and-apis/rendering.md) | Dibujar un holograma en una ubicación precisa del mundo en torno a los usuarios |
| [Controlador de movimiento](../../design/motion-controllers.md) | Permitir que los usuarios tomen medidas en Mixed Reality entornos |
| [Asignación espacial](../../design/spatial-mapping.md) | Permite asignar su espacio físico con una superposición de malla virtual para marcar los límites de su entorno. |
| [Voz](../../design/voice-input.md) | Permite capturar palabras clave, frases y dictado en voz alta de los usuarios. |
 
> [!NOTE]
> Puede encontrar las próximas características principales y en desarrollo en la documentación del mapa de ruta [de](openxr.md#roadmap) OpenXR.

### <a name="3-deploying-and-testing"></a>3. Implementación y pruebas

Puede desarrollar en un escritorio mediante OpenXR en un HoloLens 2 o Windows Mixed Reality casco envolvente.  Si no tiene acceso a un casco, puede usar el HoloLens 2 Emulator [o](../platform-capabilities-and-apis/using-the-hololens-emulator.md) el simulador de Windows Mixed Reality [en](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) su lugar.

## <a name="whats-next"></a>¿Qué sigue?

Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK. Las secciones siguientes pueden llevarle a áreas más allá del material de nivel principiante que ya ha completado. Estos temas y recursos no están en orden secuencial, así que no dude en saltar y explorar.

### <a name="additional-resources"></a>Recursos adicionales

Si quiere subir el nivel del juego de OpenXR, consulte los vínculos siguientes:

* [Procedimientos recomendados de OpenXR](openxr-best-practices.md)
* [Rendimiento de OpenXR](openxr-performance.md)
* [Solución de problemas de OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>Consulte también
* [Modelo de aplicaciones](../../design/app-model.md)
* [Vistas de aplicación](../../design/app-views.md)