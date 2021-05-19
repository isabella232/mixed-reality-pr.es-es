---
title: Instancia de material
description: Documentación sobre Instancia de material y sus usos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, MaterialInstance,
ms.openlocfilehash: 216fa72af6bb6caaf47e30c156f7caf1b1dab71e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145211"
---
# <a name="material-instance"></a><span data-ttu-id="4f02a-104">Instancia de material</span><span class="sxs-lookup"><span data-stu-id="4f02a-104">Material instance</span></span>

<span data-ttu-id="4f02a-105">El comportamiento se guía en el seguimiento de la duración del material de la instancia y destruye automáticamente los [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) materiales de instancia para el usuario.</span><span class="sxs-lookup"><span data-stu-id="4f02a-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="4f02a-106">Este componente de utilidad se puede usar como reemplazo de [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) o [Renderer.materials.](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)</span><span class="sxs-lookup"><span data-stu-id="4f02a-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="4f02a-107">[MaterialPropertyBlocks es](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) preferible a la creación de instancias de material, pero no siempre están disponibles en todos los escenarios.</span><span class="sxs-lookup"><span data-stu-id="4f02a-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="4f02a-108">¿Por qué [el uso de Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) puede ser un problema?</span><span class="sxs-lookup"><span data-stu-id="4f02a-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="4f02a-109">Si agrega el código siguiente a una escena de Unity y pulsa el uso de la memoria de reproducción, el uso de la memoria seguirá siendo desaparecado y desbocado:</span><span class="sxs-lookup"><span data-stu-id="4f02a-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

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
> <span data-ttu-id="4f02a-110">El comportamiento de pérdida **anterior bloqueará Unity** si se ejecutó durante demasiado tiempo.</span><span class="sxs-lookup"><span data-stu-id="4f02a-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="4f02a-111">Como alternativa, pruebe a usar el [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamiento:</span><span class="sxs-lookup"><span data-stu-id="4f02a-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

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

## <a name="usage"></a><span data-ttu-id="4f02a-112">Uso</span><span class="sxs-lookup"><span data-stu-id="4f02a-112">Usage</span></span>

<span data-ttu-id="4f02a-113">Al invocar [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) de Unity, Unity crea automáticamente instancias de nuevos materiales.</span><span class="sxs-lookup"><span data-stu-id="4f02a-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="4f02a-114">Es responsabilidad del autor de la llamada destruir los materiales cuando ya no se necesita un material o se destruye el objeto del juego.</span><span class="sxs-lookup"><span data-stu-id="4f02a-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="4f02a-115">El comportamiento ayuda a evitar pérdidas de material y mantiene coherentes las rutas de asignación [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) de materiales durante el tiempo de edición y ejecución.</span><span class="sxs-lookup"><span data-stu-id="4f02a-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="4f02a-116">Cuando [no se puede usar MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) y se debe crear una instancia de un material, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) se puede usar de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="4f02a-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

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

<span data-ttu-id="4f02a-117">Si varios objetos necesitan la propiedad de la instancia de material, es mejor tomar posesión explícita para el seguimiento de referencias.</span><span class="sxs-lookup"><span data-stu-id="4f02a-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="4f02a-118">(Existe una interfaz opcional [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) denominada para ayudar con la propiedad). A continuación se muestra un ejemplo de uso:</span><span class="sxs-lookup"><span data-stu-id="4f02a-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

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

<span data-ttu-id="4f02a-119">Para más información, consulte el ejemplo de uso que se muestra dentro del [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamiento.</span><span class="sxs-lookup"><span data-stu-id="4f02a-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f02a-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4f02a-120">See also</span></span>

* [<span data-ttu-id="4f02a-121">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="4f02a-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
