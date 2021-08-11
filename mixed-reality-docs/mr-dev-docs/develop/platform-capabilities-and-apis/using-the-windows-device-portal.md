---
title: Uso de Portal de dispositivos Windows
description: Obtenga información sobre cómo configurar y administrar el dispositivo de forma remota a través de Wi-Fi o USB mediante el Portal de dispositivos Windows.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Portal de dispositivos Windows, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: edcd1796598b558f42232bf54ae3d40d3c509bb9515d8dcbe7f3cf9f2b7dfd62
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221595"
---
# <a name="using-the-windows-device-portal"></a>Uso de Portal de dispositivos Windows

<table>
<tr>
<th>Característica</th><th style="width:150px"><a href="/hololens/hololens1-hardware">HoloLens (1ª generación)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px">
</tr><tr>
<td> Portal de dispositivos Windows</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Portal de dispositivos Windows para HoloLens te permite configurar y administrar de forma remota el dispositivo mediante Wi-Fi o USB. Device Portal es un servidor web en el dispositivo HoloLens al que puedes conectarte desde un navegador web del equipo. Portal de dispositivos incluye muchas herramientas que te ayudarán a administrar tu HoloLens, así como a depurar y optimizar tus aplicaciones.

Esta documentación trata específicamente sobre el Portal de dispositivos Windows para HoloLens. Para usar Portal de dispositivos Windows para escritorio (incluido para Windows Mixed Reality), consulta [Introducción a Portal de dispositivos Windows](/windows/uwp/debug-test-perf/device-portal).

> [NOTA] No se recomienda usar el Portal de dispositivos para los dispositivos HoloLens que va a implementar en su organización.

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configuración de HoloLens para usar Portal de dispositivos Windows

1. Enciende HoloLens y colócalo en el dispositivo.
2. Realice el [gesto Inicio](/hololens/hololens2-basic-usage#start-gesture) para HoloLens 2 o el de [eclosión](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) en HoloLens (primera generación) para iniciar el menú principal. 
3. Mire el icono de **Configuración** y realice un gesto de [pulsación en el aire](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) en HoloLens (primera generación). También puede seleccionarlo en HoloLens 2 si lo [toca o usa un haz de mano](/hololens/hololens2-basic-usage). 
4. Selecciona el elemento de menú **Actualizar**.
5. Selecciona el elemento de menú **Para desarrolladores**.
6. Habilita el **Modo de desarrollador**.

> [!IMPORTANT]
> Si dispone del privilegio multiusuario en lugar de administrador, es posible que la capacidad para entrar en el modo de desarrollador se muestre atenuada. Asegúrese de que es un **[administrador del dispositivo](/hololens/security-adminless-os)** .

7. [Desplázate hacia abajo](../../design/gaze-and-commit.md#composite-gestures) y habilita **Portal de dispositivos**.
8. Si está configurando un Portal de dispositivos Windows para que pueda implementar aplicaciones en este dispositivo HoloLens a través de USB o Wi-Fi, seleccione **Emparejar** para [generar un PIN de emparejamiento](using-visual-studio.md). Deja la aplicación Configuración en el menú emergente del PIN hasta que escribas el PIN en Visual Studio durante la primera implementación.

![Habilitación del modo de desarrollador en la aplicación Configuración para Windows Holographic](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a>Conexión mediante Wi-Fi

1. [Conecta HoloLens a una red Wi-Fi](/hololens/hololens-network).
2. Busque la dirección IP del dispositivo mediante una de las siguientes acciones:
  * Vaya a **Configuración > Red e Internet > Wi-Fi > Opciones avanzadas**.
  * Vaya a **Configuración > Red e Internet** y seleccione **Propiedades de hardware**.
  * Uso del comando de voz "¿Cuál es mi dirección IP?".

![Configuración de HoloLens 2](images/using-windows-portal-img-02.jpg)

3. Desde un explorador web de tu equipo, ve a https://<TU_DIRECCIÓN_IP_HOLOLENS>
   * Se mostrará el siguiente mensaje en el explorador: "Hay un problema con el certificado de seguridad de este sitio web"; esto es debido a que el certificado que se emite para el Portal de dispositivos es un certificado de prueba. Puede ignorar este error de certificado por ahora y continuar.

## <a name="connecting-over-usb"></a>Conexión mediante USB

> [!IMPORTANT]
> IpOverUsb ya no se recomienda según los nuevos estándares del explorador, ya que requiere el uso del puerto 10080. Si aun así desea usar IpOverUsb, active la casilla "Conectividad del dispositivo USB" durante la instalación de Visual Studio, que no está activada de manera predeterminada. En su lugar, se recomienda conectarse con UsbNcm, que se admite de manera predeterminada en HoloLens 2. Si usa un HoloLens 1, se recomienda conectarse al equipo mediante Wi-Fi.

1. Si el HoloLens 2 ejecuta Windows Holographic, versión 21H1 o posterior, vaya a Para desarrolladores en la aplicación Configuración y asegúrese de que la opción Detección de dispositivos esté activa. 
2. Conecte el HoloLens 2 al equipo con un cable USB-C.
3. Busque la dirección IP de UsbNcm. Existen algunas maneras de hacerlo:
  * En la aplicación Configuración en el dispositivo (este método solo funciona para dispositivos HoloLens que ejecutan Windows Holographic, versión 21H1 o posterior, con la opción "Detección de dispositivos" activada).
    1. Vaya a la aplicación Configuración en el dispositivo.
    2. Vaya a Actualización y seguridad > Para desarrolladores. Este es el mismo lugar en el que habilitó el Portal de dispositivos.
    3. Al final de la página, copie la dirección IP de **Ethernet**. Esta es la dirección IP de UsbNcm. 
    ![Configuración de HoloLens 2: IP de UsbNcm](images/deviceportal_usbncm_ipaddress.jpg)

  * En el Portal de dispositivos 
    1. En el dispositivo, abra el Portal de dispositivos con la dirección de Wi-Fi del HoloLens. Si no conoce la dirección Wi-Fi del HoloLens, puede usar el comando de voz "¿Cuál es mi dirección IP?".
    2. Vaya a Sistema > Redes.
    3. En el extremo derecho de la página, en el panel "Configuración de IP", busque la sección que comienza con "Descripción: Función UsbNcm".
    4. Su dirección IP de UsbNcm es la línea "Dirección IPv4". Puede copiar la dirección o simplemente hacer clic en ella: es un hipervínculo que se volverá a abrir en el Portal de dispositivos con la dirección IP de UsbNcm.
  
  * En un símbolo del sistema
    1. En cualquier símbolo del sistema, vaya a la carpeta bin\<SDK version>\x86, donde está instalado el SDK de Windows 10, por ejemplo: C:\Archivos de programa (x86)\Windows Kits\10\bin\10.0.19041.0\x86.
    2. Escriba "dispositivos winappdeploycmd" y presione ENTRAR.
    3. En la salida, busque la entrada donde la columna Modelo/Nombre sea el nombre de su dispositivo HoloLens, como HOLOLENS-xxxxxx. La dirección IP de UsbNcm está al principio de esta línea y será una dirección IP privada automática con el formato 169.254.x.x. Copie esta dirección. 
 
4. Si copió la dirección IP de UsbNcm, desde un explorador web del equipo, vaya a https://, seguido de la dirección IP de UsbNcm.

### <a name="moving-files-over-usb"></a>Transferencia de archivos a través de USB

Puede transferir archivos desde su equipo a HoloLens sin necesidad de realizar ninguna configuración adicional.
1. Conexión de su equipo a HoloLens con un cable USB
2. Arrastre sus archivos a **PC\\[Nombre_De_Su_Dispositivo_HoloLens]\Internal Storage** de su escritorio.
3. Abra el **menú Inicio** y seleccione **Todas las aplicaciones > Explorador de archivos** en HoloLens.

> [!NOTE]
> Es posible que tenga que seleccionar **Este dispositivo** en el lado izquierdo del panel para salir de "Utilizados recientemente" y buscar los archivos. 

## <a name="connecting-to-an-emulator"></a>Conexión a un emulador

También puedes usar Device Portal con el emulador. Para conectarte al Portal de dispositivos, usa la [barra de herramientas](using-the-hololens-emulator.md). Seleccione este icono: ![Icono de Open Device Portal](images/emulator-deviceportal.png) **Open Device Portal** (Abrir portal de dispositivos): abre el Portal de dispositivos Windows correspondiente al sistema operativo de HoloLens en el emulador.

## <a name="creating-a-username-and-password"></a>Creación de un nombre de usuario y una contraseña

![Configuración del acceso a Portal de dispositivos Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configuración del acceso a Portal de dispositivos Windows*

La primera vez que se conectes al Portal de dispositivos en HoloLens, debe crear un nombre de usuario y una contraseña.
1. En un explorador web de tu equipo, escribe la dirección IP de HoloLens. Se abrirá la página de acceso Configuración.
2. Haga clic o pulse **Solicitar PIN** y mire la pantalla de HoloLens para obtener el PIN generado.
3. Escribe el PIN en el cuadro de texto **PIN displayed on your device** (PIN mostrado en el dispositivo).
4. Escriba el nombre de usuario que usará para conectarse al Portal de dispositivos. No es necesario que sea un nombre de cuenta de Microsoft (MSA) ni un nombre de dominio.
5. Escribe una contraseña y confírmala. La contraseña debe tener al menos siete caracteres de longitud. No es necesario que sea una MSA ni una contraseña de dominio.
6. Haz clic en **Emparejar** para conectarte al Portal de dispositivos Windows en HoloLens.

Si quieres cambiar este nombre de usuario o contraseña en cualquier momento, puedes repetir este proceso. Para ello, visita la página de seguridad del dispositivo navegando hasta: https://<TU_DIRECCIÓN_IP_HOLOLENS>/devicepair.htm.

## <a name="security-certificate"></a>Certificado de seguridad

Si ves un "error de certificado" en el explorador, puedes corregirlo mediante la creación de una relación de confianza con el dispositivo.

Cada HoloLens genera un certificado autofirmado para su conexión de SSL. De manera predeterminada, este certificado no es de confianza por parte del explorador web de tu equipo y puede que recibas un "error de certificado". Puede conectarse al dispositivo de forma segura si descarga este certificado desde HoloLens (a través del USB o de una red Wi-Fi en la que confíe) y agregándolo al equipo.
1. **Asegúrate de que estás en una red segura (USB o una red Wi-Fi de confianza).**
2. Descarga el certificado de este dispositivo desde la página "Seguridad" de Portal de dispositivos.
   * Ve a: https://<TU_DIRECCIÓN_IP_HOLOLENS>/devicepair.htm
   * Abre el nodo Sistema > Preferencias. 
   * Desplácese hacia abajo hasta la opción Seguridad del dispositivo y haga clic en el botón "Download this device's certificate" (Descargar el certificado de este dispositivo).
3. Instala el certificado en el almacén "Entidades de certificación raíz de confianza" en tu equipo.
   * En el menú Windows, escribe: Administrar certificados de equipo e inicia el applet.
   * Expande la carpeta **Entidad de certificación de raíz de confianza**.
   * Haga clic en la carpeta **Certificados**.
   * En el menú Acción, selecciona: Todas las tareas > Importar...
   * Completa el Asistente para importación de certificados con el archivo de certificado descargado desde Device Portal.
4. Reinicia el explorador.

>[!NOTE]
> Este certificado solo será de confianza para el dispositivo y el usuario tendrá que volver a realizar el proceso si se instala una imagen en el dispositivo.

## <a name="sideloading-applications"></a>Instalación de prueba de aplicaciones

### <a name="installing-a-certificate"></a>Instalación de un certificado

1. En el Portal de dispositivos Windows, vaya a la página del administrador de **aplicaciones**.
2. En la sección Implementar aplicaciones, seleccione **Instalar certificado**.
3. En la sección para seleccionar un archivo de certificado (.cer) para firmar el paquete de aplicación, seleccione Elegir archivo y busque el certificado asociado al paquete de la aplicación que quiere transferir localmente.
4. Seleccione **Instalar** para iniciar la instalación.

![Captura de pantalla de la página del administrador de aplicaciones abierta en el Portal de dispositivos Windows](images/sideloading-1.png)

### <a name="installing-an-app"></a>Instalación de una aplicación

> [!NOTE]
> Para que una aplicación se instale correctamente a través del Portal de dispositivos, debe estar firmada por un certificado y este certificado debe instalarse en el dispositivo antes de intentar instalar la aplicación. Consulte la [sección anterior](#installing-a-certificate) para leer instrucciones.

1. Cuando haya [creado un paquete de la aplicación desde Visual Studio](using-visual-studio.md), podrá instalarlo remotamente en el dispositivo desde los archivos generados:

![Captura de pantalla del contenido del archivo del paquete de la aplicación](images/sideloading-2.png)

2. En el Portal de dispositivos Windows, vaya a la página del administrador de **aplicaciones**.
3. En la sección **Implementar** aplicaciones, seleccione **Almacenamiento local**.
4. En la sección para seleccionar el paquete de aplicación, seleccione Elegir archivo y busque el paquete de la aplicación que quiere transferir localmente.
5. Active las casillas correspondientes si quiere instalar paquetes opcionales o de marcos junto con la instalación de la aplicación y seleccione **Siguiente**:

![Captura de pantalla de la página del administrador de aplicaciones abierta en el Portal de dispositivos Windows con la pestaña Almacenamiento local resaltada](images/sideloading-3.png)

6. Seleccione **Instalar** para iniciar la instalación.
 
![Captura de pantalla de la página del administrador de aplicaciones abierta en el Portal de dispositivos Windows con la instalación completada correctamente](images/sideloading-4.png) 

Una vez finalizada la instalación, vuelva a la página **Todas las aplicaciones** de HoloLens e inicie la aplicación recién instalada.

## <a name="device-portal-pages"></a>Páginas de Device Portal

### <a name="home"></a>Inicio

![Página principal de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-04.png)<br>
*Página principal de Portal de dispositivos Windows en Microsoft HoloLens*

> [NOTA] Los valores configurados en el Portal de dispositivos se aplican a todo el dispositivo y se conservan luego de reiniciar. Se recomienda usar el Portal de dispositivos solo durante el desarrollo, y no en dispositivos implementados.

La sesión de Device Portal se inicia en la página principal. Accede a otras páginas desde la barra de navegación en el lado izquierdo de la página principal.

La barra de herramientas de la parte superior de la página proporciona acceso al estado usado frecuentemente y a las características.
* **En línea**: indica si el dispositivo está conectado a Wi-Fi.
* **Apagar**: apaga el dispositivo.
* **Reiniciar**: apaga y vuelve a encender el dispositivo.
* **Seguridad**: abre la página Seguridad del dispositivo.
* **Frío**: indica la temperatura del dispositivo.
* **CA**: indica si el dispositivo está enchufado y cargándose.
* **Ayuda**: abre la página de documentación de la interfaz REST.

En la página principal se muestra la siguiente información:
* **Estado del dispositivo**: supervisa el estado del dispositivo y notifica los errores graves.
* **Información de Windows**: muestra el nombre de HoloLens y la versión de Windows instalada actualmente.
* La sección **Preferencias** contiene las siguientes configuraciones:
   * **IPD**: establece la distancia interpupilar (IPD), que es la distancia, en milímetros, entre el centro de las pupilas del usuario cuando mira al frente. La configuración surte efecto inmediatamente. El valor predeterminado se calculó automáticamente al configurar el dispositivo.
   * **Nombre del dispositivo**: asigna un nombre a HoloLens. Debe reiniciar el dispositivo después de cambiar este valor para que surta efecto. Después de hacer clic en **Guardar**, se te preguntará en un cuadro de diálogo si quieres reiniciar el dispositivo inmediatamente o más tarde.
   * **Configuración de suspensión**: establece el período de tiempo de espera antes de que el dispositivo entre en el modo de suspensión cuando está conectado y cuando funciona con batería.

### <a name="3d-view"></a>Vista 3D

![Página Vista 3D de Portal de dispositivos en Microsoft HoloLens](images/using-windows-portal-img-05.png)<br>
*Página Vista 3D de Portal de dispositivos en Microsoft HoloLens*

Usa la página Vista 3D para ver cómo HoloLens interpreta el entorno. Navega por la vista con el mouse:
* Girar: haz clic con el botón izquierdo + mouse;
* Panorámica: haz clic con el botón derecho + mouse;
* Zoom: desplazamiento del mouse.
* **Opciones de seguimiento**
   * activa el seguimiento visual continuo marcando la opción **Force visual tracking** (Forzar seguimiento visual). 
   * **Pausa** detiene el seguimiento visual.
* **Opciones de vista**: establece las opciones en la vista 3D:
  * **Seguimiento**: indica si el seguimiento visual está activo.
  * **Show floor** (Mostrar suelo): muestra un plano de la planta a cuadros.
  * **Show frustum** (Mostrar tronco): muestra el tronco de la vista.
  * **Show stabilization plane** (Mostrar plano de estabilización): muestra el plano que HoloLens usa para estabilizar el movimiento.
  * **Show mesh** (Mostrar malla): muestra la malla de asignación espacial que representa el entorno.
  * **Show spatial anchors** (Mostrar delimitadores espaciales): muestra los delimitadores espaciales para la aplicación activa. Haga clic en el botón Actualizar para obtener y actualizar los delimitadores.
  * **Mostrar detalles**: muestra las posiciones de la mano, los cuaterniones de rotación de la cabeza y el vector de origen del dispositivo cuando cambian en tiempo real.
  * **Botón Pantalla completa**: muestra la vista 3D en modo de pantalla completa. Presiona ESC para salir de la vista de pantalla completa.
* **Reconstrucción de superficie**: haga clic o pulse **Actualizar** para mostrar la última malla de asignación espacial del dispositivo. Un recorrido completo puede tardar un tiempo en completarse, unos segundos. La malla no se actualiza automáticamente en la vista 3D y debe hacer clic manualmente en **Actualizar** para obtener la malla más reciente del dispositivo. Haga clic en **Guardar** para guardar la malla de asignación espacial actual como un archivo .obj en el equipo.
* **Spatial Anchors**: haga clic en Actualizar para mostrar o actualizar los delimitadores espaciales de la aplicación activa.

### <a name="map-manager"></a>Map Manager (Administrador de mapas)

Map Manager (Administrador de mapas) le permite compartir mapas entre dispositivos, que se pueden usar para configurar experiencias compartidas para clientes de entretenimiento basados en la ubicación. La herramienta le permite importar y exportar asignaciones y anclajes del sistema.  

Para acceder a Map Manager (Administrador de mapas), inicie sesión en el Portal de dispositivos y seleccione **Mixed Reality -> Map Manager (Administrador de mapas)** : 

![Página Map Manager (Administrador de mapas) del Portal de dispositivos Windows](images/using-windows-portal-img-06.png)
*Página Map Manager (Administrador de mapas) del Portal de dispositivos Windows en Microsoft HoloLens*

#### <a name="exporting-and-importing-maps"></a>Exportación e importación de mapas

Para exportar mapas, haga clic en **Export System Map & Anchors** (Exportar mapas y anclajes del sistema). Es posible que este proceso tarde unos minutos en completarse, por lo que tenga en cuenta que deberá esperar entre 30 y 60 segundos mientras se exporta la asignación. Una vez que haya finalizado, el archivo se descargará en el explorador.  

Para importar mapas y anclajes, haga clic en **Upload a map file** (Cargar un archivo de mapa) y **Upload an anchor file** (Cargar un archivo de anclaje) respectivamente y seleccione un mapa o un archivo de anclaje que ya haya exportado. El archivo de mapa o anclaje cargado puede provenir de cualquier otro dispositivo HoloLens. 

> [!NOTE]
> En HoloLens, también es posible importar y exportar la base de datos de asignación espacial. Sin embargo, esta opción no funciona en dispositivos que no sean de HoloLens.  


### <a name="mixed-reality-capture"></a>Captura de realidad mixta

![Página Captura de realidad mixta de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-07.png)<br>
*Página Captura de realidad mixta de Portal de dispositivos Windows en Microsoft HoloLens*

> [IMPORTANTE] Los valores configurados en el Portal de dispositivos se aplican a todo el dispositivo y se conservan luego de reiniciar. Toda configuración que se modifique en el Portal de dispositivos se aplicará a las capturas y aplicaciones de realidad mixta. Dado que esta configuración es persistente, se recomienda usar el Portal de dispositivos solo durante el desarrollo, y no en dispositivos implementados.

Usa la página Mixed Reality Capture (Captura de realidad mixta) para guardar flujos multimedia desde HoloLens.
* **Configuración de captura**: controla las secuencias multimedia que se capturan comprobando la siguiente configuración:
  * **Hologramas**: captura el contenido holográfico en la secuencia de vídeo. Los hologramas se representan en mono y no estéreo.
  * **PV camera** (Cámara de vídeo o fotos): captura la secuencia de vídeo de la cámara de vídeo o fotos.
  * **Mic Audio** (Audio de micrófono): captura el audio de la matriz del micrófono.
  * **App Audio** (Audio de la aplicación): captura el audio de la aplicación que está en ejecución actualmente.
  * **Render from Camera** (Representar desde la cámara): alinea la captura para que provenga de la perspectiva de la cámara de vídeo o fotos, en caso de que [la aplicación en ejecución la admita](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (solo HoloLens 2).
  * **Live preview quality** (Calidad de vista previa dinámica): selecciona la resolución de pantalla, la velocidad de fotogramas y la velocidad de streaming de la vista previa dinámica.
* **Configuración de audio** (solo HoloLens 2):
  * **Audio Media Category** (Categoría de medio de audio): seleccione la categoría que se usa al procesar el micrófono. **Predeterminada**: incluye parte del entorno, mientras que **Comunicaciones** aplica la cancelación del ruido de fondo.
  * **App Audio Gain** (Ganancia de audio de aplicación): la ganancia aplicada al volumen de audio de la aplicación.
  * **Mic Audio Gain** (Ganancia de audio de micrófono): la ganancia aplicada al volumen de audio del micrófono.
* **Photo and Video Settings** (Configuración de foto y vídeo) (HoloLens 2, versión 2004 o posterior):
  * **Capture Profile** (Perfil de captura): seleccione el perfil usado al tomar fotos y grabar vídeos. El perfil determina qué resoluciones y velocidades de fotogramas están disponibles.
  * **Resolución de foto**: la resolución con la que se tomará la foto.
  * **Video Resolution and Frame-rate** (Resolución de vídeo y velocidad de fotogramas): la resolución y la velocidad de fotogramas con las que se grabará el vídeo.
  * **Video Stabilization Buffer** (Búfer de estabilización de vídeo): tamaño de búfer usado al grabar un vídeo. Cuanto mayor sea el valor, mejor puede compensar los movimientos rápidos.
* Haga clic o pulse el botón **Vista previa dinámica** para mostrar el flujo de captura. **Stop live preview** (Detener la vista previa dinámica) detiene la secuencia de captura.
* Haga clic o pulse **Grabar** para comenzar a grabar el flujo de realidad mixta mediante la configuración especificada. **Detener grabación** finaliza la grabación y la guarda.
* Haga clic o pulse **Tomar foto** para tomar una imagen estática del flujo de captura.
* Haga clic o pulse en **Restaurar configuración predeterminada** para restaurar la configuración predeterminada de las opciones de audio, foto y vídeo.
* **Vídeos y fotos**: muestra una lista de las capturas de vídeo y fotos tomadas en el dispositivo.

Todas las opciones de esta página se aplican a las capturas tomadas con el Portal de dispositivos Windows. Igualmente, algunos también se aplican a la MRC del sistema, incluido el menú Inicio, los botones de hardware, los comandos de voz globales, Miracast y los registros de MRC personalizados.

|  Valor  |  Se aplica a MRC del sistema  |  Se aplica a grabadoras de MRC personalizadas |
|----------|----------|----------|
|  Hologramas  |  No  |  No |
|  Cámara de foto y vídeo  |  No  |  No |
|  Mic Audio (Audio de micrófono)  |  No  |  No |
|  App Audio (Audio de la aplicación)  |  No  |  No |
|  Render from Camera (Representar desde la cámara)  |  Sí    |  Sí (se puede invalidar) |
|  Live preview quality (Calidad de vista previa dinámica)  |  No  |  No |
|  Audio Media Category (Categoría de medio de audio)  |  Sí  |  No |
|  App Audio Gain (Ganancia de audio de aplicación)  |  Sí  |  Sí (se puede invalidar) |
|  Mic Audio Gain (Ganancia de audio de micrófono)  |  Sí  |  Sí (se puede invalidar) |
|  Capture Profile (Perfil de captura)  |  Sí  |  No |
|  Resolución de foto  |  Sí  |  No |
|  Video Resolution and Frame-rate (Resolución de vídeo y velocidad de fotogramas)  |  Sí  |  No |
|  Video Stabilization Buffer (Búfer de estabilización de vídeo)  |  Sí  |  Sí (se puede invalidar) |

> [!NOTE]
> Hay [limitaciones de MRC simultáneas](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * Si una aplicación intenta acceder a la cámara de vídeo o fotos mientras Portal de dispositivos Windows graba un vídeo, la grabación de vídeo se detendrá.
>   * HoloLens 2 no dejará de grabar vídeo si la aplicación accede a la cámara de vídeo o fotos con el modo SharedReadOnly.
> * Si una aplicación usa activamente la cámara de vídeo o fotos, Portal de dispositivos de Windows puede tomar una foto o grabar un vídeo.
> * Streaming en directo:
>   * HoloLens (1.ª generación) impide que una aplicación acceda a la cámara de vídeo o fotos durante el streaming en vivo desde Portal de dispositivos Windows.
>   * HoloLens (1.ª generación) no podrá hacer streaming en vivo si una aplicación está usando activamente la cámara de vídeo o fotos.
>   * HoloLens 2 detiene automáticamente el streaming en vivo cuando una aplicación intenta acceder a la cámara de vídeo o fotos en modo ExclusiveControl.
>   * HoloLens 2 es capaz de iniciar el streaming en vivo mientras una aplicación usa activamente la cámara de vídeo o fotos.

### <a name="performance-tracing"></a>Seguimiento de rendimiento

![Página Seguimiento de rendimiento de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-08.png)<br>
*Página Seguimiento de rendimiento de Portal de dispositivos Windows en Microsoft HoloLens*

Captura los seguimientos de [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) de HoloLens.
* **Perfiles disponibles**: seleccione el perfil de WPR en la lista desplegable y pulse o haga clic en **Inicio** para iniciar el seguimiento.
* **Perfiles personalizados**: haga clic o pulse **Examinar** para elegir un perfil de WPR del equipo. Haga clic o pulse **Cargar e iniciar** para iniciar el seguimiento.

Para detener el seguimiento, haga clic en el vínculo de detención. Permanece en esta página hasta que el archivo de seguimiento se haya terminado de descargar.

Los archivos ETL se pueden abrir para realizar análisis en [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)).

### <a name="processes"></a>Procesos

![Página Procesos de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-09.png)<br>
*Página Procesos de Portal de dispositivos Windows en Microsoft HoloLens*

Muestra detalles acerca de los procesos que se ejecutan actualmente. Esto incluye aplicaciones y procesos del sistema.

### <a name="system-performance"></a>Rendimiento del sistema

![Página Rendimiento del sistema de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-10.png)<br>
*Página Rendimiento del sistema de Portal de dispositivos Windows en Microsoft HoloLens*

Muestra gráficos en tiempo real de la información de diagnóstico del sistema, como el uso de energía, la velocidad de fotogramas y la carga de la CPU.

Estas son las métricas disponibles:
* **SoC power** (Energía SoC): uso de energía instantánea "system-on-chip", con una media superior a un minuto.
* **Energía del sistema**: uso de energía instantánea del sistema, con una media superior a un minuto.
* **Velocidad de fotogramas**: fotogramas por segundo, VBlank (intervalos verticales) perdidos por segundo y VBlank perdidos consecutivos
* **GPU**: uso del motor de la GPU; porcentaje del total disponible.
* **CPU**: porcentaje del total disponible
* **E/S**: lecturas y escrituras
* **Red**: envíos y recepciones
* **Memoria:** total, en uso, confirmada, paginada y no paginada

### <a name="apps"></a>Aplicaciones

![Página Aplicaciones de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-11.png)<br>
*Página Aplicaciones de Portal de dispositivos Windows en Microsoft HoloLens*

Administra las aplicaciones que están instaladas en HoloLens.
* **Aplicaciones instaladas**: quita e inicia aplicaciones.
* **Aplicaciones en ejecución**: enumera las aplicaciones que se ejecutan actualmente.
* **Instalar aplicación**: selecciona paquetes de la aplicación para la instalación desde una carpeta en el equipo o red.
* **Dependencia**: agrega las dependencias de la aplicación que va a instalar.
* **Implementar**: implementa la aplicación seleccionada y las dependencias en HoloLens.

### <a name="app-crash-dumps"></a>Página de volcados de memoria de la aplicación

![Página de volcados de memoria de aplicación de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-12.png)<br>
*Página de volcados de memoria de aplicación de Portal de dispositivos Windows en Microsoft HoloLens*

En esta página puedes recopilar los volcados de memoria de las aplicaciones transferidas localmente. Marca la casilla **Crash Dumps Enabled** (Volcados de memoria habilitados) de cada aplicación de la que quieras recopilar volcados de memoria. Vuelve a esta página para recopilar los volcados de memoria. Los archivos de volcado se pueden [abrir en Visual Studio para su depuración](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files).

### <a name="file-explorer"></a>Explorador de archivos

![Página Explorador de archivos de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-13.png)<br>
*Página Explorador de archivos de Portal de dispositivos Windows en Microsoft HoloLens*

Usa el explorador de archivos para examinar, cargar y descargar archivos. Puedes trabajar con archivos en la carpeta Documentos, en la carpeta Imágenes y en las carpetas de almacenamiento local para las aplicaciones que implementaste desde Visual Studio o desde Portal de dispositivos.

### <a name="kiosk-mode"></a>Pantalla completa

>[!NOTE]
>La opción de pantalla completa solo está disponible con [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features).

![Página de pantalla completa en el Portal de dispositivos Windows de Microsoft HoloLens](images/using-windows-portal-img-14.png)

Consulta el artículo [Configurar HoloLens en pantalla completa](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) en Windows IT Pro Center para obtener instrucciones actualizadas sobre cómo habilitar la pantalla completa a través de Portal de dispositivos Windows.

### <a name="logging"></a>Registro

![Página Registro de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-15.png)<br>
*Página Registro de Portal de dispositivos Windows en Microsoft HoloLens*

Administra el seguimiento de eventos para Windows (ETW) en tiempo real en HoloLens.

Marca **Hide providers** (Ocultar proveedores) para mostrar solamente la lista **Eventos**.
* **Registered providers** (Proveedores registrados): selecciona el proveedor ETW y el nivel de seguimiento. El nivel de seguimiento es uno de estos valores:
   1. Terminación o salida anómala
   2. Errores graves
   3. Warnings
   4. Advertencias sin errores

Haga clic o pulse **Activar** para iniciar el seguimiento. El proveedor se agrega a la lista desplegable de **Proveedores habilitados**.
* **Proveedores personalizados**: selecciona el proveedor ETW personalizado y el nivel de seguimiento. Identifica el proveedor por su GUID. No incluyas corchetes en el GUID.
* **Proveedores habilitados**: enumera los proveedores habilitados. Selecciona un proveedor de la lista desplegable y haz clic o pulsa en **Desactivar** para detener el seguimiento. Haz clic o pulsa en **Detener todo** para suspender todos los seguimientos.
* **Providers history** (Historial de proveedores): muestra los proveedores ETW habilitados durante la sesión actual. Haz clic o pulsa en **Activar** para activar un proveedor deshabilitado. Haz clic o pulsa en **Borrar** para borrar el historial.
* **Eventos**: enumera los eventos ETW de los proveedores seleccionados en formato de tabla. Esta tabla se actualiza en tiempo real. Debajo de la tabla, haz clic en el botón **Borrar** para eliminar todos los eventos ETW de la tabla. Esta acción no deshabilita ningún proveedor. Puedes hacer clic en **Guardar en archivo** para exportar los eventos ETW recopilados actualmente en un archivo CSV de forma local.
* **Filtros**: permite filtrar los eventos ETW recopilados por id., palabra clave, nivel, nombre de proveedor, nombre de la tarea o texto. Puedes combinar varios criterios:
   1. En el caso de los criterios que se aplican a la misma propiedad, se muestran los eventos que pueden cumplir cualquiera de ellos.
   2. En el caso de los criterios que se aplican a una propiedad diferente, los eventos deben cumplir todos los criterios.

Por ejemplo, puedes especificar los criterios *(el nombre de tarea contiene "Foo&quot; o &quot;Bar") y (el texto contiene "error" o "advertencia")*

### <a name="simulation"></a>Simulation

![Página Simulación de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-16.png)<br>
*Página Simulación de Portal de dispositivos Windows en Microsoft HoloLens*

Te permite grabar y reproducir datos de entrada para las pruebas.
* **Capture room** (Espacio de captura): se usa para descargar un archivo de espacio simulado que contiene la malla espacial de asignación del entorno del usuario. Asigne un nombre al espacio y, a continuación, haga clic en **Capturar** para guardar los datos como un archivo .xef en el equipo. Puedes cargar este archivo de espacio en el emulador HoloLens.
* **Grabación**: marca los flujos que quieres grabar, asigna un nombre a la grabación y haz clic o pulsa en **Grabar** para iniciar la grabación. Realice acciones con HoloLens y, a continuación, haga clic en **Detener** para guardar los datos como un archivo .xef en el equipo. Este archivo se puede cargar en el dispositivo o emulador HoloLens.
  >[!NOTE]
  >La característica Grabación solo está disponible actualmente en la HoloLens de 1.ª generación. La grabación aún no se admite en HoloLens 2, pero se admite la reproducción de las grabaciones existentes.
* **Reproducción**: haz clic o pulsa en **Cargar grabación** para seleccionar un archivo .xef desde tu equipo y enviar los datos a HoloLens.
* **Modo de control**: selecciona **Valor predeterminado** o **Simulación** en la lista desplegable y pulsa o haz clic en el botón **Establecer** para seleccionar el modo en HoloLens. Si eliges "Simulación", se deshabilitan los sensores reales de HoloLens y se usan los datos simulados cargados en su lugar. Si cambia a "Simulación", HoloLens no responderá al usuario real hasta que vuelva al "Valor predeterminado".

### <a name="networking"></a>Funciones de red

![Página Redes de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-17.png)<br>
*Página Redes de Portal de dispositivos Windows en Microsoft HoloLens*

Administra conexiones Wi-Fi en HoloLens.
* **WiFi adapters** (Adaptadores WiFi): Selecciona un adaptador Wi-Fi y un perfil mediante los controles desplegables. Pulsa o haz clic en **Conectar** para usar el adaptador seleccionado.
* **Redes disponibles**: enumera las redes Wi-Fi a las que se puede conectar HoloLens. Haz clic en o pulsa en **Actualizar** para actualizar la lista.
* **Configuración IP**: muestra la dirección IP y otros detalles de la conexión de red.

### <a name="virtual-input"></a>Entrada virtual

![Página Entrada virtual de Portal de dispositivos Windows en Microsoft HoloLens](images/using-windows-portal-img-18.png)<br>
*Página Entrada virtual de Portal de dispositivos Windows en Microsoft HoloLens*

Envía la entrada de teclado desde la máquina remota a HoloLens.

Haz clic o pulsa en la región de debajo de **Teclado virtual** para habilitar el envío de pulsaciones de teclas a HoloLens. Escribe en el cuadro de texto **Texto de entrada** y haz clic o pulsa en **Enviar** para enviar las pulsaciones de teclas a la aplicación activa.

## <a name="device-portal-rest-apis"></a>API de REST del Portal de dispositivos

Todo lo que contiene el Portal de dispositivos se basa en las [API de REST](device-portal-api-reference.md) que puede usar de forma opcional para obtener acceso a los datos y controlar el dispositivo mediante programación.

## <a name="troubleshooting"></a>Solución de problemas

### <a name="how-to-fix-the-its-lonely-here-message"></a>Cómo corregir el mensaje "It's lonely here" (No hay nada aquí)

> [!NOTE]
> El cambio de HoloLens 2 a HoloLens (primera generación) puede provocar que las páginas se muestren vacías si se han usado en HoloLens 2 antes que en HoloLens (primera generación).

![Mensaje It's lonely here (No hay nada aquí) de la página Portal de dispositivos](images/using-windows-portal-img-19.png)

1. Seleccione **Reset layout** (Restablecer diseño) en el menú superior izquierdo:

![Selección de Reset layout (Restablecer diseño) en el menú del Portal de dispositivos](images/using-windows-portal-img-20.png)

2. Haga clic en **Reset Layout** (Restablecer diseño) en el encabezado **Reset workspace** (Restablecer área de trabajo). La página del portal se actualizará automáticamente y mostrará el contenido.

![Selección de Reset layout (Restablecer diseño) desde la página Reset workspace (Restablecer área de trabajo)](images/using-windows-portal-img-21.png)
