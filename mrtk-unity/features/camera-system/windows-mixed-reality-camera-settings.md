---
title: Windows Mixed Reality configuración de la cámara
description: Documentación para usar la Windows Mixed Reality de la cámara en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, cámara,
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121643"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality de configuración de la cámara

El Windows Mixed Reality configuración de la cámara determina el tipo de dispositivo en el que se ejecuta la aplicación y aplica las opciones de configuración adecuadas en función de la pantalla (transparente u opaca).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Habilitación del proveedor Windows Mixed Reality configuración de la cámara

En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit. Los pasos necesarios para otros registradores de servicios pueden ser diferentes.

1. Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Vaya al panel Inspector a la sección sistema de cámara y expanda la **sección Proveedores de configuración de cámara.**

    ![Expandir proveedores de configuración](../images/camera-system/ExpandProviders.png)

3. Haga clic **en Agregar proveedor de configuración de cámara** y expanda la entrada Nueva configuración de cámara **recién** agregada.

    ![Expansión del nuevo proveedor de configuración](../images/camera-system/ExpandNewProvider.png)

4. Seleccione el proveedor Windows Mixed Reality configuración de la cámara

    ![Selección del Windows Mixed Reality configuración de configuración](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Al usar los perfiles predeterminados de Microsoft Mixed Reality Toolkit, el proveedor Windows Mixed Reality configuración de la cámara ya estará habilitado y configurado.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Configuración del proveedor de Windows Mixed Reality de configuración de la cámara

La Windows Mixed Reality configuración de la cámara también admite un perfil. Este perfil proporciona las siguientes opciones:

![Windows Mixed Reality configuración de la cámara](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Representación de la captura de realidad mixta desde la cámara de fotos y vídeos

Con esta configuración en HoloLens 2, puede habilitar la alineación de hologramas en las capturas de realidad mixta. Si está habilitada, la plataforma proporcionará una holographicCamera adicional a la aplicación cuando se toma una foto o un vídeo de captura de realidad mixta. HolographicCamera proporciona matrices de vistas correspondientes a la ubicación de la cámara de fotos y vídeos, y proporciona matrices de proyección mediante el campo de vista de la cámara de fotos y vídeos. Esto garantizará que los hologramas, como las mallas de mano, permanezcan visiblemente alineados en la salida del vídeo.

### <a name="hololens-2-reprojection-method"></a>HoloLens 2 método de reproducción

Establece el método inicial para la HoloLens 2 proyecto. La recomendación predeterminada es usar la reproducción de profundidad, ya que todas las partes de la escena se estabilizarán de forma independiente en función de su distancia con respecto al usuario. Si los hologramas siguen apareciendo inestables, intente asegurarse de que todos los objetos han enviado correctamente su profundidad al búfer de profundidad. A veces se trata de una configuración de sombreador. Si la profundidad parece enviarse correctamente y la inestabilidad sigue estando presente, pruebe la estabilización autoplanar, que usa el búfer de profundidad para calcular un plano de estabilización. Si una aplicación no puede enviar datos de profundidad suficientes para que cualquiera de esas opciones se pueda usar, se proporciona una reproducción plana como reserva. Este método se basará en los datos del punto de enfoque proporcionados por una aplicación a través [de SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).

Para actualizar el método de reproyecto en tiempo de ejecución, acceda al `WindowsMixedRealityReprojectionUpdater` siguiente:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Esto solo debe actualizarse una vez y el valor se reutiliza para todos los fotogramas posteriores. Si el método se actualizará con frecuencia, se recomienda almacenar en caché el resultado de en `EnsureComponent` lugar de llamarlo a menudo.

## <a name="see-also"></a>Consulte también

- [Información general del sistema de cámara](camera-system-overview.md)
- [Crear un proveedor de configuración de cámara](create-settings-provider.md)
- [Representación Captura de realidad mixta desde la cámara PV](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Reproducción holográfica](/windows/mixed-reality/hologram-stability#reprojection)