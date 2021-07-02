---
title: El plazo de migración
description: Documentación sobre cómo migrar a una actualización en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 9d960d01e738736edd452a124db5c306b5d752ce
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176129"
---
# <a name="migration-window"></a>El plazo de migración

A medida que MRTK se somete a cambios, algunos componentes podrían desusar y se introducirán reemplazos.
La ventana de migración es una herramienta que ayuda a los usuarios a migrar automáticamente un subconjunto de esos componentes en desuso a los nuevos reemplazos.

![El plazo de migración](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>Uso

Para abrir la ventana, seleccione **Mixed Reality**  >  **Toolkit**  >  **migración de**  >  **utilidades.** Una vez abierta la ventana de migración, las pestañas de navegación del modo de selección se pueden habilitar eligiendo la implementación específica del componente del controlador de migración.  

![Modos de selección de migración](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>Modo de objeto

Al seleccionar la pestaña objects (Objetos), se habilita el campo de objeto al que el usuario puede arrastrar y colocar cualquier objeto Game de la escena o los objetos prefabs actualmente abiertos de la carpeta del proyecto que se va a migrar.
Al presionar el *botón quitar (-)* que se muestra en el lado derecho del objeto enumerado, se quita el objeto de la lista de selección.

Una vez que todos los objetos  deseados están en la lista, al presionar el botón Migrar se aplicarán los cambios necesarios para la implementación del controlador de migración elegido a todos los componentes de la selección que coincidan con la implementación.

![Migración de selección](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>Modo de escena

Permite al usuario arrastrar y colocar recursos de escena que contienen objetos que se van a migrar.

![Selección de escenas para la migración](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Project modo de configuración

Al presionar *el botón* Migrar, se actualizará el componente de destino de la implementación del controlador de migración para todos los objetos prefabs y escenas del proyecto.

![Migración de un proyecto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>Consulte también

- [Actualización desde versiones anteriores](../../updates-deployment/updating.md)
- [Versiones Mixed Reality Toolkit Microsoft](../../release-notes/mrtk-26-release-notes.md)
- [Mapa de ruta de MRTK](../../roadmap.md)
