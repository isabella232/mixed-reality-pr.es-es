---
title: Pruebas unitarias
description: Pruebas unitarias para comprobar la confiabilidad de MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, UnitTest,
ms.openlocfilehash: a915b005a69de1864a5674bbb0363f18d1c74b19
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121353"
---
# <a name="writing-and-running-tests-in-mrtk"></a><span data-ttu-id="c6216-104">Escritura y ejecución de pruebas en MRTK</span><span class="sxs-lookup"><span data-stu-id="c6216-104">Writing and running tests in MRTK</span></span>

<span data-ttu-id="c6216-105">Para asegurarse de que MRTK es confiable, MRTK tiene un conjunto de pruebas para asegurarse de que los cambios en el código no revierta el comportamiento existente.</span><span class="sxs-lookup"><span data-stu-id="c6216-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="c6216-106">Tener una buena cobertura de prueba en un código base grande como MRTK es fundamental para la estabilidad y tener confianza al realizar cambios.</span><span class="sxs-lookup"><span data-stu-id="c6216-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="c6216-107">MRTK usa la [Test Runner Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) que usa una integración de Unity de [NUnit.](https://nunit.org/)</span><span class="sxs-lookup"><span data-stu-id="c6216-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="c6216-108">En esta guía se proporciona un punto de partida sobre cómo agregar pruebas a MRTK.</span><span class="sxs-lookup"><span data-stu-id="c6216-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="c6216-109">No explicará los vínculos [Test Runner Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) y [NUnit](https://nunit.org/) que se pueden buscar en los vínculos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="c6216-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="c6216-110">Antes de enviar una solicitud de extracción, asegúrese de:</span><span class="sxs-lookup"><span data-stu-id="c6216-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="c6216-111">Ejecute las pruebas localmente para que los cambios no vuelvan al comportamiento existente (no se permitirá completar las pruebas si se producirá un error en las pruebas).</span><span class="sxs-lookup"><span data-stu-id="c6216-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="c6216-112">Si corrige un error, escriba una prueba para probar la corrección y asegúrese de que las modificaciones futuras del código no vuelvan a interrumpirla.</span><span class="sxs-lookup"><span data-stu-id="c6216-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="c6216-113">Si escribe una característica, escriba nuevas pruebas para evitar que los próximos cambios en el código no supere esta característica.</span><span class="sxs-lookup"><span data-stu-id="c6216-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="c6216-114">Actualmente, las pruebas en modo de reproducción están pensadas para ejecutarse en Unity 2018.4 y pueden producir errores en otras versiones de Unity.</span><span class="sxs-lookup"><span data-stu-id="c6216-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="c6216-115">Ejecución de las pruebas</span><span class="sxs-lookup"><span data-stu-id="c6216-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="c6216-116">Editor de Unity</span><span class="sxs-lookup"><span data-stu-id="c6216-116">Unity editor</span></span>

<span data-ttu-id="c6216-117">La [página Test Runner Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) se puede encontrar en Window General Test Runner (Ventana general) y mostrará todas las pruebas disponibles de mrtk play and edit mode (Modo de edición y reproducción  >    >   de MRTK).</span><span class="sxs-lookup"><span data-stu-id="c6216-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="c6216-118">Línea de comandos</span><span class="sxs-lookup"><span data-stu-id="c6216-118">Command line</span></span>

<span data-ttu-id="c6216-119">Las pruebas también se pueden ejecutar mediante un script [de PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) ubicado en `Scripts\test\run_playmode_tests.ps1` .</span><span class="sxs-lookup"><span data-stu-id="c6216-119">Tests can also be run by a [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="c6216-120">Esto ejecutará las pruebas de playmode exactamente como se ejecutan en github/CI (consulte a continuación) e imprimirá los resultados.</span><span class="sxs-lookup"><span data-stu-id="c6216-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="c6216-121">Estos son algunos ejemplos de cómo ejecutar el script</span><span class="sxs-lookup"><span data-stu-id="c6216-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="c6216-122">Ejecute las pruebas en el proyecto ubicado en H:\mrtk.dev, con Unity 2018.4 (por ejemplo, Unity 2018.4.26f1)</span><span class="sxs-lookup"><span data-stu-id="c6216-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="c6216-123">Ejecute las pruebas en el proyecto ubicado en H:\mrtk.dev, con Unity 2018.4, los resultados de salida a C:\playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="c6216-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="c6216-124">También es posible ejecutar las pruebas de playmode varias veces a través del `run_repeat_tests.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="c6216-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="c6216-125">Se pueden usar todos `run_playmode_tests.ps1` los parámetros usados en .</span><span class="sxs-lookup"><span data-stu-id="c6216-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="c6216-126">Validación de solicitudes de extracción</span><span class="sxs-lookup"><span data-stu-id="c6216-126">Pull request validation</span></span>

<span data-ttu-id="c6216-127">La CI de MRTK compilará MRTK en todas las configuraciones y ejecutará todas las pruebas de modo de edición y reproducción.</span><span class="sxs-lookup"><span data-stu-id="c6216-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="c6216-128">Ci se puede desencadenar mediante la publicación de un comentario en la pr. de GitHub `/azp run mrtk_pr` si el usuario tiene derechos suficientes.</span><span class="sxs-lookup"><span data-stu-id="c6216-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="c6216-129">Las ejecuciones de CI se pueden ver en la pestaña "comprobaciones" de la pr.</span><span class="sxs-lookup"><span data-stu-id="c6216-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="c6216-130">Solo después de que todas las pruebas se han superado correctamente, la pr. se puede combinar en main.</span><span class="sxs-lookup"><span data-stu-id="c6216-130">Only after all of the tests have passed successfully can the PR be merged into main.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="c6216-131">Pruebas de esfuerzo y pruebas masivas</span><span class="sxs-lookup"><span data-stu-id="c6216-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="c6216-132">A veces, las pruebas solo producirán errores ocasionalmente, lo que puede resultar frustrante de depurar.</span><span class="sxs-lookup"><span data-stu-id="c6216-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="c6216-133">Para que varias pruebas se ejecuten localmente, modifique los scripts de prueba según corresponda.</span><span class="sxs-lookup"><span data-stu-id="c6216-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="c6216-134">El siguiente script de Python debe hacer que este escenario sea más cómodo.</span><span class="sxs-lookup"><span data-stu-id="c6216-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="c6216-135">El requisito previo para ejecutar el script de Python es tener [instalado Python 3.X.](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="c6216-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="c6216-136">Para una sola prueba que debe ejecutarse varias veces:</span><span class="sxs-lookup"><span data-stu-id="c6216-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="c6216-137">Ejecute lo siguiente desde una línea de comandos (se recomienda[PowerShell)](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core)</span><span class="sxs-lookup"><span data-stu-id="c6216-137">Run the following from a command line ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="c6216-138">Copie y pegue la salida en el archivo de prueba.</span><span class="sxs-lookup"><span data-stu-id="c6216-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="c6216-139">El siguiente script es para ejecutar varias pruebas en secuencia:</span><span class="sxs-lookup"><span data-stu-id="c6216-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="c6216-140">El nuevo archivo de prueba ahora debe contener</span><span class="sxs-lookup"><span data-stu-id="c6216-140">The new test file should now contain</span></span>

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

<span data-ttu-id="c6216-141">Abra el ejecutor de pruebas y observe las nuevas pruebas a las que ahora se puede llamar repetidamente.</span><span class="sxs-lookup"><span data-stu-id="c6216-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="c6216-142">Escritura de pruebas</span><span class="sxs-lookup"><span data-stu-id="c6216-142">Writing tests</span></span>

<span data-ttu-id="c6216-143">Hay dos tipos de pruebas que se pueden agregar para el nuevo código.</span><span class="sxs-lookup"><span data-stu-id="c6216-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="c6216-144">Pruebas de modo de reproducción</span><span class="sxs-lookup"><span data-stu-id="c6216-144">Play mode tests</span></span>
* <span data-ttu-id="c6216-145">Pruebas de modo de edición</span><span class="sxs-lookup"><span data-stu-id="c6216-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="c6216-146">Pruebas de modo de reproducción</span><span class="sxs-lookup"><span data-stu-id="c6216-146">Play mode tests</span></span>

<span data-ttu-id="c6216-147">Las pruebas de modo de reproducción de MRTK tienen la capacidad de probar cómo responde la nueva característica a diferentes orígenes de entrada, como manos u ojos.</span><span class="sxs-lookup"><span data-stu-id="c6216-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="c6216-148">Las nuevas pruebas de modo de reproducción pueden [heredar BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) o se puede usar el esqueleto siguiente.</span><span class="sxs-lookup"><span data-stu-id="c6216-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) or the skeleton below can be used.</span></span>

<span data-ttu-id="c6216-149">Para crear una nueva prueba de modo de reproducción:</span><span class="sxs-lookup"><span data-stu-id="c6216-149">To create a new play mode test:</span></span>

* <span data-ttu-id="c6216-150">Vaya a Assets > MRTK > Tests > PlayModeTests</span><span class="sxs-lookup"><span data-stu-id="c6216-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="c6216-151">Haga clic con el botón derecho en Crear > pruebas > script de prueba de C#</span><span class="sxs-lookup"><span data-stu-id="c6216-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="c6216-152">Reemplace la plantilla predeterminada por el esqueleto siguiente.</span><span class="sxs-lookup"><span data-stu-id="c6216-152">Replace the default template with the skeleton below</span></span>

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

### <a name="edit-mode-tests"></a><span data-ttu-id="c6216-153">Pruebas de modo de edición</span><span class="sxs-lookup"><span data-stu-id="c6216-153">Edit mode tests</span></span>

<span data-ttu-id="c6216-154">Las pruebas del modo de edición se ejecutan en el modo de edición de Unity y se pueden agregar en la carpeta  >    >  **EditModeTests** de MRTK Tests del repositorio Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="c6216-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="c6216-155">Para crear una nueva prueba, se puede usar la siguiente plantilla:</span><span class="sxs-lookup"><span data-stu-id="c6216-155">To create a new test the following template can be used:</span></span>

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

### <a name="test-naming-conventions"></a><span data-ttu-id="c6216-156">Prueba de convenciones de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="c6216-156">Test naming conventions</span></span>

<span data-ttu-id="c6216-157">Por lo general, las pruebas se deben denominar en función de la clase que están probando o del escenario que están probando.</span><span class="sxs-lookup"><span data-stu-id="c6216-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="c6216-158">Por ejemplo, dada una clase que se va a probar:</span><span class="sxs-lookup"><span data-stu-id="c6216-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="c6216-159">Considere la posibilidad de asignar un nombre a la prueba.</span><span class="sxs-lookup"><span data-stu-id="c6216-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="c6216-160">Considere la posibilidad de colocar la prueba en una jerarquía de carpetas similar a su archivo que no es de prueba correspondiente.</span><span class="sxs-lookup"><span data-stu-id="c6216-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="c6216-161">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c6216-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="c6216-162">Esto es para asegurarse de que hay una manera clara de buscar la clase de prueba correspondiente de cada clase, si existe dicha clase de prueba.</span><span class="sxs-lookup"><span data-stu-id="c6216-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="c6216-163">La colocación de pruebas basadas en escenarios está menos definida: si la prueba realiza el sistema de entrada general, por ejemplo, considere la posibilidad de colocarlo en una carpeta "InputSystem" en el modo de edición correspondiente o en la carpeta de pruebas del modo de reproducción correspondiente.</span><span class="sxs-lookup"><span data-stu-id="c6216-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="c6216-164">Iconos de script de prueba</span><span class="sxs-lookup"><span data-stu-id="c6216-164">Test script icons</span></span>

<span data-ttu-id="c6216-165">Al agregar una nueva prueba, modifique el script para que tenga el icono de MRTK correcto.</span><span class="sxs-lookup"><span data-stu-id="c6216-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="c6216-166">Hay una sencilla herramienta MRTK para hacerlo:</span><span class="sxs-lookup"><span data-stu-id="c6216-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="c6216-167">Vaya al elemento de menú Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="c6216-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="c6216-168">Haga clic en Utilidades, luego en Actualizar y, después, en Iconos.</span><span class="sxs-lookup"><span data-stu-id="c6216-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="c6216-169">Haga clic en Pruebas y el actualizador se ejecutará automáticamente, actualizando los scripts de prueba que faltan en sus iconos.</span><span class="sxs-lookup"><span data-stu-id="c6216-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="c6216-170">Métodos de la utilidad MRTK</span><span class="sxs-lookup"><span data-stu-id="c6216-170">MRTK Utility methods</span></span>

<span data-ttu-id="c6216-171">En esta sección se muestran algunos de los métodos o fragmentos de código usados habitualmente al escribir pruebas para MRTK.</span><span class="sxs-lookup"><span data-stu-id="c6216-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="c6216-172">Hay dos clases de utilidad que ayudan a configurar MRTK y probar interacciones con componentes en MRTK</span><span class="sxs-lookup"><span data-stu-id="c6216-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="c6216-173">TestUtilities proporciona los métodos siguientes para configurar la escena de MRTK y GameObjects:</span><span class="sxs-lookup"><span data-stu-id="c6216-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

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

<span data-ttu-id="c6216-174">Consulte los documentos de API de y para obtener más métodos de estas clases utiles, ya que se extienden de forma periódica mientras se agregan nuevas pruebas [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) a MRTK.</span><span class="sxs-lookup"><span data-stu-id="c6216-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>