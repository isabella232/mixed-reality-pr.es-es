---
title: Introducción a los tutoriales de MRTK
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta desde cero.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, solvers, eye-tracking, voice commands
ms.localizationpriority: high
ms.openlocfilehash: abee2163c3b92897396ea35cc43ae025e8e7b804
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175484"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1. Introducción a los tutoriales de MRTK

¡Le damos la bienvenida a la serie de tutoriales de introducción! En el transcurso de estos tutoriales, aprenderá sobre Mixed Reality Toolkit (MRTK) y algunas de las características que ofrece. También creará una experiencia de realidad mixta en la que el usuario podrá explorar un holograma basado en el vehículo explorador de Marte Curiosity de la NASA. Al final de esta serie, tendrá un buen dominio de MRTK y de cómo puede acelerar el proceso de desarrollo.

Los tutoriales de esta serie están diseñados para realizarse de forma secuencial, por lo que debe repasarlos en el orden correcto:

1. [Introducción](mr-learning-base-01.md) (ya está aquí)
2. [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md)
3. [Configuración de los perfiles de MRTK](mr-learning-base-03.md)
4. [Posicionamiento de los objetos en la escena](mr-learning-base-04.md)
5. [Creación de contenido dinámico mediante solucionadores](mr-learning-base-05.md)
6. [Creación de interfaces de usuario](mr-learning-base-06.md)
7. [Interacción con objetos 3D](mr-learning-base-07.md)
8. [Uso del seguimiento ocular](mr-learning-base-08.md)
9. [Uso de los comandos de voz](mr-learning-base-09.md)

## <a name="objectives"></a>Objetivos

* Aprender a configurar Unity para MRTK
* Aprender a crear e implementar en su dispositivo
* Aprender a usar algunas de las características importantes de MRTK
* Crear una experiencia de realidad mixta completa

## <a name="prerequisites"></a>Requisitos previos

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)
* [SDK de Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) versión 10.0.18362.0 o posterior
* Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020.3 LTS o Unity 2019.4 LTS instalado **(OpenXR requiere 2020.3.8 o posterior para evitar errores**)

Al instalar Unity, asegúrese de comprobar los siguientes componentes en **"Platforms"** (Plataformas).

* **Compatibilidad con la compilación de la Plataforma universal de Windows**
* **Compatibilidad con la compilación de Windows (IL2CPP)**

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

Si instaló Unity sin estas opciones, puede agregarlas mediante el menú **"Add Modules"** (Agregar módulos) de Unity Hub.

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> La versión de MRTK recomendada para esta serie de tutoriales es MRTK 2.7.2.

> [!Important]
> Esta serie de tutoriales admite Unity 2020 LTS (actualmente 2020.3.x) si usa Open XR o el complemento de XR de Windows y también Unity 2019 LTS (actualmente 2019.4.x) si usa WSA heredado o el complemento de XR de Windows. Esta sustituye los requisitos de versión de Unity descritas en los requisitos previos vinculados anteriormente.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 2. Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md)
