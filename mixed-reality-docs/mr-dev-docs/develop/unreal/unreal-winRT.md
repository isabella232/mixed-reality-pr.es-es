---
title: WinRT en Unreal
description: Obtenga información sobre cómo escribir y administrar características de WinRT personalizadas en aplicaciones de realidad mixta no reales para dispositivos HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicación remota, realidad mixta, desarrollo, introducción, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, WinRT, DLL
ms.openlocfilehash: f32b5b3ddbee2e24e61d08b0a1b887b7b06e6da4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580410"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="2cf47-104">WinRT en Unreal</span><span class="sxs-lookup"><span data-stu-id="2cf47-104">WinRT in Unreal</span></span>

<span data-ttu-id="2cf47-105">En el transcurso del desarrollo de HoloLens, puede que tenga que escribir una característica con WinRT.</span><span class="sxs-lookup"><span data-stu-id="2cf47-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="2cf47-106">Por ejemplo, al abrir un cuadro de diálogo de archivo en una aplicación de HoloLens, se necesitaría el archivo de encabezado FileSavePicker en winrt/Windows. Storage. Picker. h.</span><span class="sxs-lookup"><span data-stu-id="2cf47-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="2cf47-107">WinRT es compatible con el sistema de compilación de la versión 4,26 en adelante.</span><span class="sxs-lookup"><span data-stu-id="2cf47-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="2cf47-108">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="2cf47-108">Next Development Checkpoint</span></span>

<span data-ttu-id="2cf47-109">Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="2cf47-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="2cf47-110">Desde aquí, puede continuar con cualquier [tema](unreal-development-overview.md#3-advanced-features) o ir directamente a la implementación de la aplicación en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="2cf47-110">From here, you can continue to any [topic](unreal-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2cf47-111">Implementación en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="2cf47-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="2cf47-112">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2cf47-112">See also</span></span>

* [<span data-ttu-id="2cf47-113">API/WinRT de C++</span><span class="sxs-lookup"><span data-stu-id="2cf47-113">C++/WinRT APIs</span></span>](/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="2cf47-114">FileSavePicker (clase)</span><span class="sxs-lookup"><span data-stu-id="2cf47-114">FileSavePicker class</span></span>](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="2cf47-115">Bibliotecas de terceros no reales</span><span class="sxs-lookup"><span data-stu-id="2cf47-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)