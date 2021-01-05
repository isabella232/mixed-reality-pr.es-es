---
title: Diseñar entornos envolventes propios
description: Obtenga información sobre cómo crear entornos principales de Windows Mixed Reality.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, Home, entornos personalizados, lugares, acantilado House, Skyloft, usuario, creación, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 2d88b4e20c2703b554572c0d39d5c69767164694
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848082"
---
# <a name="design-your-own-immersive-environments"></a>Diseñar entornos envolventes propios

>[!NOTE]
>Se trata de una característica experimental. Pruébelo y disfrute de divertido, pero no se sorprenda si todo no funciona de la manera esperada. Estamos evaluando la viabilidad de esta característica y nos interesa usarla, así que díganos su experiencia (y los errores que encuentre) en los [foros para desarrolladores](https://forums.hololens.com/categories/custom-home-environments).

A partir de la [actualización del 2018 de abril de Windows 10](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), hemos habilitado una característica experimental que le permite agregar entornos personalizados al selector de ubicaciones (en el menú Inicio) para usarlos como [Página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md). Windows Mixed Reality tiene dos entornos predeterminados, acantilado House y Skyloft, puede elegir como su hogar. La creación de entornos personalizados permite expandir la lista con sus propias creaciones. Estamos haciendo que esta característica esté disponible en un estado temprano para evaluar el interés de los creadores y desarrolladores. Vea qué tipos de mundos crea y comprenda cómo trabaja con diferentes herramientas de creación.

Al usar un entorno personalizado, observará que el telepuerto, la interacción con las aplicaciones y la colocación de hologramas funciona igual que en la casa del acantilado y Skyloft. Puede explorar la web en un panorama de fantasía o rellenar una ciudad futurista con hologramas; las posibilidades son infinitas.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Entornos domésticos personalizados</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Probar un entorno de ejemplo

Hemos creado un entorno de ejemplo que muestra algunas de las posibilidades creativas de entornos domésticos personalizados. Siga estos pasos para probarlo:
1. [Descargue nuestro entorno de ejemplo](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) de la isla de fantasía (vínculo apunta al archivo ejecutable autoextraíble).

    ![Entorno de ejemplo de isla de fantasía](images/FantasyLand.jpg)<br>
    *Entorno de ejemplo de isla de fantasía*<br>

2. Ejecute el archivo de **Fantasy_Island.exe** que descargó.

    > [!NOTE]
    > Al intentar ejecutar un archivo. exe descargado de la web (como este), es posible que aparezca un mensaje emergente "Windows protegió su PC". Para ejecutar Fantasy_Island.exe desde esta ventana emergente, seleccione **más información** y, a continuación, **ejecute de todos modos**. Esta configuración de seguridad está destinada a protegerle de la descarga de archivos que no quiera confiar, por lo que solo debe elegir esta opción cuando confíe en el origen del archivo.

3. Abra el **Explorador de archivos** y vaya a la carpeta entornos pegando la siguiente ubicación de archivo en la barra de direcciones: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` .
4. Copie el entorno de ejemplo que descargó en esta carpeta.
5. Reinicie el **portal de realidad mixta** para actualizar la lista de entornos en el selector de ubicaciones.
6. Coloque el casco. Una vez que esté en el hogar, abra el **menú Inicio** con el botón Windows del controlador.
7. Seleccione el icono de **lugares** situado encima de la lista de aplicaciones ancladas para elegir un entorno de inicio.
8. Encontrará el entorno de la isla de fantasía que descargó en la lista de lugares. Seleccione **isla de fantasía** para entrar en el nuevo entorno de inicio personalizado.

## <a name="creating-your-own-custom-environment"></a>Creación de su propio entorno personalizado

Además de usar nuestros entornos de ejemplo, puede exportar sus propios entornos personalizados con su software de edición 3D favorito. 

### <a name="modeling-guidelines"></a>Directrices de modelado

A la hora de modelar su entorno, tenga en cuenta las siguientes recomendaciones para que los usuarios generen la orientación correcta en un mundo con un tamaño increíble:

1. Los usuarios se generarán en 0, 0, 0, por lo que debe centrar la ubicación de generación en torno al origen.
2. Las unidades de trabajo deben establecerse en metros para que los recursos puedan crearse a escala mundial.
3. El eje hacia arriba debe establecerse en "Y".
4. El recurso debe estar en "adelante" hacia el eje Z positivo.
5. No tiene que combinar todas las mallas, pero se recomienda si tiene como destino dispositivos con restricción de recursos.

### <a name="exporting-your-environment"></a>Exportar el entorno

Windows Mixed Reality se basa en glTF binario (. glb) como formato de entrega de recursos para los entornos. glTF es un estándar abierto sin regalías para la entrega de recursos 3D mantenido por el Grupo Khronos. El soporte técnico de Microsoft para el formato en las aplicaciones y experiencias de Windows crecerá a medida que glTF evolucione como un estándar del sector para el contenido 3D interoperable.

El primer paso para exportar recursos que se usarán como entornos domésticos personalizados es la generación de un modelo glTF 2,0. El grupo de trabajo glTF mantiene una [lista de los exportadores y convertidores admitidos](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) para crear un modelo glTF 2,0. Para empezar, use uno de los programas enumerados en esta página para crear y exportar un modelo glTF 2,0, o bien convertir un modelo existente mediante uno de los convertidores admitidos.

Además, consulte [este artículo útil, que proporciona información general sobre un flujo de trabajo de arte para exportar modelos de glTF de Blender y 3DS Max directamente. 

### <a name="environment-limits"></a>Límites del entorno

Todos los entornos deben tener < 256 MB. Los entornos de más de 256 MB no se cargarán y revertirán a un mundo vacío con solo el skybox predeterminado que rodea al usuario. Tenga en cuenta este límite de tamaño de archivo al crear los modelos. Además, si tiene previsto optimizar el entorno mediante WindowsMRAssetConverter, tal y como se describe a continuación, debe ser Cognizant que el tamaño de la textura aumente a medida que el optimizador cree texturas que tengan un tamaño de archivo mayor, pero que se carguen más rápido. 

### <a name="optimizing-your-environment"></a>Optimizar el entorno

Windows Mixed Reality admite muchas optimizaciones opcionales que pueden reducir significativamente los tiempos de carga del entorno. Preste especial atención a los entornos que tienen muchas texturas, ya que a veces agotarán el tiempo de espera mientras se cargan. En general, se recomienda este paso para todos los recursos; sin embargo, los entornos más pequeños con pocas texturas o de baja resolución no siempre lo requieran. 

Para facilitar este proceso, hemos creado el convertidor de [activos de Windows Mixed Reality (disponible en GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) para realizar las optimizaciones. Esta herramienta utiliza un conjunto de utilidades disponibles en el kit de herramientas de glTF de Microsoft para optimizar cualquier glTF estándar de 2,0 o. glb mediante la realización de un empaquetado de textura adicional, compresión y escalado vertical. 

El convertidor admite actualmente varias marcas para retocar el comportamiento exacto de las optimizaciones. Se recomienda ejecutar con las siguientes marcas para obtener los mejores resultados:

Marca|Valores recomendados|Description
---|---|---
-Max-Texture-size|1024 o 2048| Retoque el valor para mejorar la calidad de las texturas, el valor predeterminado es 512 x 512. Un valor mayor afectará significativamente al tamaño de archivo del entorno, por lo que debe tener en cuenta el límite de 256 MB.
-min-versión|1803|Los entornos personalizados solo se admiten en las versiones de Windows >= 1803. Esta marca quitará las texturas de las versiones anteriores y reducirá el tamaño de archivo del activo final.

Por ejemplo:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Probar el entorno

Una vez que tenga el entorno. glb final, estará listo para probarlo en el casco. Comience en el paso 2 de la sección ["probar un entorno de ejemplo"](#trying-a-sample-environment) para usar su entorno personalizado como inicio de realidad mixta. 

## <a name="sending-feedback"></a>Envío de opiniones

Mientras estamos evaluando esta característica experimental, estamos interesados en aprender cómo está usando entornos personalizados, los errores que puede encontrar y cómo le gusta la característica. Comparta cualquier comentario para crear y usar entornos domésticos personalizados en los [foros para desarrolladores](https://forums.hololens.com/categories/custom-home-environments).

## <a name="troubleshooting-and-tips"></a>Solución de problemas y sugerencias

### <a name="how-do-i-change-the-name-of-the-environment"></a>Cómo cambiar el nombre del entorno?

El nombre de archivo de la carpeta entornos se usará en el selector de lugares. Para cambiar el nombre de su entorno, cambie el nombre del archivo de entorno y, a continuación, reinicie el portal de realidad mixta.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Cómo quitar entornos personalizados del selector My Places?

Para quitar un entorno personalizado, abra la carpeta entornos en el equipo ( `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` ) y elimine el entorno. Una vez que reinicie el portal de realidad mixta, este entorno ya no aparecerá en el selector de lugares. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>¿Cómo predeterminada a mi entorno personalizado favorito?

Actualmente no se puede cambiar el entorno predeterminado. Cada vez que reinicie el portal de realidad mixta, se le devolverá al entorno de la casa de acantilado. 

### <a name="i-spawn-into-a-blank-space"></a>He generado en un espacio en blanco

Windows Mixed Reality [no es compatible con entornos que superan los 256 MB](#environment-limits). Cuando un entorno supera este límite, lo hará en el cuadro de Sky vacío sin ningún modelo.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Se tarda mucho tiempo en cargar mi entorno

Puede Agregar optimizaciones opcionales a su entorno para que se cargue más rápido. Consulte ["optimización del entorno"](#optimizing-your-environment) para obtener más información.

### <a name="the-scale-of-my-environment-is-incorrect"></a>La escala de mi entorno es incorrecta

Windows Mixed Reality traduce las unidades de glTF a 1 medida cuando se cargan entornos. Si el entorno carga una escala inesperada, compruebe su exportador para asegurarse de que está modelando en una escala de 1 metro. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>La ubicación de generación en mi entorno es incorrecta

La ubicación de generación predeterminada se encuentra en 0, 0, 0 en el entorno. Actualmente no es posible personalizar esta ubicación, por lo que debe modificar el punto de generación exportando el entorno con el origen situado en el punto de generación que desee.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>El audio no suena correctamente en el entorno

Al crear el entorno personalizado, utilizará una simulación de representación acústica que no coincide con el espacio físico que ha creado. El sonido puede proponerse de direcciones equivocadas y puede sonar silenciado. 

## <a name="see-also"></a>Consulte también
* [Convertidor de activos de Windows Mixed Reality (en GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)

