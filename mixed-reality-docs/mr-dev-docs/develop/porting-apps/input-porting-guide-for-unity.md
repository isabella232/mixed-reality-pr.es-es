---
title: Guía de portabilidad de entrada para Unity
description: Obtenga información sobre cómo controlar la entrada Windows Mixed Reality en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: entrada, unity, porting
ms.openlocfilehash: b2c328152d681a4c8753e29babf0f3ece6bdc0d3f21f9df6dd8de150c3fb47f0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212083"
---
# <a name="input-porting-guide-for-unity"></a>Guía de portabilidad de entrada para Unity

Puede portabilidad de la lógica de entrada Windows Mixed Reality uno de estos dos enfoques. La primera es usar las API input.GetButton/GetAxis generales de Unity que abarcan varias plataformas. La segunda es la Windows XR específica del usuario. Wsa. API de entrada, que ofrecen datos más completos específicamente para controladores de movimiento y HoloLens manos.

## <a name="general-inputgetbuttongetaxis-apis"></a>API Input.GetButton/GetAxis generales

Actualmente, Unity usa sus API input.GetButton/Input.GetAxis generales para exponer la entrada del SDK de [Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) y [el SDK de OpenVR.](https://docs.unity3d.com/Manual/OpenVRControllers.html) Si las aplicaciones ya usan estas API para la entrada, las API Input.GetButton/Input.GetAxis son las rutas de acceso más fáciles para admitir controladores de movimiento en Windows Mixed Reality. Solo tendrá que reasignar botones y ejes en el Administrador de entrada.

Para más información, consulte la tabla [de asignación de ejes o](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) botones de Unity y la información general de las API [comunes de Unity.](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows XR específica de la aplicación. Wsa. API de entrada

Si la aplicación ya compila lógica de entrada personalizada para cada plataforma, puede usar las API de entrada espacial específicas de Windows en el espacio de nombres **UnityEngine.XR.WSA.Input.** Desde allí, accederá a información adicional, como la precisión de la posición o el tipo de origen, lo que le permite diferenciar las manos y los controladores en HoloLens.

Para más información, consulte la introducción a las API [UnityEngine.XR.WSA.Input.](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)

## <a name="grip-pose-vs-pointing-pose"></a>Posición de control frente a posición de apuntar

Windows Mixed Reality admite controladores de movimiento en diferentes factores de forma. El diseño de cada controlador difiere en su relación entre la posición de la mano del usuario y la dirección "hacia delante" natural que las aplicaciones deben usar para señalar al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de poses que puede investigar para cada origen de interacción:

* El **control posa**, que representa la ubicación de la mano detectada por un HoloLens o la mano que mantiene un controlador de movimiento.
    * En los cascos envolventes, esta  posición se usa mejor para representar la mano del usuario o un objeto que se mantiene en la mano del **usuario,** como un pólver o un revólver.
    * Posición **del control:** centroide de la mano al mantener el controlador de forma natural, ajustado a la izquierda o a la derecha para centrar la posición dentro del control.
    * Eje **derecho** de la orientación del control: cuando se abre completamente la mano para formar una posición plana de 5 dedos, el rayo que es normal para la mano (hacia delante desde la mano izquierda, hacia atrás desde la mano derecha).
    * Eje **hacia** delante de la orientación del control: al cerrar la mano parcialmente, como si sostendes el controlador, el rayo que apunta "hacia delante" a través del manso formado por los dedos que no son de los dedos.
    * Eje **Up de la orientación del control:** eje Up implícito en las definiciones Right y Forward.
    * Puede acceder a la posición de control a través de la API de entrada entre proveedores **[(XR) de Unity. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o a través de la API específica de Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** solicitando la posición De control).
* El **puntero posa**, que representa la punta del controlador que apunta hacia delante.
    * Esta posición se usa mejor para la difusión por **rayos** al apuntar a la interfaz de usuario cuando se representa el propio modelo de controlador.
    * Actualmente, la posición del puntero solo está disponible a través de la API específica de Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** que solicita la posición de puntero).

Estas coordenadas de posición se expresan en coordenadas globales de Unity.

## <a name="see-also"></a>Consulte también
* [Controladores de movimiento](). /.. /design/motion-controllers.md)
* [Controladores de movimiento en Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guías de migración](porting-guides.md)
