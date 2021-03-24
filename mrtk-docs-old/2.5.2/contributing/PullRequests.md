---
title: PullRequests
description: Detalles relacionados con las solicitudes de incorporación de cambios.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, PR,
ms.openlocfilehash: 31db19154adbf7016aec609e7baca8c4fa3eda48
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683468"
---
# <a name="pull-requests"></a>Solicitudes de incorporación de cambios

## <a name="prerequisites"></a>Requisitos previos

Si no ha contribuido a ningún proyecto de Microsoft antes, es posible que se le pida que firme un [contrato de licencia de contribución](https://cla.microsoft.com/).
Un comentario en la solicitud de incorporación de cambios le indicará si debe hacerlo.

> [!IMPORTANT]
> Si es un empleado de Microsoft y no es miembro de la [organización de Microsoft en GitHub](https://github.com/Microsoft), vincule sus cuentas de Microsoft y GitHub en la red corporativa. Para hacerlo, visite [Open Source en Microsoft](https://opensource.microsoft.com/) antes de iniciar la solicitud de incorporación de cambios. Antes de empezar, debe seguir algunos pasos de procesamiento.

## <a name="creating-a-pull-request"></a>Crear una solicitud de incorporación de cambios

Cuando esté listo para enviar una solicitud de incorporación de cambios, [créela](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1) orientada a la rama [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development).

Lea las instrucciones y asegúrese de que se respetan en la solicitud de incorporación de cambios.

* Asegúrese de hacer referencia a cualquier problema, solicitud de característica o tarea que guarde relación con la solicitud de incorporación de cambios.
* Compruebe que la solicitud de incorporación de cambios solo contiene los archivos o cambios correspondientes a la solicitud en cuestión.
* Compruebe que la documentación está actualizada y se incluye. Compruebe que todos los campos públicos tienen comentarios.
* Si agrega una nueva característica, compruebe que se incluyen las pruebas para validarla (consulte [UnitTests](UnitTests.md)).
* Si se corrige un error, escriba una prueba para comprobar la corrección.

Los responsables del mantenimiento del proyecto revisarán los cambios. Nuestro objetivo es revisar todos los cambios en un plazo de tres días hábiles. Aborde cualquier comentario de revisión, envíe cambios a la rama puntual y publique un comentario para indicarnos si hay algo nuevo que revisar.

> [!NOTE]
> Todas las solicitudes de incorporación de cambios que se envíen al proyecto también se revisarán de acuerdo con la [Guía de estándares de programación de MRTK](CodingGuidelines.md), por lo que debe revisarlas antes de enviarlas para garantizar un proceso sin complicaciones.

## <a name="pull-request-guidelines"></a>Instrucciones para las solicitudes de incorporación de cambios

Estas instrucciones se basan en las [prácticas de ingeniería de Google](https://google.github.io/eng-practices/review/developer/small-cls.html).

### <a name="keep-pull-requests-small"></a>Las solicitudes de incorporación de cambios deben ser pequeñas

Las solicitudes de incorporación de cambios más pequeñas se revisan más rápidamente y en detalle, son menos propensas a errores y más fáciles de revertir y combinar.

Las solicitudes de incorporación de cambios deben ser lo suficientemente pequeñas como para que un ingeniero pueda revisarlas en menos de 30 minutos. Intente realizar un cambio mínimo que corrija solo una cosa. Si necesita crear una gran solicitud de incorporación de cambios, divídala en varias para la rama local o para una rama de características de MRTK. Evite agregar nuevos recursos (p. ej., fbx, archivos .obj) y, en su lugar, intente volver a usar los recursos existentes.

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>Las pruebas deben agregarse en la misma solicitud de incorporación que su corrección/característica, excepto en casos de emergencia.

Las pruebas son la mejor manera de asegurarse de que los cambios no retrasen el código existente, pero también es fácil olvidarse de las pruebas al enviar solicitudes de incorporación de cambios. Requerir que pasen por su solicitud de incorporación de cambios es una excelente manera de asegurarse de que las pruebas se escriben.

Todas las características y correcciones de errores deben tener pruebas asociadas. Si no tiene experiencia o tiempo para escribir una prueba, cree un problema para escribir las pruebas y márquelo con la etiqueta **Considerar para la iteración actual**.

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>La documentación debe agregarse en la misma solicitud de incorporación de cambios que una característica o corrección.

La mayoría de los desarrolladores buscan primero en la documentación, no en el código, para comprender cómo usar una característica. Asegurarse de que la documentación está actualizada hace que sea mucho más fácil para los usuarios consumir MRTK y confiar en este.  La documentación siempre debe empaquetarse con incorporación de cambios relacionadas para garantizar que los elementos están actualizados y son coherentes.

Asegúrese de que cada propiedad, método y campo públicos tienen [comentarios de resumen de barra diagonal triple](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) para que nuestro sitio de docfx pueda generar descripciones de campos o métodos. Si es necesario, actualice los archivos de Markdown en la carpeta de documentación.

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>Las descripciones de solicitudes de incorporación de cambios deben describir los cambios claramente y de forma completa.

Las descripciones claras y completas de las solicitudes de incorporación de cambios garantizan que los revisores entienden lo que están revisando.

Si agrega características que contienen la experiencia de usuario, agregue una imagen o GIF de la característica que está cambiando. [Este es un buen ejemplo](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532). Otra sugerencia es tener un GIF de antes y después; [por ejemplo, en esta solicitud de incorporación de cambios](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896). Una herramienta que se recomienda para generar archivos GIF a partir de capturas de pantalla es [ScreenToGif](https://www.screentogif.com/).
