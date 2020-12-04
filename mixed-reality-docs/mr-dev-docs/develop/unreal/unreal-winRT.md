---
title: WinRT en Unreal
description: Información general del complemento de audio espacial para Unreal Engine.
author: hferrone
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicación remota, realidad mixta, desarrollo, introducción, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, WinRT, DLL
ms.openlocfilehash: ff0b235a45bf0e04b82e610384a290e8fc3a7525
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578600"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="d4e46-104">WinRT en Unreal</span><span class="sxs-lookup"><span data-stu-id="d4e46-104">WinRT in Unreal</span></span>

<span data-ttu-id="d4e46-105">En el transcurso del desarrollo de HoloLens, puede que tenga que escribir una característica con WinRT.</span><span class="sxs-lookup"><span data-stu-id="d4e46-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="d4e46-106">Por ejemplo, al abrir un cuadro de diálogo de archivo en una aplicación de HoloLens, se necesitaría el archivo de encabezado FileSavePicker en winrt/Windows. Storage. Picker. h.</span><span class="sxs-lookup"><span data-stu-id="d4e46-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="d4e46-107">WinRT es compatible con el sistema de compilación de la versión 4,26 en adelante.</span><span class="sxs-lookup"><span data-stu-id="d4e46-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="d4e46-108">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="d4e46-108">Next Development Checkpoint</span></span>

<span data-ttu-id="d4e46-109">Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d4e46-109">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="d4e46-110">Desde aquí, puede pasar a cualquier [tema](unreal-development-overview.md#3-platform-capabilities-and-apis) o ir directamente a la implementación de la aplicación en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="d4e46-110">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d4e46-111">Implementación en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="d4e46-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="d4e46-112">Vea también</span><span class="sxs-lookup"><span data-stu-id="d4e46-112">See also</span></span>
* [<span data-ttu-id="d4e46-113">API/WinRT de C++</span><span class="sxs-lookup"><span data-stu-id="d4e46-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="d4e46-114">FileSavePicker (clase)</span><span class="sxs-lookup"><span data-stu-id="d4e46-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="d4e46-115">Bibliotecas de terceros no reales</span><span class="sxs-lookup"><span data-stu-id="d4e46-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
