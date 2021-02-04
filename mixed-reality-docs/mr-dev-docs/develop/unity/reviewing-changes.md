---
title: Autorización de cambios en el proyecto
description: Obtenga información sobre cómo autorizar los cambios en el proyecto en la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243974"
---
# <a name="authorizing-project-changes"></a>Autorización de cambios en el proyecto

Antes de modificar el proyecto de Unity, los cambios en el manifiesto y los archivos del proyecto deben revisarse y aprobarse:

![Solicitud de autorización](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>Manifest

Los cambios en el manifiesto propuestos se pueden ver en la columna **Manifiesto** de la izquierda. Este contenido es exactamente el que se escribirá en el manifiesto del proyecto (**Packages/manifest.json**):

![Vista previa del manifiesto](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>Archivos que se copiarán en el proyecto

En la sección **Files to be copied into the project** (Archivos que se copiarán en el proyecto) de la derecha se muestra los archivos del paquete de características específicos que se copiarán en el proyecto de Unity:

![Vista previa del manifiesto con los archivos que se copiarán](images/FilesToCopy.png)

## <a name="compare-manifests"></a>Comparación de manifiestos

Para ver una comparación en paralelo detallada de todos los cambios propuestos, seleccione **Comparar**:

![Comparación de manifiestos](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>Aprobación de cambios

Cuando se aprueben los cambios propuestos, los archivos de la lista se copiarán en el proyecto de Unity y el manifiesto se actualizará con las referencias a estos archivos.

> [!NOTE]
> Los archivos del paquete de características (*.tgz) se deben agregar al control de código fuente. Se hace referencia a ellos mediante una ruta de acceso relativa para permitir que los equipos de desarrollo compartan fácilmente las características y los cambios del manifiesto.

 Como parte de las modificaciones, se realizará una copia de seguridad del archivo **manifest.json** actual.

> [!IMPORTANT]
> Al ver las copias de seguridad del manifiesto, la más antigua se denominará **manifest.json.backup**. Las copias de seguridad más recientes se anotarán con un valor numérico, empezando por cero (0).

## <a name="going-back-to-the-previous-step"></a>Vuelta al paso anterior

Si necesita realizar cambios en las selecciones de características, use **Volver** para regresar al paso de [importación](importing-features.md).

## <a name="see-also"></a>Vea también

- [Le damos la bienvenida a la herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md)
- [Importación de paquetes seleccionados](importing-features.md)
