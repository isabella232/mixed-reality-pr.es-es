---
title: Controladores de HP reverberación G2 en Unity
description: Instrucciones sobre el uso de los controladores de HP reverberación G2 en SteamVR y Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, reverberación, reverberación G2, HP reverberación G2, realidad mixta, desarrollo, controladores de movimiento, entrada de usuario, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638392"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="05553-104">Controladores de HP reverberación G2 en Unity</span><span class="sxs-lookup"><span data-stu-id="05553-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="05553-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="05553-105">Getting started</span></span>

<span data-ttu-id="05553-106">No es necesario realizar ninguna configuración adicional para usar el controlador de HP reverberación G2 si está desarrollando para SteamVR o mediante la API de entrada de Windows Mixed Reality (XR. WSA. Entrada).</span><span class="sxs-lookup"><span data-stu-id="05553-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="05553-107">Sin embargo, los botones A, B, X, y y el desencadenador de apriete no son accesibles actualmente a través del administrador de entrada a menos que esté usando SteamVR.</span><span class="sxs-lookup"><span data-stu-id="05553-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="05553-108">La compatibilidad con las entradas de la reverberación G2 adicional estará disponible en un futuro próximo, así que asegúrese de volver a consultar.</span><span class="sxs-lookup"><span data-stu-id="05553-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="05553-109">Trasladar aplicaciones existentes</span><span class="sxs-lookup"><span data-stu-id="05553-109">Porting existing applications</span></span>

<span data-ttu-id="05553-110">Si ya tiene una aplicación existente que está desarrollando para los auriculares con un solo casco con Windows Mixed Reality, consulte nuestra [Guía de migración](../porting-apps/porting-guides.md) y las secciones de configuración del [proyecto](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) para obtener sugerencias generales.</span><span class="sxs-lookup"><span data-stu-id="05553-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="05553-111">Entrada de asignación</span><span class="sxs-lookup"><span data-stu-id="05553-111">Mapping input</span></span>

<span data-ttu-id="05553-112">Cuando esté listo para poner en marcha la asignación de entrada para los nuevos controladores, comience en la sección [asignación de entrada](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) de la guía de portabilidad envolvente.</span><span class="sxs-lookup"><span data-stu-id="05553-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="05553-113">Las instrucciones sobre cómo configurar entradas en Unity se detallan en [gestos y controladores de movimiento](gestures-and-motion-controllers-in-unity.md), junto con un [botón completo y una tabla de asignación de ejes](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) como referencia.</span><span class="sxs-lookup"><span data-stu-id="05553-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="05553-114">Consulte también</span><span class="sxs-lookup"><span data-stu-id="05553-114">See also</span></span>
* [<span data-ttu-id="05553-115">Actualización para SteamVR</span><span class="sxs-lookup"><span data-stu-id="05553-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)