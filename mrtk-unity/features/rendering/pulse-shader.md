---
title: Sombreador de pulsos
description: descripción de los sombreadores pulse en MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: add3aaa2a98ca2ddc1f60b0307a3defed3236d9a2c09aa70ea2d12b2d9638eba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228394"
---
# <a name="pulse-shader"></a>Sombreador de pulsos

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Use el sombreador de pulsos para animar un efecto de pulso visual sobre la reconstrucción de la superficie, la malla de mano articulada o cualquier otra malla.

## <a name="shader-and-material"></a>Sombreador y material

Los siguientes materiales usan **SR_Triangles** sombreador. Puede configurar varias opciones, como el color de relleno, el color de línea y el color de pulso.

- **MRTK_Pulse_SpatialMeshBlue.mat** 
- **MRTK_Pulse_SpatialMeshPurple.mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue.mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple.mat** 

## <a name="prerequisites"></a>Requisitos previos

En el ejemplo de malla espacial, asegúrese de que MRTK_Pulse_SpatialMeshBlue.mat o MRTK_Pulse_SpatialMeshPurple.mat se asignan en el objeto MixedRealityToolkit -> Spatial Awareness Profile -> Display Configuración -> Visible Material.

En el ejemplo de malla de mano, asegúrese de que MRTK_Pulse_ArticulatedHandMeshBlue.mat o MRTK_Pulse_ArticulatedHandMeshPurple.mat se asignen en ArticulatedHandMesh.prefab, que a su vez se debe asignar en MRTK Configuración -> Input -> Hand Tracking -> Hand Mesh Prefab.

## <a name="how-it-works"></a>Cómo funciona

El sombreador de malla de mano usa UV para asignar el pulso a lo largo de la malla de mano y para atenuar la bolsa. El sombreador de reconstrucción de superficie usa las posiciones de vértice para asignar el pulso.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Ejemplo de malla espacial: PulseShaderSpatialMeshExample.unity

De forma HoloLens 2 experiencia de shell, puede apuntar y pulsar el aire con el rayo de la mano para generar un efecto de pulsación en la malla espacial. La escena de ejemplo contiene el objeto ExampleSpatialMesh, que es un datos de malla espacial de prueba para el modo de juego de Unity. Este objeto se deshabilitará y ocultará en el dispositivo.

El script **PulseShaderSpatialMeshHandler.cs** genera el efecto de pulso en la malla espacial en la posición del punto de acceso `PulseOnSelect` si es true. La  `Auto Pulse` propiedad también se puede establecer en true en el propio material para una animación repetida.  En la escena de ejemplo, este script se adjunta al prefab PulseShaderSpatialMeshParent.  Se hace referencia a este objeto prefab en la propiedad Prefab Perfil de reconocimiento espacial a través de malla espacial en tiempo de ejecución. Durante el tiempo de ejecución, se crea una instancia del prefab PulseShaderSpatialMeshParent y se agregan instancias a la jerarquía de malla espacial (solo en el dispositivo, este comportamiento no se puede observar en el editor).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Ejemplo de malla de mano: PulseShaderHandMeshExample.unity

En esta escena de ejemplo se muestra la visualización de malla de mano mediante el sombreador de pulsos. Cuando el dispositivo de la HoloLens detecta una mano, la animación por pulsación se desencadenará una vez. Estos comentarios visuales pueden aumentar la confianza de interacción del usuario. 

El script **PulseShaderHandMeshHandler.cs** genera el efecto pulse en el material asignado. De forma predeterminada, se comprueba "Pulse On Hand Detected".
