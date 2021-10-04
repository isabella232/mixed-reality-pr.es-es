---
title: Windows Mixed Reality Directrices de compatibilidad de PC
description: Gráfico de información general que muestra los requisitos mínimos del sistema de PC para la compatibilidad con Windows Mixed Reality.
author: qianw211
ms.author: v-qianwen
ms.date: 09/22/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Ultra, compatible, compatibilidad, requisitos del sistema, PC
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: af3228e76bc9ce54ef877b67e8e85a3bde25e140
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436739"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality de compatibilidad de hardware de equipo mínimo

![Imagen principal de compatibilidad de PC](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>Características y experiencias

Windows 10 y Windows 11 se Windows Mixed Reality varios cascos en un conjunto diverso de hardware de PC.  La potencia del equipo determinará qué experiencias puede tener.
Con equipos de gama superior, se obtienen algunas funcionalidades y características adicionales:

* Objetos visuales más claros y una mayor frecuencia de actualización.
* Más aplicaciones y experiencias, incluidos los juegos con mayor uso de gráficos.
* Una ventana "reflejo" en el escritorio que muestra lo que ve en realidad mixta.
* Grabar y compartir vídeos y fotos de sus experiencias de realidad mixta.

## <a name="minimum-pc-hardware-guidelines"></a>Directrices mínimas de hardware de PC

Para ver si el equipo puede ejecutar Windows Mixed Reality, revise las instrucciones de hardware siguientes y ejecute [Portal de realidad mixta](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) aplicación.

Recuerde que el rendimiento variará en función de la configuración exacta. También deberá asegurarse de que el equipo tiene los [puertos](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) adecuados para el Windows Mixed Reality envolvente que está usando.

>[!NOTE]
>Las directrices para equipos de desarrollo son superiores a las de los equipos de los consumidores que ejecutan aplicaciones de realidad mixta. Si es desarrollador de realidad mixta, consulte las especificaciones recomendadas [del equipo de desarrollo.](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)

## <a name="mixed-reality-portal-app"></a>Portal de realidad mixta aplicación

[Portal de realidad mixta](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) es la mejor manera de asegurarse de que el equipo está listo para ejecutar Windows Mixed Reality.

Después de ejecutar la aplicación, verá uno de los siguientes mensajes:

* **Ya está bien.**  El equipo está listo para ejecutar juegos y experiencias de realidad mixta.
* **Admite algunas características.** El equipo puede ejecutar algunas experiencias de realidad mixta.
* **No se puede ejecutar la realidad mixta.** Este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality.

A continuación, se obtiene un análisis del equipo en el hardware, los controladores y el sistema operativo necesarios.
![Captura de pantalla de Windows Mixed Reality PC Check](images/screenshot-mr-pc-check.jpg)

| Icono | Qué significa |
| --- | --- |
| <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /> | El equipo pasa el elemento necesario. |
| <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /> | Puede haber problemas con el equipo para el requisito dado. Si se encuentra con problemas, es posible que tenga que solucionar problemas o actualizar el equipo. 
| <img alt="Error" width="30" height="30" src="images/glyph-error.png" /> | El equipo no cumple los requisitos para el elemento especificado. |

 [Obtener ayuda con los Portal de realidad mixta resultados](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Directrices de compatibilidad

> [!IMPORTANT]
> Vamos a actualizar y realizar adiciones a estas directrices de compatibilidad Windows Mixed Reality pc. Consulte periódicamente las directrices y los requisitos más recientes.

### <a name="high-resolution-headset-requirements"></a>Requisitos de cascos de alta resolución

Debido a la mayor resolución, los siguientes requisitos se aplican a las líneas de productos HP Reverb G1, G2 y Omnicept para garantizar una experiencia óptima de resolución completa de 90 Hz:

- Intel Core i5, i7, Intel Xeon E3-1240 v5, equivalente o mejor. AMD Ryzen 5 equivalente o mejor.  
- NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente o mejor  
- Memoria: 8 GB de RAM o más  
- 1x Display Port 1.3  
- 1x USB 3.0 Type-C con entrega de energía (o adaptador de alimentación incluido) 
- Windows 10 Actualización de mayo de 2019 o posterior  
 
**Todos los demás cascos compatibles con WMR** <br>
Para todos los demás HMD, consulte los siguientes requisitos:

| | Windows Mixed Reality equipos de 90Hz | Windows Mixed Reality equipos de 60Hz |
| --- | --- | --- |
| Sistema operativo | Windows 10 Fall Creators Update (RS3) o posterior: Inicio, Pro, Empresa, Educación. <br/>    (<b>Nota:</b>No se admite en N versiones o Windows 10 Pro en modo S) |
| Procesador | Intel Core i5 4590 (4ª generación), cuatro núcleos (o superior) <br> AMD Ryzen 5 1400 3,4 Ghz (escritorio), cuatro núcleos (o superior) | Intel Core i5 7200U (7.ª generación móvil), doble núcleo con Intel Hyper-Threading Technology habilitado (o mejor) <br> AMD Ryzen 5 1400 3,4 Ghz (escritorio), cuatro núcleos (o superior) |
| RAM | 8 GB DDR3 (o mejor) | Canal dual DDR3 de 8 GB (o mejor) |
| Espacio libre en disco | Al menos 10 GB | Al menos 10 GB |
| Tarjeta gráfica| <ul> <li>GPU discreta compatible con NVIDIA GTX 1060 (o superior) DX12 </li> <li>GPU discreta compatible con AMD RX 470/570 (o superior) DX12 </li> </ul> <br> <b>Nota:</b> La GPU debe hospedarse en una ranura PCIe 3.0 x4+ Link |  <ul>  <li>Gpu integrada compatible con Intel HD Graphics 620 (o superior) DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(compruebe si el modelo es mayor)</a></li> <li>NVIDIA MX150 (o superior) GPU discreta</li> <li>GPU discreta Nvidia GeForce GTX 1050</li> <li>GPU discreta nvidia 965M</li> <li>AMD Radeon RX 460/560</li> </ul> <b>Nota:</b> No se admiten GPU Intel anteriores, como HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx y 6xxx. |
| Controlador de gráficos | Windows Mostrar el modelo de controlador (WDDM) 2.2 |  |
| [Puerto de presentación de gráficos](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | HDMI 2.0 o DisplayPort 1.2 | HDMI 1.4 o DisplayPort 1.2 |
| Mostrar | Pantalla VGA externa o integrada conectada (800 x 600) (o mejor) | 
| [Conectividad USB](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | USB 3.0 | |
| Bluetooth conectividad (para controladores [de movimiento)](controllers-in-wmr.md) | Bluetooth 4.0 | |
| Velocidad de fotogramas de casco esperada | 90 Hz | 60 Hz |
| Power | Puertos USB 3.0 | Puertos USB 3.0 |

**Información adicional:**

* Los portátiles más grandes con pantallas de al menos 15 pulgadas hacen lo mejor.
* Las configuraciones de gráficos híbridos solo son compatibles Windows Mixed Reality 90Hz. El adaptador de gráficos discreto en cualquier configuración híbrida debe cumplir todos los requisitos enumerados en las Windows Mixed Reality para adaptadores de gráficos discretos.
* Si tiene una tarjeta gráfica discreta que debe ejecutarse Windows Mixed Reality 90Hz, pero su valor predeterminado es una frecuencia de actualización de 60Hz (60 fotogramas por segundo), use un adaptador DisplayPort a HDMI 2.0 de tamaño completo para conectar el casco y habilitar una frecuencia de actualización de 90Hz.
* Los cascos diferentes pueden requerir puertos de hardware diferentes, por lo que debe asegurarse de que el equipo tiene los puertos correctos o los adaptadores [necesarios](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) para conectarse al casco.

>[!NOTE]
>El hardware gráfico discreto e integrado que no cumple las especificaciones mínimas confirmadas no se ha probado, confirmado ni optimizado para Windows Mixed Reality y puede que no funcione correctamente o en absoluto.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality y Surface

Para obtener la mejor experiencia Windows Mixed Reality en un dispositivo Surface, se recomienda la versión más reciente de SurfaceBook (15") configurada con al menos NVIDIA GeForce GTX de 1060 GB y 16 GB de RAM.  Esta configuración admite todas las Windows Mixed Reality y se ha probado para Windows Mixed Reality.  Las versiones más recientes de Surface Book (13.5"), Surface Studio, Surface Laptop y Surface Pro (2017) admitirán algunas características de Windows Mixed Reality cuando se configuren con una CPU Intel Core i5 (o mejor) y al menos 8 GB de RAM.

**Requisitos:**

* Los productos de Surface requieren que las actualizaciones de controladores sean compatibles con Windows Mixed Reality. Estos controladores se pueden instalar en Surface; para ello, vaya a Configuración > actualización y seguridad **> buscar actualizaciones.**
* Los productos [](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) surface requieren un adaptador desde el puerto de vídeo (Mini DisplayPort o USB-C, dependiendo de Surface PC) a HDMI 2.0 para los cascos Windows Mixed Reality dispositivos. La versión más reciente del adaptador Mini-DisplayPort av de Surface a HDMI es compatible con HDMI 2.0 (la versión anterior no). Del mismo modo, el <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">adaptador de Surface USB-C a HDMI</a> también es compatible con HDMI 2.0.

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico.](https://support.microsoft.com/contactus/)
* [Adaptadores recomendados para Windows Mixed Reality equipos compatibles](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
