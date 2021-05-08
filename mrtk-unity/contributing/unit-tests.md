---
title: UnitTests
description: UnitTests para comprobar la fiabilidad de MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, UnitTest,
ms.openlocfilehash: 51a485ff258ceafb8841ff1b86e715b1623f3255
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489245"
---
# <a name="writing-and-running-tests-in-mrtk"></a>Escritura y ejecución de pruebas en MRTK

Para asegurarse de que MRTK es confiable, MRTK tiene un conjunto de pruebas para asegurarse de que los cambios en el código no revierta el comportamiento existente. Tener una buena cobertura de prueba en un código base grande como MRTK es fundamental para la estabilidad y tener confianza al realizar cambios.

MRTK usa el [Test Runner Unity,](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) que usa una integración de Unity de [NUnit.](https://nunit.org/) Esta guía proporcionará un punto de partida sobre cómo agregar pruebas a MRTK. No explicará los Test Runner [Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) y [NUnit](https://nunit.org/) que se pueden buscar en los vínculos proporcionados.

Antes de enviar una solicitud de extracción, asegúrese de:

1. Ejecute las pruebas localmente para que los cambios no vuelvan al comportamiento existente (no se permitirá completar las pruebas de rendimiento si se producirá un error en las pruebas).

1. Si corrige un error, escriba una prueba para probar la corrección y asegúrese de que las modificaciones futuras del código no la vuelvan a interrumpir.

1. Si escribe una característica, escriba nuevas pruebas para evitar que los próximos cambios en el código rompa esta característica.

Actualmente, las pruebas de modo de reproducción están pensadas para ejecutarse en Unity 2018.4 y pueden producirse errores en otras versiones de Unity.

## <a name="running-tests"></a>Ejecución de las pruebas

### <a name="unity-editor"></a>Editor de Unity

La [ventana Test Runner Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) se puede encontrar en Window General Test Runner (Ventana general) y mostrará todas las pruebas de reproducción y modo de edición de  >    >   MRTK disponibles.

### <a name="command-line"></a>Línea de comandos

Las pruebas también se pueden ejecutar mediante un script [de PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) ubicado en `Scripts\test\run_playmode_tests.ps1` . Esto ejecutará las pruebas de playmode exactamente como se ejecutan en github/CI (consulte a continuación) e imprimirá los resultados. Estos son algunos ejemplos de cómo ejecutar el script

Ejecute las pruebas en el proyecto ubicado en H:\mrtk.dev, con Unity 2018.4 (por ejemplo, Unity 2018.4.26f1).

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Ejecute las pruebas en el proyecto ubicado en H:\mrtk.dev, con Unity 2018.4, para generar resultados en C:\playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

También es posible ejecutar las pruebas de modo de reproducción varias veces a través del `run_repeat_tests.ps1` script. Se pueden usar todos `run_playmode_tests.ps1` los parámetros usados en .

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>Validación de solicitudes de extracción

La CI de MRTK compilará MRTK en todas las configuraciones y ejecutará todas las pruebas de modo de edición y reproducción. Ci se puede desencadenar mediante la publicación de un comentario en la pr. de GitHub `/azp run mrtk_pr` si el usuario tiene derechos suficientes. Las ejecuciones de CI se pueden ver en la pestaña "comprobaciones" de la pr.

Solo después de que todas las pruebas se han superado correctamente, la pr. se puede combinar en main.

### <a name="stress-tests--bulk-tests"></a>Pruebas de esfuerzo y pruebas masivas

A veces, las pruebas solo producirán errores ocasionalmente, lo que puede resultar frustrante de depurar.

Para que varias pruebas se ejecuten localmente, modifique los scripts de prueba según corresponda. El siguiente script de Python debe hacer que este escenario sea más cómodo.

El requisito previo para ejecutar el script de Python es tener [instalado Python 3.X.](https://www.python.org/downloads/)

Para una sola prueba que debe ejecutarse varias veces:

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

Ejecute lo siguiente desde una línea de comandos (se recomienda[PowerShell)](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core)

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

Copie y pegue la salida en el archivo de prueba. El siguiente script es para ejecutar varias pruebas en secuencia:

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

El nuevo archivo de prueba ahora debe contener

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

Abra el ejecutor de pruebas y observe las nuevas pruebas a las que ahora se puede llamar repetidamente.

## <a name="writing-tests"></a>Escritura de pruebas

Hay dos tipos de pruebas que se pueden agregar para el nuevo código.

* Pruebas de modo de reproducción
* Pruebas de modo de edición

### <a name="play-mode-tests"></a>Pruebas de modo de reproducción

Las pruebas de modo de reproducción de MRTK tienen la capacidad de probar cómo responde la nueva característica a diferentes orígenes de entrada, como manos u ojos.

Las nuevas pruebas de modo de reproducción pueden [heredar BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) o se puede usar el esqueleto siguiente.

Para crear una nueva prueba de modo de reproducción:

* Vaya a Assets > MRTK > Tests > PlayModeTests
* Haga clic con el botón derecho en Crear > pruebas > script de prueba de C#
* Reemplace la plantilla predeterminada por el esqueleto siguiente.

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a>Pruebas de modo de edición

Las pruebas de modo de edición se ejecutan en el modo de edición de Unity y se pueden agregar en la carpeta  >    >  **EditModeTests** de pruebas de MRTK en el repositorio de Mixed Reality Toolkit.
Para crear una nueva prueba, se puede usar la siguiente plantilla:

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a>Probar convenciones de nomenclatura

Por lo general, las pruebas se deben denominar en función de la clase que están probando o del escenario que están probando.
Por ejemplo, dada una clase que se va a probar:

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

Considere la posibilidad de asignar un nombre a la prueba.

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

Considere la posibilidad de colocar la prueba en una jerarquía de carpetas similar a su archivo que no es de prueba correspondiente.
Por ejemplo:

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

Esto es para asegurarse de que hay una manera clara de encontrar la clase de prueba correspondiente de cada clase, si existe dicha clase de prueba.

La colocación de pruebas basadas en escenarios está menos definida: si la prueba realiza el sistema de entrada general, por ejemplo, considere la posibilidad de colocarlo en una carpeta "InputSystem" en el modo de edición correspondiente o en la carpeta de pruebas del modo de reproducción correspondiente.

### <a name="test-script-icons"></a>Iconos de script de prueba

Al agregar una nueva prueba, modifique el script para que tenga el icono de MRTK correcto. Hay una herramienta MRTK sencilla para hacerlo:

1. Vaya al elemento de menú Mixed Reality Toolkit.
1. Haga clic en Utilidades, luego en Actualizar y, después, en Iconos.
1. Haga clic en Pruebas y el actualizador se ejecutará automáticamente, actualizando los scripts de prueba que faltan en sus iconos.

### <a name="mrtk-utility-methods"></a>Métodos de la utilidad MRTK

En esta sección se muestran algunos de los métodos o fragmentos de código usados habitualmente al escribir pruebas para MRTK.

Hay dos clases de utilidad que ayudan a configurar MRTK y probar las interacciones con componentes en MRTK

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities proporciona los métodos siguientes para configurar la escena de MRTK y GameObjects:

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

Consulte los documentos de API de y para obtener más métodos de estas clases utiles, ya que se extienden de forma periódica mientras se agregan nuevas pruebas [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) a MRTK.