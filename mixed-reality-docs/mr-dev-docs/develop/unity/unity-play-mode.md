---
title: Modo de reproducción de Unity
description: Aprenda a usar el modo de reproducción en el editor de Unity para obtener una vista previa de los cambios de la aplicación en un dispositivo sin implementar una aplicación.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, comunicación remota, comunicación remota holográfica, reproductor de comunicación remota holográfica, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, modo de juego de Unity
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392301"
---
# <a name="unity-play-mode"></a><span data-ttu-id="7ac5a-104">Modo de reproducción de Unity</span><span class="sxs-lookup"><span data-stu-id="7ac5a-104">Unity Play Mode</span></span>

<span data-ttu-id="7ac5a-105">Una manera rápida de trabajar en el proyecto de Unity es usar el "Modo de reproducción", que ejecuta la aplicación localmente en el editor de Unity en el equipo.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="7ac5a-106">Unity usa Holographic Remoting para proporcionar una manera rápida de obtener una vista previa del contenido en un dispositivo HoloLens real.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="7ac5a-107">El modo de reproducción también se puede usar con un Windows Mixed Reality casco conectado al equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="7ac5a-108">Configuración de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="7ac5a-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="7ac5a-109">En primer lugar, debe [instalar la aplicación Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la Microsoft Store en el HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7ac5a-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="7ac5a-110">Ejecute la aplicación Holographic Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a los que conectarse.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="7ac5a-111">Necesitará la versión 2.4 o posterior para trabajar con el complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="7ac5a-113">Modo de reproducción de Unity con comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="7ac5a-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="7ac5a-114">Con Holographic Remoting, puede experimentar la aplicación en HoloLens mientras se ejecuta en el editor de Unity en el equipo.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="7ac5a-115">La entrada de mirada, gesto, voz y asignación espacial se envía desde HoloLens al equipo.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="7ac5a-116">Los fotogramas representados se envían de vuelta a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="7ac5a-117">Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="7ac5a-118">La comunicación remota holográfica requiere un equipo rápido Wi-Fi conexión.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="7ac5a-119">Puede encontrar más detalles en la documentación [de Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)</span><span class="sxs-lookup"><span data-stu-id="7ac5a-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="7ac5a-120">Para obtener mejores resultados, asegúrese de que la aplicación establece correctamente el punto [de enfoque](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="7ac5a-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="7ac5a-121">Esto ayuda a Holographic Remoting a adaptar mejor la escena a la latencia de la conexión inalámbrica.</span><span class="sxs-lookup"><span data-stu-id="7ac5a-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ac5a-122">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7ac5a-122">See Also</span></span>

* [<span data-ttu-id="7ac5a-123">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="7ac5a-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
