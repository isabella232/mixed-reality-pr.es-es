---
title: Elección de una versión de Unity y el complemento XR
description: Manténgase al día sobre las últimas recomendaciones del complemento Unity y XR para el desarrollo de aplicaciones de HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938157"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Elección de una versión de Unity y el complemento XR

Aunque actualmente se **recomienda instalar Unity 2019,4 lts y el uso de la versión de XR integrada heredada** para el desarrollo de realidad mixta, también puede compilar aplicaciones con otras configuraciones de Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019,4 LTS (recomendado)

La configuración de Unity recomendada actual de Microsoft para el desarrollo de la realidad de HoloLens 2 y Windows Mixed Reality es **Unity 2019,4 lts con compatibilidad integrada de XR heredada** .

La mejor manera de instalar y administrar Unity es a través del <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>. Cuando esté instalado, abra Unity Hub:

1. Seleccione la pestaña **instalaciones** y elija **Agregar** .
2. Seleccione Unity 2019,4 LTS y haga clic en **siguiente** .

![Instalar la nueva versión de Unity Hub](images/unity-hub-img-01.png)

3. Comprobar los siguientes componentes en **' Plataformas '**
    * **Compatibilidad con la compilación de Plataforma universal de Windows** 
    * **Compatibilidad con la compilación de Windows (IL2CPP)**

![Opción de compatibilidad con la compilación de Unity Plataforma universal de Windows](../images/Unity_Install_Option_UWP.png)

4. Si instaló Unity sin estas opciones, puede agregarlos a través del menú **' agregar módulos '** en Unity Hub:

![Opción de compatibilidad con la compilación de Windows de Unity](../images/Unity_Install_Option_UWP2.png)

Para empezar a trabajar con las versiones anteriores de XR integradas en Unity 2019,4 LTS, haga clic aquí:

> [!div class="nextstepaction"]
> [Configurar XR integrado](legacy-xr-support.md)

> [!NOTE]
> Unity ha dejado de usar su compatibilidad integrada de XR heredada a partir de Unity 2019.  Aunque Unity 2019 ofrece un nuevo marco de trabajo de complemento de XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de los delimitadores espaciales de Azure con AR Foundation 2.  En Unity 2020, se admiten los delimitadores espaciales de Azure en el marco de trabajo del complemento XR.

Si va a desarrollar aplicaciones para HoloLens (1ª generación), estos auriculares siguen siendo compatibles con Unity 2019 LTS con XR integrado integrado para el ciclo de vida completo de Unity 2019 LTS a mediados de 2022.

## <a name="unity-20203-lts"></a>Unity 2020,3 LTS 

Si usa **Unity 2020,3 LTS**, puede usar el **complemento de Windows XR** para desarrollar aplicaciones de la realidad de HoloLens 2 y Windows Mixed Reality.

Sin embargo, hay problemas conocidos que afectan a la estabilidad del holograma y otras características de HoloLens 2: 

* El envío de búfer de profundidad se ha revertido en las compilaciones de Unity 2020 recientes, lo que produce una inestabilidad grave de hologramas.
* Las aplicaciones de comunicación remota de aplicaciones holográficas que usan el destino de compilación Plataforma universal de Windows no funcionan.
* El sistema de trabajos de gráficos de Unity está predeterminado en, aunque no es compatible con los proyectos de HoloLens.

Si decide iniciar un nuevo proyecto en Unity 2020 hoy, asegúrese de seguir los próximos meses para las compilaciones de Unity actualizadas y las compilaciones del complemento de Windows XR antes de enviar la aplicación.  Esto garantizará que los usuarios experimenten una estabilidad de holograma adecuada.

> [!div class="nextstepaction"]
> [Usar el complemento de Windows XR](windows-xr-plugin.md)

### <a name="using-openxr"></a>Usar OpenXR

Unity 2020,3 LTS también admite una versión preliminar pública del complemento **OpenXR de realidad mixta** .

El complemento OpenXR de realidad mixta es totalmente compatible con AR Foundation 4,0 y proporciona implementaciones ARPlaneManager y ARRaycastManager. Esto le permite escribir código de prueba de posicionamiento una vez que abarque los teléfonos y tabletas de HoloLens 2 y ARCore/ARKit. 

Más adelante este año, **unity 2020,3 LTS con el complemento OpenXR** se convertirá en la configuración de Unity recomendada y las futuras características de HoloLens 2 en Unity solo se expondrán a través de este complemento.  Aquí puede iniciar el proyecto aquí; sin embargo, si el proyecto tiene como destino HoloLens 2, actualmente se encontrará la estabilidad de los hologramas de Unity 2020 y otros problemas mencionados anteriormente.  Asegúrese de volver a consultar los próximos meses para obtener las compilaciones de Unity actualizadas y las compilaciones de complementos de OpenXR antes de enviar la aplicación.  Esto garantizará que los usuarios experimenten una estabilidad de holograma adecuada. 

> [!div class="nextstepaction"]
> [Uso del complemento OpenXR](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021,1

Si está probando versiones anteriores de **Unity 2021,1** , debe avanzar al **complemento OpenXR**, ya que el complemento de Windows XR está en desuso.  A partir de Unity 2021,2, el complemento OpenXR será la única ruta de acceso para el desarrollo de realidad mixta, ya que el complemento de Windows XR ya no se admitirá.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Si ya tiene un proyecto que usa Unity 2018,4 LTS, el motor de Unity seguirá siendo compatible durante 2 años después de su lanzamiento.  Unity 2018 LTS alcanzará el final del servicio en el muelle de 2021.
