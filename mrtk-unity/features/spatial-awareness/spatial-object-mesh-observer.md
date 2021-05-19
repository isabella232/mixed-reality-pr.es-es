---
title: Observador de la malla de objetos espaciales
description: Documentación sobre el observador de malla espacial en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144453"
---
# <a name="configuring-mesh-observers-for-the-editor"></a>Configuración de observadores de malla para el editor

Una manera cómoda de proporcionar datos de malla de entorno en el editor de Unity es usar la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) clase . El *observador de malla de* objetos espaciales es un proveedor de datos solo de editor para el sistema [de](spatial-awareness-getting-started.md) reconocimiento espacial que permite importar datos del modelo 3D para representar una malla espacial. Un uso común del observador de *la* malla de objetos espaciales es importar los datos examinados a través de un Microsoft HoloLens para probar cómo se adapta una experiencia a distintos entornos desde Unity.

## <a name="getting-started"></a>Introducción

En esta guía se le guiará por la configuración de *un observador de malla de objetos espaciales.* Hay tres pasos clave para habilitar esta característica.

1. Agregar un observador *de malla de objetos espaciales* al perfil del sistema de reconocimiento espacial
1. Establecer el objeto Environment Mesh Data
1. [Configuración del resto de las propiedades del perfil de Mesh Observer](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>Configuración de un perfil *de observador de malla de objetos espaciales*

1. Seleccione el perfil de *configuración Mixed Reality Toolkit* deseado o seleccione el objeto Mixed Reality *Toolkit* en la escena.
1. Abra o expanda la *pestaña Spatial Awareness System (Sistema de reconocimiento espacial).*
1. Haga clic en *el botón "Agregar observador espacial".*

    ![Agregar observador espacial](../images/spatial-awareness/AddObserver.png)

1. Seleccione el *tipo SpatialObjectMeshObserver.*

    ![Selección del observador de la malla de objetos espaciales](../images/spatial-awareness/SelectObjectObserver.png)

1. Seleccione el objeto *de malla espacial deseado.* De forma predeterminada, el observador se configura con un modelo de ejemplo. Este modelo se creó mediante un Microsoft HoloLens, pero es posible [crear un nuevo objeto de malla de examen](#acquiring-environment-scans).
1. [Configuración del resto de las propiedades del perfil de Mesh Observer](configuring-spatial-awareness-mesh-observer.md)

    ![Selección del objeto mesh](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>Notas del perfil de observador de malla de objetos espaciales

Puesto que *el observador de malla* de objetos espaciales carga datos de un modelo 3D, no respeta algunas de las configuraciones estándar del observador de malla que se describen a continuación.

**Intervalo de actualización**

El  *observador de malla de objetos* espaciales envía todas las mallas a una aplicación cuando se carga el modelo. No simula diferencias de tiempo entre actualizaciones. Una aplicación puede volver a recibir los eventos de malla llamando a [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) y [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .

**Is Stationary Observer**

El *observador de malla de objetos* espaciales considera que todos los objetos de malla 3D son insaltentes y no tiene en cuenta el origen.

**Forma y extensiones del observador**

El  *observador de malla de objetos espaciales* envía toda la malla 3D a la aplicación. No se tienen en cuenta la forma y las extensiones del observador.

**Nivel de detalle y triángulos/medidor cúbica**

El observador no intenta encontrar los LOD del modelo 3D al enviar las mallas a la aplicación.

## <a name="acquiring-environment-scans"></a>Adquisición de exámenes de entorno

En esta sección se describe información adicional para crear y recopilar archivos *de objeto* de malla espacial para su uso con el observador de malla de *objetos espaciales*.

### <a name="windows-device-portal"></a>Portal de dispositivos Windows

El [Portal de dispositivos Windows](/windows/mixed-reality/using-the-windows-device-portal) se puede usar para descargar la malla espacial, como un archivo .obj, desde un Microsoft HoloLens dispositivo.

1. Examinar simplemente a pie y ver el entorno deseado con un HoloLens
1. Conéctese a HoloLens mediante el Portal de dispositivos Windows
1. Vaya a la *página Vista 3D.*
1. Haga clic en *el botón Actualizar* en la sección *Asignación* espacial.
1. Haga clic en *el botón* Guardar de la *sección Asignación* espacial para guardar el archivo obj en el equipo.

> [!NOTE]
> **Archivos .room de HoloToolkit**
>
> Muchos desarrolladores habrán usado previamente HoloToolkit para examinar entornos y crear archivos .room. Ahora Mixed Reality Toolkit admite la importación de estos archivos como GameObjects en Unity y usarlos como objetos *de* malla espacial en el observador.

## <a name="see-also"></a>Consulte también

- [Perfiles](../profiles/profiles.md)
- [guía de configuración del perfil de Mixed Reality Toolkit](../../configuration/mixed-reality-configuration-guide.md)
- [Introducción al reconocimiento espacial](spatial-awareness-getting-started.md)
- [Configuración de observadores de malla en el dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configuración de observadores de malla mediante código](usage-guide.md)
- [Uso del Portal de dispositivos Windows](/windows/mixed-reality/using-the-windows-device-portal)