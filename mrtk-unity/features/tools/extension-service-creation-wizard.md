---
title: Asistente para la creación del servicio de extensión
description: Documentación sobre el Asistente para realizar la transición de singletons a servicios MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 83797a9d6d465a150406b27162a5e84c157567f1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143539"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="5ad34-104">Asistente para la creación de servicios de extensión</span><span class="sxs-lookup"><span data-stu-id="5ad34-104">Extension service creation wizard</span></span>

<span data-ttu-id="5ad34-105">Realizar la transición de singletons a servicios puede ser difícil.</span><span class="sxs-lookup"><span data-stu-id="5ad34-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="5ad34-106">Este asistente puede complementar nuestra otra documentación y código de ejemplo al permitir que los desarrolladores creen nuevos servicios con (aproximadamente) la misma facilidad que la creación de un nuevo script MonoBehaviour.</span><span class="sxs-lookup"><span data-stu-id="5ad34-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="5ad34-107">Para obtener información sobre cómo crear servicios desde cero, consulte nuestra [Guía para crear servicios registrados](../../configuration/mixed-reality-configuration-guide.md) (Próximamente).</span><span class="sxs-lookup"><span data-stu-id="5ad34-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="5ad34-108">Inicio del asistente</span><span class="sxs-lookup"><span data-stu-id="5ad34-108">Launching the wizard</span></span>

<span data-ttu-id="5ad34-109">Inicie el asistente desde el menú principal: **MixedRealityToolkit/Utilities/Create Extension Service:** el asistente le llevará a través del proceso de generación del script de servicio, la interfaz y la clase de perfil.</span><span class="sxs-lookup"><span data-stu-id="5ad34-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="5ad34-110">Edición del script de servicio</span><span class="sxs-lookup"><span data-stu-id="5ad34-110">Editing your service script</span></span>

<span data-ttu-id="5ad34-111">De forma predeterminada, los nuevos recursos de script se generarán en la `MixedRealityToolkit.Generated/Extensions` carpeta .</span><span class="sxs-lookup"><span data-stu-id="5ad34-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="5ad34-112">Una vez que haya completado el asistente, vaya aquí y abra el nuevo script de servicio.</span><span class="sxs-lookup"><span data-stu-id="5ad34-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="5ad34-113">Los scripts de servicio generados incluyen algunos avisos similares a los nuevos scripts de MonoBehaviour.</span><span class="sxs-lookup"><span data-stu-id="5ad34-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="5ad34-114">Le permitirán saber dónde inicializar y actualizar el servicio.</span><span class="sxs-lookup"><span data-stu-id="5ad34-114">They will let you know where to initialize and update your service.</span></span>

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

<span data-ttu-id="5ad34-115">Si eligió registrar el servicio en el asistente, lo único que tiene que hacer es editar este script y el servicio se actualizará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="5ad34-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="5ad34-116">De lo contrario, puede leer [sobre cómo registrar el nuevo servicio aquí.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="5ad34-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
