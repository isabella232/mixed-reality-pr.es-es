---
title: Habilitación de la colocación de modelos 3D en el hogar
description: Cómo colocar modelos 3D desde su sitio web o aplicación en la Página principal de Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, lugar en casa, lugar, mundo, modelado, Inicio de la realidad mixta, Web, aplicación, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 192c403ce50c3a47fb19f644af78d1150bb9aa3f
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703191"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Habilitación de la colocación de modelos 3D en el ambiente principal

> [!NOTE]
> Esta característica se agregó como parte de la [actualización 2018 de abril de Windows 10](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018). Las versiones anteriores de Windows no son compatibles con esta característica.

La [Página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones. En algunos escenarios, las aplicaciones 2D (como la aplicación de hologramas) permiten colocar los modelos 3D directamente en la Página principal de la realidad mixta como decoración o para realizar más inspecciones en 3D completo. El *Protocolo agregar modelo* le permite enviar un modelo 3D desde su sitio web o aplicación directamente a la Página principal de Windows Mixed Reality, donde se conservará como [iniciadores de aplicaciones 3D](3d-app-launcher-design-guidance.md), aplicaciones 2D y hologramas. 

Por ejemplo, si está desarrollando una aplicación que muestra un catálogo de mobiliario 3D para diseñar un espacio, puede usar el *Protocolo agregar modelo* para permitir que los usuarios coloquen esos modelos de mobiliario 3D desde el catálogo. Una vez colocado en el mundo, los usuarios pueden moverse, cambiar de tamaño y quitar estos modelos 3D igual que otros hologramas en el hogar. En este artículo se proporciona información general sobre la implementación del *Protocolo de adición de modelos* para que pueda empezar a permitir a los usuarios decorar su mundo con objetos 3D desde la aplicación o la Web.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Agregar protocolo de modelo</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>Información general

Hay 2 pasos para habilitar la selección de ubicación de modelos 3D en la Página principal de Windows Mixed Reality:
1. [Asegúrese de que el modelo 3D es compatible con la Página principal de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implemente el *Protocolo de adición de modelos* en la aplicación o la página web (este artículo).

## <a name="implementing-the-add-model-protocol"></a>Implementación del *Protocolo Add Model*

Una vez que tenga un [modelo 3D compatible](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), puede implementar el *Protocolo agregar modelo* activando el URI siguiente desde cualquier página web o aplicación:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Si el URI apunta a un recurso remoto, se descargará automáticamente y se colocará en el hogar. Los recursos locales se copiarán en la carpeta de datos de la aplicación de la Página principal de la realidad mixta antes de colocarse en el hogar. Se recomienda diseñar su experiencia para tener en cuenta los escenarios en los que el usuario podría estar ejecutando una versión anterior de Windows que no admita esta característica ocultando el botón o deshabilitando si es posible. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Invocar el *Protocolo agregar modelo* desde una aplicación plataforma universal de Windows:

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Invocar el *Protocolo de agregar modelo* desde una página web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Consideraciones sobre los auriculares envolventes (VR)

* En el caso de los auriculares envolventes (VR), el portal de realidad mixta no tiene que estar en ejecución antes de invocar el *Protocolo de adición del modelo*. En este caso, el *Protocolo de adición del modelo* iniciará el portal de realidad mixta y colocará el objeto directamente, donde el casco está mirando una vez que llega a la Página principal de la realidad mixta. 
* Al invocar el *Protocolo agregar modelo* desde el escritorio con el portal de realidad mixta que ya se está ejecutando, asegúrese de que el casco esté "activo". Si no es así, la selección de ubicación no se realizará correctamente. 

## <a name="see-also"></a>Consulte también

* [Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)
