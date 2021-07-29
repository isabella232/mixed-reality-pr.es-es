---
title: Windows Mixed Reality Directrices de compatibilidad de PC
description: Gráfico de información general que esquematización de los requisitos mínimos del sistema de PC para la compatibilidad con Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Ultra, compatible, compatibilidad, requisitos del sistema, PC
appliesto:
- Windows 10
ms.openlocfilehash: b7c2b4b84440e7cdd22c2c0cd7d5f9830d55625f
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757042"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality de compatibilidad de hardware de equipo mínimo

![Imagen principal de compatibilidad de PC](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>Características y experiencias

Windows 10 se Windows Mixed Reality en diversos cascos en un conjunto diverso de hardware de PC.  La potencia del equipo determinará qué experiencias puede tener.
Con los equipos de gama superior, obtiene algunas funcionalidades y características adicionales:

* Objetos visuales más claros y una frecuencia de actualización mayor.
* Más aplicaciones y experiencias, incluidos los juegos con mayor uso de gráficos.
* Una ventana "mirror" en el escritorio que muestra lo que se ve en la realidad mixta.
* Grabe y comparta vídeos y fotos de sus experiencias de realidad mixta.

## <a name="minimum-pc-hardware-guidelines"></a>Directrices mínimas de hardware de PC

Para ver si el equipo puede ejecutar Windows Mixed Reality, revise las instrucciones de hardware siguientes y ejecute [Portal de realidad mixta](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) aplicación.

Recuerde que el rendimiento variará en función de la configuración exacta. También deberá asegurarse de que el [](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) equipo tiene los puertos adecuados para el casco Windows Mixed Reality envolvente que está usando.

>[!NOTE]
>Las directrices para equipos de desarrollo son superiores a las de los equipos de los consumidores que ejecutan aplicaciones de realidad mixta. Si es un desarrollador de realidad mixta, consulte las especificaciones recomendadas [del equipo de desarrollo.](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)

## <a name="mixed-reality-portal-app"></a>Portal de realidad mixta aplicación

[Portal de realidad mixta](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) es la mejor manera de asegurarse de que el equipo está listo para ejecutarse Windows Mixed Reality.

Después de ejecutar la aplicación, verá uno de los mensajes siguientes:

* **Está bien para ir.**  El equipo está listo para ejecutar juegos y experiencias de realidad mixta.
* **Admite algunas características.** El equipo puede ejecutar algunas experiencias de realidad mixta.
* **No se puede ejecutar la realidad mixta.** Este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality.

A continuación, se obtiene un análisis del equipo con el hardware, los controladores y el sistema operativo necesarios.
![Captura de pantalla de Windows Mixed Reality PC Check](images/screenshot-mr-pc-check.jpg)

<table>
<tr>
<th>Iconos</th><th>Qué significa</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">El equipo pasa el elemento necesario.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Puede haber problemas con el equipo para el requisito dado. Si se encuentra con problemas, es posible que tenga que solucionar problemas o actualizar el equipo.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">El equipo no cumple los requisitos del elemento especificado.</td>
</tr>
</table>

 [Obtener ayuda con los Portal de realidad mixta resultados](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Directrices de compatibilidad

> [!IMPORTANT]
> Vamos a actualizar, realizar adiciones a estas directrices de compatibilidad de pc y revisar estas Windows Mixed Reality de compatibilidad de pc. Consulte periódicamente las directrices y los requisitos más recientes.

### <a name="high-resolution-headset-requirements"></a>Requisitos de cascos de alta resolución

Debido a la mayor resolución, los siguientes requisitos se aplican a las líneas de productos HP Reverb G1, G2 y Omnicept para garantizar una experiencia óptima de resolución completa de 90 Hz:

<ul>
<li> Intel Core i5, i7, Intel Xeon E3-1240 v5, equivalente o mejor. AMD Ryzen 5 equivalente o mejor. </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente o mejor </li>
<li> Memoria: 8 GB de RAM o más </li>
<li> 1x Display Port 1.3 </li>
<li> 1x USB 3.0 Type-C con entrega de energía (o adaptador de alimentación incluido)</li>
<li> Windows 10 Actualización de mayo de 2019 o posterior </li>
</ul>

**Todos los demás cascos compatibles con WMR** <br>
Para todos los demás HMD, consulte los siguientes requisitos:

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality equipos a 90Hz</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality equipos de 60Hz</th>
</tr><tr>
    <td style="vertical-align: middle">Sistema operativo</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) o posterior: Inicio, Pro, Empresa, Educación.<br/>    (<b>Nota:</b>No se admite en N versiones o Windows 10 Pro en modo S)</td>
</tr><tr>
    <td style="vertical-align: middle">Procesador</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4ª generación), cuatro núcleos (o superior) <br>AMD Ryzen 5 1400 3,4 Ghz (escritorio), cuatro núcleos (o superior)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (7ª generación móvil), doble núcleo con Intel Hyper-Threading Technology habilitado (o mejor) <br>AMD Ryzen 5 1400 3,4 Ghz (escritorio), cuatro núcleos (o superior)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (o mejor)</td>
    <td style="vertical-align: middle; text-align: center;">Canal dual DDR3 de 8 GB (o mejor)</td>
</tr><tr>
    <td style="vertical-align: middle">Espacio libre en disco</td>
    <td style="vertical-align: middle; text-align: center;">Al menos 10 GB</td>
    <td style="vertical-align: middle; text-align: center;">Al menos 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">Tarjeta gráfica</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul>
            <li>GPU discreta compatible con NVIDIA GTX 1060 (o superior) DX12</li>
            <li>GPU discreta compatible con AMD RX 470/570 (o superior) DX12 </li>
            </ul>
            <b>Nota:</b> La GPU debe hospedarse en una ranura PCIe 3.0 x4+ Link </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>GPU integrada compatible con Intel HD Graphics 620 (o superior) DX12 (compruebe si <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">el modelo es mayor)</a></li>
        <li>NVIDIA MX150 (o superior) GPU discreta</li>
        <li>GPU discreta Nvidia GeForce GTX 1050</li>
        <li>GPU discreta nvidia 965M</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>Nota:</b> No se admiten GPU intel anteriores como HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx y 6xxx.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Controlador de gráficos</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Mostrar modelo de controlador (WDDM) 2.2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Puerto de presentación de gráficos</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 o DisplayPort 1.2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 o DisplayPort 1.2</td>
</tr><tr>
    <td style="vertical-align: middle">Pantalla</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Pantalla VGA (800x600) conectada externa o integrada (o mejor)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Conectividad USB</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 </td>
</tr><tr>
    <td style="vertical-align: middle">Bluetooth conectividad (para controladores <a href="controllers-in-wmr.md">de movimiento)</a></td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4.0</td>
</tr><tr>
    <td style="vertical-align: middle">Velocidad de fotogramas de casco esperada</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Power</td>
    <td style="vertical-align: middle; text-align: center;">Puertos USB 3.0</td>
    <td style="vertical-align: middle; text-align: center;">Puertos USB 3.0</td>
</tr>
</table>

**Información adicional:**

* Los portátiles más grandes con pantallas de al menos 15 pulgadas hacen lo mejor.
* Las configuraciones de gráficos híbridos solo son compatibles Windows Mixed Reality 90Hz. El adaptador de gráficos discretos en cualquier configuración híbrida debe cumplir todos los requisitos enumerados en las Windows Mixed Reality para adaptadores de gráficos discretos.
* Si tiene una tarjeta gráfica discreta que debe ejecutarse Windows Mixed Reality 90Hz, pero su valor predeterminado es una frecuencia de actualización de 60Hz (60 fotogramas por segundo), use un adaptador DisplayPort a HDMI 2.0 de tamaño completo para conectar el casco y habilitar una frecuencia de actualización de 90Hz.
* Los cascos diferentes pueden requerir puertos de hardware diferentes, por lo que debe asegurarse de que el equipo tiene los puertos correctos o los adaptadores [necesarios](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) para conectarse a los cascos.

>[!NOTE]
>El hardware gráfico discreto e integrado que no cumple las especificaciones mínimas confirmadas no se ha probado, confirmado ni optimizado para Windows Mixed Reality y puede que no funcione correctamente o en absoluto.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality y Surface

Para obtener la mejor experiencia Windows Mixed Reality en un dispositivo Surface, se recomienda la versión más reciente de SurfaceBook (15") configurada con al menos NVIDIA GeForce GTX de 1060 GB y 16 GB de RAM.  Esta configuración admite todas las Windows Mixed Reality y se ha probado para Windows Mixed Reality.  Las versiones más recientes de Surface Book (13.5"), Surface Studio, Surface Laptop y Surface Pro (2017) admitirán algunas características de Windows Mixed Reality cuando se configuren con una CPU Intel Core i5 (o mejor) y al menos 8 GB de RAM.

**Requisitos:**

* Los productos surface requieren que las actualizaciones de controladores sean compatibles con Windows Mixed Reality. Estos controladores se pueden instalar en Surface; para ello, vaya a Configuración > Actualización y seguridad **> Buscar actualizaciones.**
* Los productos [](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) surface requieren un adaptador desde el puerto de vídeo (Mini DisplayPort o USB-C, dependiendo de Surface PC) a HDMI 2.0 para Windows Mixed Reality cascos. La versión más reciente del adaptador de Surface Mini-DisplayPort a HDMI AV es compatible con HDMI 2.0 (la versión anterior no lo es). Del mismo modo, el <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">adaptador de Surface USB-C a HDMI</a> también es compatible con HDMI 2.0.

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico.](https://support.microsoft.com/contactus/)
* [Adaptadores recomendados para Windows Mixed Reality equipos compatibles](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
