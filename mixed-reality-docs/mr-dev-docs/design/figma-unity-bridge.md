---
title: MrTK Figma Bridge para Unity
description: MRTK Figma Bridge for Unity permite traer el diseño de Figma Toolkit a Unity
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: Figma, Sketch, Adobe XD, design, designer, design file, UX design, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053898"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>MRTK Figma Bridge para Unity (beta)

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

MRTK Figma Bridge para Unity le permite traer el diseño de Figma Toolkit a Unity. El puente puede importar el diseño de interfaz de usuario creado con MRTK Figma Toolkit y, a continuación, crea instancias de los elementos prefabs de MRTK correspondientes con la posición y el tamaño adecuados. Figma Bridge ayudará a diseñar el proceso de integración y la colaboración entre diseñadores y desarrolladores.


Consulte [la página de Toolkit MrTK Figma](figma-toolkit.md) para obtener información sobre Figma Toolkit que es el archivo de diseño con HoloLens 2 de interfaz de usuario de estilo.

## <a name="prerequisites"></a>Requisitos previos
- Consulte [Instalación de las herramientas](/windows/mixed-reality/develop/install-the-tools) para el software necesario para el Mixed Reality desarrollo
- Unity 2019 o posterior
- [MRTK-Unity 2.7.0 o posterior](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **Requiere MRTK-Unity 2.7.0 o superior**
> 
> Dado que Figma Toolkit y Figma Bridge se basan en los requisitos previos de MRTK 2.7.0, se requiere MRTK 2.7.0 o una versión posterior. Cuando se usa con una versión inferior de MRTK, algunos componentes no se traducirán correctamente.

## <a name="how-to-use-mrtk-figma-bridge"></a>Uso de MRTK Figma Bridge

### <a name="1-installation"></a>1. Instalación

Figma Unity Bridge se puede instalar a través [de Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool). Descargue y ejecute Mixed Reality Feature Tool.

En **la página Detectar** características, en **Mixed Reality Toolkit** sección, seleccione **MRTK Figma Unity Bridge**. Siga los pasos para finalizar mr feature tool y volver al proyecto de Unity. Unity importará el paquete para MRTK Figma Bridge.

### <a name="2-open-figma-bridge-window"></a>2. Abrir la ventana del puente de Figma

Una vez que se haya realizado el proceso de importación, podrá encontrar Figma Bridge en el **menú Mixed Reality > Toolkit > Figma Bridge.**

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3. Generar y escribir el token de Figma

En el sitio web de Figma, haga clic en el menú Figma en la esquina superior izquierda y abra Ayuda y cuenta > configuración de la cuenta. Genere un nuevo token de acceso personal en la sección "Tokens de acceso personal".

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4. Escriba el identificador de un documento figma.
Cada documento de Figma tiene un identificador único en la dirección URL. Copie y pegue este identificador en Figma Bridge.

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

Haga **clic en Obtener** archivo para descargar el archivo Figma. Para descargar otros archivos Figma, escriba un nuevo identificador.

Haga **clic en Cargar** archivo para abrir un archivo Figma.

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5. Compilación de una página

Figma Bridge mostrará la lista de páginas en el archivo Figma. Compruebe las páginas que desea compilar en Unity. Haga clic **en el botón Compilar** páginas.

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6. Actualizar un documento para ver si hay cambios

Puede modificar el archivo Figma en la web (o mediante el editor de escritorio) y hacer clic en **Actualizar** para recuperar los cambios. Haga clic **en Compilar páginas** para compilar con actualizaciones. De este modo, puede iterar fácilmente el diseño en Figma y verlo en Unity.



## <a name="see-also"></a>Consulta también
* [Kit de herramientas de Figma](figma-toolkit.md)
* [Cursores](cursors.md)
* [Haces de mano](point-and-commit.md)
* [Botón](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipulación](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Menú Cerca](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Información sobre herramientas](tooltip.md)
* [Claqueta](slate.md)
* [Control deslizante](slider.md)
* [Sombreador](shader.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)
