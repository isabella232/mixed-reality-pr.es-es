---
title: 'Notas de la versión: abril de 2018'
description: Manténgase al día de las HoloLens y Windows Mixed Reality de la versión de Windows 10 actualización de abril de 2018/RS4.
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: notas de la versión, versión, windows 10, compilación, rs4, sistema operativo
ms.openlocfilehash: 27f80d659c63362191a80eeae973111ca342090901c243772868d1a7c11e24d3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202437"
---
# <a name="release-notes---april-2018"></a>Notas de la versión: abril de 2018

La Windows 10 de abril de **[2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (también conocida como RS4) incluye nuevas características para cascos envolventes de HoloLens y Windows Mixed Reality conectados a equipos. 

Para actualizar a la versión más reciente para cualquier tipo de dispositivo, abra la aplicación **Configuración,** vaya a **Actualizar & Security** y, a continuación, seleccione el botón **Buscar** actualizaciones. En un Windows 10, también puede instalar manualmente la actualización de Windows 10 de abril de 2018 mediante la Windows [de creación de medios](https://www.microsoft.com/software-download/windows10).

**Versión más reciente de Desktop:** Windows 10 actualización de abril de 2018 (**10.0.17134.1**)<br>
**Versión más reciente de HoloLens:** Windows 10 actualización de abril de 2018 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Un mensaje de Alex Hawái e información general sobre las nuevas características de realidad mixta en la actualización de Windows 10 de abril de 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuevas características de Windows Mixed Reality cascos envolventes

La Windows 10 de abril de 2018 incluye muchas mejoras para usar cascos envolventes de Windows Mixed Reality (VR) con el equipo de escritorio, como: 

* **Nuevos entornos para la ambiente principal:** elija entre el Casa sobre el acantilado y el nuevo  entorno de Skyloft seleccionando Lugares en el menú Inicio. También hemos agregado una [característica experimental que](/windows/mixed-reality/design/add-custom-home-environments) le permitirá usar entornos personalizados que ha creado.
* **Acceso rápido** a la captura de realidad mixta: tome fotos de realidad mixta mediante un controlador de movimiento entre entornos y aplicaciones, pero no capturará contenido protegido con DRM. Mantenga presionado Windows botón y, a continuación, pulse el desencadenador. .
* **Nuevas opciones para iniciar y ajustar el** tamaño del contenido: las aplicaciones ahora se colocan automáticamente delante de usted al iniciarlas desde el menú Inicio. Ahora también puede cambiar el tamaño de las aplicaciones 2D arrastrando los bordes y las esquinas de la ventana.
* Saltar fácilmente al contenido con el comando de voz **"teleportar":** teleporte rápidamente delante del contenido de la página principal de Windows Mixed Reality, para lo que debe mirar el contenido y decir "teleportar".
* **[Iniciadores de aplicaciones 3D animados](/windows/mixed-reality/distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home#animation-guidelines) [y objetos 3D decorados](/windows/mixed-reality/distribute/enable-placement-of-3d-models-in-the-home) para el ambiente principal**. Ahora puede agregar animación a los iniciadores de aplicaciones 3D y permitir que los usuarios coloquen modelos 3D decorados desde una página web o una aplicación 2D en el Windows Mixed Reality principal.
* Las mejoras en Windows Mixed Reality para **[SteamVR](/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)** - Windows Mixed Reality para SteamVR no tienen "acceso anticipado" con nuevas actualizaciones, incluidos los comentarios hápticos al usar controladores de movimiento, el rendimiento y la confiabilidad mejorados, y mejoras en la apariencia de los controladores de movimiento en SteamVR.
* **Otras mejoras:** la configuración de rendimiento automática actualizada proporciona una experiencia más optimizada (puede [invalidar manualmente](#visual-quality) esta configuración). El programa de instalación ahora proporciona información más detallada sobre los problemas comunes de compatibilidad con controladores USB 3.0 y tarjetas gráficas.

## <a name="new-features-for-hololens"></a>Nuevas características para HoloLens

La Windows 10 de abril de 2018 ha llegado para todos los HoloLens clientes. Esta actualización está llena de mejoras introducidas desde la última versión principal de HoloLens software en [agosto de 2016.](release-notes-august-2016.md)

### <a name="for-everyone"></a>Para todos los usuarios

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Colocación automática de contenido 2D y 3D en el inicio</td><td>Un iniciador de aplicaciones 2D o una aplicación para UWP 2D coloca automáticamente en el mundo un tamaño y una distancia óptimos cuando se inicia en lugar de requerir que el usuario la coloque. Si una <a href="/windows/mixed-reality/design/app-views">aplicación inmersiva</a> usa un iniciador de aplicaciones 2D en lugar de un iniciador de aplicaciones <a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3D,</a>la aplicación inmersiva se iniciará automáticamente desde el iniciador de aplicaciones 2D igual que en RS1.<br><br>Un iniciador de aplicaciones 3D del menú Inicio también coloca automáticamente en el mundo. En lugar de iniciar automáticamente la aplicación, los usuarios pueden hacer clic en el iniciador para iniciar la aplicación inmersiva. El contenido 3D abierto desde Hologramas aplicación y desde Edge también se coloca automáticamente en el mundo.</td><td>Al abrir una aplicación desde el menú Inicio, no se le pedirá que la coloque en el mundo.<br><br>Si la ubicación del iniciador de aplicaciones<a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">2D o 3D</a> no es óptima, puede moverlas fácilmente mediante las nuevas manipulaciones de aplicaciones fluidas que se describen a continuación. También puede cambiar la posición del contenido 3D o iniciador de aplicaciones 2D si dice "Mover esto..." y, a continuación, usa la mirada para cambiar la posición del contenido.</td>
  </tr>
  <tr>
    <td>Manipulación fluida de aplicaciones</td><td>Mover, cambiar el tamaño y girar contenido 2D y 3D sin tener que entrar en el modo "Ajustar".</td><td>Para mover una aplicación 2D para UWP o un iniciador de aplicaciones 2D, basta con mirar la barra de la aplicación y, a continuación, usar el gesto de pulsar + mantener presionada la tecla + arrastrar. Para mover contenido 3D, puede desplazarse por cualquier lugar del objeto y, a continuación, pulsar + mantener presionado y arrastrar.<br><br>Para cambiar el tamaño del contenido 2D, mire su esquina. El cursor de mirada se convertirá en un cursor de cambio de tamaño y, a continuación, puede pulsar + mantener presionado + arrastrar para cambiar el tamaño. También puede hacer que el contenido 2D sea más alto o más ancho si observa sus bordes y arrastra.<br><br>Para cambiar el tamaño del contenido 3D, eleva las dos manos al marco de gestos, con los dedos hacia arriba en la posición lista. Verá que el cursor se convierte en un estado con dos manos pequeñas. Pulse y mantenga presionado el gesto con ambas manos. Al acercar o separar las manos, cambie el tamaño del objeto. Al mover las manos hacia delante y hacia atrás en relación entre sí, se girará el objeto. También puede cambiar el tamaño o girar el contenido 2D de esta manera.</td>
  </tr>
  <tr>
    <td>Cambio de tamaño horizontal de la aplicación 2D con reflujo</td><td>Haga que una aplicación 2D para UWP sea más amplia en relación de aspecto para ver más contenido de la aplicación. Por ejemplo, hacer que la aplicación Mail se muestre lo suficientemente ancha como para mostrar el panel de vista previa.</td><td>Basta con mirar el borde izquierdo o derecho de la aplicación para UWP 2D para ver el cursor de cambio de tamaño y, a continuación, use el gesto de pulsar + mantener presionado + arrastrar para cambiar el tamaño.</td>
  </tr>
  <tr>
    <td>Compatibilidad con comandos de voz expandido</td><td>Puede hacer más sencillamente con su voz.</td><td>Pruebe estos comandos de voz:<ul><li>"Ir a Inicio": abre el menú Inicio o sale de una <a href="/windows/mixed-reality/design/app-views">aplicación inmersiva.</a></li><li>"Mover esto...": permite mover un objeto.</li></ul></td>
  </tr>
  <tr>
    <td>Aplicaciones Hologramas y Fotos actualizadas</td><td>Se Hologramas aplicación con nuevos hologramas. Se ha Fotos aplicación.</td><td>Observará un aspecto actualizado de las aplicaciones Hologramas y Fotos personalizadas. La Hologramas aplicación incluye varios nuevos Hologramas y un creador de etiquetas para facilitar la creación de texto.</td>
  </tr>
  <tr>
    <td>Captura de realidad mixta mejorada</td><td>Vídeo de inicio y finalización de MRC de acceso directo de hardware.</td><td>Mantenga el volumen hacia arriba y abajo durante 3 segundos para empezar a grabar el vídeo de MRC. Pulse ambos de nuevo o use el gesto de Bloom para finalizar.</td>
  </tr>
  <tr>
    <td>Espacios consolidados</td><td>Simplifique la administración del espacio para hologramas en un solo espacio.</td><td>HoloLens el espacio automáticamente y ya no requiere que administre o seleccione espacios. Si tiene problemas con los hologramas que le rodea, puede ir a Configuración > System > Hologramas > Remove nearby holograms (Quitar <b>hologramas cercanos).</b> Si es necesario, también puede seleccionar <b>Quitar todos los hologramas.</b></td>
  </tr>
  <tr>
    <td>Mejora de la reproducción de audio</td><td>Ahora puede escuchar HoloLens mejor en entornos ruidosos y experimentar un sonido más similar al de las aplicaciones porque el sonido está oculto por las paredes reales detectadas por el dispositivo.</td><td>No tiene que hacer nada para disfrutar del sonido espacial mejorado.</td>
  </tr>
  <tr>
    <td>Explorador de archivos</td><td>Mueva y elimine archivos desde dentro HoloLens.</td><td>Puede usar la aplicación <b>Explorador de archivos</b> para mover y eliminar archivos desde dentro HoloLens.<br><br><b>Sugerencia:</b> Si no ve ningún archivo, el filtro "Reciente" puede estar activo (el icono de reloj se resalta en el panel izquierdo). Para corregirlo, seleccione este icono de documento de dispositivo en el panel izquierdo (debajo del icono de reloj) o abra el menú </b> y seleccione <b>Este dispositivo.</b>
</td>
  </tr>
  <tr>
    <td>Compatibilidad con MTP (Protocolo de transferencia de medios)</td><td>Permite que el equipo de escritorio acceda a las bibliotecas (fotos, vídeos, documentos) HoloLens para facilitar la transferencia.</td><td>De forma similar a otros dispositivos móviles, conecte <b></b> el HoloLens al equipo para que Explorador de archivos pueda acceder a las bibliotecas de HoloLens (fotos, vídeos, documentos) para facilitar la transferencia.<br><br><b>Sugerencias:</b><ul><li>Si no ve ningún archivo, asegúrese de iniciar sesión en el HoloLens para habilitar el acceso a los datos.</li><li>Desde <b>Explorador de archivos</b> en el equipo, puede <b></b> seleccionar Propiedades del dispositivo para ver Windows versión del sistema operativo holográfico (versión de firmware) y el número de serie del dispositivo.</li></ul><b>Problema conocido:</b> No se HoloLens <b>cambiar Explorador de archivos</b> nombre a través de Explorador de archivos en el equipo.</td>
  </tr>
  <tr>
    <td>Compatibilidad de red de Captive Portal durante la instalación</td><td>Ahora puede configurar su cuenta HoloLens una red de invitados en hoteles, centros de conferencias, tiendas minoristas o empresas que usan captive portal.</td><td>Durante la instalación, seleccione la red, active conectarse automáticamente y escriba la información de red como se le solicite.</td>
  </tr>
  <tr>
    <td>Sincronización de fotos y vídeos a través OneDrive aplicación</td><td>Las fotos y vídeos de HoloLens ahora se sincronizarán a través de la aplicación OneDrive desde el Microsoft Store en lugar de la Fotos aplicación.</td><td>Para configurarlo, descargue e inicie la aplicación OneDrive desde la Tienda. En la primera ejecución, se le pedirá que cargue automáticamente las fotos en OneDrive. Si no aparece este mensaje, puede encontrar la opción en la configuración de la aplicación.</td>
  </tr>
</table>

### <a name="for-developers"></a>Para desarrolladores

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Mejoras en la asignación espacial</td><td>Mejoras de calidad, simplificación y rendimiento.</td><td>La malla de asignación espacial aparecerá más limpia: se requieren menos triángulos para representar el mismo nivel de detalle. Es posible que observe cambios en la densidad del triángulo en la escena.</td>
  </tr>
  <tr>
    <td>Selección automática del punto de enfoque basado en el búfer de profundidad</td><td>El envío de un búfer de profundidad Windows permite a HoloLens seleccionar automáticamente un punto de enfoque para optimizar la estabilidad del holograma.</td><td>En Unity, vaya a la pestaña Edit > Project Configuración > Player > Universal Windows Platform (Editar > Project Configuración > <b>Player > Universal Windows Platform) > XR Configuración</b>, expanda el elemento del SDK de <b>Windows Mixed Reality</b> y active Enable Depth <b>Buffer Sharing</b>(Habilitar el uso compartido del búfer de profundidad). Se comprobará automáticamente si hay nuevos proyectos.<br><br>En el caso de las aplicaciones DirectX, asegúrese de llamar al método <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a> en <b>HolographicRenderingParameters</b> en cada fotograma para proporcionar el búfer de profundidad a Windows.
</td>
  </tr>
  <tr>
    <td>Modos de reproducción holográfica</td><td>Ahora puede deshabilitar la reproducción posicional en HoloLens mejorar la estabilidad del holograma del contenido rígidamente bloqueado por el cuerpo, como vídeo de 360 grados.</td><td>En Unity, establezca <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a> en <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a> cuando todo el contenido de la vista esté bloqueado de forma rígida por el cuerpo.<br><br>En el caso de las aplicaciones de DirectX, establezca <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters.ReprojectionMode</a> en <a href="/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a> cuando todo el contenido de la vista esté bloqueado de forma rígida por el cuerpo.</td>
  </tr>
  <tr>
    <td>API de adaptación de aplicaciones</td><td>Windows Las API saben más sobre dónde se ejecuta la aplicación, como si la pantalla del dispositivo es transparente (HoloLens) o opaca (casco envolvente) y si la vista 2D de una aplicación para UWP aparece en el shell holográfico.</td><td>Unity había expuesto manualmente <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a> de una manera que funcionaba incluso antes de esta compilación.<br><br>En el caso de las aplicaciones de DirectX, ahora puede acceder a las API existentes, <a href="/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">como HolographicDisplay.GetDefault(). IsOpaque</a> y <a href="/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a> en HoloLens también.
</td>
  </tr>
  <tr>
      <td>Modo de investigación</td><td>Permite a los desarrolladores acceder a sensores de HoloLens al crear aplicaciones académicas e industriales para probar nuevas ideas en los campos de la visión informática y la robótica, incluidos:<ul><li>Las cuatro cámaras de seguimiento del entorno</li><li>Dos versiones de los datos de la cámara de asignación de profundidad</li><li>Dos versiones de un flujo de reflectividad de IR</li></ul></td><td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/research-mode">Documentación del modo de investigación</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Aplicaciones de ejemplo del modo de investigación</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Para clientes comerciales

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Uso de varias Azure Active Directory de usuario en un único dispositivo</td><td>Comparta una HoloLens con varios Azure AD usuarios, cada uno con su propia configuración de usuario y datos de usuario en el dispositivo.</td><td><a href="/hololens/hololens-multiple-users">Centro de Pro de IT: Compartir HoloLens con varias personas</a></td>
  </tr>
  <tr>
    <td>Cambiar Wi-Fi red al iniciar sesión</td><td>Cambie Wi-Fi red antes del inicio de sesión para permitir que otro usuario inicie sesión con su cuenta de usuario de Azure AD por primera vez, lo que permite a los usuarios compartir dispositivos en varias ubicaciones y sitios de trabajo.</td><td>En la pantalla de inicio de sesión, puede usar el icono de red situado debajo del campo de contraseña para conectarse a una red. Esto resulta útil cuando es la primera vez que inicia sesión en un dispositivo.</td>
  </tr>
  <tr>
    <td>Inscripción unificada</td><td>Ahora es fácil para un usuario de HoloLens que configura el dispositivo con una cuenta personal de Microsoft agregar una cuenta de trabajo (Azure AD) y unir el dispositivo a su servidor MDM.</td><td>Inicie sesión con una cuenta Azure AD y la inscripción se realiza automáticamente.</td>
  </tr>
  <tr>
    <td>Sincronización de correo sin inscripción de MDM</td><td>Compatibilidad con Exchange de correo de Active Sync (EAS) sin necesidad de inscripción de MDM.</td><td>Ahora puede sincronizar el correo electrónico sin inscribirse en MDM. Puede configurar el dispositivo con una cuenta Microsoft, descargar e instalar la aplicación Mail y agregar una cuenta de correo electrónico de trabajo directamente.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>para profesionales de TI

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Nuevo nombre del sistema Windows Holographic for Business "Windows Holographic for Business"</td><td>Borre los nombres de edición para reducir la confusión en la aplicación de licencia de actualización de edición cuando las características de Commercial Suite están habilitadas en HoloLens.</td><td>Puede ver qué edición de Windows Holographic está en el dispositivo en Configuración > <b>System > About</b>. "Windows Holographic for Business" aparecerá si se ha aplicado una actualización de edición para habilitar las características de Commercial Suite. Obtenga información sobre <a href="/hololens/hololens-upgrade-enterprise">cómo desbloquear Windows Holographic for Business características</a>.</td>
  </tr>
  <tr>
  <td>Windows Diseñador de configuración (WCD)</td><td>Cree y edite paquetes de aprovisionamiento para configurar HoloLens a través de la aplicación WCD actualizada. Asistente HoloLens para actualización de edición, OOBE configurable, región o zona horaria, CSP de Azure AD, red y desarrolladores. Editor avanzado filtrado para HoloLens opciones admitidas, incluidos LOSPS de acceso asignado y administración de cuentas.</td><td><a href="/hololens/hololens-provisioning">Centro de Pro de IT: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
    <td>Configuración configurable (OOBE)</td><td>Oculte la calibración, el entrenamiento de gestos y miradas y Wi-Fi pantallas de configuración durante la instalación.</td><td><a href="/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">Centro de Pro de IT: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
    <td>Compatibilidad Azure AD token de carga masiva</td><td>Registre previamente el dispositivo en Azure AD de directorio para un flujo de instalación de usuario más rápido.</td><td><a href="/hololens/hololens-provisioning">Centro de Pro de IT: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup CSP</td><td>Implemente el perfil para configurar HoloLens en modo de desarrollador. Útil para dispositivos de desarrollo y demostración.</td><td><a href="/hololens/hololens-provisioning">Centro de Pro de IT: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
  <td>AccountManagement CSP</td><td>Comparta un HoloLens dispositivo y quite los datos de usuario después de los umbrales de cierre de sesión o de inactividad/almacenamiento para su uso temporal. Admite Azure AD cuentas.</td><td><a href="/hololens/hololens-provisioning">Centro de Pro de IT: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
  <td>Acceso asignado</td><td>Windows acceso asignado a los trabajadores o demostraciones de primera línea. Bloqueo de una o varias aplicaciones. No es necesario que el desarrollador desbloquee.</td><td><a href="/hololens/hololens-kiosk">Centro de Pro de IT: Configuración de HoloLens pantalla completa</a></td>
  </tr>
  <tr>
  <td>Acceso de invitado para dispositivos de quiosco</td><td>Windows acceso asignado con una cuenta de invitado sin contraseña para demostraciones. Bloqueo de una o varias aplicaciones. No es necesario que el desarrollador desbloquee.</td><td><a href="/hololens/hololens-kiosk#guest">Centro de Pro de IT: Configuración de HoloLens pantalla completa</a></td>
  </tr>
  <tr>
    <td>Configuración de diagnósticos (OOBE)</td><td>Obtenga registros de diagnóstico de HoloLens para que pueda solucionar Azure AD errores de inicio de sesión (antes de que Centro de opiniones esté disponible para el usuario cuyo inicio de sesión ha generado un error).</td><td>Cuando se produce un error en la instalación o el inicio de sesión, elija la <b>nueva opción Recopilar información</b> para obtener registros de diagnóstico para solucionar problemas.</td>
  </tr>
  <tr>
    <td>Expiración indefinida de la contraseña de la cuenta local</td><td>Quite la interrupción del restablecimiento del dispositivo cuando expire la contraseña de la cuenta local.</td><td>Al aprovisionar una cuenta local, ya no es necesario cambiar la contraseña cada 42 días en <b>Configuración</b>, ya que la contraseña de la cuenta ya no expira.</td>
  </tr>
  <tr>
    <td>Estado y detalles de sincronización de MDM</td><td>Funcionalidad Windows estándar para comprender el estado y los detalles de sincronización de MDM desde dentro HoloLens.</td><td>Puede comprobar el estado de sincronización de MDM de un dispositivo <b>en Configuración > Accounts > Access Work or School > Info</b>. En la <b> sección Estado de sincronización de dispositivos, puede iniciar una sincronización, ver las áreas administradas por MDM y crear y exportar un <b> informe de diagnóstico avanzado.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado duro para ofrecer una excelente experiencia Windows Mixed Reality, pero seguimos haciendo un seguimiento de algunos problemas conocidos. Si encuentra a otros usuarios, [envíenos sus comentarios.](/windows/mixed-reality/give-us-feedback)

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Después de la actualización

Es posible que observe los siguientes problemas después de actualizar de RS1 a RS4 en su HoloLens:
* **Restablecimiento de los** pines: las aplicaciones 3x3 ancladas a la menú Inicio se restablecerán a los valores predeterminados después de la actualización. 
* **Restablecimiento de aplicaciones y hologramas colocados:** las aplicaciones colocadas en su mundo se quitarán después de la actualización y tendrán que volver a colocarse en todo el espacio. 
* **Centro de opiniones** iniciar inmediatamente: inmediatamente después de la actualización, pasarán unos minutos antes de poder iniciar algunas aplicaciones de bandeja de entrada, como Centro de opiniones, mientras se actualizan ellos mismos. 
* Es necesario volver a sincronizar los certificados de Wi-Fi **corporativos:** estamos investigando un problema que requiere que el HoloLens esté conectado a una red diferente para que los certificados corporativos se vuelvan a sincronizar con el dispositivo antes de poder volver a conectarse a las redes corporativas mediante certificados. 
* La reproducción de vídeo **H.265 HEVC** no funciona: las aplicaciones que intentan reproducir vídeos H.265 recibirán un mensaje de error. La solución alternativa consiste [en acceder al Windows Portal de dispositivos,](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)seleccionar **Aplicaciones en** la barra de navegación izquierda y **quitar** la aplicación HEVC. A continuación, instale el [Extensión de vídeo HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) más reciente desde el Microsoft Store. Estamos investigando el problema. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Para desarrolladores: actualización de HoloLens aplicaciones para dispositivos que se ejecutan Windows 10 actualización de abril de 2018

Junto con una excelente lista de nuevas [características,](#new-features-for-hololens)la actualización de abril de 2018 (RS4) de Windows 10 para HoloLens aplica algunos comportamientos de código que las versiones anteriores no:
* Solicitudes de permiso para usar recursos confidenciales **(cámara, micrófono,** entre otros): RS4 en HoloLens aplicará las solicitudes de permiso para las aplicaciones que pretenden acceder a recursos confidenciales, como la cámara o el micrófono. RS1 en HoloLens no fuerce estos mensajes, por lo que, si la aplicación asume el acceso inmediato a estos recursos, puede bloquearse en RS4 (incluso si el usuario concede permiso al recurso solicitado). Lea el artículo [sobre declaraciones de funcionalidad de aplicaciones para UWP pertinentes](/windows/uwp/packaging/app-capability-declarations) para obtener más información.
* **Las llamadas** a aplicaciones fuera de su propio RS4 en HoloLens exigirán el uso adecuado de la clase [ *tem.Selector*](/uwp/api/Windows.System.Launcher) deWindows.Syspara iniciar otra aplicación desde la suya propia. Por ejemplo, hemos visto problemas con las aplicaciones que llaman *aWindows.System.Selector. LaunchUriForResultsAsync* desde un subproceso que no es de ASTA(UI). Esto se realizaría correctamente en RS1 HoloLens, pero RS4 requiere que la llamada se ejecute en el subproceso de la interfaz de usuario.

### <a name="windows-mixed-reality-on-desktop"></a>Windows Mixed Reality en el escritorio

#### <a name="visual-quality"></a>Calidad visual

* Si observa después de la actualización de abril de 2018 de Windows 10 que los gráficos son más desenfocados que antes, o que el campo de vista parece más pequeño en el casco, es posible que se haya cambiado la configuración de rendimiento automático para mantener una velocidad de fotogramas suficiente en una tarjeta gráfica menos eficaz (como Nvidia 1050). Para invalidarlo manualmente (si lo elige), vaya a Configuración > **Mixed reality > Headset display > Experience options > Change** and changing "Automatic" (Automático) a "90 Hz". También puede intentar cambiar **la calidad visual** (en la misma Configuración) a "Alta".

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality configuración

* Al configurar el Windows con un casco conectado, es posible que el monitor del equipo se quepa en blanco. Desconecte los cascos para habilitar la salida en el monitor del equipo para completar Windows configuración.
* Si no tiene cascos conectados, puede que se pierdan sugerencias la primera vez que visite la Windows Mixed Reality hogar.
* Otros Bluetooth dispositivos pueden causar interferencias con los controladores de movimiento. Si los controladores de movimiento tienen problemas de conexión, emparejamiento y seguimiento, asegúrese de que la radio Bluetooth (si es un dongle externo) está conectada a una ubicación sin estructura y no inmediatamente junto a otro Bluetooth dongle. Pruebe también a encender otros Bluetooth periféricos durante Windows Mixed Reality sesiones para ver si ayuda.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Juegos y aplicaciones de la Microsoft Store

* Algunos juegos de uso intensivo gráfico, como Forza Ques 7, pueden causar problemas de rendimiento en equipos con menos capacidad cuando se reproducen dentro de Windows Mixed Reality.

#### <a name="audio"></a>Audio

* Si Cortana está habilitado en el equipo host antes de usar el casco de Windows Mixed Reality, es posible que pierda la simulación de sonido espacial aplicada a las aplicaciones que coloque alrededor del Windows Mixed Reality principal. 
   * La alternativa es habilitar "Windows Sonic para auriculares" en todos los dispositivos de audio conectados al equipo, incluso en el dispositivo de audio conectado al casco:
      1. Haga clic con el botón izquierdo en el icono del altavoz en la barra de tareas del escritorio y seleccione en la lista de dispositivos de audio.
      2. Haga clic con el botón derecho en el icono del hablante en la barra de tareas del escritorio y seleccione "Windows Sonic para auriculares" en el menú "Configuración del hablante".
      3. Repita estos pasos para todos los dispositivos de audio (puntos de conexión).
   * Otra opción es desactivar "Let Cortana respond to Hey Cortana" en Configuración Cortana en el escritorio antes de iniciar  >   Windows Mixed Reality.
* Cuando otro dispositivo USB multimedia (por ejemplo, una cámara web) comparte el mismo concentrador USB (ya sea externo o dentro del equipo) con el casco Windows Mixed Reality, en raras ocasiones, los auriculares o el conector de audio del casco pueden tener un sonido de timbre o ningún audio. Puede corregir esto mediante el casco en un puerto USB que no comparta el mismo centro que el otro dispositivo, o desconectar o deshabilitar el otro dispositivo multimedia USB.
* En raras ocasiones, el concentrador USB del equipo host no puede proporcionar suficiente energía al casco de Windows Mixed Reality y es posible que observe una ráfaga de ruido de los auriculares conectados al casco.

#### <a name="holograms"></a>Hologramas

* Si ha colocado un gran número de hologramas en su Windows Mixed Reality, algunos pueden desaparecer y volver a aparecer a medida que mira. Para evitar esto, quite algunos de los hologramas de esa área del Windows Mixed Reality inicio.

#### <a name="motion-controllers"></a>Controladores de movimiento

* Si la entrada no se enruta al casco, el controlador de movimiento desaparecerá brevemente cuando se mantiene junto al límite de la sala. Al presionar Win+Y para asegurarse de que hay un banner azul en el monitor de escritorio, esto se resolverá. 
* En ocasiones, al hacer clic en una página web Microsoft Edge, el contenido se acercará en lugar de hacer clic.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicación de escritorio en la Windows Mixed Reality inicio

* Herramienta Recortes no funciona en la aplicación de escritorio.
* La aplicación de escritorio no conserva la configuración al volver a iniciar.
* Si usa la versión preliminar Portal de realidad mixta escritorio, al abrir la aplicación de escritorio en Windows Mixed Reality inicio, es posible que observe el efecto de reflejo infinito. 
* La ejecución de la aplicación de escritorio puede causar problemas de rendimiento en equipos Windows Mixed Reality Ultra. no se recomienda.  
* La aplicación de escritorio puede iniciarse automáticamente porque una ventana invisible del escritorio tiene el foco. 
* El símbolo del sistema de control de cuentas de usuario de escritorio hará que el casco se muestre en negro hasta que se complete el aviso.

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows Mixed Reality para SteamVR

* Es posible que deba iniciar Portal de realidad mixta después de actualizar para asegurarse de que las actualizaciones de software necesarias para la actualización de Windows 10 de abril de 2018 se hayan completado antes de iniciar SteamVR. 
* Debe tener una versión reciente de Windows Mixed Reality para que SteamVR siga siendo compatible con la actualización Windows 10 de abril de 2018. Asegúrese de que las actualizaciones automáticas están activadas Windows Mixed Reality para SteamVR, que se encuentra en la sección "Software" de la biblioteca en Steam.  

#### <a name="other-issues"></a>Otros problemas

>[!IMPORTANT]
>Faltaba una versión anterior de la actualización de Windows 10 de abril de 2018 que se insertaba en Insiders (versión 17134.5) y faltaba un fragmento de software necesario para ejecutar Windows Mixed Reality. Se recomienda evitar esta versión si se usa Windows Mixed Reality. 

Hemos identificado una regresión del rendimiento al usar Surface Book 2 en la versión inicial de esta actualización (10.0.17134.1) que estamos trabajando para corregir en una próxima revisión de actualización. Se recomienda esperar hasta que se haya corregido antes de actualizar manualmente o esperar a que la actualización se revierte con normalidad.

## <a name="provide-feedback-and-report-issues"></a>Proporcionar comentarios e informar de problemas

Use la [Centro de opiniones en el equipo HoloLens](/windows/mixed-reality/give-us-feedback) o Windows 10 para proporcionar comentarios e informar de los problemas. El Centro de opiniones garantiza que se incluye toda la información de diagnóstico necesaria para ayudar a nuestros ingenieros a depurar y resolver rápidamente el problema.

>[!NOTE]
>Asegúrese de aceptar el mensaje que le pregunta si desea Centro de opiniones acceder a la carpeta Documentos (seleccione **Sí** cuando se le solicite).

## <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión (octubre de 2017)](release-notes-october-2017.md)
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte también
* [Compatibilidad con cascos envolventes (vínculo externo)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (vínculo externo)](https://support.microsoft.com/products/hololens)
* [Instalación de las herramientas](/windows/mixed-reality/develop/install-the-tools)
* [Envíenos sus comentarios.](/windows/mixed-reality/give-us-feedback)