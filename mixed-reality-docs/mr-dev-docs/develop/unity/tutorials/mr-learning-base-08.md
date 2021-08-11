---
title: Uso del seguimiento ocular
description: En este curso se muestra cómo usar el seguimiento ocular en las aplicaciones de realidad mixta con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, eye-tracking
ms.localizationpriority: high
ms.openlocfilehash: 8a12bf37547466a07cd47e34d7fbc41e88ca87d345e2ef4fcd73b749bdfd0322
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227504"
---
# <a name="8-using-eye-tracking"></a>8. Uso del seguimiento ocular

En este tutorial, aprenderá a habilitar el seguimiento ocular para HoloLens 2 y agregará el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.

> [!NOTE]
> Si también va a implementar este proyecto en HoloLens (primera generación), tenga en cuenta que el seguimiento ocular solo es compatible con HoloLens 2.

## <a name="objectives"></a>Objetivos

* Aprender a habilitar el seguimiento ocular para HoloLens 2
* Aprender a usar el seguimiento ocular para desencadenar la acción

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Asegurarse de que está habilitada la funcionalidad de entrada de mirada

En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Project for MRTK** (Configurar proyecto para MRTK) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Eye Gaze Input Capability** (Habilitar funcionalidad de entrada de mirada) esté atenuada:

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La funcionalidad de entrada de mirada con los ojos debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) al configurar el proyecto de Unity al principio de esta serie de tutoriales. Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Habilitar la mirada con los ojos en el proveedor de mirada

En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, seleccione la pestaña MixedRealityToolkit > **Input** (Entrada) y realice los pasos siguientes:

* Clone el perfil **DefaultHoloLens2InputSystemProfile** y asígnele un nombre adecuado; por ejemplo, _GettingStarted_HoloLens2InputSystemProfile_.
* Expanda la sección **Punteros**.
* Clone el perfil **DefaultMixedRealityPointerProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityPointerProfile_.
* Busque la sección **Gaze Settings** (Configuración de mirada) y active la casilla **Is Eye Tracking Enabled** (Está habilitado el seguimiento ocular).

![Componente MixedRealityToolkit de Unity con los perfiles recién creados aplicados y el seguimiento ocular habilitado](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Para recibir un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Habilitar el seguimiento ocular simulado para el editor de Unity

En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, navegue hasta la pestaña **Entrada** y, a continuación:

* Expanda la sección **Input Data Providers** (Proveedores de datos de entrada)  > **Input Simulation Service** (Servicio de simulación de entrada).
* Clone el perfil **DefaultMixedRealityInputSimulationProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityInputSimulationProfile_.
* Busque **Eye Gaze Simulation** (Simulación de mirada) y establezca el valor de **Default Eye Gaze Simulation Mode** (Modo de simulación de mirada predeterminado) en **Camera Forward Axis** (Eje de cámara hacia adelante).

![Unity con el objeto TextMeshPro seleccionado](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Agregar seguimiento ocular a los objetos

En la ventana Hierarchy (Jerarquía), expanda **RoverExplorer** > **Buttons** y, a continuación, seleccione los tres objetos de botón secundarios:

![Unity con el objeto Button seleccionado](images/mr-learning-base/base-08-section4-step1-1.png)

Con los tres objetos Button todavía seleccionados, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **EyeTrackingTarget** a todos los objetos seleccionados:

![Unity con el objeto TextMeshPro seleccionado y componentes agregados](images/mr-learning-base/base-08-section4-step1-2.png)

En la ventana Hierarchy (Jerarquía), expanda **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel**  >  **TextMeshPro**.

Luego, en la ventana Hierarchy (Jerarquía), seleccione el objeto de botón **Hints** (Sugerencias) y configure el componente **EyeTrackingTarget** como se indica a continuación:

* En la sección de eventos **On Look At Start ()**
  * Haga clic en el icono **+** pequeño para agregar otro evento.
  * Asigne el objeto **TextMeshPro** del botón **Hints** al campo **None (Object)** (Ninguno [Objeto]).
  * En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.
  * Establezca el argumento en **0,06** para aumentar el tamaño de fuente actual de 0,04 por el 50 %.
* En la sección de eventos **On Look Away ()**
  * Haga clic en el icono **+** pequeño para agregar otro evento.
  * Asigne el objeto **TextMeshPro** del botón **Hints** al campo **None (Object)** (Ninguno [Objeto]).
  * En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.
  * Establezca el argumento en **0,04** para restablecer el tamaño de fuente en 0,04.

![Unity con el objeto TextMeshPro de Hints seleccionado y el componente EyeTrackingTarget configurado](images/mr-learning-base/base-08-section4-step1-3.png)

**Repita** este paso para el objeto de botón **Explode** (Expandir) y **Reset** (Restablecer) para configurar el seguimiento ocular de los botones restantes.

Ahora, si entra en el Modo de Juego y, a continuación, mantiene presionado el botón derecho del mouse mientras lo mueve hasta que la mirada entre en contacto con uno de los botones, verá cómo la fuente aumenta su tamaño en un 50 % y se restablece su tamaño original al apartar la mirada:

![Vista dividida del modo de reproducción de Unity con la mirada que en contacto con la etiqueta del botón Explode del destino de seguimiento ocular](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a habilitar el seguimiento ocular para HoloLens 2 y cómo agregar el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 9. Uso de los comandos de voz](mr-learning-base-09.md)
