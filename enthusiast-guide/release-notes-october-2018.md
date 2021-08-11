---
title: Notas de la versión (octubre de 2018)
description: Manténgase al día con las notas HoloLens y Windows Mixed Reality de la versión de Windows 10 actualización de octubre de 2018/RS5.
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: notas de la versión, versión, windows 10, compilación, rs5, sistema operativo
ms.openlocfilehash: e046025ff4952a6e8779545374ec59d9f49c907ad3174b188474ae040cb28ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219980"
---
# <a name="release-notes---october-2018"></a>Notas de la versión (octubre de 2018)

El **[Actualización de octubre de 2018 de Windows 10](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (también conocido como RS5) incluye nuevas características para los cascos envolventes HoloLens y Windows Mixed Reality envolventes conectados a los equipos. 

Para actualizar a la versión más reciente en HoloLens o PC (para cascos envolventes (VR) de **Windows Mixed Reality),** abra la aplicación  Configuración, vaya a Update & Security (Actualizar **& Security)** y, a continuación, seleccione el botón Buscar actualizaciones. En un Windows 10, también puede instalar manualmente el Actualización de octubre de 2018 de Windows 10 mediante la herramienta de Windows [de creación de medios](https://www.microsoft.com/software-download/windows10).

**Versión más reciente de Desktop:** Actualización de octubre de 2018 de Windows 10 (**10.0.17763.107**)<br>
**Versión más reciente HoloLens:** Actualización de octubre de 2018 de Windows 10 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuevas características de Windows Mixed Reality cascos envolventes

La Actualización de octubre de 2018 de Windows 10 incluye muchas mejoras para usar cascos envolventes (VR) de Windows Mixed Reality con el equipo de escritorio.

### <a name="for-everyone"></a>Para todos los usuarios

* **Mixed Reality flashlight:** abra un portal en el mundo real para encontrar el teclado, ver a alguien cercano o echar un vistazo a su entorno sin quitar el casco. Puede activar Mixed Reality Flashlight desde el menú Inicio, presionando Windows + Agarrar en el controlador de movimiento, o bien decir "Con la luz de encendido y apagado". Apunte el controlador en la dirección de lo que desea ver, como usar una linterna en la sombra.

    ![Mixed Reality de luz](images/mr-flashlight.png)

* **Aplicaciones nuevas y formas de iniciar contenido en el ambiente principal**
    * Si usas Windows Mixed Reality para [SteamVR,](./using-steamvr-with-windows-mixed-reality.md)los títulos de SteamVR ahora se muestran en el menú Inicio y los iniciadores de aplicaciones para cada uno se pueden colocar en el ambiente principal.
    
        ![Iniciadores de aplicaciones de SteamVR](images/steamvr-launchers.png)
        
    * Nueva *aplicación 360 Videos* para detectar una selección periódica de vídeos de 360 grados.
    * Nueva *aplicación WebVR Showcase* para detectar una selección periódica de experiencias de WebVR.
    * La primera vez Windows Mixed Reality clientes escribirán el Casa sobre el acantilado y lo encontrarán rellenado previamente con los iniciadores de aplicaciones 3D para algunas de nuestras aplicaciones y juegos inmersivos favoritos de la Microsoft Store.
    * Microsoft Edge ventanas ahora incluyen un *botón Compartir.*
* **Menú** Acciones rápidas: desde una aplicación de realidad mixta inmersiva, puede presionar el botón Windows para acceder a un nuevo menú de acciones rápidas, con fácil acceso al menú *de SteamVR,* la captura de fotos y *vídeos,* la linterna y el *hogar.*
* **Compatibilidad con equipos portátiles:** Windows Mixed Reality cascos envolventes (VR) se ejecutan en equipos portátiles sin necesidad de un emulador de pantalla una vez completada la configuración.
* Nuevas características de **audio:** ahora puede reflejar el audio desde una experiencia de Windows Mixed Reality tanto  en el conector de audio (o auriculares) del casco como en un dispositivo de audio conectado al equipo (como altavoces externos). También hemos agregado un indicador visual para el nivel de volumen en la pantalla del casco.
* **Otras mejoras**
    * Portal de realidad mixta actualizaciones se entregan ahora a través del Microsoft Store, lo que permite actualizaciones más rápidas entre las versiones Windows principales. Tenga en cuenta que esto solo se aplica a la aplicación de escritorio y a Windows Mixed Reality experiencia de casco todavía se actualiza con el sistema operativo. 
    * Cuando los cascos se suspenden, Windows Mixed Reality aplicaciones se suspenden en lugar de finalizar (hasta Portal de realidad mixta cierre).
    
### <a name="for-developers"></a>Para desarrolladores

* Seguimiento de código **[QR:](/windows/mixed-reality/develop/platform-capabilities-and-apis/qr-code-tracking)** habilite el seguimiento de código QR en la aplicación de realidad mixta, lo que permite Windows Mixed Reality los cascos envolventes (VR) buscar códigos QR y notificarlos a las aplicaciones interesadas.
* **Compatibilidad con DRM** de hardware para aplicaciones inmersivas: los desarrolladores ahora pueden solicitar texturas de búfer de reserva protegidas por hardware si son compatibles con el hardware de presentación, lo que permite a las aplicaciones usar contenido protegido por hardware de orígenes como PlayReady.
* **[Integración](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** de la interfaz de usuario de captura de realidad mixta en aplicaciones inmersivas: los desarrolladores pueden integrar la captura de realidad mixta en sus aplicaciones mediante la interfaz de usuario de captura de cámara de Windows integrada con solo unas pocas líneas de [código.](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)

## <a name="new-features-for-hololens"></a>Nuevas características para HoloLens

La Actualización de octubre de 2018 de Windows 10 está disponible públicamente para todos los HoloLens clientes e incluye una serie de mejoras, como:

### <a name="for-everyone"></a>Para todos los usuarios

*  Menú Acciones rápidas: desde una aplicación de realidad mixta inmersiva, puede presionar el botón Windows para acceder a un nuevo menú de acciones rápidas, con fácil acceso a Iniciar grabación de *vídeo,* Tomar *imágenes,* *Mixed Reality* *Inicio, Cambiar volumen* *y Conectar*.
* **Iniciar o detener** la captura de vídeo desde el menú Inicio o acciones rápidas: si inicia la captura de vídeo desde el menú de acciones rápidas o menú Inicio, podrá detener la grabación desde el mismo lugar. (No olvide que siempre puede hacerlo con comandos de voz).
* Project a un dispositivo habilitado para **Miracast:** Project el contenido de HoloLens a un dispositivo Surface o un televisor o monitor cercanos si se usa una pantalla o adaptador habilitado para Miracast.
* **Nuevas notificaciones:** vea y responda a las notificaciones en HoloLens, igual que en un equipo.  
* **Superposiciones útiles** en aplicaciones de realidad mixta inmersivas: ahora verá superposiciones como el teclado, los diálogos, el selector de archivos, etc. al usar aplicaciones de realidad mixta inmersivas.
* **Indicador visual para el** cambio de volumen: al usar los botones de subir o bajar volumen en el HoloLens verá un indicador visual del nivel de volumen en el casco.
* **Nuevos objetos visuales para el arranque del** dispositivo: se agregó un indicador de carga durante el proceso de arranque para proporcionar comentarios visuales que el sistema está cargando.
* **Uso compartido cercano:** la Windows uso compartido cercano le permite compartir una captura con un dispositivo Windows cercano.  
* **Compartir desde Microsoft Edge:** Microsoft Edge ahora incluye un *botón* Compartir. 

### <a name="for-developers"></a>Para desarrolladores

* **[Integración](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** de la interfaz de usuario de captura de realidad mixta en aplicaciones inmersivas: los desarrolladores pueden integrar la captura de realidad mixta en sus aplicaciones mediante la interfaz de usuario de captura de cámara de Windows integrada con solo unas pocas líneas de [código.](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)

### <a name="for-commercial-customers"></a>Para clientes comerciales

* **Habilitar el aprovisionamiento posterior a la** instalación: ahora puede aplicar un paquete de aprovisionamiento en tiempo de ejecución en cualquier momento mediante Configuración.
* Acceso asignado con **grupos Azure AD:** ahora puede usar grupos de Azure AD para la configuración de un acceso asignado Windows para configurar la pantalla completa de una o varias aplicaciones.
* **Cambio de perfil de** inicio de sesión de PIN desde la pantalla de inicio de sesión: el inicio de sesión de PIN ahora está disponible para "Otro usuario" en la pantalla de inicio de sesión. 
* **Leer la información de hardware del dispositivo** a través de MDM: los administradores de TI pueden ver y realizar un seguimiento HoloLens por número de serie del dispositivo en su consola MDM.
* **Establecer HoloLens dispositivo mediante MDM (cambiar nombre):** los administradores de TI pueden ver y cambiar el nombre de HoloLens dispositivos en su consola MDM.

### <a name="for-international-customers"></a>Para clientes internacionales

Ahora puede usar HoloLens interfaz de usuario localizada para chino simplificado o japonés, incluidos el teclado Pinyin localizado, el dictado, el texto a voz (TTS) y los comandos de voz.

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado duro para ofrecer una experiencia Windows Mixed Reality excelente, pero todavía estamos haciendo un seguimiento de algunos problemas conocidos. Si encuentra a otros usuarios, [envíenos sus comentarios.](/windows/mixed-reality/give-us-feedback)

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Después de la actualización
Puede observar los siguientes problemas al usar el Actualización de octubre de 2018 de Windows 10 en su HoloLens:
* **Las aplicaciones pueden** acabar en un bucle de inicio de sesión cuando se inician desde una notificación: algunas aplicaciones que requieren inicio de sesión pueden acabar en un bucle de inicio de sesión sin fin cuando se inician desde una notificación. Por ejemplo, esto puede ocurrir después de instalar la aplicación microsoft Portal de empresa desde el Microsoft Store iniciarla desde la notificación de instalación completa.
*  La página de inicio de sesión de la aplicación se puede completar con una página en blanco: en algunos casos, cuando se muestra un mensaje de inicio de sesión a través de la aplicación, al finalizar la página de inicio de sesión no se cierra y, en su lugar, se muestra una página en blanco (negra). Puede cerrar la página en blanco o moverla para descubrir la aplicación debajo. Por ejemplo, esto puede ocurrir al iniciar sesión durante la inscripción de MDM desde Configuración aplicación. 

## <a name="provide-feedback-and-report-issues"></a>Proporcionar comentarios e informar de problemas

Use la aplicación Centro de opiniones en el equipo HoloLens o [Windows 10 para](/windows/mixed-reality/give-us-feedback) proporcionar comentarios e informar de los problemas. El Centro de opiniones garantiza que se incluye toda la información de diagnóstico necesaria para ayudar a nuestros ingenieros a depurar y resolver rápidamente el problema.

>[!NOTE]
>Asegúrese de aceptar el mensaje que le pregunta si desea Centro de opiniones acceder a la carpeta Documentos (seleccione **Sí** cuando se le solicite).

## <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión: abril de 2018](release-notes-april-2018.md)
* [Notas de la versión (octubre de 2017)](release-notes-october-2017.md)
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte también
* [Compatibilidad con cascos envolventes (vínculo externo)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (vínculo externo)](https://support.microsoft.com/products/hololens)
* [Instalación de las herramientas](/windows/mixed-reality/develop/install-the-tools)
* [Envíenos sus comentarios.](/windows/mixed-reality/give-us-feedback)