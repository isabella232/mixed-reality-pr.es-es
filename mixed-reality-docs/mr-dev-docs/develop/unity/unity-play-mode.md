---
title: Modo de reproducción de Unity
description: Obtenga información sobre cómo usar el modo de reproducción en el editor de Unity para obtener una vista previa de los cambios de la aplicación en un dispositivo sin implementar una aplicación.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, comunicación remota, comunicación remota holográfica, reproductor de comunicación remota holográfica, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, modo de juego de Unity
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547104"
---
# <a name="unity-play-mode"></a><span data-ttu-id="15bd8-104">Modo de reproducción de Unity</span><span class="sxs-lookup"><span data-stu-id="15bd8-104">Unity Play Mode</span></span>

<span data-ttu-id="15bd8-105">Una manera rápida de trabajar en el proyecto de Unity es usar el "Modo de reproducción", que ejecuta la aplicación localmente en el editor de Unity en el equipo.</span><span class="sxs-lookup"><span data-stu-id="15bd8-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="15bd8-106">Unity usa Holographic Remoting para proporcionar una forma rápida de obtener una vista previa del contenido en un dispositivo HoloLens real.</span><span class="sxs-lookup"><span data-stu-id="15bd8-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="15bd8-107">El modo de reproducción también se puede usar con un Windows Mixed Reality casco conectado al equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="15bd8-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="15bd8-108">Configuración de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="15bd8-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="15bd8-109">En primer lugar, debe [instalar la aplicación Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la Microsoft Store en el HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="15bd8-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="15bd8-110">Ejecute la aplicación Holographic Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a los que conectarse.</span><span class="sxs-lookup"><span data-stu-id="15bd8-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="15bd8-111">Necesitará la versión 2.4 o posterior para trabajar con el complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="15bd8-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="15bd8-113">Comunicación remota holográfica en el modo de reproducción del Editor de Unity</span><span class="sxs-lookup"><span data-stu-id="15bd8-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="15bd8-114">Compilar un proyecto de Unity para UWP Visual Studio proyecto y, a continuación, empaquetar e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo.</span><span class="sxs-lookup"><span data-stu-id="15bd8-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="15bd8-115">Una solución es habilitar la característica de comunicación remota del editor holográfico, que le permite depurar el script de C# mediante el modo "Reproducir" directamente en un dispositivo HoloLens 2 a través de la red.</span><span class="sxs-lookup"><span data-stu-id="15bd8-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="15bd8-116">Este escenario evita la sobrecarga de compilar e implementar un paquete de UWP en un dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="15bd8-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="15bd8-117">Siga los pasos descritos en [Configuración de Holographic Remoting.](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="15bd8-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="15bd8-118">Abra **Windows > XR > comunicación remota del editor de OpenXR:**</span><span class="sxs-lookup"><span data-stu-id="15bd8-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con la administración del complemento XR resaltada](images/openxr-features-img-02.png)

3. <span data-ttu-id="15bd8-120">Introduzca la dirección IP que obtiene de la aplicación Holographic Remoting y seleccione **Habilitar comunicación remota del editor.**</span><span class="sxs-lookup"><span data-stu-id="15bd8-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con características resaltadas](images/openxr-features-img-03.png)

<span data-ttu-id="15bd8-122">Ahora puede hacer clic en el botón "Play" (Reproducir) para reproducir la aplicación unity en la aplicación Holographic Remoting en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15bd8-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="15bd8-123">También puede adjuntar [Visual Studio a Unity para](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) depurar scripts de C# en el modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="15bd8-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="15bd8-124">A partir de la versión 0.1.0, el entorno de ejecución de comunicación remota holográfica no admite delimitadores y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="15bd8-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="15bd8-125">Esta característica se va a publicar en futuras versiones.</span><span class="sxs-lookup"><span data-stu-id="15bd8-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="15bd8-126">Modo de reproducción de Unity con comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="15bd8-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="15bd8-127">Con Holographic Remoting, puede experimentar la aplicación en HoloLens mientras se ejecuta en el editor de Unity en el equipo.</span><span class="sxs-lookup"><span data-stu-id="15bd8-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="15bd8-128">La entrada de mirada, gesto, voz y asignación espacial se envía desde HoloLens al equipo.</span><span class="sxs-lookup"><span data-stu-id="15bd8-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="15bd8-129">A continuación, los fotogramas representados se envían de vuelta a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15bd8-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="15bd8-130">Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo.</span><span class="sxs-lookup"><span data-stu-id="15bd8-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="15bd8-131">La comunicación remota holográfica requiere un equipo rápido y Wi-Fi conexión.</span><span class="sxs-lookup"><span data-stu-id="15bd8-131">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="15bd8-132">Puede encontrar más detalles en la documentación [de Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)</span><span class="sxs-lookup"><span data-stu-id="15bd8-132">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="15bd8-133">Para obtener mejores resultados, asegúrese de que la aplicación establece correctamente el punto [de enfoque](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="15bd8-133">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="15bd8-134">Esto ayuda a Holographic Remoting a adaptar mejor la escena a la latencia de la conexión inalámbrica.</span><span class="sxs-lookup"><span data-stu-id="15bd8-134">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="15bd8-135">Consulte también</span><span class="sxs-lookup"><span data-stu-id="15bd8-135">See Also</span></span>

* [<span data-ttu-id="15bd8-136">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="15bd8-136">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
