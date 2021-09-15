---
title: Generación de perfiles con Unreal Insights
description: Aprenda a usar Unreal Ideas en HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, development, profling, unreal insights, documentation, guides, features, holograms, game development, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: a77d7795cd7e8c281ebaa2ef89bb6bc9152f5f9c
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779393"
---
# <a name="profiling-with-unreal-insights"></a>Generación de perfiles con Unreal Insights

[Unreal Ideas](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) es un sistema de generación de perfiles que recopila, analiza y visualiza datos de Unreal Engine. El sistema de generación de perfiles puede ayudarle a encontrar cuellos de botella de optimización y áreas en las que el rendimiento de las aplicaciones podría usar un aumento. Normalmente, se habilita Unreal Ideas directamente desde el editor, pero para HoloLens 2 deberá usar la línea de comandos.

## <a name="setup"></a>Configurar

Unreal permite crear y configurar un "perfil personalizado" en el iniciador de HoloLens con los parámetros de línea de comandos que habilitan Unreal Ideas.

1. Busque la dirección IP del equipo mediante el **comando ipconfig** en el símbolo del sistema. La dirección IP es la dirección IPv4 enumerada por ipconfig. Tenga esto en cuenta para más adelante cuando establezca Parámetros de línea de comandos.

> [!IMPORTANT]
> Si está detrás de una VPN, es posible que tenga que proporcionar la dirección IP proporcionada a través de la VPN en su lugar.

![Captura de pantalla de los resultados de la línea de comandos para el comando ipconfig](images/unreal-insights-img-01.png)

2. Abra **Project Configuración** la barra de herramientas "Editar" en la ventana principal del editor.

![Captura de pantalla de la lista desplegable Editar Project Configuración resaltado](images/unreal-insights-img-15.png)

3. Desplácese hacia abajo en el panel izquierdo hasta que encuentre el **encabezado Plataformas** y **seleccione HoloLens**.

![Captura de pantalla de la sección Plataformas Project Configuración panel izquierdo con HoloLens resaltado](images/unreal-insights-img-15.png)

4. Confirme que la **sección Funcionalidades** tiene seleccionados "Internet Client", "Internet Client Server" y "Private Network Client Server".

![Captura de pantalla de las opciones de funcionalidades con el cliente de Internet, el servidor cliente de Internet y el servidor cliente de red privada seleccionados](images/unreal-insights-img-14.png)

## <a name="launch"></a>Launch

1. Abra **Project Selector** desde el panel UE4 bajo el **botón** Iniciar:

![Captura de pantalla de las opciones de inicio con el iniciador de proyectos resaltado](images/unreal-insights-img-07.png)

2. Seleccione el **+** botón para crear un perfil personalizado en **Perfiles de inicio personalizados.** Una vez creado, siempre puede editar este perfil más adelante:

![Captura de pantalla del iniciador de proyectos con perfiles de inicio personalizados resaltados](images/unreal-insights-img-08.png)

3. Seleccione **el botón Editar** perfil en el HoloLens de inicio personalizado. En la **sección Build (Compilación),** active Build **UAT (Compilar UAT)** y establezca Additional Command Line Parameters **(Parámetros de línea de comandos adicionales).**
   - Pruébalo para empezar: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**
   - Puede encontrar una lista completa de los parámetros de inicio disponibles en la documentación [de referencia Ideas unreal.](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)

> [!NOTE]
> "IP_OF_YOUR_PC" es la dirección IP que se encontró en el paso 1. Esta es la dirección IP del equipo que ejecuta Unreal Ideas, NO la dirección IP del HoloLens.

> [!IMPORTANT]
> Los seguimientos pueden ser grandes muy rápidamente. Habilite solo los canales que necesita para mantener un tamaño de seguimiento bajo.

![Captura de pantalla de las opciones de compilación en la configuración del perfil](images/unreal-insights-img-17.png)

4. Seleccione **Cook** to **By the Book (Coráctese en según el** libro) para habilitar la copia en el dispositivo. Asegúrese de que los mapas están seleccionados **en Cooked Mapas**.

![Captura de pantalla de las opciones de cook en la configuración del perfil con cook del libro y HoloLens resaltado](images/unreal-insights-img-09.png)

5. Establezca **¿Cómo desea empaquetar la compilación** en Package **& store locally .** Anote la ruta de acceso del archivo que elija, ya que la necesitará más adelante.

![Captura de pantalla de las opciones del paquete en configuración de perfil establecida en empaquetar y almacenar localmente](images/unreal-insights-img-18.png)

6. Establezca **¿Cómo desea implementar la compilación?** **en No implementar**.

![Captura de pantalla de las opciones de implementación en la configuración del perfil con la implementación establecida para no implementar](images/unreal-insights-img-19.png)

8. Seleccione **Volver** para volver a la raíz del cuadro de **Project Selector** diálogo
9. De nuevo en el editor, haga clic **en Iniciar** en el perfil de inicio personalizado.

![Captura de pantalla de perfiles de inicio personalizados](images/unreal-insights-img-13.png)

10. Observe cómo se ha creado el proyecto y, a continuación, implemente appxbundle (en la ruta de acceso del paquete del paso 5) en el HoloLens a través del portal del dispositivo.

11. Inicie Unreal Ideas. El ejecutable Ideas unreal se almacena en la carpeta del motor de archivos binarios, normalmente de la siguiente manera: "C:\Archivos de programa\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Captura de pantalla del ejecutable de Unreal Insights en ejecución](images/unreal-insights-img-12.png)

12. Inicie la aplicación en el HoloLens.

## <a name="profiling"></a>Generación de perfiles

De nuevo en Unreal Ideas, seleccione **la conexión** activa al dispositivo para iniciar la generación de perfiles.

El perfil personalizado se comparte entre proyectos. De aquí en adelante, puede usar el perfil personalizado que creó en lugar de tener que hacerlo cada vez. Solo tiene que volver a crear la conexión al dispositivo cada vez que inicie Unreal con los pasos 3 a 6 de la [sección de configuración](#setup).

## <a name="see-also"></a>Consulte también

- [Documentación de Unreal Ideas](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
