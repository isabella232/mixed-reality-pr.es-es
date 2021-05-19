---
title: Formato de archivo de animación de entrada
description: Documentación sobre la especificación de formato de archivo binario de animación de entrada en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: ba232818c0a49d803ca6fae0b5adbc64e6deefa8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145124"
---
# <a name="input-animation-binary-file-format-specification"></a>Especificación de formato de archivo binario de animación de entrada

## <a name="overall-structure"></a>Estructura general

El archivo binario de animación de entrada comienza con un número mágico entero de 64 bits. El valor de este número en notación hexadecimal es `0x6a8faf6e0f9e42c6` y se puede usar para identificar archivos de animación de entrada válidos.

Los ocho bytes siguientes son dos valores Int32 que declaran el número de versión principal y secundaria del archivo.

El resto del archivo lo toman los datos de animación, que pueden cambiar entre los números de versión.

| Sección | Tipo |
|---------|------|
| Número mágico | Int64 |
| Número de versión principal | Int32 |
| Número de versión secundaria | Int32 |
| Datos de animación | _consulte la sección de versión._ |

## <a name="version-11"></a>Versión 1.1

Los datos de animación de entrada constan de tres valores booleanos que indican si la animación contiene datos de cámara, mano y mirada con los ojos, seguidos de una secuencia de curvas de animación. Las curvas presentes dependen de los valores de estos booleanos. Cada curva puede tener un número diferente de fotogramas clave.

| Sección | Tipo | Notas |
|---------|------|------|
| Tiene posición de cámara | Boolean | |
| Tiene datos de mano | Boolean | |
| Tiene la mirada con los ojos| Boolean | |
| Cámara | [Curvas de posición](#pose-curves) | Solo si tiene la posición de la cámara es true |
| Izquierda con seguimiento a mano | [Curva booleana](#boolean-curve) | Solo si tiene datos de mano es true |
| Derecha con seguimiento a mano | [Curva booleana](#boolean-curve) | Solo si tiene datos de mano es true |
| Acercamiento de la mano a la izquierda | [Curva booleana](#boolean-curve) | Solo si tiene datos de mano es true |
| Apreción de la mano a la derecha | [Curva booleana](#boolean-curve) | Solo si tiene datos de mano es true |
| Uniones de mano izquierda | [Curvas de posición conjuntas](#joint-pose-curves) | Solo si tiene datos de mano es true |
| Derecha de las uniones de mano | [Curvas de posición conjuntas](#joint-pose-curves) | Solo si tiene datos de mano es true |
| Mirada con los ojos | [Curvas de rayo](#ray-curves)] | Solo si la mirada con los ojos es verdadera |

## <a name="version-10"></a>Versión 1.0

Los datos de animación de entrada constan de una secuencia de curvas de animación. El número y el significado de las curvas de animación son fijos, pero cada curva puede tener un número diferente de fotogramas clave.

| Sección | Tipo |
|---------|------|
| Cámara | [Curvas de posición](#pose-curves) |
| Izquierda con seguimiento a mano | [Curva booleana](#boolean-curve) |
| Derecha con seguimiento a mano | [Curva booleana](#boolean-curve) |
| Acercamiento de la mano a la izquierda | [Curva booleana](#boolean-curve) |
| Acercamiento de la mano a la derecha | [Curva booleana](#boolean-curve) |
| Uniones de mano a la izquierda | [Curvas de posición conjuntas](#joint-pose-curves) |
| Derecha de las uniones de mano | [Curvas de posición conjuntas](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>Curvas de posición conjuntas

Para cada mano se almacena una secuencia de curvas de animación conjuntas. El número de uniones es fijo y se almacena un conjunto de curvas de posición para cada unión.

| Sección | Tipo |
|---------|------|
| Ninguno | [Curvas de posición](#pose-curves) |
| Muñeca | [Curvas de posición](#pose-curves) |
| Palm | [Curvas de posición](#pose-curves) |
| ThumbMetacarpalJoint | [Curvas de posición](#pose-curves) |
| ThumbProximalJoint | [Curvas de posición](#pose-curves) |
| ThumbDistalJoint | [Curvas de posición](#pose-curves) |
| Información general | [Curvas de posición](#pose-curves) |
| IndexMetacarpal | [Curvas de posición](#pose-curves) |
| IndexKnuckle | [Curvas de posición](#pose-curves) |
| IndexMiddleJoint | [Curvas de posición](#pose-curves) |
| IndexDistalJoint | [Curvas de posición](#pose-curves) |
| IndexTip | [Curvas de posición](#pose-curves) |
| MiddleMetacarpal | [Curvas de posición](#pose-curves) |
| MiddleKnuckle | [Curvas de posición](#pose-curves) |
| MiddleMiddleJoint | [Curvas de posición](#pose-curves) |
| MiddleDistalJoint | [Curvas de posición](#pose-curves) |
| Información intermedia | [Curvas de posición](#pose-curves) |
| RingMetacarpal | [Curvas de posición](#pose-curves) |
| RingKnuckle | [Curvas de posición](#pose-curves) |
| RingMiddleJoint | [Curvas de posición](#pose-curves) |
| RingDistalJoint | [Curvas de posición](#pose-curves) |
| RingTip | [Curvas de posición](#pose-curves) |
| PinkyMetacarpal | [Curvas de posición](#pose-curves) |
| PinkyKnuckle | [Curvas de posición](#pose-curves) |
| PinkyMiddleJoint | [Curvas de posición](#pose-curves) |
| PinkyDistalJoint | [Curvas de posición](#pose-curves) |
| Información sobre rosas | [Curvas de posición](#pose-curves) |

### <a name="pose-curves"></a>Curvas de posición

Las curvas de posición son una secuencia de 3 curvas de animación para el vector de posición, seguidas de 4 curvas de animación para el cuaternión de rotación.

| Sección | Tipo |
|---------|------|
| Posición X | [Curva float](#float-curve) |
| Posición Y | [Curva float](#float-curve) |
| Posición Z | [Curva float](#float-curve) |
| Rotación X | [Curva float](#float-curve) |
| Rotación Y | [Curva flotante](#float-curve) |
| Rotación Z | [Curva float](#float-curve) |
| Rotación W | [Curva flotante](#float-curve) |

### <a name="ray-curves"></a>Curvas de rayo

Las curvas de rayo son una secuencia de 3 curvas de animación para el vector de origen, seguidas de 3 curvas de animación para el vector de dirección.

| Sección | Tipo |
|---------|------|
| Origen X | [Curva flotante](#float-curve) |
| Origen Y | [Curva flotante](#float-curve) |
| Origen Z | [Curva flotante](#float-curve) |
| Dirección X | [Curva flotante](#float-curve) |
| Dirección Y | [Curva flotante](#float-curve) |
| Dirección Z | [Curva float](#float-curve) |

### <a name="float-curve"></a>Curva float

Las curvas de punto flotante son curvas bézier totalmente inquentes con un número variable de fotogramas clave. Cada fotograma clave almacena un tiempo y un valor de curva, así como tangentes y pesos en el lado izquierdo y derecho de cada fotograma clave.

| Sección | Tipo |
|---------|------|
| Modo de encapsulado previo | Int32, [modo de encapsulado](#wrap-mode) |
| Modo posterior al encapsulado | Int32, [modo de encapsulado](#wrap-mode) |
| Número de fotogramas clave | Int32 |
| Fotogramas clave | [Fotograma clave flotante](#float-keyframe) |

### <a name="float-keyframe"></a>Fotograma clave float

Un fotograma clave flotante almacena valores tangentes y de peso junto con el tiempo y el valor básicos.

| Sección | Tipo |
|---------|------|
| Hora | Float32 |
| Valor | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32, [modo ponderado](#weighted-mode) |

### <a name="boolean-curve"></a>Curva booleana

Las curvas booleanas son secuencias simples de valores de encendido y apagado. En cada fotograma clave, el valor de la curva se invierte inmediatamente.

| Sección | Tipo |
|---------|------|
| Modo de encapsulado previo | Int32, [modo de encapsulado](#wrap-mode) |
| Modo posterior al encapsulado | Int32, [modo de encapsulado](#wrap-mode) |
| Número de fotogramas clave | Int32 |
| Fotogramas clave | [Fotograma clave booleano](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>Fotograma clave booleano

Un fotograma clave booleano solo almacena una hora y un valor.

| Sección | Tipo |
|---------|------|
| Hora | Float32 |
| Valor | Float32 |

### <a name="wrap-mode"></a>Modo de encapsulado

La semántica de los modos Pre y Post-Wrap sigue la definición [de WrapMode de Unity.](https://docs.unity3d.com/ScriptReference/WrapMode.html) Son una combinación de los bits siguientes:

| Valor | Significado |
|-------|---------|
| 0 | Valor predeterminado: lee el modo de repetición predeterminado configurado más arriba. |
| 1 | Una vez: cuando el tiempo llegue al final del clip de animación, el clip dejará de reproducirse automáticamente y la hora se restablecerá al principio del clip. |
| 2 | Bucle: cuando el tiempo llega al final del clip de animación, la hora continuará al principio. |
| 4 | PingPong: cuando el tiempo llega al final del clip de animación, el tiempo vuelve a hacer ping entre el principio y el final. |
| 8 | ClampForever: reproduce la animación. Cuando llegue al final, seguirá reproduciendo el último fotograma y nunca dejará de reproducirse. |

### <a name="weighted-mode"></a>Modo ponderado

La semántica del modo ponderado sigue la [definición weightedMode de Unity.](https://docs.unity3d.com/ScriptReference/WeightedMode.html)

| Valor | Significado |
|-------|---------|
| 0 | Ninguno: excluya inWeight o outWeight al calcular segmentos de curva. |
| 1 | En: incluya inWeight al calcular el segmento de curva anterior. |
| 2 | Out: incluya outWeight al calcular el siguiente segmento de curva. |
| 3 | Ambos: incluya inWeight y outWeight al calcular segmentos de curva. |
