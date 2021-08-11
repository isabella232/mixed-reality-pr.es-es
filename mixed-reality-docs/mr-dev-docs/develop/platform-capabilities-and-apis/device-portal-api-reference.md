---
title: Referencia de la API del Portal de dispositivos
description: Manténgase al día en la API Windows Portal de dispositivos para HoloLens desarrollo.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, Windows Portal de dispositivos, API, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 6b41c569917150c303da933a75d354f574fb579ba676dac281e9cde2bfc59818
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207843"
---
# <a name="device-portal-api-reference"></a>Referencia de la API del Portal de dispositivos

Todo el contenido [Windows Portal de dispositivos](using-the-windows-device-portal.md) se basa en las API REST que puede usar para acceder a los datos y controlar el dispositivo mediante programación.

## <a name="app-deloyment"></a>Desatención de aplicaciones

**/api/app/packagemanager/package (DELETE)**

Desinstala una aplicación

Parámetros
* package: nombre de archivo del paquete que se va a desinstalar.

**/api/app/packagemanager/package (POST)**

Instala una aplicación

Parámetros
* package: nombre de archivo del paquete que se va a instalar.

Carga
* cuerpo HTTP conforme a varias partes

**/api/app/packagemanager/packages (GET)**

Recupera la lista de aplicaciones instaladas en el sistema, con detalles

Devolver datos
* Lista de paquetes instalados con detalles

**/api/app/packagemanager/state (GET)**

Obtiene el estado de la instalación de la aplicación en curso.

## <a name="dump-collection"></a>Colección de volcados de memoria

**/api/debug/dump/usermode/crashcontrol (DELETE)**

Deshabilita la recopilación de volcado de memoria para una aplicación de instalación local

Parámetros
* packageFullname: nombre del paquete

**/api/debug/dump/usermode/crashcontrol (GET)**

Obtiene la configuración de la recopilación de volcado de memoria de aplicaciones de instalación local

Parámetros
* packageFullname: nombre del paquete

**/api/debug/dump/usermode/crashcontrol (POST)**

Habilita y establece la configuración del control de volcado de memoria para una aplicación de instalación local

Parámetros
* packageFullname: nombre del paquete

**/api/debug/dump/usermode/crashdump (DELETE)**

Elimina un volcado de memoria para una aplicación de instalación local

Parámetros
* packageFullname: nombre del paquete
* fileName: nombre de archivo de volcado

**/api/debug/dump/usermode/crashdump (GET)**

Recupera un volcado de memoria para una aplicación de instalación local

Parámetros
* packageFullname: nombre del paquete
* fileName: nombre de archivo de volcado

Devolver datos
* Archivo de volcado. Inspeccione con WinDbg o Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

Devuelve una lista de todos los volcados de memoria para las aplicaciones de instalación local

Devolver datos
* Lista de volcados de memoria por aplicación cargada lateralmente

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

Enumera los proveedores registrados

Devolver datos
* Lista de proveedores, nombre descriptivo y GUID

**/api/etw/session/realtime (GET/WebSocket)**

Crea una sesión ETW en tiempo real; administrado a través de un websocket.

Devolver datos
* Eventos ETW de los proveedores habilitados

## <a name="holographic-os"></a>SO Holographic

**/api/holographic/os/etw/customproviders (GET)**

Devuelve una lista de HoloLens proveedores etw específicos que no están registrados en el sistema

**/api/holographic/os/services (GET)**

Devuelve los estados de todos los servicios en ejecución.

**/api/holographic/os/settings/ipd (GET)**

Obtiene el IPD almacenado (distancia interpupillaria) en milímetros

**/api/holographic/os/settings/ipd (POST)**

Establece el IPD

Parámetros
* ipd: nuevo valor ipD que se establecerá en milímetros

**/api/holographic/os/webmanagement/settings/https (GET)**

Obtener los requisitos de HTTPS para Device Portal

**/api/holographic/os/webmanagement/settings/https (POST)**

Establece los requisitos HTTPS para el Portal de dispositivos

Parámetros
* requerido: sí, no o predeterminado

## <a name="holographic-perception"></a>Percepción holográfica

**/api/holographic/perception/client (GET/WebSocket)**

Acepta actualizaciones de websocket y ejecuta un cliente de percepción que envía actualizaciones a 30 fps.

Parámetros
* clientmode: "active" fuerza el modo de seguimiento visual cuando no se puede establecer pasivamente

## <a name="holographic-thermal"></a>Holográficamente térmico

**/api/holographic/thermal/stage (GET)**

Obtener la fase térmico del dispositivo (0 normal, 1 caliente, 2 crítico)

## <a name="map-manager"></a>Map Manager (Administrador de mapas)

**/api/holographic/mapmanager/mapFiles (GET)**

Obtiene la lista de los archivos de mapa disponibles (.mapx).

**/api/holographic/mapmanager/anchorFiles (GET)**

Obtiene la lista de archivos delimitadores disponibles (.ancx).

**/api/holographic/mapmanager/srdbFiles (GET)**

Obtiene la lista de archivos de base de datos de reconstrucción espacial disponibles (.srdb).

**/api/holographic/mapmanager/getanchors (GET)**

Obtiene la lista de delimitadores persistentes para el usuario actual. 

### <a name="downloaduploaddelete-files"></a>Descargar/Upload/Eliminar archivos
**/api/holographic/mapmanager/download (GET)**

Descarga un archivo de base de datos de mapa, delimitador o reconstrucción espacial. El archivo se debe haber cargado o exportado previamente.

Parámetros
* FileName: nombre del archivo que se descargará.

Ejemplo: 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

**/api/holographic/mapmanager/upload (POST)**

Carga un archivo de base de datos de mapa, delimitador o reconstrucción espacial. Una vez cargado un archivo, se puede importar posteriormente para que lo utilice el sistema.

Parámetros
* file: nombre del archivo que se cargará.

Ejemplo:
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

**/api/holographic/mapmanager/delete (POST)**

Elimina un archivo de base de datos de mapa, delimitador o reconstrucción espacial. El archivo se debe haber cargado o exportado previamente.

Parámetros
* FileName: nombre del archivo que se eliminará.

Ejemplo: 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a>Exportación

**/api/holographic/mapmanager/export (POST)**

Exporta el mapa actualmente en uso por el sistema. Una vez exportado, se puede descargar. 

Ejemplo: 
```
$.post("/api/holographic/mapmanager/export")
```

**/api/holographic/mapmanager/exportanchors (POST)**

Exporta el mapa actualmente en uso por el sistema. Una vez exportado, se puede descargar. Ejemplo: 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

**/api/holographic/mapmanager/exportmapgrafíanchors (POST)**

Exporta el mapa y los delimitadores actualmente en uso por el sistema. Una vez que se exportan, se pueden descargar. Ejemplo: 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**

Exporta el mapa y la base de datos de reconstrucción espacial actualmente en uso por el sistema. Una vez que se exportan, se pueden descargar. 

Ejemplo: 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a>Importar

**/api/holographic/mapmanager/import (POST)**

Indica al sistema qué asignación se debe usar actualmente. Se puede llamar a en archivos que se han exportado o cargado.

Parámetros
* FileName: nombre de la asignación que se va a usar. 

Ejemplo: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importanchors (POST)**

Indica al sistema qué delimitadores se deben usar actualmente. Se puede llamar a en archivos que se han exportado o cargado.

Parámetros
* FileName: nombre de los delimitadores que se usarán. 

Ejemplo: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importspatialmappingdb (POST)**

Indica al sistema qué base de datos espacial de reconstrucción debe usarse actualmente. Se puede llamar a en archivos que se han exportado o cargado.

Parámetros
* FileName: nombre de la base de datos de asignación espacial que se va a usar. 

Ejemplo: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a>Otros

**/api/holographic/mapmanager/resetmapgrafíanchorsandsrdb (POST)**

Restablezca el sistema de la base de datos de mapa, delimitadores y reconstrucción espacial.

Ejemplo: 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

**/api/holographic/mapmanager/status (GET)**

Obtiene el estado del sistema, incluidos los archivos de base de datos de mapa, delimitadores y reconstrucción espacial que se importaron por última vez. 


## <a name="mixed-reality-capture"></a>Captura de realidad mixta

**/api/holographic/mrc/file (GET)**

Descarga un archivo de realidad mixta desde el dispositivo. Use el parámetro de consulta op=stream para el streaming.

Parámetros
* filename: nombre, codificado en hexadecimal, del archivo de vídeo que se va a obtener.
* op : stream

**/api/holographic/mrc/file (DELETE)**

Elimina una grabación de realidad mixta del dispositivo.

Parámetros
* filename: nombre, codificado en hexadecimal64, del archivo que se va a eliminar.

**/api/holographic/mrc/files (GET)**

Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo.

**/api/holographic/mrc/photo (POST)**

Toma una foto de realidad mixta y crea un archivo en el dispositivo.

Parámetros
* holo : capture hologramas: true o false (el valor predeterminado es false)
* pv : capture pv camera: true o false (el valor predeterminado es false)
* RenderFromCamera: (solo HoloLens 2) desde la perspectiva de la cámara de fotos o vídeos: true o false (el valor predeterminado es true)

**/api/holographic/mrc/settings (GET)**

Obtiene la configuración de captura de realidad mixta predeterminada.

**/api/holographic/mrc/settings (POST)**

Establece la configuración de captura de realidad mixta predeterminada.  Algunas de estas opciones se aplican a la captura de fotos y vídeos de MRC del sistema.

**/api/holographic/mrc/status (GET)**

Obtiene el estado de la captura de realidad mixta dentro del Windows Portal de dispositivos.

***Respuesta***

La respuesta contiene una propiedad JSON que indica si Windows Portal de dispositivos está grabando vídeo o no.

``` javascript
{"IsRecording" : boolean}
```

**/api/holographic/mrc/thumbnail (GET)**

Obtiene la imagen en miniatura del archivo especificado.

Parámetros
* filename: nombre, codificado en hexadecimal64, del archivo para el que se solicita la miniatura

**/api/holographic/mrc/video/control/start (POST)**

Inicia una grabación de realidad mixta

Parámetros
* holo : capture hologramas: true o false (el valor predeterminado es false)
* pv : capture pv camera: true o false (el valor predeterminado es false)
* mic : capture microphone: true o false (el valor predeterminado es false)
* loopback: capture el audio de la aplicación: true o false (el valor predeterminado es false)
* RenderFromCamera: (solo HoloLens 2) desde la perspectiva de la cámara de fotos o vídeos: true o false (el valor predeterminado es true)
* vstab : (solo HoloLens 2) habilitar la estabilización de vídeo: true o false (el valor predeterminado es true)
* vstabbuffer: (solo HoloLens 2) latencia del búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)

**/api/holographic/mrc/video/control/stop (POST)**

Detiene la grabación de realidad mixta actual

## <a name="mixed-reality-streaming"></a>Mixed Reality Streaming

> [!CAUTION]
> Debido al aislamiento de bucles bucles, no se puede conectar a Mixed Reality Streaming desde dentro de una aplicación en un dispositivo.

HoloLens admite la versión preliminar en vivo de la realidad mixta mediante la descarga fragmentada de un mp4 fragmentado.

Los flujos de realidad mixta comparten el mismo conjunto de parámetros para controlar lo que se captura:
* holo: capturar hologramas: true o false
* pv : capture pv camera: true o false
* mic : capture microphone: true o false
* loopback: capture el audio de la aplicación: true o false

Si no se especifica ninguno de estos valores: se capturarán hologramas, cámara de fotos y vídeo y audio de la aplicación.<br>
Si se especifica alguna: el valor predeterminado de los parámetros no especificados será false.

Parámetros opcionales (HoloLens 2 solo)
* RenderFromCamera: render desde la perspectiva de la cámara de fotos o vídeos: true o false (el valor predeterminado es true)
* vstab: habilitar la estabilización de vídeo: true o false (el valor predeterminado es false)
* vstabbuffer: latencia del búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)

**/api/holographic/stream/live.mp4 (GET)**

Una secuencia de 1280 x 720p 30fps de 5 bits.

**/api/holographic/stream/live_high.mp4 (GET)**

Una secuencia de 1280 x 720p 30fps de 5 bits.

**/api/holographic/stream/live_med.mp4 (GET)**

Una secuencia de 854 x 480p 30fps de 2,5 bits.

**/api/holographic/stream/live_low.mp4 (GET)**

Una secuencia de 428 x 240p 15fps de 0,6 bits.

## <a name="networking"></a>Redes

**/api/networking/ipconfig (GET)**

Obtiene la configuración ip actual.

## <a name="os-information"></a>Información del sistema operativo

**/api/os/info (GET)**

Obtiene información del sistema operativo.

**/api/os/machinename (GET)**

Obtiene el nombre de la máquina.

**/api/os/machinename (POST)**

Establece el nombre de la máquina

Parámetros
* name: nuevo nombre de la máquina, codificado en hexadecimal64, para establecer en

## <a name="perception-simulation-control"></a>Control de simulación de percepción

**/api/holographic/simulation/control/mode (GET)**

Obtener el modo de simulación

**/api/holographic/simulation/control/mode (POST)**

Establecer el modo de simulación

Parámetros
* mode : modo de simulación: predeterminado, simulación, remoto, heredado

**/api/holographic/simulation/control/stream (DELETE)**

Elimina una secuencia de control.

**/api/holographic/simulation/control/stream (GET/WebSocket)**

Abra una conexión de socket web para una secuencia de control.

**/api/holographic/simulation/control/stream (POST)**

Cree una secuencia de control (se requiere prioridad) o publique datos en una secuencia creada (se requiere streamId). Se espera que los datos publicados sean del tipo "application/octet-stream".

**/api/holographic/simulation/display/stream (GET/WebSocket)**

Solicite una secuencia de vídeo de simulación que contenga el contenido representado en la pantalla del sistema en modo "Simulación".  Inicialmente se enviará un encabezado de descriptor de formato simple, seguido de texturas codificadas con H.264, cada una precedida de un encabezado que indica el índice de los ojos y el tamaño de la textura.

## <a name="perception-simulation-playback"></a>Reproducción de simulación de percepción

**/api/holographic/simulation/playback/file (DELETE)**

Eliminar una grabación.

Parámetros
* recording: nombre de la grabación que se eliminará.

**/api/holographic/simulation/playback/file (POST)**

Upload una grabación.

**/api/holographic/simulation/playback/files (GET)**

Obtenga todas las grabaciones.

**/api/holographic/simulation/playback/session (GET)**

Obtiene el estado de reproducción actual de una grabación.

Parámetros
* recording: nombre de la grabación.

**/api/holographic/simulation/playback/session/file (DELETE)**

Descargar una grabación.

Parámetros
* recording: nombre de la grabación que se descargará.

**/api/holographic/simulation/playback/session/file (POST)**

Cargue una grabación.

Parámetros
* recording: nombre de la grabación que se cargará.

**/api/holographic/simulation/playback/session/files (GET)**

Obtenga todas las grabaciones cargadas.

**/api/holographic/simulation/playback/session/pause (POST)**

Pausar una grabación.

Parámetros
* recording: nombre de la grabación.

**/api/holographic/simulation/playback/session/play (POST)**

Reproducir una grabación.

Parámetros
* recording: nombre de la grabación.

**/api/holographic/simulation/playback/session/stop (POST)**

Detenga una grabación.

Parámetros
* recording: nombre de la grabación.

**/api/holographic/simulation/playback/session/types (GET)**

Obtiene los tipos de datos de una grabación cargada.

Parámetros
* recording: nombre de la grabación.

## <a name="perception-simulation-recording"></a>Grabación de simulación de percepción

**/api/holographic/simulation/recording/start (POST)**

Inicie una grabación. Solo una sola grabación puede estar activa a la vez. Se debe establecer una de la cabeza, las manos, spatialMapping o el entorno.

Parámetros
* head: se establece en 1 para registrar los datos de la cabeza.
* hands : se establece en 1 para registrar los datos de la mano.
* spatialMapping: se establece en 1 para registrar la asignación espacial.
* environment : se establece en 1 para registrar los datos del entorno.
* name: nombre de la grabación.
* singleSpatialMappingFrame: se establece en 1 para registrar solo un fotograma de asignación espacial.

**/api/holographic/simulation/recording/status (GET)**

Obtiene el estado de grabación.

**/api/holographic/simulation/recording/stop (GET)**

Detenga la grabación actual. La grabación se devolverá como un archivo.

## <a name="performance-data"></a>Datos de rendimiento

**/api/resourcemanager/processes (GET)**

Devuelve la lista de procesos en ejecución con detalles

Devolver datos
* JSON con lista de procesos y detalles para cada proceso

**/api/resourcemanager/systemperf (GET)**

Devuelve estadísticas de rendimiento del sistema (lectura/escritura de E/S, estadísticas de memoria, etc.

Devolver datos
* JSON con información del sistema: CPU, GPU, memoria, red, E/S

## <a name="power"></a>Potencia

**/api/power/battery (GET)**

Obtiene el estado actual de la batería.

**/api/power/state (GET)**

Comprueba si el sistema está en un estado de bajo consumo.

## <a name="remote-control"></a>Control remoto

**/api/control/restart (POST)**

Reinicia el dispositivo de destino

**/api/control/shutdown (POST)**

Apaga el dispositivo de destino.

## <a name="task-manager"></a>Administrador de tareas

**/api/taskmanager/app (DELETE)**

Detiene una aplicación moderna

Parámetros
* package: nombre completo del paquete de aplicación, codificado en hexadecimal64
* forcestop: forzar que todos los procesos se detengan (=sí)

**/api/taskmanager/app (POST)**

Inicia una aplicación moderna

Parámetros
* appid: PRAID de la aplicación que se va a iniciar, codificado en hexadecimal64
* package: nombre completo del paquete de aplicación, codificado en hexadecimal64

## <a name="wifi-management"></a>Administración de Wi-Fi

**/api/wifi/interfaces (GET)**

Enumera las interfaces de red inalámbrica

Devolver datos
* Lista de interfaces inalámbricas con detalles (GUID, descripción, etc.)

**/api/wifi/network (DELETE)**

Elimina un perfil asociado a una red en una interfaz especificada.

Parámetros
* interface : GUID de interfaz de red
* profile: nombre del perfil

**/api/wifi/networks (GET)**

Enumera las redes inalámbricas en la interfaz de red especificada

Parámetros
* interface : GUID de interfaz de red

Devolver datos
* Lista de redes inalámbricas que se encuentran en la interfaz de red con detalles

**/api/wifi/network (POST)**

Se conecta o se desconecta a una red en la interfaz especificada.

Parámetros
* interface : GUID de interfaz de red
* ssid: ssid, codificado en hexadecimal64, al que conectarse
* op: conexión o desconexión
* createprofile: sí o no
* key: clave compartida, codificada en hexadecimal64

## <a name="windows-performance-recorder"></a>Windows Grabadora de rendimiento

**/api/wpr/customtrace (POST)**

Carga un perfil de WPR y comienza el seguimiento con el perfil cargado.

Carga
* cuerpo HTTP conforme a varias partes

Devolver datos
* Devuelve el estado de sesión WPR.

**/api/wpr/status (GET)**

Recupera el estado de la sesión de WPR.

Devolver datos
* Estado de la sesión de WPR.

**/api/wpr/trace (GET)**

Detiene una sesión de seguimiento de WPR (rendimiento)

Devolver datos
* Devuelve el archivo ETL de seguimiento.

**/api/wpr/trace (POST)**

Inicia sesiones de seguimiento de WPR (rendimiento)

Parámetros
* profile: nombre del perfil. Los perfiles disponibles se almacenan en perfprofiles/profiles.json

Devolver datos
* Al iniciar, devuelve el estado de la sesión de WPR.

## <a name="see-also"></a>Consulte también
* [Uso del Portal de dispositivos Windows](using-the-windows-device-portal.md)
* [Portal de dispositivos de API principal (UWP)](/windows/uwp/debug-test-perf/device-portal-api-core)