---
title: Configuración de la herramienta de características de Mixed Reality
description: Obtenga información sobre cómo descargar e instalar paquetes de Mixed Reality para Unity desde la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731954"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Configuración de la herramienta de características de Mixed Reality

Cuando usa la herramienta de características de Mixed Reality, tiene acceso a tres categorías de configuración diferentes que puede personalizar como desee:

* [Configuración de descarga](#download-settings)
* [Configuración de características](#feature-settings)
* [Importar configuración](#import-settings)

## <a name="download-settings"></a>Configuración de descarga

![Configuración de descarga](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>Sobrescribir archivos de paquete existentes

Al habilitar esta opción, se descargan los archivos del paquete cada vez que se adquieren. 

* **Le recomendamos mantener esta opción deshabilitada para reducir el uso del ancho de banda de red**.
* De manera predeterminada, los archivos de paquetes adquiridos previamente no se volverán a descargar.

### <a name="package-cache"></a>Memoria caché de paquetes

Cambie esta configuración para actualizar la ubicación en la que se descargan los paquetes de características.

> [!NOTE]
> Esta opción es de **solo lectura** en esta versión. Es posible que en versiones futuras se pueda configurar.

## <a name="feature-settings"></a>Configuración de características

![Configuración de características](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>Visualización de versiones preliminares

Habilite esta opción para adquirir versiones preliminares.
* De manera predeterminada, las versiones preliminares no se muestran en la herramienta de características de Mixed Reality. 

> [!NOTE]
> Cuando se define una versión preliminar, esta indica que contiene la designación **"-preview"** en la versión del paquete.

### <a name="show-early-access-program-features"></a>Visualización de características del programa de acceso anticipado

Habilite esta opción para adquirir características de las versiones de los programas de acceso anticipado registrados.

* De manera predeterminada, las características de acceso anticipado no se muestran en la herramienta de características de Mixed Reality. 

> [!NOTE]
> La habilitación de `Show early access program features` sin `Show preview releases` puede dar lugar a que los paquetes de acceso anticipado no aparezcan en la detección.

## <a name="import-settings"></a>Importar configuración

![Importar configuración](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>Reemplazo de los archivos de paquete existentes

De manera predeterminada, la herramienta de características de Mixed Reality quita las copias anteriores de los paquetes que se van a importar para reducir el tamaño de archivo y los cálculos innecesarios. 

* Desactive esta opción para conservar todas las versiones.

### <a name="project-relative-import-path"></a>Ruta de importación relativa del proyecto

Cambie esta configuración para actualizar la ruta de acceso de la carpeta del proyecto en la que se copian los paquetes de características durante la importación. 

* Por ejemplo, si la carpeta del proyecto es **C:\GalaxyExplorer**, la ruta de acceso de importación completa será **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Esta opción es de **solo lectura** en esta versión. Es posible que en versiones futuras se pueda configurar.

## <a name="early-access-settings"></a>Configuración de acceso anticipado

![Configuración de acceso anticipado](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>Pedido de confirmación antes de quitar un programa de acceso anticipado

Esta opción determina si se mostrará un aviso cada vez que se quite un programa de acceso anticipado.

### <a name="my-previews"></a>Mis versiones preliminares

Lista de programas de acceso anticipado registrados. Use `Add`, `Edit` y `Remove` para administrar la colección de programas registrados.

## <a name="diagnostic-settings"></a>Configuración de diagnóstico

![Configuración de diagnóstico](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>Archivo de registro

Muestra la ruta del archivo de registro de diagnóstico.

## <a name="see-also"></a>Vea también

- [Le damos la bienvenida a la herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md)