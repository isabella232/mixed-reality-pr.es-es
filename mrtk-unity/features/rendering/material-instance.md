---
title: Instancia de material
description: Documentación sobre la instancia de material y sus usos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, MaterialInstance,
ms.openlocfilehash: 6d9a2a35a009bfce1fcfae15000ea02c47be637a8c5a483254ea30d9948922e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210055"
---
# <a name="material-instance"></a>Instancia de material

Los asistentes de comportamiento en el seguimiento de la duración del material de la instancia destruyen automáticamente los [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) materiales de instancia para el usuario. Este componente de utilidad se puede usar como reemplazo de [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) o [Renderer.materials.](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) es preferible a la creación de instancias de material, pero no siempre están disponibles en todos los escenarios.

¿Por qué [el uso de Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) puede ser un problema? Si agrega el código siguiente a una escena de Unity y pulsa el uso de memoria de reproducción, el uso de la memoria seguirá siendo desparpase y se verá afectado:

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> El comportamiento de pérdida **anterior bloqueará Unity** si se ejecutó durante demasiado tiempo.

Como alternativa, pruebe a usar el [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamiento:

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a>Uso

Al invocar [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) de Unity, Unity crea automáticamente instancias de nuevos materiales. Es responsabilidad del autor de la llamada destruir los materiales cuando ya no se necesita un material o se destruye el objeto del juego. El [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamiento ayuda a evitar pérdidas de material y mantiene las rutas de asignación de material coherentes durante el tiempo de edición y ejecución.

Cuando [no se puede usar MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) y se debe crear una instancia de un material, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) se puede usar de la siguiente manera:

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

Si varios objetos necesitan la propiedad de la instancia de material, es mejor tomar posesión explícita para el seguimiento de referencias. (Existe una interfaz opcional [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) llamada para ayudar con la propiedad). A continuación se muestra un ejemplo de uso:

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

Para más información, consulte el ejemplo de uso que se muestra dentro del [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamiento.

## <a name="see-also"></a>Consulte también

* [Sombreador estándar de MRTK](mrtk-standard-shader.md)
