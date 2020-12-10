---
title: Uso de Vuforia con Unity
description: Use Vuforia para compilar aplicaciones de Windows Mixed Reality en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, marcadores, coordenadas, fotogramas de referencia, seguimiento, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, Unity, HoloLens, seguimiento de dispositivos, modo de rendimiento, portal para desarrolladores de Vuforia
ms.openlocfilehash: ecacf4036bfab38eb90782a194c445a83ca623ba
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010566"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso del motor Vuforia con Unity

El motor de Vuforia ofrece una funcionalidad importante para HoloLens: la capacidad de conectar experiencias de AR a imágenes y objetos específicos del entorno. Puede usar esta capacidad para superponer instrucciones paso a paso guiadas sobre maquinaria para la empresa industrial o para agregar características y experiencias digitales a un producto o juego físico.

El motor de Vuforia ofrece una amplia gama de características y destinos para que el proceso de desarrollo de AR sea más flexible. Una de nuestras características más recientes, objetivos del modelo Vuforia, es una capacidad clave para los usos comerciales y industriales. Los destinos de modelo permiten a las aplicaciones reconocer objetos físicos, como máquinas, automóviles o juguetes, y realizar un seguimiento de ellos según un modelo 3D de CAD o digital. En el caso de los usos industriales, esta característica puede proporcionar a los trabajadores de ensamblados y a los técnicos de servicios las instrucciones de trabajo de AR y la guía de procedimientos en la fábrica o en el campo.

Las aplicaciones de Vuforia Engine existentes que se compilaron para teléfonos y tabletas se pueden configurar fácilmente en Unity para que se ejecuten en HoloLens. Incluso puede usar el motor Vuforia para realizar la nueva aplicación de HoloLens en tabletas con Windows 10, como el libro de Surface Pro y Surface.


## <a name="get-the-tools"></a>Obtener las herramientas

[Instale las versiones recomendadas](../install-the-tools.md) de Visual Studio y Unity y, después, configure Unity para usar Visual Studio y el IDE y el compilador preferidos. 

Al instalar Unity, asegúrese de instalar el "back-end de scripting de la tienda Windows IL2CPP".

Agregue el paquete del motor Vuforia tal como se describe [aquí.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)

## <a name="getting-started-with-vuforia-engine"></a>Introducción al motor de Vuforia

El mejor punto de partida para aprender sobre el motor de Vuforia y HoloLens es el [ejemplo de hololens del motor de Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponible en el almacén de recursos de Unity). El ejemplo proporciona un proyecto de HoloLens completo que incluye escenas preconfiguradas que se pueden implementar en HoloLens.

Las escenas muestran cómo usar los destinos de imagen de Vuforia para reconocer una imagen y aumentarla con contenido digital en una experiencia de HoloLens. El ejemplo de HoloLens del motor de Vuforia también incluye una escena que muestra el uso de los destinos del modelo y VuMarks en HoloLens. Puede sustituir fácilmente su propio contenido en segundo plano para experimentar con la creación de aplicaciones de HoloLens que usan el motor de Vuforia.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Configuración de una aplicación de Vuforia para HoloLens

El desarrollo de una aplicación de motor de Vuforia para HoloLens es fundamentalmente el mismo que el desarrollo de aplicaciones de motor de Vuforia para otros dispositivos. Después, puede aplicar la configuración de compilación y las configuraciones que se describen en la sección siguiente. Eso es todo lo que se necesita para permitir que el motor de Vuforia funcione con la asignación espacial de HoloLens y los sistemas de seguimiento posicional.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilación y ejecución del ejemplo de Vuforia Engine para HoloLens
1.  Descargar el [ejemplo de Vuforia Engine para HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) del almacén de recursos de Unity
2.  Aplicar las [Opciones de motor de Unity recomendadas para potencia y rendimiento](performance-recommendations-for-unity.md)
3.  Agregue escenas de ejemplo a **escenas** en la **compilación.**
4.  En **configuración de compilación**, cambie crear plataforma a **UWP** haciendo clic en el botón **Agregar escenas abiertas** .
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  Seleccione el botón **configuración del reproductor** .  
   * Seleccione el icono de **UWP** y expanda la sección **configuración de XR** .
   * Asegúrese de que la **realidad virtual compatible** está habilitada.    
   * En **SDK de realidad virtual** , asegúrese de que:
     * **Window Mixed Reality** está incluido en la lista y habilitado el uso compartido de **búfer de profundidad** . 
     * El **formato de profundidad** se establece en **una profundidad de 16 bits.** 
   * Asegúrese de que el **modo de representación estéreo** está establecido en **instancia de paso único.**
6.  Expanda la sección **configuración de publicación** .
   * En **capacidades** , asegúrese de que esté seleccionado **cliente de Internet, cámara web, micrófono** y **SpatialPerception** .
   * **Nota: SpatialPerception** solo debe seleccionarse si tiene previsto usar la API de la superficie de observador.
   * En **familias de dispositivos compatibles**, asegúrese de que **Holographic** esté seleccionado. 
7.  Expanda la sección **resolución y presentación** .
   * Deshabilite la **ejecución en segundo plano** para que el motor de Vuforia se ponga en pausa cuando la aplicación esté en segundo plano y pueda acceder a la cámara de nuevo cuando se reanude la aplicación. 
   * En la lista desplegable **orientación predeterminada** , asegúrese de que está seleccionado **horizontalmente** a la izquierda.
8.  Vuelva a la ventana **configuración de compilación** y seleccione **compilar** para generar un proyecto de Visual Studio.
9.  Compile el archivo ejecutable desde Visual Studio e instálelo en HoloLens.

## <a name="the-vuforia-developer-portal"></a>Portal para desarrolladores de Vuforia

Los desarrolladores que quieran crear sus propias experiencias de AR con el motor de Vuforia y HoloLens deben registrarse en nuestro portal para desarrolladores de Vuforia en [Developer.Vuforia.com](https://developer.vuforia.com/). En el portal, los desarrolladores tienen acceso a los [foros del motor de Vuforia](https://developer.vuforia.com/forum) , donde pueden unirse a discusiones de la comunidad, una [biblioteca](https://library.vuforia.com/) con documentación detallada sobre todas las características del motor de Vuforia y el administrador de [destino de Vuforia](https://developer.vuforia.com/target-manager) , donde los usuarios pueden crear sus propios destinos personalizados. Los desarrolladores también pueden registrarse para obtener una licencia de desarrollador gratuita mediante el [Administrador de licencias de Vuforia](https://developer.vuforia.com/license-manager).

## <a name="device-tracking-with-vuforia"></a>Seguimiento de dispositivos con Vuforia

El [seguimiento de dispositivos](https://library.vuforia.com/features/environments/device-tracker-overview.html) mantiene el seguimiento incluso cuando un destino ya no está en la vista. Se habilita automáticamente para todos los destinos cuando está habilitado el seguimiento de dispositivos posicionales. En el caso de las aplicaciones de HoloLens, el seguimiento de dispositivos posicionales se inicia automáticamente en Unity.

El motor de Vuforia funde automáticamente las supuestos del seguimiento de la cámara y el seguimiento espacial de HoloLens para proporcionar un objetivo estable con independencia de si el destino es visible o no en la cámara.

Dado que el proceso se controla automáticamente, no es necesario que el desarrollador lo programe.


**La siguiente es una descripción de alto nivel del proceso:**
1. El rastreador de destino de Vuforia reconoce el destino
2. A continuación, se inicializa el seguimiento de destino
3. La posición y la rotación del destino se analizan para proporcionar una estimación de postura sólida para HoloLens
4. El motor de Vuforia transforma la postura del destino en el espacio de coordenadas de asignación espacial de HoloLens
5. HoloLens realiza el seguimiento si el destino ya no está en la vista. Siempre que vuelva a mirar el destino, Vuforia continuará realizando el seguimiento de las imágenes y los objetos con precisión.

Los destinos que se detectan, pero que ya no están en la vista, se muestran como EXTENDED_TRACKED. En estos casos, el script DefaultTrackableEventHandler que se usa en todos los destinos continúa representando el contenido de aumento. El desarrollador puede controlar este comportamiento implementando un script de controlador de eventos de seguimiento personalizado.

## <a name="performance-mode-with-vuforia-engine"></a>Modo de rendimiento con el motor de Vuforia 

Es posible a través del motor de Vuforia administrar el rendimiento de HoloLens para obtener las experiencias de AR y reducir la carga de trabajo en la CPU. El motor de Vuforia ofrece tres modos que se pueden seleccionar: predeterminado, para optimizar la velocidad y para optimizar la calidad. 

*   MODE_OPTIMIZE_SPEED le permite minimizar la carga de trabajo en el dispositivo HoloLens y es ideal para ampliar las experiencias de AR. Se recomienda en situaciones en las que la aplicación realiza el seguimiento de objetos o destinos estáticos.
*   MODE_DEFAULT es el modo normal, que se puede usar en la mayoría de los escenarios.
*   MODE_OPTIMIZE_QUALITY es mejor para realizar un seguimiento de los destinos móviles o los destinos de modelo que espera que se recojan.

**Establecer el modo**

Para cambiar el modo de rendimiento en Unity, vaya a configuración de Vuforia (Ctrl + Mayús + V/Cmd + Mayús + V) que se encuentra como componente en el GameObject de ARCamera. 
*   Seleccione el menú desplegable para el modo de dispositivo de cámara y seleccione una de las tres opciones.


## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](../install-the-tools.md)
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* [Asignación espacial](../../design/spatial-mapping.md)
* [Cámara en Unity](camera-in-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentación de Vuforia: desarrollo para Windows 10 en Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentación de Vuforia: instalación de la extensión Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentación de Vuforia: trabajar con el ejemplo de HoloLens en Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentación de Vuforia: seguimiento de dispositivos en Vuforia](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Documentación de Vuforia: velocidad de fotogramas y optimización del rendimiento](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
