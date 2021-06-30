---
title: Configuración de la cámara ar de Unity
description: Documentación para usar la cámara ar en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, cámara ar,
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121203"
---
# <a name="unity-ar-camera-settings-provider"></a>Proveedor de configuración de cámara ar de Unity

El proveedor de configuración de la cámara AR de Unity es un componente experimental de MRTK que permite que las aplicaciones de realidad mixta se ejecuten en dispositivos iOS y Android.

## <a name="unity-ar-camera-settings-provider-options"></a>Opciones del proveedor de configuración de la cámara ar de Unity

![Configuración de la cámara ar de Unity](../images/camera-system/UnityArSettingsConfiguration.png)

Para obtener una guía sobre cómo agregar el proveedor a la escena: [Configuración de MRTK para iOS y Android](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>Configuración de seguimiento

El proveedor de configuración de la cámara ar de Unity permite opciones de configuración para cómo se realiza el seguimiento. Esta configuración es específica de la implementación del proveedor de configuración de cámara ar de Unity.

**Pos Source**

El origen de la posición define los tipos disponibles de poses de seguimiento de realidad aumentada. En general, estos valores se asignan a un componente del dispositivo en el que se ejecuta la aplicación.

Las opciones disponibles se describen en la tabla siguiente.

| Opción | Descripción |
| --- | --- |
| Center | El ojo central de un dispositivo montado en la cabeza. |
| Cámara de color | Cámara de color de un dispositivo móvil. |
| Head | El ojo de la cabeza de un dispositivo montado en la cabeza, a menudo ligeramente por encima del ojo central. |
| Ojo izquierdo | El ojo izquierdo de un dispositivo montado en la cabeza. |
| Posición izquierda | Posición del controlador izquierdo. |
| Ojo derecho | El ojo derecho de un dispositivo montado en la cabeza. |
| Posición derecha | Posición del controlador derecho. |

El valor predeterminado para el origen de la posición es **Color Camera**, para habilitar una pantalla transparente en dispositivos móviles, como un teléfono o una tableta.

**Tipo de seguimiento**

El tipo de seguimiento define las partes de la posición que se usarán para el seguimiento.

Las opciones disponibles se describen en la tabla siguiente.

| Opción | Descripción |
| --- | --- |
| Posición | Posición del dispositivo. |
| Rotación | Rotación del dispositivo. |
| Rotación y posición | Posición y rotación del dispositivo. |

El valor predeterminado para el tipo de seguimiento **es Rotación y posición** para habilitar la experiencia de seguimiento más completa.

**Tipo de actualización**

El tipo de actualización define en qué puntos, durante el procesamiento de fotogramas, se muestrearán los datos de posición.

Las opciones disponibles se describen en la tabla siguiente.

| Opción | Descripción |
| --- | --- |
| Antes de representar | Justo antes de la representación. |
| Actualizar | Durante la fase de actualización del marco. |
| Actualizar y antes de representar | Durante la fase de actualización y justo antes de la representación. |

El valor predeterminado para el tipo de seguimiento **es Update y Before Render** para habilitar la latencia de seguimiento más baja.

## <a name="see-also"></a>Consulte también

- [Información general del sistema de cámara](camera-system-overview.md)
- [Creación de un proveedor de configuración de cámara](create-settings-provider.md)
