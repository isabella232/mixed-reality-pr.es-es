---
title: Configuración de la herramienta de características de Mixed Reality
description: Obtenga información sobre cómo descargar e instalar paquetes de Mixed Reality para Unity desde la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244015"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Configuración de la herramienta de características de Mixed Reality

Cuando usa la herramienta de características de Mixed Reality, tiene acceso a tres categorías de configuración diferentes que puede personalizar como desee:

* [Configuración de descarga](#download-settings)
* [Configuración de características](#feature-settings)
* [Importar configuración](#import-settings)

![Configuración](images/FeatureToolSettings.png)

## <a name="download-settings"></a>Configuración de descarga

### <a name="overwrite-existing-package-files"></a>Sobrescribir archivos de paquete existentes

Al habilitar esta opción, se descargan los archivos del paquete cada vez que se adquieren. 
* **Le recomendamos mantener esta opción deshabilitada para reducir el uso del ancho de banda de red**.
* De manera predeterminada, los archivos de paquetes adquiridos previamente no se volverán a descargar.

### <a name="package-cache"></a>Memoria caché de paquetes

Cambie esta configuración para actualizar la ubicación en la que se descargan los paquetes de características.

> [!NOTE]
> Esta opción es de **solo lectura** en esta versión. Es posible que en versiones futuras se pueda configurar.

## <a name="feature-settings"></a>Configuración de características

### <a name="include-preview-releases"></a>Inclusión de versiones preliminares

Habilite esta opción para adquirir versiones preliminares.
* De manera predeterminada, las versiones preliminares no se muestran en la herramienta de características de Mixed Reality. 

> [!NOTE]
> Cuando se define una versión preliminar, esta indica que contiene la designación **"-preview"** en la versión del paquete.

## <a name="import-settings"></a>Importar configuración

### <a name="replace-existing-package-files"></a>Reemplazo de los archivos de paquete existentes

De manera predeterminada, la herramienta de características de Mixed Reality quita las copias anteriores de los paquetes que se van a importar para reducir el tamaño de archivo y los cálculos innecesarios. 
* Desactive esta opción para conservar todas las versiones.

### <a name="project-relative-import-path"></a>Ruta de importación relativa del proyecto

Cambie esta configuración para actualizar la ruta de acceso de la carpeta del proyecto en la que se copian los paquetes de características durante la importación. 
* Por ejemplo, si la carpeta del proyecto es **C:\GalaxyExplorer**, la ruta de acceso de importación completa será **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Esta opción es de **solo lectura** en esta versión. Es posible que en versiones futuras se pueda configurar.

## <a name="see-also"></a>Vea también

- [Le damos la bienvenida a la herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md)