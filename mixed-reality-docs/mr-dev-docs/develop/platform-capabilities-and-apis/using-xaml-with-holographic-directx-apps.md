---
title: Uso de XAML con aplicaciones de DirectX holográficas
description: Explica el impacto de cambiar entre vistas XAML 2D y vistas inmersivas en la aplicación DirectX, y cómo hacer un uso eficaz de una vista XAML y una vista inmersiva.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows mixed reality, UWP, administración de vistas de aplicaciones, xaml, teclado, tutorial, DirectX
ms.openlocfilehash: 3c7edfdf4ff2ed629699dca0514efabc9ce7241cb1781e4b9c914ad4bff1f900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220951"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Uso de XAML con aplicaciones de DirectX holográficas

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](../native/openxr-getting-started.md)**.

En este tema se explica el impacto de cambiar entre vistas [XAML 2D](../../design/app-views.md) y vistas inmersivas en la aplicación DirectX, y cómo hacer un uso eficaz de una vista XAML y una vista inmersiva.

## <a name="xaml-view-switching-overview"></a>Introducción a la conmutación de vistas XAML

En HoloLens, una aplicación inmersiva que posteriormente pueda mostrar una vista XAML 2D debe inicializar esa vista XAML primero y cambiar inmediatamente a una vista inmersiva desde allí. XAML se cargará antes de que la aplicación pueda hacer nada, lo que agrega un pequeño aumento al tiempo de inicio. XAML seguirá ocupando espacio de memoria en el proceso de la aplicación mientras permanece en segundo plano. La cantidad de retraso de inicio y el uso de memoria depende de lo que haga la aplicación con XAML antes de cambiar a la vista nativa. Si al principio no hace nada en el código de inicio XAML excepto iniciar la vista inmersiva, el impacto debe ser menor. Además, dado que la representación holográfica se realiza directamente en la vista inmersiva, evitará las restricciones relacionadas con XAML en esa representación.

Recuentos de uso de memoria para CPU y GPU. Direct3D 11 puede intercambiar memoria de gráficos virtuales, pero es posible que no pueda intercambiar algunos o todos los recursos de GPU XAML y podría haber un impacto notable en el rendimiento. En cualquier caso, no cargar ninguna de las características XAML que no necesite dejará más espacio para la aplicación y proporcionará una mejor experiencia.

## <a name="xaml-view-switching-workflow"></a>Flujo de trabajo de conmutación de vista XAML

El flujo de trabajo de una aplicación que va directamente desde XAML al modo inmersivo es como este:
* La aplicación se inicia en la vista XAML 2D.
* La secuencia de inicio XAML de la aplicación detecta si el sistema actual admite la representación holográfica:
* Si es así, la aplicación crea la vista inmersiva y la pone en primer plano de inmediato. La carga de XAML se omite para cualquier cosa que no sea necesaria Windows Mixed Reality dispositivos, incluidas las clases de representación y la carga de recursos en la vista XAML. Si la aplicación usa XAML para la entrada de teclado, se debe crear esa página de entrada.
* Si no es así, la vista XAML puede continuar con el negocio como de costumbre.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Sugerencia para representar gráficos en ambas vistas

Si la aplicación necesita implementar cierta cantidad de representación en DirectX para la vista XAML en Windows Mixed Reality, la mejor opción es crear un representador que pueda trabajar con ambas vistas. El representador debe ser una instancia a la que se pueda acceder desde ambas vistas y debe cambiar entre la representación holográfica y 2D. De este modo, los recursos de GPU solo se cargan una vez, lo que reduce los tiempos de carga, el impacto en la memoria y la cantidad de recursos intercambiados al cambiar de vista.
