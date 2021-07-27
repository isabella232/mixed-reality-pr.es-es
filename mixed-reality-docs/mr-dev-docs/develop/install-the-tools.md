---
title: Instalación de las herramientas
description: Comience aquí con las versiones más actuales de Unity y Visual Studio, y con las herramientas recomendadas para el desarrollo de HoloLens y VR.
author: thetuvix
ms.author: alexturn
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 948783b8ad6df993b1a982c8d73846e40d96aff7
ms.sourcegitcommit: eb39526f9620f0459bd30e4484307892f4609334
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201626"
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
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (vínculo de instalación manual)</a><br><br>Instala la versión más reciente de Windows 10 para que el sistema operativo del equipo coincida con la plataforma para la que vas a compilar las aplicaciones de realidad mixta.  | **Instalación de Windows 10** <br> Puedes instalar la versión más reciente de Windows 10 mediante Windows Update en Configuración o mediante la creación de soportes de instalación a través del vínculo de la columna izquierda. <br><br>Consulta las [notas de la versión actual](/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md) para más información acerca de las características de realidad mixta más recientes disponibles en cada versión de Windows 10. **Habilita el modo para desarrolladores en el equipo** en Configuración > Actualización y seguridad > Para programadores. <br><br> **Nota para equipos empresariales y de administración corporativa**<br>Si administra el equipo un departamento de TI de la organización, es posible que deba ponerse en contacto con ellos para la actualización. <br><br> **Versiones "N" de Windows**<br> Los cascos envolventes de Windows Mixed Reality no son compatibles con las versiones "N" de Windows. |
| ![Imagen del logotipo de Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 o superior)** (vínculo de instalación)</a> <br><br>Entorno de desarrollo integrado (IDE) completo para Windows, etc. Vas a utilizar Visual Studio para escribir código, depurar, realizar pruebas e implementar. | **Instalación de Visual Studio 2019** <br> Asegúrate de instalar las siguientes cargas de trabajo: <br><br>*● Desarrollo de escritorio con C++*<br>*● Desarrollo para la Plataforma universal de Windows (UWP)*<br>*• Desarrollo de juegos con Unity (**si planea usar Unity**)*<br><br>Dentro de la carga de trabajo de UWP, **asegúrese de que los siguientes componentes estén incluidos para la instalación**:<br><br>*● SDK de Windows 10, versión 10.0.19041.0 o 10.0.18362.0*<br>*• Conectividad para dispositivos USB (necesario para implementar o depurar en HoloLens a través de USB)*<br>*• Herramientas de la Plataforma universal de Windows para C++ (v142) (se requiere cuando se usa Unity)*<br><br>**Tenga en cuenta HoloLens (1.ª generación) y los cascos de Windows Mixed Reality de escritorio**<br>Si solo va a desarrollar aplicaciones para cascos de Windows Mixed Reality de escritorio o HoloLens (1.ª generación), puede usar Visual Studio 2017 y el SDK de Windows que se instala.<br><br>**Problemas conocidos**<br>Hay algunos problemas conocidos con la depuración de aplicaciones de realidad mixta en Visual Studio 2019, versión 16.0.  Asegúrate de actualizar a **Visual Studio 2019, versión 16.8 o superior**. |
| ![Logotipo de Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2167725" target="_blank">**Emulador de HoloLens 2 (Windows Holographic, versión 21H1, actualización de julio de 2021)** (vínculo de instalación: 10.0.20348.1010)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador de HoloLens (Gen 1)** (vínculo de instalación: 10.0.17763.134)</a> <br><br>El emulador opcional le permite ejecutar aplicaciones en una imagen de máquina virtual de HoloLens sin necesidad de un dispositivo HoloLens físico.<br> <br> | Consulte [Uso del emulador de HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) para más información sobre cómo empezar a trabajar con el emulador opcional.<br> <br> **El sistema debe admitir Hyper-V** para que la instalación del emulador se realice correctamente. Consulta la sección Requisitos del sistema que aparece a continuación para obtener los detalles. <br> <br> **Nota sobre el emulador de HoloLens (1.ª generación)** <br>  Se requiere Visual Studio 2017 para completar correctamente la instalación. Si va a instalar el emulador de HoloLens (1.ª generación) con Visual Studio 2019, debe anular la selección de las plantillas de VS e [instalarlas desde Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Instalación del motor de su elección

Ahora que tiene Windows 10, Visual Studio y el SDK de Windows 10 listo para usar, instale y configure el motor de su elección.

> [!div class="nextstepaction"]
> [Elección del motor](choosing-an-engine.md)

## <a name="troubleshooting"></a>Solución de problemas

### <a name="setting-developer-mode-is-grayed-out"></a>La configuración del modo de desarrollador está atenuada

Si tiene problemas para habilitar el modo de desarrollador en el dispositivo, es posible que no sea el [propietario del dispositivo](/hololens/security-adminless-os). En el modo multiusuario, la persona que usa el dispositivo primero es el propietario del dispositivo: los usuarios posteriores no tendrán los permisos necesarios para habilitar el modo de desarrollador ni realizar otros cambios de configuración. Sin embargo, hay una excepción en la que el primer usuario puede no ser el propietario del dispositivo en un entorno de AutoPilot, como se detalla en la [documentación de seguridad de HoloLens](/hololens/security-adminless-os#device-owner).

Entre las posibles soluciones se incluyen:

* Hacer que el propietario del dispositivo active el modo de desarrollador antes de pasar el dispositivo a otros usuarios o desarrolladores
* Sugerir que su administrador de TI/MDM habilite la [directiva de CSP ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) para el dispositivo específico o para un grupo de dispositivos de desarrollador.
    * Esta directiva se puede establecer mediante [paquetes de aprovisionamiento](/hololens/hololens-provisioning) o mediante [MDM para dispositivos de HoloLens](/hololens/hololens-mdm-configure)
* Uso del complemento [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> Puede aprender más información sobre la administración del dispositivo en **[Introducción a la administración de dispositivos de HoloLens](/hololens/hololens-csp-policy-overview)** .

#### <a name="i-cant-deploy-over-usb"></a>No puedo implementar mediante USB

Si no puede implementar una aplicación directamente mediante USB, asegúrese de que cumple todos los requisitos de instalación indicados anteriormente y siga nuestro [tutorial detallado](unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).
