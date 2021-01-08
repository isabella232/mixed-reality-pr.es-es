---
title: Instrucciones de compatibilidad de equipos de Windows Mixed Reality
description: El gráfico de información general describe los requisitos mínimos del sistema de equipos para la compatibilidad con Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, ultra, compatible, compatibilidad, requisitos del sistema, PC
appliesto:
- Windows 10
ms.openlocfilehash: ed53c388797cb57a7f2a53ed40b18923a23c8b74
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009125"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Instrucciones de compatibilidad de hardware de equipo mínima de Windows Mixed Reality

## <a name="features-and-experiences"></a>Características y experiencias

Windows 10 potencia Windows Mixed Reality y Windows Mixed Reality ultra. La versión que experimente dependerá del hardware de su equipo.

Con Windows Mixed Reality ultra, obtiene algunas funcionalidades y características adicionales:

* Objetos visuales más nítidos y una frecuencia de actualización más alta (90 fotogramas por segundo).
* Más aplicaciones y experiencias, incluidos los juegos más intensivos de gráficos.
* Una ventana de "reflejo" en el escritorio que muestra lo que se ve en la realidad mixta.
* Grabe y Comparta vídeos y fotos de experiencias de realidad mixta.

## <a name="minimum-pc-hardware-guidelines"></a>Directrices mínimas de hardware de PC

Para disfrutar de la mejor experiencia con Windows Mixed Reality, empiece con un nuevo [equipo preparado para la realidad mixta de Windows](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) o un equipo compatible con Windows Mixed Reality que pueda proporcionar las experiencias de alta realidad de Windows Mixed. Windows Mixed Reality ultra proporciona objetos visuales más nítidos con frecuencias de actualización más altas, más experiencias de la aplicación, como la mayoría de los juegos de uso intensivo de gráficos, la creación de reflejo de la experiencia de Windows Mixed Reality en el escritorio y la capacidad de grabar y compartir (fotos y vídeos) sus experiencias con otros usuarios. 

Para ver si su equipo puede ejecutar Windows Mixed Reality, revise las instrucciones de hardware siguientes y ejecute la [aplicación del portal de realidad mixta](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M).

Recuerde que el rendimiento variará en función de la configuración exacta. También tendrás que asegurarte de que tu equipo tenga los [puertos correctos](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para los auriculares con pausa de Windows Mixed Reality que estés usando.

>[!NOTE]
>Las directrices para los equipos de desarrollo son mayores que las de los equipos de los consumidores que ejecutan aplicaciones de realidad mixta. Si es un desarrollador de realidad mixta, [consulte especificaciones recomendadas de equipos de desarrollo](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development).


## <a name="mixed-reality-portal-app"></a>Aplicación del portal de realidad mixta

El portal de realidad mixta es la mejor manera de asegurarse de que su equipo está listo para ejecutar Windows Mixed Reality. 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

Después de ejecutar la aplicación, recibirá uno de los siguientes mensajes:
* **Está listo.** Su equipo tiene lo que se necesita para ejecutar Windows Mixed Reality.
* **Admite algunas características.** Este equipo puede ejecutar Windows Mixed Reality, pero es posible que algunas características estén limitadas.
* **No se puede ejecutar Mixed Reality.** Este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality.

A continuación, obtendrá un análisis del equipo con el hardware, los controladores y el sistema operativo necesarios.
![Captura de pantalla de la comprobación de PC de Windows Mixed Reality](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Icono</th><th>Qué significa</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">El equipo pasa el elemento necesario.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Puede haber problemas con su equipo para el requisito determinado. Si surgen problemas, es posible que tenga que solucionar problemas o actualizar el equipo.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">El equipo no cumple los requisitos del elemento especificado.</td>
</tr>
</table>

 [Obtener ayuda con los resultados del portal de realidad mixta](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>Instrucciones de compatibilidad

> [!IMPORTANT]
> Se va a actualizar, con lo que se realizarán adiciones a y es posible que se revisen estas instrucciones de compatibilidad de equipos Windows Mixed Reality. Consulte periódicamente las instrucciones y los requisitos más recientes.

**Especificaciones compatibles con la reverberación de HP**<br>
Debido a la resolución más alta, los siguientes requisitos se aplican a las líneas de producto de la reverberación G1 & G2 de HP para garantizar una experiencia 90 óptima de resolución completa: 

<ul>
<li> Intel Core i5, i7, Intel xenón E3-1240 V5, equivalente o superior. AMD Ryzen 5 equivalente o superior. </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente o superior </li> 
<li> Memoria: 8 GB de RAM o más </li> 
<li> 1x puerto de pantalla 1,3 </li> 
<li> 1x USB 3,0 tipo-C con entrega de energía (o adaptador de alimentación incluido)</li>
<li> Windows 10 mayo de 2019 Update o posterior </li>
</ul>

**Todos los demás auriculares compatibles con WMR** <br>
Para el resto de HMDs, consulte los siguientes requisitos: 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality ultra PC</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Equipos con Windows Mixed Reality</th>
</tr><tr>
    <td style="vertical-align: middle">Sistema operativo</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) o posterior: Home, Pro, Business, Education.<br/>    (<b>Nota</b>: no se admite en las versiones N o Windows 10 Pro en modo S)</td>
</tr><tr>
    <td style="vertical-align: middle">Procesador</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (cuarta generación), Quad-Core (o superior) <br>AMD Ryzen 5 1400 3,4 GHz (escritorio), cuádruple núcleo (o superior)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (séptima generación Mobile), doble núcleo con tecnología de Hyper-Threading Intel habilitada (o superior) <br>AMD Ryzen 5 1400 3,4 GHz (escritorio), cuádruple núcleo (o superior)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">DDR3 de 8 GB (o superior)</td>
    <td style="vertical-align: middle; text-align: center;">canal dual DDR3 de 8 GB (o superior)</td>
</tr><tr>
    <td style="vertical-align: middle">Espacio libre en disco</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Al menos 10 GB</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Al menos 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">Tarjeta gráfica</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>NVIDIA GTX 1060 (o superior) GPU discreta compatible con DX12</li>
            <li>AMD RX 470/570 (o superior) GPU discreta compatible con DX12 </li>
            </ul>     
            <b>Nota:</b> La GPU debe estar hospedada en una ranura de vínculo PCIe 3,0 x4 + </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>Intel HD Graphics integrado 620 (o superior) GPU integrada compatible con DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(Compruebe si el modelo es mayor)</a></li>
        <li>GPU discreta de NVIDIA MX150 (o superior)</li>
        <li>GPU discreta NVIDIA GeForce GTX 1050</li>
        <li>GPU discreta de NVIDIA 965M</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>Nota:</b> No se admiten GPU de Intel anteriores, como los gráficos de alta definición 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx y 6xxx.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Controlador de gráficos</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Display Driver Model (WDDM) 2,2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Puerto de visualización de gráficos</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2,0 o DisplayPort 1,2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1,4 o DisplayPort 1,2</td>
</tr><tr>
    <td style="vertical-align: middle">Pantalla</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Pantalla externa conectada o integrada VGA (800x600) (o superior)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Conectividad USB</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">Tipo USB 3,0-A </td>
</tr><tr>
    <td style="vertical-align: middle">Conectividad Bluetooth (para <a href="controllers-in-wmr.md">controladores de movimiento</a>)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4,0</td>
</tr><tr>
    <td style="vertical-align: middle">Fotogramas del casco esperado</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Power</td>
    <td style="vertical-align: middle; text-align: center;">Puertos USB 3,0 (tipo A)</td>
    <td style="vertical-align: middle; text-align: center;">Puertos USB 3,0 (tipo A)</td>
</tr>
</table>



**Información adicional:**
* Los equipos portátiles más grandes con pantallas de al menos 15 "hacen lo mejor.
* Para disfrutar de la mejor experiencia, se recomienda un procesador Intel® Core de 8 gen™ o la séptima generación Intel® Core™ i5.
* Las configuraciones de gráficos híbridas solo son compatibles con la realidad mixta de Windows ultra. El adaptador de gráficos discretos en cualquier configuración híbrida debe cumplir todos los requisitos enumerados en las instrucciones de realidad mixta de Windows para adaptadores de gráficos discretos.
* Si tiene una tarjeta de gráficos discretos que debe ejecutar Windows Mixed Reality ultra, pero tiene como valor predeterminado una frecuencia de actualización de 60 Hz (60 fotogramas por segundo), use un adaptador de DisplayPort a HDMI 2,0 para conectar los auriculares y habilitar una frecuencia de actualización de 90-Hz.
* Los auriculares diferentes pueden requerir puertos de hardware diferentes, por lo que debe asegurarse de que el equipo tiene los puertos correctos o los [adaptadores necesarios](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) para conectarse a los auriculares.

>[!NOTE]
>El hardware gráfico discreto e integrado que no cumple con las especificaciones mínimas confirmadas no se ha probado, confirmado u optimizado para Windows Mixed Reality y puede que no funcione correctamente o en absoluto.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality y Surface

Para obtener la mejor experiencia de Windows Mixed Reality en un dispositivo Surface, se recomienda desplazaba 2 (15)) configurado con NVIDIA GeForce GTX 1060 GB y 16 GB de RAM.  Esta configuración es compatible con todas las características de Windows Mixed Reality a las 90 Hz y se ha probado y se ha identificado para Windows Mixed Reality ultra.  El libro Surface 2 (13), Surface Studio, Surface Laptop y Surface Pro (2017) admitirán algunas características de Windows Mixed Reality cuando se configuren con una CPU de Intel Core i5 (o superior) y al menos 8 GB de RAM.

**Requisitos:**
* Los productos de Surface requieren actualizaciones de controladores que sean compatibles con Windows Mixed Reality. Estos controladores se pueden instalar en la superficie de; para ello, vaya a **configuración > actualización y seguridad > comprobar si hay actualizaciones**.
* Los productos de Surface requieren un [adaptador](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) desde el puerto de vídeo (mini DisplayPort o USB-C, según el equipo Surface) hasta HDMI 2,0 para auriculares con Windows Mixed Reality. La versión más reciente de la superficie Mini-DisplayPort al adaptador audiovisual HDMI es compatible con HDMI 2,0 (la versión anterior no es). Del mismo modo, el <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">adaptador Surface USB-C to HDMI</a> también es compatible con HDMI 2,0.

>[!WARNING]
>No todos los adaptadores de mini DisplayPort o USB-C a HDMI son compatibles con HDMI 2,0. Considere la posibilidad de comprobar la compatibilidad de "HDMI 2,0" explícita o la compatibilidad de "4K" en cualquier adaptador.

Puede encontrar más información sobre la compatibilidad de las superficies con Windows Mixed Reality en la tabla siguiente:

<table>
    <tr>
        <th> Dispositivo Surface </th><th> Compatibilidad con características de Windows Mixed Reality </th><th> Configuración recomendada </th><th> Notas</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (original)/Surface Pro 2 </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
(con Windows 10 Pro instalado) <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Libro de superficie con base de rendimiento </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Libro de superficie 2 (15 &quot; ) </td><td style="vertical-align: middle"> Completo </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1060/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Recomendado</b>: para obtener la mejor experiencia de Windows Mixed Reality en un dispositivo Surface, se recomienda desplazaba 2 15 "configurado con NVIDIA GeForce GTX 1060 GB y 16 GB de RAM.  Esta configuración se prueba y se incluye en el distintivo, ya que la realidad mixta de Windows es compatible con todas las características de Windows Mixed Reality y le permitirá disfrutar de la mayor variedad de aplicaciones compatibles y juegos.</li>
                <li>La GPU discreta NVIDIA GeForce GTX 1060 proporcionará una experiencia de Windows Mixed Reality Ultra @ 90-Hz</li><br/>                <li>Para obtener el mejor rendimiento, use los controladores de gráficos de NVIDIA publicados para el libro de Surface 2. Los controladores más recientes pueden estar disponibles en el sitio web de NVIDIA&#39;s, pero no se prueban.</li><br/>                <li>Requiere <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">el adaptador de USB-C de superficie para HDMI</a> (otros adaptadores pueden funcionar, pero no se prueban)</li>
                <li><b>Nota en el docking Surface</b>: el uso de la base de superficie con Surface Book 2 no se admite oficialmente con Windows Mixed Reality, debido a las limitaciones de la fuente de alimentación del muelle de superficie.</li><br/>                <li><b>Nota en la versión 1803 de Windows 10</b>: si&#39;vuelve a ejecutar la versión 1803 de Windows 10, asegúrese de que&#39;volver a compilar el sistema operativo 17134,137 o posterior (instalado por KB4284848) para asegurarse de que tiene las últimas correcciones de rendimiento. Para obtener más información, consulte las notas de la versión de <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Libro de superficie 2 (13,5 &quot; ) </td><td style="vertical-align: middle"> Parcial </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1050/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Nota</b>: el libro Surface 2 (13)) no se ha identificado para Windows Mixed Reality, pero admitirá algunas características de Windows Mixed Reality, lo que le permite usar un número limitado de aplicaciones y juegos compatibles.  El rendimiento dependerá de la configuración.</li>
                <li>Las configuraciones con una GPU integrada de Intel Core i5/Intel HD Graphics 620 proporcionarán una experiencia de Windows Mixed Reality @ 60-Hz</li>
                <li>Las configuraciones con una GPU discreta de Intel Core i7/NVIDIA GeForce GTX 1050 proporcionarán una experiencia de Windows Mixed Reality @ 90-Hz</li>                       <li>Para obtener el mejor rendimiento, use los controladores de gráficos de NVIDIA publicados para el libro de Surface 2. Los controladores más recientes pueden estar disponibles en el sitio web de NVIDIA&#39;s, pero no se prueban.</li>
                <li>Requiere <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">el adaptador de USB-C de superficie para HDMI</a> (otros adaptadores pueden funcionar, pero no se prueban)</li>
                <li><b>Nota en el docking Surface</b>: el uso de la base de superficie con Surface Book 2 no se admite oficialmente con Windows Mixed Reality, debido a las limitaciones de la fuente de alimentación del muelle de superficie.</li>
                <li><b>Nota en la versión 1803 de Windows 10</b>: si&#39;vuelve a ejecutar la versión 1803 de Windows 10, asegúrese de que&#39;volver a compilar el sistema operativo 17134,137 o posterior (instalado por KB4284848) para asegurarse de que tiene las últimas correcciones de rendimiento. Para obtener más información, consulte las notas de la versión de <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> Parcial </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce GTX 980m/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Nota</b>: Surface Studio no se ha identificado para Windows Mixed Reality, pero admitirá algunas características de Windows Mixed Reality, lo que le permite usar un número limitado de aplicaciones y juegos compatibles.  El rendimiento dependerá de la configuración.</li>
                <li>Las configuraciones con NVIDIA GeForce GTX 965 m proporcionan una experiencia de Windows Mixed Reality @ 60-Hz.</li>
                <li>Las configuraciones con NVIDIA GeForce GTX 980 m proporcionan una experiencia de Windows Mixed Reality @ 90-Hz.</li>
                <li>Surface DisplayPort en el adaptador HDMI 2,0 (otros adaptadores pueden funcionar, pero no se prueban)</li>
                <li>El casco de la realidad mixta de Windows debe estar conectado al puerto USB con el símbolo "+"</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (2017) </td><td style="vertical-align: middle"> Parcial </td><td style="vertical-align: middle"> Intel Core i7/Intel® iris™ más gráficos 640/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Nota</b>: Surface Pro (2017) no se ha identificado para Windows Mixed Reality, pero admitirá algunas características de Windows Mixed Reality, lo que le permite usar un número limitado de aplicaciones y juegos compatibles.  El rendimiento dependerá de la configuración.</li>
                <li><b>No se admiten</b> las configuraciones con una GPU integrada Intel Core m3/Intel HD graphics 615</li>
                <li>Las configuraciones con una GPU integrada de Intel Core i5/Intel HD Graphics 620 proporcionarán una experiencia de Windows Mixed Reality @ 60-Hz</li>
                <li>Las configuraciones con una GPU integrada de Intel Core i7/Intel® Iris™ Plus 640 proporcionan una experiencia de Windows Mixed Reality @ 60-Hz</li><br/><li>Requiere la mini DisplayPort de superficie para el adaptador HDMI 2,0 (otros adaptadores pueden funcionar, pero no se prueban)</li>
                <li>Requiere el <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">control deslizante de rendimiento</a> establecido en "mejor rendimiento" durante el uso</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Surface Laptop </td><td style="vertical-align: middle"> Parcial </td><td style="vertical-align: middle"> Intel Core i7/Intel® iris™ más gráficos 640/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Nota</b>: el portátil Surface no se ha identificado para Windows Mixed Reality, pero admitirá algunas características de Windows Mixed Reality, lo que le permite usar un número limitado de aplicaciones y juegos compatibles.  El rendimiento dependerá de la configuración.</li>
                <li><b>No se admiten</b> las configuraciones con una GPU integrada Intel Core m3/Intel HD graphics 615</li>
                <li>Las configuraciones con una GPU integrada de Intel Core i5/Intel HD Graphics 620 proporcionarán una experiencia de Windows Mixed Reality @ 60-Hz</li>
                <li>Las configuraciones con una GPU integrada de Intel Core i7/Intel® Iris™ Plus 640 proporcionan una experiencia de Windows Mixed Reality @ 60-Hz</li><br/><li>Requiere la mini DisplayPort de superficie para el adaptador HDMI 2,0 (otros adaptadores pueden funcionar, pero no se prueban)</li>
                <li>Requiere el <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">control deslizante de rendimiento</a> establecido en "mejor rendimiento" durante el uso</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)
* [Adaptadores recomendados para equipos con capacidad de Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
