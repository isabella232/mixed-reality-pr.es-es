---
title: Lenguaje básico
description: Obtenga información sobre los detalles del lenguaje principal de Maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototyping, Mixed Reality, Virtual Reality, VR, MR, Feedback, Centro de opiniones, bugs
ms.openlocfilehash: 290b1442c3cc7fed10b315f4beeebfe2eab4a775d4909d5411c651362e24d94e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197405"
---
# <a name="maquettescript-core-language-details"></a>Detalles del lenguaje principal de MaquetteScript

<!-- TODO(Harrison): Need consolidated logo with text -->
![Detalles del lenguaje principal del ](../images/MaquetteIcon.png) logotipo de MaquetteScript

## <a name="accessing-maquette-object-and-namespace"></a>Acceso a `Maquette` objetos y espacios de nombres

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette expone objetos e interfaces internos en JavaScript a través del `Maquette` objeto y sus secundarios. Esta funcionalidad se describe en la documentación sobre objetos [y espacios de nombres de Maquette.](https://www.maquette.ms/doc_staging/objects/Maquette.html) 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
El objeto tiene funciones de nivel superior para facilitar la interacción con Maquette y facilitar la resolución de `Maquette` problemas repetitivos. Esto se describe en la documentación de [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).

## <a name="maquette-startup-and-loading"></a>Inicio y carga de Maquette

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette cargará y evaluará archivos de JavaScript específicos para habilitar la configuración, la instalación y la inicialización en los siguientes momentos:

Durante el inicio de Maquette:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Cada vez que se carga un proyecto:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

Los proyectos cargan sus respectivos scripts de proyecto:
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>Implementación de JavaScript

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
El intérprete de JavaScript que se usa en Maquette se basa en [Jint](https://github.com/sebastienros/jint). Jint es compatible con ECMAScript 5.1 y admite extensiones [adicionales de ECMAScript 6.](https://github.com/sebastienros/jint/issues/343) 

La extensión `.mqjs` se usa para distinguir los archivos JavaScript de Maquette de JavaScript normal.

## <a name="see-also"></a>Consulte también 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->