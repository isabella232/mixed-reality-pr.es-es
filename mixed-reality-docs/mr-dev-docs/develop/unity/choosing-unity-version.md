---
title: Elección de una versión de Unity y un complemento XR
description: Manténgase al día con las recomendaciones más recientes de los complementos de Unity y XR para el desarrollo de aplicaciones holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual, unity
ms.openlocfilehash: f37dbdccf175a5cea9a647f0c14b90682b19dfb3
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906861"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Elección de una versión de Unity y un complemento XR

Aunque actualmente se recomienda instalar **Unity 2019.4 LTS** y usar XR integrado heredado para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (recomendado)

La configuración de Unity recomendada actualmente de Microsoft para el desarrollo HoloLens 2 y Windows Mixed Reality es **Unity 2019.4 LTS** con compatibilidad con XR integrada heredada.

La mejor manera de instalar y administrar Unity es a través de <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub].</a> Cuando esté instalado, abra Unity Hub:

1. Seleccione la **pestaña Installs (Instala)** y elija **ADD (AGREGAR).**
2. Seleccione Unity 2019.4 LTS y haga clic en **Siguiente.**

![Nueva versión de la instancia de Unity Hub](images/unity-hub-img-2019.png)

3. Compruebe los siguientes componentes en **"Plataformas".**
    * **Compatibilidad con la compilación de la Plataforma universal de Windows** 
    * **Compatibilidad con la compilación de Windows (IL2CPP)**

![Opción de compatibilidad con la compilación de la Plataforma universal de Windows para Unity](images/Unity_Install_Option_UWP_2019.png)

4. Si instaló Unity sin estas opciones, puede agregarlas a través del menú **"Agregar módulos"** en Unity Hub:

![Opción de compatibilidad con la compilación de Windows para Unity](images/Unity_Install_Option_UWP2_2019.png)

Para empezar a trabajar con XR integrado heredado en Unity 2019.4 LTS, haga clic aquí:

> [!div class="nextstepaction"]
> [Configuración de XR integrado heredado](./xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity ha dejado de ser compatible con XR integrado heredado a partir de Unity 2019.  Aunque Unity 2019 ofrece un nuevo marco de complementos XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de Azure Spatial Anchors con AR Foundation 2.  En Unity 2020, Azure Spatial Anchors se admite en el marco del complemento XR.

Si va a desarrollar aplicaciones para HoloLens (1.ª generación), estos cascos seguirán siendo compatibles con Unity 2019 LTS con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

Si usa **Unity 2020.3 LTS,** la recomendación actual de Microsoft es la Mixed Reality **complemento OpenXR.** DEBE usar la versión de revisión de Unity 2020.3.8f1 o posterior para evitar problemas de rendimiento conocidos con compilaciones anteriores de 2020.3.

El Mixed Reality complemento OpenXR es totalmente compatible con AR Foundation 4.0, lo que proporciona implementaciones de ARPlaneManager y ARRaycastManager. Esto le permite escribir código de prueba de acceso una vez que, a continuación, HoloLens 2 teléfonos y tabletas ARCore/ARKit.

Sin embargo, hay problemas conocidos que afectan a los proyectos de Unity 2020 LTS:

* La canalización de representación universal (URP) 10.5.0 o anterior tiene penalizaciones de rendimiento en HoloLens 2 dispositivos.

Si decide iniciar un nuevo proyecto en Unity 2020 hoy mismo, asegúrese de realizar un seguimiento en las próximas semanas de las compilaciones de Unity y los paquetes URP actualizados antes de enviar la aplicación.  Esto garantizará que los usuarios experimente la estabilidad adecuada del holograma.

> [!div class="nextstepaction"]
> [Uso del complemento OpenXR](./xr-project-setup.md?tabs=openxr)

## <a name="unity-20211"></a>Unity 2021.1

Si está probando las primeras compilaciones de **Unity 2021.1,** debe pasar al complemento **OpenXR,** ya que el complemento XR de Windows está en desuso allí.  A partir de Unity 2021.2, el complemento OpenXR será la única ruta de acceso para el desarrollo de Mixed Reality, ya que ya no se admite el complemento XR de Windows.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Si ya tiene un proyecto con Unity 2018.4 LTS, el motor de Unity seguirá siendo compatible durante dos años después de su lanzamiento.  Unity 2018 LTS llegará al final del servicio en la primavera de 2021.