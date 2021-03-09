---
title: ScreenshotUtility
description: Documentación sobre cómo usar la herramienta de captura de pantalla en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: a1f5e6503244852d79abaf143f8e922ceb1b489c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101770738"
---
# <a name="screenshot-utility"></a>Utilidad de captura de pantalla

A menudo, la obtención de capturas de pantallas en Unity para documentación e imágenes promocionales puede ser agobiante, y el resultado en general no es el deseable. Aquí es donde entra en juego la clase `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility).

La clase ScreenshotUtility ayuda a obtener capturas de pantallas a través de elementos de menú y API públicas en el editor de Unity. Las capturas de pantallas se pueden obtener en distintas resoluciones y con colores transparentes para su uso en la composición sencilla de imágenes. Esta herramienta no admite la obtención de capturas de pantallas de una compilación independiente.

## <a name="taking-screenshots"></a>Obtención de capturas de pantallas

Para obtener capturas de pantalla fácilmente, en el editor seleccione *Mixed Reality Toolkit -> Utilities -> Take Screenshot* (Mixed Reality Toolkit -> Utilidades -> Obtener captura de pantalla) y, luego, la opción que quiera. Asegúrese de que la pestaña de la ventana de juego esté visible si obtiene la captura de pantalla mientras no está jugando, o es posible que no se guarde una captura.

De manera predeterminada, todas las capturas de pantalla se guardan en la [ruta de acceso de caché temporal](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html); la ruta de acceso a la captura de pantalla se mostrará en la consola de Unity.

![Elemento de menú de la utilidad de captura de pantalla](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Ejemplo de captura de pantalla

La captura de pantalla siguiente se obtuvo con la opción *4x Resolution (Transparent Background)* (Resolución 4x [fondo transparente]). Esto genera una imagen de alta resolución, donde los píxeles que normalmente se representan con el color transparente se guardan como píxeles transparentes. Esta técnica ayuda a los desarrolladores a presentar su aplicación para la tienda, u otros medios de distribución multimedia, superponiendo esta imagen encima de otras imágenes.

![Ejemplo de captura de la utilidad de captura de pantalla](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
