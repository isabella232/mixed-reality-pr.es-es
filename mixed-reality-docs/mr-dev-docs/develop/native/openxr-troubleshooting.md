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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="a5ec8-104">Solución de problemas de OpenXR</span><span class="sxs-lookup"><span data-stu-id="a5ec8-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="a5ec8-105">A continuación se muestran algunas sugerencias para la solución de problemas al desarrollar una aplicación de OpenXR mediante el tiempo de ejecución de Windows Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a5ec8-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="a5ec8-106">Si tiene alguna pregunta sobre la especificación de <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1,0</a>, visite los <a href="https://community.khronos.org/c/openxr" target="_blank">foros de Khronos OpenXR</a> o el <a href="https://khr.io/slack" target="_blank">margen de demora #openxr canal</a>.</span><span class="sxs-lookup"><span data-stu-id="a5ec8-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="a5ec8-107">Existen problemas conocidos en el tiempo de ejecución actual de Windows Mixed Reality OpenXR con las aplicaciones x86.</span><span class="sxs-lookup"><span data-stu-id="a5ec8-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="a5ec8-108">En este momento, debe compilar aplicaciones de escritorio OpenXR para x64.</span><span class="sxs-lookup"><span data-stu-id="a5ec8-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="a5ec8-109">La aplicación OpenXR no inicia Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a5ec8-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="a5ec8-110">Si la aplicación de OpenXR no inicia Windows Mixed Reality cuando se ejecuta, es posible que el tiempo de ejecución de Windows Mixed Reality OpenXR no se establezca como el tiempo de ejecución activo.</span><span class="sxs-lookup"><span data-stu-id="a5ec8-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="a5ec8-111">Siga las instrucciones para empezar a [trabajar con los auriculares de OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para solucionar el problema.</span><span class="sxs-lookup"><span data-stu-id="a5ec8-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="a5ec8-112">También puede ejecutar el [herramientas de desarrollo OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obtener ayuda para la solución de problemas en el estado de los sistemas Windows Mixed Reality OpenXR Runtime.</span><span class="sxs-lookup"><span data-stu-id="a5ec8-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>