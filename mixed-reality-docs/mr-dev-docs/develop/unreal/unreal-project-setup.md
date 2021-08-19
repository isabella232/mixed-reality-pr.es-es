---
title: Configuración del proyecto con Unreal
description: Obtenga información sobre cómo configurar el proyecto con la versión más reciente de Unreal Engine y Mixed Reality Feature Tool.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, mixed reality, development, features, new project, emulator, documentation, guides, holograms, game development, mixed reality headset, windows mixed reality headset, virtual reality headset, up-to-date, tools, get started, basics, unreal, toolkit, hub, installation, Windows, HoloLens, openxr, mrtk
ms.openlocfilehash: fee0e9a9deb92dffca742e19ebe27d2dd4cb53c0
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905594"
---
# <a name="setting-up-your-unreal-project"></a>Configuración del proyecto con Unreal

Se recomienda instalar [Unreal Engine, versión 4.25 ](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o posterior, para aprovechar al máximo la compatibilidad integrada de HoloLens.

Vaya a la pestaña **Biblioteca** en Selector de juegos Epic, seleccione la flecha desplegable situada junto a **Lanzar** > y haga clic en **Opciones**. En **Target Platforms** (Plataformas de destino), selecciona **HoloLens 2** y haz clic en **Aplicar**.
![Opción de instalación no real de HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importación de Mixed Reality Toolkit para Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta. MRTK proporciona un sistema de entrada multiplataforma, componentes fundamentales y bloques de creación comunes para interacciones espaciales. El kit de herramientas está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.

Si aún no tiene un proyecto de realidad mixta, siga las tres primeras secciones de los [tutoriales de Introducción a HoloLens 2](tutorials/unreal-uxt-ch1.md) para preparar un proyecto para MRTK.

### <a name="introducing-the-mrtk-hub-for-unreal"></a>Presentación de MRTK Hub para Unreal

Se recomienda usar MRTK Hub para adquirir complementos de MRTK. Es una nueva manera de que los desarrolladores detecten y actualicen los complementos de Microsoft Mixed Reality y los agreguen a sus proyectos de Unreal. Puede ver complementos, ver sus dependencias e instalarlos en el proyecto sin salir del editor de Unreal.

- Descubra los nuevos complementos de Microsoft Mixed Reality e instálelos junto con sus dependencias en el proyecto de Unreal.
- Mantenga actualizados los complementos de Microsoft Mixed Reality.
- Elimine los complementos de Microsoft Mixed Reality del proyecto si ya no los necesita.

> [!NOTE]
> MRTK Hub para Unreal solo está disponible para Unreal Engine versión 4.26 o posterior. Para Unreal Engine 4.25, puede obtener complementos de MRTK desde Unreal Engine Marketplace o GitHub como se indica en la [sección de introducción](unreal-development-overview.md#1-getting-started).

#### <a name="installing-the-mrtk-hub"></a>Instalación de MRTK Hub

Descargue el complemento desde [Unreal Engine Marketplace](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-toolkit-hub), abra el proyecto y, a continuación, habilite el complemento desde la sección _Mixed Reality_ del menú _Complementos_. Cuando se le pida, reinicie el editor.

![Habilitación del complemento MRTK Hub](images/hub-enable-plugin.png)

Una vez que el complemento está habilitado para el proyecto, puede acceder a MRTK Hub desde el botón de la barra de herramientas.

![Apertura de la ventana de MRTK Hub](images/hub-toolbar.png)

#### <a name="installing-mixed-reality-plugins"></a>Instalación de complementos de realidad mixta

Para instalar un complemento mediante Hub, seleccione el complemento que desea agregar al proyecto y, a continuación, presione el botón _Instalar_. Para descargar el complemento, compruebe que no haya ningún conflicto en el cuadro _Problemas_ y presione _Confirmar_. Una vez descargado el complemento, se le pedirá que reinicie el editor. Desafortunadamente, no podemos reiniciar automáticamente el editor; a veces, la nueva instancia del editor se inicia antes de que se complete la instalación.

![Instalación de un complemento mediante MRTK Hub](images/hub-download.png)

Después de cerrar el editor, verá que aparece un símbolo del sistema con una barra de progreso para desempaquetar el complemento descargado. Aparecerá un símbolo del sistema para cada complemento que se va a instalar. Una vez que finalice el desempaquetado, puede volver a abrir el editor y continuar con el [recorrido de desarrollo de realidad mixta](unreal-quickstart.md).

![Desempaquetado de un complemento mediante el símbolo del sistema de MRTK Hub](images/hub-unpack.png)

> [!IMPORTANT]
> Una vez instalado el complemento, se debe comprobar en el control de código fuente como cualquier otro complemento en el nivel de proyecto.

#### <a name="updating-mixed-reality-plugins"></a>Actualización de complementos de realidad mixta

Para actualizar un complemento mediante Hub, seleccione el complemento que desea actualizar de la lista y presione el botón _Instalar_. Para descargar el complemento actualizado, compruebe que no haya ningún conflicto en el cuadro _Problemas_ y presione _Confirmar_. Se le pedirá que reinicie el editor para completar la actualización. Las actualizaciones del complemento se realizan durante el inicio del editor, por lo que no es necesario esperar a que se complete el desempaquetado antes de volver a abrir el editor.

![Actualización de un complemento mediante MRTK Hub](images/hub-update.png)

#### <a name="removing-mixed-reality-plugins"></a>Eliminación de complementos de realidad mixta

Para desinstalar un complemento mediante MRTK Hub, seleccione el complemento que desea quitar y, a continuación, seleccione la versión que ha instalado en la lista desplegable. Para eliminar el complemento, compruebe que no haya ningún conflicto en el cuadro _Problemas_ y presione _Confirmar_. Se le pedirá que reinicie el editor para completar la eliminación.

![Eliminación de un complemento mediante MRTK Hub](images/hub-remove.png)

#### <a name="reviewing-changes-and-detecting-incompatibilities"></a>Revisión de cambios y detección de incompatibilidades

Puede ver los cambios exactos que se realizarán en el proyecto en la sección inferior de la ventana de MRTK Hub. Desde aquí puede ver los complementos que se agregarán o eliminarán del proyecto junto con las posibles incompatibilidades que podrían causar problemas cuando se hayan realizado los cambios.

> [!NOTE]
> La lista _Problemas_ mostrará incompatibilidades en la versión de Unreal Engine y las versiones de dependencia del complemento, pero no las corregirá automáticamente ni sugerirá correcciones a los problemas.

![Intento de instalación de un complemento incompatible](images/hub-issues.png)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Imagen del logotipo de Unreal](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit - Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Si no desea usar MRTK para Unreal, tendrá que crear scripts para todas las interacciones y comportamientos.