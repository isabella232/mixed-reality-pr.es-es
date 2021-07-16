---
title: Contribución a MRTK
description: Cómo contribuir a la Mixed Reality Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, informe de errores,
ms.openlocfilehash: b79f69cbb6dea1201c88d9fd1a354967ce40735e
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282042"
---
# <a name="contributing-to-mrtk"></a>Contribución a MRTK

El Mixed Reality Toolkit (MRTK) agradece las contribuciones de la comunidad. Todos los cambios, ya sean pequeños o grandes, deben cumplir los estándares de codificación [MRTK,](coding-guidelines.md)por lo que debe asegurarse de que está familiarizado con estos durante el desarrollo para evitar retrasos cuando se está revisando el cambio.

Si tiene alguna pregunta, póngase en contacto con el canal [mixed-reality-toolkit en Slack.](https://holodevelopers.slack.com/messages/C2H4HT858)
Puede unirse a la comunidad de Slack a través del [remitente de invitación automática](https://holodevelopersslack.azurewebsites.net/).

## <a name="submission-process"></a>Proceso de envío

Proporcionamos varias rutas de acceso para permitir que los desarrolladores contribuyan a la Mixed Reality Toolkit, empezando por [crear un nuevo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

Desde aquí, archivo:

- **Informe de errores:** problema de funcionalidad con uno de los componentes Mixed Reality Toolkit errores
- **Problema de documentación:** problema con la documentación Mixed Reality Toolkit [documentación](https://microsoft.github.io/MixedRealityToolkit-Unity)
- **Solicitud de características:** propuesta para una nueva Mixed Reality Toolkit característica

## <a name="proposing-feature-requests"></a>Solicitudes de características de propuesta

Al solicitar una nueva Mixed Reality Toolkit, es importante documentar la ventaja o el problema del cliente que se va a resolver. Una vez enviada, se revisará y analizará una solicitud de característica en GitHub. Animamos a una discusión abierta y provechosa de cada propuesta de característica para garantizar que el trabajo sea beneficioso para un gran segmento de clientes.

Para evitar tener que volver a trabajar con la característica, por lo general se recomienda que el desarrollo de la característica no comience durante la fase de revisión. Muchas veces, el proceso de revisión de la comunidad descubre uno o varios problemas que pueden requerir cambios significativos en la implementación propuesta.

> [!NOTE]
> Si desea trabajar en algo que ya existe en nuestro trabajo pendiente, puede usar ese elemento de trabajo como propuesta. Asegúrese también de comentar la tarea notificando a los encargados de mantenimiento que está trabajando para completarla.

## <a name="contribution-process"></a>Proceso de contribución

Para empezar, simplemente siga estos pasos:

1. Bifurque el repositorio. Haga clic en el botón "Bifurcar" en la parte superior derecha de la página y siga el flujo.
1. Cree una rama en la bifurcación (fuera de la rama principal) para que sea más fácil aislar los cambios hasta que esté listo para el envío. [](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) Para obtener correcciones de errores durante un período de estabilización de versión, busque la rama más `prerelease/*` reciente. Las nuevas características siempre deben ir a `main` .

Si no está nuevo en el flujo de trabajo de Git, [consulte esta introducción desde Github](https://guides.github.com/activities/hello-world/).

Al agregar una corrección de errores o una característica, siga estos pasos:

1. Implemente la corrección de errores o la característica. Las instrucciones para compilar e implementar MRTK se [encuentran en Implementación en dispositivos Hololens y WMR.](../supported-devices/wmr-mrtk.md) No olvide seguir las instrucciones [de codificación](../contributing/coding-guidelines.md).
1. Si agrega una característica, agregue también una escena de ejemplo que muestra la característica.
1. Si agrega una característica experimental, no es necesario escribir pruebas ni documentación. En su lugar, siga [las directrices de características experimentales](../contributing/experimental-features.md).
1. Agregue pruebas para comprobar la corrección de errores o la característica. Las instrucciones para escribir y ejecutar pruebas se encuentran [en UnitTests](../contributing/unit-tests.md).
1. Asegúrese de que el código y las características están documentados como se describe en las [directrices de documentación](../contributing/documentation-guide.md).
1. Asegúrese de que el código funciona según lo previsto en todas las plataformas. Consulte las [notas de la versión](../release-notes/mrtk-26-release-notes.md) para obtener la lista de plataformas admitidas. Para Windows proyectos de UWP, el código debe ser [compatible con WACK.](https://developer.microsoft.com/windows/develop/app-certification-kit) Para ello, genere una solución Visual Studio, haga clic con el botón derecho en el proyecto; **Almacén**  >  **Crear paquetes de aplicación.** Siga las indicaciones y ejecute pruebas WACK. Asegúrese de que todos se realicen correctamente.
1. Siga las instrucciones de [Solicitudes de extracción](../contributing/pull-requests.md) al realizar una solicitud de extracción.
