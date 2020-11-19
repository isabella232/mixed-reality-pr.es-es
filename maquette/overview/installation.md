---
title: Instalación de Maquette
description: Obtenga información sobre cómo instalar y configurar Maquette en VSCode.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototipo, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935554"
---
# <a name="installing-maquette"></a>Instalación de Maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![Instalación del logotipo ](../images/MaquetteIcon.png) MaquetteScript

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
El desarrollo de MaquetteScript se realiza principalmente dentro de VSCode. MaquetteScript se puede ejecutar desde el script contenido en `.mqjs` archivos y también a través de una interfaz especial de extensión VSCode. La integración entre VSCode y Maquette para habilitar la interfaz de extensión se logra con una extensión MaquetteScript VSCode.

## <a name="installing-the-vscode-extension"></a>Instalación de la extensión VSCode

* Descargue e instale [VSCode](https://code.visualstudio.com). 

La extensión Maquette de JavaScript está en [el Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).

* Ejecute el [procedimiento de instalación de la extensión](vscode:extension/ms-maquette.vscode-maquette-javascript).

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Habilitar scripting

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

Para que el scripting sea accesible durante la versión preliminar:

* Coloque un archivo con el nombre `scripting.enabled` en el directorio de documentos de los usuarios para Maquette en: `~/Documents/Maquette/Settings` .

Después de la instalación, el scripting se deshabilitará de forma predeterminada por motivos de seguridad.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Para habilitar la ejecución de scripts, actívelo en la pestaña principal de la ventana complementaria o en el archivo de configuración de JSON.

![Habilitación del scripting en VS Code](images/IntroductionEnableScripting.png)


