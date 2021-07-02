---
title: Ventana Dependencia
description: Documentación sobre el uso de la ventana de dependencia en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176667"
---
# <a name="dependency-window"></a>Ventana Dependencia

En Unity, a menudo es difícil deducir qué recursos se usan y qué hace referencia a ellos. La opción "Buscar referencias en la escena" funciona muy bien cuando solo está interesado en la escena actual, pero ¿qué ocurre con todo el proyecto de Unity? Aquí es donde **la ventana de dependencia** (Assets/MRTK/Tools/DependencyWindow) puede ser útil.

La ventana Dependencia muestra cómo los recursos hacen referencia y dependen entre sí. Las dependencias se calculan analizando guides dentro de los archivos YAML del proyecto (no se tienen en cuenta las dependencias de script a script).

## <a name="usage"></a>Uso

Para abrir la ventana, seleccione **Mixed Reality** Toolkit Ventana de dependencia de utilidades, que abrirá la ventana y comenzará automáticamente a compilar el gráfico de  >    >    >   dependencias del proyecto. Una vez creado el gráfico de dependencias, puede seleccionar recursos en la pestaña del proyecto para inspeccionar sus dependencias.

![Ventana Dependencia](../images/dependency-window/MRTK_Dependency_Window.png)

La ventana muestra una lista de recursos de los que depende el recurso seleccionado actualmente y una lista jerárquica de recursos que dependen de él. Si nada depende del recurso seleccionado actualmente, puede considerar la posibilidad de eliminarlo del proyecto (tenga en cuenta que algunos recursos se cargan mediante programación a través de API como Shader.Find() y es posible que el seguimiento de dependencias no lo descubra).

La ventana también puede mostrar solo una lista de todos los recursos a los que no hace referencia ningún otro activo y que se podrían considerar para su eliminación:

![Ventana de dependencia que muestra los recursos sin referencia](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> Si los recursos se modifican, agregan o quitan mientras la ventana de dependencia está en uso, se recomienda actualizar el gráfico de dependencias para obtener los resultados más "actualizados".
