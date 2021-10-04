---
title: Uso de SteamVR con Windows Mixed Reality
description: Aprenda a configurar y reproducir juegos de SteamVR en Windows Mixed Reality cascos y controladores con equipos compatibles.
author: qianw211
ms.author: v-qianwen
ms.date: 9/23/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, juegos, SteamVR, Steam, requisitos del sistema
ms.openlocfilehash: b06c5e0b9918a5277a2c31e391dbdbc1ef740110
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436722"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Uso de SteamVR con Windows Mixed Reality

Windows Mixed Reality para SteamVR permite a los usuarios ejecutar experiencias de SteamVR Windows Mixed Reality cascos envolventes. Después de instalar el Windows Mixed Reality para SteamVR, los usuarios pueden iniciar sus aplicaciones de SteamVR favoritas desde su biblioteca de escritorio o de Steam y reproducirlas directamente en su casco Windows de escritorio.

## <a name="get-your-pc-ready"></a>Preparar el equipo

* Asegúrese de que no tiene actualizaciones pendientes: seleccione Start > Configuración > Update & Security > Windows Update (Iniciar > Configuración > actualización de **& seguridad > Windows update).** Si hay actualizaciones disponibles, seleccione **Instalar ahora.** Si no hay actualizaciones disponibles, seleccione **Buscar actualizaciones** y, a continuación, instale las nuevas.
* Los requisitos de pc varían para las aplicaciones y el contenido de Steam. Consulte los requisitos mínimos por título. Un equipo con una tarjeta gráfica GTX 1070 (o equivalente) y un procesador Intel® Core™ i7 debe ofrecer una buena experiencia para una amplia gama de títulos.
* Configure [Windows Mixed Reality](set-up-windows-mixed-reality.md) si aún no lo ha hecho. 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>Configuración de Windows Mixed Reality para SteamVR

1. [Descargue e instale SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. Cuando esté listo, inicie SteamVR. El tutorial de SteamVR debe iniciarse automáticamente.

> **Nota:** Para solucionar problemas avanzados de la instalación de SteamVR, asegúrese de que tiene instalados los siguientes componentes de software:
> 1. Instale [Steam e](http://store.steampowered.com/about/) inicie **sesión** o cree una **nueva cuenta.**
> 2. Instale [SteamVR.](https://store.steampowered.com/app/250820/SteamVR/) Con el casco conectado, inicie Steam y verá un cuadro de diálogo en el que se le pedirá que instale SteamVR. Siga las indicaciones del cuadro de diálogo para instalarlo.
    * Si no ve el elemento emergente, instale SteamVR; para ello, vaya a la *sección Herramientas* de la *biblioteca*. Busque SteamVR en la lista y, a continuación, haga clic con el botón derecho y seleccione *Instalar juego.*
> 3. Instale [Windows Mixed Reality para SteamVR.](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>Configuración de Windows Mixed Reality para SteamVR en un entorno sin acceso a Internet

**Almacenamiento de los medios necesarios en un dispositivo de almacenamiento portátil**
1. Instale [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) y [Windows Mixed Reality para SteamVR como](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) se indicó anteriormente mediante [Steam](http://store.steampowered.com/about/) en un equipo con acceso completo a Internet.
2. En Steam, abra la sección Biblioteca y busque la parte etiquetada como "Herramientas".
3. Una vez instalado SteamVR, haga clic con el botón derecho en la entrada "SteamVR" y, en el menú emergente resultante, haga clic en la entrada "Propiedades".
4. Se abrirá una nueva ventana con varias pestañas. Seleccione la pestaña "ARCHIVOS LOCALES" y haga clic en el botón con la etiqueta "EXAMINAR ARCHIVOS LOCALES".
5. Se abrirá el directorio que contiene el runtime de SteamVR. Copie todo este directorio (denominado SteamVR) en un medio portátil de su elección (por ejemplo, una unidad usb).
6. Haga lo mismo con Windows Mixed Reality para SteamVR y las aplicaciones compatibles con SteamVR que quiera instalar en el equipo de destino.

**Ejecución de SteamVR en el equipo de destino**
1. Después de conectar el dispositivo de almacenamiento portátil en el equipo de destino, mueva las carpetas SteamVR, MixedRealityVRDriver y otras carpetas a un lugar cómodo en el equipo de destino.
![SteamVR y Windows Mixed Reality para SteamVR instalados en el equipo de destino](images/steamvr-install-files.png)

2. Para asegurarse de que SteamVR y MixedRealityVRDriver están en la misma carpeta, abra un símbolo del sistema. Para este ejemplo, se supone que la carpeta que lo contiene se encuentra en *C:\SteamVRInstall.* En ese caso, en el símbolo del sistema debe ejecutar:
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
(Tenga en cuenta que si ejecuta una versión de 32 bits de Windows, la parte de la ruta de acceso anterior `win64` debe ser en su `win32` lugar).

Esto permitirá que el tiempo de ejecución encuentre el Windows Mixed Reality para el controlador de SteamVR en la instalación personalizada.

4. Para ejecutar SteamVR, debe hacer doble clic en el archivo "vrstartup.exe" ubicado  en *SteamVR\bin\win64\vrstartup.exe* oSteamVR\bin\win32\vrstartup.exesi el equipo de destino ejecuta una versión de 32 bits de Windows.

Consulte la [página de documentación de Steamworks para obtener más información y solucionar problemas.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>Reproducir juegos de SteamVR

1. Conectar el casco al equipo y active los controladores de movimiento.
2. Una vez Windows Mixed Reality se haya cargado el dispositivo principal y los controladores estén visibles, abra la aplicación Dete en el escritorio.
3. Use la aplicación Dete para iniciar un juego de SteamVR desde la biblioteca de Steam.

**Sugerencia:** Para iniciar juegos de SteamVR sin quitarse el casco, use la aplicación de escritorio (Iniciar **> Desktop)** para ver e interactuar con el escritorio del equipo dentro de Windows Mixed Reality.

## <a name="using-motion-controllers-with-steamvr"></a>Uso de controladores de movimiento con SteamVR

Usará los controladores de movimiento de forma diferente en distintos juegos. Estos son algunos aspectos básicos que le ayudarán a empezar:

* Para abrir el panel de Steam, presione directamente a la izquierda o a la derecha.
* Para salir de un juego de SteamVR y volver al Windows Mixed Reality inicio, presione Windows botón.

## <a name="changing-the-resolution"></a>Cambio de la resolución

Puede ajustar el control deslizante Resolución de aplicaciones en la ventana Aplicaciones de SteamVR -> Configuración -> en cualquier momento si quiere jugar a juegos con una resolución más alta. **Cuando se usa un multiplicador de resolución más alto, puede esperar que el juego ponga más presión en el equipo. Si aumenta el multiplicador y ve un rendimiento degradado, vuelva a ajustar el control deslizante al nivel predeterminado y reinicie el juego para asegurarse de que el cambio suba.![Ajuste de la resolución de la aplicación](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Uso de varios cascos

Si es un entusiasta de la realidad virtual, es posible que use periódicamente más de un casco de realidad virtual en el mismo equipo. Si ese es el caso, tenga en cuenta que cuando un casco Windows Mixed Reality está conectado, los juegos de SteamVR siempre se iniciarán en el casco Windows Mixed Reality dispositivo. Si desea iniciar juegos de SteamVR en otro casco, asegúrese de desconectar primero el casco Windows Mixed Reality antes de continuar.

## <a name="preview-programs"></a>Programas en versión preliminar

Publicamos actualizaciones periódicas para mejorar el rendimiento, la confiabilidad y la experiencia general del uso de SteamVR Windows Mixed Reality cascos envolventes. Aunque no se requiere ninguno de estos programas en versión preliminar, le recomendamos que se una a ellos si desea obtener actualizaciones antes y con más frecuencia (y enviarnos comentarios sobre esas actualizaciones).

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality para La versión beta de SteamVR

Windows Mixed Reality para SteamVR es el componente que se instala desde la tienda de Steam que permite a SteamVR trabajar con el casco Windows Mixed Reality dispositivo.  Publicamos actualizaciones de este "puente" periódicamente y Steam las instala automáticamente.

Si desea obtener actualizaciones con más frecuencia, le recomendamos que se una a nuestra versión beta pública.  Las actualizaciones van primero a nuestra audiencia beta y usamos sus comentarios para asegurarnos de que las actualizaciones son de alta calidad antes de publicarlas para todos los usuarios.  Si no está en nuestro programa Beta, al final tendrá todas las mismas correcciones y características, pero después de que nuestros usuarios beta las hayan probado.

Para unirse:

  1. En Steam, use la lista desplegable del menú **Biblioteca** para filtrar por **Software.**
  2. En la lista, haga clic con el **botón derecho Windows Mixed Reality en SteamVR** y seleccione **Propiedades.**
  3. Seleccione la **pestaña Betas (Betas).**
  4. Opte por **"beta - public beta"** y seleccione **Cerrar** para confirmar. El campo beta access code (Código de acceso beta) se debe dejar en blanco.
  
### <a name="steamvr-beta"></a>SteamVR Beta

SteamVR está creado y publicado por Valve y es común en todos los cascos de SteamVR.  Sigue un modelo similar de publicación de actualizaciones para los miembros beta antes de publicar en todos los usuarios.

Para unirse:

  1. En Steam, use la lista desplegable del menú **Biblioteca** para filtrar por **Herramientas.**
  2. En la lista, haga clic con el botón **derecho en SteamVR** y seleccione **Propiedades.**
  3. Seleccione la **pestaña Betas (Betas).**
  4. Opte por **"beta - public beta"** y seleccione **Cerrar** para confirmar.  El campo de código de acceso beta se debe dejar en blanco. ![ Cambie a la versión beta de SteamVR en el cuadro de diálogo de propiedades de SteamVR.](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Programa Windows Insider

Windows Mixed Reality forma parte de Windows 10 y Windows 11.  Muchas correcciones y características que afectan a los usuarios de SteamVR incluyen Windows sistema operativo.  Si desea probar las últimas compilaciones Windows 10 y Windows versión preliminar 11, le recomendamos que se una al [Windows Programa Insider](https://insider.windows.com).

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Habilitación de la reproducción de movimiento para aplicaciones de SteamVR

Windows Mixed Reality para SteamVR tiene una característica experimental de reproducción de movimiento para que la reproducción de 90 FPS sea más fluida.

Cuando se habilita la reproducción de movimiento, todos los juegos de Vr de Steam se representarán nominalmente a una velocidad de fotogramas de 1/2 (45 fps en lugar de 90 FPS), mientras que Windows Mixed Reality para SteamVR usa vectores de movimiento generados por la GPU para extrapolar el fotograma siguiente. En el caso de los juegos de SteamVR que alcanzaron de forma confiable 60 FPS+ en un equipo determinado, esto debería dar lugar a una experiencia sólida de 90 FPS con artefactos ocasionales mientras se mantiene una experiencia cómoda.

Los modos de reproducción de movimiento disponibles son los siguientes:

* **Configuración de SteamVR** por aplicación: permite controlar la reproducción de movimiento a través de la interfaz de usuario de Configuración Desaprotección de Movimiento. A continuación, puede abrir la Configuración Desenlaz, ir a Video > Per-Application Video Configuración y seleccionar una opción para "Suavizado de movimiento".
* **Automático:** permite que la reproducción de movimiento se active automáticamente cuando un juego se representa demasiado lentamente para mantener 90 FPS. Cuando un juego comienza a mantener 90 FPS o empieza a representarse a menos de 45 FPS, se desactivará la reproducción del movimiento. La reproducción de rotación asincrónica siempre está habilitada.
* **Vector de movimiento:** fuerza a la aplicación a ejecutarse siempre a una velocidad de fotogramas media con reproducción de vector de movimiento.
* **Ninguno:** deshabilita la reproducción de movimiento.

**Se esperaba visual Artifacts** 

1. Cuando se usa una resolución de aplicación superior al 150 %, puede experimentar un desenfoque. Al usar la reproducción de movimiento, se recomienda usar un valor inferior al 150 %.
2. Los bordes o texto de contraste nítido, especialmente en los menús o huds del juego, pueden parecer deformes o distorsionados temporalmente debido a la disoclusión.
3. SteamVR Home y muchos otros juegos que no alcanzarán de forma confiable 50-60 FPS en el equipo seguirán teniendo una experiencia deficiente con este modo.
4. Se ha notificado que algunos juegos se ejecutan a una velocidad del 50 % o con mayor latencia (retraso). Informe de estos juegos a través [de las Centro de opiniones sobre Windows](filing-feedback.md) siguientes.

Inicialmente, tenemos compatibilidad experimental con GPU NVidia de generación reciente. Seguimos iterando y mejorando la compatibilidad con la reproducción de movimiento en más GPU, y estamos dispuestos a escuchar sus comentarios.

**GPU admitidas:** Nvidia GeForce GTX1060, AMD RX470 o una versión más alta, con Windows Mixed Reality controladores de gráficos compatibles instalados.

Para habilitar la reproducción de movimiento:

1. Asegúrese de que ha optado por la versión **Windows Mixed Reality de SteamVR Beta** con las instrucciones anteriores.
2. Abra el panel de SteamVR.
3. Seleccione el botón del lado izquierdo con el logotipo de Windows Mixed Reality para abrir **Windows Mixed Reality para SteamVR** Configuración.
4. En la interfaz de usuario que aparece, seleccione la pestaña Gráficos.
5. Seleccione "Auto" (Automático) en "Default SteamVR app motion reprojection mode" (Modo predeterminado de reproducción de movimiento de la aplicación SteamVR) para habilitar la reproducción automática del movimiento.

![Habilitación del indicador LSR & LSR con configuraciónUX](images/settingsux-enable-lsr.gif)

**Indicador de reproyecto de movimiento**

El indicador de reproyecto de movimiento ayuda a diagnosticar problemas con la característica experimental de reproducción automática de movimiento. Cuando se establece en true, verá un indicador en la parte superior izquierda de la pantalla del casco durante la reproducción automática del movimiento. El color y la posición de este indicador se corresponden con el modo de reproducción de movimiento actual; consulte el diagrama siguiente para obtener ejemplos.

![mvLSR Indicator](images/mvLSRIndicator.png)

Verde = la reproducción de movimiento está desactivada porque la aplicación se puede representar a velocidad de fotogramas completa.

La reproducción de movimiento de agua = está en porque la aplicación está enlazada a la CPU.

Azul = la reproducción de movimiento está en porque la aplicación está enlazada a gpu.

Rojo = la reproducción de movimiento está desactivada porque la aplicación se ejecuta a menos de la mitad de la velocidad de fotogramas; intente reducir el super muestreo si está habilitado.

Verde + azul + azul = la reproducción de movimiento está en modo de velocidad de fotogramas media o la aplicación solicitó la reproducción de movimiento.

## <a name="sharing-feedback-on-steamvr"></a>Compartir comentarios sobre SteamVR

Sus comentarios son muy valiosos a la hora de mejorar la Windows Mixed Reality de SteamVR. Envíe todos los comentarios y errores a través [del Centro de opiniones sobre Windows](filing-feedback.md). Siga estas sugerencias para ayudarnos a sacar el máximo partido de sus comentarios:

1. En Centro de opiniones, indique que está informando de un nuevo problema en "¿Qué tipo de comentarios es?" sección de la parte superior.
2. Seleccione la **Mixed Reality** categoría y la **subcategoría** Aplicaciones.
3. Coloque la palabra "SteamVR" en el resumen del problema. Esto nos ayuda a encontrar sus comentarios.
4. Describa qué juego o aplicación de SteamVR usaba al encontrarse con el problema.
5. Considere la posibilidad de adjuntar un informe del sistema de SteamVR a sus comentarios. Esto proporciona más registros que pueden ayudarnos a diagnosticar el problema.
    1. En la ventana de SteamVR (las ventanas pequeñas que muestran el estado del controlador), seleccione en el título para abrir el menú.
    2. Seleccione "Crear informe del sistema".
    3. Guardar en archivo.
    4. Adjunte el archivo generado a la Centro de opiniones entrada directamente.
6. Si sus comentarios son sobre el rendimiento de SteamVR, recopile un Mixed Reality de rendimiento: 
    1. Seleccione el **botón Volver a crear mi** problema.
    2. En la lista desplegable situada junto a "Incluir datos sobre", **seleccione Mixed Reality Rendimiento.**
    3. Asegúrese de que el juego se está ejecutando y seleccione **Iniciar captura.**
    4. Pase unos segundos en el juego para capturar el seguimiento. No capture el seguimiento durante más de 10-15 segundos o será demasiado grande para enviarlo.
    5. Seleccione **Detener captura.**
7. Seleccione **Enviar** una vez que haya completado el resto de los campos.

Si tiene preguntas o comentarios que compartir, también puede comunicarse con nosotros en nuestro foro [de Steam.](http://steamcommunity.com/app/719950/discussions/)

## <a name="see-also"></a>Consulte también

* [Solución de problemas de SteamVR con Windows Mixed Reality](steamvr-questions.md)
* [Uso de juegos y aplicaciones en Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Uso de controladores de HP en Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Uso de controladores de HP en Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [Registro de problemas y comentarios](filing-feedback.md)
