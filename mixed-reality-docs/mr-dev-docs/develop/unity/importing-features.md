---
title: Importación de características
description: Obtenga información sobre cómo importar e instalar características desde la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230835"
---
# <a name="importing-features"></a>Importación de características

Una vez que se han descargado las características, se pueden revisar e importar en el proyecto de Unity. En este paso, la ventana de la aplicación debería tener un aspecto similar al de la siguiente imagen:

![Importación de características](images/FeatureToolImport.png)

## <a name="features-list"></a>Lista de características

La lista **Características** contiene la colección de paquetes seleccionados durante la detección. Las características se pueden seleccionar o deseleccionar antes de la importación. Los detalles del paquete se pueden ver mediante el vínculo **Detalles** que se muestra a continuación.

![Lista de características](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>Lista de dependencias requeridas

La lista **Dependencias requeridas** contiene los paquetes que una o varias de las características seleccionadas necesitan para funcionar. Esta lista también contendrá las dependencias de las dependencias. Cada dependencia se puede seleccionar o deseleccionar antes de la importación. Los detalles del paquete se pueden ver mediante el vínculo **Detalles** que se muestra a continuación.

![Lista de dependencias](images/RequiredDependencyList.png)

> [!NOTE]
> Si se anula la selección de las dependencias requeridas, se producirán uno o varios errores debidos a la ausencia de dichas dependencias al cargar el proyecto en Unity. Estas características no se podrán usar en el proyecto.

## <a name="validating-selections"></a>Validación de selecciones

Se recomienda validar las selecciones de características antes de la importación. Este paso presentará los problemas que es probable que impidan el desarrollo correcto del proyecto.

![Problemas de validación](images/ValidationIssues.png)

La herramienta de características de Mixed Reality ofrece dos resoluciones de problemas automáticas que se describen en las secciones siguientes, así como la opción de cancelar y resolver problemas manualmente.

### <a name="enable-dependencies"></a>Habilitación de dependencias

El botón **Enable dependencies** (Habilitar dependencias) volverá a seleccionar automáticamente las dependencias que falten. Esto se aplica a las dependencias que se seleccionaron explícitamente (aparecen en la lista de **Características**) y a las que se seleccionaron implícitamente en función de los requisitos de las características seleccionadas.

### <a name="disable-features"></a>Deshabilitación de características

Al seleccionar **Disable features** (Deshabilitar características), se anulará automáticamente la selección de cualquier característica que dependa de una o varias de las dependencias que se deseleccionaron. Esto se aplica a los paquetes de dependencia seleccionados implícitamente y a las características seleccionadas explícitamente.

## <a name="importing"></a>Importación

Seleccione **Importar** para agregar las características seleccionadas y dé su [aprobación final](reviewing-changes.md) antes de actualizar el proyecto de destino.

> [!IMPORTANT]
> Si sigue existiendo un problema de validación al realizar la importación, se mostrará un mensaje de advertencia. Se recomienda seleccionar No, hacer clic en **Validar** y resolver los problemas que se presenten.
>
> ![Continuar con problemas de validación](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>Vuelta al paso anterior

Desde **Import features** (Importar características), la herramienta de características de Mixed Reality permite volver a la pantalla de [detección](discovering-features.md). Seleccione **Volver** para descargar otros paquetes de características.

## <a name="see-also"></a>Vea también

- [Le damos la bienvenida a la herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md)
- [Detección y adquisición](discovering-features.md)
- [Visualización de los detalles del paquete de características](viewing-package-details.md)
- [Revisión y aprobación de las modificaciones del proyecto](reviewing-changes.md)