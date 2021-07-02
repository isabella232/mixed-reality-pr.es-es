---
title: Herramienta de asignación de controladores
description: Documentación sobre la herramienta de asignación de controladores en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176173"
---
# <a name="controller-mapping-tool"></a>Herramienta de asignación de controladores

La herramienta de asignación de controladores es una herramienta en tiempo de ejecución (en el dispositivo o en el editor) que permite a los desarrolladores determinar rápidamente el eje de entrada de Unity y las asignaciones de botones para un controlador de hardware (por ejemplo, controlador de movimiento).

Esta herramienta es muy útil al desarrollar compatibilidad con un nuevo controlador de hardware. También puede ayudar a confirmar un problema sospechoso de asignación de controles en la clase de soporte técnico para un controlador existente.

![Herramienta de asignación de controladores](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Uso de la herramienta de asignación de controladores

Para empezar a trabajar con la herramienta de asignación de controladores, vaya a **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** y abra la **escena ControllerMappingTool.** Una vez cargada la escena, el proyecto se puede ejecutar en el editor, mediante el modo de reproducción, o bien se puede crear y ejecutar en un dispositivo.

Para examinar las asignaciones de Unity para un controlador:

- Conectar el controlador
- Presione cada botón y mueva cada eje.
- Tenga en cuenta las asignaciones en la pantalla
- Actualización de las asignaciones de controles en el proveedor de datos del sistema de entrada para el controlador

> [!NOTE]
> La herramienta de asignación de controladores no hace uso de los componentes Mixed Reality Toolkit Microsoft. Se comunica directamente con Unity para determinar y mostrar las asignaciones de control.

### <a name="all-controls-display"></a>Se muestran todos los controles

El panel de pantalla grande informa del estado de todos los ejes y botones de entrada de Unity definidos (por ejemplo: Eje 10, Botón 3). Este panel proporciona una vista completa del estado del controlador.

![Se muestran todos los controles](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Presentación de controles activos

El panel de pantalla más pequeño y estrecho muestra los botones y ejes de entrada de Unity que están en estado activo (por ejemplo, se presiona un botón). La pantalla de controles activos proporciona una vista de resumen fácil de leer del estado del controlador.

![Presentación de controles activos](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Consulte también

- [Creación de un proveedor de datos del sistema de entrada](../input/create-data-provider.md)
- [Herramienta InputFeatureUsage](input-feature-usage-tool.md)
