---
title: Uso del administrador de paquetes de Unity
description: Uso de MRTK en Unity Administrador de paquetes
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, paquetes MRTK,
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177326"
---
# <a name="using-the-unity-package-manager"></a>Uso del administrador de paquetes de Unity

A partir de la versión 2.5.0, con la herramienta de características de [Mixed Reality,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)Microsoft Mixed Reality Toolkit se integra con Unity Administrador de paquetes (UPM) cuando se usa Unity 2019.4 y versiones más recientes.

## <a name="using-the-mixed-reality-feature-tool"></a>Uso de la herramienta de características de Mixed Reality

Como se describe [en Le damos la bienvenida a Mixed Reality Feature Tool,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) puede descargar la herramienta mediante [este vínculo](https://aka.ms/MRFeatureTool).

> [!IMPORTANT]
> Si el manifiesto del proyecto tiene una entrada en la sección , se `Microsoft Mixed Reality` `scopedRegistries` recomienda quitarlo.
>
> Para quitar un registro con ámbito configurado, consulte `Edit`  >  `Project Settings`  >  `Package Manager` a .
>
> ![Eliminación del registro con ámbito](../features/images/packaging/RemoveScopedRegistry.png)

Los paquetes MRTK aparecen debajo `Mixed Reality Toolkit` del encabezado al detectar características.

![Detectar características](../features/images/packaging/DiscoverFeatures.png)

Al seleccionar características, no es necesario preocuparse por las dependencias necesarias; la herramienta las descargará e integrará automáticamente en el proyecto.

![Dependencias requeridas](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Administración Mixed Reality características con unity Administrador de paquetes

Una vez Mixed Reality Toolkit paquete de paquete se ha agregado al manifiesto del paquete, se puede administrar mediante la interfaz de usuario Administrador de paquetes Unity.

![Paquete UPM de MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Si se Mixed Reality Toolkit un paquete de Administrador de paquetes con unity, tendrá que volver a agregarlo mediante los pasos [descritos anteriormente.](#using-the-mixed-reality-feature-tool)

### <a name="using-mixed-reality-toolkit-examples"></a>Uso de Mixed Reality Toolkit ejemplos

A diferencia de cuando se usan archivos de paquete de recursos (.unitypackage), y no importan automáticamente los recursos y las escenas `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` de ejemplo.

Para usar uno o varios de los ejemplos, siga estos pasos:

1. En el Editor de Unity, vaya a `Window` > `Package Manager`
1. En la lista de paquetes, seleccione `Mixed Reality Toolkit Examples`
1. Busque las muestras deseadas en la `Samples` lista.
1. Haga clic en `Import into Project`

![Importación de ejemplos](../features/images/packaging/MRTK_ExamplesUpm.png)

Cuando se actualiza un paquete de ejemplo, Unity proporciona la opción de actualizar ejemplos importados.

> [!NOTE]
> La actualización de un ejemplo importado sobrescribirá los cambios realizados en esa muestra y en los recursos asociados.

## <a name="see-also"></a>Consulte también

- [Mixed Reality Toolkit paquetes](../packages/mrtk-packages.md)
