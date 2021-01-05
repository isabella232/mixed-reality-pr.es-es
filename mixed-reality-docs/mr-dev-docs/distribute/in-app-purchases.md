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
# <a name="in-app-purchases"></a>Compras desde la aplicación

Las compras desde la aplicación se admiten en HoloLens, pero hay algún trabajo para configurarlas.

Para usar la funcionalidad de compra de la aplicación, debe:
* Crear una [vista 2D](../design/app-views.md) de XAML para que aparezca como una pizarra
* Cambiar a él para activar la selección de ubicación, que deja la vista envolvente
* Llame a la API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Esta API abrirá el menú contextual de sistema operativo Windows que muestra el nombre, la descripción y el precio de la compra desde la aplicación. El usuario puede elegir opciones de compra. Una vez completada la acción, la aplicación necesitará presentar la interfaz de usuario, lo que permite al usuario volver a su [vista envolvente](../design/app-views.md).

En el caso de las aplicaciones destinadas a los auriculares que se encuentran en el escritorio con Windows Mixed Reality, no es necesario cambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.
