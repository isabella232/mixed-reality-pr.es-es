---
title: Configuración del proyecto sin MRTK
description: Aprenda a configurar un nuevo proyecto de Unity para Windows Mixed Reality sin el Mixed Reality Toolkit.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento
ms.openlocfilehash: 85f8dee3208ce2c2a3bd328641544cbba0525cabdd1bf99404065572aeb354cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210991"
---
# <a name="configuring-your-project-without-mrtk"></a>Configuración de un proyecto sin MRTK

Windows Mixed Reality (WMR) es una plataforma de Microsoft introducida como parte del Windows 10 operativo. La plataforma WMR permite compilar aplicaciones que representan contenido digital en dispositivos de visualización holográficas y vr.

Aunque Microsoft y la comunidad han creado herramientas de código abierto como [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) que configurarán automáticamente el entorno WMR, muchos desarrolladores desean crear sus experiencias desde el primer momento.  En la siguiente documentación se muestra cómo configurar correctamente un proyecto para Mixed Reality desarrollo independientemente de si usa MRTK o no.  La configuración que debe cambiar se divide en dos categorías: configuración por proyecto y configuración por escena.

> [!NOTE]
> Siempre puede importar MRTK más adelante, por lo que no hay ninguna penalización por ir primero a la ruta manual.

Si elige la configuración manual de WMR, la configuración que debe cambiar se divide en dos categorías: por proyecto y por escena.

## <a name="per-project-settings"></a>Configuración por proyecto

Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltada](images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar a la Plataforma de Windows universal:

1.  Seleccione **Archivo > compilación Configuración...**
2.  Seleccione **Universal Windows Platform en** la lista Plataforma y seleccione Cambiar **plataforma.**
3.  Establezca la **arquitectura** en **ARM 64**
4.  Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5.  Establezca **Build Type** (Tipo de compilación) en **D3D**.
6.  Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)
7.  Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).

![Captura de pantalla de la ventana Configuración compilación abierta en el editor de Unity con Universal Windows Platform resaltado](images/wmr-config-img-4.png)

Después de configurar la plataforma, debe hacer [](../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.

### <a name="for-xrsdk"></a>Para XRSDK 

1. En el Editor de Unity, vaya **a Editar > Project configuración y** seleccione Administración de complementos **XR.**

2. Seleccione **Install XR Plugin Management (Instalar administración de complementos XR).**

![Captura de pantalla Project Configuración ventana abierta en el editor de Unity con la administración del complemento XR resaltada](images/wmr-config-img-5.png)

3. Seleccione **Initialize XR on Startup (Inicializar XR)** **al iniciar Windows Mixed Reality**

![Captura de pantalla de Project ventana de configuración abierta en el editor de Unity con la administración de complementos XR resaltada](images/wmr-config-img-7.png)

4. Expanda la **sección XR Plug-in Management (Administración** de complementos de XR) y seleccione Univeral Windows Platform Configuración (Plataforma **Configuración univeral).**
5. Si usa Unity 2020 o posterior, verá las opciones para comprobar **OpenXR** o **Windows Mixed Reality**. 
    * Puede elegir cualquiera de los entornos de ejecución.  Si va a desarrollar específicamente para HoloLens 2 o HP Reverb G2 y decide probar **OpenXR,** active la casilla OpenXR y revise nuestra guía Uso del complemento [openXR](./xr-project-setup.md) de Mixed Reality para Unity para configurarse correctamente para estos dispositivos antes de volver a este tutorial.

> [!NOTE]
> A partir de Unity 2020 LTS, Microsoft está adoptando el desarrollo con OpenXR.  A medida que migramos a esta ruta de acceso, en Unity 2021.1 el complemento XR de Windows estará en desuso y se quitará en 2021.2, lo que hace que OpenXR sea la única ruta de acceso admitida. Puede encontrar más información en [Uso del complemento Mixed Reality OpenXR.](./xr-project-setup.md)

6. Si decide elegir  el complemento de Windows Mixed Reality, active todas las casillas y establezca **Modo de envío de** profundidad en Profundidad **de 16 bits.**

![Captura de pantalla Project ventana de configuración abierta en el editor de Unity con Windows Mixed Reality sección resaltada](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Para XR heredado 

> [!CAUTION]
> El XR heredado está en desuso en Unity 2019 y se ha quitado en Unity 2020.

1. Abra **player Configuración...** desde el **cuadro de diálogo Configuración... ventana** y expanda el **grupo de Configuración XR**
2. En la **sección XR Configuración,** seleccione **Virtual Reality Supported (Compatible con Virtual Reality)** para agregar la lista Dispositivos de realidad virtual.
3. Establezca **Depth Format (Formato de** profundidad) en Profundidad de **16 bits** y habilite Depth Buffer Sharing (Uso compartido del búfer de **profundidad).**
4. Establecer **el modo de representación estéreo** en Instancia de paso **único**
5. Seleccione **WSA Holographic Remoting Supported** (Comunicación remota holográfica de WSA compatible) si quiere usar la comunicación remota holográfica. 

![Captura de pantalla de Project ventana de configuración abierta en el editor de Unity con la sección Configuración del reproductor resaltada](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Actualización del manifiesto

La aplicación ahora puede controlar la representación holográfica y la entrada espacial. Sin embargo, la aplicación debe declarar las funcionalidades adecuadas en su manifiesto para aprovechar determinadas funcionalidades. Para encontrar las funcionalidades de los proyectos, vaya a Player Configuración > Configuración for Universal Windows Platform > Publishing Configuración > Capabilities (Funcionalidades de publicación **Configuración > universales).** 

Se recomienda que realice las declaraciones de manifiesto en Unity para incluirlas en todos los proyectos futuros que exporte. Las funcionalidades aplicables para habilitar las API de Unity más usadas para Mixed Reality son:

|  Capacidad  |  API que requieren funcionalidad | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acceso a [mallas](../../design/spatial-mapping.md) de asignación espacial en HoloLens) No se necesita ninguna funcionalidad para el seguimiento &mdash; *espacial general del casco* | 
|  Webcam  |  PhotoCapture y VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture o VideoCapture, respectivamente (al almacenar el contenido capturado) | 
|  Micrófono  |  VideoCapture (al capturar audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (y para usar Unity Profiler) | 

### <a name="quality-settings"></a>Configuración de calidad

HoloLens tiene una GPU de clase móvil. Si la aplicación tiene como destino HoloLens, querrá empezar con la configuración de calidad de la aplicación ajustada para obtener un rendimiento más rápido para asegurarse de que mantiene la velocidad de fotogramas completa.  Una vez que haya mejorado aún más el desarrollo, puede considerar la posibilidad de mejorar la configuración de calidad para encontrar el equilibrio adecuado entre calidad y rendimiento: 

1. Seleccione **Editar > Project Configuración > calidad** 
2. Seleccione la **lista desplegable** debajo del  **Windows store** y seleccione Very Low    **(Muy bajo).** Sabrá que la configuración se aplica correctamente cuando el cuadro de la columna Windows Store y la fila Very Low (Muy baja) sea verde. 
3. En **** la sección   Sombras, seleccione **Deshabilitar sombras.** 

![Captura de pantalla de Project ventana de configuración abierta en el editor de Unity con la sección de configuración de calidad resaltada](images/wmr-config-img-10.png)<br>
*Configuración de calidad de Unity*

## <a name="per-scene-settings"></a>Configuración por escena

### <a name="unity-camera-settings"></a>Configuración de la cámara de Unity

Con **La realidad virtual compatible activada,** el componente Cámara de [Unity](camera-in-unity.md) controla el seguimiento de la cabeza y la [representación estereomática.](../platform-capabilities-and-apis/rendering.md) Esto significa que no es necesario reemplazar el objeto Cámara principal por una cámara personalizada.

Si la aplicación tiene como destino HoloLens específicamente, debe cambiar algunas opciones de configuración para optimizar las pantallas transparentes del dispositivo. Esta configuración permite que el contenido holográfico se muestre en el mundo físico:

1. En la **jerarquía**, seleccione la **cámara principal.**
2. En el **panel Inspector,** establezca la posición de transformación en  **0, 0, 0** para que la ubicación de la cabeza del usuario comience en el origen del mundo de Unity.
3. Cambie **Clear Flags (Borrar marcas)** **a Solid Color (Color sólido).**
4. Cambie el color **de** fondo **a RGBA 0,0,0,0**. El negro se representa como transparente en HoloLens.
5. Cambiar **planos de recorte: cerca** del HoloLens [recomendado](camera-in-unity.md#using-clipping-planes) 0,85 (metros).

![Captura de pantalla de la pestaña inspector abierta en el editor de Unity](images/wmr-config-img-11.png)<br>
*Configuración de la cámara de Unity*

> [!IMPORTANT]
> Si elimina y crea una cámara nueva, asegúrese de que la nueva cámara esté etiquetada **como MainCamera**.

## <a name="next-steps"></a>Pasos siguientes

Ahora que el proyecto está listo, puede empezar a desarrollar su experiencia Mixed Reality trabajo:

* Agregar [bloques de creación principales](unity-development-overview.md#2-core-building-blocks)
* Consulte las API [y las funcionalidades de la plataforma disponibles](unity-development-overview.md#3-advanced-features)
* Aprenda a implementar [la aplicación](../platform-capabilities-and-apis/using-visual-studio.md#)
* Uso del [simulador de Mixed Reality de datos](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](../install-the-tools.md)