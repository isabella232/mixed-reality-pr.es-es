---
title: Entrada desde teclado, ratón y controlador en DirectX
description: Explica cómo crear una aplicación para Windows Mixed Reality que usa el teclado, el mouse y los controladores de juegos.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, teclado, Mouse, dispositivo de juego, controladora Xbox, HoloLens, escritorio, tutorial, código de ejemplo
ms.openlocfilehash: 47d5ac7c7517d607d29d004497f62ac0755c3051
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692079"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="b308c-104">Entrada desde teclado, ratón y controlador en DirectX</span><span class="sxs-lookup"><span data-stu-id="b308c-104">Keyboard, mouse, and controller input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="b308c-105">Este artículo está relacionado con las API nativas de WinRT heredadas.</span><span class="sxs-lookup"><span data-stu-id="b308c-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="b308c-106">En el caso de los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](../native/openxr-getting-started.md)** .</span><span class="sxs-lookup"><span data-stu-id="b308c-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)** .</span></span>

<span data-ttu-id="b308c-107">Los teclados, los mouse y los controladores de juego pueden ser formas útiles de entrada para dispositivos Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b308c-107">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="b308c-108">Los teclados y ratones Bluetooth se admiten en HoloLens, para su uso con la depuración de la aplicación o como una forma alternativa de entrada.</span><span class="sxs-lookup"><span data-stu-id="b308c-108">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="b308c-109">Windows Mixed Reality también admite auriculares envolventes conectados a equipos, donde los ratones, los teclados y los controladores de juegos han sido históricamente la norma.</span><span class="sxs-lookup"><span data-stu-id="b308c-109">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="b308c-110">Para usar la entrada del teclado en HoloLens, empareje un teclado Bluetooth a su dispositivo o use la entrada virtual a través del portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="b308c-110">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="b308c-111">Para usar la entrada del teclado al mismo tiempo que usa un auricular envolvente de realidad mixta de Windows, asigne el foco de entrada a la realidad mixta colocando en el dispositivo o mediante la combinación de teclas de Windows + Y.</span><span class="sxs-lookup"><span data-stu-id="b308c-111">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="b308c-112">Tenga en cuenta que las aplicaciones destinadas a HoloLens deben proporcionar funcionalidad sin estos dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="b308c-112">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="b308c-113">Los fragmentos de código de este artículo muestran actualmente el uso de C++/CX en lugar de C + +17 compatible con C++/WinRT tal y como se usa en la [plantilla de proyecto de C++ Holographic](../native/creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="b308c-113">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="b308c-114">Los conceptos son equivalentes para un proyecto/WinRT de C++, aunque tendrá que traducir el código.</span><span class="sxs-lookup"><span data-stu-id="b308c-114">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="b308c-115">Suscribirse a eventos de entrada de CoreWindow</span><span class="sxs-lookup"><span data-stu-id="b308c-115">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="b308c-116">Entrada de teclado</span><span class="sxs-lookup"><span data-stu-id="b308c-116">Keyboard input</span></span>

<span data-ttu-id="b308c-117">En la plantilla de aplicación de Windows Holographic, se incluye un controlador de eventos para la entrada de teclado como cualquier otra aplicación de UWP.</span><span class="sxs-lookup"><span data-stu-id="b308c-117">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="b308c-118">La aplicación consume los datos de entrada del teclado de la misma forma en Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b308c-118">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="b308c-119">Desde AppView. cpp:</span><span class="sxs-lookup"><span data-stu-id="b308c-119">From AppView.cpp:</span></span>

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a><span data-ttu-id="b308c-120">Entrada de teclado virtual</span><span class="sxs-lookup"><span data-stu-id="b308c-120">Virtual keyboard input</span></span>
<span data-ttu-id="b308c-121">En el caso de los auriculares de escritorio envolventes, también puede admitir Teclados virtuales representados por Windows sobre la vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="b308c-121">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="b308c-122">Para admitir esto, la aplicación puede implementar **CoreTextEditContext** .</span><span class="sxs-lookup"><span data-stu-id="b308c-122">To support this, your app can implement **CoreTextEditContext** .</span></span> <span data-ttu-id="b308c-123">Esto permite a Windows comprender el estado de sus propios cuadros de texto presentados por la aplicación, por lo que el teclado virtual puede contribuir correctamente al texto.</span><span class="sxs-lookup"><span data-stu-id="b308c-123">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="b308c-124">Para obtener más información sobre cómo implementar la compatibilidad con CoreTextEditContext, vea el [ejemplo CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="b308c-124">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="b308c-125">Entrada del mouse</span><span class="sxs-lookup"><span data-stu-id="b308c-125">Mouse Input</span></span>

<span data-ttu-id="b308c-126">También puede usar la entrada del mouse de nuevo a través de los controladores de eventos de entrada de CoreWindow de UWP.</span><span class="sxs-lookup"><span data-stu-id="b308c-126">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="b308c-127">Aquí se muestra cómo modificar la plantilla de la aplicación holográfica de Windows para admitir los clics del mouse de la misma manera que los gestos presionados.</span><span class="sxs-lookup"><span data-stu-id="b308c-127">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="b308c-128">Después de realizar esta modificación, al hacer clic con el mouse mientras se contenía un dispositivo con auriculares envolvente, cambiará la posición del cubo.</span><span class="sxs-lookup"><span data-stu-id="b308c-128">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="b308c-129">Tenga en cuenta que las aplicaciones UWP también pueden obtener datos XY sin formato para el mouse mediante la API de [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .</span><span class="sxs-lookup"><span data-stu-id="b308c-129">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="b308c-130">Empiece por declarar un nuevo controlador OnPointerPressed en AppView. h:</span><span class="sxs-lookup"><span data-stu-id="b308c-130">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="b308c-131">En AppView. cpp, agregue este código a SetWindow:</span><span class="sxs-lookup"><span data-stu-id="b308c-131">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="b308c-132">Después, coloque esta definición para OnPointerPressed en la parte inferior del archivo:</span><span class="sxs-lookup"><span data-stu-id="b308c-132">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

<span data-ttu-id="b308c-133">El controlador de eventos que acabamos de agregar es un paso a través de la clase principal de la plantilla.</span><span class="sxs-lookup"><span data-stu-id="b308c-133">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="b308c-134">Vamos a modificar la clase principal para que admita este paso.</span><span class="sxs-lookup"><span data-stu-id="b308c-134">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="b308c-135">Agregue esta declaración de método público al archivo de encabezado:</span><span class="sxs-lookup"><span data-stu-id="b308c-135">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="b308c-136">Necesitará esta variable miembro privada también:</span><span class="sxs-lookup"><span data-stu-id="b308c-136">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="b308c-137">Por último, actualizaremos la clase principal con una nueva lógica para admitir los clics del mouse.</span><span class="sxs-lookup"><span data-stu-id="b308c-137">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="b308c-138">Empiece por agregar este controlador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b308c-138">Start by adding this event handler.</span></span> <span data-ttu-id="b308c-139">Asegúrese de actualizar el nombre de clase:</span><span class="sxs-lookup"><span data-stu-id="b308c-139">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="b308c-140">Ahora, en el método de actualización, reemplace la lógica existente para obtener una repose de puntero con este:</span><span class="sxs-lookup"><span data-stu-id="b308c-140">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="b308c-141">Vuelva a compilar e implementar.</span><span class="sxs-lookup"><span data-stu-id="b308c-141">Recompile and redeploy.</span></span> <span data-ttu-id="b308c-142">Tenga en cuenta que, al hacer clic con el mouse, se volverá a colocar el cubo en el casco envolvente, o HoloLens, con el mouse Bluetooth conectado.</span><span class="sxs-lookup"><span data-stu-id="b308c-142">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="b308c-143">Compatibilidad con el dispositivo de juego</span><span class="sxs-lookup"><span data-stu-id="b308c-143">Game controller support</span></span>

<span data-ttu-id="b308c-144">Los dispositivos de juego pueden ser una forma divertida y cómoda de permitir al usuario controlar una experiencia de Windows Mixed Reality más envolvente.</span><span class="sxs-lookup"><span data-stu-id="b308c-144">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="b308c-145">El primer paso para agregar compatibilidad con dispositivos de juego a la plantilla de aplicación de Windows Holographic es agregar las siguientes declaraciones de miembro privado a la clase de encabezado para el archivo principal:</span><span class="sxs-lookup"><span data-stu-id="b308c-145">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

<span data-ttu-id="b308c-146">Inicialice los eventos del controlador de juegos y los controladores de juegos que estén conectados actualmente en el constructor de la clase principal:</span><span class="sxs-lookup"><span data-stu-id="b308c-146">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

<span data-ttu-id="b308c-147">Agregue estos controladores de eventos a la clase principal.</span><span class="sxs-lookup"><span data-stu-id="b308c-147">Add these event handlers to your main class.</span></span> <span data-ttu-id="b308c-148">Asegúrese de actualizar el nombre de clase:</span><span class="sxs-lookup"><span data-stu-id="b308c-148">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

<span data-ttu-id="b308c-149">Por último, actualice la lógica de entrada para que reconozca los cambios en el estado del controlador.</span><span class="sxs-lookup"><span data-stu-id="b308c-149">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="b308c-150">Aquí, usamos la misma variable m_pointerPressed descrita en la sección anterior para agregar eventos del mouse.</span><span class="sxs-lookup"><span data-stu-id="b308c-150">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="b308c-151">Agregue esto al método Update, justo antes de donde comprueba el SpatialPointerPose:</span><span class="sxs-lookup"><span data-stu-id="b308c-151">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="b308c-152">No olvide anular el registro de los eventos al limpiar la clase principal:</span><span class="sxs-lookup"><span data-stu-id="b308c-152">Don't forget to unregister the events when cleaning up the main class:</span></span>

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

<span data-ttu-id="b308c-153">Vuelva a compilar e implementar.</span><span class="sxs-lookup"><span data-stu-id="b308c-153">Recompile, and redeploy.</span></span> <span data-ttu-id="b308c-154">Ahora puede adjuntar, o emparejar, un dispositivo de juego y usarlo para cambiar la posición del cubo giratorio.</span><span class="sxs-lookup"><span data-stu-id="b308c-154">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="b308c-155">Directrices importantes para la entrada de teclado y del mouse</span><span class="sxs-lookup"><span data-stu-id="b308c-155">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="b308c-156">Hay algunas diferencias importantes en el modo en que este código se puede usar en Microsoft HoloLens, que es un dispositivo que se basa principalmente en la entrada natural del usuario, frente a lo que está disponible en un equipo con Windows Mixed Reality habilitado.</span><span class="sxs-lookup"><span data-stu-id="b308c-156">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="b308c-157">No se puede confiar en que la entrada del mouse o del teclado esté presente.</span><span class="sxs-lookup"><span data-stu-id="b308c-157">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="b308c-158">Toda la funcionalidad de la aplicación debe funcionar con la mirada, el gesto y la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="b308c-158">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="b308c-159">Cuando se adjunta un teclado Bluetooth, puede resultar útil habilitar la entrada del teclado para cualquier texto que la aplicación pueda solicitar.</span><span class="sxs-lookup"><span data-stu-id="b308c-159">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="b308c-160">Este puede ser un complemento excelente para el dictado, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="b308c-160">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="b308c-161">En lo que respecta al diseño de la aplicación, no confíe en los controles WASD y de apariencia del mouse para el juego.</span><span class="sxs-lookup"><span data-stu-id="b308c-161">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="b308c-162">HoloLens está diseñado para que el usuario pueda desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="b308c-162">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="b308c-163">En este caso, el usuario controla la cámara directamente.</span><span class="sxs-lookup"><span data-stu-id="b308c-163">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="b308c-164">Una interfaz para impulsar la cámara en torno a la habitación con controles de movimiento y apariencia no proporciona la misma experiencia.</span><span class="sxs-lookup"><span data-stu-id="b308c-164">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="b308c-165">La entrada mediante teclado puede ser una manera excelente de controlar los aspectos de depuración de la aplicación o el motor de juegos, sobre todo porque el usuario no tendrá que usar el teclado.</span><span class="sxs-lookup"><span data-stu-id="b308c-165">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="b308c-166">El cableado es el mismo que se usa con las API de eventos de CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="b308c-166">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="b308c-167">En este escenario, puede optar por implementar una manera de configurar la aplicación para que enrute los eventos de teclado a un modo de "depuración de solo entrada" durante las sesiones de depuración.</span><span class="sxs-lookup"><span data-stu-id="b308c-167">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="b308c-168">Los controladores Bluetooth también funcionan.</span><span class="sxs-lookup"><span data-stu-id="b308c-168">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="b308c-169">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b308c-169">See also</span></span>
* [<span data-ttu-id="b308c-170">Accesorios de hardware</span><span class="sxs-lookup"><span data-stu-id="b308c-170">Hardware accessories</span></span>](../../discover/hardware-accessories.md)
