---
title: Configuración del observador de la malla de reconocimiento espacial
description: Configuración del observador de malla espacial lista para usar en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144963"
---
# <a name="configuring-mesh-observers-for-device"></a>Configuración de observadores de malla para el dispositivo

Esta guía le guiará a través de la configuración del observador de malla espacial integrada en MRTK que admite la plataforma Windows Mixed Reality (es decir, HoloLens). La implementación predeterminada proporcionada por Mixed Reality Toolkit es [la clase WindowsMixedRealitySpatialMeshObserver.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Muchas de las propiedades de este artículo se aplican a [otras implementaciones de Observer personalizadas.](create-data-provider.md)

## <a name="profile-settings"></a>Configuración del perfil

Los dos elementos siguientes deben definirse primero al configurar un perfil de observador de malla espacial para el [sistema de reconocimiento espacial](spatial-awareness-getting-started.md).

1. Implementación concreta del tipo de observador
1. lista de plataformas admitidas para ejecutar este observador

> [!NOTE]
> Todos los observadores deben extender la [interfaz IMixedRealitySpatialAwarenessObserver.](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)

![Tipos de plataforma de configuración general de Mesh Observer](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Configuración general

![Configuración general del observador de malla Configuración general del genral](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Comportamiento de inicio**

El comportamiento de inicio especifica si el observador comenzará a ejecutarse cuando se cree una instancia por primera vez. Las dos opciones son las siguientes:

* *Inicio automático:* el valor predeterminado por el que el observador iniciará la operación después de la inicialización.
* *Inicio manual:* el observador esperará a que se le dirija para iniciarse.

Si usa *Inicio manual*, debe [reanudarlos y suspenderlos en tiempo de ejecución a través del código](usage-guide.md#starting-and-stopping-mesh-observation).

**Intervalo de actualización**

Tiempo, en segundos, entre las solicitudes a la plataforma para actualizar los datos de la malla espacial. Los valores típicos se encuentra en el intervalo de 0,1 y 5,0 segundos.

**Is Stationary Observer**

Indica si el observador debe permanecer o no estacionados o si se va a mover y actualizar con el usuario. Si es true, *la forma observador con* el volumen definido por Las extensiones *de* observación permanecerá en el origen en el inicio. Si es false, el espacio Observador seguirá la cabeza del usuario como origen de la forma.

No se calcularán datos de malla para ningún área física fuera del espacio de observador tal como se define en estas propiedades: *Is Stationary Observer*, *Observer Shape** y *Observation Extents*.

**Forma de observador**

La forma de observador define el tipo de volumen que usará el observador de malla al observar mallas. Las opciones admitidas son:

* *Cubo alineado del eje:* forma rectangular que permanece alineada con los ejes del sistema de coordenadas mundial, como se determina en el inicio de la aplicación.
* *Cubo alineado por el usuario:* forma rectangular que gira para alinearse con el sistema de coordenadas local de los usuarios.
* *Sphere:* volumen esférico con un centro en el origen del espacio mundial. El valor X de la *propiedad Observation Extents* se usará como radio de la esfera.

**Extensiones de observación**

Las extensiones de observación definen la distancia desde el punto de observación que se observarán las mallas.

### <a name="physics-settings"></a>Configuración física

![Configuración física del observador de malla](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Capa de física**

Capa física en la que se colocarán los objetos de malla espacial para interactuar con los sistemas Unity Physics y RayCast.

> [!NOTE]
> El Mixed Reality kit de herramientas reserva *la capa 31* de forma predeterminada para que la usen los observadores de reconocimiento espacial.

**Recalcular normales**

Especifica si el observador de malla volverá a calcular o no las normales de la malla después de la observación. Esta configuración está disponible para garantizar que las aplicaciones reciben mallas que contienen datos normales válidos en plataformas que no las devuelven con mallas.

### <a name="level-of-detail-settings"></a>Configuración de nivel de detalle

![Configuración de nivel de detalle del observador de malla](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Nivel de detalle**

Especifica el nivel de detalle (LOD) de los datos de malla espacial. Los valores definidos actualmente son General, Fine y Custom.

* *General:* tiene un impacto menor en el rendimiento de la aplicación y es una excelente opción para la búsqueda de navegación y plano.

* *Medio:* configuración equilibrada a menudo útil para experiencias que analizan continuamente el entorno en busca de características grandes, plantas y paredes, así como detalles de oclusión.

* *Fine:* por lo general, tiene un mayor impacto en el rendimiento de la aplicación y es una excelente opción para las mallas de oclusión.

* *Personalizado:* requiere que la aplicación especifique la propiedad *Triángulos o* medidores cúbicas y permite a las aplicaciones ajustar la precisión frente al impacto en el rendimiento del observador de malla espacial.

> [!NOTE]
> No se garantiza que todas las plataformas respetan todos los valores de *triángulos* y medidores cúbicos. Se recomienda encarecidamente la experimentación y la generación de perfiles cuando se usa un LOD personalizado.

**Triángulos por medidor cúbica**

Válido cuando se usa *el valor Personalizado* para la propiedad **Nivel** de detalle y especifica la densidad del triángulo para la malla espacial.

### <a name="display-settings"></a>Configuración de pantalla

![Configuración de visualización del observador de malla](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Opción Mostrar**

Especifica cómo el observador mostrará las mallas espaciales. Los valores admitidos son:

* *Ninguno:* el observador no representará la malla
* *Visible:* los datos de malla estarán visibles mediante *el material visible*
* *Oclusión:* los datos de malla serán elementos occluir en la escena mediante el *material de oclusión*

![Selección de la implementación del sistema de reconocimiento espacial](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Los observadores espaciales se [pueden reanudar o suspender en tiempo de ejecución mediante código.](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> Establecer *Opción de visualización* en *Ninguno* NO **detiene** la ejecución del observador. Si desea detener todos los observadores, las aplicaciones tendrán que suspender todos los observadores a través de [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Visible Material**

Indica el material que se va a usar al visualizar la malla espacial.

**Material de oclusión**

Indica el material que se va a usar para hacer que la malla espacial occlude los hologramas.

## <a name="see-also"></a>Consulte también

* [Sistema de reconocimiento espacial](spatial-awareness-getting-started.md)
* [Configuración del sistema de reconocimiento espacial mediante código](usage-guide.md)
* [Documentación de la API IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [Documentación de la API IMixedRealitySpatialAwarenessMeshObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [Documentación de la API BaseSpatialObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
