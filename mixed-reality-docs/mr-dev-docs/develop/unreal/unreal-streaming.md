---
title: Streaming en Unreal
description: Obtenga información sobre cómo transmitir aplicaciones de Unreal a HoloLens 2, incluidas las limitaciones de streaming y las opciones de línea de comandos.
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, streaming, PC, holographic app remoting, holographic remoting player, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: a0c376ed6366e57b8a521c52db2fc02fcd1c0285
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009955"
---
# <a name="streaming-in-unreal"></a>Streaming en Unreal

El streaming de un equipo a HoloLens ofrece dos ventajas principales: 
* Permite que la aplicación de realidad mixta aproveche la eficacia de cálculo de los equipos. 
* Ayuda a acelerar el tiempo de iteración de desarrollo. 

Para empezar, deberá descargar [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) en su dispositivo HoloLens. Holographic Remoting Player permitirá que la aplicación transmita directamente al reproductor de control remoto en HoloLens desde los orígenes siguientes:

* Editor Unreal Engine
* Ejecutable de Windows empaquetado 

Durante el streaming, tiene acceso prácticamente a las mismas funcionalidades de HoloLens que cuando se ejecuta una aplicación en un dispositivo. Esto incluye [seguimiento de articulación de la mano](unreal-hand-tracking.md) (si utiliza HoloLens 2), [asignación espacial](unreal-spatial-mapping.md) y [anclajes espaciales](unreal-spatial-anchors.md), pero descarta las características de esta [lista](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md). 

> [!NOTE]
> * La calidad de streaming depende en gran medida de la intensidad de la señal de su red WiFi.
> * Todas las funciones se habilitan automáticamente para la aplicación Holographic Remoting Player. Si encuentra una funcionalidad que requiere permiso del usuario (p. ej., el seguimiento ocular) para funcionar en streaming, pero no cuando se ejecuta en el dispositivo, asegúrese de haber habilitado las funcionalidades adecuadas en la configuración del proyecto.

### <a name="streaming-limitations"></a>Limitaciones de streaming

Las mallas de mano, la cámara de HoloLens y el teclado del sistema no están disponibles a través de streaming. Tenga en cuenta que la entrada de voz para las aplicaciones transmitidas se puede adquirir a través del micrófono del equipo desde el que se hace streaming.

#### <a name="openxr"></a>OpenXR

Unreal 4.26 en ejecución en OpenXR admite el streaming a las versiones 2.4.0 o posteriores del reproductor de control remoto de holografías. El streaming de OpenXR en la versión 2.4.0 no tiene compatibilidad con la asignación espacial y los anclajes espaciales. 

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Origen</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>Primera generación de HoloLens</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Cascos envolventes</strong></td>
    </tr>
     <tr>
        <td>Editor de Unreal</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Paquetes de Windows</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Streaming desde el editor de Unreal

Como desarrollador, descubrirá que el streaming desde el editor de Unreal a su dispositivo HoloLens proporciona ventajas importantes al realizar pruebas; por ejemplo, ya no tiene que esperar a que la aplicación se compile e implemente antes de probar las actualizaciones.

Puede encontrar instrucciones detalladas sobre el [streaming desde el editor de Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) en nuestra serie de tutoriales.

## <a name="streaming-from-a-packaged-windows-executable"></a>Streaming desde un ejecutable de Windows empaquetado

En Unreal 4.25.1, puede transmitir la aplicación a un dispositivo HoloLens 2 desde un ejecutable de Windows empaquetado: 

1. Vaya a **File > Package Project > Windows** (Archivo > Proyecto de paquete > Windows) en el menú del editor. 
    * Elija una ubicación donde guardar el paquete y seleccione **Seleccionar carpeta**.

2. Una vez que el paquete termine de compilarse, abra **Holographic Remoting Player** en HoloLens 2 y tome nota de la dirección IP. 
3. Deje **Holographic Remoting Player** abierto y en el símbolo del sistema: 
    * Invoque cd en el directorio local donde guardó el paquete.
    * Escriba el comando siguiente: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`

> [!NOTE]
> El nombre de la aplicación en la configuración del proyecto debe usarse automáticamente para crear el paquete de Windows. Si por alguna razón son diferentes, utilice el nombre del ejecutable de Windows en el símbolo del sistema.

Presione Entrar y observe que la aplicación inicia el streaming.

### <a name="command-line-options"></a>Opciones de línea de comandos

En la tabla siguiente, se pueden encontrar opciones adicionales de la línea de comandos para hacer streaming desde cada plataforma de Unreal Engine 4.26 o versiones posteriores. 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a>Consulta también

* [Historial de versiones de Control remoto de holografías](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [Establecimiento de una conexión segura con Control remoto de holografías](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
