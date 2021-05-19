---
title: Sistema elástico
description: documentación relacionada con la simulación de elásticos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, ElasticsSystem,
ms.openlocfilehash: 01a4c4a337593252e0955c03e883e35e1329fc45
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145179"
---
# <a name="elastic-system-experimental"></a>Sistema elástico (experimental)

![Sistema elástico](../images/elastics/Elastics_Main1.gif)

MRTK incluye un sistema de simulación elástica que incluye una amplia variedad de subclases extensibles y flexibles, que ofrecen enlaces para sistemas de cuaternión de cuaternión 4 dimensionales, sonidos de volumen tridimensionales y sistemas de spring lineales simples.

Actualmente, los siguientes componentes de MRTK que admiten [el administrador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) pueden aprovechar la funcionalidad de los elásticos:

- [Control Bounds](../ux-building-blocks/bounds-control.md)
- [Manipulador de objetos](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Administrador de elastics

![Elastic System2](../images/elastics/Elastics_Main.gif)

El administrador de elásticos procesa las transformaciones pasadas y las alimenta en el sistema elástico.

La habilitación de los elásticos para los componentes personalizados se puede lograr mediante dos pasos:

1. Llamar al método Initialize al iniciar la manipulación, actualizando el sistema con la transformación de host actual.
1. Consulta de ApplyHostTransform cada vez que se debe realizar un cálculo elástico en la transformación de destino actualizada.

Tenga en cuenta que los elásticos seguirán simulando una vez que finalice la manipulación (a través del bucle de actualización del administrador de elásticos). Para bloquear el comportamiento, la actualización automática de [elastics EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) se puede establecer en false.

De forma predeterminada, el componente de administrador de elásticos, cuando se agrega a un objeto de juego, no tendrá elásticos habilitados para ningún tipo de transformación.
El campo `Manipulation types using elastic feedback` debe habilitarse para tipos de transformación específicos para crear configuraciones elásticas y extensiones para el tipo seleccionado.

### <a name="elastics-configurations"></a>Configuraciones elásticas

De forma similar a las configuraciones de control de [límites,](../ux-building-blocks/bounds-control.md#configuration-objects)Elastic Manager incluye un conjunto de objetos de configuración que se pueden almacenar como objetos que pueden incluirse en scripts y compartirse entre instancias diferentes o instancias previas. Las configuraciones se pueden compartir y vincular como archivos de recursos individuales que pueden incluirse en scripts o recursos que se pueden incluir en scripts anidados dentro de objetos prefab. También se pueden definir otras configuraciones directamente en la instancia sin vincular a un recurso que permite scripts externo o anidado.

El inspector del administrador elástico indicará si una configuración se comparte o se inline como parte de la instancia actual mostrando un mensaje en el inspector de propiedades. Además, las instancias compartidas no se podrán editar directamente en la propia ventana de propiedades del administrador de elásticos, sino que el recurso al que está vinculando debe modificarse directamente para evitar cambios accidentales en las configuraciones compartidas.

Elastics Manager ofrece opciones de objetos de configuración para los siguientes tipos de transformación, cada uno de ellos representado por un [objeto de configuración elástica](#elastic-configuration-object):

- Traducción elástica
- Rotación elástica
- Escalado elástico

#### <a name="elastic-configuration-object"></a>Objeto de configuración elástica

Una configuración de elásticos define las propiedades de un sistema diferencial de oscilación armónica desasistido.
Las siguientes propiedades se pueden ajustar, pero ya vienen con un conjunto de valores predeterminados en MRTK:

- **Masa:** masa del elemento de oscilador simulado.
- **HandK:** constante de spring de mano.
- **EndK:** end cap spring constant.
- **SnapK:** constante de spring de punto de instantánea.
- **Arrastre**: factor de arrastre/desastrador, proporcional a la velocidad.

### <a name="elastics-extents"></a>Extensiones elásticas

La configuración de extensiones elásticas varía en función del tipo de manipulación. La traducción y la escala se representan [mediante extensiones elásticas de volumen](#volume-elastic-extent) y la rotación se representa mediante una extensión elástica de [cuaternión](#quaternion-elastic-extent).

#### <a name="volume-elastic-extent"></a>Extensión elástica del volumen

Las extensiones de volumen definen un espacio tridimensional en el que el oscilador del armónico desasistido es libre de moverse.

![Límites elásticos de stretch de volumen](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds:** representa los límites inferiores del espacio elástico.
- **UseBounds:** indica si el sistema debe respetar los límites de extensión. Si es true, cuando la iteración actual de la posición de destino está fuera de los límites de extensión, se aplicará la fuerza final.
- **Puntos de instantánea:** apunta dentro del espacio al que se ajustará el sistema.
- **RepeatSnapPoints:** repite los puntos de ajuste al infinito. Los puntos de ajuste existentes servirán como módulo donde los puntos de ajuste reales se asignan a los múltiples enteros más cercanos de cada punto de instantánea.
- **SnapRadius:** distancia a la que los puntos de instantánea comienzan a forzar el spring.

![Elastic Volume Snap Grid](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Extensión elástica de cuaternión

Las extensiones de cuaternión definen un espacio de rotación de cuatro dimensiones en el que el oscilador tortico desasistido es libre de girar.

![Ejemplo de rotación elástica](../images/elastics/Elastics_Rotation.gif)

- **Puntos de instantánea:** ángulos euler a los que se ajustará el sistema.
- **RepeatSnapPoints:** repite los puntos de ajuste. Los puntos de ajuste existentes servirán como módulo donde los puntos de ajuste reales se asignan a los múltiples enteros más cercanos de cada punto de instantánea.
- **SnapRadius:** ángulo de arco en el que los puntos de ajuste comienzan a forzar el spring en grados euler.

## <a name="elastics-example-scene"></a>Escena de ejemplo de elastics

Puede encontrar ejemplos de configuraciones elásticas en la `ElasticSystemExample` escena.

![Escena de ejemplo de elastics](../images/elastics/Elastics_Example_Scene.png)
