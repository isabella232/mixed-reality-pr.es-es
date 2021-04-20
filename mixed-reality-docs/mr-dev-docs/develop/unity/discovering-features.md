---
title: Detección y adquisición de características
description: Detecte y descargue características de Mixed Reality.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 9f12a1eba0c28b89000f1541ba62747a03e3564b
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2021
ms.locfileid: "107732013"
---
# <a name="discovering-and-acquiring-features"></a>Detección y adquisición de características

En las secciones de este artículo se describe cómo buscar paquetes de características en la herramienta de características de Mixed Reality. Consulte la siguiente captura de pantalla si necesita la referencia de una sección determinada:

![Detección de características](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>Características disponibles

### <a name="category"></a>Category

La herramienta de características de Mixed Reality muestra una colección de categorías de características para que sea más fácil encontrar lo que quiere. Expanda cualquiera de las categorías para mostrar la colección de características disponibles.

> [!NOTE]
> Si no encuentra la funcionalidad que busca, consulte **Otras características**.

![Categoría de la característica](images/FeatureCategory.png)

El encabezado de categoría de la captura de pantalla anterior contiene las siguientes propiedades de izquierda a derecha:

- Botón para expandir y contraer
- Nombre de la categoría (p. ej., Mixed Reality Toolkit)
- Número de características seleccionadas
- Número de características disponibles
- Botones de selección

> [!NOTE]
> Los botones de selección distinguen el contexto. En función del estado de selección de una características dentro de la categoría, se mostrarán uno o varios de los botones `Select All` y `Select None`.

### <a name="feature"></a>Característica

![Entrada de característica](images/FeatureEntry.png)

Las características se muestran en la categoría correspondiente. Las entradas de características contienen los siguientes elementos, que aparecen de izquierda a derecha en la captura de pantalla anterior:

- Casilla de selección
- Nombre de la característica (p. ej., Mixed Reality Toolkit Foundation)
- Lista de las versiones disponibles
- Vínculo a los [detalles del paquete de características](viewing-package-details.md)

> [!NOTE]
> Si un programa de acceso anticipado (también denominado versión preliminar privada) proporciona una característica, se mostrará un icono indicador de ![acceso anticipado](images/EarlyAccess.png).

## <a name="refresh-the-feature-catalog"></a>Actualización del catálogo de características

Para comprobar si hay características nuevas y actualizadas, haga clic en el botón Actualizar ![botón Actualizar](images/RefreshButton.png) . De este modo, se conectará al sitio del catálogo y recuperará la información más reciente. Una vez que se haya leído el catálogo, se mostrará la fecha y la hora de la última actualización.

## <a name="select-features"></a>Selección de características

Para seleccionar características, expanda una categoría, seleccione una versión y haga clic en la casilla:

![Características seleccionadas](images/SelectedFeatures.png)

Para seleccionar cada paquete dentro de una categoría, se proporciona un botón `Select All`. `Select None` anulará la selección de todos los paquetes seleccionados. 

Cada categoría con una o más características seleccionadas se actualizará para mostrar el recuento.

## <a name="acquiring-features"></a>Adquisición de características

Una vez que haya elegido las características, seleccione **Get features** (Obtener características) para empezar a descargar los archivos del paquete de características seleccionados.

> [!NOTE]
> De manera predeterminada, los archivos del paquete de características adquiridos previamente no se volverán a descargar. Para cambiar este comportamiento, consulte [Configuración de la herramienta de características](configuring-feature-tool.md).

Una vez completada la descarga, la herramienta de características de Mixed Reality se desplazará al paso [Importación de características](importing-features.md).

## <a name="going-back-to-the-previous-step"></a>Vuelta al paso anterior

Desde **Discover features** (Detectar características), la herramienta de características de Mixed Reality permite volver a la selección de proyectos. Seleccione **Volver** para volver a comenzar.

## <a name="see-also"></a>Vea también

- [Le damos la bienvenida a la herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md)
- [Configuración de la herramienta de características](configuring-feature-tool.md)
- [Visualización de los detalles del paquete de características](viewing-package-details.md)
- [Importación de paquetes seleccionados](importing-features.md)
