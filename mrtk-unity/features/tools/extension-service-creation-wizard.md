---
title: Asistente para la creación del servicio de extensión
description: Documentación sobre el Asistente para realizar la transición de singletons a servicios MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 6b4efa39a99755f3c031757c7298465886d0c39512c93750f4653200edce9e17
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214301"
---
# <a name="extension-service-creation-wizard"></a>Asistente para la creación del servicio de extensión

Realizar la transición de singletons a servicios puede ser difícil. Este asistente puede complementar nuestra otra documentación y código de ejemplo al permitir que los desarrolladores creen nuevos servicios con (aproximadamente) la misma facilidad que la creación de un nuevo script MonoBehaviour. Para obtener información sobre cómo crear servicios desde cero, consulte nuestra [Guía para crear servicios registrados](../../configuration/mixed-reality-configuration-guide.md) (Próximamente).

## <a name="launching-the-wizard"></a>Inicio del asistente

Inicie el asistente desde el menú principal: **MixedRealityToolkit/Utilities/Create Extension Service:** el asistente le llevará a través del proceso de generación del script de servicio, la interfaz y la clase de perfil.

## <a name="editing-your-service-script"></a>Edición del script de servicio

De forma predeterminada, los nuevos recursos de script se generarán en la `MixedRealityToolkit.Generated/Extensions` carpeta . Una vez que haya completado el asistente, vaya aquí y abra el nuevo script de servicio.

Los scripts de servicio generados incluyen algunos avisos similares a los nuevos scripts de MonoBehaviour. Le permitirán saber dónde inicializar y actualizar el servicio.

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

Si eligió registrar el servicio en el asistente, lo único que tiene que hacer es editar este script y el servicio se actualizará automáticamente. De lo contrario, puede leer [sobre cómo registrar el nuevo servicio aquí.](../../configuration/mixed-reality-configuration-guide.md)
