---
title: Sistema elástico
description: Documentación relacionada con la simulación de elásticos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, ElasticsSystem,
ms.openlocfilehash: e34b9ea68bfbdc7b7f285686565a1e049ba58ad8677b16e915a2db8272ec1cbe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217907"
---
# <a name="elastic-system"></a>Sistema elástico

![Sistema elástico](../images/elastics/Elastics_Main1.gif)

MRTK incluye un sistema de simulación elástica que incluye una amplia variedad de subclases extensibles y flexibles, que ofrece enlaces para cuaternión de cuaternión de 4 dimensiones, sonidos de volumen tridimensionales y sistemas de spring lineales simples.

Actualmente, los siguientes componentes de MRTK que [admiten el administrador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) pueden aprovechar la funcionalidad de los elásticos:

- [Control de límites](../ux-building-blocks/bounds-control.md)
- [Manipulador de objetos](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Administrador de elastics

![Elastic System2](../images/elastics/Elastics_Main.gif)

Los procesos del administrador de elásticos pasan transformaciones y las alimentan en el sistema elástico.

La habilitación de elásticos para componentes personalizados se puede lograr mediante dos pasos:

1. Al llamar al método Initialize al iniciar la manipulación, se actualiza el sistema con la transformación de host actual.
1. Consultar ApplyHostTransform siempre que se deba realizar un cálculo elástico en la transformación de destino actualizada.

Tenga en cuenta que los elásticos seguirán simulando una vez que finalice la manipulación (a través del bucle de actualización del administrador de elásticos). Para bloquear el comportamiento, la actualización automática de [los elásticos EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) se puede establecer en false.

De forma predeterminada, el componente de administrador de elásticos, cuando se agrega a un objeto de juego, no tendrá elásticos habilitados para ningún tipo de transformación.
El campo `Manipulation types using elastic feedback` debe habilitarse para tipos de transformación específicos para crear configuraciones elásticas y extensiones para el tipo seleccionado.

### <a name="elastics-configurations"></a>Configuraciones elásticas

De forma similar a las configuraciones de control de [límites,](../ux-building-blocks/bounds-control.md#configuration-objects)Elastic Manager incluye un conjunto de objetos de configuración que se pueden almacenar como objetos que pueden incluirse en scripts y compartirse entre instancias o elementos prefab diferentes. Las configuraciones se pueden compartir y vincular como archivos de recursos individuales que pueden incluirse en scripts o recursos anidados que se pueden incluir en scripts dentro de objetos prefab. También se pueden definir otras configuraciones directamente en la instancia sin vincular a un recurso que puede incluir scripts externo o anidado.

El inspector del administrador elástico indicará si una configuración se comparte o se inline como parte de la instancia actual mostrando un mensaje en el inspector de propiedades. Además, las instancias compartidas no se podrán editar directamente en la propia ventana de propiedades del administrador de elásticos, sino que el recurso al que está vinculando debe modificarse directamente para evitar cambios accidentales en las configuraciones compartidas.

Elastics Manager ofrece opciones de objetos de configuración para los siguientes tipos de transformación, cada uno de ellos representado por un [objeto de configuración elástica](#elastic-configuration-object):

- Traducción elástica
- Rotación elástica
- Escalado elástico

#### <a name="elastic-configuration-object"></a>Objeto de configuración elástica

Una configuración de elásticos define las propiedades de un sistema diferencial de diferenciales de diferenciales armónicos.
Las siguientes propiedades se pueden ajustar, pero ya vienen con un conjunto de valores predeterminados en MRTK:

- **Masa:** masa del elemento de oscilador simulado.
- **HandK:** constante de spring de mano.
- **EndK:** constante de extremo de spring.
- **SnapK:** constante de spring de punto de instantánea.
- **Arrastre**: factor de arrastre/desastrador, proporcional a la velocidad.

### <a name="elastics-extents"></a>Extensiones elásticas

La configuración de extensiones elásticas varía en función del tipo de manipulación. La traducción y la escala se representan [mediante extensiones elásticas de volumen](#volume-elastic-extent) y la rotación se representa mediante una extensión elástica de [cuaternión](#quaternion-elastic-extent).

#### <a name="volume-elastic-extent"></a>Extensión elástica del volumen

Las extensiones de volumen definen un espacio tridimensional en el que el oscilador del armónico desasistido es libre de moverse.

![Límites elásticos de stretch de volumen](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds:** representa los límites inferiores del espacio elástico.
- **UseBounds:** indica si el sistema debe respetar los límites de extensión. Si es true, cuando la iteración actual de la posición de destino está fuera de los límites de extensión, se aplicará la fuerza final.
- **Puntos de instantánea:** puntos dentro del espacio al que se ajustará el sistema.
- **RepeatSnapPoints:** repite los puntos de ajuste al infinito. Los puntos de ajuste existentes servirán como módulo donde los puntos de ajuste reales se asignan a los múltiples enteros más cercanos de cada punto de instantánea.
- **SnapRadius:** distancia a la que los puntos de ajuste comienzan a forzar el resorte.

![Elastic Volume Snap Grid](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Extensión elástica de cuaternión

Las extensiones de cuaternión definen un espacio de rotación dimensional de cuatro dimensiones en el que el oscilador del armónico desasistido es libre de girar.

![Ejemplo de rotación elástica](../images/elastics/Elastics_Rotation.gif)

- **SnapPoints:** ángulos euler a los que se ajustará el sistema.
- **RepeatSnapPoints:** repite los puntos de ajuste. Los puntos de ajuste existentes servirán como módulo donde los puntos de ajuste reales se asignan a los múltiples enteros más cercanos de cada punto de instantánea.
- **SnapRadius:** ángulo de arco en el que los puntos de ajuste comienzan a forzar el resorte en grados euler.

## <a name="elastics-example-scene"></a>Escena de ejemplo de elastics

Puede encontrar ejemplos de configuraciones elásticas en la `ElasticSystemExample` escena.

![Escena de ejemplo de elastics](../images/elastics/Elastics_Example_Scene.png)
