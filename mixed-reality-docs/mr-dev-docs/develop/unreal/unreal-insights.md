---
title: Generación de perfiles con Unreal Insights
description: Aprenda a usar Unreal Ideas en HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, development, profling, unreal insights, documentation, guides, features, holograms, game development, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: a13655f394b4d2531ab2ae99ee21ebe9185ebe227ef07a16e3ca54eae9375ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228640"
---
# <a name="profiling-with-unreal-insights"></a>Generación de perfiles con Unreal Insights 

[Unreal Ideas](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) es un sistema de generación de perfiles que recopila, analiza y visualiza datos de Unreal Engine. El sistema de generación de perfiles puede ayudarle a encontrar cuellos de botella de optimización y áreas en las que el rendimiento de las aplicaciones podría usar un aumento. Normalmente, se habilita Unreal Ideas directamente desde el editor, pero para HoloLens 2 deberá usar la línea de comandos.  

## <a name="setup"></a>Configurar

Unreal permite crear y configurar un "perfil personalizado" en el iniciador de HoloLens con los parámetros de línea de comandos que habilitan Unreal Ideas.

1.  Busque la dirección IP del equipo mediante el **comando ipconfig** en el símbolo del sistema. La dirección IP es la dirección IPv4 enumerada por ipconfig. Tenga esto en cuenta para más adelante cuando establezca Parámetros de línea de comandos.

> [!IMPORTANT]
> Si está detrás de una VPN, es posible que tenga que proporcionar la dirección IP proporcionada a través de la VPN en su lugar.

![Captura de pantalla de los resultados de la línea de comandos para el comando ipconfig](images/unreal-insights-img-01.png)

2.  Vaya a la parte superior del panel Unreal Engine y abra **Administrador de dispositivos** en el **botón** Iniciar:

![Captura de pantalla de las opciones de inicio con el administrador de dispositivos resaltado](images/unreal-insights-img-02.png)

3.  En la Administrador de dispositivos, seleccione **Agregar un dispositivo no publicado:**

![Captura de pantalla del administrador de dispositivos abierto en un motor de Unreal](images/unreal-insights-img-03.png)

4. Haga **clic en Seleccionar una plataforma** y elija **HoloLens**:

![Captura de pantalla de la lista desplegable Agregar dispositivo no publicado HoloLens resaltado](images/unreal-insights-img-04.png)

5.  Si usa IPoverUSB, escriba 127.0.0.1:10080 como identificador de dispositivo. Escriba el HoloLens usuario y la contraseña en sus respectivos campos y rellene **El nombre para mostrar** como desee.

> [!IMPORTANT]
> El identificador de dispositivo es la dirección IP del HoloLens, NO del equipo que ejecuta Unreal Ideas encontró en el paso 1.

![Captura de pantalla HoloLens detalles del dispositivo en el administrador de dispositivos](images/unreal-insights-img-05.png)

6.  Seleccione **Agregar** y el HoloLens debe aparecer en la lista de dispositivos del administrador de dispositivos:

![Captura de pantalla HoloLens agregado a la lista de dispositivos](images/unreal-insights-img-06.png)

## <a name="launch"></a>Launch

1. Abra **Project Selector** desde el panel UE4 bajo el **botón** Iniciar:

![Captura de pantalla de las opciones de inicio con el iniciador de proyectos resaltado](images/unreal-insights-img-07.png)

2. Seleccione el **+** botón para crear un perfil personalizado en **Perfiles de inicio personalizados.** Una vez creado, siempre puede editar este perfil más adelante:

![Captura de pantalla del iniciador de proyectos con perfiles de inicio personalizados resaltados](images/unreal-insights-img-08.png)

3. Seleccione **el botón Editar** perfil en el HoloLens de inicio personalizado y configure:
    * Seleccione **Cook** to By the Book (Preparar **en por el libro)** para habilitar la copia en el dispositivo.
    * Puede que quiera comprobar **¿Desea archivar?** en la sección Archivo para conservar el archivo .appxbundle generado en lugar de eliminar para ahorrar espacio en disco.  Especifique una ubicación para .appxbundle y cambie a una compilación de desarrollo si lo desea.

![Captura de pantalla de las opciones de cook en la configuración del perfil con cook por el libro y HoloLens resaltado](images/unreal-insights-img-09.png)

4. Establezca **¿Cómo desea implementar la compilación?** en Copiar en **el dispositivo para** activar la sección **Inicio** de la interfaz de usuario:

![Captura de pantalla del iniciador del proyecto con las opciones de implementación con la copia en el dispositivo resaltada](images/unreal-insights-img-10.png)

5. Establezca **Parámetros de línea de comandos adicionales** en la **sección** Inicio. Los parámetros se escribirán en un archivo ue4commandline.txt, se empaquetarán en la agrupación y se usarán en el inicio. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Pruébalo para empezar: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**
    * Puede encontrar una lista completa de los parámetros de inicio disponibles en la documentación [de referencia de Unreal Ideas .](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)

> [!NOTE]
> "IP_OF_YOUR_PC" es la dirección IP que se encontró en el paso 1. Esta es la dirección IP del equipo que ejecuta Unreal Ideas, NO la dirección IP del HoloLens.

> [!IMPORTANT]
> Los seguimientos pueden ser grandes muy rápidamente. Habilite solo los canales que necesita para mantener un tamaño de seguimiento bajo.

![Captura de pantalla de las opciones de configuración de inicio](images/unreal-insights-img-11.png)

6. Inicie Unreal Ideas ANTES de iniciar la aplicación; de lo contrario, Unreal Ideas no podrá inicializarse correctamente antes de la aplicación:
    * El ejecutable Ideas unreal se almacena en la carpeta del motor de archivos binarios, normalmente de la siguiente manera: "C:\Archivos de programa\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Captura de pantalla del ejecutable de Unreal Insights en ejecución](images/unreal-insights-img-12.png)

6.  Seleccione **Volver** para volver a la raíz del cuadro de **Project Selector** diálogo
7.  De nuevo en el editor, haga clic **en Iniciar** en el perfil de inicio personalizado.

![Captura de pantalla de perfiles de inicio personalizados](images/unreal-insights-img-13.png)

8.  Vea cómo el proyecto se empaqueta, se instala en el dispositivo y se inicia

## <a name="profiling"></a>Generación de perfiles

De nuevo en Unreal Ideas, seleccione **la conexión** activa al dispositivo para iniciar la generación de perfiles.

El perfil personalizado se comparte entre proyectos. De aquí en adelante, puede usar el perfil personalizado que creó en lugar de tener que hacerlo cada vez. Solo tiene que volver a crear la conexión al dispositivo cada vez que inicie Unreal con los pasos 3 a 6 de la [sección de configuración](#setup).

## <a name="see-also"></a>Consulte también
* [Documentación de Unreal Ideas](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

