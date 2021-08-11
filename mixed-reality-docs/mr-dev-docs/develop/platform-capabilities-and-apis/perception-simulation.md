---
title: Simulación de percepción
description: Guía para usar la biblioteca Perception Simulation para automatizar la entrada simulada para aplicaciones envolventes
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulación, pruebas
ms.openlocfilehash: 8d2999868bfdcf67c1174209566e67fe937005946ef82dd50337d9098c1e1971
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193784"
---
# <a name="perception-simulation"></a>Simulación de percepción

¿Desea crear una prueba automatizada para la aplicación? ¿Quiere que las pruebas vayan más allá de las pruebas unitarias de nivel de componente y realmente realicen ejercicios de la aplicación de un extremo a otro? La simulación de percepción es lo que busca. La biblioteca Perception Simulation envía datos de entrada humanos y del mundo a la aplicación para que pueda automatizar las pruebas. Por ejemplo, puede simular la entrada de una persona que busca una posición específica y repetible y, a continuación, usar un gesto o un controlador de movimiento.

Perception Simulation puede enviar entradas simuladas como esta a un HoloLens físico, el emulador de HoloLens (primera generación), el HoloLens 2 Emulator o un equipo con Portal de realidad mixta instalado. Perception Simulation omite los sensores en directo en Mixed Reality dispositivo y envía entradas simuladas a las aplicaciones que se ejecutan en el dispositivo. Las aplicaciones reciben estos eventos de entrada a través de las mismas API que siempre usan y no pueden saber la diferencia entre la ejecución con sensores reales y la simulación de percepción. Perception Simulation es la misma tecnología que usan los emuladores de HoloLens para enviar entradas simuladas a la máquina virtual HoloLens virtual.

Para empezar a usar la simulación en el código, empiece por crear un objeto IPerceptionSimulationManager. Desde ese objeto, puede emitir comandos para controlar las propiedades de una "persona" simulada, incluida la posición de la cabeza, la posición de la mano y los gestos. También puede habilitar y manipular controladores de movimiento.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Configuración de un Visual Studio Project simulación de percepción
1. [Instale el emulador HoloLens en](../install-the-tools.md) el equipo de desarrollo. El emulador incluye las bibliotecas que se usan para Perception Simulation.
2. Cree un nuevo Visual Studio proyecto de escritorio de C# (una consola Project excelente para empezar a trabajar).
3. Agregue los siguientes archivos binarios al proyecto como referencias (Project->add->Reference...). Puede encontrarlos en %ProgramFiles(x86)%\Microsoft XDE \\ (versión), como **%ProgramFiles(x86)%\Microsoft XDE \\ 10.0.18362.0** para el HoloLens 2 Emulator.  (Nota: Aunque los archivos binarios forman parte del HoloLens 2 Emulator, también funcionan para Windows Mixed Reality en el escritorio). Un. PerceptionSimulationManager.Interop.dll: contenedor de C# administrado para la simulación de percepción.
    b. PerceptionSimulationRest.dll: biblioteca para configurar un canal de comunicación de socket web con el HoloLens o emulador.
    c. SimulationStream.Interop.dll: tipos compartidos para la simulación.
4. Agregue el archivo binario de PerceptionSimulationManager.dll al proyecto a. En primer lugar, agrégrelo como binario al proyecto (Project->add->Existing Item...). Guárdelo como un vínculo para que no lo copie en la carpeta de origen del proyecto. ![Agregue PerceptionSimulationManager.dll al proyecto como un vínculo ](images/saveaslink.png) b. A continuación, asegúrese de que se copia en la carpeta de salida en la compilación. Se encuentra en la hoja de propiedades del binario. ![Marcar PerceptionSimulationManager.dll copiar en el directorio de salida](images/copyalways.png)
5. Establezca la plataforma de solución activa en x64.  (Use la Administrador de configuración para crear una entrada de plataforma para x64 si aún no existe).

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Crear un objeto IPerceptionSimulation Manager

Para controlar la simulación, emitirá actualizaciones de los objetos recuperados de un objeto IPerceptionSimulationManager. El primer paso consiste en obtener ese objeto y conectarlo al emulador o dispositivo de destino. Para obtener la dirección IP del emulador, haga clic en el botón Portal de dispositivos de la barra de [herramientas.](using-the-hololens-emulator.md)

![Abrir Portal de dispositivos icono ](images/emulator-deviceportal.png) **Abrir Portal de dispositivos:** abra el Windows Portal de dispositivos del sistema HoloLens sistema operativo en el emulador.  Por Windows Mixed Reality, esto se puede recuperar en la aplicación de Configuración en "Actualizar seguridad de &" y, a continuación, en "Para desarrolladores" en la sección "Conectar using:" en "Habilitar Portal de dispositivos".  Asegúrese de tener en cuenta la dirección IP y el puerto.

En primer lugar, llamará a RestSimulationStreamSink.Create para obtener un objeto RestSimulationStreamSink. Se trata del dispositivo o emulador de destino que controlará sobre una conexión HTTP. Los comandos se pasarán y controlarán mediante la Windows Portal de dispositivos [que](using-the-windows-device-portal.md) se ejecuta en el dispositivo o emulador. Los cuatro parámetros que necesitará para crear un objeto son:
* URI uri: dirección IP del dispositivo de destino (por ejemplo, " https://123.123.123.123 " o " https://123.123.123.123:50080 ")
* Credenciales de System.Net.NetworkCredential: nombre de usuario y contraseña para conectarse al [Windows Portal de dispositivos](using-the-windows-device-portal.md) en el dispositivo o emulador de destino. Si se conecta al emulador a través de su dirección local (por ejemplo, 168.*.* *) en el mismo equipo, se aceptarán las credenciales.
* bool normal: true para la prioridad normal, false para prioridad baja. Por lo general, quiere establecer esto en *true para* escenarios de prueba, lo que permite que la prueba tome el control.  El emulador y Windows Mixed Reality simulación usan conexiones de prioridad baja.  Si la prueba también usa una conexión de prioridad baja, la conexión establecida más recientemente estará en control.
* Token de System.Threading.CancellationToken: token para cancelar la operación asincrónica.

En segundo lugar, creará IPerceptionSimulationManager. Este es el objeto que se usa para controlar la simulación. Esto también debe hacerse en un método asincrónico.

## <a name="control-the-simulated-human"></a>Control del humano simulado

IPerceptionSimulationManager tiene una propiedad Human que devuelve un objeto ISimulated Human. Para controlar la persona simulada, realice operaciones en este objeto. Por ejemplo:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Aplicación de consola de C# de ejemplo básico

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>Aplicación de consola de C# de ejemplo extendida

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>Nota sobre los controladores 6-DOF

Antes de llamar a cualquier propiedad de los métodos de un controlador 6-DOF simulado, debe activar el controlador.  Si no lo hace, se producirá una excepción.  A partir de Actualización de mayo de 2019 de Windows 10, los controladores 6-DOF simulados se pueden instalar y activar estableciendo la propiedad Status en el objeto ISimulatedSixDofController en SimulatedSixDofControllerStatus.Active.
En Actualización de octubre de 2018 de Windows 10 y versiones anteriores, primero debe instalar por separado un controlador 6-DOF simulado llamando a la herramienta PerceptionSimulationDevice ubicada en la carpeta \Windows\System32.  El uso de esta herramienta es el siguiente:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Por ejemplo

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Las acciones admitidas son:
* i = instalar
* q = consulta
* r = remove

Las instancias admitidas son:
* 1 = controlador 6-DOF izquierdo
* 2 = controlador 6-DOF derecho

El código de salida del proceso indicará que se ha hecho correctamente (un valor devuelto cero) o un error (un valor devuelto distinto de cero).  Al usar la acción "q" para consultar si un controlador está instalado, el valor devuelto será cero (0) si el controlador aún no está instalado o uno (1) si el controlador está instalado.

Al quitar un controlador en el Actualización de octubre de 2018 de Windows 10 o anterior, establezca su estado en Desactivado a través de la API en primer lugar y, a continuación, llame a la herramienta PerceptionSimulationDevice.

Esta herramienta debe ejecutarse como administrador.




## <a name="api-reference"></a>Referencia de API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

Describe un tipo de dispositivo simulado

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

Un dispositivo de referencia ficticio, el valor predeterminado para PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

Describe un modo de seguimiento de la cabeza

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

Seguimiento de la cabeza predeterminado. Esto significa que el sistema puede seleccionar el mejor modo de seguimiento de la cabeza en función de las condiciones de tiempo de ejecución.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

Seguimiento de la cabeza solo de orientación. Esto significa que es posible que la posición de seguimiento no sea confiable y que algunas funciones dependientes de la posición de la cabeza no estén disponibles.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

Seguimiento de la cabeza posicional. Esto significa que la posición de la cabeza y la orientación de la cabeza con seguimiento son confiables.

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

Describe un gesto simulado

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

Valor centinela que se usa para indicar que no hay gestos.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Gesto presionado con el dedo.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Gesto de dedo liberado.

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

Gesto de inicio o sistema.

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

Gesto máximo válido.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

Los posibles estados de un controlador 6-DOF simulado.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

El controlador 6-DOF está desactivado.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

El controlador 6-DOF está activado y se realiza el seguimiento.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

El controlador 6-DOF está activado, pero no se puede realizar el seguimiento.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

Botones admitidos en un controlador 6-DOF simulado.

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

Valor centinela que se usa para indicar que no hay botones.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

Se presiona el botón Inicio.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

Se presiona el botón Menú.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

Se presiona el botón Control.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

Se presiona TouchPad.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

Se presiona el botón Seleccionar.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

TouchPad se tocan.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

Se presiona la tecla Thumbstick.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

Botón máximo válido.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesIntegrationState

El estado de calibración de los ojos simulados

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesIntegrabrationState.Unavailable**

La calibración de los ojos no está disponible.

**Microsoft.PerceptionSimulation.SimulatedEyesIntegrabrationState.Ready**

Los ojos se han calibrado.  Este es el valor predeterminado.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configde datos**

Los ojos se calibran.

**Microsoft.PerceptionSimulation.SimulatedEyesIntegrabrationState.UserIntegrabrationNeeded**

Los ojos deben calibrarse.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

Precisión de seguimiento de una unión de la mano.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

No se realiza el seguimiento de la unión.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

La posición de la unión se deduce.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

Se realiza un seguimiento completo de la unión.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

Precisión de seguimiento de una unión de la mano.

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

Las uniones de los dedos de la mano están configuradas para reflejar una posición cerrada.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

Las uniones de los dedos de la mano están configuradas para reflejar una posición abierta.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

Las uniones de los dedos de la mano están configuradas para reflejar una posición apuntando.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

Las uniones de los dedos de la mano están configuradas para reflejar una posición de acercamiento.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

Valor máximo válido para SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Describe el estado de una reproducción.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

La grabación está detenida actualmente y lista para su reproducción.

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

La grabación se está reproduciendo actualmente.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

La grabación está actualmente en pausa.

**Microsoft.PerceptionSimulation.PlaybackState.End**

La grabación ha llegado al final.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Describe un vector de tres componentes, que podría describir un punto o un vector en el espacio 3D.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

Componente X del vector.

**Microsoft.PerceptionSimulation.Vector3.Y**

Componente Y del vector.

**Microsoft.PerceptionSimulation.Vector3.Z**

Componente Z del vector.

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

Construya un nuevo Vector3.

Parámetros
* x: componente x del vector.
* y: componente y del vector.
* z: componente z del vector.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Describe una rotación de tres componentes.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

El componente Pitch del giro, hacia abajo alrededor del eje X.

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Componente Yaw del giro, justo alrededor del eje Y.

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Componente Roll del giro, justo alrededor del eje Z.

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

Construya un nuevo rotation3.

Parámetros
* pitch: componente de lanzamiento de la rotación.
* yaw: el componente yaw de rotation.
* roll: componente de lanzamiento de rotation.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

Describe la configuración de una unión en una mano simulada.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

Posición de la unión.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

Rotación de la unión.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

Precisión de seguimiento de la unión.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Describe un frustum de vista, como suele usar una cámara.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

Distancia mínima que se encuentra en el frustum.

**Microsoft.PerceptionSimulation.Frustum.Far**

Distancia máxima que se encuentra en el frustum.

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

Campo horizontal de vista del frustum, en radianes (menor que PI).

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

La relación entre el campo horizontal de la vista y el campo de vista vertical.

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration

Describe la configuración de la pantalla del casco simulado.

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**

Transformación desde el centro de la cabeza hasta el ojo izquierdo para fines de representación estéreo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**

Rotación del ojo izquierdo para fines de representación estéreo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**

Transformación desde el centro de la cabeza hasta el ojo derecho para fines de representación estéreo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**

Rotación del ojo derecho para fines de representación estéreo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**

Valor ipd notificado por el sistema para fines de representación estéreo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**

Si los valores proporcionados para las transformaciones de los ojos izquierdo y derecho deben considerarse válidos y aplicarse al sistema en ejecución.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**

Si el valor proporcionado para Ipd debe considerarse válido y aplicarse al sistema en ejecución.


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Raíz para generar los paquetes usados para controlar un dispositivo.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

Recupere el objeto de dispositivo simulado que interpreta el ser humano simulado y el mundo simulado.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

Recupere el objeto que controla el humano simulado.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

Restablece la simulación a su estado predeterminado.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

Interfaz que describe el dispositivo, que interpreta el mundo simulado y el humano simulado

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

Recupere el seguimiento de la cabeza del dispositivo simulado.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

Recupere el seguimiento de mano del dispositivo simulado.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

Establezca las propiedades del dispositivo simulado para que coincidan con el tipo de dispositivo proporcionado.

Parámetros
* type: el nuevo tipo de dispositivo simulado

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>Microsoft.PerceptionSimulation.ISimulatedDevice2

Hay propiedades adicionales disponibles mediante la conversión de ISimulatedDevice a ISimulatedDevice2

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**

Recupere o establezca si el humano simulado lleva activamente el casco.

**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**

Recupere o establezca las propiedades de la pantalla simulada.

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de la cabeza del humano simulado.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

Recupera y establece el modo de seguimiento de la cabeza actual.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de las manos del humano simulado

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

Recupere la posición del nodo con respecto al mundo, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Recupere y establezca la posición del seguimiento de mano simulado, en relación con el centro de la cabeza.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Recupere y establezca el paso hacia abajo del rastreador de manos simulado.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Recupere y establezca si se omite el frustum del seguimiento de manos simulado. Cuando se omite, ambas manos siempre están visibles. Cuando no se omiten (el valor predeterminado) las manos solo son visibles cuando están dentro del frustum del rastreador de manos.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Recupere y establezca las propiedades de frustum que se usan para determinar si las manos son visibles para el seguimiento de manos simulado.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedGrad

Interfaz de nivel superior para controlar la persona simulada.

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft.PerceptionSimulation.ISimulatedComposición.WorldPosition**

Recupere y establezca la posición del nodo con respecto al mundo, en metros. La posición corresponde a un punto en el centro de los pies de la persona.

**Microsoft.PerceptionSimulation.ISimulatedGrad.Direction**

Recupere y establezca la dirección en la que se enfrentan las caras humanas simuladas en el mundo. 0 radianes mira hacia abajo el eje Z negativo. Los radianes positivos giran en el sentido de las agujas del reloj sobre el eje Y.

**Microsoft.PerceptionSimulation.ISimulatedDula.Height**

Recupere y establezca el alto del humano simulado, en metros.

**Microsoft.PerceptionSimulation.ISimulatedDula.LeftHand**

Recupere la mano izquierda del humano simulado.

**Microsoft.PerceptionSimulation.ISimulatedDula.RightHand**

Recupere la mano derecha del humano simulado.

**Microsoft.PerceptionSimulation.ISimulatedDula.Head**

Recupere la cabeza del humano simulado.

**Microsoft.PerceptionSimulation.ISimulatedGrad.Move(Microsoft.PerceptionSimulation.Vector3)**

Mueva el humano simulado en relación con su posición actual, en metros.

Parámetros
* translation: la traducción que se moverá, en relación con la posición actual.

**Microsoft.PerceptionSimulation.ISimulatedDula.Rotate(System.Single)**

Girar la persona simulada con respecto a su dirección actual, en el sentido de las agujas del reloj sobre el eje Y

Parámetros
* radianes: la cantidad que se gira alrededor del eje Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedSim2

Hay propiedades adicionales disponibles mediante la conversión de ISimulated Human a ISimulated Human2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedController2.LeftController**

Recupere el controlador 6-DOF izquierdo.

**Microsoft.PerceptionSimulation.ISimulatedController2.RightController**

Recupere el controlador 6-DOF correcto.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

Interfaz que describe una mano del humano simulado

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

Recupere la posición del nodo con respecto al mundo, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

Recupere y establezca la posición de la mano simulada con respecto al humano, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

Recupere y establezca si la mano está activada actualmente.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

Recupere si la mano está visible actualmente para SimulatedDevice (es decir, si está en una posición que el HandTracker va a detectar).

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

Mueva la mano para que sea visible para SimulatedDevice.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

Mueva la posición de la mano simulada con respecto a su posición actual, en metros.

Parámetros
* translation: la cantidad para traducir la mano simulada.

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Realice un gesto con la mano simulada.  Solo lo detectará el sistema si la mano está habilitada.

Parámetros
* gesture: el gesto que se debe realizar.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

Hay propiedades adicionales disponibles mediante la conversión de ISimulatedHand a ISimulatedHand2.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

Recupere o establezca la rotación de la mano simulada.  Los radianes positivos giran en el sentido de las agujas del reloj al mirar a lo largo del eje.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

Hay propiedades adicionales disponibles mediante la conversión de ISimulatedHand a ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

Obtenga la configuración de la unión para la unión especificada.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

Establezca la configuración de la unión para la unión especificada.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

Establezca la mano en una posición conocida con una marca opcional para animar.  Nota: La animación no dará lugar a que las uniones reflejen inmediatamente sus configuraciones de juntas finales.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Interfaz que describe la cabeza del humano simulado.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

Recupere la posición del nodo con respecto al mundo, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Recupere la rotación del head simulado. Los radianes positivos giran en el sentido de las agujas del reloj al mirar a lo largo del eje.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Recupere el diámetro de la cabeza simulada. Este valor se usa para determinar el centro de la cabeza (punto de rotación).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Girar la cabeza simulada con respecto a su rotación actual. Los radianes positivos giran en el sentido de las agujas del reloj al mirar a lo largo del eje.

Parámetros
* rotation: la cantidad que se girará.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

Hay propiedades adicionales disponibles mediante la conversión de ISimulatedHead a ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

Recupere los ojos del humano simulado.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

Interfaz que describe un controlador 6-DOF asociado a la persona simulada.

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

Recupere la posición del nodo con respecto al mundo, en metros.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

Recupere o establezca el estado actual del controlador.  El estado del controlador debe establecerse en un valor distinto de Desactivado antes de que las llamadas para mover, girar o presionar botones se realizarán correctamente.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

Recupere o establezca la posición del controlador simulado con respecto al humano, en metros.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

Recupere o establezca la orientación del controlador simulado.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

Mueva la posición del controlador simulado con respecto a su posición actual, en metros.

Parámetros
* translation: la cantidad para traducir el controlador simulado.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

Presione un botón en el controlador simulado.  Solo lo detectará el sistema si el controlador está habilitado.

Parámetros
* button: botón que se debe presionar.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

Suelte un botón en el controlador simulado.  Solo lo detectará el sistema si el controlador está habilitado.

Parámetros
* button: botón que se debe liberar.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**

Obtenga la posición de un dedo simulado en el panel táctil del controlador simulado.

Parámetros
* x: posición horizontal del dedo.
* y: posición vertical del dedo.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**

Establezca la posición de un dedo simulado en el panel táctil del controlador simulado.

Parámetros
* x: posición horizontal del dedo.
* y: posición vertical del dedo.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

Hay propiedades y métodos adicionales disponibles mediante la conversión de ISimulatedSixDofController a ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**

Obtenga la posición del control de posición simulado en el controlador simulado.

Parámetros
* x: posición horizontal del control de posición.
* y: posición vertical del control de posición.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**

Establezca la posición del control de posición simulado en el controlador simulado.

Parámetros
* x: posición horizontal del control de posición.
* y: posición vertical del control de posición.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

Recupere o establezca el nivel de batería del controlador simulado.  El valor debe ser mayor que 0,0 y menor o igual que 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

Interfaz que describe los ojos del humano simulado.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

Recupera la rotación de los ojos simulados. Los radianes positivos giran en el sentido de las agujas del reloj al mirar a lo largo del eje.

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Girar los ojos simulados con respecto a su rotación actual. Los radianes positivos giran en el sentido de las agujas del reloj al mirar a lo largo del eje.

Parámetros
* rotation: la cantidad que se debe girar.

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

Recupera o establece el estado de calibración de los ojos simulados.

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

Recupere la posición del nodo con respecto al mundo, en metros.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

Interfaz para interactuar con una sola grabación cargada para la reproducción.

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

Recupera la lista de tipos de datos de la grabación.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

Recupera el estado actual de la grabación.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

Inicie la reproducción. Si la grabación está en pausa, la reproducción se reanudará desde la ubicación en pausa. Si se detiene, la reproducción se iniciará al principio. Si ya se está reproduciendo, se omite esta llamada.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

Pausa la reproducción en su ubicación actual. Si se detiene la grabación, se omite la llamada.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

Busca la grabación a la hora especificada (en intervalos de 100 nanosegundos desde el principio) y se pausa en esa ubicación. Si el tiempo está más allá del final de la grabación, se pausa en el último fotograma.

Parámetros
* ticks: hora a la que se va a buscar.

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Detiene la reproducción y restablece la posición al principio.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Interfaz para recibir cambios de estado durante la reproducción.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Se llama cuando el estado de reproducción de ISimulationRecording ha cambiado.

Parámetros
* newState: el nuevo estado de la grabación.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Objeto raíz para crear objetos de simulación de percepción.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

Cree en el objeto para generar paquetes simulados y entregarlos al receptor proporcionado.

Parámetros
* sink: el receptor que recibirá todos los paquetes generados.

Valor devuelto

Administrador creado.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Cree un receptor, que almacena todos los paquetes recibidos en un archivo en la ruta de acceso especificada.

Parámetros
* path: ruta de acceso del archivo que se creará.

Valor devuelto

Receptor creado.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Cargue una grabación desde el archivo especificado.

Parámetros
* path: ruta de acceso del archivo que se cargará.
* factory: un generador utilizado por la grabación para crear un ISimulationStreamSink cuando es necesario.

Valor devuelto

Grabación cargada.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Cargue una grabación desde el archivo especificado.

Parámetros
* path: ruta de acceso del archivo que se cargará.
* factory: un generador utilizado por la grabación para crear un ISimulationStreamSink cuando es necesario.
* devolución de llamada: devolución de llamada, que recibe actualizaciones que degradan el estado de la grabación.

Valor devuelto

Grabación cargada.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Describe los distintos tipos de datos de flujo.

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

Valor de Sentinel que se usa para indicar que no hay tipos de datos de flujo.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Flujo de datos para la posición y orientación de la cabeza.

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Flujo de datos para la posición y los gestos de las manos.

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Flujo de datos para la asignación espacial del entorno.

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Flujo de datos para la calibración del dispositivo. Los paquetes de calibración solo los acepta un sistema en modo remoto.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Flujo de datos para el entorno del dispositivo.

**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**

Flujo de datos para controladores de movimiento.

**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**

Flujo de datos con los ojos de la persona simulada.

**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**

Flujo de datos con la configuración de pantalla del dispositivo.

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Valor centinela que se usa para indicar todos los tipos de datos registrados.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Objeto que recibe paquetes de datos de un flujo de simulación.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

Recibe un único paquete, que se escribe internamente y tiene versiones.

Parámetros
* length: longitud del paquete.
* packet: los datos del paquete.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Objeto que crea ISimulationStreamSink.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Crea una única instancia de ISimulationStreamSink.

Valor devuelto

Receptor creado.
