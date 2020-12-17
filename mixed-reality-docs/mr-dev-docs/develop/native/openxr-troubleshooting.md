---
title: Solución de problemas de OpenXR
description: Solucionar problemas en las aplicaciones de OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware, solución de problemas
ms.openlocfilehash: ddfe548d689d84576ad0ac06bda46d7c2757859c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612939"
---
# <a name="openxr-troubleshooting"></a>Solución de problemas de OpenXR

A continuación se muestran algunas sugerencias para la solución de problemas al desarrollar una aplicación de OpenXR mediante el tiempo de ejecución de Windows Mixed Reality OpenXR.  Si tiene alguna pregunta sobre la especificación de <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1,0</a>, visite los <a href="https://community.khronos.org/c/openxr" target="_blank">foros de Khronos OpenXR</a> o el <a href="https://khr.io/slack" target="_blank">margen de demora #openxr canal</a>.

>[!NOTE]
>Existen problemas conocidos en el tiempo de ejecución actual de Windows Mixed Reality OpenXR con las aplicaciones x86.  En este momento, debe compilar aplicaciones de escritorio OpenXR para x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>La aplicación OpenXR no inicia Windows Mixed Reality

Si la aplicación de OpenXR no inicia Windows Mixed Reality cuando se ejecuta, es posible que el tiempo de ejecución de Windows Mixed Reality OpenXR no se establezca como el tiempo de ejecución activo. Siga las instrucciones para empezar a [trabajar con los auriculares de OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para solucionar el problema.

También puede ejecutar el [herramientas de desarrollo OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obtener ayuda para la solución de problemas en el estado de los sistemas Windows Mixed Reality OpenXR Runtime.