---
title: Uso de Vuforia con Unity
description: Use Vuforia para compilar Windows Mixed Reality aplicaciones en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, marcadores, coordenadas, marco de referencia, seguimiento, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, unity, HoloLens, seguimiento de dispositivos, modo de rendimiento, Vuforia Portal para desarrolladores
ms.openlocfilehash: 1a21f4bb441a1ab0706b5916feaac0d691486626
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232175"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso de Vuforia Engine con Unity

Vuforia Engine ofrece una funcionalidad importante para HoloLens: la capacidad de conectar experiencias de AR a imágenes y objetos específicos del entorno. Puede usar esta funcionalidad para superponer instrucciones paso a paso guiadas sobre maquinaria para la empresa industrial o agregar características digitales y experiencias a un producto físico o juego.

Vuforia Engine ofrece una amplia gama de características y destinos para que el proceso de desarrollo de AR sea más flexible. Una de nuestras características más nuevas, Objetivos de modelo de Vuforia, es una funcionalidad clave para usos comerciales e industriales. Los destinos de modelo permiten a las aplicaciones reconocer objetos físicos como máquinas, automóviles o juguetes y realizar un seguimiento de ellos en función de un modelo CAD o 3D digital. Para usos industriales, esta característica puede proporcionar a los trabajadores de ensamblado y a los técnicos de servicio instrucciones de trabajo de AR e instrucciones de procedimientos mientras están en la fábrica o fuera del campo.

Las aplicaciones de Vuforia Engine existentes que se crearon para teléfonos y tabletas se pueden configurar fácilmente en Unity para que se ejecuten HoloLens. Incluso puede usar Vuforia Engine para llevar la nueva aplicación de HoloLens a Windows 10 tabletas como Surface Pro y Surface Book.


## <a name="get-the-tools"></a>Obtener las herramientas

[Instale las versiones recomendadas](../install-the-tools.md) de Visual Studio y Unity y, a continuación, configure Unity para que use Visual Studio el IDE y el compilador preferidos. 

Al instalar Unity, asegúrese de instalar el "back-end de scripting Windows IL2CPP".

Agregue el paquete del motor de Vuforia como se describe [aquí.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html).

## <a name="getting-started-with-vuforia-engine"></a>Introducción a Vuforia Engine

El mejor punto de partida para aprender sobre El motor de Vuforia y HoloLens es el ejemplo de HoloLens del motor de [Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponible en el almacén de recursos de Unity). El ejemplo proporciona un proyecto de HoloLens completo que incluye escenas preconfiguradas que se pueden implementar en un HoloLens.

En las escenas se muestra cómo usar Los destinos de imagen de Vuforia para reconocer una imagen y aumentarla con contenido digital en HoloLens experiencia. El ejemplo de HoloLens del motor de Vuforia también incluye una escena que muestra el uso de destinos de modelo y VuMarks en HoloLens. Puede sustituir fácilmente su propio contenido en escenas para experimentar con la creación de HoloLens aplicaciones que usan Vuforia Engine.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Configuración de una aplicación de Vuforia para HoloLens

Desarrollar una aplicación de Vuforia Engine para HoloLens es fundamentalmente lo mismo que desarrollar aplicaciones de Vuforia Engine para otros dispositivos. A continuación, puede aplicar las configuraciones y la configuración de compilación que se describen en la sección siguiente. Eso es todo lo que se necesita para permitir que Vuforia Engine funcione con los sistemas HoloLens asignación espacial y seguimiento posicional.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilación y ejecución del ejemplo de motor de Vuforia para HoloLens
1.  Descargue el [ejemplo del motor de Vuforia para HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) desde el Almacén de recursos de Unity
2.  Aplicación de las [opciones recomendadas del motor de Unity para la potencia y el rendimiento](performance-recommendations-for-unity.md)
3.  Agregue las escenas de ejemplo a **Escenas** en **la compilación.**
4.  En **Compilar Configuración**, cambie la plataforma de compilación a **UWP** haciendo clic en **el botón Agregar escenas abiertas.**
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  Seleccione el **botón Player Configuración** (Reproductor).  
   * Seleccione el **icono de UWP** y expanda **la Configuración XR.**
   * Asegúrese de **que Virtual Reality Supported está** habilitado.    
   * En **SDK de realidad virtual,** asegúrese de que:
     * **El Mixed Reality** se incluye en la lista y habilitar el uso compartido **del búfer** de profundidad está habilitado. 
     * El **formato de** profundidad se establece en una profundidad de **16 bits.** 
   * Asegúrese de que **el modo de representación estéreo** está establecido en Instancia de paso **único.**
6.  Expanda la **sección Configuración** publicación.
   * En **Funcionalidades,** asegúrese de que está seleccionada la opción **Cliente de Internet, WebCam, Micrófono** y **SpatialPerception.**
   * **NOTA: SpatialPerception** solo debe seleccionarse si piensa usar Surface Observer API.
   * En **Supported Device Families (Familias de dispositivos compatibles),** asegúrese **de que Holographic** esté seleccionado. 
7.  Expanda la **sección Resolución y** presentación.
   * **Deshabilite Ejecutar** en segundo plano para que El motor de Vuforia se detenga cuando la aplicación se ponga en segundo plano y pueda acceder de nuevo a la cámara cuando se reanude la aplicación. 
   * En la **lista desplegable Orientación predeterminada,** asegúrese de que **horizontal izquierda** está seleccionado.
8.  Vuelva a la **ventana Build Configuración** (Compilar) y seleccione Build **(Compilar)** para generar Visual Studio proyecto.
9.  Compile el archivo ejecutable Visual Studio e instállo en el HoloLens.

## <a name="the-vuforia-developer-portal"></a>El Portal para desarrolladores Vuforia

Los desarrolladores que buscan crear sus propias experiencias de AR con Vuforia Engine y HoloLens deben registrarse en nuestro Portal para desarrolladores vuforia [en developer.vuforia.com](https://developer.vuforia.com/). En el portal, los desarrolladores tienen acceso [a](https://library.vuforia.com/) los foros de [Vuforia Engine,](https://developer.vuforia.com/forum) donde pueden unirse a los debates de la comunidad, una biblioteca con documentación detallada sobre todas las características del motor de Vuforia y el Administrador de destinos de [Vuforia,](https://developer.vuforia.com/target-manager) donde los usuarios pueden crear sus propios destinos personalizados. Los desarrolladores también pueden registrarse para obtener una licencia de desarrollador gratuita mediante el Administrador de [licencias de Vuforia](https://developer.vuforia.com/license-manager).

## <a name="device-tracking-with-vuforia"></a>Seguimiento de dispositivos con Vuforia

[Device Tracking](https://library.vuforia.com/features/environments/device-tracker-overview.html) mantiene el seguimiento incluso cuando un destino ya no está en la vista. Se habilita automáticamente para todos los destinos cuando el seguimiento de dispositivos posicionales está habilitado. Para HoloLens aplicaciones, el seguimiento de dispositivos posicionales se inicia automáticamente en Unity.

El motor de Vuforia fusiona automáticamente las poses del seguimiento de la cámara y el seguimiento espacial de HoloLens para proporcionar poses de destino estables, independientemente de si la cámara ve o no el objetivo.

Puesto que el proceso se controla automáticamente, no requiere ninguna programación por parte del desarrollador.


**A continuación se muestra una descripción de alto nivel del proceso:**
1. El rastreador de destino de Vuforia reconoce el destino
2. A continuación, se inicializa el seguimiento de destino
3. La posición y la rotación del destino se analizan para proporcionar una estimación de posición sólida para el HoloLens
4. El motor de Vuforia transforma la posición del destino en el espacio de coordenadas HoloLens asignación espacial
5. HoloLens se encarga del seguimiento si el destino ya no está en la vista. Cada vez que vuelva a mirar el destino, Vuforia seguirá haciendo un seguimiento preciso de las imágenes y los objetos.

Los destinos detectados, pero que ya no están a la vista, se notifican como EXTENDED_TRACKED. En estos casos, el script DefaultTrackableEventHandler que se usa en todos los destinos continúa representando el contenido de aumento. El desarrollador puede controlar este comportamiento implementando un script de controlador de eventos de seguimiento personalizado.

## <a name="performance-mode-with-vuforia-engine"></a>Modo de rendimiento con el motor de Vuforia 

Es posible a través del motor de Vuforia administrar el rendimiento en el HoloLens en la extensión de las experiencias de AR y reducir la carga de trabajo en la CPU. El motor de Vuforia ofrece tres modos que se pueden seleccionar: predeterminado, para optimizar la velocidad y para optimizar la calidad. 

*   MODE_OPTIMIZE_SPEED permite minimizar la carga de trabajo en HoloLens dispositivo y es excelente para ampliar las experiencias de AR. Se recomienda para situaciones en las que la aplicación está siguiendo objetos o destinos estáticos.
*   MODE_DEFAULT es el modo normal, que se puede usar en la mayoría de los escenarios.
*   MODE_OPTIMIZE_QUALITY es mejor para realizar el seguimiento de destinos móviles o destinos de modelo que espera que se seleccionen.

**Establecimiento del modo**

Para cambiar el modo de rendimiento en Unity, vaya a Configuración de Vuforia (Ctrl+Mayús+V / Cmd+Mayús+V) que se encuentra como un componente en arCamera GameObject. 
*   Seleccione el menú desplegable Modo de dispositivo de cámara y seleccione una de las tres opciones.


## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](../install-the-tools.md)
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* [Asignación espacial](../../design/spatial-mapping.md)
* [Cámara en Unity](camera-in-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentación de Vuforia: Tareas iniciales con Vuforia Engine for Windows 10 Development](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Documentación de Vuforia: Tareas iniciales con Vuforia Engine en Unity](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [Documentación de Vuforia: Trabajo con el ejemplo HoloLens en Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Documentación de Vuforia: Seguimiento de dispositivos en Vuforia](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Documentación de Vuforia: Velocidad de fotogramas y optimización del rendimiento](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
