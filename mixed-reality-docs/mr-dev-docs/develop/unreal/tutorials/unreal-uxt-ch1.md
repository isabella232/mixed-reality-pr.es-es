---
title: 1. Introducción
description: Parte 1 de 6 de una serie de tutoriales para compilar una aplicación de ajedrez con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 465215efd953c0acb9f2d80a2905ee06963c5f8c
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609726"
---
# <a name="1-getting-started"></a>1. Introducción

Independientemente de que no esté familiarizado con la realidad virtual o que sea un profesional experimentado, está en el lugar adecuado para empezar su camino con [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) y [Unreal Engine](https://www.unrealengine.com/en-US/). En esta serie de tutoriales se ofrece una guía paso a paso sobre cómo compilar una aplicación de ajedrez interactiva con el [complemento UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), parte de [Mixed Reality Toolkit para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). El complemento le ayudará a agregar características comunes de UX a sus proyectos con código, planos técnicos y ejemplos. 

![Escena final en la ventanilla](images/unreal-uxt/5-endscene.PNG)

Al final de la serie tendrá experiencia en las siguientes tareas:
* Inicio de un nuevo proyecto
* Configuración para la realidad mixta
* Trabajo con la entrada de usuario
* Adición de botones
* Reproducción en un emulador o un dispositivo

## <a name="prerequisites"></a>Requisitos previos

Asegúrese de haber instalado lo siguiente antes de empezar:
* Windows 10 1809 o posterior
* SDK de Windows 10 10.0.18362.0 o posterior
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 o posterior
* Un dispositivo Microsoft HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) o un emulador
* Visual Studio 2019 con las cargas de trabajo siguientes

### <a name="installing-visual-studio-2019"></a>Instalación de Visual Studio 2019

En primer lugar, asegúrese de configurar todos los paquetes de Visual Studio necesarios:
1. Instale la versión más reciente de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).
2. Instale las [cargas de trabajo](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads) siguientes:
    * Desarrollo de escritorio con C++
    * Desarrollo de escritorio de .NET
    * Desarrollo con la Plataforma universal de Windows

3. Instale los [componentes](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components) siguientes:
    * Compiladores, herramientas de compilación y entornos en tiempo de ejecución > herramientas de desarrollo para ARM64 en C++ de MSVC v142 - VS 2019 (versión más reciente)

Eso es todo. Está listo para continuar e iniciar el proyecto de ajedrez.

[Sección siguiente: 2. Inicialización del proyecto y primera aplicación](unreal-uxt-ch2.md)