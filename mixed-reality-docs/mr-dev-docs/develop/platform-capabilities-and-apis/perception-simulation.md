---
title: Simulación de percepción
description: Guía para el uso de la biblioteca de simulación de percepción para automatizar la entrada simulada para aplicaciones envolventes
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulación, pruebas
ms.openlocfilehash: 64028c3a1ad58cecfebc93aee325b73c3a6a649a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530396"
---
# <a name="perception-simulation"></a><span data-ttu-id="e1fd0-104">Simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="e1fd0-104">Perception simulation</span></span>

<span data-ttu-id="e1fd0-105">¿Desea crear una prueba automatizada para la aplicación?</span><span class="sxs-lookup"><span data-stu-id="e1fd0-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="e1fd0-106">¿Desea que las pruebas vayan más allá de las pruebas unitarias de nivel de componente y realmente ejecute su aplicación de un extremo a otro?</span><span class="sxs-lookup"><span data-stu-id="e1fd0-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="e1fd0-107">La simulación de percepción es lo que está buscando.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="e1fd0-108">La biblioteca de simulación de percepción envía datos de entrada humanos y del mundo a la aplicación para que pueda automatizar las pruebas.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="e1fd0-109">Por ejemplo, puede simular la entrada de un usuario que busca una posición específica y repetible y, a continuación, usar un gesto o un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then use a gesture or motion controller.</span></span>

<span data-ttu-id="e1fd0-110">La simulación de percepción puede enviar una entrada simulada como esta a una HoloLens física, el emulador de HoloLens (primera generación), el emulador de HoloLens 2 o un equipo con el portal de realidad mixta instalado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (first gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="e1fd0-111">La simulación de percepción omite los sensores en directo en un dispositivo de realidad mixta y envía una entrada simulada a las aplicaciones que se ejecutan en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="e1fd0-112">Las aplicaciones reciben estos eventos de entrada a través de las mismas API que siempre usan y no indican la diferencia entre la ejecución con sensores reales frente a la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus Perception Simulation.</span></span> <span data-ttu-id="e1fd0-113">La simulación de percepción es la misma tecnología que usan los emuladores de HoloLens para enviar datos simulados a la máquina virtual HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="e1fd0-114">Para empezar a usar la simulación en el código, empiece por crear un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="e1fd0-115">Desde ese objeto, puede emitir comandos para controlar las propiedades de una "persona" simulada, incluida la posición del encabezado, la posición de la mano y los gestos.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span> <span data-ttu-id="e1fd0-116">También puede habilitar y manipular los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-116">You can also enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="e1fd0-117">Configuración de un proyecto de Visual Studio para la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="e1fd0-117">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="e1fd0-118">[Instale el emulador de HoloLens](../install-the-tools.md) en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-118">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="e1fd0-119">El emulador incluye las bibliotecas que se usan para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-119">The emulator includes the libraries you' use for Perception Simulation.</span></span>
2. <span data-ttu-id="e1fd0-120">Cree un nuevo proyecto de escritorio de Visual Studio C# (un proyecto de consola funciona bien para empezar a trabajar).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-120">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="e1fd0-121">Agregue los siguientes archivos binarios al proyecto como referencias (proyecto->referencia del complemento de >...). Puede encontrarlos en% ProgramFiles (x86)% \ Microsoft XDE \\ (versión), como **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** para el emulador de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-121">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="e1fd0-122">(Nota: aunque los archivos binarios forman parte del emulador de HoloLens 2, también funcionan para Windows Mixed Reality en el escritorio). un.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-122">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="e1fd0-123">Contenedor de C# administrado por PerceptionSimulationManager.Interop.dll para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-123">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="e1fd0-124">b.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-124">b.</span></span> <span data-ttu-id="e1fd0-125">PerceptionSimulationRest.dll-Library para configurar un canal de comunicación de socket web a HoloLens o Emulator.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-125">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="e1fd0-126">c.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-126">c.</span></span> <span data-ttu-id="e1fd0-127">SimulationStream.Interop.dll: tipos compartidos para la simulación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-127">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="e1fd0-128">Agregue la PerceptionSimulationManager.dll binaria de implementación al proyecto a.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-128">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="e1fd0-129">Agréguelo primero como un archivo binario al proyecto (proyecto->agregar >elemento existente...). Guárdelo como un vínculo para que no lo copie en la carpeta de origen del proyecto.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-129">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="e1fd0-130">![Agregue PerceptionSimulationManager.dll al proyecto como un vínculo ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-130">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="e1fd0-131">Después, asegúrese de que se copia en la carpeta de salida en la compilación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-131">Then make sure that it gets copied to your output folder on build.</span></span> <span data-ttu-id="e1fd0-132">Está en la hoja de propiedades del archivo binario.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-132">This is in the property sheet for the binary.</span></span> <span data-ttu-id="e1fd0-133">![Marcar PerceptionSimulationManager.dll para copiarlo en el directorio de salida](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="e1fd0-133">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="e1fd0-134">Establezca la plataforma de soluciones activa en x64.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-134">Set your active solution platform to x64.</span></span>  <span data-ttu-id="e1fd0-135">(Utilice la Configuration Manager para crear una entrada de plataforma para x64 si aún no existe ninguna).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-135">(Use the Configuration Manager to create a Platform entry for x64 if one doesn't already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="e1fd0-136">Creación de un objeto de administrador de IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="e1fd0-136">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="e1fd0-137">Para controlar la simulación, emitirá actualizaciones de los objetos recuperados de un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-137">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="e1fd0-138">El primer paso es obtener ese objeto y conectarlo al dispositivo o emulador de destino.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-138">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="e1fd0-139">Para obtener la dirección IP del emulador, haga clic en el botón portal de dispositivos en la [barra de herramientas](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="e1fd0-139">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="e1fd0-140">![Abra el icono del portal de dispositivos ](images/emulator-deviceportal.png) **abrir portal** de dispositivos: Abra el portal de dispositivos de Windows para el sistema operativo HoloLens en el emulador.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-140">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="e1fd0-141">En el caso de Windows Mixed Reality, puede recuperarse en la aplicación de configuración en "actualizar & seguridad" y luego en "para desarrolladores" en la sección "conectar usando:" en "habilitar el portal de dispositivos".</span><span class="sxs-lookup"><span data-stu-id="e1fd0-141">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="e1fd0-142">Asegúrese de anotar la dirección IP y el puerto.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-142">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="e1fd0-143">En primer lugar, llame a RestSimulationStreamSink. Create para obtener un objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-143">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="e1fd0-144">Este es el dispositivo de destino o el emulador que controlará una conexión http.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-144">This is the target device or emulator that you'll control over an http connection.</span></span> <span data-ttu-id="e1fd0-145">Los comandos se pasarán y controlarán en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) que se ejecuta en el dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-145">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="e1fd0-146">Los cuatro parámetros que necesitará para crear un objeto son:</span><span class="sxs-lookup"><span data-stu-id="e1fd0-146">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="e1fd0-147">URI del URI: dirección IP del dispositivo de destino (por ejemplo, " https://123.123.123.123 " o " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="e1fd0-147">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="e1fd0-148">Credenciales de System .net. NetworkCredential: nombre de usuario/contraseña para conectarse al [portal de dispositivos de Windows](using-the-windows-device-portal.md) en el emulador o dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-148">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="e1fd0-149">Si se va a conectar al emulador a través de su dirección local (por ejemplo,*168...* \*) en el mismo equipo, se aceptarán las credenciales.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-149">If you're connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="e1fd0-150">bool normal: true para la prioridad normal; false para la prioridad baja.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-150">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="e1fd0-151">Por lo general, desea establecer este valor en *true* para los escenarios de prueba, lo que permite que la prueba tome el control.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-151">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="e1fd0-152">El emulador y la simulación de Windows Mixed Reality usan conexiones de prioridad baja.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-152">The emulator and Windows Mixed Reality simulation use low-priority connections.</span></span>  <span data-ttu-id="e1fd0-153">Si la prueba también usa una conexión de prioridad baja, la conexión establecida más recientemente tendrá el control.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-153">If your test also uses a low-priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="e1fd0-154">System. Threading. CancellationToken token-token para cancelar la operación asincrónica.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-154">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="e1fd0-155">En segundo lugar, creará el IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-155">Second, you'll create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="e1fd0-156">Este es el objeto que se usa para controlar la simulación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-156">This is the object you use to control simulation.</span></span> <span data-ttu-id="e1fd0-157">Esto también se debe hacer en un método asincrónico.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-157">This must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="e1fd0-158">Controlar el usuario simulado</span><span class="sxs-lookup"><span data-stu-id="e1fd0-158">Control the simulated Human</span></span>

<span data-ttu-id="e1fd0-159">Un IPerceptionSimulationManager tiene una propiedad humana que devuelve un objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-159">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="e1fd0-160">Para controlar el humano simulado, realice operaciones en este objeto.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-160">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="e1fd0-161">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e1fd0-161">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="e1fd0-162">Aplicación de consola C# de ejemplo básica</span><span class="sxs-lookup"><span data-stu-id="e1fd0-162">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="e1fd0-163">Aplicación de consola de C# de ejemplo extendida</span><span class="sxs-lookup"><span data-stu-id="e1fd0-163">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="e1fd0-164">Nota en los controladores de 6 DOF</span><span class="sxs-lookup"><span data-stu-id="e1fd0-164">Note on 6-DOF controllers</span></span>

<span data-ttu-id="e1fd0-165">Antes de llamar a cualquier propiedad de los métodos en un controlador simulado de 6 DOF, debe activar el controlador.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-165">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="e1fd0-166">Si no lo hace, se producirá una excepción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-166">Not doing so will result in an exception.</span></span>  <span data-ttu-id="e1fd0-167">A partir de la actualización 2019 de Windows 10, se pueden instalar y activar controladores simulados de 6 DOF si se establece la propiedad Status en el objeto ISimulatedSixDofController en SimulatedSixDofControllerStatus. Active.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-167">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="e1fd0-168">En la actualización de Windows 10 de octubre de 2018 y versiones anteriores, debe instalar por separado un controlador simulado de 6 DOF en primer lugar mediante una llamada a la herramienta PerceptionSimulationDevice que se encuentra en la carpeta \Windows\System32..</span><span class="sxs-lookup"><span data-stu-id="e1fd0-168">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="e1fd0-169">El uso de esta herramienta es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="e1fd0-169">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="e1fd0-170">Por ejemplo</span><span class="sxs-lookup"><span data-stu-id="e1fd0-170">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="e1fd0-171">Las acciones admitidas son:</span><span class="sxs-lookup"><span data-stu-id="e1fd0-171">Supported actions are:</span></span>
* <span data-ttu-id="e1fd0-172">i = instalación</span><span class="sxs-lookup"><span data-stu-id="e1fd0-172">i = install</span></span>
* <span data-ttu-id="e1fd0-173">q = consulta</span><span class="sxs-lookup"><span data-stu-id="e1fd0-173">q = query</span></span>
* <span data-ttu-id="e1fd0-174">r = quitar</span><span class="sxs-lookup"><span data-stu-id="e1fd0-174">r = remove</span></span>

<span data-ttu-id="e1fd0-175">Las instancias admitidas son:</span><span class="sxs-lookup"><span data-stu-id="e1fd0-175">Supported instances are:</span></span>
* <span data-ttu-id="e1fd0-176">1 = el controlador de 6 DOF izquierdo</span><span class="sxs-lookup"><span data-stu-id="e1fd0-176">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="e1fd0-177">2 = el controlador de 6 DOF adecuado</span><span class="sxs-lookup"><span data-stu-id="e1fd0-177">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="e1fd0-178">El código de salida del proceso indicará que la operación se ha realizado correctamente (un valor devuelto de cero) o un error (valor devuelto distinto de cero).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-178">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="e1fd0-179">Al usar la acción ' q ' para consultar si un controlador está instalado, el valor devuelto será cero (0) si el controlador no está ya instalado o uno (1) si el controlador está instalado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-179">When using the 'q' action to query whether a controller is installed, the return value will be zero (0) if the controller isn't already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="e1fd0-180">Al quitar un controlador en la actualización 2018 de octubre de Windows 10 o versiones anteriores, establezca su estado en desactivado a través de la API primero y, a continuación, llame a la herramienta PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-180">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="e1fd0-181">Esta herramienta debe ejecutarse como administrador.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-181">This tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="e1fd0-182">Referencia de API</span><span class="sxs-lookup"><span data-stu-id="e1fd0-182">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="e1fd0-183">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="e1fd0-183">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="e1fd0-184">Describe un tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="e1fd0-184">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="e1fd0-185">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-185">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="e1fd0-186">Un dispositivo de referencia ficticio, el valor predeterminado para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e1fd0-186">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="e1fd0-187">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="e1fd0-187">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="e1fd0-188">Describe un modo de seguimiento de encabezado</span><span class="sxs-lookup"><span data-stu-id="e1fd0-188">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="e1fd0-189">**Microsoft. PerceptionSimulation. HeadTrackerMode. default**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-189">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="e1fd0-190">Seguimiento de encabezado predeterminado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-190">Default Head Tracking.</span></span> <span data-ttu-id="e1fd0-191">Esto significa que el sistema puede seleccionar el mejor modo de seguimiento de los encabezados según las condiciones del tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-191">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="e1fd0-192">**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-192">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="e1fd0-193">Seguimiento de encabezado de solo orientación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-193">Orientation Only Head Tracking.</span></span> <span data-ttu-id="e1fd0-194">Esto significa que es posible que la posición de la que se realiza el seguimiento no sea confiable y que algunas funciones que dependen de la posición principal no estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-194">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="e1fd0-195">**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-195">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="e1fd0-196">Seguimiento de los cabezales posicionales.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-196">Positional Head Tracking.</span></span> <span data-ttu-id="e1fd0-197">Esto significa que la posición y la orientación del encabezado controlados son confiables</span><span class="sxs-lookup"><span data-stu-id="e1fd0-197">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="e1fd0-198">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="e1fd0-198">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="e1fd0-199">Describe un gesto simulado</span><span class="sxs-lookup"><span data-stu-id="e1fd0-199">Describes a simulated gesture</span></span>

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

<span data-ttu-id="e1fd0-200">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-200">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="e1fd0-201">Un valor de centinela que se usa para indicar que no hay gestos.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-201">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="e1fd0-202">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-202">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="e1fd0-203">Gesto de presionar un dedo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-203">A finger pressed gesture.</span></span>

<span data-ttu-id="e1fd0-204">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-204">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="e1fd0-205">Gesto de dedo liberado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-205">A finger released gesture.</span></span>

<span data-ttu-id="e1fd0-206">**Microsoft. PerceptionSimulation. SimulatedGesture. Home**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-206">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="e1fd0-207">El gesto Home/System.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-207">The home/system gesture.</span></span>

<span data-ttu-id="e1fd0-208">**Microsoft. PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-208">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="e1fd0-209">El gesto máximo válido.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-209">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="e1fd0-210">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="e1fd0-210">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="e1fd0-211">Los posibles estados de un controlador simulado 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-211">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="e1fd0-212">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. OFF**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-212">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="e1fd0-213">El controlador 6-DOF está desactivado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-213">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="e1fd0-214">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. Active**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-214">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="e1fd0-215">El controlador 6-DOF está activado y controlado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-215">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="e1fd0-216">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-216">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="e1fd0-217">El controlador 6-DOF está activado, pero no se puede realizar su seguimiento.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-217">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="e1fd0-218">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="e1fd0-218">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="e1fd0-219">Los botones admitidos en un controlador simulado 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-219">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="e1fd0-220">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-220">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="e1fd0-221">Un valor de centinela que se usa para indicar que no hay botones.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-221">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="e1fd0-222">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-222">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="e1fd0-223">Se presiona el botón Inicio.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-223">The Home button is pressed.</span></span>

<span data-ttu-id="e1fd0-224">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Menu**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-224">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="e1fd0-225">Se presiona el botón de menú.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-225">The Menu button is pressed.</span></span>

<span data-ttu-id="e1fd0-226">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. control**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-226">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="e1fd0-227">Se presiona el botón de control.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-227">The Grip button is pressed.</span></span>

<span data-ttu-id="e1fd0-228">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-228">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="e1fd0-229">El TouchPad está presionado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-229">The TouchPad is pressed.</span></span>

<span data-ttu-id="e1fd0-230">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-230">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="e1fd0-231">Se presiona el botón seleccionar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-231">The Select button is pressed.</span></span>

<span data-ttu-id="e1fd0-232">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-232">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="e1fd0-233">El TouchPad se toca.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-233">The TouchPad is touched.</span></span>

<span data-ttu-id="e1fd0-234">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Stick**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-234">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="e1fd0-235">Se presiona el stick.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-235">The Thumbstick is pressed.</span></span>

<span data-ttu-id="e1fd0-236">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-236">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="e1fd0-237">El botón válido máximo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-237">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="e1fd0-238">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="e1fd0-238">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="e1fd0-239">El estado de calibrado de los ojos simulados</span><span class="sxs-lookup"><span data-stu-id="e1fd0-239">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="e1fd0-240">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. no disponible**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-240">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="e1fd0-241">La calibración de ojos no está disponible.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-241">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="e1fd0-242">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-242">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="e1fd0-243">Los ojos se han calibrado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-243">The eyes have been calibrated.</span></span>  <span data-ttu-id="e1fd0-244">Este es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-244">This is the default value.</span></span>

<span data-ttu-id="e1fd0-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configusamos**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="e1fd0-246">Los ojos se están calibrando.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-246">The eyes are being calibrated.</span></span>

<span data-ttu-id="e1fd0-247">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-247">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="e1fd0-248">Los ojos deben calibrarse.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-248">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="e1fd0-249">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="e1fd0-249">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="e1fd0-250">La precisión del seguimiento de una Unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-250">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="e1fd0-251">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. no disponible**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-251">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="e1fd0-252">No se realiza el seguimiento de la Unión.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-252">The joint isn't tracked.</span></span>

<span data-ttu-id="e1fd0-253">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. aproximado**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-253">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="e1fd0-254">Se deduce la posición de la Unión.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-254">The joint position is inferred.</span></span>

<span data-ttu-id="e1fd0-255">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. visible**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-255">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="e1fd0-256">Se realiza un seguimiento completo de la Unión.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-256">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="e1fd0-257">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="e1fd0-257">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="e1fd0-258">La precisión del seguimiento de una Unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-258">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="e1fd0-259">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-259">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="e1fd0-260">Las uniones de dedos de la mano se configuran para reflejar una pose cerrada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-260">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="e1fd0-261">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-261">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="e1fd0-262">Las uniones de dedos de la mano se configuran para reflejar una pose abierta.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-262">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="e1fd0-263">**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-263">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="e1fd0-264">Las uniones de dedos de la mano se configuran para reflejar una postura señaladora.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-264">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="e1fd0-265">**Microsoft. PerceptionSimulation. SimulatedHandPose. Pinch**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-265">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="e1fd0-266">Las uniones de dedos de la mano se configuran para reflejar una pose de pinch.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-266">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="e1fd0-267">**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-267">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="e1fd0-268">Valor máximo válido para SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-268">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="e1fd0-269">Microsoft. PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="e1fd0-269">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="e1fd0-270">Describe el estado de una reproducción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-270">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="e1fd0-271">**Microsoft. PerceptionSimulation. PlaybackState. Stopped**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-271">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="e1fd0-272">La grabación está actualmente detenida y lista para su reproducción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-272">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="e1fd0-273">**Microsoft. PerceptionSimulation. PlaybackState. Playing**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-273">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="e1fd0-274">La grabación se está reproduciendo actualmente.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-274">The recording is currently playing.</span></span>

<span data-ttu-id="e1fd0-275">**Microsoft. PerceptionSimulation. PlaybackState. pausado**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-275">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="e1fd0-276">La grabación está en pausa actualmente.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-276">The recording is currently paused.</span></span>

<span data-ttu-id="e1fd0-277">**Microsoft. PerceptionSimulation. PlaybackState. end**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-277">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="e1fd0-278">La grabación ha alcanzado el final.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-278">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="e1fd0-279">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="e1fd0-279">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="e1fd0-280">Describe un vector de tres componentes, que puede describir un punto o un vector en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-280">Describes a three components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="e1fd0-281">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-281">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="e1fd0-282">Componente X del vector.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-282">The X component of the vector.</span></span>

<span data-ttu-id="e1fd0-283">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-283">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="e1fd0-284">Componente Y del vector.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-284">The Y component of the vector.</span></span>

<span data-ttu-id="e1fd0-285">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-285">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="e1fd0-286">Componente Z del vector.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-286">The Z component of the vector.</span></span>

<span data-ttu-id="e1fd0-287">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-287">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="e1fd0-288">Construya un nuevo Vector3.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-288">Construct a new Vector3.</span></span>

<span data-ttu-id="e1fd0-289">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-289">Parameters</span></span>
* <span data-ttu-id="e1fd0-290">x: el componente x del vector.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-290">x - The x component of the vector.</span></span>
* <span data-ttu-id="e1fd0-291">y: el componente y del vector.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-291">y - The y component of the vector.</span></span>
* <span data-ttu-id="e1fd0-292">z: el componente z del vector.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-292">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="e1fd0-293">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="e1fd0-293">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="e1fd0-294">Describe un giro de tres componentes.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-294">Describes a three components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="e1fd0-295">**Microsoft. PerceptionSimulation. Rotation3. Brea**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-295">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="e1fd0-296">El componente de tono de la rotación, en torno al eje X.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-296">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="e1fd0-297">**Microsoft. PerceptionSimulation. Rotation3. guiñada**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-297">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="e1fd0-298">Componente de guiñada de la rotación, justo alrededor del eje Y.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-298">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="e1fd0-299">**Microsoft. PerceptionSimulation. Rotation3. roll**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-299">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="e1fd0-300">Componente de rollo de la rotación, justo alrededor del eje Z.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-300">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="e1fd0-301">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-301">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="e1fd0-302">Construya un nuevo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-302">Construct a new Rotation3.</span></span>

<span data-ttu-id="e1fd0-303">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-303">Parameters</span></span>
* <span data-ttu-id="e1fd0-304">paso: el componente de paso de la rotación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-304">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="e1fd0-305">guiñada: el componente de guiñada de la rotación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-305">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="e1fd0-306">rollo: componente de rollo de la rotación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-306">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="e1fd0-307">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="e1fd0-307">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="e1fd0-308">Describe la configuración de una Unión en una mano simulada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-308">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="e1fd0-309">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-309">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="e1fd0-310">La posición de la Unión.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-310">The position of the joint.</span></span>

<span data-ttu-id="e1fd0-311">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-311">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="e1fd0-312">Rotación de la Unión.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-312">The rotation of the joint.</span></span>

<span data-ttu-id="e1fd0-313">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-313">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="e1fd0-314">La precisión del seguimiento de la Unión.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-314">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="e1fd0-315">Microsoft. PerceptionSimulation. frustum</span><span class="sxs-lookup"><span data-stu-id="e1fd0-315">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="e1fd0-316">Describe un frustum de vista, tal y como lo usa normalmente una cámara.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-316">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="e1fd0-317">**Microsoft. PerceptionSimulation. frustum. Near**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-317">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="e1fd0-318">Distancia mínima contenida en el frustum.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-318">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="e1fd0-319">**Microsoft. PerceptionSimulation. frustum. Far**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-319">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="e1fd0-320">La distancia máxima contenida en el frustum.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-320">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="e1fd0-321">**Microsoft. PerceptionSimulation. frustum. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-321">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="e1fd0-322">Campo horizontal de la vista del frustum, en radianes (menor que PI).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-322">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="e1fd0-323">**Microsoft. PerceptionSimulation. frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-323">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="e1fd0-324">La proporción del campo horizontal de la vista en el campo vertical de la vista.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-324">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="e1fd0-325">Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="e1fd0-325">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="e1fd0-326">Describe la configuración de la pantalla del casco simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-326">Describes the configuration of the simulated headset's display.</span></span>

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

<span data-ttu-id="e1fd0-327">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-327">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="e1fd0-328">La transformación desde el centro de la cabeza hacia la izquierda para fines de representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-328">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="e1fd0-329">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-329">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="e1fd0-330">Rotación del ojo izquierdo de la representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-330">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="e1fd0-331">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-331">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="e1fd0-332">La transformación desde el centro del cabezal hasta el ojo adecuado para fines de representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-332">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="e1fd0-333">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-333">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="e1fd0-334">La rotación del ojo adecuado para fines de representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-334">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="e1fd0-335">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. IPD**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-335">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="e1fd0-336">El valor de IPD indicado por el sistema para la representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-336">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="e1fd0-337">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-337">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="e1fd0-338">El hecho de que los valores proporcionados para las transformaciones de ojo izquierdo y derecho se consideren válidos y se apliquen al sistema en ejecución.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-338">Whether the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="e1fd0-339">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-339">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="e1fd0-340">Si el valor proporcionado para IPD se debe considerar válido y aplicar al sistema en ejecución.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-340">Whether the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="e1fd0-341">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e1fd0-341">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="e1fd0-342">Raíz para generar los paquetes usados para controlar un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-342">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="e1fd0-343">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-343">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="e1fd0-344">Recupere el objeto de dispositivo simulado que interpreta el usuario simulado y el mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-344">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="e1fd0-345">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-345">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="e1fd0-346">Recupera el objeto que controla el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-346">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="e1fd0-347">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-347">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="e1fd0-348">Restablece el estado predeterminado de la simulación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-348">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="e1fd0-349">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="e1fd0-349">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="e1fd0-350">Interfaz que describe el dispositivo, que interpreta el mundo simulado y el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-350">Interface describing the device, which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="e1fd0-351">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-351">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="e1fd0-352">Recupere el rastreador principal del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-352">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="e1fd0-353">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-353">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="e1fd0-354">Recupere el seguimiento de manos del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-354">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="e1fd0-355">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-355">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="e1fd0-356">Establezca las propiedades del dispositivo simulado para que coincida con el tipo de dispositivo proporcionado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-356">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="e1fd0-357">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-357">Parameters</span></span>
* <span data-ttu-id="e1fd0-358">tipo: el nuevo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="e1fd0-358">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="e1fd0-359">Microsoft. PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-359">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="e1fd0-360">Las propiedades adicionales están disponibles al convertir ISimulatedDevice en ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-360">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="e1fd0-361">**Microsoft. PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-361">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="e1fd0-362">Recupera o establece si el usuario simulado está usando activamente el casco.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-362">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="e1fd0-363">**Microsoft. PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-363">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="e1fd0-364">Recupera o establece las propiedades de la pantalla simulada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-364">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="e1fd0-365">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="e1fd0-365">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="e1fd0-366">Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento del encabezado del usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-366">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="e1fd0-367">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-367">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="e1fd0-368">Recupera y establece el modo de seguimiento de encabezado actual.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-368">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="e1fd0-369">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="e1fd0-369">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="e1fd0-370">Interfaz que describe la parte del dispositivo simulado que hace un seguimiento de las manos del usuario simulado</span><span class="sxs-lookup"><span data-stu-id="e1fd0-370">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="e1fd0-371">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-371">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="e1fd0-372">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-372">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="e1fd0-373">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-373">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="e1fd0-374">Recupera y establece la posición del seguimiento de mano simulado, en relación con el centro del encabezado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-374">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="e1fd0-375">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Brea**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-375">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="e1fd0-376">Recupere y establezca el tono hacia abajo del seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-376">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="e1fd0-377">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-377">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="e1fd0-378">Recupera y establece si se omite el frustum del seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-378">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="e1fd0-379">Cuando se omite, ambas manecillas siempre están visibles.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-379">When ignored, both hands are always visible.</span></span> <span data-ttu-id="e1fd0-380">Cuando no se omite (el valor predeterminado), las manecillas solo están visibles cuando se encuentran dentro del frustum del seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-380">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="e1fd0-381">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-381">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="e1fd0-382">Recupere y establezca las propiedades de frustum utilizadas para determinar si las manecillas están visibles para el seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-382">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="e1fd0-383">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="e1fd0-383">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="e1fd0-384">Interfaz de nivel superior para controlar el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-384">Top-level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="e1fd0-385">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-385">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="e1fd0-386">Recuperar y establecer la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-386">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="e1fd0-387">La posición corresponde a un punto en el centro de los pies del hombre.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-387">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="e1fd0-388">**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-388">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="e1fd0-389">Recupere y establezca la dirección de las caras humanas simuladas del mundo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-389">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="e1fd0-390">0 radianes se orientan hacia abajo en el eje Z negativo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-390">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="e1fd0-391">Los radianes positivos giran en el sentido de las agujas del reloj sobre el eje Y.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-391">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="e1fd0-392">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-392">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="e1fd0-393">Recupere y establezca el alto del hombre simulado, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-393">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="e1fd0-394">**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-394">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="e1fd0-395">Recupere el lado izquierdo del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-395">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="e1fd0-396">**Microsoft. PerceptionSimulation. ISimulatedHuman. derecho**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-396">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="e1fd0-397">Recupere la mano derecha del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-397">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="e1fd0-398">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-398">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="e1fd0-399">Recupera el encabezado del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-399">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="e1fd0-400">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-400">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="e1fd0-401">Mover el humano simulado con respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-401">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="e1fd0-402">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-402">Parameters</span></span>
* <span data-ttu-id="e1fd0-403">Translation: la traducción que se va a mover, relativa a la posición actual.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-403">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="e1fd0-404">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-404">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="e1fd0-405">Girar el hombre simulado con respecto a su dirección actual, en el sentido de las agujas del reloj sobre el eje Y</span><span class="sxs-lookup"><span data-stu-id="e1fd0-405">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="e1fd0-406">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-406">Parameters</span></span>
* <span data-ttu-id="e1fd0-407">radianes: la cantidad que se va a girar alrededor del eje Y.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-407">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="e1fd0-408">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-408">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="e1fd0-409">Las propiedades adicionales están disponibles al convertir ISimulatedHuman en ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-409">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="e1fd0-410">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-410">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="e1fd0-411">Recupere el controlador de 6-DOF izquierdo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-411">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="e1fd0-412">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-412">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="e1fd0-413">Recupere el controlador de 6-DOF adecuado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-413">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="e1fd0-414">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="e1fd0-414">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="e1fd0-415">Interfaz que describe una mano del usuario simulado</span><span class="sxs-lookup"><span data-stu-id="e1fd0-415">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="e1fd0-416">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-416">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="e1fd0-417">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-417">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="e1fd0-418">**Microsoft. PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-418">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="e1fd0-419">Recupera y establece la posición de la mano simulada en relación con el hombre, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-419">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="e1fd0-420">**Microsoft. PerceptionSimulation. ISimulatedHand. activado**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-420">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="e1fd0-421">Recupera y establece si la mano está activada actualmente.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-421">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="e1fd0-422">**Microsoft. PerceptionSimulation. ISimulatedHand. visible**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-422">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="e1fd0-423">Recupera si la mano es visible actualmente para SimulatedDevice (es decir, si se encuentra en una posición que HandTracker).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-423">Retrieve whether the hand is currently visible to the SimulatedDevice (that is, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="e1fd0-424">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-424">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="e1fd0-425">Mueva la mano para que sea visible para el SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-425">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="e1fd0-426">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-426">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="e1fd0-427">Mover la posición de la mano simulada en relación con su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-427">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="e1fd0-428">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-428">Parameters</span></span>
* <span data-ttu-id="e1fd0-429">Translation: la cantidad que se va a trasladar a la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-429">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="e1fd0-430">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-430">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="e1fd0-431">Realizar un gesto mediante la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-431">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="e1fd0-432">Solo lo detectará el sistema si está habilitada la mano.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-432">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="e1fd0-433">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-433">Parameters</span></span>
* <span data-ttu-id="e1fd0-434">gesto: el gesto que se va a realizar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-434">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="e1fd0-435">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-435">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="e1fd0-436">Las propiedades adicionales están disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-436">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="e1fd0-437">**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-437">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="e1fd0-438">Recupera o establece la rotación de la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-438">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="e1fd0-439">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-439">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="e1fd0-440">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="e1fd0-440">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="e1fd0-441">Hay propiedades adicionales disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="e1fd0-441">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="e1fd0-442">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-442">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="e1fd0-443">Obtiene la configuración conjunta de la Unión especificada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-443">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="e1fd0-444">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-444">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="e1fd0-445">Establezca la configuración conjunta de la Unión especificada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-445">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="e1fd0-446">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-446">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="e1fd0-447">Establezca la mano en una pose conocida con una marca opcional que se va a animar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-447">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="e1fd0-448">Nota: la animación no provocará que las uniones reflejen inmediatamente sus configuraciones de conjuntos finales.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-448">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="e1fd0-449">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="e1fd0-449">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="e1fd0-450">Interfaz que describe el encabezado del usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-450">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="e1fd0-451">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-451">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="e1fd0-452">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-452">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="e1fd0-453">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-453">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="e1fd0-454">Recupera el giro del encabezado simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-454">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="e1fd0-455">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-455">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e1fd0-456">**Microsoft. PerceptionSimulation. ISimulatedHead. diameter**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-456">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="e1fd0-457">Recuperar el diámetro del cabezal simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-457">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="e1fd0-458">Este valor se usa para determinar el centro del encabezado (punto de giro).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-458">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="e1fd0-459">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-459">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="e1fd0-460">Gira el encabezado simulado con respecto a su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-460">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="e1fd0-461">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-461">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e1fd0-462">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-462">Parameters</span></span>
* <span data-ttu-id="e1fd0-463">rotación: la cantidad que se va a girar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-463">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="e1fd0-464">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-464">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="e1fd0-465">Hay propiedades adicionales disponibles mediante la conversión de un ISimulatedHead a ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-465">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="e1fd0-466">**Microsoft. PerceptionSimulation. ISimulatedHead2. Eyes**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-466">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="e1fd0-467">Recupere los ojos del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-467">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="e1fd0-468">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="e1fd0-468">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="e1fd0-469">Interfaz que describe un controlador de 6 DOF asociado con el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-469">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="e1fd0-470">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="e1fd0-471">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-471">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="e1fd0-472">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-472">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="e1fd0-473">Recupera o establece el estado actual del controlador.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-473">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="e1fd0-474">El estado del controlador debe establecerse en un valor distinto de OFF antes de que las llamadas para moverse, girar o presionar botones se realicen correctamente.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-474">The controller status must be set to a value other than Off before any calls to move, rotate, or press buttons will succeed.</span></span>

<span data-ttu-id="e1fd0-475">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="e1fd0-476">Recupera o establece la posición del controlador simulado con respecto al hombre, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-476">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="e1fd0-477">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-477">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="e1fd0-478">Recupera o establece la orientación del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-478">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="e1fd0-479">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-479">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="e1fd0-480">Mover la posición del controlador simulado con respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-480">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="e1fd0-481">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-481">Parameters</span></span>
* <span data-ttu-id="e1fd0-482">Translation: la cantidad para traducir el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-482">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="e1fd0-483">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-483">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="e1fd0-484">Presione un botón en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-484">Press a button on the simulated controller.</span></span>  <span data-ttu-id="e1fd0-485">Solo lo detectará el sistema si el controlador está habilitado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-485">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="e1fd0-486">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-486">Parameters</span></span>
* <span data-ttu-id="e1fd0-487">Button: botón que se va a presionar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-487">button - The button to press.</span></span>

<span data-ttu-id="e1fd0-488">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-488">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="e1fd0-489">Suelte un botón en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-489">Release a button on the simulated controller.</span></span>  <span data-ttu-id="e1fd0-490">Solo lo detectará el sistema si el controlador está habilitado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-490">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="e1fd0-491">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-491">Parameters</span></span>
* <span data-ttu-id="e1fd0-492">Button: el botón que se va a liberar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-492">button - The button to release.</span></span>

<span data-ttu-id="e1fd0-493">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out Float, out float)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-493">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="e1fd0-494">Obtiene la posición de un dedo simulado en el Touchpad del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-494">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="e1fd0-495">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-495">Parameters</span></span>
* <span data-ttu-id="e1fd0-496">x: la posición horizontal del dedo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-496">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="e1fd0-497">y: posición vertical del dedo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-497">y - The vertical position of the finger.</span></span>

<span data-ttu-id="e1fd0-498">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-498">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="e1fd0-499">Establece la posición de un dedo simulado en el Touchpad del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-499">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="e1fd0-500">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-500">Parameters</span></span>
* <span data-ttu-id="e1fd0-501">x: la posición horizontal del dedo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-501">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="e1fd0-502">y: posición vertical del dedo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-502">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="e1fd0-503">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-503">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="e1fd0-504">Los métodos y propiedades adicionales están disponibles mediante la conversión de un ISimulatedSixDofController a ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="e1fd0-504">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="e1fd0-505">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out Float, out float)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-505">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="e1fd0-506">Obtiene la posición del stick analógico simulado en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-506">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="e1fd0-507">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-507">Parameters</span></span>
* <span data-ttu-id="e1fd0-508">x: la posición horizontal del Stick.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-508">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="e1fd0-509">y: la posición vertical del Stick.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-509">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="e1fd0-510">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-510">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="e1fd0-511">Establece la posición del stick analógico simulado en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-511">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="e1fd0-512">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-512">Parameters</span></span>
* <span data-ttu-id="e1fd0-513">x: la posición horizontal del Stick.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-513">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="e1fd0-514">y: la posición vertical del Stick.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-514">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="e1fd0-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="e1fd0-516">Recupera o establece el nivel de batería del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-516">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="e1fd0-517">El valor debe ser mayor que 0,0 y menor o igual que 100,0.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-517">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="e1fd0-518">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="e1fd0-518">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="e1fd0-519">Interfaz que describe los ojos del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-519">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="e1fd0-520">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-520">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="e1fd0-521">Recupera el giro de los ojos simulados.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-521">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="e1fd0-522">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-522">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e1fd0-523">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-523">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="e1fd0-524">Gira los ojos simulados en relación con su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-524">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="e1fd0-525">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-525">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e1fd0-526">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-526">Parameters</span></span>
* <span data-ttu-id="e1fd0-527">rotación: la cantidad que se va a girar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-527">rotation - The amount to rotate.</span></span>

<span data-ttu-id="e1fd0-528">**Microsoft. PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-528">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="e1fd0-529">Recupera o establece el estado de calibrado de los ojos simulados.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-529">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="e1fd0-530">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-530">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="e1fd0-531">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-531">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="e1fd0-532">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="e1fd0-532">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="e1fd0-533">Interfaz para interactuar con un solo registro cargado para la reproducción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-533">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="e1fd0-534">**Microsoft. PerceptionSimulation. ISimulationRecording. Datatypes**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-534">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="e1fd0-535">Recupera la lista de tipos de datos de la grabación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-535">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="e1fd0-536">**Microsoft. PerceptionSimulation. ISimulationRecording. State**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-536">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="e1fd0-537">Recupera el estado actual de la grabación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-537">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="e1fd0-538">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-538">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="e1fd0-539">Inicie la reproducción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-539">Start the playback.</span></span> <span data-ttu-id="e1fd0-540">Si se pausa la grabación, la reproducción se reanudará desde la ubicación en pausa; Si se detiene, la reproducción se iniciará al principio.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-540">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="e1fd0-541">Si ya se está reproduciendo, se omitirá esta llamada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-541">If already playing, this call is ignored.</span></span>

<span data-ttu-id="e1fd0-542">**Microsoft. PerceptionSimulation. ISimulationRecording. PAUSE**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-542">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="e1fd0-543">Pausa la reproducción en su ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-543">Pauses the playback at its current location.</span></span> <span data-ttu-id="e1fd0-544">Si se detiene la grabación, se omite la llamada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-544">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="e1fd0-545">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-545">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="e1fd0-546">Busca la grabación en el tiempo especificado (en intervalos de 100-nanosegundos desde el principio) y se pausa en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-546">Seeks the recording to the specified time (in 100-nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="e1fd0-547">Si el tiempo está más allá del final de la grabación, se pausa en el último fotograma.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-547">If the time is beyond the end of the recording, it's paused at the last frame.</span></span>

<span data-ttu-id="e1fd0-548">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-548">Parameters</span></span>
* <span data-ttu-id="e1fd0-549">TICs: la hora a la que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-549">ticks - The time to which to seek.</span></span>

<span data-ttu-id="e1fd0-550">**Microsoft. PerceptionSimulation. ISimulationRecording. STOP**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-550">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="e1fd0-551">Detiene la reproducción y restablece la posición al principio.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-551">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="e1fd0-552">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="e1fd0-552">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="e1fd0-553">Interfaz para recibir cambios de estado durante la reproducción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-553">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="e1fd0-554">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-554">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="e1fd0-555">Se llama cuando el estado de reproducción de un ISimulationRecording ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-555">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="e1fd0-556">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-556">Parameters</span></span>
* <span data-ttu-id="e1fd0-557">newState: el nuevo estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-557">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="e1fd0-558">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e1fd0-558">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="e1fd0-559">Objeto raíz para crear objetos de simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-559">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="e1fd0-560">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-560">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="e1fd0-561">Cree en el objeto para generar paquetes simulados y entregarlos al receptor proporcionado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-561">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="e1fd0-562">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-562">Parameters</span></span>
* <span data-ttu-id="e1fd0-563">receptor: el receptor que recibirá todos los paquetes generados.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-563">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="e1fd0-564">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e1fd0-564">Return value</span></span>

<span data-ttu-id="e1fd0-565">Administrador creado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-565">The created Manager.</span></span>

<span data-ttu-id="e1fd0-566">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-566">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="e1fd0-567">Cree un receptor, que almacena todos los paquetes recibidos en un archivo en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-567">Create a sink, which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="e1fd0-568">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-568">Parameters</span></span>
* <span data-ttu-id="e1fd0-569">Ruta de acceso: la ruta de acceso del archivo que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-569">path - The path of the file to create.</span></span>

<span data-ttu-id="e1fd0-570">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e1fd0-570">Return value</span></span>

<span data-ttu-id="e1fd0-571">Receptor creado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-571">The created sink.</span></span>

<span data-ttu-id="e1fd0-572">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-572">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="e1fd0-573">Cargar una grabación del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-573">Load a recording from the specified file.</span></span>

<span data-ttu-id="e1fd0-574">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-574">Parameters</span></span>
* <span data-ttu-id="e1fd0-575">Ruta de acceso: la ruta de acceso del archivo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-575">path - The path of the file to load.</span></span>
* <span data-ttu-id="e1fd0-576">Factory: un generador que utiliza la grabación para crear un ISimulationStreamSink cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-576">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="e1fd0-577">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e1fd0-577">Return value</span></span>

<span data-ttu-id="e1fd0-578">Grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-578">The loaded recording.</span></span>

<span data-ttu-id="e1fd0-579">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-579">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="e1fd0-580">Cargar una grabación del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-580">Load a recording from the specified file.</span></span>

<span data-ttu-id="e1fd0-581">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-581">Parameters</span></span>
* <span data-ttu-id="e1fd0-582">Ruta de acceso: la ruta de acceso del archivo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-582">path - The path of the file to load.</span></span>
* <span data-ttu-id="e1fd0-583">Factory: un generador que utiliza la grabación para crear un ISimulationStreamSink cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-583">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="e1fd0-584">callback: una devolución de llamada, que recibe actualizaciones que retrasan el estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-584">callback - A callback, which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="e1fd0-585">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e1fd0-585">Return value</span></span>

<span data-ttu-id="e1fd0-586">Grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-586">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="e1fd0-587">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="e1fd0-587">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="e1fd0-588">Describe los diferentes tipos de datos de secuencia.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-588">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="e1fd0-589">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-589">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="e1fd0-590">Un valor de centinela que se usa para indicar que no hay tipos de datos de flujo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-590">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="e1fd0-591">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-591">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="e1fd0-592">Flujo de datos para la posición y orientación del encabezado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-592">Stream of data for the position and orientation of the head.</span></span>

<span data-ttu-id="e1fd0-593">**Microsoft. PerceptionSimulation. StreamDataTypes. handles**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-593">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="e1fd0-594">Flujo de datos para la posición y los gestos de las manos.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-594">Stream of data for the position and gestures of hands.</span></span>

<span data-ttu-id="e1fd0-595">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-595">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="e1fd0-596">Flujo de datos para la asignación espacial del entorno.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-596">Stream of data for spatial mapping of the environment.</span></span>

<span data-ttu-id="e1fd0-597">**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-597">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="e1fd0-598">Flujo de datos para la calibración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-598">Stream of data for calibration of the device.</span></span> <span data-ttu-id="e1fd0-599">Los paquetes de calibración solo los acepta un sistema en modo remoto.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-599">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="e1fd0-600">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-600">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="e1fd0-601">Flujo de datos para el entorno del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-601">Stream of data for the environment of the device.</span></span>

<span data-ttu-id="e1fd0-602">**Microsoft. PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-602">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="e1fd0-603">Flujo de datos para controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-603">Stream of data for motion controllers.</span></span>

<span data-ttu-id="e1fd0-604">**Microsoft. PerceptionSimulation. StreamDataTypes. Eyes**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-604">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="e1fd0-605">Flujo de datos con los ojos del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-605">Stream of data with the eyes of the simulated human.</span></span>

<span data-ttu-id="e1fd0-606">**Microsoft. PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-606">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="e1fd0-607">Flujo de datos con la configuración de pantalla del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-607">Stream of data with the display configuration of the device.</span></span>

<span data-ttu-id="e1fd0-608">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-608">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="e1fd0-609">Un valor de centinela que se usa para indicar todos los tipos de datos grabados.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-609">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="e1fd0-610">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="e1fd0-610">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="e1fd0-611">Objeto que recibe paquetes de datos de una secuencia de simulación.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-611">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="e1fd0-612">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint longitud, Byte [], paquete)**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-612">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="e1fd0-613">Recibe un único paquete, que está escrito internamente y con control de versiones.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-613">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="e1fd0-614">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e1fd0-614">Parameters</span></span>
* <span data-ttu-id="e1fd0-615">longitud: la longitud del paquete.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-615">length - The length of the packet.</span></span>
* <span data-ttu-id="e1fd0-616">paquete: los datos del paquete.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-616">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="e1fd0-617">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="e1fd0-617">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="e1fd0-618">Objeto que crea ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-618">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="e1fd0-619">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="e1fd0-619">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="e1fd0-620">Crea una única instancia de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-620">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="e1fd0-621">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e1fd0-621">Return value</span></span>

<span data-ttu-id="e1fd0-622">Receptor creado.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-622">The created sink.</span></span>
