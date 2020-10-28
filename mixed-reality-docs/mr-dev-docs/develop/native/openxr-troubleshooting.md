---
title: Solución de problemas de OpenXR
description: Solucionar problemas en las aplicaciones de OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware, solución de problemas
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903098"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="feaf7-104">Solución de problemas de OpenXR</span><span class="sxs-lookup"><span data-stu-id="feaf7-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="feaf7-105">A continuación se muestran algunas sugerencias para la solución de problemas al desarrollar una aplicación de OpenXR mediante el tiempo de ejecución de Windows Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="feaf7-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="feaf7-106">Si tiene alguna pregunta sobre la especificación de <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1,0</a>, visite los foros de <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR</a> o el <a href="https://khr.io/slack" target="_blank">margen de demora #openxr canal</a>.</span><span class="sxs-lookup"><span data-stu-id="feaf7-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="feaf7-107">Existen problemas conocidos en el tiempo de ejecución actual de Windows Mixed Reality OpenXR con las aplicaciones x86.</span><span class="sxs-lookup"><span data-stu-id="feaf7-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="feaf7-108">En este momento, debe compilar aplicaciones de escritorio OpenXR para x64.</span><span class="sxs-lookup"><span data-stu-id="feaf7-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="feaf7-109">La aplicación OpenXR no inicia Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="feaf7-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="feaf7-110">Si la aplicación de OpenXR no inicia Windows Mixed Reality al ejecutarla, es posible que el tiempo de ejecución de Windows Mixed Reality OpenXR no se establezca como el tiempo de ejecución activo.</span><span class="sxs-lookup"><span data-stu-id="feaf7-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="feaf7-111">Siga las instrucciones para empezar a [trabajar con los auriculares de OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para activar el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feaf7-111">Be sure to follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="feaf7-112">También puede ejecutar el [herramientas de desarrollo OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) para obtener ayuda adicional sobre el estado del tiempo de ejecución de Windows Mixed Reality OpenXR en el sistema.</span><span class="sxs-lookup"><span data-stu-id="feaf7-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>