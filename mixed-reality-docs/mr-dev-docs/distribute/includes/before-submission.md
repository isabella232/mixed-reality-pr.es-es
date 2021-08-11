---
ms.openlocfilehash: d811df7f0dbd7c44a5135ed82c9061e19c1335e3e23dda6398562317f7ee8861
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198795"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Si tiene una aplicación HoloLens, elija la opción de [distribución que prefiera](../distribute-overview.md#distribution-options) en la tabla siguiente. Si va a publicar en el Microsoft Store, tiene la opción de agregar compras desde la aplicación [para](../in-app-purchases.md) monetizar el contenido.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Si está trabajando con una aplicación envolvente que tiene como destino un casco Windows Mixed Reality, [](../distribute-overview.md#distribution-options) cree un iniciador de aplicaciones 3D y, a continuación, elija la opción de distribución que prefiera en la tabla siguiente. Si va a publicar en el Microsoft Store, tiene la opción de agregar compras desde la aplicación [para](../in-app-purchases.md) monetizar el contenido.

### <a name="designing-3d-app-launchers-for-vr"></a>Diseño de iniciadores de aplicaciones 3D para VR 

Los iniciadores de aplicaciones 3D aparecen como objetos en el Windows Mixed Reality inicio que aparece cada vez que un usuario coloca un casco envolvente. Estos objetos son los que se pueden crear y personalizar como quiera, pero se recomienda comenzar con nuestro artículo de guía de diseño para obtener el resalte de los procedimientos de diseño recomendados, como el escalado, el tipo, la elección de color, el texturing y, sobre todo, que se destaura en un entorno virtual. [](../3d-app-launcher-design-guidance.md)

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modelado y exportación de iniciadores de aplicaciones 3D

Una vez que se haya establecido en la idea del iniciador de aplicaciones 3D, debe asegurarse de que cumple los requisitos de Microsoft Store, incluido el formato de archivo de recursos, el recuento de triángulos, los tamaños de textura, la longitud de la animación y la optimización de recursos. Este proceso puede ser muy técnico, por lo que se recomienda usar nuestro artículo de creación de modelos [3D](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para marcar todas las casillas. Los recursos que no cumplan esta especificación de creación no se representarán en el Windows Mixed Reality inicio.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Incorporación de iniciadores de aplicaciones 3D en las aplicaciones

Después de asegurarse de que el iniciador de aplicaciones 3D cumple las directrices de creación de Windows Mixed Reality, se puede usar para invalidar el iniciador 2D predeterminado para la aplicación en el entorno principal de Windows Mixed Reality. El proceso de integración de un iniciador de aplicaciones 3D en la aplicación depende del tipo de aplicación que se está desarrollando:

* [Aplicaciones para UWP](../implementing-3d-app-launchers.md)
* [Aplicaciones de Win32](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>[Opcional] Colocación de modelos 3D en el Windows Mixed Reality inicio

Como ventaja adicional, algunas aplicaciones 2D permiten colocar modelos 3D directamente en la casa de Windows Mixed Reality como decoración o para una inspección posterior en 3D completo. El protocolo agregar modelo le permite enviar un modelo 3D desde su sitio web o aplicación a la página principal de Windows Mixed Reality, donde persistirá como los iniciadores de aplicaciones 3D, las aplicaciones 2D y los hologramas. Consulte cómo [colocar modelos 3D](../enable-placement-of-3d-models-in-the-home.md) en el Windows Mixed Reality principal para obtener más detalles e instrucciones sobre cómo crear sus propias aplicaciones.