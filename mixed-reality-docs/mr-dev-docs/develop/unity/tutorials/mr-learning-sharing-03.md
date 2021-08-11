---
title: Conexión de varios usuarios
description: Siga este curso para aprender a conectar a varios usuarios en una aplicación de realidad mixta de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, multi-user capabilities, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: ba8a29844489a9153f970f6e39ff2022701c845711ffd9abc232d8da8eeb2e32
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200741"
---
# <a name="3-connecting-multiple-users"></a>3. Conexión de varios usuarios

En este tutorial, aprenderás a conectar varios usuarios como parte de una experiencia compartida en directo. Al final del tutorial, podrá ejecutar la aplicación en varios dispositivos y hacer que todos los usuarios vean cómo se mueve el avatar de los demás en tiempo real.

## <a name="objectives"></a>Objetivos

* Aprender a conectar varios usuarios en una experiencia compartida

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.

En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK.Tutorials.MultiUserCapabilities** > carpeta **Prefabs** (Recursos prefabricados) y, a continuación, haga clic y arrastre el siguiente objeto prefabricado a la ventana Jerarquía para agregarlos a la escena:

* Objeto prefabricado **NetworkLobby**
* Objeto prefabricado **SharedPlayground**

![Unity con los objetos prefabricados NetworkLobby y SharedPlayground recién agregados seleccionados](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

En la ventana Proyecto, desplácese hasta **Assets** (Recursos)  > **MRTK.Tutorials.AzureSpatialAnchors** > carpeta **Prefabs** (Recursos prefabricados) y haga clic y arrastre el siguiente objeto prefabricado a la ventana Jerarquía para agregarlo a la escena:

* Objeto prefabricado **DebugWindow**

![Unity con el objeto prefabricado DebugWindow recién agregado seleccionado](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Configuración de PUN para crear una instancia del elemento prefabricado del usuario

En esta sección, configurará el proyecto para usar el elemento prefabricado PhotonUser que creó en la sección anterior.

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Photon User Prefab** (Elemento prefabricado de usuario de Photon), asigna el elemento **PhotonUser** de la carpeta Recursos.

![Unity con el componente de Photon Room (Sala de Photon) configurado parcialmente](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Prueba de la experiencia con varios usuarios

Si ahora compila e implementa el proyecto de Unity en su dispositivo HoloLens, vuelva a Unity y entre en el Modo Juego. Mientras la aplicación se ejecuta en HoloLens, verá que el avatar de usuario de HoloLens se mueve cuando mueve la cabeza (HoloLens):

![Animación que muestra Unity con usuarios de red](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> La aplicación necesita conectarse a Photon, por lo que debe asegurarse de que el equipo o dispositivo esté conectado a Internet.

## <a name="congratulations"></a>Enhorabuena

Has configurado correctamente el proyecto para permitir que varios usuarios se conecten a la misma experiencia y vean los movimientos de los demás. En el siguiente tutorial, implementarás la funcionalidad para que los movimientos de objetos también se compartan entre varios dispositivos.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 4. Uso compartido de movimientos de objetos con varios usuarios](mr-learning-sharing-04.md)
