---
title: Configuración del proyecto sin MRTK
description: Aprenda a configurar un nuevo proyecto de Unity para Windows Mixed Reality sin el kit de herramientas de realidad mixta.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento
ms.openlocfilehash: 1d4acb80a7ad0c5143a4408829759aab0a2c012b
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009908"
---
# <a name="configuring-your-project-without-mrtk"></a>Configuración de un proyecto sin MRTK

Windows Mixed Reality (WMR) es una plataforma de Microsoft introducida como parte del sistema operativo Windows 10. La plataforma WMR permite crear aplicaciones que representan contenido digital en dispositivos de visualización holográfica y VR.

Aunque Microsoft y la comunidad han creado herramientas de código abierto, como el kit de herramientas de la [realidad mixta (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , que configurará automáticamente el entorno de WMR, muchos desarrolladores quieren crear sus experiencias desde cero.  En la siguiente documentación se muestra cómo configurar correctamente un proyecto para el desarrollo de realidad mixta, tanto si usa MRTK como si no.  La configuración que debe cambiar se divide en dos categorías: configuración por proyecto y configuración por escena.

> [!NOTE]
> Siempre puede importar MRTK más adelante, por lo que no hay ninguna penalización en primer lugar en la ruta manual.

Si elige la configuración manual de WMR, la configuración que debe cambiar se divide en dos categorías: por proyecto y por escena.

## <a name="per-project-settings"></a>Configuración por proyecto

Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana de configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltada](images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar a la Plataforma universal de Windows:

1.  Seleccionar **archivo > configuración de compilación...**
2.  Seleccione **plataforma universal de Windows** en la lista plataforma y seleccione **Switch Platform (cambiar plataforma** ).
3.  Establecimiento de la **arquitectura** en **ARM 64**
4.  Establecimiento del **dispositivo de destino** en **HoloLens**
5.  Establecer el **tipo de compilación** en **D3D**
6.  Establecimiento del **SDK de UWP** en la **versión más reciente instalada**
7.  Establezca la **configuración de compilación** en **Release** porque hay problemas de rendimiento conocidos con debug

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

Después de establecer la plataforma, debe dejar que Unity sepa crear una [vista envolvente](../../design/app-views.md) en lugar de una vista 2D cuando se exporte.

### <a name="for-xrsdk"></a>Para XRSDK 

1. En el editor de Unity, navegue a **editar > configuración del proyecto** y seleccione **Administración de complementos de XR** .

2. Seleccione **instalar administración de complementos de XR**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-5.png)

3. Seleccione **inicializar XR en el inicio** y **Windows Mixed Reality** .

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-7.png)

4. Expanda la sección **Administración de complementos de XR** y seleccione **Windows Mixed Reality** .
5. Active todas las casillas y establezca el **modo de envío de profundidad** en profundidad de **16 bits**

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con Windows Mixed Reality sección resaltada](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Para XR heredado 

> [!CAUTION]
> El XR heredado está en desuso en Unity 2019 y se quitó en Unity 2020.

1. Abra **configuración del reproductor...** en la **configuración de compilación... y** expanda el grupo de **configuración XR**
2. En la sección **configuración de XR** , seleccione **realidad virtual compatible** para agregar la lista de dispositivos de realidad virtual.
3. Establecer el **formato de profundidad** en profundidad de **16 bits** y habilitar el **uso compartido del búfer de profundidad**
4. Establecer el **modo de representación estéreo** en **una instancia de paso único**
5. Seleccione **WSA Holographic Remoting compatible** si desea usar Holographic Remoting 

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con la sección configuración del reproductor resaltada](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Actualización del manifiesto

La aplicación ahora puede controlar la representación holográfica y la entrada espacial. Sin embargo, la aplicación debe declarar las capacidades adecuadas en el manifiesto para aprovechar ciertas funciones. Para encontrar las capacidades de los proyectos, vaya a **configuración del reproductor > configuración de Plataforma universal de Windows > configuración de publicación > funcionalidades**. 

Se recomienda que realice las declaraciones de manifiesto en Unity para incluirlas en todos los proyectos futuros que exporte. Las capacidades aplicables para habilitar las API de Unity usadas con frecuencia para la realidad mixta son:

|  Capacidad  |  API que requieren funcionalidad | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acceso a mallas de [asignación espacial](../../design/spatial-mapping.md) en HoloLens) &mdash; *no se necesita ninguna funcionalidad para el seguimiento espacial general de los auriculares* | 
|  Web  |  Fotocaptura y videocaptura | 
|  PicturesLibrary/VideosLibrary  |  Fotocaptura o videocaptura, respectivamente (al almacenar el contenido capturado) | 
|  Micrófono  |  VideoCapture (al capturar audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (y para usar el generador de perfiles de Unity) | 

### <a name="quality-settings"></a>Configuración de calidad

HoloLens tiene una GPU de clase móvil. Si su aplicación tiene como destino HoloLens, querrá que la configuración de calidad de la aplicación se ajuste para obtener un rendimiento más rápido para asegurarse de que mantiene la velocidad de fotogramas completa:

1. Seleccione **editar > configuración del proyecto > calidad**
2. Seleccione la **lista desplegable** en el logotipo de la **tienda Windows** y seleccione **muy baja**. Sabrá que la configuración se aplica correctamente cuando el cuadro de la columna de la tienda Windows y la fila **muy baja** es verde.
3. En la sección **Shadows** , seleccione **deshabilitar sombras** .

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con la sección configuración de calidad resaltada](images/wmr-config-img-10.png)<br>
*Configuración de calidad de Unity*

## <a name="per-scene-settings"></a>Configuración por escena

### <a name="unity-camera-settings"></a>Configuración de la cámara de Unity

Con la **realidad virtual compatible** activada, el componente de [cámara Unity](camera-in-unity.md) controla el [seguimiento de los cabezales y la representación Stereoscopic](../platform-capabilities-and-apis/rendering.md). Esto significa que no es necesario reemplazar el objeto de cámara principal por una cámara personalizada.

Si su aplicación tiene como destino HoloLens específicamente, debe cambiar algunas opciones de configuración para optimizar las pantallas transparentes del dispositivo. Esta configuración permite que el contenido holográfica se muestre a través del mundo físico:

1. En la **jerarquía**, seleccione la **cámara principal** .
2. En el panel **Inspector** , establezca la **posición** de la transformación en **0, 0, 0** para que la ubicación del encabezado del usuario se inicie en el origen del mundo Unity.
3. Cambie las **marcas de borrado** a **color sólido**.
4. Cambie el color de **fondo** a **RGBA 0, 0, 0 y 0**. Los negros se representan como transparentes en HoloLens.
5. Cambiar los **planos de recorte, cerca** de [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).

![Captura de pantalla de la pestaña inspector abierta en el editor de Unity](images/wmr-config-img-11.png)<br>
*Configuración de la cámara de Unity*

> [!IMPORTANT]
> Si elimina y crea una nueva cámara, asegúrese de que la nueva cámara esté etiquetada como **MainCamera**.

## <a name="next-steps"></a>Pasos siguientes

Ahora que el proyecto está listo, puede empezar a desarrollar su experiencia de realidad mixta:

* Agregar [bloques de creación principales](unity-development-overview.md#2-core-building-blocks)
* Consulte las [funcionalidades de la plataforma y las API](unity-development-overview.md#3-platform-capabilities-and-apis) disponibles
* Obtener información sobre cómo [implementar la aplicación](../platform-capabilities-and-apis/using-visual-studio.md#deploying-an-app-to-your-local-pc---immersive-headset)
* Usar el [simulador de realidad mixta](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](../install-the-tools.md)