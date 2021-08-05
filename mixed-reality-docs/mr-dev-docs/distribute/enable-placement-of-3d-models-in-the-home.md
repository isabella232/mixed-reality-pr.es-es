---
title: Habilitación de la colocación de modelos 3D en el hogar
description: Obtenga información sobre cómo colocar modelos 3D desde su sitio web o aplicación en la Windows Mixed Reality principal.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, model, place in home, place, world, modeling, ambiente principal, web, app, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 29761cb2a8725221a3be90187488cb13bf6643e4ff334a1edca73e633e7b1d4c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186801"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Habilitación de la colocación de modelos 3D en el ambiente principal

> [!NOTE]
> Esta característica se agregó como parte de la actualización Windows 10 [abril de 2018.](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) Las versiones anteriores Windows no son compatibles con esta característica.

La [Windows Mixed Reality principal es](../discover/navigating-the-windows-mixed-reality-home.md) el punto de partida en el que los usuarios se desatensan antes de iniciar aplicaciones. En algunos escenarios, las aplicaciones 2D (como la aplicación Hologramas) permiten la colocación de modelos 3D directamente en el ambiente principal como decoración o para una inspección más completa en 3D. El *protocolo* agregar modelo permite enviar un modelo 3D desde su sitio web o aplicación directamente a la página principal de Windows Mixed Reality, donde se conservará como los iniciadores de aplicaciones [3D,](3d-app-launcher-design-guidance.md)las aplicaciones 2D y los hologramas. 

Por ejemplo, si está desarrollando una aplicación que muestra un catálogo de piezas 3D para diseñar un espacio, use el protocolo agregar modelo para permitir a los usuarios colocar esos modelos de productos 3D del catálogo.  Una vez colocados en el mundo, los usuarios pueden mover, cambiar el tamaño y quitar estos modelos 3D como otros hologramas del hogar. En este artículo se proporciona información general sobre cómo implementar el protocolo add *model* para permitir que los usuarios decoren su mundo con objetos 3D desde la aplicación o la web.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Agregar protocolo de modelo</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>Conceptos básicos

Hay dos pasos para habilitar la colocación de modelos 3D en el Windows Mixed Reality principal:
1. [Asegúrese de que el modelo 3D es compatible con el Windows Mixed Reality principal.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
2. Implemente *el protocolo agregar modelo* en la aplicación o página web (este artículo).

## <a name="implementing-the-add-model-protocol"></a>Implementación del protocolo *add model*

Una vez que tenga un [modelo 3D compatible,](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)puede implementar el protocolo add *model* activando el siguiente URI desde cualquier página web o aplicación:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Si el URI apunta a un recurso remoto, se descargará automáticamente y se colocará en el hogar. Los recursos locales se copiarán en la carpeta de ambiente principal de datos de la aplicación antes de colocarse en la página principal. Se recomienda diseñar la experiencia para tener en cuenta los escenarios en los que el usuario podría ejecutar una versión anterior de Windows que no admite esta característica ocultando el botón o deshabilitándose si es posible. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Invocación del protocolo *de adición de modelo* desde una aplicación Windows plataforma universal:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Invocación del protocolo *add model desde* una página web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Consideraciones sobre los cascos envolventes (VR)

* En el caso de los cascos envolventes (VR), el Portal de realidad mixta no tiene que ejecutarse antes de invocar el *protocolo add model*. En este caso, el *protocolo* agregar modelo iniciará el Portal de realidad mixta colocará el objeto directamente donde el casco mira una vez que llegue a la ambiente principal. 
* Al invocar el protocolo agregar *modelo* desde el escritorio con el Portal de realidad mixta ya en ejecución, asegúrese de que el casco esté "activo". Si no es así, la selección de ubicación no se realiza correctamente. 

## <a name="see-also"></a>Vea también

* [Creación de modelos 3D para su uso en el Windows Mixed Reality principal](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)