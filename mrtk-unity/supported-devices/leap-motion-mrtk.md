---
title: MRTK de movimiento intercalar
description: Documentación que se debe configurar para Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Leap Motion,
ms.openlocfilehash: 285328b1248f04504f30192f1294e9ae665b3fc9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145195"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Configuración del seguimiento de manos de Leap Motion (by Ultraleap) en MRTK

Se [requiere un controlador leap motion](https://www.ultraleap.com/product/leap-motion-controller/) para usar este proveedor de datos.

El proveedor de datos Leap Motion permite el seguimiento de manos articulado para VR y podría ser útil para la creación rápida de prototipos en el editor.  El proveedor de datos se puede configurar para usar el controlador leap motion montado en un casco o colocado en un escritorio cara arriba.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Este proveedor se puede usar en el editor y en el dispositivo en la plataforma independiente.  También se puede usar en el editor en la plataforma UWP, pero NO en una compilación de UWP.

|Versiones admitidas de los módulos de Unity de Leap Motion|
|---|
|4.5.0|
|4.5.1|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Uso del seguimiento manual de Leap Motion (by Ultraleap) en MRTK

1. Importación de MRTK y los módulos leap motion de Unity
    - Instale [el SDK de Leap Motion 4.0.0](https://developer.leapmotion.com/releases/?category=orion) si aún no está instalado
    - Importe el **paquete Microsoft.MixedReality.Toolkit.Foundation** en el proyecto de Unity.
    - Descarga e importación de la versión más reciente de los módulos [de Unity leap motion](https://developer.leapmotion.com/unity) en el proyecto
        - Importar solo el **paquete Principal** dentro de los módulos de Unity

1. Integración de los módulos de Unity leap motion con MRTK
    - Una vez que los módulos de Unity estén en el proyecto, vaya a **Mixed Reality Toolkit**  >  **Leap Motion** Integrate Leap Motion Unity Modules (Integración de los módulos leap motion de  >  **Unity).**
    > [!NOTE]
    > La integración de los módulos de Unity en MRTK agrega 10 definiciones de ensamblado al proyecto y agrega referencias a la definición del ensamblado **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.** Asegúrese de que Visual Studio esté cerrado.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Agregar el proveedor de datos Leap Motion
    - Creación de una escena de Unity
    - Para agregar MRTK a la escena, vaya **a Mixed Reality Toolkit** Add to Scene and Configure (Agregar a la escena y  >  **configurar)**
    - Seleccione el objeto de juego MixedRealityToolkit en la jerarquía y seleccione **Copiar y** personalizar para clonar el perfil de realidad mixta predeterminado.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - Selección del perfil **de configuración** de entrada

    ![Perfil de configuración de entrada 1](../images/cross-platform/InputConfigurationProfile.png)

    - Seleccione **Clonar** en el perfil del sistema de entrada para habilitar la modificación.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - Abra la sección Proveedores  de datos **de** entrada, seleccione Agregar proveedor de datos en la parte superior y se agregará un nuevo proveedor de datos al final de la lista.  Abra el nuevo proveedor de datos y establezca **el** tipo en **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager.**

    ![Leap Add Data Provider](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Seleccione **Clonar** para cambiar la configuración predeterminada de Leap Motion.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - El proveedor de datos leap motion contiene `LeapControllerOrientation` la propiedad que es la ubicación del controlador de movimiento leap. `LeapControllerOrientation.Headset` indica que el controlador está montado en un casco. `LeapControllerOrientation.Desk` indica que el controlador se coloca plano sobre el escritorio. El valor predeterminado se establece en `LeapControllerOrientation.Headset` .
    - Cada orientación del controlador contiene propiedades de desplazamiento:
      - Las **propiedades de desplazamiento** de orientación del casco reflejan las propiedades de desplazamiento en el componente LeapXRServiceProvider.  tiene `LeapVRDeviceOffsetMode` tres opciones: Predeterminada, Desplazamiento manual de la cabeza y Transformación.  Si el modo de desplazamiento es Predeterminado, no se aplicará un desplazamiento al controlador leap motion.  El modo desplazamiento manual de la cabeza permite la modificación de tres propiedades: `LeapVRDeviceOffsetY` y `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` .  A continuación, los valores de propiedad de desplazamiento del eje se aplican a la ubicación predeterminada del controlador.  El modo de desplazamiento Transformar contiene la `LeapVRDeviceOrigin` propiedad Transformar que especifica un nuevo origen para el controlador leap motion.
      - La **orientación desk** contiene la propiedad que define la posición `LeapControllerOffset` delimitadora de las manos bisiesta del escritorio.  El desplazamiento se calcula en relación con la posición de la cámara principal y el valor predeterminado es (0,-0,2, 0,35) para asegurarse de que las manos aparecen delante y a la vista de la cámara.

        > [!NOTE]
        > Las propiedades de desplazamiento del perfil se aplican una vez cuando se inicia la aplicación.  Para modificar los valores durante el tiempo de ejecución, obtenga el proveedor del servicio Leap Motion en la página Leap Motion Administrador de dispositivos:
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` y `ExitPinchDistance` son los umbrales de distancia para la detección de gestos de pulsar en el aire o desenlazador.  El gesto de acercar se calcula midiendo la distancia entre la punta del dedo índice y la punta del dedo.  Para generar un evento de entrada hacia abajo, el valor `EnterPinchDistance` predeterminado se establece en 0,02.  Para generar un evento de entrada arriba (salir de la acción de acercar), la distancia predeterminada entre la punta del dedo índice y la punta del control es 0,05.

    `LeapControllerOrientation`: casco (valor predeterminado) |  `LeapControllerOrientation`: Desk
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. Prueba del proveedor de datos Leap Motion
    - Una vez agregado el proveedor de datos leap motion al perfil del sistema de entrada, presione play, mueva la mano delante del leap motion controller y debería ver la representación conjunta de la mano.

1. Creación del proyecto
    - Vaya a **File > Build Settings (Configuración > compilación de archivos).**
    - Solo se admiten compilaciones independientes si se usa el proveedor de datos Leap Motion.
    - Para obtener instrucciones sobre cómo usar un casco Windows Mixed Reality para compilaciones independientes, consulte Compilación e implementación [de MRTK (independiente).](wmr-mrtk.md#building-and-deploying-mrtk-standalone)

## <a name="getting-the-hand-joints"></a>Obtención de las uniones de mano

La obtención de uniones mediante el proveedor de datos Leap Motion es idéntica a la recuperación conjunta manual para una mano articulada de MRTK.  Para obtener más información, vea [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).

Con MRTK en una escena de Unity y el proveedor de datos Leap Motion agregado como proveedor de datos de entrada en el perfil del sistema de entrada, cree un objeto de juego vacío y adjunte el siguiente script de ejemplo.

Este script es un ejemplo sencillo de cómo recuperar la posición de la coyuntura de la mano de la mano de movimiento bisiesto.  Una esfera sigue a la mano leap izquierda, mientras que un cubo sigue a la mano leap derecha.

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a>Sugerencia de flujo de trabajo del editor de Unity

El uso del proveedor de datos Leap Motion no requiere un casco de realidad virtual.  Los cambios en una aplicación MRTK se pueden probar en el editor con las manos leap sin casco.

Las manos leap motion se mostrarán en el editor, sin un casco de realidad virtual conectado.  Si está establecido en Casco, el controlador Leap Motion tendrá que mantener el control Leap Motion con una mano con la `LeapControllerOrientation` cámara orientada hacia delante. 

> [!NOTE]
> Si la cámara se mueve mediante teclas WASD en el editor y es Casco , las manos `LeapControllerOrientation` no seguirán a la cámara.  Las manos solo seguirán el movimiento de la cámara si un casco vr está conectado mientras `LeapControllerOrientation` está establecido el **casco**.  Las manos bisiesta seguirán el movimiento de la cámara en el editor si `LeapControllerOrientation` está establecido en **Desk**.

## <a name="removing-leap-motion-from-the-project"></a>Quitar Leap Motion del proyecto

1. Vaya a los **módulos de Unity leap** motion independientes  >  **Mixed Reality Toolkit Leap Motion**  >  
    - Permitir que Unity se actualice como referencias en el **archivo Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** se modifica en este paso.
1. Cerrar Unity
1. Cierre Visual Studio, si está abierto
1. Abra Explorador de archivos y vaya a la raíz del proyecto de Unity de MRTK.
    - Eliminación del **directorio UnityProjectName/Library**
    - Eliminación **del directorio UnityProjectName/Assets/Plugins/LeapMotion**
    - Eliminación **del archivo UnityProjectName/Assets/Plugins/LeapMotion.meta**
1. Volver a abrir Unity

En Unity 2018.4, es posible que observe que los errores permanecen en la consola después de eliminar la biblioteca y los recursos principales de Leap Motion.
Si se registran errores después de volver a abrir, reinicie Unity de nuevo.

## <a name="common-errors"></a>Errores comunes

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap Motion no se ha integrado con MRTK

Para probar si los módulos de Unity leap motion se han integrado con MRTK:

- Vaya a Mixed Reality **Toolkit > Utilities > Leap Motion > Estado de integración.**
  - Se mostrará una ventana emergente con un mensaje sobre si los módulos de Unity leap motion se han integrado con MRTK o no.
- Si el mensaje indica que los recursos no se han integrado:
  - Asegúrese de que los módulos leap motion de Unity están en el proyecto.
  - Asegúrese de que se admite la versión agregada, consulte la tabla en la parte superior de la página para ver las versiones admitidas.
  - Pruebe **Mixed Reality Toolkit > Utilities > Leap Motion > integrar módulos de Unity leap motion**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Error al copiar HLAPI multijugador de ensamblado

Al importar los recursos principales de Unity De Leap Motion, este error podría registrarse:

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Solución**

- Una solución a corto plazo es reiniciar Unity. Consulte [el problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) para obtener más información.

## <a name="leap-motion-example-scene"></a>Escena de ejemplo de leap motion

En la escena de ejemplo se usa el perfil DefaultLeapMotionConfiguration y se determina si el proyecto de Unity se ha configurado correctamente para usar el proveedor de datos Leap Motion.

La escena de ejemplo se encuentra en el **paquete Microsoft.MixedReality.Toolkit.Examples** del **directorio MRTK/Examples/Demos/HandTracking/.**  

## <a name="see-also"></a>Consulte también

-[Proveedores de entrada](../features/input/input-providers.md) 
- [Seguimiento de manos](../features/input/hand-tracking.md)
