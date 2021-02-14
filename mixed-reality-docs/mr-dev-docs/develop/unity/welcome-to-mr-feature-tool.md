---
title: Le damos la bienvenida a la herramienta de características de Mixed Reality
description: Conozca los aspectos básicos de la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 0aad81ddd625467dd9159232d590b1a4bf68d06b
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570258"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Le damos la bienvenida a la herramienta de características de Mixed Reality

![Imagen de banner de la herramienta de características de Mixed Reality](images/feature-tool-banner.png)

> [!IMPORTANT]
> La herramienta de características de Mixed Reality solo está disponible para Unity en este momento. Si usa el motor Unreal para el desarrollo, consulte la documentación de [instalación de herramientas](../install-the-tools.md).

La herramienta de características de Mixed Reality es una nueva manera de que los desarrolladores detecten, actualicen y agreguen paquetes de características de Mixed Reality en proyectos de Unity. Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación. Si nunca antes ha trabajado con un archivo de manifiesto, se trata de un archivo JSON que contiene todos los paquetes de proyectos. Una vez que haya validado los paquetes que quiere, la herramienta de características de Mixed Reality los descargará en el proyecto que elija.

## <a name="system-requirements"></a>Requisitos del sistema

Para que pueda ejecutar la herramienta de característica de Mixed Reality, necesitará lo siguiente:

* [Entorno de ejecución de .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> Actualmente, la herramienta de características de Mixed Reality solo se ejecuta en Windows, pero pronto estará disponible la compatibilidad con MacOS.

## <a name="download"></a>Descargar 

Una vez configurado el entorno, haga lo siguiente:

* [Descargue la última versión de la herramienta Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) del Centro de descarga de Microsoft.
* Una vez finalizada la descarga, descomprima el archivo y guárdelo en el escritorio.
    * Se recomienda crear un acceso directo al archivo ejecutable para obtener un acceso más rápido.

## <a name="1-getting-started"></a>1. Introducción

Inicie la herramienta de características de Mixed Reality desde el archivo ejecutable, que muestra la página de inicio en el primer inicio:

![Introducción](images/FeatureToolStart.png)

Desde la página de inicio, puede hacer lo siguiente:

* [Configurar](configuring-feature-tool.md) las opciones de la herramienta mediante el botón con el **icono de engranaje**.
* Usar el botón de **signo de interrogación** para iniciar el explorador web predeterminado y mostrar nuestra documentación
* Seleccionar **Iniciar** para empezar a explorar paquetes de características.

## <a name="2-discovering-and-acquiring-feature-packages"></a>2. Detección y adquisición de paquetes de características

El catálogo de paquetes de características se muestra en cuanto se presiona Iniciar. Las características se agrupan por categoría a fin de facilitar la búsqueda. Por ejemplo, la categoría **Mixed Reality Toolkit** tiene varias características entre las que puede elegir:

![Detección y adquisición](images/FeatureToolDiscovery.png)

Una vez que haya elegido las opciones, seleccione **Get features** (Obtener características) para capturar todos los paquetes necesarios del catálogo. Para obtener más información, consulte [Detección y adquisición de características](discovering-features.md).

## <a name="3-importing-feature-packages"></a>3. Importación de paquetes de características

Después de adquirirlo, el conjunto completo de paquetes se muestra en pantalla, junto con una lista de las dependencias necesarias. Si necesita cambiar su selección de características o paquetes, este es el momento:

![Importación de paquetes](images/FeatureToolImport.png)

Le recomendamos usar el botón **Validar** para asegurarse de que el proyecto de Unity pueda importar correctamente las características seleccionadas. Después de la validación, verá un cuadro de diálogo emergente con un mensaje de operación correcta o una lista de los problemas identificados.

También debe establecer la ubicación del proyecto de Unity de destino antes de realizar la importación. Use el botón de **puntos suspensivos** que hay en la izquierda del campo de ruta de acceso del proyecto para examinar la ubicación. Cuando haya terminado de desplazarse por el sistema de archivos, abra la carpeta que contiene el proyecto de Unity de destino.

> [!NOTE]
> El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo. Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.

Seleccione **Importar** para continuar.

> [!NOTE]
> Después de hacer clic en el botón **Importar**, si hay algún problema, se mostrará un mensaje simple. Se recomienda hacer clic en No y usar el botón **Validar** para ver y resolver los problemas.

Para más información, consulte [Importación de características](importing-features.md).

## <a name="4-reviewing-and-approving-project-changes"></a>4. Revisión y aprobación de los cambios del proyecto

El último paso consiste en revisar y aprobar los cambios propuestos en los archivos de manifiesto y proyecto:

* Los cambios propuestos en el manifiesto se muestran a la izquierda.
* Los archivos que se van a agregar al proyecto se muestran a la derecha.
* El botón **Comparar** permite ver el manifiesto actual y los cambios propuestos en paralelo.

![Authorization](images/FeatureToolApprovalRequest.png)

Para obtener más información, consulte [Revisión y aprobación de las modificaciones del proyecto](reviewing-changes.md).

## <a name="5-project-updated"></a>5. Proyecto actualizado

Cuando se aprueban los cambios propuestos, el proyecto de Unity de destino se actualiza para hacer referencia a las características de Mixed Reality seleccionadas:

![Proyecto actualizado](images/FeatureToolProjectUpdated.png)

La carpeta **Packages** del proyecto de Unity ahora tiene una subcarpeta **MixedReality** con los archivos del paquete de características, y el manifiesto contendrá las referencias correspondientes.

Vuelva a Unity, espere a que se carguen las nuevas características seleccionadas y empiece a crear contenido.

## <a name="see-also"></a>Vea también

- [Configuración de la herramienta de características](configuring-feature-tool.md)
- [Detección y adquisición](discovering-features.md)
- [Visualización de los detalles del paquete de características](viewing-package-details.md)
- [Importación de paquetes seleccionados](importing-features.md)
- [Revisión y aprobación de las modificaciones del proyecto](reviewing-changes.md)
