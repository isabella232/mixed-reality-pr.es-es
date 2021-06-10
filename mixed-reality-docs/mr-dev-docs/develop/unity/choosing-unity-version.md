---
title: Elección de una versión de Unity y un complemento XR
description: Manténgase al día con las recomendaciones más recientes de los complementos de Unity y XR para el desarrollo de aplicaciones holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, unity
ms.openlocfilehash: da171db41e508fe556d8645b23f12f6f437446a1
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908231"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Elección de una versión de Unity y un complemento XR

Aunque actualmente se recomienda instalar **Unity 2019.4 LTS** y usar XR integrado heredado para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (recomendado)

La configuración de Unity recomendada actualmente de Microsoft para el desarrollo HoloLens 2 y Windows Mixed Reality es **Unity 2019.4 LTS** con compatibilidad con XR integrada heredada.

La mejor manera de instalar y administrar Unity es a través de <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub].</a> Cuando esté instalado, abra Unity Hub:

1. Seleccione la **pestaña Installs (Instala)** y elija **ADD (AGREGAR).**
2. Seleccione Unity 2019.4 LTS y haga clic en **Siguiente.**

![Nueva versión de la instancia de Unity Hub](images/unity-hub-img-01.png)

3. Compruebe los siguientes componentes en **"Plataformas"**
    * **Compatibilidad con la compilación de la Plataforma universal de Windows** 
    * **Compatibilidad con la compilación de Windows (IL2CPP)**

![Opción de compatibilidad con la compilación de la Plataforma universal de Windows para Unity](../images/Unity_Install_Option_UWP.png)

4. Si ha instalado Unity sin estas opciones, puede agregarlas a través del menú **"Agregar módulos"** en Unity Hub:

![Opción de compatibilidad con la compilación de Windows para Unity](../images/Unity_Install_Option_UWP2.png)

Para empezar a trabajar con XR integrado heredado en Unity 2019.4 LTS, haga clic aquí:

> [!div class="nextstepaction"]
> [Configuración de XR integrado heredado](legacy-xr-support.md)

> [!NOTE]
> Unity ha dejado de ser compatible con XR integrado heredado a partir de Unity 2019.  Aunque Unity 2019 ofrece un nuevo marco de complementos XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de Azure Spatial Anchors con AR Foundation 2.  En Unity 2020, Azure Spatial Anchors se admite en el marco del complemento XR.

Si va a desarrollar aplicaciones para HoloLens (1.ª generación), estos cascos seguirán siendo compatibles con Unity 2019 LTS con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

Si usa **Unity 2020.3 LTS,** puede usar el complemento **XR** de Windows para desarrollar HoloLens 2 y Windows Mixed Reality aplicaciones.

Sin embargo, hay problemas conocidos que afectan a la estabilidad del holograma y otras características en HoloLens 2: 

* Las aplicaciones remotas de aplicaciones holográficas que usan Plataforma universal de Windows destino de compilación no funcionan.
* El sistema de trabajos gráficos de Unity está predeterminado, aunque no sea compatible con proyectos de HoloLens.

Si decide iniciar un nuevo proyecto en Unity 2020 hoy mismo, asegúrese de realizar un seguimiento en los próximos meses de las compilaciones de Unity actualizadas y las compilaciones del complemento XR de Windows antes de enviar la aplicación.  Esto garantizará que los usuarios experimente una estabilidad adecuada del holograma.

> [!div class="nextstepaction"]
> [Uso del complemento XR de Windows](windows-xr-plugin.md)

### <a name="using-openxr"></a>Uso de OpenXR

Unity 2020.3 LTS también admite una versión preliminar pública del **Mixed Reality complemento OpenXR.**

El Mixed Reality complemento OpenXR es totalmente compatible con AR Foundation 4.0, lo que proporciona implementaciones de ARPlaneManager y ARRaycastManager. Esto le permite escribir código de prueba de acceso una vez que, a continuación, HoloLens 2 teléfonos y tabletas ARCore/ARKit. 

Más adelante este año, **Unity 2020.3 LTS** con el complemento OpenXR se convertirá en la configuración recomendada de Unity y las futuras características de HoloLens 2 en Unity solo se mostrarán a través de este complemento.

> [!div class="nextstepaction"]
> [Uso del complemento OpenXR](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021.1

Si está probando las primeras compilaciones de **Unity 2021.1,** debe pasar al complemento **OpenXR,** ya que el complemento XR de Windows está en desuso allí.  A partir de Unity 2021.2, el complemento OpenXR será la única ruta de acceso para el desarrollo de Mixed Reality, ya que ya no se admite el complemento XR de Windows.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Si ya tiene un proyecto con Unity 2018.4 LTS, el motor de Unity seguirá siendo compatible durante dos años después de su lanzamiento.  Unity 2018 LTS llegará al final del servicio en la primavera de 2021.