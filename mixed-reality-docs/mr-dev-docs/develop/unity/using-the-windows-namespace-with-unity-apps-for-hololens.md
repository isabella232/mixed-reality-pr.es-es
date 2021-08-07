---
title: API de WinRT con Unity para HoloLens
description: Leanr how to make use of WinRT APIs and the Windows namespace in your Unity mixed reality projects for HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, walkthrough, mixed reality headset, windows mixed reality headset, virtual reality headset, Mixed Reality API
ms.openlocfilehash: 158c28d9186269108442226bbfcfc90a3c235a71336fdab9dbf9eadc21a309a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215611"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>API de WinRT con Unity para HoloLens

En esta página se describe cómo usar las API de WinRT en el proyecto de Unity para HoloLens.

## <a name="mixed-reality-apis"></a>Mixed Reality API

Un Mixed Reality específico del SDK de Windows está disponible en una proyección compatible con .NET Standard 2.0, que puede usar en el proyecto sin directivas de preprocesador. La mayoría de las API de la Windows. Percepción y Windows. Ui. Los espacios de nombres Input.Spatial se incluyen y pueden expandirse para incluir API adicionales en el futuro. Las API proyectadas se pueden usar mientras se ejecutan en el editor, lo que permite el uso del [modo de reproducción](/windows/mixed-reality/unity-play-mode). Para usar esta proyección, realice las siguientes modificaciones en el proyecto:

1) Agregue una referencia a [Microsoft.Windows. Paquete de NuGet MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Las referencias de prefijo al `Windows` espacio de nombres con `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Reemplace las conversión de puntero nativo por `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Incluir condicionalmente llamadas API de WinRT

También puede usar las API de WinRT en proyectos de Unity creados para la plataforma universal Windows y Xbox One mediante directivas de preprocesador. Cualquier código que escriba en scripts de Unity que tenga como destino las API de WinRT debe incluirse condicionalmente solo para esas compilaciones. 

Esto se puede realizar mediante dos pasos en Unity:
1) El nivel de compatibilidad de API debe establecerse en **.NET 4.6** **o .NET Standard 2.0 en** la configuración del reproductor
    - **Editar**  >  **Project Configuración**  >  **Player**  >  **Configuración**  >  **Nivel de compatibilidad de API** a **.NET 4.6** **o .NET Standard 2.0**
2) La directiva de **ENABLE_WINMD_SUPPORT** debe ajustarse en torno a cualquier código aprovechado por WinRT

El siguiente fragmento de código es de la página manual de Unity para [Universal Windows Platform: Api winRT en scripts de C#.](https://docs.unity3d.com/Manual/windowsstore-scripts.html) En este ejemplo, se devuelve un identificador de publicidad, pero solo en UWP y Xbox One compilaciones:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Edición de scripts en un proyecto de C# de Unity

Al hacer doble clic en un script en el editor de Unity, se iniciará de forma predeterminada el script en un proyecto de editor. Las API de WinRT parecerán desconocidas porque el proyecto Visual Studio no hace referencia al Windows runtime. La **ENABLE_WINMD_SUPPORT** directiva no está definida y cualquier #if *código* encapsulado se omite hasta que compile el proyecto en una solución de Visual Studio UWP.

## <a name="see-also"></a>Consulte también
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Compatibilidad con el entorno de ejecución de Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)