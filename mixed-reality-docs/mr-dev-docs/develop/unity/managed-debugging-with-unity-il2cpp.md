---
title: Depuración administrada con Unity IL2CPP
description: En este artículo se explica cómo ejecutar un depurador administrado en el proyecto de IL2CPP para UWP de Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, depuración, il2cpp, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010246"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Depuración administrada con Unity IL2CPP

Siga estos pasos para asociar un depurador administrado a la compilación de UWP IL2CPP para HoloLens y HoloLens 2.

1. Deberá estar en una red que admita la [multidifusión](https://en.wikipedia.org/wiki/Multicast).
2. Vaya a la **configuración de publicación de UWP funcionalidades** y compruebe **InternetClientServer** y **PrivateNetworkClientServer**:

    ![Funcionalidades de configuración de publicación de UWP](images/il2cpp-debugging-capabilities.png)

3. Configurar las opciones de compilación de UWP para Unity:
    - Compilación de desarrollo
    - Depuración de script
    - Esperar al depurador administrado (opcional)

    ![Configuración de compilación de UWP](images/il2cpp-debugging-build.png)

4. Compilar en Unity.
5. Compile e implemente desde la solución de Visual Studio en el dispositivo. Debe compilar con las configuraciones de **depuración** o de **lanzamiento** . La configuración **maestra** deshabilita el generador de perfiles de Unity y puede impedir la depuración óptima. Opcionalmente, compruebe **Internet (cliente & servidor)** y **redes privadas (servidor de & de cliente)** en la lista de capacidades de Package. appxmanifest en la solución.
6. Asegúrese de que el dispositivo está conectado a la misma red que el equipo e inicie la aplicación en el dispositivo.
7. Asegúrese de que el dispositivo **no está** conectado al equipo a través de USB.
8. Haga doble clic en uno de los scripts en Unity y vaya a la solución de Visual Studio que se abre para ver y editar.
9. Debug: > adjuntar el depurador de Unity.

    ![Adjuntar depurador de Unity](images/il2cpp-debugging-attach.png)

10. Seleccione el dispositivo en la lista y haga clic en "Aceptar" para adjuntarlo.

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
