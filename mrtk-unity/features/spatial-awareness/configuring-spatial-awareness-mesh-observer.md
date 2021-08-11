---
title: Configuración de observadores de la malla para dispositivos
description: Configuración del observador de malla espacial de forma lista para usar en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 00a3b9afe1970239f52b1ead4f87f930c5826ba75522b99a52cf368249c9fd83
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228496"
---
# <a name="configuring-mesh-observers-for-device"></a>Configuración de observadores de la malla para dispositivos

Esta guía le guiará a través de la configuración del observador de malla espacial integrada en MRTK, que admite la plataforma Windows Mixed Reality (es decir, HoloLens). La implementación predeterminada proporcionada por el Mixed Reality Toolkit es [la clase WindowsMixedRealitySpatialMeshObserver.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Muchas de las propiedades de este artículo se aplican a [otras implementaciones de Observer personalizadas.](create-data-provider.md)

## <a name="profile-settings"></a>Configuración del perfil

Los dos elementos siguientes deben definirse primero al configurar un perfil de observador de malla espacial para el [sistema de reconocimiento espacial](spatial-awareness-getting-started.md).

1. Implementación concreta del tipo de observador
1. lista de plataformas admitidas para ejecutar este observador

> [!NOTE]
> Todos los observadores deben extender la [interfaz IMixedRealitySpatialAwarenessObserver.](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)

![Tipos de mesh observer general Configuración platform](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Configuración general

![Configuración general de mesh observer Configuración Genral](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Comportamiento de inicio**

El comportamiento de inicio especifica si el observador comenzará a ejecutarse cuando se cree una instancia por primera vez. Las dos opciones son las siguientes:

* *Inicio automático:* el valor predeterminado por el que el observador iniciará la operación después de la inicialización
* *Inicio manual:* el observador esperará a que se le dirija para iniciarse.

Si usa *Inicio manual*, debe [reanudarlos y suspenderlos en tiempo de ejecución a través del código](usage-guide.md#starting-and-stopping-mesh-observation).

**Intervalo de actualización**

Tiempo, en segundos, entre las solicitudes a la plataforma para actualizar los datos de la malla espacial. Los valores típicos se encuentra en el intervalo de 0,1 y 5,0 segundos.

**Is Stationary Observer**

Indica si el observador debe permanecer o no en estado de insondía o si se va a mover y actualizar con el usuario. Si es true, *la forma del observador* con el volumen definido por las extensiones *de* observación permanecerá en el origen en el inicio. Si es false, el espacio Observer seguirá la cabeza del usuario como origen de la forma.

No se calculará ningún dato de malla para ningún área física fuera del espacio del observador tal como se define en estas propiedades: *Is Stationary Observer*, *Observer Shape** y *Observation Extents*.

**Forma de observador**

La forma de observador define el tipo de volumen que usará el observador de malla al observar mallas. Las opciones admitidas son:

* *Cubo alineado del eje:* forma rectangular que permanece alineada con los ejes del sistema de coordenadas del mundo, como se determina en el inicio de la aplicación.
* *Cubo alineado por el usuario:* forma rectangular que gira para alinearse con el sistema de coordenadas local de los usuarios.
* *Sphere:* volumen esférico con un centro en el origen del espacio mundial. El valor X de la *propiedad Observation Extents* se usará como radio de la esfera.

**Extensiones de observación**

Las extensiones de observación definen la distancia desde el punto de observación que se observarán las mallas.

### <a name="physics-settings"></a>Configuración física

![Mesh Observer Physics Configuración](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Capa física**

Capa física en la que se colocarán los objetos de malla espacial para interactuar con los sistemas Unity Physics y RayCast.

> [!NOTE]
> El Mixed Reality Toolkit reserva la *capa 31* de forma predeterminada para que la usen los observadores de reconocimiento espacial.

**Recalcular normales**

Especifica si el observador de malla volverá a calcular o no las normales de la malla después de la observación. Esta configuración está disponible para garantizar que las aplicaciones reciben mallas que contienen datos normales válidos en plataformas que no las devuelven con mallas.

### <a name="level-of-detail-settings"></a>Configuración de nivel de detalle

![Nivel de detalle del observador de malla Configuración](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Nivel de detalle**

Especifica el nivel de detalle (LOD) de los datos de malla espacial. Los valores definidos actualmente son General, Fine y Custom.

* *General:* tiene un impacto menor en el rendimiento de la aplicación y es una excelente opción para la búsqueda de navegación y plano.

* *Medio:* configuración equilibrada a menudo útil para experiencias que analizan continuamente el entorno en busca de características grandes, plantas y paredes, así como detalles de oclusión.

* *Fine:* por lo general, tiene un mayor impacto en el rendimiento de la aplicación y es una excelente opción para las mallas de oclusión.

* *Personalizado:* requiere que la aplicación especifique la propiedad *Triángulos o* medidores cúbicas y permite que las aplicaciones ajusten la precisión frente al impacto en el rendimiento del observador de malla espacial.

> [!NOTE]
> No se garantiza que todas las plataformas respetan todos los valores de *triángulos* y medidores cúbicos. Se recomienda encarecidamente la experimentación y la generación de perfiles cuando se usa un LOD personalizado.

**Triángulos por medidor cúbica**

Válido cuando se usa *el valor Personalizado* para la propiedad **Nivel** de detalle y especifica la densidad del triángulo para la malla espacial.

### <a name="display-settings"></a>Configuración de pantalla

![Pantalla del observador de malla Configuración](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Opción Mostrar**

Especifica cómo el observador mostrará las mallas espaciales. Los valores admitidos son:

* *Ninguno:* el observador no representará la malla
* *Visible:* los datos de malla estarán visibles mediante *el material visible*
* *Oclusión:* los datos de malla serán elementos de ocultación en la escena mediante el *material de oclusión*

![Selección de la implementación del sistema de reconocimiento espacial](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Los observadores espaciales se [pueden reanudar o suspender en tiempo de ejecución mediante código.](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> Establecer *opción de presentación* en *Ninguno* NO **detiene** la ejecución del observador. Si desea detener todos los observadores, las aplicaciones tendrán que suspender todos los observadores a través de [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Visible Material**

Indica el material que se va a usar al visualizar la malla espacial.

**Material de oclusión**

Indica el material que se va a usar para hacer que la malla espacial occlude hologramas.

## <a name="see-also"></a>Consulte también

* [Sistema de reconocimiento espacial](spatial-awareness-getting-started.md)
* [Configuración del sistema de reconocimiento espacial mediante código](usage-guide.md)
* [Documentación de la API IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [Documentación de la API IMixedRealitySpatialAwarenessMeshObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [Documentación de la API BaseSpatialObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
