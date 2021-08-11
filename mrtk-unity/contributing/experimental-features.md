---
title: Características experimentales
description: Documento relacionado con las características experimentales de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 9b7ef7564e0e4f84ba70c034b1bcc33a29498432620a002c8509de518dde479c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228395"
---
# <a name="experimental-features"></a>Características experimentales

Algunas características en las que trabaja el equipo de MRTK parecen tener una gran cantidad de valor inicial, aunque no hayamos aprendido por completo los detalles. Para estos tipos de características, queremos que la comunidad pueda verlas pronto. Dado que están al principio del ciclo, las etiquetamos como experimentales para indicar que siguen evolucionando y sujetas a cambios con el tiempo.

## <a name="what-to-expect-from-an-experimental-feature"></a>Qué esperar de una característica experimental

Si un componente está marcado como experimental, puede esperar lo siguiente:

- Una escena de ejemplo que muestra el uso, ubicada en `MRTK/Examples/Experimental` la sub carpeta
- Es posible que las características experimentales no tengan documentos.
- Probablemente no tengan pruebas.
- Las características experimentales están sujetas a cambios.

## <a name="experimental-feature-guidelines"></a>Directrices de características experimentales

### <a name="experimental-code-should-live-in-a-separate-folder"></a>El código experimental debe estar en una carpeta independiente

El código experimental debe ir a una carpeta experimental de nivel superior seguida del nombre de la característica experimental. Por ejemplo, si intenta contribuir con una nueva característica FooBar, coloque el código en lo siguiente:

- Escenas de ejemplo en las que los scripts van a `MRTK/Examples/Experimental/FooBar/`
- Los scripts de componentes, los elementos prefabs van a `MRTK/SDK/Experimental/FooBar/`
- Los inspectores de componentes van a `MRTK/SDK/Inspectors/Experimental/FooBar`

Al usar subcarpetas con el nombre de característica experimental, intente reflejar la misma estructura de carpetas de MRTK.

Por ejemplo, los solucionadores entrarían en `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

Mantenga las escenas en una carpeta de escena cerca de la parte superior: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> Se consideró no tener una sola carpeta raíz experimental y, en su lugar, colocar Experimental en , por `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` ejemplo, . Hemos decidido ir con carpetas en la base para facilitar la descución de las características experimentales.

### <a name="experimental-code-should-be-in-a-special-namespace"></a>El código experimental debe estar en un espacio de nombres especial

Asegúrese de que el código experimental reside en un espacio de nombres experimental que coincida con la ubicación no experimental. Por ejemplo, si el componente forma parte de solucionadores en `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , su espacio de nombres debe ser `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .

Consulte [esta PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) para obtener un ejemplo.

### <a name="experimental-features-should-have-an-experimental-attribute"></a>Las características experimentales deben tener un atributo [Experimental]

Agregue un atributo encima de uno de los campos para que aparezca un cuadro de diálogo pequeño en el editor de componentes que mencione que la característica es experimental y `[Experimental]` está sujeta a cambios significativos.

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>Los menús de las características experimentales deben ir en el submenú "Experimental".

Asegúrese de que las características experimentales están en submenúes "experimentales" al agregar comandos a los menús del editor. Estos son algunos ejemplos:

Agregar un comando de menú de nivel superior:

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

Agregar un menú de componentes:

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>Documentación

Siga estos pasos para agregar documentación para la característica experimental:

1. Cualquier documentación de una característica experimental debe ir en un `readme.md` archivo de la carpeta experimental. Por ejemplo, MRTK/SDK/Experimental/PulseShader/readme.md.

1. En *Información general de características,* agregue un vínculo en la sección *Experimental* de [`Documentation/toc.yml`](../toc.yml) .

### <a name="minimize-impact-to-mrtk-code"></a>Minimizar el impacto en el código MRTK

Aunque el cambio de MRTK puede hacer que el experimento funcione, podría afectar a otras personas de maneras que no se esperan.
Cualquier regresión que realice en el código principal de MRTK daría lugar a la reversión de la solicitud de extracción.

El objetivo es tener cero cambios en carpetas que no son carpetas experimentales. Esta es una lista de carpetas que pueden tener cambios experimentales:

- MRTK/SDK/Experimental
- MRTK/SDK/Inspectors/Experimental
- MRTK/Examples/Experimental

Los cambios fuera de estas carpetas deben tratarse con mucho cuidado. Si la característica experimental debe incluir cambios en el código principal de MRTK, considere la posibilidad de dividir los cambios de MRTK en una solicitud de extracción independiente que incluya pruebas y documentación.

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>El uso de la característica experimental no debería afectar a la capacidad de las personas de usar controles principales

La mayoría de las personas usan componentes principales de la experiencia de usuario, como el botón ManipulationHandler e Interactable con mucha frecuencia. Es probable que no usen la característica experimental si impide que usen botones.

El uso del componente no debe interrumpir botones, ManipulationHandler, BoundingBox ni interactables.

Por ejemplo, en esta PR [ScrollableObjectCollection](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), al agregar scrollableObjectCollection, los usuarios no pudieron usar los elementos prefabs del botón HoloLens de texto. Aunque esto no fue causado por un error en la PR (sino que expuso un error existente), impidió que la PR se registrase.

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>Proporcionar una escena de ejemplo que muestra cómo usar la característica

Los usuarios deben ver cómo usar la característica y cómo probarla.

Proporcione un ejemplo en MRTK/Examples/Experimental/YOUR_FEATURE

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>Minimizar los errores visibles del usuario en las características experimentales

Otros no usarán la característica experimental si no funciona, no se graduará a una característica.

Pruebe la escena de ejemplo en la plataforma de destino y asegúrese de que funciona según lo previsto. Asegúrese de que la característica también funciona en el editor, para que los usuarios puedan iterar rápidamente y ver la característica incluso si no tienen la plataforma de destino.

## <a name="graduating-experimental-code-into-mrtk-code"></a>Pasar código experimental al código MRTK

Si una característica termina viendo bastante uso, debemos convertirla en código MRTK básico. Para ello, la característica debe tener pruebas, documentación y una escena de ejemplo.

Cuando esté listo para licenciar la característica MRTK, cree un problema con el que comprobar la pr. La pr. debe incluir todo lo necesario para que esta sea una característica principal: pruebas, documentación y una escena de ejemplo que muestre el uso.

Además, no olvide actualizar los espacios de nombres para quitar el subespacio "Experimental".
