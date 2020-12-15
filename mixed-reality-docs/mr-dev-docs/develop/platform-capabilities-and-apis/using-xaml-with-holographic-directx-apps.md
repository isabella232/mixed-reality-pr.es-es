---
title: Uso de XAML con aplicaciones de DirectX holográficas
description: Explica el impacto de cambiar entre las vistas XAML 2D y las vistas de envolvente en la aplicación DirectX y cómo hacer un uso eficaz de una vista XAML y una vista envolvente.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, UWP, administración de vistas de aplicaciones, XAML, teclado, tutorial, DirectX
ms.openlocfilehash: b062efadca9ccfe2e2caeb054f662becc0807b50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530273"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Uso de XAML con aplicaciones de DirectX holográficas

> [!NOTE]
> Este artículo está relacionado con las API nativas de WinRT heredadas.  En el caso de los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](../native/openxr-getting-started.md)**.

En este tema se explica el impacto del cambio entre las [vistas XAML 2D y las vistas de envolvente](../../design/app-views.md) en la aplicación DirectX y cómo hacer un uso eficaz de una vista XAML y una vista envolvente.

## <a name="xaml-view-switching-overview"></a>Información general sobre el cambio de vista XAML

En HoloLens, una aplicación envolvente que puede mostrar más adelante una vista XAML 2D debe inicializar esa vista XAML primero y cambiar inmediatamente a una vista envolvente desde allí. XAML se cargará antes de que la aplicación pueda hacer nada, lo que agrega un pequeño aumento en el tiempo de inicio. XAML seguirá ocupando espacio en la memoria en el proceso de la aplicación mientras se mantiene en segundo plano. La cantidad de retraso de inicio y el uso de memoria depende de lo que hace la aplicación con XAML antes de cambiar a la vista nativa. Si no hace nada en el código de inicio XAML en primer lugar, excepto iniciar la vista envolvente, el impacto debe ser menor. Además, dado que la representación holográfica se realiza directamente en la vista envolvente, evitará las restricciones relacionadas con XAML en esa representación.

Los recuentos de uso de memoria para CPU y GPU. Direct3D 11 puede intercambiar la memoria de los gráficos virtuales, pero es posible que no pueda intercambiar algunos o todos los recursos de GPU de XAML, y puede haber un descenso significativo en el rendimiento. En cualquier caso, si no se cargan las características de XAML que no necesite, dejará más espacio para la aplicación y proporcionará una mejor experiencia.

## <a name="xaml-view-switching-workflow"></a>Flujo de trabajo de cambio de vista XAML

El flujo de trabajo de una aplicación que va directamente desde XAML al modo inmersivo es como el siguiente:
* La aplicación se inicia en la vista XAML 2D.
* La secuencia de inicio de XAML de la aplicación detecta si el sistema actual admite la representación holográfica:
* Si es así, la aplicación crea la vista envolvente y la pone en primer plano de forma inmediata. La carga de XAML se omite para cualquier elemento que no sea necesario en dispositivos de Windows Mixed Reality, incluidas las clases de representación y la carga de recursos en la vista XAML. Si la aplicación usa XAML para la entrada de teclado, la página de entrada se debe crear.
* Si no es así, la vista XAML puede continuar con la empresa como de costumbre.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Sugerencia para representar gráficos en ambas vistas

Si la aplicación necesita implementar una cantidad de representación en DirectX para la vista XAML en Windows Mixed Reality, la mejor opción es crear un representador que pueda funcionar con ambas vistas. El representador debe ser una instancia a la que se pueda tener acceso desde ambas vistas y debe cambiar entre la representación 2D y holográfica. De esta forma, los recursos de GPU solo se cargan una vez, lo que reduce los tiempos de carga, el impacto en la memoria y la cantidad de recursos intercambiados al cambiar de vista.
