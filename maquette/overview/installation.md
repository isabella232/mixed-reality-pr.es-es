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
# <a name="installing-maquette"></a><span data-ttu-id="d60cb-104">Instalación de Maquette</span><span class="sxs-lookup"><span data-stu-id="d60cb-104">Installing Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text. -->
<span data-ttu-id="d60cb-105">![Instalación del logotipo ](../images/MaquetteIcon.png) MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="d60cb-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Installation</span></span>

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
<span data-ttu-id="d60cb-106">El desarrollo de MaquetteScript se realiza principalmente dentro de VSCode.</span><span class="sxs-lookup"><span data-stu-id="d60cb-106">MaquetteScript development is primarily done within VSCode.</span></span> <span data-ttu-id="d60cb-107">MaquetteScript se puede ejecutar desde el script contenido en `.mqjs` archivos y también a través de una interfaz especial de extensión VSCode.</span><span class="sxs-lookup"><span data-stu-id="d60cb-107">MaquetteScript can run from script contained in `.mqjs` files and also via a special VSCode extension interface.</span></span> <span data-ttu-id="d60cb-108">La integración entre VSCode y Maquette para habilitar la interfaz de extensión se logra con una extensión MaquetteScript VSCode.</span><span class="sxs-lookup"><span data-stu-id="d60cb-108">Integration between VSCode and Maquette to enable the extension interface is accomplished with a MaquetteScript VSCode extension.</span></span>

## <a name="installing-the-vscode-extension"></a><span data-ttu-id="d60cb-109">Instalación de la extensión VSCode</span><span class="sxs-lookup"><span data-stu-id="d60cb-109">Installing the VSCode Extension</span></span>

* <span data-ttu-id="d60cb-110">Descargue e instale [VSCode](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="d60cb-110">Download and install [VSCode](https://code.visualstudio.com).</span></span> 

<span data-ttu-id="d60cb-111">La extensión Maquette de JavaScript está en [el Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="d60cb-111">The Maquette javascript extension is in [the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span></span>

* <span data-ttu-id="d60cb-112">Ejecute el [procedimiento de instalación de la extensión](vscode:extension/ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="d60cb-112">Run the [installation procedure for the extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span></span>

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a><span data-ttu-id="d60cb-113">Habilitar scripting</span><span class="sxs-lookup"><span data-stu-id="d60cb-113">Enabling Scripting</span></span>

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

<span data-ttu-id="d60cb-114">Para que el scripting sea accesible durante la versión preliminar:</span><span class="sxs-lookup"><span data-stu-id="d60cb-114">To make scripting accessible during pre-release:</span></span>

* <span data-ttu-id="d60cb-115">Coloque un archivo con el nombre `scripting.enabled` en el directorio de documentos de los usuarios para Maquette en: `~/Documents/Maquette/Settings` .</span><span class="sxs-lookup"><span data-stu-id="d60cb-115">Put a file with the name `scripting.enabled` in the Users Documents directory for Maquette in: `~/Documents/Maquette/Settings`.</span></span>

<span data-ttu-id="d60cb-116">Después de la instalación, el scripting se deshabilitará de forma predeterminada por motivos de seguridad.</span><span class="sxs-lookup"><span data-stu-id="d60cb-116">After installation, scripting will be disabled by default for security reasons.</span></span>

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* <span data-ttu-id="d60cb-117">Para habilitar la ejecución de scripts, actívelo en la pestaña principal de la ventana complementaria o en el archivo de configuración de JSON.</span><span class="sxs-lookup"><span data-stu-id="d60cb-117">To enable execution of script, turn it ON in the main tab of the companion window or in the json settings file.</span></span>

![Habilitación del scripting en VS Code](images/IntroductionEnableScripting.png)


