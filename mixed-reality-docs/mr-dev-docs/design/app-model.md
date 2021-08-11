---
title: Modelo de aplicación
description: Windows Mixed Reality usa el modelo de aplicación proporcionado por universal Windows Platform, un modelo y un entorno para aplicaciones Windows modernas.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, modelo de aplicación, ciclo de vida, suspender, reanudar, icono, vistas, contratos, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5f15f0a2516a21cd6432e7f09df7950f8d832acc77ac77056f5bf1382500024e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221941"
---
# <a name="app-model"></a>Modelo de aplicación

Windows Mixed Reality usa el modelo de aplicación proporcionado por la Plataforma [universal de Windows](/windows/uwp/get-started/) (UWP), que es un modelo y un entorno para aplicaciones Windows modernas. El modelo de aplicación para UWP define cómo se instalan, actualizan, versiona y quitan completamente las aplicaciones de forma segura. También rige el ciclo de vida de la aplicación (cómo se ejecutan, se detienen y se detienen las aplicaciones) y cómo pueden conservar el estado. Por último, el modelo de aplicación trata la integración y la interacción con el sistema operativo, los archivos y otras aplicaciones.

![Aplicaciones 2D organizadas en la Windows Mixed Reality hogar en un área de menú](images/20160112-055908-hololens-500px.jpg)<br>
*Aplicaciones con una vista 2D organizada en la Windows Mixed Reality principal*

## <a name="app-lifecycle"></a>Ciclo de vida de la aplicación

El ciclo de vida de una aplicación de realidad mixta implica conceptos de aplicaciones estándar, como la selección de ubicación, el inicio, la finalización y la eliminación.

### <a name="placement-is-launch"></a>Se inicia la selección de ubicación

Cada aplicación se inicia en realidad mixta colocando un icono de aplicación (solo un Windows [secundario)](/uwp/api/Windows.UI.StartScreen.SecondaryTile)en el [Windows Mixed Reality principal.](../discover/navigating-the-windows-mixed-reality-home.md) Estos iconos de aplicación, al colocarse, comenzarán a ejecutar la aplicación. Estos iconos de aplicación se conservan y permanecen en su ubicación colocada, actuando como iniciadores en cualquier momento en el que quiera volver a la aplicación.

![La selección de ubicación coloca un icono secundario en el mundo](images/slide1-600px.png)<br>
*La selección de ubicación coloca un icono secundario en el mundo*

En cuanto se completa la selección de [](app-model.md#protocols) ubicación (a menos que una aplicación haya iniciado la colocación en el inicio de la aplicación), la aplicación comienza a iniciarse. Windows Mixed Reality ejecutar un número limitado de aplicaciones a la vez. En cuanto coloque e inicie una aplicación, es posible que se suspendan otras aplicaciones activas. Las aplicaciones suspendidas dejan una captura de pantalla del último estado de la aplicación en el icono de la aplicación dondequiera que la coloque. Para obtener más información sobre cómo controlar los eventos de reanudación y otros ciclos de vida, Windows 10 ciclo de vida de [la aplicación para UWP.](/windows/uwp/launch-resume/app-lifecycle)

![Después de colocar un icono, la aplicación comienza a ejecutar el diagrama de estado para la aplicación en ](images/slide2-500px.png) ![ ejecución, suspendida o no en ejecución.](images/ic576232-500px.png)<br>
*Izquierda: después de colocar un icono, la aplicación comienza a ejecutarse. Derecha: diagrama de estado para la aplicación en ejecución, suspendida o no en ejecución.*

### <a name="remove-is-closeterminate-process"></a>Quitar es el proceso de cierre o terminación

Cuando se quita un icono de aplicación colocado del mundo, los procesos subyacentes se cierran. Esto puede ser útil para asegurarse de que la aplicación se detiene o reinicia una aplicación problemática.

### <a name="app-suspensiontermination"></a>Suspensión o terminación de la aplicación

En la [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)principal, el usuario puede crear varios puntos de entrada para una aplicación iniciando la aplicación desde el menú Inicio colocando el icono de la aplicación en el mundo. Cada icono de aplicación se comporta como un punto de entrada diferente y tiene una instancia de icono independiente en el sistema. Una consulta para [SecondaryTile.FindAllAsync](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) dará como resultado **un SecondaryTile** para cada instancia de aplicación.

Cuando se suspende una aplicación para UWP, se toma una captura de pantalla del estado actual.

![Se muestran capturas de pantalla para aplicaciones suspendidas](images/slide9-800px.png)<br>
*Se muestran capturas de pantalla para aplicaciones suspendidas*

Una diferencia clave de otros shells de Windows 10 es cómo se informa a la aplicación de la activación de una instancia de aplicación a través de los eventos [CoreApplication.Resuming](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) y [CoreWindow.Activated.](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated)

|  Escenario |  Reanudando  |  Activado | 
|----------|----------|----------|
|  Inicie una nueva instancia de la aplicación desde el menú Inicio  |   |  **Activado** con un [nuevo TileId](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Inicie la segunda instancia de la aplicación desde el menú Inicio  |   |  **Activado** con un **nuevo TileId** | 
|  Seleccione la instancia de la aplicación que no está activa actualmente.  |   |  **Activado** con el **TileId** asociado a la instancia | 
|  Seleccione otra aplicación y, a continuación, seleccione la instancia previamente activa.  |  **Reanudación** de la generación  |  | 
|  Seleccione otra aplicación y, a continuación, seleccione la instancia que estaba inactiva anteriormente.  |  **Reanudación** de la generación  |  A **continuación,** se activa **con el TileId** asociado a la instancia de | 

### <a name="extended-execution"></a>Ejecución extendida

A veces, la aplicación debe seguir trabajando en segundo plano o reproduciendo audio. [Las tareas en](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) segundo plano están disponibles HoloLens.

![Las aplicaciones se pueden ejecutar en segundo plano](images/slide10-800px.png)<br>
*Las aplicaciones se pueden ejecutar en segundo plano*

## <a name="app-views"></a>Vistas de aplicación

Cuando se activa la aplicación, puede elegir qué tipo de vista le gustaría mostrar. Para **CoreApplication** de una aplicación, siempre [](/uwp/api/Windows.UI.ViewManagement.ApplicationView) hay una vista de aplicación principal y cualquier número de otras vistas de aplicación que quiera crear. En el escritorio, puede pensar en una vista de aplicación como una ventana. Nuestras plantillas de aplicación de realidad mixta crean un proyecto de Unity donde la vista de aplicación principal es [envolvente.](app-views.md) 

La aplicación puede crear una vista de aplicación 2D adicional mediante tecnología como XAML, para usar características Windows 10 como la compra desde la aplicación. Si la aplicación se inició como una aplicación para UWP Windows 10 dispositivos, la vista principal es 2D. Sin embargo, puede "encender" en la realidad mixta agregando otra vista de aplicación que sea envolvente para mostrar una experiencia por volumen. Imagine crear una aplicación de visor de fotos en XAML donde el botón de presentación cambió a una vista de aplicación inmersiva que fotos de la aplicación en todo el mundo y superficies.

![La aplicación en ejecución puede tener una vista 2D o una vista inmersiva](images/slide3-800px.png)<br>
*La aplicación en ejecución puede tener una vista 2D o una vista inmersiva*

### <a name="creating-an-immersive-view"></a>Creación de una vista inmersiva

Las aplicaciones de realidad mixta crean una vista inmersiva, que se logra con el [tipo HolographicSpace.](/uwp/api/windows.graphics.holographic.holographicspace)

Una aplicación que sea puramente inmersiva siempre debe crear una vista inmersiva al iniciarse, incluso si se inicia desde el escritorio. Las vistas inmersivas siempre se muestran en el casco, independientemente de dónde se crearon. Al activar una vista inmersiva se mostrará el Portal de realidad mixta y se guiará al usuario para que se ponga el casco.

Una aplicación que comienza con una vista 2D en el monitor de escritorio puede crear una vista inmersiva secundaria para mostrar contenido en el casco. Un ejemplo de esto es una ventana perimetral 2D en el monitor que muestra un vídeo de 360 grados en el casco.

![Las aplicaciones que se ejecutan en la vista inmersiva son las únicas visibles](images/slide4-800px.png)<br>
*Una aplicación que se ejecuta en una vista inmersiva es la única visible*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Vista 2D en la página Windows Mixed Reality inicio

Todo lo que no sea una vista inmersiva se representa como una vista 2D en su mundo.

Una aplicación puede tener vistas 2D en el monitor de escritorio y en el casco. Se colocará una nueva vista 2D en el mismo shell que la vista que lo creó, ya sea en el monitor o en el casco. Actualmente no es posible que una aplicación o un usuario muevan una vista 2D entre el Mixed Reality principal y el monitor.

![Las aplicaciones que se ejecutan en la vista 2D comparten el espacio en el mundo mixto con otras aplicaciones](images/slide5-800px.png)<br>
*Las aplicaciones que se ejecutan en una vista 2D comparten el espacio con otras aplicaciones*

### <a name="placement-of-additional-app-tiles"></a>Colocación de iconos de aplicación adicionales

Puede colocar tantas aplicaciones con una vista 2D en su mundo como desee con las API [de mosaico secundario.](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles) Estos iconos "anclados" aparecerán como pantallas de presentación que los usuarios deben colocar y, a continuación, pueden usarse posteriormente para iniciar la aplicación. Windows Mixed Reality no admite actualmente la representación del contenido del icono 2D como iconos dinámicos.

![Las aplicaciones pueden tener varias ubicaciones mediante iconos secundarios](images/slide6-800px.png)<br>
*Las aplicaciones pueden tener varias ubicaciones mediante iconos secundarios*

### <a name="switching-views"></a>Cambio de vistas

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Cambio de la vista XAML 2D a la vista inmersiva

Si la aplicación usa XAML, el [IFrameworkViewSource](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) de XAML controlará la primera vista de la aplicación. La aplicación tendrá que cambiar a la vista inmersiva antes de activar **CoreWindow** para asegurarse de que la aplicación se inicia directamente en la experiencia inmersiva.

Use [CoreApplication.CreateNewView](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) [y ApplicationViewSwitcher.SwitchAsync](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) para convertirla en la vista activa.

> [!NOTE]
>* No especifique la marca [ApplicationViewSwitchingOptions.ConsolidateViews](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) en **SwitchAsync** al cambiar de la vista XAML a la vista inmersiva, o la pizarra que inició la aplicación se quitará del mundo.
>* Se debe llamar a **SwitchAsync** mediante [el distribuidor](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) asociado a la vista a la que está cambiando.
>* Tendrá que volver **a SwitchAsync** a la vista XAML si necesita iniciar un teclado virtual o quiere activar otra aplicación.

![Las aplicaciones pueden cambiar entre vistas 2D y vistas inmersivas Cuando una aplicación entra en una vista inmersiva, el mundo mixto ](images/slide7-600px.png) ![ y otras aplicaciones desaparecen.](images/slide8-600px.png)<br>
*Izquierda: las aplicaciones pueden cambiar entre la vista 2D y la vista inmersiva. Derecha: cuando una aplicación entra en una vista inmersiva, el Windows Mixed Reality y otras aplicaciones desaparecen.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Cambio de la vista inmersiva a una vista XAML de teclado

Una razón común para cambiar de una vista a otra es mostrar un teclado en una aplicación de realidad mixta. El shell solo puede mostrar el teclado del sistema si la aplicación muestra una vista 2D. Si la aplicación necesita obtener entrada de texto, puede proporcionar una vista XAML personalizada con un campo de entrada de texto, cambiar a ella y, a continuación, volver a cambiar una vez completada la entrada.

Al igual que en la sección anterior, puedes usar **ApplicationViewSwitcher.SwitchAsync** para volver a realizar la transición a una vista XAML desde la vista inmersiva.

## <a name="app-size"></a>Tamaño de la aplicación

Las vistas de aplicaciones 2D siempre aparecen en una pizarra virtual fija. Esto hace que todas las vistas 2D muestren exactamente la misma cantidad de contenido. Estos son algunos detalles adicionales sobre el tamaño de la vista 2D de la aplicación:
* La relación de aspecto de la aplicación se conserva al volver a tamaño.
* La [resolución de aplicaciones y el factor](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) de escala no se cambian al cambiar el tamaño.
* Las aplicaciones no pueden consultar su tamaño real en el mundo.

![Las aplicaciones 2D aparecen con tamaños fijos de ventana](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Las aplicaciones con una vista 2D aparecen con tamaños fijos de ventana*

## <a name="app-tiles"></a>Iconos de aplicación

El menú Inicio usa el icono pequeño estándar y el  icono mediano para los pines y la lista Todas las aplicaciones en realidad mixta. 

![El menú Inicio para Windows Mixed Reality](images/start-500px.png)<br>
*El menú Inicio para Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>Interacciones de aplicación a aplicación

A medida que compila aplicaciones, tiene acceso a la aplicación enriquección a los mecanismos de comunicación de aplicaciones disponibles en Windows 10. Muchas de las nuevas API de protocolo y registros de archivos funcionan perfectamente en HoloLens permitir el inicio y la comunicación de aplicaciones. 

En el caso de los cascos de escritorio, la aplicación asociada a una extensión de archivo o protocolo determinados puede ser una aplicación Win32 que solo puede aparecer en el monitor de escritorio o en la pizarra del escritorio.

### <a name="protocols"></a>Protocolos

HoloLens admite el inicio de aplicaciones a aplicaciones a través [deWindows.System.Selector API](/uwp/api/Windows.System.Launcher).

Hay algunos aspectos que se deben tener en cuenta al iniciar otra aplicación:

* Al realizar un inicio no modal, como [LaunchUriAsync,](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)el usuario debe colocar la aplicación antes de interactuar con ella.

* Al realizar un inicio modal, como a través [de LaunchUriForResultsAsync,](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)la aplicación modal se coloca en la parte superior de la ventana.

* Windows Mixed Reality no se pueden superponer aplicaciones sobre vistas exclusivas. Para mostrar la aplicación iniciada, Windows que el usuario vuelva al mundo para mostrar la aplicación.

### <a name="file-pickers"></a>Selectores de archivos

HoloLens admite los [contratos FileOpenPicker](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) y [FileSavePicker.](/uwp/api/Windows.Storage.Pickers.FileSavePicker) Sin embargo, no hay ninguna aplicación preinstalada que cumpla los contratos del selector de archivos. Estas aplicaciones ,OneDrive, por ejemplo, se pueden instalar desde el Microsoft Store.

Si tiene más de una aplicación de selector de archivos instalada, no verá ninguna interfaz de usuario de desambiguación para elegir qué aplicación se va a iniciar. En su lugar, se elegirá el primer selector de archivos instalado. Al guardar un archivo, se genera el nombre de archivo, que incluye la marca de tiempo. El usuario no puede cambiarlo.

De forma predeterminada, las siguientes extensiones se admiten localmente:

|  Aplicación  |  Extensiones | 
|----------|----------|
|  Fotos  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>Contratos de aplicación y Windows Mixed Reality de aplicaciones

Los contratos de aplicación y los puntos de extensión permiten registrar la aplicación para aprovechar las características más profundas del sistema operativo, como el control de una extensión de archivo o el uso de tareas en segundo plano. Esta es una lista de los contratos y puntos de extensión admitidos y no admitidos en HoloLens.

|  Contrato o extensión  |  ¿Compatible? | 
|----------|----------|
| [Proveedor de imágenes de cuenta (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | No compatible | 
| [Alarma](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | No compatible | 
| [App Service](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | Compatible, pero no totalmente funcional | 
| [Proveedor de citas](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | No compatible | 
| [Reproducción automática (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | No compatible | 
| [Tareas en segundo plano (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | Parcialmente compatible (no todos los desencadenadores funcionan) | 
| [Tarea De actualización (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | Compatible | 
| [Contrato del actualizador de archivos almacenados en caché](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | Compatible | 
| [Configuración de la cámara (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | No compatible | 
| [Protocolo de marcado](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | No compatible | 
| [Activación de archivos (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | Compatible | 
| [contrato del Selector de archivos para abrir](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | Compatible | 
| [contrato del Selector de guardar archivo](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | Compatible | 
| [Llamada a la pantalla de bloqueo](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | No compatible | 
| [Reproducción de multimedia](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | No compatible | 
| [Reproducir en contrato](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | No compatible | 
| [Tarea de configuración preinstalada](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | No compatible | 
| [Impresión 3D de trabajo](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | Compatible | 
| [Configuración de la tarea de impresión (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | No compatible | 
| [Activación de URI (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | Compatible | 
| [Inicio restringido](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | No compatible | 
| [Contrato de búsqueda](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | No compatible | 
| [Configuración contrato](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | No compatible | 
| [Compartir contrato](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | No compatible | 
| [SSL/certificates (extensión)](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | Compatible | 
| [Proveedor de cuentas web](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | Compatible | 

## <a name="app-file-storage"></a>Almacenamiento de archivos de aplicación

Todo el almacenamiento se hace a través [del espacio de nombres Windows.Storage .](/uwp/api/Windows.Storage) HoloLens no admite la sincronización o itinerancia del almacenamiento de aplicaciones. Para más información, consulte la documentación siguiente:

* [Archivos, carpetas y bibliotecas](/windows/uwp/files/index)
* [Almacenar y recuperar la configuración y otros datos de aplicación](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Carpetas conocidas

Consulta [KnownFolders para](/uwp/api/Windows.Storage.KnownFolders) obtener todos los detalles de las aplicaciones para UWP.

<table>
<tr>
<th> Propiedad</th><th> Compatible con HoloLens</th><th> Compatible con cascos envolventes</th><th> Description</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta Capturas de aplicación.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta Camera Roll.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca De documentos. La biblioteca de documentos no está pensada para uso general.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la Música de datos.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta Objects 3D.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca Pictures.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Listas</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de listas de reproducción.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta Imágenes guardadas.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de vídeos.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Grupo Hogar</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta HomeGroup.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de dispositivos del servidor multimedia (Digital Living Network Alliance (DLNA)).</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de llamadas registradas.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta dispositivos extraíbles.</td>
</tr>
</table>

## <a name="app-package"></a>Paquete de aplicaciones

Con Windows 10, ya no tiene como destino un sistema operativo, sino que la aplicación se dirigirá a una o varias familias [de dispositivos.](/windows/uwp/get-started/universal-application-platform-guide#device-families) Una familia de dispositivos identifica las API, las características del sistema y los comportamientos que puedes esperar en todos los dispositivos de la familia. También determina el conjunto de dispositivos en los que se puede instalar la aplicación desde [el Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Para dirigirse a cascos de escritorio y HoloLens, dirigir la aplicación al **Windows. Familia de** dispositivos universales.
* Para dirigirse solo a cascos de escritorio, el destino de la aplicación **es el Windows. Familia de** dispositivos de escritorio.
* Para dirigirse solo HoloLens, el destino de la aplicación es **el Windows. Familia de dispositivos** holográficos.

## <a name="see-also"></a>Consulte también

* [Vistas de aplicación](app-views.md)
* [Actualización de aplicaciones para UWP bidimensionales para la realidad mixta](../develop/porting-apps/building-2d-apps.md)
* [Guía de diseño del iniciador de aplicaciones 3D](../distribute/3d-app-launcher-design-guidance.md)
* [Implementación de iniciadores de aplicaciones 3D](../distribute/implementing-3d-app-launchers.md)