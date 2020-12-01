---
ms.openlocfilehash: c9ce068adc3b4b550ecaf1b1c106d9b12f363ac0
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443498"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Si tiene una aplicación de HoloLens, elija la [opción de distribución](../distribute-overview.md#distribution-options) que prefiera en la tabla siguiente. Si está publicando en el Microsoft Store, tiene la opción de agregar [compras desde la aplicación](../in-app-purchases.md) para rentabilizar el contenido.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Si está trabajando con una aplicación envolvente destinada a un casco de Windows Mixed Reality, cree un iniciador de aplicaciones 3D y, después, elija la [opción de distribución](../distribute-overview.md#distribution-options) preferida en la tabla siguiente. Si está publicando en el Microsoft Store, tiene la opción de agregar [compras desde la aplicación](../in-app-purchases.md) para rentabilizar el contenido.

### <a name="designing-3d-app-launchers-for-vr"></a>Diseño de iniciadores de aplicaciones 3D para VR 

los iniciadores de aplicaciones 3D aparecen como objetos en el entorno de inicio de Windows Mixed Reality que aparece siempre que un usuario se pone en un casco envolvente. Estos objetos son de su elección para crear y personalizar, pero le recomendamos que comience con nuestro artículo de la [Guía de diseño](../3d-app-launcher-design-guidance.md) para obtener el bloqueo de buenas prácticas de diseño, como el escalado, el tipo, la elección del color, la texturización y sobre todo, lo que hace que se resalte en un entorno virtual.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modelado y exportación de iniciadores de aplicaciones 3D

Una vez que haya establecido la idea del iniciador de aplicaciones 3D, debe asegurarse de que cumple los requisitos Microsoft Store, como el formato de archivo de recursos, el recuento de triángulos, los tamaños de textura, la duración de la animación y la optimización de recursos. Este proceso puede ser muy técnico, por lo que se recomienda usar nuestro artículo de [creación de modelos 3D](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para activar todas las casillas. Los activos que no cumplan esta especificación de creación no se representarán en la Página principal de Windows Mixed Reality.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Incorporación de iniciadores de aplicaciones 3D en las aplicaciones

Una vez que se haya asegurado de que el iniciador de aplicaciones 3D cumple las directrices de creación de la realidad mixta de Windows, se puede usar para invalidar el iniciador de 2D predeterminado de la aplicación en el entorno de inicio de Windows Mixed Reality. El proceso de integración de un iniciador de aplicaciones 3D en la aplicación depende del tipo de aplicación que se está desarrollando:

* [Aplicaciones para UWP](../implementing-3d-app-launchers.md)
* [Aplicaciones de Win32](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>Opta Colocar modelos 3D en la Página principal de Windows Mixed Reality

Como ventaja adicional, algunas aplicaciones 2D permiten colocar modelos 3D directamente en la Página principal de Windows Mixed Reality como decoración o para realizar más inspecciones en 3D completo. El protocolo agregar modelo le permite enviar un modelo 3D desde su sitio web o aplicación a la Página principal de Windows Mixed Reality, donde se conservará como iniciadores de aplicaciones 3D, aplicaciones 2D y hologramas. Consulte [Cómo colocar modelos 3D en la Página principal de Windows Mixed Reality](../enable-placement-of-3d-models-in-the-home.md) para encontrar más detalles e instrucciones sobre cómo vivir sus propias aplicaciones.