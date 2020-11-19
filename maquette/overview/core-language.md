---
title: Lenguaje básico
description: Obtenga información sobre los detalles principales del lenguaje de Maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototipo, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935628"
---
# <a name="maquettescript-core-language-details"></a>Detalles de idioma de MaquetteScript Core

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette logo ](../images/MaquetteIcon.png) MaquetteScript Core Language details

## <a name="accessing-maquette-object-and-namespace"></a>Obtener acceso a `Maquette` objetos y espacios de nombres

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette expone objetos e interfaces internos en JavaScript a través del `Maquette` objeto y sus elementos secundarios. Esta funcionalidad se describe en el [objeto Maquette y](https://www.maquette.ms/doc_staging/objects/Maquette.html) en la documentación del espacio de nombres. 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
El `Maquette` objeto tiene funciones de nivel superior para facilitar la interacción con el propio Maquette y facilitar la resolución de problemas repetitivos. Esto se describe en la documentación de [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).

## <a name="maquette-startup-and-loading"></a>Inicio y carga de Maquette

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette cargará y evaluará determinados archivos JavaScript para habilitar la configuración, la instalación y la inicialización en las siguientes ocasiones:

Durante el inicio de Maquette:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Cada vez que se carga algún proyecto:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

Los proyectos cargan sus scripts de proyecto respectivos:
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>Implementación de JavaScript

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
El intérprete de JavaScript usado en Maquette se basa en [Jint](https://github.com/sebastienros/jint). Jint es compatible con ECMAScript 5,1 y admite [extensiones adicionales de ECMAScript 6](https://github.com/sebastienros/jint/issues/343). 

La extensión `.mqjs` se usa para distinguir los archivos de JavaScript de Maquette de JavaScript normal.

## <a name="see-also"></a>Vea también 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->