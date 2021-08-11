---
title: Diseñar entornos envolventes propios
description: Obtenga información sobre cómo Windows Mixed Reality entornos de inicio propios.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Home, Custom Environments, places, skyloft, user, create, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c0f006d3e05cb0892a0a9b2014a4d46a0668f628cf369e38c63c83756148d778
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198610"
---
# <a name="design-your-own-immersive-environments"></a>Diseñar entornos envolventes propios

>[!NOTE]
>Se trata de una característica experimental. Pruébalo y pruébalo, pero no se preocupe si todo no funciona según lo previsto. Estamos evaluando la viabilidad de esta característica y su interés en usarlo, así que háganos saber su experiencia (y los errores que haya encontrado) en los foros para [desarrolladores.](https://forums.hololens.com/categories/custom-home-environments)

A partir de la actualización de abril de [2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)de Windows 10, hemos habilitado una característica experimental que le permite agregar entornos personalizados al selector Lugares (en el menú Inicio) para usarlos como inicio [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)inicio. Windows Mixed Reality tiene dos entornos predeterminados, Casa sobre el acantilado y Skyloft, puede elegir como su hogar. La creación de entornos personalizados le permite expandir la lista con sus propias creaciones. Vamos a hacer que esta característica esté disponible en un estado temprano para evaluar el interés de los creadores y desarrolladores. Vea qué tipos de mundos crea y comprenda cómo trabaja con diferentes herramientas de creación.

Al usar un entorno personalizado, observará que la teleportación, la interacción con las aplicaciones y la colocación de hologramas funciona igual que en Casa sobre el acantilado y Skyloft. Puede examinar la web en un panorama desfilando o rellenar una ciudad futurista con hologramas: las posibilidades son infinitas.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Entornos de inicio personalizados</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Probar un entorno de ejemplo

Hemos creado un entorno de ejemplo que muestra algunas de las posibilidades creadoras de los entornos de inicio personalizados. Siga estos pasos para probarlo:
1. [Descargue nuestro entorno de islandesa de Isla](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) Desaprobleba de ejemplo (puntos de vínculo al archivo ejecutable autoextraíble).

    ![Entorno de ejemplo islandesa de isla de Isla de La Isla](images/FantasyLand.jpg)<br>
    *Entorno de ejemplo islandesa de isla de Isla de La Isla*<br>

2. Ejecute el **Fantasy_Island.exe** que descargó.

    > [!NOTE]
    > Al intentar ejecutar un archivo .exe descargado de la web (como este), es posible que encuentre un elemento emergente "Windows protegido por el equipo". Para ejecutar Fantasy_Island.exe desde este menú emergente, seleccione **Más información** y, a continuación, Ejecutar de **todas formas.** Esta configuración de seguridad está pensada para protegerle frente a la descarga de archivos en los que quizás no quiera confiar, por lo que solo debe elegir esta opción cuando confíe en el origen del archivo.

3. Abra **Explorador de archivos** y vaya a la carpeta environments pegando la siguiente ubicación de archivo en la barra de direcciones: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` .
4. Copie el entorno de ejemplo que descargó en esta carpeta.
5. Reinicie **Portal de realidad mixta** para actualizar la lista de entornos en el selector Lugares.
6. Póntese el casco. Una vez que se encuentra en la página principal, abra **el menú Inicio** con el botón Windows el controlador.
7. Seleccione el **icono Lugares** situado encima de la lista de aplicaciones ancladas para elegir un entorno de inicio.
8. En la lista de lugares encontrará el entorno de Isla de La Isla de la Isla Desarás que descargó. Seleccione **Isla de la isla** de la isla para entrar en el nuevo entorno de inicio personalizado.

## <a name="creating-your-own-custom-environment"></a>Creación de su propio entorno personalizado

Además de usar nuestros entornos de ejemplo, puede exportar sus propios entornos personalizados mediante su software de edición 3D favorito. 

### <a name="modeling-guidelines"></a>Directrices de modelado

Al modelar el entorno, tenga en cuenta las siguientes recomendaciones para que los usuarios se resalte en la orientación correcta en un mundo de tamaño indiscutible:

1. Los usuarios se generan a las 0,0,0, así que centra la ubicación de generación en torno al origen.
2. Las unidades de trabajo deben establecerse en metros para que los recursos se puedan crear a escala mundial.
3. El eje Up debe establecerse en "Y".
4. El recurso debe enfrentarse "hacia delante" hacia el eje Z positivo.
5. No tiene que combinar todas las mallas, pero se recomienda si tiene como destino dispositivos con recursos restringidos.

### <a name="exporting-your-environment"></a>Exportación del entorno

Windows Mixed Reality se basa en glTF binario (.glb) como formato de entrega de recursos para entornos. glTF es un estándar abierto gratuito para la entrega de recursos 3D mantenida por el grupo Deserciones. La compatibilidad de Microsoft con el formato en Windows aplicaciones y experiencias crecerá a medida que glTF evolucione como un estándar del sector para el contenido 3D interoperable.

El primer paso para exportar los recursos que se usarán como entornos de inicio personalizados es generar un modelo glTF 2.0. El grupo de trabajo glTF mantiene una lista [de exportadores](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) y convertidores admitidos para crear un modelo glTF 2.0. Para empezar, use uno de los programas enumerados en esta página para crear y exportar un modelo glTF 2.0 o convertir un modelo existente mediante uno de los convertidores admitidos.

<!-- Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.  -->

### <a name="environment-limits"></a>Límites de entorno

Todos los entornos deben < 256 mbs. Los entornos de más de 256 MB no se cargarán y volverán a un mundo vacío con solo el skybox predeterminado que rodea al usuario. Tenga en cuenta este límite de tamaño de archivo al crear los modelos. Además, si planea optimizar el entorno mediante WindowsMRAssetConverter como se describe a continuación, tenga en cuenta que el tamaño de la textura aumentará a medida que el optimizador cree texturas que tengan un tamaño de archivo mayor, pero que se carguen más rápido. 

### <a name="optimizing-your-environment"></a>Optimización del entorno

Windows Mixed Reality admite muchas optimizaciones opcionales que pueden reducir significativamente los tiempos de carga del entorno. Preste especial atención a los entornos que tienen una gran cantidad de texturas, ya que a veces se va a hacer tiempo de espera durante la carga. En general, se recomienda este paso para todos los recursos; sin embargo, los entornos más pequeños con pocas texturas o de baja resolución no siempre lo necesitarán. 

Para facilitar este proceso, hemos creado el convertidor de recursos [Windows Mixed Reality (disponible](https://github.com/Microsoft/glTF-Toolkit/releases) en GitHub) para realizar las optimizaciones. Esta herramienta usa un conjunto de utilidades disponibles en microsoft glTF Toolkit para optimizar cualquier glTF estándar 2.0 o.glb mediante la realización de un empaquetado de textura adicional, compresión y reducción de la resolución. 

Actualmente, el convertidor admite varias marcas para ajustar el comportamiento exacto de las optimizaciones. Se recomienda ejecutar con las marcas siguientes para obtener mejores resultados:

Marca|Valores recomendados|Description
---|---|---
-max-texture-size|1024 o 2048| Ajuste el valor para mejorar la calidad de las texturas; el valor predeterminado es 512 x 512. Un valor mayor afectará significativamente al tamaño de archivo del entorno, por lo que tenga en cuenta el límite de 256 MB.
-min-version|1803|Los entornos personalizados solo se admiten en versiones de Windows >= 1803. Esta marca quitará las texturas de las versiones anteriores y reducirá el tamaño de archivo del recurso final.

Por ejemplo:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Prueba del entorno

Una vez que tenga el entorno final.glb, estará listo para probarlo en el casco. Comience en el paso 2 de la [sección "Probar un entorno](#trying-a-sample-environment) de ejemplo" para usar el entorno personalizado como ambiente principal. 

## <a name="sending-feedback"></a>Envío de opiniones

Mientras estamos evaluando esta característica experimental, nos interesa aprender cómo usa entornos personalizados, los errores que pueda encontrar y cómo le gusta la característica. Comparta cualquier comentario para crear y usar entornos de inicio personalizados en los [foros para desarrolladores.](https://forums.hololens.com/categories/custom-home-environments)

## <a name="troubleshooting-and-tips"></a>Solución de problemas y sugerencias

### <a name="how-do-i-change-the-name-of-the-environment"></a>Cómo cambiar el nombre del entorno?

El nombre de archivo de la carpeta environments se usará en el selector Lugares. Para cambiar el nombre del entorno, cambie el nombre del archivo de entorno y reinicie Portal de realidad mixta.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Cómo quitar entornos personalizados del selector Lugares?

Para quitar un entorno personalizado, abra la carpeta environments del equipo `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` () y elimínelo. Una vez que Portal de realidad mixta, este entorno ya no aparecerá en el selector Lugares. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Cómo mi entorno personalizado favorito de forma predeterminada?

Actualmente no se puede cambiar el entorno predeterminado. Cada vez que reinicie Portal de realidad mixta, se le devolverá al entorno Casa sobre el acantilado usuario. 

### <a name="i-spawn-into-a-blank-space"></a>Se genera en un espacio en blanco.

Windows Mixed Reality [no admite entornos que superen los 256 mb.](#environment-limits) Cuando un entorno supere este límite, se despedará en el sky box vacío sin ningún modelo.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Mi entorno tarda mucho tiempo en cargarse.

Puede agregar optimizaciones opcionales a su entorno para que se cargue más rápido. Consulte ["Optimización del entorno"](#optimizing-your-environment) para obtener más información.

### <a name="the-scale-of-my-environment-is-incorrect"></a>La escala de mi entorno es incorrecta

Windows Mixed Reality unidades glTF a 1 medidor al cargar entornos. Si el entorno carga una escala inesperada, compruebe de nuevo el exportador para asegurarse de que está modelando en una escala de 1 medidor. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>La ubicación de generación en mi entorno es incorrecta

La ubicación de generación predeterminada se encuentra en 0,0,0 en el entorno. Actualmente no es posible personalizar esta ubicación, por lo que debe modificar el punto de generación mediante la exportación del entorno con el origen situado en el punto de generación que desee.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>El audio no suena correctamente en el entorno

Al crear el entorno personalizado, se usa una simulación de representación acústica que no coincide con el espacio físico que ha creado. El sonido puede proceder de direcciones incorrectas y puede parecer desconcertado. 

## <a name="see-also"></a>Consulte también
* [Windows Mixed Reality Asset Converter (en GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)