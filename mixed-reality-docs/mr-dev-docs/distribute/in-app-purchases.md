---
title: Compras desde la aplicación
description: Las compras desde la aplicación se admiten en aplicaciones de realidad mixta, pero hay algún trabajo para configurarlas.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras desde la aplicación, hololens
ms.openlocfilehash: 7174fe555322216b7e547055aaaf7879c01d8f23
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691983"
---
# <a name="in-app-purchases"></a>Compras desde la aplicación

Las compras desde la aplicación se admiten en HoloLens, pero hay algún trabajo para configurarlas.

Para aprovechar la funcionalidad de compra de la aplicación, debe:
* Crear una [vista 2D](../design/app-views.md) de XAML para que aparezca como una pizarra
* Cambiar a él para activar la selección de ubicación, que deja la vista envolvente
* Llame a la API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Esta API abrirá el menú contextual de sistema operativo Windows que muestra el nombre, la descripción y el precio de la compra desde la aplicación. El usuario puede elegir opciones de compra. Una vez completada la acción, la aplicación necesitará presentar una interfaz de usuario que permita al usuario cambiar a su [vista envolvente](../design/app-views.md).

En el caso de las aplicaciones destinadas a auriculares con Windows Mixed Reality en el escritorio, no es necesario cambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.
