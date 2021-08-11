---
title: Creación de un proyecto de DirectX holográfico
description: Aprenda a crear una nueva aplicación Holográfica directX basada en la plantilla Windows Mixed Reality aplicación.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, aplicación holográfica, nueva aplicación, aplicación para UWP, aplicación de plantilla, hologramas, nuevo proyecto, tutorial, descarga, código de ejemplo, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 7de7d73ec1e5fd8abde6d4822c86628e090fdf0cf89769fc9ef21311ff1aff15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200179"
---
# <a name="creating-a-holographic-directx-project"></a>Creación de un proyecto de DirectX holográfico

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](openxr-getting-started.md)**.

Una aplicación holográfica que cree para un HoloLens será una aplicación de Windows plataforma universal <a href="/windows/uwp/get-started/universal-application-platform-guide" target="_blank">(UWP).</a>  Si el destino es Windows Mixed Reality cascos de escritorio, puedes crear una aplicación para UWP o una aplicación Win32.

La plantilla de aplicación para UWP holográfica de DirectX 11 es muy parecido a la plantilla de aplicación para UWP de DirectX 11. La plantilla incluye un bucle de programa, una **clase DeviceResources** para administrar el dispositivo y el contexto de Direct3D y una clase de representador de contenido simplificada. También tiene un <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView,</a>al igual que cualquier otra aplicación para UWP.

Sin embargo, la aplicación de realidad mixta tiene algunas funcionalidades adicionales que no están presentes en una aplicación para UWP típica de Direct3D. La Windows Mixed Reality de aplicación puede:
* Controle los recursos de dispositivo Direct3D asociados con cámaras holográficas.
* Recupere los búferes de la cámara del sistema. En el caso de Direct3D12, cree recursos de búfer de reserva holográficos y administre la duración de los recursos.
* Controle [la entrada](../../design/gaze-and-commit.md) de mirada y reconozca un [gesto](../../design/gaze-and-commit.md#composite-gestures).
* Vaya al modo de representación estéreo a pantalla completa.

## <a name="how-do-i-get-started"></a>¿Cómo empiezo?

En [primer lugar,](../install-the-tools.md)instale las herramientas siguiendo las instrucciones para descargar Visual Studio 2019 y las plantillas Windows Mixed Reality aplicación. Las plantillas de aplicación de realidad mixta están disponibles en Visual Studio Marketplace como una descarga [web](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)o instalandolas como una extensión a través de la interfaz Visual Studio usuario.

Ahora está listo para crear la aplicación directX 11 Windows Mixed Reality aplicación. Tenga en cuenta que, para quitar el contenido de ejemplo, **comente** DRAW_SAMPLE_CONTENT directiva de preprocesador en *pch.h*.

## <a name="creating-a-uwp-project"></a>Creación de un proyecto de UWP

Una vez instaladas las herramientas, ](.. /install-the-tools.md) puede crear un proyecto holográfico de DirectX para UWP.

Para crear un proyecto en Visual Studio 2019:
1. Inicie **Visual Studio**.
2. En la **Introducción** a la derecha, seleccione **Crear un nuevo proyecto.**
3. En los menús desplegables  del cuadro de diálogo Crear un nuevo proyecto, seleccione **C++**, **Windows Mixed Reality** y **UWP.**
4. Seleccione **Holographic DirectX 11 App (Universal Windows) (C++/WinRT).**
   ![Captura de pantalla de la plantilla de proyecto de aplicación para UWP de Holographic DirectX 11 C++/WinRT en Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Plantilla de proyecto de aplicación para UWP de Holographic DirectX 11 C++/WinRT en Visual Studio 2019*
   >[!IMPORTANT]
   >Asegúrese de que el nombre de la plantilla de proyecto incluye "(C++/WinRT)".  Si no es así, tiene instalada una versión anterior de las plantillas de proyecto holográficas.  Para obtener las plantillas de proyecto más recientes, [instállas](../install-the-tools.md) como una extensión para Visual Studio 2019.
5. Seleccione **Siguiente**.
5. Rellene los cuadros **de Project y** **Ubicación** y seleccione o pulse **Crear**. Se crea el proyecto de aplicación holográfica.
6. Para el desarrollo dirigido solo HoloLens 2,  asegúrese  de que la versión de destino y la versión mínima están **establecidas en Windows 10, versión 1903.**  Si también tiene como destino cascos HoloLens (1.ª generación) o de  escritorio Windows Mixed Reality, puede establecer La versión mínima en **Windows 10, versión 1809**. Esto requerirá algunas <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">comprobaciones adaptables de versión</a> en el código al usar nuevas características de HoloLens 2.
   ![Captura de pantalla de Windows 10, versión 1903 como destino y versiones mínimas](images/new-uwp-project.png)<br>
   *Establecer **Windows 10, versión 1903** como destino y versiones mínimas*
   >[!IMPORTANT]
   >Si no ve la **Windows 10, versión 1903** como opción, no tiene instalada la versión Windows 10 SDK.  Para que aparezca esta opción, instale la <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">versión 10.0.18362.0</a>o posterior del SDK Windows 10 .

Para crear un proyecto en Visual Studio 2017:
1. Inicie **Visual Studio**.
2. En el **menú** Archivo, seleccione **Nuevo** y **seleccione Project** en el menú contextual. Se abre el cuadro de diálogo **Nuevo proyecto**.
3. Expanda **Instalado a** la izquierda y expanda el **Visual C++** de idioma.
4. Vaya al nodo **Windows universal > Holographic** y seleccione **Holographic DirectX 11 App (Universal Windows) (C++/WinRT) (Aplicación Holográfica directX 11 [Aplicación universal Windows]) (C++/WinRT).**
   ![Captura de pantalla de la plantilla de proyecto de aplicación para UWP de Holographic DirectX 11 C++/WinRT en Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *Plantilla de proyecto de aplicación para UWP de Holographic DirectX 11 C++/WinRT en Visual Studio 2017*
   >[!IMPORTANT]
   >Asegúrese de que el nombre de la plantilla de proyecto incluye "(C++/WinRT)".  Si no es así, tiene instalada una versión anterior de las plantillas de proyecto holográficas.  Para obtener las plantillas de proyecto más recientes, [instállas](../install-the-tools.md) como una extensión para Visual Studio 2017.
5. Rellene los cuadros **de texto Nombre** y Ubicación y seleccione o pulse **Aceptar.**  Se crea el proyecto de aplicación holográfica.
6. Para el desarrollo dirigido solo HoloLens 2,  asegúrese  de que la versión de destino y la versión mínima están **establecidas en Windows 10, versión 1903.**  Si también tiene como destino cascos HoloLens (1.ª generación) o de  escritorio Windows Mixed Reality, puede establecer La versión mínima en **Windows 10, versión 1809**. Esto requerirá algunas <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">comprobaciones adaptables de versión</a> en el código al usar nuevas características de HoloLens 2.
   ![Captura de pantalla de Windows 10, versión 1903 como destino y versiones mínimas](images/new-uwp-project.png)<br>
   *Establecer **Windows 10, versión 1903** como destino y versiones mínimas*
   >[!IMPORTANT]
   >Si no ve la **Windows 10, versión 1903** como opción, no tiene instalada la versión Windows 10 SDK.  Para que aparezca esta opción, instale la <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">versión 10.0.18362.0</a>o posterior del SDK Windows 10 .

La plantilla genera un proyecto mediante <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT,</a>una proyección del lenguaje C++17 de las API de tiempo de ejecución de Windows que admite cualquier compilador de C++17 compatible con estándares.  El proyecto muestra cómo crear un cubo bloqueado por el mundo que se coloca a 2 metros del usuario. El usuario puede [pulsar en](../../design/gaze-and-commit.md#composite-gestures) el aire o presionar un botón en el controlador para colocar el cubo en una posición diferente especificada por la mirada del [usuario.](../../design/gaze-and-commit.md) Puede modificar este proyecto para crear cualquier aplicación de realidad mixta.

También puede crear un nuevo proyecto mediante la plantilla de proyecto holográfico de **Visual C#,** que se basa en SharpDX.  Si el proyecto holográfico de C# no comenzó desde la plantilla de aplicación holográfica de Windows, deberá copiar el archivo ms.fxcompile.targets de un proyecto de plantilla de C# de Windows Mixed Reality e importarlo en el archivo .csproj para compilar los archivos HLSL que agregue al proyecto. También se proporciona una plantilla de Direct3D 12 en la extensión Windows Mixed Reality plantillas de aplicación para Visual Studio.

Consulte [Uso Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md) para implementar y depurar para obtener información sobre cómo compilar e implementar el ejemplo en HoloLens, equipo con dispositivo envolvente conectado o un emulador.

En el resto de las instrucciones siguientes se supone que usa C++ para compilar la aplicación.

### <a name="uwp-app-entry-point"></a>Punto de entrada de la aplicación para UWP

La aplicación holográfica para UWP se inicia en la **función wWinMain** en AppView.cpp. La **función wWinMain** crea el <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> de la aplicación e inicia <a href="/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> con él.

Desde **AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

A partir de ese momento, la clase AppView controla la interacción con Windows eventos de entrada básicos, eventos y mensajería de CoreWindow, y así sucesivamente. También creará el espacio holográfico que usa la aplicación.

## <a name="creating-a-win32-project"></a>Creación de un proyecto win32

La manera más fácil de empezar a crear un proyecto holográfico de Win32 es adaptar el ejemplo <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">de Win32 *basicHologram*</a>.

En este ejemplo de Win32 se usa <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT,</a>una proyección del lenguaje C++17 de las API de tiempo de ejecución de Windows que admite cualquier compilador de C++17 compatible con estándares.  El proyecto muestra cómo crear un cubo bloqueado por el mundo que se coloca a 2 metros del usuario. El usuario puede presionar un botón en el controlador para colocar el cubo en una posición diferente especificada por la mirada del [usuario.](../../design/gaze-and-commit.md) Puede modificar este proyecto para crear cualquier aplicación de realidad mixta.

### <a name="win32-app-entry-point"></a>Punto de entrada de la aplicación Win32

La aplicación holográfica Win32 se inicia en la **función wWinMain** de AppMain.cpp. La **función wWinMain** crea el HWND de la aplicación e inicia su bucle de mensajes.

Desde **AppMain.cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

A partir de ese momento, la clase AppMain controla la interacción con mensajes de ventana básicos, y así sucesivamente. También creará el espacio holográfico que usa la aplicación.

## <a name="render-holographic-content"></a>Representación de contenido holográfico

La carpeta Content **del proyecto** contiene clases para representar hologramas en el [espacio holográfico](getting-a-holographicspace.md). El holograma predeterminado de la plantilla es un cubo giratorio que se coloca a 2 metros del usuario. Dibujar este cubo se implementa en **SpinningCubeRenderer.cpp,** que tiene estos métodos clave:

|  Método  |  Explicación | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carga sombreadores y crea la malla de cubo. | 
|  `PositionHologram` |  Coloca el holograma en la ubicación especificada por el <a href="/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">objeto SpatialPointerPose proporcionado.</a> | 
|  `Update` |  Gira el cubo y establece la matriz del modelo. | 
|  `Render` |  Representa un marco mediante los sombreadores de vértices y píxeles. | 

La **subcarpeta Sombreadores** contiene cuatro implementaciones de sombreador predeterminadas:

|  Sombreador  |  Explicación | 
|----------|----------|
|  `GeometryShader.hlsl` |  Paso a través que deja la geometría sin modificar. | 
|  `PixelShader.hlsl` |  Pasa a través de los datos de color. Los datos de color se interpolan y se asignan a un píxel en el paso de rasterización. | 
|  `VertexShader.hlsl` |  Sombreador simple para realizar el procesamiento de vértices en la GPU. | 
|  `VPRTVertexShader.hlsl` |  Sombreador simple para realizar el procesamiento de vértices en la GPU, que está optimizado para Windows Mixed Reality representación estéreo. | 

`VertexShaderShared.hlsl` contiene código común compartido entre `VertexShader.hlsl` y `VPRTVertexShader.hlsl` .

Nota: La plantilla de aplicación de Direct3D 12 también incluye `ViewInstancingVertexShader.hlsl` . Esta variante usa características opcionales de D3D12 para representar imágenes estéreo de forma más eficaz.

Los sombreadores se compilan cuando se compila el proyecto y se cargan en el método **SpinningCubeRenderer::CreateDeviceDependentResources.**

## <a name="interact-with-your-holograms"></a>Interacción con los hologramas

La entrada del usuario se procesa en la **clase SpatialInputHandler,** que obtiene una instancia de <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> y se suscribe al <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">evento SourcePressed.</a> Esto permite detectar el gesto de pulsar el aire y otros eventos de entrada espacial.

## <a name="update-holographic-content"></a>Actualización del contenido holográfico

La aplicación de realidad mixta se actualiza en un bucle de juego, que de forma predeterminada se implementa en el **método Update** de `AppMain.cpp` . El **método Update** actualiza los objetos de escena, como el cubo giratorio, y devuelve un objeto <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> que se usa para obtener matrices de proyección y vista actualizadas y para presentar la cadena de intercambio.

El **método Render** de toma `AppMain.cpp` <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> y representa el fotograma actual en cada cámara holográfica, según el estado actual de la aplicación y el posicionamiento espacial.

## <a name="notes"></a>Notas

La Windows Mixed Reality de aplicación ahora admite la compilación con la marca de mitigación spectre habilitada (/Qspectre). Asegúrese de instalar la versión mitigada por Spectre de las bibliotecas en tiempo de ejecución Microsoft Visual C++ (MSVC) antes de compilar una configuración con la mitigación de Spectre habilitada. Para instalar las bibliotecas de C++ mitigadas por Spectre, inicie el Instalador de Visual Studio y seleccione **Modificar**. Vaya a **Componentes individuales** y busque "spectre". Seleccione los cuadros correspondientes MSVC las plataformas de destino y la versión para la  que necesita compilar el código mitigado por Spectre y haga clic en Modificar para comenzar la instalación.

## <a name="see-also"></a>Consulte también
* [Obtención de HolographicSpace](getting-a-holographicspace.md)
* <a href="/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Representación en DirectX](rendering-in-directx.md)
* [Uso de Visual Studio para implementar y depurar](../platform-capabilities-and-apis/using-visual-studio.md)
* [Uso del emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Uso de XAML con aplicaciones de DirectX holográficas](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)