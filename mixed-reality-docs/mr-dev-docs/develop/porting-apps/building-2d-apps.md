---
title: Actualización de aplicaciones para UWP en 2D para Windows Mixed Reality
description: En este artículo se describe la actualización de la aplicación 2D Universal Windows Platform existente para que se ejecute en HoloLens y Windows Mixed Reality cascos envolventes.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Aplicación 2D, UWP, aplicación plana, HoloLens, casco envolvente, modelo de aplicación, botón Atrás, barra de la aplicación, ppp, resolución, escala, porte, HoloLens 1.ª generación, HoloLens 2, casco de realidad mixta, casco de realidad mixta de Windows, migración, Windows 10
ms.openlocfilehash: 2b0fa403394432f2cec80e44d27804b07934260e60281f5c70b68c7377d3e55e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196029"
---
# <a name="updating-2d-uwp-apps-for-windows-mixed-reality"></a>Actualización de aplicaciones para UWP en 2D para Windows Mixed Reality

Windows Mixed Reality permite a los usuarios ver hologramas como si se hubieran situado a su alrededor en el mundo físico y digital. En esencia, tanto los HoloLens como los equipos de escritorio a los que se adjuntan los accesorios de los cascos envolventes Windows 10 dispositivos. Puedes ejecutar casi todas las aplicaciones de la Plataforma Windows universal (UWP) en la Tienda como aplicaciones 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Creación de una aplicación para UWP en 2D para realidad mixta

El primer paso para llevar una aplicación 2D a cascos de realidad mixta es hacer que la aplicación se ejecute como una aplicación 2D estándar en el monitor de escritorio.

### <a name="building-a-new-2d-uwp-app"></a>Creación de una nueva aplicación 2D para UWP

Para compilar una nueva aplicación 2D para la realidad mixta, creas una aplicación 2D Universal Windows Platform (UWP) estándar. No se requiere ningún otro cambio de aplicación para que esa aplicación se ejecute como una pizarra en la realidad mixta.

Para empezar a crear una aplicación para UWP en 2D, consulta [el artículo Creación de tu primera aplicación.](/windows/uwp/get-started/your-first-app)

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Llevar una aplicación de la Tienda 2D existente a UWP

Si ya tienes una aplicación de Windows 2D en la Tienda, asegúrate de que tiene como destino Windows 10 Plataforma Windows universal (UWP). Estos son todos los posibles puntos de partida que puede tener con la aplicación de la Tienda hoy:
<br>

|  Punto de partida  |  Destino de la plataforma de manifiesto de AppX  |  ¿Cómo hacer que sea universal? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifiesto de aplicación de Silverlight |  [Migración a WinRT](/previous-versions/windows/apps/dn642486(v=vs.105)) | 
|  Windows Phone 8.1 Universal  |  8.1 Manifiesto de AppX que no incluye el destino de plataforma  |  [Migración de la aplicación a la plataforma Windows universal](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Tienda 8  |  8 Manifiesto de AppX que no incluye el destino de plataforma  |  [Migración de la aplicación a la plataforma Windows universal](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8.1 Universal  |  8.1 Manifiesto de AppX que no incluye el destino de plataforma  |  [Migración de la aplicación a la plataforma Windows universal](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 

Si tiene una aplicación de Unity 2D compilada actualmente como una aplicación Win32 en el equipo, mac & Linux standalone build target (Destino de compilación independiente de **Mac & Linux),** cambie al destino de compilación de la Plataforma universal **de Windows** para la realidad mixta.

Hablaremos sobre las formas en que puede restringir la aplicación específicamente para HoloLens mediante el Windows. Familia de dispositivos [holográficos debajo de](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Ejecución de la aplicación 2D en un casco Windows Mixed Reality envolvente

Si ha implementado la aplicación 2D en una máquina de escritorio y la ha probado en el monitor, está listo para probarlo con un casco de escritorio envolvente.

Solo tiene que ir al menú Inicio el casco de realidad mixta e iniciar la aplicación desde allí. Tanto el shell de escritorio como el shell holográfico comparten el mismo conjunto de aplicaciones para UWP, por lo que la aplicación ya debe estar presente una vez que se haya implementado desde Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Dirigirse tanto a cascos envolventes como a HoloLens

¡Enhorabuena! La aplicación ahora usa la plataforma Windows 10 Universal Windows (UWP).

La aplicación ahora es capaz de ejecutarse en los dispositivos Windows actuales, como escritorio, móvil, Xbox, cascos envolventes de Windows Mixed Reality, HoloLens y dispositivos Windows futuro. Sin embargo, para dirigirse realmente a todos esos dispositivos, deberá asegurarse de que la aplicación tiene como destino el Windows. Familia de dispositivos universales.

### <a name="change-your-device-family-to-windowsuniversal"></a>Cambie la familia de dispositivos a Windows. Universal

Ahora vamos a saltar al manifiesto de AppX para asegurarnos de que Windows 10 aplicación para UWP se puede ejecutar en HoloLens:
* Abra el archivo de solución de la aplicación **con Visual Studio** vaya al manifiesto del paquete de aplicación.
* Haga clic con el botón **derecho en el archivo Package.appxmanifest** de la solución y vaya a Ver **código.**<br>
  ![package.appxmanifest en Explorador de soluciones](images/openappxmanifest-500px.png)<br>
* Asegúrese de que la plataforma de destino Windows. Universal en la sección de dependencias
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* ¡Salvar!

Si no usa Visual Studio para el entorno de desarrollo, puede abrir **AppXManifest.xml** en el editor de texto de su elección para asegurarse de que el destino es **Windows. Universal** *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Ejecute en el HoloLens Emulator

Ahora que la aplicación para UWP tiene como destino "Windows. Universal", vamos a compilar la aplicación y ejecutarla en el [HoloLens Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).
* Asegúrese de que está [instalado el HoloLens Emulator](../install-the-tools.md).
* En Visual Studio, seleccione la configuración **de compilación x86** para la aplicación.

  ![Configuración de compilación x86 en Visual Studio](../platform-capabilities-and-apis/images/x86setting.png)<br>
* Selecciona **Emulador de HoloLens** en el menú desplegable de destino de la implementación.

  ![HoloLens Emulator en la lista de destinos de implementación](images/deployemulator-500px.png)<br>
* Seleccione **Depurar > Iniciar depuración** para implementar la aplicación e iniciar la depuración.
* El emulador iniciará y ejecutará la aplicación.
* Con un teclado, un mouse y un controlador de Xbox, coloque la aplicación en el mundo para iniciarla.

  ![HoloLens Emulator cargado con un ejemplo de UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Pasos siguientes

En este momento, puede ocurrir una de estas dos cosas:
1. La aplicación mostrará su presentación y comenzará a ejecutarse después de colocarla en el Emulator. Genial.
2. O bien, después de ver una animación de carga para un holograma 2D, la carga se detendrá y solo verá la aplicación en su pantalla de presentación. Esto significa que algo salió mal y se llevará a cabo una investigación más exhaustiva para comprender cómo dar vida a la aplicación en Mixed Reality.

Deberá depurar para llegar a la raíz de los posibles problemas que impiden que la aplicación para UWP se inicie en HoloLens.

### <a name="running-your-uwp-app-in-the-debugger"></a>Ejecución de la aplicación para UWP en el depurador

Estos pasos le ayudarán a depurar la aplicación para UWP mediante Visual Studio depurador.
* Si aún no lo ha hecho, abra la solución en Visual Studio. Cambie el destino a la **HoloLens Emulator** y la configuración de compilación a **x86**.
* Seleccione **Depurar > Iniciar depuración** para implementar la aplicación e iniciar la depuración.
* Coloque la aplicación en el mundo con el mouse, el teclado o el controlador de Xbox.
* Visual Studio debería interrumpirse en algún lugar del código de la aplicación.
  - Si la aplicación no se bloquea inmediatamente o se interrumpe en el depurador debido a un error no controlada, pase por una prueba de las características principales de la aplicación para asegurarse de que todo se está ejecutando y funcionando. Es posible que vea errores como los que se muestran a continuación (excepciones internas que se están controlando). Para asegurarse de que no se pierden los errores internos que afectan a la experiencia de la aplicación, ejecute las pruebas automatizadas y las pruebas unitarias para asegurarse de que todo se comporta según lo previsto.

![HoloLens Emulator cargado con un ejemplo de UWP que muestra una excepción del sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Actualización de la interfaz de usuario

Ahora que la aplicación para UWP se ejecuta en cascos envolventes y HoloLens como un holograma 2D, nos aseguraremos de que tiene un aspecto muy bueno. Estos son algunos aspectos que hay que tener en cuenta:
* Windows Mixed Reality todas las aplicaciones 2D a una resolución fija y PPP que equivale a 853 x 480 píxeles efectivos. Tenga en cuenta si el diseño necesita refinamiento a esta escala y revise las instrucciones de diseño siguientes para mejorar su experiencia en HoloLens cascos envolventes.
* Windows Mixed Reality [no admite iconos](../../design/app-model.md) dinámicos 2D. Si la funcionalidad principal muestra información en un icono dinámico, considere la posibilidad de volver a mover esa información a la aplicación o explorar los iniciadores de [aplicaciones 3D.](../../distribute/3d-app-launcher-design-guidance.md)

### <a name="2d-app-view-resolution-and-scale-factor"></a>Resolución de vista de aplicaciones 2D y factor de escala

![Desde el diseño con capacidad de respuesta](images/scale-500px.png)

Windows 10 todo el diseño visual de píxeles de pantalla reales a **píxeles efectivos.** Esto significa que los desarrolladores diseñan su interfaz de usuario siguiendo las directrices de interfaz humana de Windows 10 para píxeles efectivos, y el escalado de Windows garantiza que esos píxeles efectivos son el tamaño adecuado para la facilidad de uso entre dispositivos, resoluciones, PPP, entre otros. Consulte esta [excelente lectura en MSDN y](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) esta presentación de [COMPILAción](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx) para obtener más información.

Incluso con la capacidad única de colocar aplicaciones en su mundo a una variedad de distancias, se recomiendan las distancias de visualización similares a la televisión para generar la mejor legibilidad e interacción con la mirada y el gesto. Por eso, una pizarra virtual en el Mixed Reality inicio mostrará la vista plana de UWP en:

**1280 x 720, 150 %PPP** (853 x 480 píxeles efectivos)

Esta resolución tiene varias ventajas:
* Este diseño de píxeles efectivo tendrá aproximadamente la misma densidad de información que una tableta o un escritorio pequeño.
* Coincide con los ppp fijos y los píxeles efectivos para las aplicaciones para UWP que se ejecutan en Xbox One, lo que permite experiencias sin problemas en todos los dispositivos.
* Este tamaño se ve bien cuando se escala a través de nuestra gama de distancias de funcionamiento para las aplicaciones del mundo.

### <a name="2d-app-view-interface-design-best-practices"></a>Procedimientos recomendados de diseño de la interfaz de vista de aplicaciones 2D

**hacer:**
* Siga las instrucciones [Windows 10 human interfaces (HIG)](https://dev.windows.com/design) para obtener estilos, tamaños de fuente y tamaños de botón. HoloLens realizará el trabajo para asegurarse de que la aplicación tendrá patrones de aplicación compatibles, tamaños de texto legibles y el tamaño adecuado del destino de la coincidencia.
* Asegúrese de que la [](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) interfaz de usuario sigue los procedimientos recomendados para que el diseño con capacidad de respuesta se vea mejor en HoloLens resolución única y PPP de la interfaz de usuario.
* Use las recomendaciones de tema de color "claro" de Windows.

**No:**
* Cambie la interfaz de usuario demasiado drásticamente en realidad mixta para asegurarse de que los usuarios tienen una experiencia familiar dentro y fuera del casco.

### <a name="understand-the-app-model"></a>Comprender el modelo de aplicación

El [modelo de aplicación](../../design/app-model.md) para la realidad mixta está diseñado para usar Mixed Reality Home, donde muchas aplicaciones convivien. Piense en esto como el equivalente de realidad mixta del escritorio, donde se ejecutan muchas aplicaciones 2D a la vez. Esto tiene implicaciones en el ciclo de vida de la aplicación, los iconos y otras características clave de la aplicación.

### <a name="app-bar-and-back-button"></a>Barra de la aplicación y botón Atrás

Las vistas 2D se decoran con una barra de aplicación encima de su contenido. La barra de la aplicación tiene dos puntos de personalización específicos de la aplicación:

**Título:** muestra el *nombre para mostrar* del icono asociado a la instancia de la aplicación.

**Botón Atrás:** genera el *[evento BackRequested](/uwp/api/Windows.UI.Core.SystemNavigationManager)* cuando se presiona. La visibilidad del botón Atrás se controla *[mediante SystemNavigationManager.AppViewBackButtonVisibility](/uwp/api/Windows.UI.Core.SystemNavigationManager)*.

![Interfaz de usuario de la barra de aplicaciones en la vista de aplicación 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Interfaz de usuario de la barra de aplicaciones en la vista de aplicación 2D*

### <a name="test-your-2d-apps-design"></a>Prueba del diseño de la aplicación 2D

Es importante probar la aplicación para asegurarse de que el texto es legible, de que los botones son de destino y de que la aplicación general tiene el aspecto correcto. Puede probar [en un](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) casco de escritorio, un HoloLens, un emulador o un dispositivo táctil con una resolución establecida en 1280 x 720 @150 %.

## <a name="new-input-possibilities"></a>Nuevas posibilidades de entrada

HoloLens sensores de profundidad avanzados para ver el mundo y ver a los usuarios. Esto permite gestos de mano avanzados [como bloom](../../design/system-gesture.md#bloom) y [pulsación en el aire.](../../design/gaze-and-commit.md#composite-gestures) Los micrófonos eficaces también permiten [experiencias de voz.](../../design/voice-input.md)

Con los cascos de escritorio, los usuarios pueden usar controladores de movimiento para apuntar a las aplicaciones y tomar medidas. También pueden usar un gamepad, que tiene como destino objetos con su mirada.

Windows se encarga de toda esta complejidad para las aplicaciones para UWP, traduciendo [](/windows/uwp/design/input/handle-pointer-input#pointer_events) la [mirada,](../../design/gaze-and-commit.md)los gestos, la voz y la entrada del controlador de movimiento en eventos de puntero que abstraen el mecanismo de entrada. Por ejemplo, es posible que un usuario haya realizado una pulsación en el aire con la mano o que haya presionado el desencadenador Select en un controlador de movimiento, pero las aplicaciones 2D no necesitan saber de dónde provenía la entrada: simplemente ven una pulsación táctil 2D, como en una pantalla táctil.

Estos son los conceptos o escenarios de alto nivel que debe comprender para la entrada al llevar la aplicación para UWP a HoloLens:
* [La](../../design/gaze-and-commit.md) mirada se convierte en eventos de mantener el mouse, lo que puede desencadenar de forma inesperada menús, controles o otros elementos de la interfaz de usuario para que se desplacen por la aplicación.
* La mirada no es tan precisa como la entrada del mouse. Use destinos de acceso con el tamaño adecuado para HoloLens, de forma similar a las aplicaciones móviles táctiles. Los elementos pequeños cerca de los bordes de la aplicación son especialmente difíciles de interactuar.
* Los usuarios deben cambiar los modos de entrada para pasar de desplazarse a arrastrar hasta desplazarse con dos dedos. Si la aplicación se diseñó para la entrada táctil, considere la posibilidad de asegurarse de que ninguna funcionalidad principal esté bloqueada detrás del movimiento panorámico de dos dedos. Si es así, considere la posibilidad de tener mecanismos de entrada alternativos, como botones que pueden iniciar el movimiento panorámico de dos dedos. Por ejemplo, la aplicación Mapas puede hacer zoom con movimiento panorámico con dos dedos, pero tiene un botón más, menos y girar para simular las mismas interacciones de zoom con clics únicos.

[La entrada de](../../design/voice-input.md) voz es una parte fundamental de la experiencia de realidad mixta. Hemos habilitado todas las API de voz que están en Windows 10 encendido Cortana usar un casco.

## <a name="publish-and-maintain-your-universal-app"></a>Publicación y mantenimiento de la aplicación universal

Una vez que la aplicación esté en funcionamiento, empaquete la aplicación [para enviarla al Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Consulte también
* [Modelo de aplicaciones](../../design/app-model.md)
* [Mirada-cabeza y confirmación](../../design/gaze-and-commit.md)
* [Controladores de movimiento](../../design/motion-controllers.md)
* [Entrada de voz](../../design/voice-input.md)
* [Envío de aplicaciones a Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Uso del emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)