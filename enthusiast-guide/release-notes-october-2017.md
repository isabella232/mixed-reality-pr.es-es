---
title: Notas de la versión (octubre de 2017)
description: Manténgase al día de las notas Windows Mixed Reality de la versión de Windows 10 Fall Creators Update (octubre de 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: notas de la versión, versión, windows 10, compilación, rs3, sistema operativo
ms.openlocfilehash: 09a33e1bc4a13c75e4c8a0ee250c7b67eb8e68e21220840037085e727acfb1f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190599"
---
# <a name="release-notes---october-2017"></a>Notas de la versión (octubre de 2017)

Le damos la bienvenida a Windows Mixed Reality. En **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** versión anterior se presenta compatibilidad con nuevos [Windows Mixed Reality cascos envolventes y](/windows/mixed-reality/discover/immersive-headset-hardware-details) controladores de [movimiento.](/windows/mixed-reality/design/motion-controllers) Ahora puede explorar nuevos mundos, jugar a juegos de realidad virtual y experimentar el entretenimiento inmersivo cuando se conecta a [un equipo Windows Mixed Reality compatible con](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).

La versión Windows Mixed Reality cascos y controladores de movimiento es la continuación de un esfuerzo masivo del equipo y un paso importante para la plataforma [Windows Mixed Reality,](/windows/mixed-reality/discover/mixed-reality)incluido [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details). Aunque HoloLens no recibe una actualización con el Windows 10 Fall Creators Update, el trabajo HoloLens no se ha detenido. Tendremos una gran cantidad de aprendizajes e información que aplicar a partir de nuestro trabajo reciente en Windows Mixed Reality como un todo. De hecho, Windows Mixed Reality cascos envolventes y controladores de movimiento representan también un excelente punto de entrada al desarrollo de HoloLens, ya que las mismas API, herramientas y conceptos se aplican a ambos.

Para actualizar a la versión más reciente de cada dispositivo, abra la aplicación **Configuración,** vaya a **Actualizar & Security** y, a continuación, seleccione el botón **Buscar** actualizaciones. En un Windows 10, también puede instalar manualmente el Windows 10 Fall Creators Update mediante la herramienta de Windows [de creación de medios](https://www.microsoft.com/software-download/windows10).

 **Versión más reciente de Desktop:** Windows 10 Desktop de octubre de 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 Versión más reciente **de HoloLens:** [Windows 10 Holographic agosto de 2016](release-notes-august-2016.md) (**10.0.14393.0**, Windows 10 Anniversary Update)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Presentación de Windows Mixed Reality

El Windows 10 Fall Creators Update incorpora oficialmente compatibilidad con Windows Mixed Reality cascos y controladores de movimiento, y Windows 10 el primer sistema operativo espacial del mundo. Estos son los aspectos destacados:
* **[Variedad de cascos:](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** Windows Mixed Reality permite a los asociados ofrecer diferentes tipos de cascos a partir de 399 USD agrupados con controladores de movimiento.
* **[Controladores de](/windows/mixed-reality/design/motion-controllers)** movimiento: Windows Mixed Reality de movimiento se emparejan de forma inalámbrica con el equipo a través de Bluetooth y cuentan con un seguimiento de seis grados de libertad, una gran cantidad de métodos de entrada e IMUs.
* **[Configuración y portabilidad sencillas:](./recommended-adapters-for-windows-mixed-reality-capable-pcs.md)** configure y empezar a trabajar en menos de 10 minutos. Los cascos envolventes usan el seguimiento interno para realizar un seguimiento del movimiento y los controladores de movimiento, con seis grados de libertad. No se requieren cámaras externas ni marcadores de foco.
* **[Compatibilidad con](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)** una gama más amplia de equipos: Windows Mixed Reality permitirá que más personas experimenten la realidad virtual de escritorio que nunca, con compatibilidad con tarjetas gráficas y equipos integrados seleccionados a partir de 499 USD.
* **[Windows Mixed Reality](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** home: el primer sistema operativo espacial del mundo proporciona un entorno familiar para tareas múltiples con aplicaciones 2D, el inicio de juegos y aplicaciones vr y la colocación de hologramas decorados.
* **[Sorprendentes](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** juegos y aplicaciones de REALIDAD virtual en Microsoft Store: desde el entretenimiento inmersivo como Hulu VR y 360 vídeos hasta juegos de epopeya como SUPERHOT VR y Arizona Phoenix, el Microsoft Store tiene una variedad de contenido para experimentar en Windows Mixed Reality.
* Acceso anticipado de **[SteamVR:](./using-steamvr-with-windows-mixed-reality.md)** el Windows 10 Fall Creators Update permite reproducir títulos de SteamVR con cascos y controladores de Windows Mixed Reality, lo que hace que el catálogo más grande de títulos de VR esté disponible para Windows Mixed Reality usuarios.

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado duro para ofrecer una experiencia Windows Mixed Reality excelente, pero todavía estamos haciendo un seguimiento de algunos problemas conocidos. Si encuentra a otros usuarios, [puede enviarnos sus comentarios.](/windows/mixed-reality/give-us-feedback)

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicación de escritorio en la Windows Mixed Reality inicio
* Herramienta Recortes no funciona en la aplicación de escritorio.
* La aplicación de escritorio no conserva la configuración al volver a iniciar.
* Si usa la versión preliminar Portal de realidad mixta escritorio, al abrir la aplicación de escritorio en Windows Mixed Reality inicio, es posible que observe el efecto de reflejo infinito. 
* La ejecución de la aplicación de escritorio puede causar problemas de rendimiento en equipos Windows Mixed Reality Ultra. no se recomienda.  
* La aplicación de escritorio puede iniciarse automáticamente porque una ventana invisible del escritorio tiene el foco. 
* El símbolo del sistema de control de cuentas de usuario de escritorio hará que el casco se muestre en negro hasta que se complete el aviso.

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality configuración
* Al configurar el Windows con un casco conectado, es posible que el monitor del equipo se quepa en blanco. Desconecte los cascos para habilitar la salida en el monitor del equipo para completar Windows configuración.
* Al crear un límite, se puede producir un error en el seguimiento. Si es así, inténtelo de nuevo, ya que el sistema aprenderá más sobre el espacio a lo largo del tiempo.
* Si activa o desactiva Cortana configuración durante Windows Mixed Reality configuración, este cambio se aplicará a la configuración de Cortana escritorio.
* Si no tiene cascos conectados, puede que pierda sugerencias cuando visite por primera vez la Windows Mixed Reality hogar.
* Bluetooth los auriculares pueden provocar interferencias con los controladores de movimiento. Se recomienda desapair o encender los controladores Bluetooth durante Windows Mixed Reality sesiones.

### <a name="games-and-apps-from-windows-store"></a>Juegos y aplicaciones de Windows Store
* Algunos juegos de uso intensivo gráfico, como Forza Ahora, 6, pueden causar problemas de rendimiento en equipos con menos capacidad cuando se reproducen dentro de Windows Mixed Reality.

### <a name="audio"></a>Audio
* Como se indicó anteriormente, Bluetooth periféricos de audio no funcionan bien con Windows Mixed Reality de voz y sonido espacial. También pueden afectar negativamente a la experiencia del controlador de movimiento. No se recomienda usar cascos Bluetooth audio con Windows Mixed Reality.
* No se puede usar el dispositivo de audio conectado a (o parte de) el casco para la reproducción de audio cuando el dispositivo no se está agotando. Si solo tiene un casco de audio, puede que desee conectar el casco de audio al equipo host en lugar del casco. Si es así, debe desactivar "Switch to headset audio" (Cambiar al audio del casco) **en Configuración**  >  **Mixed Reality**  >  **audio y voz.**
* Algunas aplicaciones, incluidas muchas de las que se inician a través de SteamVR, pueden perder audio o detenerse cuando cambia el dispositivo de audio al iniciar o detener el Portal de realidad mixta. Reinicie la aplicación después de abrir la aplicación Portal de realidad mixta para corregirlo.
* Si Cortana está habilitado en el equipo host antes de usar el casco de Windows Mixed Reality, puede perder la simulación de sonido espacial aplicada a las aplicaciones que se coloquen alrededor del Windows Mixed Reality principal. La alternativa es habilitar "Windows Sonic para auriculares" en todos los dispositivos de audio conectados al equipo, incluso en el dispositivo de audio conectado al casco:
   1. Haga clic con el botón izquierdo en el icono del altavoz en la barra de tareas del escritorio y seleccione en la lista de dispositivos de audio.
   2. Haga clic con el botón derecho en el icono del hablante en la barra de tareas del escritorio y seleccione "Windows Sonic para auriculares" en el menú "Configuración del hablante".
   3. Repita estos pasos para todos los dispositivos de audio (puntos de conexión).
>[!NOTE]
> - Dado que los auriculares o altavoces conectados al casco no aparecerán a menos que lo lleve, tendrá que hacerlo desde la ventana aplicación de escritorio de la página principal de Windows Mixed Reality para aplicar esta configuración al dispositivo de audio conectado a los cascos (o integrado en el casco).
> - Otra opción es desactivar "Let Cortana respond to Hey Cortana" en Configuración Cortana en el escritorio antes de iniciar  >   Windows Mixed Reality.

* Cuando otro dispositivo USB multimedia (por ejemplo, una cámara web) comparte el mismo concentrador USB (ya sea externo o dentro del equipo) con el casco Windows Mixed Reality, en raras ocasiones los auriculares pueden tener un sonido de timbre o ningún audio. Puede corregir esto mediante el casco en un puerto USB que no comparta el mismo centro que el otro dispositivo, o desconectar o deshabilitar el otro dispositivo multimedia USB.
* En raras ocasiones, el concentrador USB del equipo host no puede proporcionar suficiente energía al casco de Windows Mixed Reality y es posible que observe una ráfaga de ruido de los auriculares conectados al casco.

### <a name="speech"></a>Voz
* Cortana reproducir sus indicaciones de audio para escuchar/pensar y respuestas de audio a los comandos.
* Cortana en los mercados de China y Japón no muestra correctamente el texto debajo del Cortana durante el uso.
* Cortana puede ser lenta la primera vez que se invoca en una Portal de realidad mixta sesión. Para evitarlo, asegúrese de que "Deje que Cortana responder a Hey Cortana" en Configuración Cortana Hable con  >    >  **Cortana** está habilitado.
* Cortana pueden ejecutarse más lentamente en equipos que no están Windows Mixed Reality Ultra equipos.
* Cuando el teclado del sistema se establece en un idioma diferente del idioma de la interfaz de usuario en Windows Mixed Reality, el uso del dictado del teclado en Windows Mixed Reality producirá un cuadro de diálogo de error sobre el dictado que no funciona debido a que no Wi-Fi conexión. Para corregir el problema, asegúrese de que el idioma del teclado del sistema coincide con el Windows Mixed Reality de la interfaz de usuario.
* España no se reconoce correctamente como un mercado en el que la voz está habilitada para Windows Mixed Reality.

### <a name="holograms"></a>Hologramas
* Si ha colocado un gran número de hologramas en su Windows Mixed Reality, algunos pueden desaparecer y volver a aparecer a medida que mira. Para evitar esto, quite algunos de los hologramas de esa área del Windows Mixed Reality inicio.

### <a name="motion-controllers"></a>Controladores de movimiento
* En ocasiones, si selecciona una página web en Edge, el contenido se acercará en lugar de hacer clic.
* A veces, al seleccionar un vínculo en Edge, la selección no funcionará.

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte también
* [Compatibilidad con cascos envolventes (vínculo externo)](./troubleshooting-windows-mixed-reality.md)
* [Problemas conocidos de HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Instalación de las herramientas](/windows/mixed-reality/develop/install-the-tools)
* [Envíenos sus comentarios.](/windows/mixed-reality/give-us-feedback)