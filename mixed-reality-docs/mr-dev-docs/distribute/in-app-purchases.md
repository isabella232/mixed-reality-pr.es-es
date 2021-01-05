---
title: Compras desde la aplicación
description: Las compras desde la aplicación se admiten en aplicaciones de realidad mixta, pero hay algún trabajo para configurarlas.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras desde la aplicación, hololens, XAML, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 905c1be72bf2a3d6fa167cab68a4cb71e6538acc
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757792"
---
# <a name="in-app-purchases"></a><span data-ttu-id="fe2cd-104">Compras desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="fe2cd-104">In-app purchases</span></span>

<span data-ttu-id="fe2cd-105">Las compras desde la aplicación se admiten en HoloLens, pero hay algún trabajo para configurarlas.</span><span class="sxs-lookup"><span data-stu-id="fe2cd-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="fe2cd-106">Para usar la funcionalidad de compra de la aplicación, debe:</span><span class="sxs-lookup"><span data-stu-id="fe2cd-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="fe2cd-107">Crear una [vista 2D](../design/app-views.md) de XAML para que aparezca como una pizarra</span><span class="sxs-lookup"><span data-stu-id="fe2cd-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="fe2cd-108">Cambiar a él para activar la selección de ubicación, que deja la vista envolvente</span><span class="sxs-lookup"><span data-stu-id="fe2cd-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="fe2cd-109">Llame a la API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="fe2cd-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="fe2cd-110">Esta API abrirá el menú contextual de sistema operativo Windows que muestra el nombre, la descripción y el precio de la compra desde la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fe2cd-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="fe2cd-111">El usuario puede elegir opciones de compra.</span><span class="sxs-lookup"><span data-stu-id="fe2cd-111">The user can then choose purchase options.</span></span> <span data-ttu-id="fe2cd-112">Una vez completada la acción, la aplicación necesitará presentar la interfaz de usuario, lo que permite al usuario volver a su [vista envolvente](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="fe2cd-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="fe2cd-113">En el caso de las aplicaciones destinadas a los auriculares que se encuentran en el escritorio con Windows Mixed Reality, no es necesario cambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="fe2cd-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
