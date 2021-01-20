---
title: Compras desde la aplicación
description: Obtenga información sobre cómo usar compras desde la aplicación en las aplicaciones de realidad mixta con vistas XAML 2D y ventanas emergentes del sistema operativo Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras desde la aplicación, hololens, XAML, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: dfc5a0cfcc7a4d63147a753c8892d65dfae5e495
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582951"
---
# <a name="in-app-purchases"></a>Compras desde la aplicación

Las compras desde la aplicación se admiten en HoloLens, pero hay algún trabajo para configurarlas.

Para usar la funcionalidad de compra de la aplicación, debe:
* Crear una [vista 2D](../design/app-views.md) de XAML para que aparezca como una pizarra
* Cambiar a él para activar la selección de ubicación, que deja la vista envolvente
* Llame a la API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Esta API abrirá el menú contextual de sistema operativo Windows que muestra el nombre, la descripción y el precio de la compra desde la aplicación. El usuario puede elegir opciones de compra. Una vez completada la acción, la aplicación necesitará presentar la interfaz de usuario, lo que permite al usuario volver a su [vista envolvente](../design/app-views.md).

En el caso de las aplicaciones destinadas a los auriculares que se encuentran en el escritorio con Windows Mixed Reality, no es necesario cambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.