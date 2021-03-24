---
title: ScreenshotUtility
description: Documentación sobre cómo usar la herramienta de captura de pantalla en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 2f5110e0ad4cbad42dcbfef93a21dc34644bfe8d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694672"
---
# <a name="screenshot-utility"></a><span data-ttu-id="b2b28-104">Utilidad de captura de pantalla</span><span class="sxs-lookup"><span data-stu-id="b2b28-104">Screenshot utility</span></span>

<span data-ttu-id="b2b28-105">A menudo, la obtención de capturas de pantallas en Unity para documentación e imágenes promocionales puede ser agobiante, y el resultado en general no es el deseable.</span><span class="sxs-lookup"><span data-stu-id="b2b28-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="b2b28-106">Aquí es donde entra en juego la clase `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility).</span><span class="sxs-lookup"><span data-stu-id="b2b28-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="b2b28-107">La clase ScreenshotUtility ayuda a obtener capturas de pantallas a través de elementos de menú y API públicas en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="b2b28-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="b2b28-108">Las capturas de pantallas se pueden obtener en distintas resoluciones y con colores transparentes para su uso en la composición sencilla de imágenes.</span><span class="sxs-lookup"><span data-stu-id="b2b28-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="b2b28-109">Esta herramienta no admite la obtención de capturas de pantallas de una compilación independiente.</span><span class="sxs-lookup"><span data-stu-id="b2b28-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="b2b28-110">Obtención de capturas de pantallas</span><span class="sxs-lookup"><span data-stu-id="b2b28-110">Taking screenshots</span></span>

<span data-ttu-id="b2b28-111">Para obtener capturas de pantalla fácilmente, en el editor seleccione *Mixed Reality Toolkit -> Utilities -> Take Screenshot* (Mixed Reality Toolkit -> Utilidades -> Obtener captura de pantalla) y, luego, la opción que quiera.</span><span class="sxs-lookup"><span data-stu-id="b2b28-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="b2b28-112">Asegúrese de que la pestaña de la ventana de juego esté visible si obtiene la captura de pantalla mientras no está jugando, o es posible que no se guarde una captura.</span><span class="sxs-lookup"><span data-stu-id="b2b28-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="b2b28-113">De manera predeterminada, todas las capturas de pantalla se guardan en la [ruta de acceso de caché temporal](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html); la ruta de acceso a la captura de pantalla se mostrará en la consola de Unity.</span><span class="sxs-lookup"><span data-stu-id="b2b28-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![Elemento de menú de la utilidad de captura de pantalla](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="b2b28-115">Ejemplo de captura de pantalla</span><span class="sxs-lookup"><span data-stu-id="b2b28-115">Example screenshot capture</span></span>

<span data-ttu-id="b2b28-116">La captura de pantalla siguiente se obtuvo con la opción *4x Resolution (Transparent Background)* (Resolución 4x [fondo transparente]).</span><span class="sxs-lookup"><span data-stu-id="b2b28-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="b2b28-117">Esto genera una imagen de alta resolución, donde los píxeles que normalmente se representan con el color transparente se guardan como píxeles transparentes.</span><span class="sxs-lookup"><span data-stu-id="b2b28-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="b2b28-118">Esta técnica ayuda a los desarrolladores a presentar su aplicación para la tienda, u otros medios de distribución multimedia, superponiendo esta imagen encima de otras imágenes.</span><span class="sxs-lookup"><span data-stu-id="b2b28-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![Ejemplo de captura de la utilidad de captura de pantalla](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Example_Capture.png)
