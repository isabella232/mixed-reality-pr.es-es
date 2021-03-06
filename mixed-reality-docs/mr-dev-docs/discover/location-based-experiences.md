---
title: Entretenimiento basado en la ubicación con Windows Mixed Reality
description: 'Obtenga información sobre Windows Mixed Reality para entretenimiento basado en ubicación: hardware, equipos Backpack, seguimiento, configuración y soporte técnico.'
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: realidad mixta, VR, LBE, ubicación, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, hardware, HoloLens, varios jugadores, servicios en la nube, Azure
ms.openlocfilehash: 49e96b99d3f74bd24a4a0e71f212018108148ad2
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236916"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Entretenimiento basado en la ubicación con Windows Mixed Reality

En el último par de años, hemos visto una cantidad increíble de crecimiento e innovación en la categoría de ocio basada en la ubicación. Los lugares tradicionales, como los parques de tema y los cines, han empezado a ofrecer experiencias envolventes y multijugador como experiencias gratuitas en instalaciones e instalaciones existentes. Los nuevos operadores y lugares aportan experiencias únicas de varios jugadores y multisensorial a un precio atractivo para las masas. Todas estas experiencias están empujando el sobre en lo que es posible con la realidad mixta.

Este documento es una guía para empezar a trabajar con Windows Mixed Reality en la categoría de entretenimiento basada en la ubicación. Las instrucciones siguientes pueden aplicarse además a experiencias basadas en la ubicación más allá del entretenimiento, como el entrenamiento, el diseño del producto y otros casos de uso.

## <a name="engineering-faq"></a>Preguntas más frecuentes sobre ingeniería

### <a name="hardware"></a>Hardware

**P: ¿Qué hardware está disponible en Microsoft y sus asociados que puedo usar en mi instalación?**

R: Microsoft y sus asociados OEM ofrecen una amplia cartera de dispositivos para elegir en función de sus necesidades.  

Si las experiencias que va a proporcionar a sus clientes requieren un casco de realidad virtual, los auriculares en el mercado de HP, Samsung y Acer son una buena opción. Cada casco tiene sus propios atributos diferenciados. Más información sobre cada uno de ellos.

HP reverberación: [detalles](https://hp.com/go/Reverbpro)

Samsung Odyssey +: [detalles](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [detalles](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Si su ubicación se especializa en experiencias de realidad enriquecidas o aumentadas con auriculares de información, consulte Microsoft HoloLens 2.  

HoloLens 2: [interés previo al pedido](https://www.microsoft.com//hololens/buy)

Si está experimentando con experiencias que usan Advanced Computer Vision, voz y seguimiento de cuerpos, el sensor de Azure de Kinect DK es una buena opción.  

Azure Kinect: [detalles](https://azure.microsoft.com//services/kinect-dk/)

**P: ¿Cuál es la cartera de equipos Backpack que puedo usar para ejecutar las experiencias de VR con tethering PC?**

En el caso de las experiencias de VR con tethering de PC, nuestros OEM ofrecen una increíble selección de equipos de mochila creados exactamente para esa necesidad.

HP acaba de lanzar su mochila de HP VR de la versión G2, el equipo portátil más eficaz del mundo, optimizado para experiencias de movilidad gratuita, ahora con un 30% más de energía con una GPU de RTX 2080 dentro de. [Detalles](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Configurar

**P: ¿Cómo puedo configurar más fácilmente el programa de instalación y personalizar el portal de realidad mixta para LBE?**

>[!NOTE]
>Esta característica requiere la versión 2000.19061.1011.0 o posterior.  

Es posible que necesite más personalización del portal de realidad mixta que normalmente está disponible a través de la aplicación para la implementación de aplicaciones en quioscos o experiencias personalizadas. La actualización más reciente de julio del portal de realidad mixta admite varias configuraciones avanzadas, que se pueden establecer a través de un archivo de configuración:  

Permitir comprobaciones del sistema con error: normalmente, el proceso de instalación comprueba si el equipo es compatible con Windows Mixed Reality antes de completar la instalación. Omitir las comprobaciones de compatibilidad puede producir problemas al intentar ejecutar Windows Mixed Reality si hay problemas de compatibilidad.  

Omitir aplicación complementaria de dispositivo: el DCA proporciona pasos de configuración específicos del casco que proporciona el fabricante y permite actualizar el firmware del casco.  

Omitir configuración de la habitación: en lugar de que se le pida que cree un límite de habitación, puede continuar directamente con el casco en el modo sentado/permanente.  

Omitir la instalación de aplicaciones desde la tienda: el programa de instalación normal instala varias aplicaciones de la tienda, como el visor 3D y el complemento Edge 360 Viewer. Se omitirá la instalación de estas aplicaciones, pero es posible que falte funcionalidad de dispositivo.  

Mostrar vista previa en pantalla completa: el portal de realidad mixta mostrará de forma predeterminada la vista previa del casco en la pantalla completa en el equipo de escritorio mientras el casco está en uso.  

Ocultar nuevo en el panel lateral: impide que el panel nuevo en su panel se expanda al iniciar el portal de realidad mixta.  

#### <a name="how-to-configure"></a>Cómo se configura:  

Para establecer cualquiera de estas configuraciones, debe crear un archivo llamado _UserConfig.jsen en_ este directorio: _\\ $env: localappdata\packages\ Microsoft.MixedReality.Portal_8wekyb3d8bbwe \localstate_

Para la mayoría de los usuarios, tendrá el siguiente aspecto: _C:\Users \<username> \Appdata\local\packages\ Microsoft.mixedreality.portal_8wekyb3d8bbwe \localstate \\_

El archivo JSON debe tener el siguiente contenido con el valor "true" establecido para cualquiera de las opciones anteriores que desee habilitar:  

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
 
**P: ¿hay alguna orientación sobre la configuración de Playspace?**

R: la configuración de un Playspace debe realizarse tal como lo haría con una experiencia de instalación del consumidor. El proceso de configuración del salón también le permitirá definir los límites de la habitación. Puede leer [aquí](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)más detalles sobre la configuración de los límites de la habitación.

Como se explicó en el documento anterior, el Playspace de coordenada única razonable máximo está alrededor de 5mx5m. Si desea tener un área más grande, puede usar la capacidad de anclajes espaciales en la pila de la API de Windows Holographic. El uso de esta API requerirá ingeniería personalizada en las experiencias que está generando.  

Puede leer [aquí](/windows/mixed-reality/coordinate-systems)más detalles sobre cómo optimizar el contenido de los distintos tamaños de espacio.
 

**P: mi espacio es demasiado grande y se están ejecutando errores al intentar configurar una experiencia permanente con límites. ¿Qué debo hacer para configurar mi trabajo de gran experiencia de movilidad gratuita?**

R: para configurar un espacio mayor que ~ 18x18ft, no puede usar la experiencia de límite que proporciona el sistema.  Los sistemas de límites se basan en un único "delimitador de coordenadas fijas", que puede volverse inestable cuando un usuario está demasiado lejos del delimitador de la fase central. 

Puede configurar el modo "sentado", que no mostrará el límite ni configurará límites de fase o Playspace.  Tendrá que configurar varios delimitadores espaciales dentro de la aplicación para hacer referencia a áreas de límites físicos. 

El desarrollador de la aplicación es responsable de mostrar las medidas de seguridad necesarias para que los usuarios no entren en conflicto con el entorno físico.  Podrían ser paredes digitales dentro de la experiencia o un visual de límite de juego personalizado. 

Puede encontrar instrucciones sobre cómo configurar el límite de la habitación con WMR [aquí](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

**P: ¿Dónde está el origen de Playspace?**

R: el origen de Playspace viene determinado por la experiencia de instalación del salón, más específicamente la posición de HMD cuando se presiona el botón central durante la instalación. 

### <a name="multi-player-setup"></a>CONFIGURACIÓN DE VARIOS JUGADORES

**P: estoy implementando una experiencia de varios jugadores en mi lugar. ¿Es compatible con Windows Mixed Reality?**

R: Si opta por la compilación de Windows 20H1 o posterior a través de nuestro programa Insider, puede acceder a una nueva interfaz para el uso compartido de mapas. Esta nueva funcionalidad está disponible a través de la interfaz del [Administrador de mapas](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) del portal de dispositivos de Windows. Para usar esta herramienta, siga estos pasos:
* Asegúrese de que está suscrito a 20H1 o posterior: después del 2019 de septiembre, esto significa el uso de nuestro programa Insider
* Habilitar Windows Device portal (WDP) mediante estas [instrucciones](/windows/uwp/debug-test-perf/device-portal-desktop)
* Conecte una HMD de realidad mixta de Windows que quiera descargar una asignación existente desde o importar una nueva asignación.
* Navegue hasta el WDP en el explorador que prefiera mediante la dirección URL proporcionada en la pantalla Configuración.
    * Una vez que haya navegado a la sección "Mixed Reality" y seleccione "Administrador de mapas".
    * Ahora puede usar el botón "Descargar" para exportar una asignación existente desde la máquina.
    * Puede usar el botón "cargar un archivo de asignación" para importar un mapa de una exportación anterior (quizás en otro equipo).
    * Puede usar "importar" para permitir que el sistema use esa asignación para este HMD en este equipo.

> [!NOTE] 
> Anteriormente, era posible usar la herramienta del Empaquetador de datos espaciales; sin embargo, esa herramienta se lanzó originalmente como no compatible y ahora está en desuso y ya no funciona en 20H1. En su lugar, use la herramienta [Administrador de mapas](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) de bandeja de entrada como se describió anteriormente. 

### <a name="tracking"></a>LLEVAR

P: ¿Cómo funciona la tecnología de seguimiento de los auriculares Windows Mixed Reality?  

La realidad mixta comparte la misma tecnología de seguimiento que la HoloLens. Para obtener más información sobre el sistema de seguimiento interno, consulte la documentación [aquí](/windows/mixed-reality/enthusiast-guide/tracking-system).

Para obtener una descripción de cómo funciona el sistema de asignación espacial de nivel superior, puede leer nuestra descripción [aquí](../design/spatial-mapping.md).

**P: ¿existen procedimientos recomendados para obtener un volumen de seguimiento confiable?**

Para configurar mejor el entorno para el seguimiento correcto, puede leer los procedimientos recomendados en esta [publicación](/hololens/hololens-environment-considerations).

**P: ¿existen matices específicos con el seguimiento de los espacios de escala de almacenamiento o de las optimizaciones que se deben tener en cuenta?**

R: las siguientes prácticas pueden ayudarle a obtener un volumen de seguimiento más confiable:  

Proporcionar diferentes características en el salón que se superponen en varias posiciones ayudará al sistema de seguimiento a obtener un bloqueo sólido. Piense en la Splatters de pintura aleatoria y en el sombreado en lugar de usar líneas de estilo de contorno sólido. 

Minimice el intervalo dinámico de iluminación en el área donde sea posible. Las cámaras de seguimiento de nuestras HMDss de realidad mixta no son HDR y tienen AGC (ganancia automática) y AEC (exposición automática) para tratar con la iluminación diferente. En función de la distribución de la luz de superficie, los patrones y el contraste, el AGC o AEC pueden concluir que está en una habitación de todo el blanco o negro, lo que puede descolorar las características que pueden estar en el "color" opuesto. Si está intentando tomar una imagen interior delante de una ventana exterior con el horario de verano brillante y ajusta la exposición para que pueda ver los detalles fuera, todo el interior está subexpuesto y negro. O bien, si se establece para dentro de, todo lo que se encuentra fuera se sobreexpone y todo el blanco.  

Focos en una habitación (incluso en la sobrecarga) que están en la vista si las cámaras de seguimiento pueden ser a veces culpantes, lo que confunde el AEC/AGC de las cámaras de seguimiento. La iluminación plana/difusa ayuda a.  

### <a name="mixed-reality-cloud-services-and-azure"></a>SERVICIOS EN LA NUBE DE REALIDAD MIXTA Y AZURE 

**P: ¿Cómo puede Microsoft Azure ayudar a mi escala empresarial?**

R: la administración remota y en el sitio de Azure puede ayudar a su empresa a controlar los datos, reducir los costos operativos y escalar la implementación en las ubicaciones nuevas y existentes. Los servicios en la nube de Azure, como Azure Storage, Azure Functions, App Service, redes de Azure y IOT Hub, pueden ayudar con los siguientes casos de uso:  

Administración de & de implementación de dispositivos remotos 

Análisis in situ Real-Time 

Juego LBE adaptable inteligente 

Transmisión e implementación de contenido de LBE 

Preferencias de LBE Player mapa térmico 

Sistema de reserva y reserva de LBE 

**P: estoy desarrollando un MMOG espacial para implementarlo en una superficie masiva. ¿Todos los servicios que me ayudan a administrar mi contenido y persistencia de objetos?**

R: los delimitadores espaciales de Azure son un nuevo servicio de realidad mixta que permite experiencias de realidad mixta multiusuario y con reconocimiento espacial en dispositivos de HoloLens, iOS y Android. Puede obtener más información sobre los anclajes espaciales de Azure [aquí](https://azure.microsoft.com//services/spatial-anchors/).

**Respuestas. Nuestro lugar está especializado en experiencias con varios jugadores y me gustaría centrarnos en el tiempo de desarrollo en el contenido y el desarrollo de front-end. ¿Hay ofertas que puedan ayudarme a arrancar o descargar el desarrollo de back-end?**

R: Azure PlayFab es una plataforma de back-end completa para juegos en vivo. Puede obtener más información al respecto [aquí](https://playfab.com/).

### <a name="misc"></a>Varios

**P: uso SteamVR para implementar mis experiencias. ¿Funciona Windows Mixed Reality con SteamVR?**

R: Windows Mixed Reality para SteamVR permite a los usuarios ejecutar experiencias de SteamVR en auriculares con micrófonos de realidad con Windows Mixed Reality. [Aquí](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)encontrará más información sobre STEAMVR con WMR.

### <a name="support-and-community"></a>Soporte técnico y comunidad  

Tenemos unos pocos recursos útiles para ayudarle a ponerse en contacto con expertos en la materia en nuestro equipo, obtener soporte técnico para solucionar problemas y contribuir a la mayor comunidad de desarrollo de la realidad mixta.  

Si surgen problemas con características publicadas de forma pública, envíe un error a través del centro de comentarios. para obtener instrucciones, consulte esta [Página](/windows/mixed-reality/enthusiast-guide/filing-feedback).

Para obtener más ayuda para la solución de problemas con WMR, [pida una solicitud de soporte técnico](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) al equipo de soporte técnico al cliente.

Únase a nuestro canal de demora de HoloDevelopers para interactuar con los desarrolladores de realidad mixta y los expertos en la materia: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: siga nuestro equipo de relaciones con el desarrollador de realidad mixta para obtener noticias, eventos y actualizaciones @MxdRealityDev 

En caso de que se encuentre en San Francisco, siempre habrá algo en marcha en el reactor de Microsoft. [Aquí](https://developer.microsoft.com//reactor/Location/San%20Francisco)puede ver el calendario de eventos.
