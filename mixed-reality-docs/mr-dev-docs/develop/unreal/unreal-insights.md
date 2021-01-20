---
title: Generación de perfiles con Unreal Insights
description: Obtenga información sobre cómo usar información no real en HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, desarrollo, Prof., información inreal, documentación, guías, características, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580832"
---
# <a name="profiling-with-unreal-insights"></a>Generación de perfiles con Unreal Insights 

La [información inreal](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) es un sistema de generación de perfiles que recopila, analiza y visualiza datos de un motor inreal. El sistema de generación de perfiles puede ayudarle a encontrar cuellos de botella y áreas de optimización donde el rendimiento de las aplicaciones podría usar un aumento. Normalmente, se habilita la información no real directamente desde el editor, pero para HoloLens 2 deberá usar la línea de comandos.  

## <a name="setup"></a>Configurar

No real le permite crear y configurar un "perfil personalizado" en el iniciador de HoloLens con los parámetros de la línea de comandos que permiten obtener información inreal.

1.  Busque la dirección IP del equipo mediante el comando **ipconfig** en el símbolo del sistema. La dirección IP es la dirección IPv4 que se muestra en ipconfig. Tenga esto en cuenta para más adelante al establecer los parámetros de la línea de comandos.

> [!IMPORTANT]
> Si está detrás de una VPN, puede que necesite proporcionar la dirección IP proporcionada a través de la VPN en su lugar.

![Captura de pantalla de los resultados de la línea de comandos para el comando ipconfig](images/unreal-insights-img-01.png)

2.  Vaya a la parte superior del panel de inreal Engine y Abra **Device Manager** en el botón **Launch (iniciar** ):

![Captura de pantalla de las opciones de inicio con el administrador de dispositivos resaltado](images/unreal-insights-img-02.png)

3.  En el Device Manager, seleccione **Agregar un dispositivo** que no está en la lista:

![Captura de pantalla del administrador de dispositivos abierto en el motor inreal](images/unreal-insights-img-03.png)

4. Haga clic en **seleccionar una plataforma** y elija **HoloLens**:

![Captura de pantalla de la lista desplegable Agregar dispositivo no enumerado con HoloLens resaltado](images/unreal-insights-img-04.png)

5.  Si utiliza IPoverUSB, escriba 127.0.0.1:10080 como identificador de dispositivo. Escriba el usuario y la contraseña de HoloLens en sus respectivos campos y rellene **el nombre para mostrar** como desee.

> [!IMPORTANT]
> El identificador de dispositivo es la dirección IP de HoloLens, no el equipo que ejecuta información inreal que encontró en el paso 1.

![Captura de pantalla de los detalles del dispositivo HoloLens en el administrador de dispositivos](images/unreal-insights-img-05.png)

6.  Seleccione **Agregar** y la HoloLens debe aparecer en la lista de dispositivos del administrador de dispositivos:

![Captura de pantalla de HoloLens agregada a la lista de dispositivos](images/unreal-insights-img-06.png)

## <a name="launch"></a>Launch

1. Abra el **iniciador del proyecto** desde el panel de UE4 en el botón **Launch (iniciar** ):

![Captura de pantalla de opciones de inicio con el iniciador de proyecto resaltado](images/unreal-insights-img-07.png)

2. Seleccione el **+** botón para crear un perfil personalizado en **perfiles de inicio personalizados**. Una vez creada, siempre puede editar este perfil más adelante:

![Captura de pantalla del iniciador del proyecto con perfiles de inicio personalizados resaltados](images/unreal-insights-img-08.png)

3. Seleccione el botón **Editar perfil** en el perfil de inicio personalizado de HoloLens y configure:
    * Seleccione **Cook** en **el libro** para habilitar la copia en el dispositivo
    * Es posible que desee comprobar **¿desea archivar?** en la sección **archivar** para conservar el archivo. appxbundle generado en lugar de eliminarlo y ahorrar espacio en disco. Especifique una ubicación para el. appxbundle y cambie a una compilación de desarrollo si lo desea

![Captura de pantalla de las opciones de Cook en configuración de perfil con Cook en el libro y HoloLens resaltados](images/unreal-insights-img-09.png)

4. Establezca **Cómo desea implementar la compilación** para **Copiar en el dispositivo** y activar la sección Launch ( **iniciar** ) de la interfaz de usuario:

![Captura de pantalla del iniciador del proyecto con opciones de implementación con la opción copiar en el dispositivo resaltada](images/unreal-insights-img-10.png)

5. Establezca **parámetros adicionales** de la línea de comandos en la sección **Launch (iniciar** ). Los parámetros se escribirán en un archivo ue4commandline.txt, empaquetado en la agrupación y se usarán en el inicio. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Pruébelos para los iniciadores: **-tracehost = IP_OF_YOUR_PC-Trace = registro, marcador, fotograma, CPU, GPU, LoadTime, archivo, red**
    * Puede encontrar una lista completa de los parámetros de inicio disponibles en la [documentación de referencia de Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> "IP_OF_YOUR_PC" es la dirección IP que encontramos en el paso 1. Esta es la dirección IP del equipo que ejecuta información inreal, no la dirección IP de HoloLens.

> [!IMPORTANT]
> Los seguimientos pueden llegar a ser grandes muy rápidamente. Habilite solo los canales que necesita para mantener un tamaño de seguimiento bajo.

![Captura de pantalla de las opciones de configuración de inicio](images/unreal-insights-img-11.png)

6. Inicie información no real antes del inicio de la aplicación, de lo contrario, la información no real no podrá inicializarse correctamente antes de la aplicación:
    * El ejecutable de Insights no real se almacena en la carpeta del motor de archivos binarios, normalmente de la siguiente manera: "C:\Archivos de Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Captura de pantalla del ejecutable inreal de Insights en ejecución](images/unreal-insights-img-12.png)

6.  Seleccione **atrás** para volver a la raíz del cuadro de diálogo del **iniciador del proyecto** .
7.  De nuevo en el editor, haga clic en **iniciar** en el perfil de inicio personalizado.

![Captura de pantalla de perfiles de inicio personalizados](images/unreal-insights-img-13.png)

8.  Observe que el proyecto está empaquetado, instalado en el dispositivo e iniciado

## <a name="profiling"></a>Generación de perfiles

De nuevo en información no real, seleccione la conexión **dinámica** al dispositivo para iniciar la generación de perfiles.

El perfil personalizado se comparte entre proyectos. Desde aquí, puede usar el perfil personalizado que creó en lugar de tener que hacerlo cada vez. Solo tiene que volver a crear la conexión con el dispositivo cada vez que se inicia de un momento dado con los pasos 3 a 6 de la [sección de configuración](#setup).

## <a name="see-also"></a>Consulte también
* [Documentación de Insights no real](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

