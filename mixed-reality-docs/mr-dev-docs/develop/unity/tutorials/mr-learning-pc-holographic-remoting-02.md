---
title: Creación de una aplicación para equipos de comunicación remota holográfica
description: Siga este curso para aprender cómo crear una aplicación de PC para la comunicación remota de una experiencia de realidad mixta remota del equipo a HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, PC holographic remoting, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: d395801c20d95ee0fdddc144b4e28c841554fb5116f847574ec4a931d116026e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198042"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Creación de una aplicación para PC de comunicación remota holográfica

En este tutorial, aprenderá a crear una aplicación de PC que usa la comunicación remota holográfica para que pueda transmitir el trabajo en curso a HoloLens y verlo sin necesidad de compilarlo antes.

[Aprenda los conceptos básicos de la comunicación remota holográfica.](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

## <a name="objectives"></a>Objetivos

* Configurar Unity para la comunicación remota holográfica
* Aprender a compilar e implementar la aplicación con Visual Studio
* Desarrollo de una aplicación de comunicación remota holográfica y conexión a HoloLens

## <a name="configuring-the-capabilities"></a>Configuración de las funcionalidades

En la ventana **Project Settings** (Configuración del proyecto), expanda **Publishing Settings** (Configuración de la publicación), desplácese hacia abajo a la sección Capabilities (Funcionalidades) y seleccione la casilla de funcionalidad que aparece a continuación además de las funcionalidades ya existentes.

* Servidor cliente de Internet
* Servidor cliente de red privada

![Habilitación de funcionalidades](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a>Compilación de la aplicación para PC

La aplicación de comunicación remota holográfica ya está lista para compilarse en su PC. Siga los pasos que se indican a continuación y realice estos cambios para compilar esta aplicación en su PC.

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a>Prueba de la aplicación remota de comunicación remota holográfica

Para conectar la aplicación de PC a HoloLens 2, siga el proceso siguiente:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Instalación de la aplicación Remoting Player en el dispositivo HoloLens 2

* En HoloLens 2, visite la aplicación Store y busque "**Remoting Player**".
* Seleccione la aplicación **Remoting Player**.
* Pulse **Instalar** una vez para descargar e instalar la aplicación.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Conexión de la aplicación de comunicación remota holográfica para PC a Remoting Player

* Inicie **Remoting Player** en HoloLens.
* Tome nota de la **dirección IP** de HoloLens. **Remoting Player** la mostrará como un holograma en cuanto se inicie.
* Abra la aplicación de comunicación remota holográfica para PC en su PC.
* Una vez iniciada la aplicación, escriba la **dirección IP** y haga clic en el botón **Conectar** para conectarse.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió cómo crear una aplicación para la comunicación remota holográfica y a conectarse a HoloLens 2 en cualquier momento, lo que proporciona una manera de visualizar contenido 3D en realidad mixta. Una vez que HoloLens esté conectado a la aplicación de comunicación remota holográfica para PC, debería ver la experiencia de realidad mixta transmitida en el dispositivo HoloLens 2.
