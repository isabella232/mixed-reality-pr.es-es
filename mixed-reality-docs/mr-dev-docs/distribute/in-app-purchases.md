---
title: Compras desde la aplicación
description: Obtenga información sobre cómo usar compras desde la aplicación en las aplicaciones de realidad mixta con vistas XAML 2D y ventanas emergentes del sistema operativo Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras desde la aplicación, hololens, XAML, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: a87cc68f67def1d46a3a6ba352e723d356f51fa2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008675"
---
# <a name="in-app-purchases"></a><span data-ttu-id="54d1f-104">Compras desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="54d1f-104">In-app purchases</span></span>

<span data-ttu-id="54d1f-105">Las compras desde la aplicación se admiten en HoloLens, pero hay algún trabajo para configurarlas.</span><span class="sxs-lookup"><span data-stu-id="54d1f-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="54d1f-106">Para usar la funcionalidad de compra de la aplicación, debe:</span><span class="sxs-lookup"><span data-stu-id="54d1f-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="54d1f-107">Crear una [vista 2D](../design/app-views.md) de XAML para que aparezca como una pizarra</span><span class="sxs-lookup"><span data-stu-id="54d1f-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="54d1f-108">Cambiar a él para activar la selección de ubicación, que deja la vista envolvente</span><span class="sxs-lookup"><span data-stu-id="54d1f-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="54d1f-109">Llame a la API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="54d1f-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="54d1f-110">Esta API abrirá el menú contextual de sistema operativo Windows que muestra el nombre, la descripción y el precio de la compra desde la aplicación.</span><span class="sxs-lookup"><span data-stu-id="54d1f-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="54d1f-111">El usuario puede elegir opciones de compra.</span><span class="sxs-lookup"><span data-stu-id="54d1f-111">The user can then choose purchase options.</span></span> <span data-ttu-id="54d1f-112">Una vez completada la acción, la aplicación necesitará presentar la interfaz de usuario, lo que permite al usuario volver a su [vista envolvente](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="54d1f-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="54d1f-113">En el caso de las aplicaciones destinadas a los auriculares que se encuentran en el escritorio con Windows Mixed Reality, no es necesario cambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="54d1f-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
