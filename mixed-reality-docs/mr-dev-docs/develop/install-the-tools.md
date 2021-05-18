---
title: Instalación de las herramientas
description: Comience aquí con las versiones más actuales de Unity y Visual Studio, y con las herramientas recomendadas para el desarrollo de HoloLens y VR.
author: thetuvix
ms.author: alexturn
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 03977467b27f7a4a70f241f25f3046675cd824ad
ms.sourcegitcommit: f77adfa23a98ccc0412eb6be5871ad4b1da0f755
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2021
ms.locfileid: "109740636"
---
# <a name="install-the-tools"></a>Instalación de las herramientas

Consigue las herramientas necesarias para compilar aplicaciones para Microsoft HoloLens y los cascos envolventes de Windows Mixed Reality (VR). No hay ningún SDK independiente para el desarrollo con Windows Mixed Reality. Tendrás que usar Visual Studio con el SDK de Windows 10.

¿No tienes un dispositivo de realidad mixta? Puedes instalar el [emulador de HoloLens](platform-capabilities-and-apis/using-the-hololens-emulator.md) para probar algunas funciones de las aplicaciones de realidad mixta sin necesidad de un dispositivo HoloLens. También puedes utilizar el [simulador de Windows Mixed Reality](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) para probar las aplicaciones de realidad mixta con unos cascos envolventes. 

Se recomienda instalar los motores de juego de Unity o Unreal, ya que es la manera más sencilla de empezar a crear aplicaciones de realidad mixta. Sin embargo, también puedes compilar en DirectX si quieres utilizar un motor personalizado.

Si usa Unity, puede utilizar la simulación de entrada de [Mixed Reality Toolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) para probar distintos tipos de interacciones de entrada, como el seguimiento de la mano y el seguimiento de los ojos. En el caso de los proyectos de Unreal, use el [complemento UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) para probar tanto las interacciones de entrada comunes como las características de la experiencia del usuario.

>[!TIP]
>Marca esta página como favorita y compruébala con regularidad para estar al día de la versión más reciente de cada herramienta recomendada para el desarrollo de realidad mixta.

<br>

## <a name="installation-checklist"></a>Lista de comprobación de la instalación

| Herramienta | Notas |
|---------|---------|
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (vínculo de instalación manual)</a><br><br>Instala la versión más reciente de Windows 10 para que el sistema operativo del equipo coincida con la plataforma para la que vas a compilar las aplicaciones de realidad mixta.  | **Instalación de Windows 10** <br> Puedes instalar la versión más reciente de Windows 10 mediante Windows Update en Configuración o mediante la creación de soportes de instalación a través del vínculo de la columna izquierda. <br><br>Consulta las [notas de la versión actual](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md) para más información acerca de las características de realidad mixta más recientes disponibles en cada versión de Windows 10. **Habilita el modo para desarrolladores en el equipo** en Configuración > Actualización y seguridad > Para programadores. <br><br> **Nota para equipos empresariales y de administración corporativa**<br>Si administra el equipo un departamento de TI de la organización, es posible que deba ponerse en contacto con ellos para la actualización. <br><br> **Versiones "N" de Windows**<br> Los cascos envolventes de Windows Mixed Reality no son compatibles con las versiones "N" de Windows. |
| ![Imagen del logotipo de Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 o superior)** (vínculo de instalación)</a> <br><br>Entorno de desarrollo integrado (IDE) completo para Windows, etc. Vas a utilizar Visual Studio para escribir código, depurar, realizar pruebas e implementar. | **Instalación de Visual Studio 2019** <br> Asegúrate de instalar las siguientes cargas de trabajo: <br><br>*● Desarrollo de escritorio con C++*<br>*● Desarrollo para la Plataforma universal de Windows (UWP)*<br><br>En la carga de trabajo de UWP, asegúrate de comprobar el siguiente componente opcional si vas a desarrollar para HoloLens:<br><br>*● Conectividad con dispositivo USB*<br><br>**Nota sobre la conectividad USB**<br>Debe activar la casilla **IP a través de USB** durante la instalación, que no está activada de manera predeterminada. Esto es necesario para comunicarse con HoloLens a través de USB.<br><br>**Nota acerca de Unity**<br>A menos que intencionadamente esté intentando instalar una versión más reciente (no LTS) de Unity, se recomienda *no* instalar la carga de trabajo de Unity como parte de la instalación de Visual Studio y, en su lugar, instalar la secuencia **Unity 2019 LTS**.<br><br>**Problemas conocidos**<br>Hay algunos problemas conocidos con la depuración de aplicaciones de realidad mixta en Visual Studio 2019, versión 16.0.  Asegúrate de actualizar a **Visual Studio 2019, versión 16.8 o superior**. |
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**SDK de Windows 10 (10.0.18362.0)** (vínculo de instalación manual)</a> <br><br>Proporciona los encabezados, bibliotecas, metadatos y herramientas más recientes para compilar aplicaciones de Windows 10 en HoloLens 2. | **Para compilar aplicaciones de HoloLens 2, debe instalar Windows SDK, compilación 18362 o posterior.**<br> <br> Si solo vas a desarrollar aplicaciones para cascos de Windows Mixed Reality o HoloLens (1.ª generación), puedes usar el SDK de Windows que instala Visual Studio 2017. |
| ![Logotipo de Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2162581" target="_blank">**Emulador de HoloLens 2 (Windows Holographic, versión 21H1, actualización de mayo de 2021)** (vínculo de instalación: 10.0.20346.1002)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador de HoloLens (Gen 1)** (vínculo de instalación: 10.0.17763.134)</a> <br><br>El emulador te permite ejecutar aplicaciones en una imagen de máquina virtual de HoloLens sin necesidad de un dispositivo HoloLens físico.<br> <br> | Consulta [Uso del emulador de HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) para más información sobre cómo empezar a trabajar con el emulador.<br> <br> **El sistema debe admitir Hyper-V** para que la instalación del emulador se realice correctamente. Consulta la sección Requisitos del sistema que aparece a continuación para obtener los detalles. <br> <br> **Nota sobre el emulador de HoloLens (1.ª generación)** <br>  Se requiere Visual Studio 2017 para completar correctamente la instalación. Si va a instalar el emulador de HoloLens (1.ª generación) con Visual Studio 2019, debe anular la selección de las plantillas de VS e [instalarlas desde Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Instalación del motor de su elección

Ahora que tiene Windows 10, Visual Studio y el SDK de Windows 10 listo para usar, instale y configure el motor de su elección. 

Si todavía necesita elegir un motor, consulte la [Introducción al desarrollo con Mixed Reality](./development.md?tabs=unity#what-technology-path-are-you-interested-in). 

[!INCLUDE[](includes/tools-overview.md)]