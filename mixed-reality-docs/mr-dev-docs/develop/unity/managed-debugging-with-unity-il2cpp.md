---
title: Depuración administrada con Unity
description: En este artículo se explica cómo ejecutar un depurador administrado en el proyecto de Unity IL2CPP para UWP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, Visual Studio, depuración, il2cpp, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, UWP
ms.openlocfilehash: 48f5fbd4b2ac217a3f840117595aa36fb3d7c10e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394509"
---
# <a name="managed-debugging-with-unity"></a>Depuración administrada con Unity

Siga estos pasos para asociar un depurador administrado a la compilación de Unity IL2CPP para UWP para HoloLens y HoloLens 2.

1. Deberá estar en una red que admita [multidifusión.](https://en.wikipedia.org/wiki/Multicast)
2. Vaya a **Funcionalidades de configuración de publicación de UWP** y compruebe **InternetClientServer** y **PrivateNetworkClientServer**:

    ![Funcionalidades de configuración de publicación de UWP](images/il2cpp-debugging-capabilities.png)

3. Configure las opciones de compilación de Unity para UWP:
    - Compilación de desarrollo
    - Depuración de script
    - Esperar a Managed Debugger (opcional)

    ![Configuración de compilación de UWP](images/il2cpp-debugging-build.png)

4. Compilación en Unity.
5. Compile e implemente desde la Visual Studio en el dispositivo. Debe compilar con las **configuraciones Debug** **o Release.** La **configuración** maestra deshabilita el profiler de Unity y puede impedir una depuración óptima. Opcionalmente, compruebe **Internet (servidor cliente &)** y redes privadas **(cliente & Server)** en la lista de funcionalidades de Package.appxmanifest en la solución.
6. Asegúrese de que el dispositivo está conectado a la misma red que el equipo e inicie la aplicación en el dispositivo.
7. Asegúrese de que el **dispositivo no está** conectado al equipo a través de USB.
8. Haga doble clic en uno de los scripts de Unity y vaya a la Visual Studio que se abre para ver y editar.
9. Depurar -> Adjuntar depurador de Unity.

    ![Adjuntar depurador de Unity](images/il2cpp-debugging-attach.png)

10. Seleccione el dispositivo en la lista y haga clic en "Aceptar" para adjuntarlo.

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a>Vea también 

* [Depuración de C#](/visualstudio/get-started/csharp/tutorial-debugger)
