---
title: Entrada desde teclado, ratón y controlador en DirectX
description: Explica cómo crear una aplicación para Windows Mixed Reality usa controladores de teclado, mouse y juego.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, teclado, mouse, controlador de juegos, controlador de Xbox, HoloLens, escritorio, tutorial, código de ejemplo
ms.openlocfilehash: e7ae65e660fe0348205fabc1c292328912fb1cdc
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244172"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Entrada desde teclado, ratón y controlador en DirectX

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](../native/openxr-getting-started.md)**.

Los teclados, los mouse y los controladores de juegos pueden ser formas útiles de entrada para Windows Mixed Reality dispositivos. Bluetooth teclados y mouse se admiten en HoloLens, para su uso con la depuración de la aplicación o como una forma alternativa de entrada. Windows Mixed Reality también admite cascos envolventes conectados a equipos, donde mouse, teclados y controladores de juegos han sido históricamente la norma.

Para usar la entrada de teclado HoloLens, emparere un teclado Bluetooth en el dispositivo o use la entrada virtual a través del Windows Portal de dispositivos. Para usar la entrada de teclado mientras lleva un casco envolvente de Windows Mixed Reality, asigne el foco de entrada a la realidad mixta colocando el dispositivo o usando la combinación de teclado Windows Tecla e Y. Tenga en cuenta que las aplicaciones diseñadas para HoloLens deben proporcionar funcionalidad sin estos dispositivos conectados.
<!--Unity Note: the paragraph below explains that the article provides C++ code snippets. -->
>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso de C++/CX en lugar de C++17 compatible con C++/WinRT como se usa en la plantilla de proyecto holográfico de [C++.](../native/creating-a-holographic-directx-project.md)  Los conceptos son equivalentes para un proyecto de C++/WinRT, aunque deberá traducir el código.

## <a name="subscribe-for-corewindow-input-events"></a>Suscripción a eventos de entrada de CoreWindow

### <a name="keyboard-input"></a>Entrada de teclado

En la Windows de aplicación Holográfica, se incluye un controlador de eventos para la entrada de teclado como cualquier otra aplicación para UWP. La aplicación consume los datos de entrada del teclado de la misma manera en Windows Mixed Reality.

Desde AppView.cpp:

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

### <a name="virtual-keyboard-input"></a>Entrada de teclado virtual
Para los cascos de escritorio envolventes, puede admitir teclados virtuales representados por Windows sobre la vista inmersiva mediante la implementación **de CoreTextEditContext**. Esto permite Windows el estado de sus propios cuadros de texto representados por la aplicación, por lo que el teclado virtual puede contribuir correctamente al texto allí.

Para obtener más información sobre cómo implementar la compatibilidad con CoreTextEditContext, vea el [ejemplo coreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Entrada del mouse

También puedes usar la entrada del mouse, de nuevo a través de los controladores de eventos de entrada coreWindow de UWP. Aquí se muestra cómo modificar la plantilla de Windows holographic para admitir los clics del mouse de la misma manera que los gestos presionados. Después de realizar esta modificación, al hacer clic con el mouse mientras se lleva a cabo un dispositivo de casco envolvente, se cambiará la posición del cubo.

> [!NOTE]
> Las aplicaciones para UWP también pueden obtener datos XY sin procesar para el mouse mediante [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) API.

Comience declarando un nuevo controlador OnPointerPressed en AppView.h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

En AppView.cpp, agregue este código a SetWindow:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

A continuación, coloque esta definición para OnPointerPressed en la parte inferior del archivo:

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

El controlador de eventos que se acaba de agregar es un paso a través a la clase principal de la plantilla. Vamos a modificar la clase principal para admitir este paso a través. Agregue esta declaración de método público al archivo de encabezado:

```
// Handle mouse input.
       void OnPointerPressed();
```

También necesitará esta variable de miembro privado:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Por último, actualizaremos la clase principal con una nueva lógica para admitir los clics del mouse. Empiece agregando este controlador de eventos. Asegúrese de actualizar el nombre de clase:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Ahora, en el método Update, reemplace la lógica existente para obtener una posición de puntero por esta:

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

Vuelva a compilar y volver a implementar. Observe que el clic del mouse ahora cambiará la posición del cubo en el casco envolvente o HoloLens con el mouse bluetooth conectado.

### <a name="game-controller-support"></a>Compatibilidad con el controlador de juegos

Los controladores de juegos pueden ser una manera divertida y cómoda de permitir al usuario controlar una experiencia Windows Mixed Reality envolvente.

 agregue las siguientes declaraciones de miembro privado a la clase de encabezado para el archivo principal:

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

Inicialice los eventos del controlador de juegos y cualquier controlador de juegos que esté asociado actualmente en el constructor de la clase principal:

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

Agregue estos controladores de eventos a la clase principal. Asegúrese de actualizar el nombre de clase:

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

Por último, actualice la lógica de entrada para reconocer los cambios en el estado del controlador. Aquí, usamos la misma variable m_pointerPressed que se describe en la sección anterior para agregar eventos del mouse. Agregue esto al método Update, justo antes de comprobar si hay SpatialPointerPose:

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

No olvide anular el registro de los eventos al limpiar la clase principal:

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

Vuelva a compilar y vuelva a implementar. Ahora puede asociar o emparejar un controlador de juego y usarlo para cambiar la posición del cubo de giro.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Directrices importantes para la entrada de teclado y mouse

Hay algunas diferencias clave en cómo se puede usar este código en Microsoft HoloLens, que es un dispositivo que se basa principalmente en la entrada del usuario natural, frente a lo que está disponible en un equipo Windows Mixed Reality habilitado para Windows Mixed Reality.
* No puede confiar en que la entrada del teclado o del mouse esté presente. Toda la funcionalidad de la aplicación debe funcionar con la mirada, el gesto y la entrada de voz.
* Cuando se Bluetooth teclado, puede resultar útil habilitar la entrada de teclado para cualquier texto que la aplicación pueda solicitar. Esto puede ser un complemento excelente para el dictado, por ejemplo.
* Cuando se trata de diseñar la aplicación, no se base en (por ejemplo) los controles WASD y de aspecto del mouse para el juego. HoloLens está diseñado para que el usuario pasee por la sala. En este caso, el usuario controla la cámara directamente. Una interfaz para impulsar la cámara alrededor de la sala con controles de movimiento y aspecto no proporcionará la misma experiencia.
* La entrada de teclado es una excelente manera de controlar la depuración de la aplicación o del motor de juego, especialmente porque el usuario no tendrá que usar el teclado. Conectarlo es lo mismo que está acostumbrado, con las API de eventos de CoreWindow. En este escenario, puede optar por implementar una manera de configurar la aplicación para enrutar eventos de teclado a un modo de "solo entrada de depuración" durante las sesiones de depuración.
* Bluetooth controladores también funcionan.

## <a name="see-also"></a>Consulte también
* [Accesorios de hardware](../../discover/hardware-accessories.md)