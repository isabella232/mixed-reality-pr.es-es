---
title: Barra de la aplicación
description: Información general sobre la barra de aplicaciones en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, barra de aplicaciones,
ms.openlocfilehash: 1ecb43d25a4353ff4c3bd8350efaab877900a5b979cd42d2c8d1cb91ce32ae0c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198282"
---
# <a name="app-bar"></a>Barra de la aplicación

![Barra de la aplicación](../images/app-bar/MRTK_AppBar_Main.png)

La barra de aplicación es un componente de interfaz de usuario que se usa junto con el script [de control de límites.](bounds-control.md) Agrega controles de botón a un objeto con la intención de manipularlo. Con el botón "Ajustar", la interfaz de control de límites de un objeto se puede des-/ activar. El botón "Quitar" debe quitar el objeto de la escena.

## <a name="how-to-use-app-bar"></a>Uso de la barra de aplicaciones

Arrastre y coloque `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) en la jerarquía de escena. En el panel inspector del componente, asigne cualquier objeto  con un control de límites como cuadro de límite de destino para agregarle la barra de aplicación.

**Importante:** La opción de activación del control de límites para el objeto de destino debe ser "Activar manualmente".

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
