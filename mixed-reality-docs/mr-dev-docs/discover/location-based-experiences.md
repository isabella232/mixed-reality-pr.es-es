---
title: Entretenimiento basado en la ubicación con Windows Mixed Reality
description: 'Obtenga información sobre Windows Mixed Reality para el entretenimiento basado en la ubicación: hardware, equipos portátiles, seguimiento, configuración y soporte técnico.'
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: mixed reality, vr, lbe, location, mixed reality headset, windows mixed reality headset, virtual reality headset, hardware, HoloLens, multi-player, cloud services, azure
ms.openlocfilehash: e9cff1184ca60f4b64be5346a187666e7b401aab06fee87c179917e300aa07f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196789"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Entretenimiento basado en la ubicación con Windows Mixed Reality

En los últimos dos años, hemos visto una cantidad increíble de crecimiento e innovación en la categoría De entretenimiento basado en la ubicación. Los lugares tradicionales, como los lugares de música y los cines, han empezado a ofrecer experiencias envolventes y multi player como experiencias complementarios a las instalaciones y carreras existentes. Los nuevos operadores y lugares están llevando experiencias únicas de varios reproductores y multi player a un precio atractivo para las masas. Todas estas experiencias están presionando el sobre para lo que es posible con la realidad mixta.

Este documento es una guía para empezar a trabajar con Windows Mixed Reality categoría Entretenimiento basado en la ubicación. Las instrucciones siguientes también pueden ser aplicables a experiencias basadas en la ubicación más allá del entretenimiento, como el entrenamiento, el diseño de productos y otros casos de uso.

## <a name="engineering-faq"></a>Preguntas más frecuentes sobre ingeniería

### <a name="hardware"></a>Hardware

**P: ¿Qué hardware está disponible de Microsoft y sus asociados que puedo usar en mi configuración?**

A. Microsoft y sus asociados OEM ofrecen una atractiva cartera de dispositivos entre los que elegir en función de sus necesidades.  

Si las experiencias que proporciona a los clientes requieren un casco de realidad virtual, los cascos en el mercado de HP, Samsung y Acer son una excelente opción. Cada casco tiene sus propios atributos diferenciados. Más detalles sobre cada uno de ellos a continuación.

HP Reverb: [Detalles](https://hp.com/go/Reverbpro)

Samsung Samsung Samsung+: [detalles](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [Detalles](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Si su ubicación se especializa en experiencias de realidad mixta o aumentada con cascos de consulta, consulte Microsoft HoloLens 2.  

HoloLens 2: [Interés de pedidos previos](https://www.microsoft.com//hololens/buy)

Si experimenta con experiencias que usan visión informática avanzada, voz y seguimiento corporal, Azure Kinect DK es una buena opción.  

Azure Kinect: [Detalles](https://azure.microsoft.com//services/kinect-dk/)

**P: ¿Cuál es la cartera de equipos portátiles que puedo usar para ejecutar mis experiencias de realidad virtual con tethered PC?**

Para las experiencias de REALIDAD virtual con tethered PC, nuestros OEM ofrecen una selección increíble de equipos portátiles diseñados exactamente para esa necesidad.

HP acaba de lanzar su hp vr con tecnología G2, el equipo portátil más eficaz del mundo, optimizado para experiencias de distribución libre, ahora con un 30 % más de potencia con una GPU RTX 2080 dentro. [Detalles](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Configurar

**P: ¿Cómo puedo configurar y personalizar más fácilmente el Portal de realidad mixta para LBE?**

>[!NOTE]
>Esta característica requiere la versión 2000.19061.1011.0 o posterior.  

Es posible que necesite más personalización de Portal de realidad mixta de la que está disponible normalmente a través de la aplicación para implementar aplicaciones en quioscos o experiencias personalizadas. La última actualización de julio de Portal de realidad mixta admite varias opciones avanzadas, que puede establecer a través de un archivo de configuración:  

Permitir comprobaciones del sistema con errores: normalmente, el proceso de instalación comprueba la compatibilidad del equipo Windows Mixed Reality antes de completar la instalación. Omitir las comprobaciones de compatibilidad puede causar problemas al intentar ejecutar Windows Mixed Reality si hay problemas de compatibilidad.  

Omitir aplicación complementaria de dispositivo: el DCA proporciona pasos de configuración específicos del casco proporcionados por el fabricante y permite actualizar el firmware del casco.  

Omitir la configuración de la sala: en lugar de que se le pida que cree un límite de sala, puede continuar directamente en el casco en modo Sentado/De pie.  

Omitir la instalación de aplicaciones desde la Tienda: el programa de instalación normal instala varias aplicaciones de la Tienda, incluidos Visor 3D y el complemento Visor de Edge 360. Esto omitirá la instalación de estas aplicaciones, pero es posible que falte la funcionalidad del dispositivo.  

Mostrar vista previa en pantalla completa: Portal de realidad mixta muestra de forma predeterminada la vista previa de los cascos en pantalla completa en el equipo de escritorio mientras el casco está en uso.  

Ocultar nuevo en el panel lateral: impide que el panel Nuevo para usted se expanda al iniciar Portal de realidad mixta.  

#### <a name="how-to-configure"></a>Cómo se configura:  

Para establecer cualquiera de estas configuraciones, debe crear un archivo denominado _UserConfig.js_ en en este directorio: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState \\_

Para la mayoría de los usuarios, tendrá el siguiente aspecto: _C:\Users \<username> \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState \\_

El archivo JSON debe tener el siguiente contenido con el valor "true" establecido para cualquiera de las configuraciones anteriores que desee habilitar:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**P: ¿Hay alguna guía sobre cómo configurar el espacio de juego?**

A. La configuración de un espacio de juego debe realizarse como lo haría con una experiencia de configuración del consumidor. El proceso de configuración de la sala también le permitirá definir los límites de la sala. Puede leer más detalles sobre cómo configurar los límites de la sala [aquí.](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)

Como se describe en el documento anterior, el espacio de juego de coordenadas única máximo razonable es de aproximadamente 5mx5 m. Si desea tener un área más grande, puede usar la funcionalidad Spatial Anchors en la Windows de Holographic API. El uso de esta API requerirá ingeniería personalizada en las experiencias que se producen.  

Puede leer más detalles sobre cómo optimizar el contenido para diferentes tamaños de espacio [aquí.](/windows/mixed-reality/coordinate-systems)
 

**P: Mi espacio es demasiado grande y se producen errores al intentar configurar una experiencia permanente con límites. ¿Qué debo hacer para configurar mi trabajo de gran experiencia de free-roam?**

A. Para configurar un espacio mayor que ~18 x 18ft, no se puede usar la experiencia de límite proporcionada por el sistema.  Los sistemas de límites se basan en un único "delimitador" de coordenada fija, que puede volverse inestable cuando un usuario está demasiado lejos del delimitador de la fase central. 

Puede configurar el modo "asentado", que no mostrará el límite ni configurará límites de fase o espacio de juego.  Deberá configurar varios anclajes espaciales dentro de la aplicación para hacer referencia a áreas de límite físico. 

El desarrollador de aplicaciones es responsable de mostrar las medidas de seguridad necesarias para que los usuarios no entren en colisión con el entorno físico.  Podrían ser paredes digitales dentro de la experiencia o un objeto visual de límite de juego personalizado. 

Puede encontrar instrucciones sobre cómo configurar el límite de la sala con WMR [aquí.](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)

**P: ¿Dónde está el origen del espacio de juego?**

A. El origen del espacio de juego viene determinado por la experiencia de configuración de la sala, más específicamente la posición de HMD cuando se presiona el botón Centro durante la instalación. 

### <a name="multi-player-setup"></a>CONFIGURACIÓN DE VARIOS REPRODUCTORES

**P: Estoy implementando una experiencia de varios reproductores en mi ubicación. ¿Es compatible con Windows Mixed Reality?**

A. Si participa en la compilación Windows 20H1 o posterior a través de nuestro programa Insider, puede acceder a una nueva interfaz para compartir mapas. Esta nueva funcionalidad está disponible a través de la interfaz [del](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) Administrador de mapas del portal Windows dispositivos. Para usar esta herramienta, siga estos pasos:
* Asegúrese de que ha optado por participar en 20H1 o posterior: después de septiembre de 2019, esto significa usar nuestro programa Insider.
* Habilite el Windows Portal de dispositivos (WDP) con estas [instrucciones.](/windows/uwp/debug-test-perf/device-portal-desktop)
* Conecte un Windows Mixed Reality HMD desde el que quiera descargar un mapa existente o importar uno nuevo.
* Vaya al WDP en el explorador que prefiera con la dirección URL proporcionada en la pantalla de configuración.
    * Una vez allí, vaya a la sección "Mixed Reality" y seleccione "Map Manager".
    * Ahora puede usar el botón "Descargar" para exportar un mapa existente desde la máquina.
    * Puede usar el botón "Upload archivo de mapa" para importar un mapa de una exportación anterior (quizás en otro equipo).
    * Puede usar "Importar" para permitir que el sistema use ese mapa para este HMD en esta máquina.

> [!NOTE] 
> Anteriormente, era posible usar la herramienta Spatial Data Packager; sin embargo, esa herramienta se publicó originalmente como no compatible y ahora está oficialmente en desuso y ya no funciona en 20H1. En su lugar, use la herramienta [Administrador de mapas de bandeja de](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) entrada como se describió anteriormente. 

### <a name="tracking"></a>Seguimiento

P: ¿Cómo funciona la tecnología de seguimiento en Windows Mixed Reality cascos?  

Mixed Reality comparte la misma tecnología de seguimiento que el HoloLens. Para obtener más información sobre el sistema de seguimiento interno, consulte la documentación [aquí.](/windows/mixed-reality/enthusiast-guide/tracking-system)

Para obtener una descripción de cómo funciona el sistema de asignación espacial de nivel superior, puede leer nuestra descripción [aquí.](../design/spatial-mapping.md)

**P: ¿Existen procedimientos recomendados para obtener un volumen de seguimiento confiable?**

Para configurar mejor el entorno para realizar el seguimiento correcto, puede leer los procedimientos recomendados en esta [publicación.](/hololens/hololens-environment-considerations)

**P: ¿Hay algún matiz específico con el seguimiento en los espacios de escalado de almacenamiento o las optimizaciones que se deben tener en cuenta?**

A. Las siguientes prácticas pueden ayudar a obtener un volumen de seguimiento más confiable:  

Proporcionar características diferentes en la sala que se superponen en varias posiciones ayudará al sistema de seguimiento a obtener un bloqueo sólido. Piense en las superficies de pintura aleatorias y el sombreado en lugar de usar líneas de estilo de contorno sólidas. 

Minimice el intervalo dinámico de iluminación de su área siempre que sea posible. Las cámaras de seguimiento de Mixed Reality HMD no son HDR y tienen AGC (ganancia automática) y AEC (exposición automática) que se van a ocupar de una iluminación diferente. En función de la distribución de la luz, los patrones y el contraste de la superficie, AGC o AEC pueden concluir que se encuentra en una sala totalmente blanca o negra, que puede despuntar con las características que pueden estar en el "color" opuesto. Si intenta tomar una imagen interior delante de una ventana exterior con una luz de verano brillante detrás y ajusta la exposición para que pueda ver los detalles fuera, todo el interior está infraexplogado y negro. O bien, si se establece para dentro, todo lo que está fuera ahora está sobreexpuesto y todo en blanco.  

Destacados en una sala (incluso sobrecarga) que están a la vista si las cámaras de seguimiento a veces pueden ser responsables, lo que confunda el AEC/AGC de las cámaras de seguimiento. La iluminación plana o difusa ayuda.  

### <a name="mixed-reality-cloud-services-and-azure"></a>MIXED REALITY CLOUD SERVICES Y AZURE 

**P: ¿Cómo puede Microsoft Azure mi escala empresarial?**

A. La administración remota y local basada en Azure puede ayudar a su empresa a controlar los datos, reducir los costos operativos y escalar la implementación en ubicaciones nuevas y existentes. Los servicios en la nube de Azure como Azure Storage, Azure Functions, App Service, Redes de Azure e IOT Hub pueden ayudar con los siguientes casos de uso:  

Remote Device Deployment & Management 

Real-Time Onsite Analytics 

Juego de LBE adaptable inteligente 

Streaming e implementación de contenido LBE 

Mapa térmico de preferencias de jugador LBE 

Sistema de reservas y reservas LBE 

**P: Estoy desarrollando un MMATRIZ espacial para implementar en una superficie masiva. ¿Algún servicio que me ayude a administrar mi contenido y persistencia de objetos?**

A. Azure Spatial Anchors es un nuevo servicio de Mixed Reality que permite experiencias de realidad mixta con múltiples usuarios y con conocimiento espacial en HoloLens, iOS y Android. Puede obtener más información sobre Azure Spatial Anchors [aquí.](https://azure.microsoft.com//services/spatial-anchors/)

**Q. Nuestro lugar se especializa en experiencias de varios reproductores y me gustaría centrar nuestro tiempo de desarrollo en contenido y desarrollo de front-end. ¿Hay ofertas que puedan ayudarme a arrancar o descargar el desarrollo de back-end?**

A. Azure PlayFab es una plataforma de back-end completa para juegos en directo. Puede obtener más información al respecto [aquí.](https://playfab.com/)

### <a name="misc"></a>Varios

**P: Uso SteamVR para implementar mis experiencias. ¿Windows Mixed Reality funciona con SteamVR?**

R: Windows Mixed Reality para SteamVR permite a los usuarios ejecutar experiencias de SteamVR Windows Mixed Reality cascos envolventes. Obtenga más información sobre SteamVR con WMR [aquí.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

### <a name="support-and-community"></a>Soporte técnico y comunidad  

Tenemos algunos recursos útiles para ayudarle a interactuar con expertos en la materia de nuestro equipo, obtener soporte técnico para la solución de problemas y contribuir a la comunidad de desarrollo de realidad mixta más amplia.  

Si tiene problemas con las características publicadas públicamente, presente un error mediante Centro de opiniones.Para obtener instrucciones, consulte esta [página](/windows/mixed-reality/enthusiast-guide/filing-feedback).

Para obtener otra ayuda para solucionar problemas con WMR, abra una solicitud [de soporte técnico](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) a nuestro equipo de soporte técnico al cliente.

Únase a nuestro canal holodevelopers de Slack para interactuar con los desarrolladores de realidad mixta y los expertos en la materia: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: siga nuestro equipo de Mixed Reality developer Relations para obtener noticias, eventos y actualizaciones. @MxdRealityDev 

Si se encuentra dentro o alrededor de San Francisco, siempre sucede algo en Microsoft Reactor. Puede ver nuestro calendario de eventos [aquí.](https://developer.microsoft.com//reactor/Location/San%20Francisco)
