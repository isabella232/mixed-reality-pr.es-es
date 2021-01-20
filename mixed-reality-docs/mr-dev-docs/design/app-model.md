---
title: Modelo de aplicación
description: Windows Mixed Reality usa el modelo de aplicación proporcionado por el Plataforma universal de Windows, un modelo y un entorno para las aplicaciones modernas de Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, modelo de aplicación, ciclo de vida, suspensión, reanudación, icono, vistas, contratos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 941c0f3f81596e8465157121462b4150cefd8ac2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583213"
---
# <a name="app-model"></a>Modelo de aplicación

Windows Mixed Reality usa el modelo de aplicación proporcionado por el [plataforma universal de Windows](/windows/uwp/get-started/) (UWP), que es un modelo y un entorno para las aplicaciones modernas de Windows. El modelo de aplicación de UWP define el modo en que las aplicaciones se instalan, actualizan, controlan versiones y se quitan por completo. También rige el ciclo de vida de la aplicación: cómo las aplicaciones se ejecutan, suspenden y detienen, y cómo pueden conservar el estado. Por último, el modelo de aplicación cubre la integración y la interacción con el sistema operativo, los archivos y otras aplicaciones.

![aplicaciones 2D organizadas en la Página principal de Windows Mixed Reality en un área de desayuno](images/20160112-055908-hololens-500px.jpg)<br>
*Aplicaciones con una vista 2D organizada en la Página principal de Windows Mixed Reality*

## <a name="app-lifecycle"></a>Ciclo de vida de la aplicación

El ciclo de vida de una aplicación de realidad mixta implica conceptos de aplicaciones estándar, como la selección de ubicación, el inicio, la terminación y la eliminación.

### <a name="placement-is-launch"></a>La selección de ubicación es Launch

Todas las aplicaciones se inician en la realidad mixta colocando un icono de la aplicación (solo un [icono secundario de Windows](/uwp/api/Windows.UI.StartScreen.SecondaryTile)) en la [Página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md). Estos iconos de la aplicación, en la ubicación, comenzarán a ejecutar la aplicación. Estos iconos de la aplicación se conservan y permanecen en su ubicación colocada, actuando como iniciadores en cualquier momento que quiera volver a la aplicación.

![La selección de ubicación coloca un icono secundario en el mundo](images/slide1-600px.png)<br>
*La selección de ubicación coloca un icono secundario en el mundo*

En cuanto se complete la selección de ubicación (a menos que la ubicación la haya iniciado una [aplicación para](app-model.md#protocols) el inicio de la aplicación), la aplicación comenzará a iniciarse. Windows Mixed Reality puede ejecutar un número limitado de aplicaciones al mismo tiempo. En cuanto se coloca e inicia una aplicación, otras aplicaciones activas pueden suspenderse. Las aplicaciones suspendidas dejan una captura de pantalla del último estado de la aplicación en el icono de la aplicación donde se colocó. Para obtener más información sobre el control de reanudación y otros eventos del ciclo de vida, consulte ciclo de vida de la [aplicación Windows 10 UWP](/windows/uwp/launch-resume/app-lifecycle).

![Después de colocar un icono, la aplicación comienza el ](images/slide2-500px.png) ![ Diagrama de estado de ejecución de la aplicación en ejecución, suspendida o no en ejecución.](images/ic576232-500px.png)<br>
*Izquierda: después de colocar un icono, la aplicación comienza a ejecutarse. Right: Diagrama de estado de la aplicación en ejecución, suspendida o no se está ejecutando.*

### <a name="remove-is-closeterminate-process"></a>Quitar es el proceso de cierre y terminación

Cuando se quita un icono de aplicación colocada del mundo, se cierran los procesos subyacentes. Esto puede ser útil para garantizar que la aplicación se detenga o se reinicie una aplicación problemática.

### <a name="app-suspensiontermination"></a>Suspensión/terminación de la aplicación

En la [Página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md), el usuario puede crear varios puntos de entrada para una aplicación iniciando la aplicación desde el menú Inicio y colocando el icono de la aplicación en el mundo. Cada icono de la aplicación se comporta como un punto de entrada diferente y tiene una instancia de mosaico independiente en el sistema. Una consulta para [SecondaryTile. FindAllAsync](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) producirá un **SecondaryTile** para cada instancia de la aplicación.

Cuando se suspende una aplicación para UWP, se toma una captura de pantalla del estado actual.

![Se muestran capturas de pantallas para aplicaciones suspendidas](images/slide9-800px.png)<br>
*Se muestran capturas de pantallas para aplicaciones suspendidas*

Una diferencia clave de otros shells de Windows 10 es cómo se informa a la aplicación de la activación de una instancia de aplicación a través de los eventos [CoreApplication. RESUMING](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) y [CoreWindow. Activated](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) .

|  Escenario |  Reanudando  |  Activado | 
|----------|----------|----------|
|  Iniciar una nueva instancia de la aplicación desde el menú Inicio  |   |  **Activado** con un nuevo [TileId](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Iniciar una segunda instancia de la aplicación desde el menú Inicio  |   |  **Activado** con un nuevo **TileId** | 
|  Seleccione la instancia de la aplicación que no está activa actualmente  |   |  Se **activa** con el **TileId** asociado a la instancia. | 
|  Seleccione otra aplicación y, a continuación, seleccione la instancia activa previamente.  |  **Reanudación** generada  |  | 
|  Seleccione otra aplicación y, a continuación, seleccione la instancia que estaba inactiva previamente.  |  **Reanudación** generada  |  A continuación, se **activa** con el **TileId** asociado a la instancia. | 

### <a name="extended-execution"></a>Ejecución extendida

A veces, la aplicación debe seguir trabajando en segundo plano o reproduciendo audio. [Las tareas en segundo plano](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) están disponibles en HoloLens.

![Las aplicaciones se pueden ejecutar en segundo plano](images/slide10-800px.png)<br>
*Las aplicaciones se pueden ejecutar en segundo plano*

## <a name="app-views"></a>Vistas de aplicación

Cuando se activa la aplicación, puede elegir el tipo de vista que le gustaría mostrar. En el caso de una aplicación de **CoreApplication**, siempre hay una [vista de aplicación](/uwp/api/Windows.UI.ViewManagement.ApplicationView) principal y cualquier número de vistas de aplicación adicionales que quiera crear. En el escritorio, puede pensar en una vista de la aplicación como una ventana. Nuestras plantillas de aplicaciones de realidad mixta crean un proyecto de Unity en el que la vista de la aplicación principal es [envolvente](app-views.md). 

La aplicación puede crear una vista de aplicación 2D adicional mediante tecnología como XAML, para usar características de Windows 10 como la compra desde la aplicación. Si la aplicación se inicia como una aplicación para UWP para otros dispositivos de Windows 10, la vista principal es 2D. Sin embargo, se puede "iluminar" en la realidad mixta agregando otra vista de la aplicación que es envolvente para mostrar una experiencia de forma volumétrica. Imagine que compila una aplicación de visor de fotos en XAML donde el botón de presentación de diapositivas cambió a una vista de aplicación envolvente que voló fotos de la aplicación en todo el mundo y Surfaces.

![La aplicación en ejecución puede tener una vista 2D o una vista envolvente](images/slide3-800px.png)<br>
*La aplicación en ejecución puede tener una vista 2D o una vista envolvente*

### <a name="creating-an-immersive-view"></a>Crear una vista envolvente

Las aplicaciones de realidad mixta crean una vista envolvente, que se consigue con el tipo [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace) .

Una aplicación que es puramente envolvente siempre debe crear una vista envolvente en el inicio, incluso si se inicia desde el escritorio. Las vistas envolventes siempre aparecen en el casco, independientemente de dónde se crearon. Al activar una vista envolvente, se mostrará el portal de realidad mixta y se guiará al usuario para que se ponga en el casco.

Una aplicación que se inicia con una vista 2D en el monitor de escritorio puede crear una vista envolvente secundaria para mostrar el contenido del casco. Un ejemplo de esto es una ventana de borde 2D en el monitor en la que se muestra un vídeo de 360 grados en el casco.

![Las aplicaciones que se ejecutan en la vista envolvente son las únicas visibles](images/slide4-800px.png)<br>
*Una aplicación que se ejecuta en una vista envolvente es la única que está visible*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>vista 2D en la Página principal de Windows Mixed Reality

Cualquier cosa que no sea una vista envolvente se representa como una vista 2D en su mundo.

Una aplicación puede tener vistas 2D en el monitor de escritorio y en el casco. Una nueva vista 2D se colocará en el mismo Shell que la vista que la creó, ya sea en el monitor o en el casco. Actualmente, no es posible que una aplicación o un usuario mueva una vista 2D entre la Página principal de la realidad mixta y el monitor.

![Las aplicaciones que se ejecutan en la vista 2D comparten el espacio del mundo mixto con otras aplicaciones](images/slide5-800px.png)<br>
*Las aplicaciones que se ejecutan en una vista 2D comparten el espacio con otras aplicaciones*

### <a name="placement-of-additional-app-tiles"></a>Selección de ubicación de iconos de aplicación adicionales

Puede colocar tantas aplicaciones con una vista 2D en su mundo como desee con las API de [iconos secundarios](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Estos mosaicos "anclados" aparecerán como pantallas de presentación que los usuarios deben colocar y después podrán usar para iniciar la aplicación. Windows Mixed Reality no admite actualmente la representación del contenido del mosaico 2D como mosaicos dinámicos.

![Las aplicaciones pueden tener varias ubicaciones con iconos secundarios](images/slide6-800px.png)<br>
*Las aplicaciones pueden tener varias ubicaciones con iconos secundarios*

### <a name="switching-views"></a>Cambiar de vista

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Cambiar de la vista XAML 2D a la vista envolvente

Si la aplicación usa XAML, el [IFrameworkViewSource](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) de XAML controlará la primera vista de la aplicación. La aplicación deberá cambiar a la vista envolvente antes de activar **CoreWindow** para asegurarse de que la aplicación se inicia directamente en la experiencia envolvente.

Use [CoreApplication. CreateNewView](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) y [ApplicationViewSwitcher. SwitchAsync](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) para convertirlo en la vista activa.

> [!NOTE]
>* No especifique la marca [ApplicationViewSwitchingOptions. ConsolidateViews](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) en **SwitchAsync** al cambiar de la vista XAML a la vista envolvente, o bien se quitará del mundo la pizarra que inició la aplicación.
>* Se debe llamar a **SwitchAsync** mediante el [distribuidor](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) asociado a la vista en la que se va a cambiar.
>* Tendrá que volver a **SwitchAsync** a la vista XAML si necesita iniciar un teclado virtual o desea activar otra aplicación.

![Las aplicaciones pueden cambiar entre las vistas 2D y las vistas envolventes ](images/slide7-600px.png) ![ cuando una aplicación entra en una vista envolvente, el mundo mixto y otras aplicaciones desaparecen](images/slide8-600px.png)<br>
*Izquierda: las aplicaciones pueden cambiar entre la vista 2D y la vista envolvente. Right: cuando una aplicación entra en una vista envolvente, la Página principal de Windows Mixed Reality y otras aplicaciones desaparecen.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Cambiar de la vista envolvente de nuevo a una vista XAML de teclado

Una razón común para alternar entre las vistas es mostrar un teclado en una aplicación de realidad mixta. El shell solo puede mostrar el teclado del sistema si la aplicación muestra una vista 2D. Si la aplicación necesita obtener entrada de texto, puede proporcionar una vista XAML personalizada con un campo de entrada de texto, cambiar a ella y, a continuación, volver a cambiar después de que se complete la entrada.

Como en la sección anterior, puede usar **ApplicationViewSwitcher. SwitchAsync** para volver a la transición a una vista XAML desde la vista envolvente.

## <a name="app-size"></a>Tamaño de la aplicación

las vistas de aplicación 2D siempre aparecen en una pizarra virtual fija. Esto hace que todas las vistas 2D muestren la misma cantidad de contenido exacta. Estos son algunos detalles adicionales sobre el tamaño de la vista 2D de la aplicación:
* La relación de aspecto de la aplicación se conserva al cambiar el tamaño.
* La [resolución y el factor de escala](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) de la aplicación no cambian cambiando el tamaño.
* Las aplicaciones no pueden consultar su tamaño real en el mundo.

![las aplicaciones 2D aparecen con tamaños de ventana fijos](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Las aplicaciones con una vista 2D aparecen con tamaños de ventana fijos*

## <a name="app-tiles"></a>Iconos de la aplicación

El menú Inicio usa el icono pequeño estándar y el icono mediano para los pin y la lista **todas las aplicaciones** en la realidad mixta. 

![Menú Inicio de Windows Mixed Reality](images/start-500px.png)<br>
*Menú Inicio de Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>Interacciones entre aplicaciones y aplicaciones

A medida que crea aplicaciones, tiene acceso a la aplicación enriquecida a los mecanismos de comunicación de aplicaciones disponibles en Windows 10. Muchas de las nuevas API de protocolo y registros de archivos funcionan perfectamente en HoloLens para permitir el inicio y la comunicación de aplicaciones. 

En el caso de los auriculares de escritorio, la aplicación asociada a una extensión de archivo o protocolo determinados puede ser una aplicación Win32 que solo puede aparecer en el monitor de escritorio o en la pizarra de escritorio.

### <a name="protocols"></a>Protocolos

HoloLens admite el inicio de aplicaciones a través de la [Windows.SysTEM. API del iniciador](/uwp/api/Windows.System.Launcher).

Hay algunos aspectos que se deben tener en cuenta al iniciar otra aplicación:

* Cuando se realiza un inicio no modal, como [LaunchUriAsync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), el usuario debe colocar la aplicación antes de interactuar con ella.

* Al realizar un inicio modal, como a través de [LaunchUriForResultsAsync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), la aplicación modal se coloca en la parte superior de la ventana.

* Windows Mixed Reality no puede superponer aplicaciones encima de vistas exclusivas. Para mostrar la aplicación iniciada, Windows vuelve al usuario al mundo para mostrar la aplicación.

### <a name="file-pickers"></a>Selectores de archivos

HoloLens admite contratos de [FileOpenPicker](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) y [FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) . Sin embargo, no hay ninguna aplicación preinstalada que cumpla los contratos del selector de archivos. Estas aplicaciones (por ejemplo, OneDrive) se pueden instalar desde el Microsoft Store.

Si tiene más de una aplicación de selector de archivos instalada, no verá ninguna interfaz de usuario de desambiguación para elegir la aplicación que se va a iniciar. En su lugar, se elegirá el primer selector de archivos instalado. Cuando se guarda un archivo, se genera el nombre de archivo, que incluye la marca de tiempo. El usuario no puede cambiarlo.

De forma predeterminada, se admiten las siguientes extensiones localmente:

|  Aplicación  |  Extensiones | 
|----------|----------|
|  Fotos  |  BMP, GIF, JPG, PNG, AVI, MOV, MP4 y WMV | 
|  Microsoft Edge  |  htm, HTML, PDF, SVG, XML | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>Contratos de aplicaciones y extensiones de Windows Mixed Reality

Los contratos de aplicación y los puntos de extensión permiten registrar la aplicación para aprovechar las ventajas de las características más avanzadas del sistema operativo, como el control de una extensión de archivo o el uso de tareas en segundo plano. Esta es una lista de los contratos y puntos de extensión admitidos y no admitidos en HoloLens.

|  Contrato o extensión  |  ¿Compatible? | 
|----------|----------|
| [Proveedor de imágenes de cuenta (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | No compatible | 
| [Alarma](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | No compatible | 
| [App Service](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | Compatible pero no totalmente funcional | 
| [Proveedor de citas](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | No compatible | 
| [Reproducción automática (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | No compatible | 
| [Tareas en segundo plano (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | Parcialmente compatible (no todos los desencadenadores funcionan) | 
| [Tarea de actualización (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | Compatible | 
| [Contrato del actualizador de archivos en caché](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | Compatible | 
| [Configuración de la cámara (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | No compatible | 
| [Protocolo de marcado](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | No compatible | 
| [Activación de archivos (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | Compatible | 
| [Contrato del selector para abrir archivos](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | Compatible | 
| [Contrato del selector para guardar archivos](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | Compatible | 
| [Llamada a la pantalla de bloqueo](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | No compatible | 
| [Reproducción de multimedia](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | No compatible | 
| [Reproducir en contrato](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | No compatible | 
| [Tarea de configuración preinstalada](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | No compatible | 
| [Imprimir flujo de trabajo 3D](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | Compatible | 
| [Configuración de la tarea de impresión (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | No compatible | 
| [Activación de URI (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | Compatible | 
| [Inicio restringido](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | No compatible | 
| [Buscar contrato](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | No compatible | 
| [Contrato de configuración](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | No compatible | 
| [Compartir contrato](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | No compatible | 
| [SSL/certificados (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | Compatible | 
| [Proveedor de cuentas web](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | Compatible | 

## <a name="app-file-storage"></a>Almacenamiento de archivos de aplicación

Todo el almacenamiento se realiza a través del [espacio de nombres Windows. Storage](/uwp/api/Windows.Storage). HoloLens no es compatible con la sincronización/itinerancia de App Storage. Para obtener más información, consulte la documentación siguiente:

* [Archivos, carpetas y bibliotecas](/windows/uwp/files/index)
* [Almacenar y recuperar la configuración y otros datos de aplicación](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Carpetas conocidas

Consulte [KnownFolders](/uwp/api/Windows.Storage.KnownFolders) para obtener los detalles completos de las aplicaciones para UWP.

<table>
<tr>
<th> Propiedad</th><th> Compatible con HoloLens</th><th> Compatible con auriculares inmersivo</th><th> Descripción</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de capturas de la aplicación.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de rollo de cámara.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de documentos. La biblioteca de documentos no está pensada para su uso general.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de música.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta 3D de objetos.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de imágenes.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Reproducción</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta play lists.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta imágenes guardadas.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de vídeos.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Grupo Hogar</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta grupo hogar.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de los dispositivos de servidor multimedia (red de redes digitales (DLNA)).</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de llamadas grabadas.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta dispositivos extraíbles.</td>
</tr>
</table>

## <a name="app-package"></a>Paquete de aplicaciones

Con Windows 10, ya no tiene como destino un sistema operativo, sino [que dirige su aplicación a una o varias familias de dispositivos](/windows/uwp/get-started/universal-application-platform-guide#device-families). Una familia de dispositivos identifica las API, las características del sistema y los comportamientos que puedes esperar en todos los dispositivos de la familia. También determina el conjunto de dispositivos en los que se puede instalar la aplicación desde el [Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Para tener como destino los auriculares de escritorio y HoloLens, destine su aplicación a **Windows.** Familia de dispositivos universales.
* Para dirigirse solo a auriculares de escritorio, dirija su aplicación a la familia de dispositivos **Windows. Desktop** .
* Para dirigirse solo a HoloLens, dirige la aplicación a la familia de dispositivos **Windows. Holographic** .

## <a name="see-also"></a>Consulte también

* [Vistas de aplicación](app-views.md)
* [Actualización de aplicaciones para UWP bidimensionales para la realidad mixta](../develop/porting-apps/building-2d-apps.md)
* [Guía de diseño del iniciador de aplicaciones 3D](../distribute/3d-app-launcher-design-guidance.md)
* [Implementación de iniciadores de aplicaciones 3D](../distribute/implementing-3d-app-launchers.md)