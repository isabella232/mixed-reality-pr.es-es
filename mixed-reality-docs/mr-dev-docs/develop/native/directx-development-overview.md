---
title: Introducción al desarrollo con Native
description: Cree un motor de realidad mixta basado en DirectX mediante las API de realidad mixta de Windows directamente.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, representación holográfica, nativa, aplicación nativa, WinRT, aplicación de WinRT, API de plataforma, motor personalizado, middleware, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 0d5e364fdb4faac73f28649f5c009823a74ac595
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679654"
---
# <a name="native-development-overview"></a>Introducción al desarrollo con Native

![Logotipo de banner nativo](../images/native_logo_banner.png)

los motores 3D como [Unity](../unity/unity-development-overview.md) o las no [reales](../unreal/unreal-development-overview.md) no son las únicas rutas de desarrollo de realidad mixta que se abren. También puede crear aplicaciones de realidad mixta mediante la codificación directa en las API de Windows Mixed Reality con DirectX 11 o DirectX 12. Al aprovechar la plataforma directamente, básicamente está creando su propio middleware o marco. 

> [!IMPORTANT]
> Si tiene un proyecto de WinRT existente que le gustaría mantener, diríjase a nuestra documentación principal de [winrt](creating-a-holographic-directx-project.md). 

## <a name="development-checkpoints"></a>Puntos de control de desarrollo

Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unity en el mundo de la realidad mixta.

### <a name="1-getting-started"></a>1. Introducción

Windows Mixed Reality admite [dos tipos de aplicaciones](../../design/app-views.md):
* **Aplicaciones de realidad mixta** (UWP o Win32) que usan la [API de HOLOGRAPHICSPACE](getting-a-holographicspace.md) o la [API de OpenXR](openxr.md) para presentar una [vista envolvente](../../design/app-views.md) al usuario que rellena la pantalla del casco
* **aplicaciones 2D** (UWP) que usan DirectX, XAML u otro marco de trabajo para representar [vistas 2D](../../design/app-views.md#2d-views) en pizarras en la Página principal de Windows Mixed Reality

Las diferencias entre el desarrollo de DirectX para [vistas 2D y vistas envolventes](../../design/app-views.md) se refieren principalmente a la representación holográfica y la entrada espacial. El HWND de la aplicación de [UWP o el](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) HWND de la aplicación de Win32 son necesarios y permanecen en gran medida. Lo mismo se aplica a las API de WinRT que están disponibles para la aplicación. Sin embargo, debe usar un subconjunto diferente de estas API para aprovechar las características holográficas. Por ejemplo, el sistema intercambio y el marco actual se administran mediante el sistema para aplicaciones holográficas con el fin de habilitar un bucle de trama de predicción de supuestos.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Bloques de creación principales

Las aplicaciones de Windows Mixed Reality usan las siguientes API para compilar experiencias de [realidad mixta](../../discover/mixed-reality.md) para HoloLens y otros auriculares envolventes:

|  Característica  |  Funcionalidad  |
| --- | --- |
| [Gaze](../../design/gaze-and-commit.md) | Permite que los usuarios se dirijan a los hologramas mediante su mirada. |
| [Gesto](../../design/gaze-and-commit.md#composite-gestures) | Agregar acciones espaciales a las aplicaciones |
| [Representación de holografías](../platform-capabilities-and-apis/rendering.md) | Dibuje un holograma en una ubicación precisa del mundo en torno a los usuarios |
| [Controlador de movimiento](../../design/motion-controllers.md) | Permita que los usuarios tomen medidas en sus entornos de realidad mixta. |
| [Asignación espacial](../../design/spatial-mapping.md) | Permite asignar su espacio físico con una superposición de malla virtual para marcar los límites de su entorno. |
| [Voz](../../design/voice-input.md) | Permite capturar palabras clave, frases y dictado en voz alta de los usuarios. |
 
> [!NOTE]
> Puede encontrar características principales futuras y en desarrollo en la documentación del [plan](openxr.md#roadmap) de OpenXR.

### <a name="3-deploying-and-testing"></a>3. implementación y prueba

Puede desarrollar con OpenXR en un casco envolvente HoloLens 2 o de Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el [emulador de HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) o el [simulador de realidad mixta de Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) en su lugar.

## <a name="whats-next"></a>¿Qué sigue?

Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK. En las secciones siguientes se le proporcionará contenido más ampliado sobre lo que ha visto en el nivel principiante, junto con recursos útiles por si se queda bloqueado. Tenga en cuenta que estos temas y recursos no están ordenados de forma secuencial, de modo que no dude en consultar los que le interesen y explorarlos.

### <a name="additional-resources"></a>Recursos adicionales

Si desea realizar un seguimiento del juego de OpenXR, consulte los vínculos siguientes:

* [Procedimientos recomendados de OpenXR](openxr-best-practices.md)
* [Rendimiento de OpenXR](openxr-performance.md)
* [Solución de problemas de OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>Vea también
* [Modelo de aplicaciones](../../design/app-model.md)
* [Vistas de aplicación](../../design/app-views.md)
