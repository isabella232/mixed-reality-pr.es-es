---
title: Cambios importantes
description: Directiva relacionada con los cambios importantes en MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 46e3061319140a561d267983d4d170eea937fd28b7d3e833c3382c1e37a70392
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191539"
---
# <a name="breaking-changes"></a>Últimos cambios

Los consumidores de MRTK dependen de tener una superficie de API de versión a versión estable, para que puedan realizar actualizaciones de MRTK sin tener cambios importantes cada vez.

En esta página se describe nuestra directiva actual con respecto a los cambios importantes en MRTK, junto con algunos objetivos a largo plazo en torno a cómo podemos administrar mejor el equilibrio entre mantener bajos los cambios importantes y poder realizar los cambios técnicos a largo plazo correctos en el código.

## <a name="what-is-a-breaking-change"></a>¿Qué es un cambio importante?

Un cambio es un cambio importante si cumple cualquiera de las condiciones de la lista [A](#list-a) Y cumple todas las condiciones de la [lista B.](#list-b)

### <a name="list-a"></a>Lista A

- La adición, eliminación o actualización de cualquier miembro o función de cualquier interfaz (o eliminación o cambio de nombre de toda la interfaz).
- Eliminación, actualización (cambio de tipo o definición, hacer privado o interno) de cualquier miembro o función pública o protegido de la clase. (o eliminación o cambio de nombre de toda la clase).
- Cambio en el orden de los eventos desencadenados por una clase.
- El cambio de nombre de cualquier serializedField privado (sin una etiqueta FormerlySerializedAs correspondiente) o propiedad pública en un scriptableObject (especialmente cambios en los perfiles).
- Cambiar el tipo de un campo en scriptableObject (especialmente cambios en los perfiles).
- Actualizaciones del espacio de nombres o las definiciones de cualquier clase o interfaz.
- Eliminación de cualquier prefab o eliminación de un script en el objeto de nivel superior de un objeto prefab.

### <a name="list-b"></a>Lista B

- El recurso en cuestión está en el paquete de base (es decir, se encuentra en una de las carpetas siguientes):

  - MRTK/Core
  - MRTK/Providers/
  - MRTK/Services/
  - MRTK/SDK/
  - MRTK/Extensions

- El recurso en cuestión no pertenece al espacio de nombres experimental.

> [!IMPORTANT]
> Cualquier recurso que se encuentra en el paquete de ejemplos (es decir, parte de la carpeta MRTK/Examples/) está sujeto a cambios en cualquier momento, ya que los recursos están diseñados para que los consumidores los copien y los vean como "implementaciones de referencia", pero no forman parte del conjunto principal de API y recursos. Los recursos del espacio de nombres experimental (o, más generalmente, las características etiquetadas como experimentales) son los que se publican antes de que se haya realizado toda la debida diligencia (es decir, pruebas, iteración de la experiencia de usuario, documentación) y se publican pronto para obtener comentarios antes.  Sin embargo, dado que no tienen pruebas y documentación, y como es probable que no hayamos eliminado todas las interacciones y diseños, las publicamos en un estado en el que el público debe asumir que pueden y cambiarán (es decir, se modifican, se quitan completamente, etc.).
>
> Consulte [Características experimentales](../contributing/experimental-features.md) para obtener más información.

Dado que el área de superficie para los cambios importantes es muy grande, es importante tener en cuenta que tener una regla absoluta que dice "no hay cambios importantes" sería imposible; puede haber problemas que solo se puedan solucionar de forma sanea al tener un cambio importante. En otras palabras, la única manera de que realmente podamos tener "ningún cambio importante" es no tener ningún cambio.

Nuestra directiva permanente es evitar realizar cambios importantes si es posible y solo hacerlo si el cambio acumularía un valor significativo a largo plazo para el cliente o el marco.

## <a name="what-to-do-about-breaking-changes"></a>Qué hacer con los cambios importantes

Si es posible realizar algo sin un cambio importante y sin poner en peligro la estructura a largo plazo y la viabilidad de la característica, no realice el cambio importante. Si no hay otra manera, la directiva actual es evaluar cada cambio importante individual, para comprender si la ventaja de tomar el cambio supera el costo para el consumidor de la absorbencia del cambio. El debate sobre lo que merece la pena hacer y lo que no suele tener lugar en la PR o en la propia discusión de problemas.

Lo que puede ocurrir aquí se divide en varios depósitos:

### <a name="the-breaking-change-adds-value-but-could-be-written-in-a-way-that-isnt-breaking"></a>El cambio importante agrega valor, pero podría escribirse de una manera que no sea importante.

Por [ejemplo,](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4882) esta solicitud de participación agregó una nueva característica que se escribió inicialmente de una manera que se estaba separando (modificó una interfaz existente), pero luego se reescribía donde la característica se desglosaba como su propia interfaz. Este suele ser el mejor resultado posible. No intente forzar un cambio en una forma sin separación si esto pone en peligro la viabilidad o la estructura a largo plazo de la característica.

### <a name="the-breaking-change-adds-sufficient-value-to-the-customer-that-its-worth-doing"></a>El cambio importante agrega un valor suficiente al cliente que merece la pena hacer.

Documente cuáles son los cambios importantes y proporcione la mejor mitigación posible (es decir, pasos prescriptivos sobre cómo migrar o, mejor aún, herramientas que se migrarán automáticamente para el cliente). Cada versión puede contener una pequeña cantidad de cambios importantes, que siempre se deben documentar en documentos como se hizo en [esta pr.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4858) Si ya hay una guía de migración 2.x.x→2.x+1.x+1, agregue instrucciones o herramientas a ese documento. Si no existe, cándalo.

### <a name="the-breaking-change-adds-value-but-the-customer-pain-would-be-too-high"></a>El cambio importante agrega valor, pero el daño del cliente sería demasiado alto.

No todos los tipos de cambios importantes se crean iguales; algunos son significativamente más difíciles que otros, en función de nuestra experiencia y en función de las experiencias de los clientes. Por ejemplo, los cambios en las interfaces pueden ser difíciles, pero si el cambio importante es aquel en el que es poco probable que un cliente se haya ampliado o implementado en el pasado (por ejemplo, el sistema de visualización de diagnóstico), el costo real probablemente sea bajo o nada. Sin embargo, si el cambio es el tipo de un campo en un scriptableObject (por ejemplo, en uno de los perfiles principales de MRTK), es probable que esto cause un gran problema al cliente. Los clientes ya han clonado el perfil predeterminado, combinar o actualizar perfiles puede ser muy difícil de hacer manualmente (es decir, a través de un editor de texto durante el tiempo de combinación) y volver a copiar el perfil predeterminado y volver a configurarlo manualmente es muy probable que lleve a regresión difíciles de depurar.

Estos cambios tenemos que volver a colocar en el espacio hasta que exista una rama que permita cambios importantes (junto con un valor significativo que dará a los clientes una razón para actualizar). Esta rama no existe actualmente. En nuestras futuras reuniones de planeamiento de iteraciones, revisaremos el conjunto de cambios o problemas que eran "demasiado importantes" para ver si alcanzamos una masa crítica para que sea razonable llevar a cabo un conjunto de cambios a la vez. Tenga en cuenta que es peligroso crear una rama "todo está permitido" sin realizar la debida diligencia debido a los limitados recursos de ingeniería que tenemos y al hecho de que tendríamos que dividir las pruebas y la validación entre esos dos. Debe haber un propósito claro y una fecha de inicio y finalización bien comunicada de dicha rama cuando exista.

## <a name="long-term-management-of-breaking-changes"></a>Administración a largo plazo de cambios importantes

A largo plazo, debemos intentar reducir el ámbito de lo que es un cambio importante al aumentar el conjunto de condiciones de la [lista B.](#list-b) A partir de ahora, el conjunto de elementos de la lista [A](#list-a) siempre será técnicamente muy completo para el conjunto de archivos y recursos que consideramos que están en la "superficie de API pública". La manera en que podemos obtener un poco más de libertad para la iteración (es decir, cambiar los detalles internos de la implementación, lo que permite una refactorización y un uso compartido más sencillos del código entre varias clases, etc.) es ser más explícitos sobre qué partes del código son superficie oficial, en lugar de detalles de implementación.

Algo que ya hemos hecho es presentar el concepto de una característica "experimental" (pertenece al espacio de nombres experimental, es posible que no tenga pruebas o documentación y que exista públicamente, pero que se pueda quitar y actualizar sin previo aviso). Esto ha dado libertad para agregar nuevas características antes para obtener comentarios anteriores, pero no estar vinculado inmediatamente a su superficie de API (porque es posible que no hayamos pensado completamente la superficie de la API).

### <a name="other-examples-of-things-that-could-help-in-the-future"></a>Otros ejemplos de cosas que podrían ayudar en el futuro

- Uso de la [palabra clave internal](/dotnet/csharp/language-reference/keywords/internal).
  Esto nos permitiría tener código compartido dentro de nuestros propios ensamblados (para reducir la duplicación de código) sin hacer que las cosas se haga públicas para los consumidores externos.
- Creación de un espacio de nombres "interno" (es decir, Microsoft.MixedReality.Toolkit. Internal.Utilities), donde se documenta públicamente que todo lo contenido dentro de ese espacio de nombres interno está sujeto a cambios en cualquier momento y se podría quitar, etc. Esto es similar a cómo las bibliotecas de encabezados de C++ usarán los espacios de nombres ::internal para ocultar sus detalles de implementación.
