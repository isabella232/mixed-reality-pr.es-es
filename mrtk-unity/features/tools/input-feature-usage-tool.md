---
title: Herramienta de uso de las características de entrada
description: Herramienta InputFeatureUsage de documentación en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 9d5e80ee5f31086b12ec2b82ab2368361fb738e03ea7fe5cf02ba0b4bd22c0b8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189444"
---
# <a name="input-feature-usage-tool"></a>Herramienta de uso de las características de entrada

La herramienta InputFeatureUsage es una herramienta en tiempo de ejecución (en el dispositivo o en el editor) que permite a los desarrolladores determinar rápidamente las entradas de Unity disponiblesFeatureUsages para un origen de entrada detectado (por ejemplo: controlador de movimiento o mano articulada).

> [!NOTE]
> Esta escena solo funciona en Unity 2019.3 o posterior.

Esta herramienta es muy útil al desarrollar compatibilidad con un nuevo controlador de hardware. También puede ayudar a confirmar un problema sospechoso de asignación de controles en la clase de soporte técnico para un controlador existente.

![Herramienta InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Uso de la herramienta InputFeatureUsage

Para empezar a trabajar con la herramienta InputFeatureUsage, vaya a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** y abra la **escena InputFeatureUsageTool.** Una vez cargada la escena, el proyecto se puede ejecutar en el editor, mediante el modo de reproducción, o bien se puede crear y ejecutar en un dispositivo.

Para examinar las asignaciones de Unity para un controlador:

- Conectar el controlador
- Presione cada botón y mueva cada eje.
- Tenga en cuenta los usos de características en la pantalla
- Actualización de las asignaciones de control en el proveedor de datos del sistema de entrada para el controlador

> [!NOTE]
> La herramienta InputFeatureUsage no hace uso de los componentes Mixed Reality Toolkit Microsoft. Se comunica directamente con Unity para determinar y mostrar los usos de características.

### <a name="panels"></a>Paneles

Los paneles muestran el estado actual de todos los inputFeatureUsages notificados en todos los orígenes de entrada de Unity detectados.

En el panel más pequeño de la parte superior se enumeran los nombres de todos los orígenes detectados.

## <a name="see-also"></a>Consulte también

- [Creación de un proveedor de datos del sistema de entrada](../input/create-data-provider.md)
- [Herramienta de asignación de controladores](controller-mapping-tool.md)
