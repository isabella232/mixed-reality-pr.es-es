---
title: Uso compartido de movimientos de objetos con varios usuarios
description: Siga este curso para aprender a compartir movimientos de objetos con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, multi-user capabilities, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: c9a37dd94083b796da6d5fba2727d739112e411b494af5882ad08525e733a722
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200826"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Uso compartido de movimientos de objetos con varios usuarios

En este tutorial, aprenderá a compartir los movimientos de objetos para que todos los participantes de una experiencia compartida puedan colaborar y ver las interacciones de los demás.

## <a name="objectives"></a>Objetivos

* Configurar el proyecto para compartir los movimientos de los objetos
* Aprender a crear una aplicación de colaboración de varios usuarios básica

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, agregaras elementos prefabricados del tutorial para preparar la escena.

En la ventana "Jerarquía", expanda el objeto **MixedRealityPlayspace** y seleccione el objeto secundario **Cámara principal**; a continuación, en la ventana Inspector, use el botón **Agregar componente** para agregar el componente **Administrador de cámara de AR (script)** al objeto **Cámara principal**:

![Unity con el componente Administrador de cámara de AR configurado parcialmente](images/mr-learning-sharing/sharing-04-section1-step1-0.png)

En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** y arrastre el elemento prefabricado **TableAnchor** para colocarlo encima del objeto **SharedPlayground** de la ventana Hierarchy (Jerarquía) y agregarlo a la escena como elemento secundario del objeto SharedPlayground:

![Unity con el objeto prefabricado TableAnchor recién agregado seleccionado](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

En la ventana Jerarquía, asegúrese de que el objeto **MixedRealityPlayspace** está expandido y de que el objeto **TableAnchor** está seleccionado. Arrastre el componente **Cámara principal** al campo **Cámara** del componente **Origen de la sesión de AR** de **TableAnchor**:

![Unity con la asignación de la cámara principal del origen de sesión de AR configurada](images/mr-learning-sharing/sharing-04-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Configuración de PUN para crear instancias de los objetos

En esta sección, configurará el proyecto para usar la experiencia Rover Explorer creada durante los [tutoriales de introducción](mr-learning-base-01.md) y definirá dónde se crearán las instancias.

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Rover Explorer Prefab** (Elemento prefabricado de explorador rover), asigne el elemento prefabricado **RoverExplorer_Complete_Variant** desde la carpeta de recursos.

![Unity con el componente de Photon Room (Sala de Photon) configurado parcialmente](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Con el objeto secundario **NetworkLobby** seleccionado, en la ventana Jerarquía, expande el objeto **TableAnchor**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Rover Explorer Location** (Ubicación del explorador rover), asigne el objeto secundario TableAnchor > **Table** (Tabla) desde la ventana Hierarchy (Jerarquía).

![Unity con el componente de Photon Room (Sala de Photon) configurado](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Prueba de la experiencia con el movimiento de objetos compartidos

Si ahora compila e implementa el proyecto de Unity en su dispositivo HoloLens y, después, vuelve a Unity, presione el botón Reproducir para entrar en el modo de juego. Mientras la aplicación se ejecuta en HoloLens, verá que el objeto se mueve en Unity cuando lo mueve en HoloLens:

![Animación que muestra Unity con objetos en red](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Enhorabuena

Ha configurado correctamente el proyecto para que los movimientos de los objetos se sincronicen y los usuarios puedan ver que los objetos se mueven cuando otros usuarios los mueven. En el siguiente tutorial, implementará la funcionalidad para alinear la experiencia en el mundo físico. Esto garantizará que los usuarios se vean entre sí en su ubicación física real y, por tanto, los objetos aparezcan en la misma posición y rotación física para todos los usuarios.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 5. Integración de Azure Spatial Anchors en una experiencia compartida](mr-learning-sharing-05.md)
