---
title: Creación de una aplicación para equipos de comunicación remota holográfica
description: Siga este curso para aprender cómo crear una aplicación de PC para la comunicación remota de una experiencia de realidad mixta remota del equipo a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, PC holographic remoting, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392627"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Creación de una aplicación para PC de comunicación remota holográfica

En este tutorial, aprenderá cómo crear una aplicación de PC para la comunicación remota holográfica y a conectarse a HoloLens 2 en cualquier momento, lo que proporciona una manera de visualizar contenido 3D en realidad mixta.

## <a name="objectives"></a>Objetivos

* Configurar Unity para la comunicación remota holográfica
* Aprender a compilar e implementar la aplicación con Visual Studio
* Desarrollar una aplicación de comunicación remota holográfica y conectarla a HoloLens

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
