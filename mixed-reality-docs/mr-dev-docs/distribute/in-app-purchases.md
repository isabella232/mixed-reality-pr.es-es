---
title: Compras desde la aplicación
description: Obtenga información sobre cómo usar las compras desde la aplicación en las aplicaciones de realidad mixta con vistas XAML 2D y acciones Windows emergente del sistema operativo.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras en la aplicación, hololens, XAML, cascos de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual
ms.openlocfilehash: fbb957d1044a5c76c19691b875de8f9513bfc4b49bc4cb0dbb98d045d615f1a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196153"
---
# <a name="in-app-purchases"></a>Compras desde la aplicación

Las compras desde la aplicación se admiten HoloLens, pero hay algún trabajo para configurarlas.

Para usar la funcionalidad de compra de aplicaciones, debe:
* Creación de una [vista 2D de](../design/app-views.md) XAML para que aparezca como una pizarra
* Cambie a él para activar la selección de ubicación, lo que deja la vista inmersiva.
* Llame a la API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Esta API mostrará las acciones Windows emergente del sistema operativo que muestra el nombre, la descripción y el precio de la compra en la aplicación. A continuación, el usuario puede elegir opciones de compra. Una vez completada la acción, la aplicación tendrá que presentar la interfaz de usuario, lo que permite al usuario volver a su [vista inmersiva.](../design/app-views.md)

En el caso de las aplicaciones que tienen como destino cascos envolventes basados Windows Mixed Reality escritorio, no es necesario cambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.