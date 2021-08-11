---
title: Notas de la versión (mayo de 2016)
description: Manténgase al día en las notas de la HoloLens de lanzamiento de la Windows holographic may 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de la versión, sistema operativo, características, compilación, plataforma
ms.openlocfilehash: fe93890300d46dc12041f198a772671c79c97af0d6be2fc959937932a1d108c3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202542"
---
# <a name="release-notes---may-2016"></a>Notas de la versión (mayo de 2016)

El HoloLens se compromete a proporcionarle las actualizaciones de características más recientes y las correcciones principales a través del Windows Programa Insider. Gracias a todas sus sugerencias, agradecemos sus comentarios. Continúe para [enviarnos comentarios a](/windows/mixed-reality/give-us-feedback) través de los Centro de opiniones, los foros para desarrolladores [y](https://forums.hololens.com) Twitter a [través @HoloLens de ](https://twitter.com/hololens).

**Versión de lanzamiento:** Windows holographic de mayo de 2016 (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

Para actualizar a la versión  actual, abra la aplicación Configuración, vaya a *Actualizar & Security* y, a continuación, seleccione el *botón Buscar* actualizaciones.

## <a name="new-features"></a>Nuevas características

* Ahora puede ejecutar hasta tres aplicaciones en la vista **2D** simultáneamente, lo que permite casos de uso infinitos para tareas múltiples en HoloLens. Haga que el nuevo Centro de opiniones con la lista de misiones abierta mientras explora las nuevas características de este vuelo.

  ![HoloLens ejecutar tres aplicaciones al mismo tiempo](images/img-3625-400px.jpg)<br>
  Ejecutar hasta tres aplicaciones en la vista 2D simultáneamente

* Hemos agregado nuevos comandos **de voz:**
   * Pruebe a mirar un holograma y girarlo; para ello, diga "cara a cara".
   * Para cambiar su tamaño, diga "más grande" o "más pequeño".
   * Mueva una aplicación con el mensaje "Hey Cortana, move app name here" (Hola, mueva *el nombre de la* aplicación aquí).
* Hemos hecho que el **desarrollo en HoloLens más fácil.** Ahora puede examinar, cargar y descargar archivos a través del [Windows Portal de dispositivos](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal). Puede acceder a la carpeta Documentos, a la carpeta Imágenes y al almacenamiento local para cualquier aplicación que cargue o implemente en paralelo a través de Visual Studio.
* El **emulador ahora admite el inicio** de sesión con una cuenta Microsoft como lo haría en un HoloLens real, que puede habilitar desde el menú Herramientas adicionales ">>".
* **Las aplicaciones 2D ahora ocultan la barra de la aplicación** y el cursor al ver la pantalla completa del vídeo para evitar distracciones. La experiencia de ver vídeos será aún más divertida en HoloLens.
* También puede **anclar fotos sin la barra de aplicaciones** de su mundo.

  ![La barra de la aplicación se puede ocultar para aplicaciones 2D como fotos](images/img-3626-400px.jpg)<br>
  La barra de la aplicación se puede ocultar para las aplicaciones con una vista 2D, como Fotos

* **El selector de** archivos funciona de la forma esperada en HoloLens.
* Se ha **actualizado el explorador Edge** para asignar la experiencia de usuario unificada con el escritorio y el teléfono. Hemos habilitado varias instancias del explorador, personalizadas HoloLens nueva página de pestañas, un vistazo a pestañas y se abren en nuevas ventanas, junto con mejoras de rendimiento & power &.
* **Groove Música** aplicación está ahora en HoloLens. Visite la tienda para descargarla e intente reproducirla en segundo plano.
* Puede personalizar fácilmente cómo se organizan las aplicaciones en su mundo. Pruebe **a girar los hologramas en** modo de ajuste simplemente haciendo clic y arrastrando el círculo en los wireframes verticales centrales. Es posible que observe que los hologramas tienen rectángulos delimitadores ajustados más **estrictos** para garantizar una interacción maximizada. También puede cambiar el tamaño de todas las aplicaciones planas verticalmente (excepto Fotos y hologramas).

  ![Hologramas se pueden girar después de colocarlos en el mundo](images/img-3627-400px.jpg)<br>
  Girar hologramas después de colocarlos en su mundo

* Hemos realizado varias mejoras **de entrada** en este vuelo. Puede conectar un mouse de Bluetooth a HoloLens. El clicker se ha ajustado para permitir cambiar el tamaño & mover hologramas con un clicker. El teclado también se ejecuta mejor que nunca.
* Ahora puede tomar imágenes **de realidad mixta** presionando el volumen hacia arriba y hacia abajo simultáneamente. También puede compartir las fotos capturadas de realidad mixta & vídeos en Facebook, Twitter y YouTube.
* La longitud máxima de grabación **de los** vídeos de realidad mixta se ha aumentado a cinco minutos.
* **Fotos aplicación ahora** transmite vídeos desde OneDrive en lugar de tener que descargar todo el vídeo antes de la reproducción.
* Hemos mejorado el modo en que los **hologramas estarán justo donde los dejó.** También se le presentará la opción de volver a conectarse a Wi-Fi probar de nuevo si HoloLens no puede detectar dónde están.
* El teclado tiene un **diseño mejorado** para escribir la dirección de correo electrónico con claves que le permiten escribir los dominios de correo electrónico más populares con un solo clic.
* Registro **de aplicaciones y** **detección automática más** rápidos de la zona horaria durante la OOBE, lo que le ofrece la mejor experiencia de usuario.
* **Storage sentido permite** ver el espacio en disco restante y usado por el sistema y las aplicaciones en la aplicación de configuración.
* Hemos convergedo Aplicación de comentarios e Inside Hub en una sola aplicación **Centro de opiniones**  , que es la herramienta de acceso para proporcionarnos comentarios sobre las características que le encantan, cuáles necesitan mejoras y cuáles sin las que podría hacer. Al unirse a la Programa Insider, puede mantenerse al día con las noticias  más recientes de **Insider,** las compilaciones de **tasas** y los comentarios de Centro de opiniones.
* También hemos publicado [una versión HoloLens Emulator](/windows/mixed-reality/develop/install-the-tools) compilación.
* Los vídeos de realidad mixta ahora se ven mejor debido a la **estabilización automática de vídeo.**

## <a name="major-fixes"></a>Correcciones principales

Se han corregido problemas con los espacios de hologramas en los que los espacios serían lentos o se detectarían incorrectamente. Se ha corregido un problema de apagado que podía seguir intentando iniciar el shell durante el apagado.

Se ha corregido un problema
* que bloquea la capacidad de reanudar una aplicación XAML.
* donde un bloqueo dejaría una pantalla negra y algunas líneas irregulares.
* el desplazamiento a veces se acoplía en la dirección incorrecta al usar algunas aplicaciones.
* los LED de alimentación podrían indicar un estado desactivado cuando el dispositivo todavía estaba encendido.
* La conexión Wi-Fi podría desactivarse después de reanudarse desde el modo de espera.
* El proveedor de identidades de Xbox ofrece la configuración gamertag y, a continuación, se queda bloqueado en un bucle.
* El shell se bloquea ocasionalmente al seleccionar un archivo descargado en el selector OneDrive archivo.
* Al presionar y mantener presionado un vínculo, a veces se abre una nueva pestaña rota y se abre un menú contextual.
* donde el portal de dispositivos Windows no permitía ajustes de IPD de 50 a 80

Se han corregido problemas con Fotos donde
* En ocasiones, una imagen se mostraría girada porque se omitía la propiedad de orientación EXIF.
* podría bloquearse durante el inicio en el Fotos.
* Los vídeos se reiniciarían después de pausar en lugar de continuar desde donde se pausaron por última vez.
* Se podría impedir la reproducción de un vídeo compartido si se compartió durante la reproducción.
* Captura de realidad mixta grabaciones comenzarían con 0,5-1 segundo de fuente de solo audio.
* El botón Sincronizar desaparece durante la Sincronización de OneDrive.

Se han corregido problemas con la configuración en la que
* se necesitaba una actualización cuando cambia el entorno.
* "Entrar" en el teclado no se comportaría como hacer clic en Siguiente en algunos cuadros de diálogo.
* era difícil saber cuándo no se pudo emparejar el clicker.
* podría dejar de responder con la conexión y desconexión de Wi-Fi.

Se han corregido problemas con Cortana
* podría quedarse bloqueado mostrando la interfaz de usuario de escucha.
* al preguntar "Hey Cortana, what can I say" (Hola, qué puedo decir) desde una aplicación en modo exclusivo, se atascaría si respondía quizás más bien sí/no a la solicitud para salir de la aplicación.
* la Cortana la interfaz de usuario de escucha no se reanuda correctamente si Cortana a suspensión y, a continuación, se reanuda.
* las consultas "¿A qué red estoy conectado?" y el "Am I connected?" (¿Estoy conectado?) podría producir un error cuando el primer perfil de red vuelve sin conectividad.
* la interfaz de usuario se congeló en "Listening" pero al salir de una aplicación empezaría inmediatamente a realizar el reconocimiento de voz de nuevo.
* donde cerrar sesión en Cortana aplicación no le permitirá volver a iniciar sesión en ella hasta un reinicio.
* no se iniciaría cuando Captura de realidad mixta la interfaz de usuario estaba activa.

Se han corregido problemas con Visual Studio donde
* la depuración de tareas en segundo plano no funcionaba.
* El análisis de fotogramas en el depurador de gráficos no funcionaba.
* el HoloLens Emulator no aparece en la lista desplegable de Visual Studio a menos que targetPlatformVersion del proyecto se haya establecido en 10240.

## <a name="changes-from-previous-release"></a>Cambios de la versión anterior
* El Cortana comando **Hey Cortana, reiniciar el dispositivo** no funciona. El usuario puede decir **Hey Cortana, restart** o **Hey Cortana, restart the device**.
* Se ha quitado el modo de quiosco del producto.

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte también
* [Problemas conocidos de HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Instalación de las herramientas](/windows/mixed-reality/develop/install-the-tools)
* [Shell](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)
* [Actualización de aplicaciones para UWP bidimensionales para la realidad mixta](/windows/mixed-reality/develop/porting-apps/building-2d-apps)
* [Accesorios de hardware](/windows/mixed-reality/discover/hardware-accessories)
* [Captura de realidad mixta](/windows/mixed-reality/mixed-reality-capture)
* [Entrada de voz](/windows/mixed-reality/design/voice-input)
* [Envío de una aplicación a Windows Store](/windows/mixed-reality/distribute/submitting-an-app-to-the-microsoft-store)
* [Uso del emulador de HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)