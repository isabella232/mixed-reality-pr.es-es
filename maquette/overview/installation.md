---
title: Instalación de Maquette
description: Obtenga información sobre cómo instalar y configurar Maquette en VSCode.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, creación de prototipos, Mixed Reality, Virtual Reality, VR, MR, Feedback, Centro de opiniones, bugs
ms.openlocfilehash: c31f461adbe553a5c10e7acfff3037ea0c2b65caf2bbe63bfc234e067a6369e8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214780"
---
# <a name="installing-maquette"></a>Instalación de Maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![Instalación ](../images/MaquetteIcon.png) de MaquetteScript del logotipo

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
El desarrollo de MaquetteScript se realiza principalmente en VSCode. MaquetteScript se puede ejecutar desde el script contenido en los archivos y también a través de `.mqjs` una interfaz de extensión de VSCode especial. La integración entre VSCode y Maquette para habilitar la interfaz de extensión se realiza con una extensión VSCode de MaquetteScript.

## <a name="installing-the-vscode-extension"></a>Instalación de la extensión VSCode

* Descargue e instale [VSCode.](https://code.visualstudio.com) 

La extensión de JavaScript de Maquette se encuentra [en Visual Studio Marketplace.](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)

* Ejecute el [procedimiento de instalación de la extensión](vscode:extension/ms-maquette.vscode-maquette-javascript).

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Habilitación de scripting

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

Para que el scripting sea accesible durante la versión anterior:

* Coloque un archivo con el nombre `scripting.enabled` en el directorio Documentos de usuarios de Maquette en: `~/Documents/Maquette/Settings` .

Después de la instalación, el scripting se deshabilitará de forma predeterminada por motivos de seguridad.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Para habilitar la ejecución del script, active esta opción en la pestaña principal de la ventana complementaria o en el archivo de configuración json.

![Habilitación de scripting en VS Code](images/IntroductionEnableScripting.png)


