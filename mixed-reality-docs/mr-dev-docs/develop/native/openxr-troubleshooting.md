---
title: Solución de problemas de OpenXR
description: Busque recursos y respuestas a problemas comunes de solución de problemas Windows Mixed Reality aplicaciones OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, aplicación nativa, nativa, motor personalizado, middleware, solución de problemas
ms.openlocfilehash: 456dcf927c70aaaebc8dda1338d24acc910a1e801cf29e8880048d44f9432718
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219209"
---
# <a name="openxr-troubleshooting"></a>Solución de problemas de OpenXR

Estas son algunas sugerencias de solución de problemas al desarrollar una aplicación OpenXR mediante el Windows Mixed Reality en tiempo de ejecución de OpenXR.  Si tiene alguna otra pregunta sobre la especificación <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">de OpenXR 1.0,</a>visite los foros de <a href="https://community.khronos.org/c/openxr" target="_blank">OpenXR deIónronos</a> o <a href="https://khr.io/slack" target="_blank">slack #openxr canal</a>.

>[!NOTE]
>Hay problemas conocidos en el entorno de ejecución Windows Mixed Reality OpenXR con aplicaciones x86.  En este momento, debe compilar aplicaciones OpenXR de escritorio para x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>La aplicación OpenXR no se inicia Windows Mixed Reality

Si la aplicación OpenXR no se inicia Windows Mixed Reality al ejecutarla, es posible que Windows Mixed Reality OpenXR Runtime no se establezca como tiempo de ejecución activo. Siga las instrucciones para [empezar a trabajar con OpenXR Windows Mixed Reality cascos para](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) solucionar el problema.

También puede ejecutar [openxr Herramientas de desarrollo](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para Windows Mixed Reality ayuda para solucionar problemas sobre el estado de los sistemas Windows Mixed Reality openxr runtime.