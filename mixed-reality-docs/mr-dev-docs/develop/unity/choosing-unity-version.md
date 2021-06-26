---
title: Elección de una versión de Unity y un complemento XR
description: Manténgase al día de las recomendaciones más recientes del complemento Unity y XR para el desarrollo de aplicaciones holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality headset, windows mixed reality headset, virtual reality headset, unity
ms.openlocfilehash: 646a0ec3b3b332b038509cba39caa085c1590c1a
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112921433"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Elección de una versión de Unity y un complemento XR

Aunque actualmente se recomienda instalar **Unity 2020.3 LTS** con el complemento openXR de Mixed Reality más reciente para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (recomendado)

La configuración de Unity recomendada actualmente de Microsoft para el desarrollo de HoloLens 2 y Windows Mixed Reality es **Unity 2020.3 LTS** con la versión más reciente Mixed Reality complemento OpenXR. DEBE usar la versión de revisión de Unity 2020.3.8f1 o posterior para evitar problemas de rendimiento conocidos con compilaciones anteriores de la versión 2020.3.

> [!IMPORTANT]
> Unity 2020 no admite el destino HoloLens (1ª generación). Estos cascos siguen siendo compatibles con **[Unity 2019 LTS](#unity-20194-lts)** con XR integrado heredado durante el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.
>
> [!NOTE]
> Algunos paquetes aún no son compatibles con proyectos de realidad mixta en Unity 2020 LTS:
> 
> * La canalización de representación universal (URP) 10.5.0 o anterior tiene un problema de rendimiento conocido en HoloLens 2 dispositivos. _(corregido en la próxima versión de URP)_
> * Azure Remote Rendering ha enviado aún una versión actualizada compatible con Unity 2020.
>
> Si el proyecto de Unity usa la canalización de representación universal o Azure Remote Rendering, se recomienda no actualizar el proyecto a Unity 2020 hasta que haya paquetes actualizados disponibles.

La mejor manera de instalar y administrar Unity es mediante <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>. Cuando esté instalado, abra Unity Hub:

1. Seleccione la **pestaña Installs (Instala)** y elija **ADD (AGREGAR).**
2. Seleccione Unity 2020.3 LTS y haga clic en **Siguiente.**

![Nueva versión de la nueva versión de la instancia de Unity Hub](images/unity-hub-img-01.png)

3. Compruebe los siguientes componentes en **"Plataformas".**
    * **Compatibilidad con la compilación de la Plataforma universal de Windows**
    * **Compatibilidad con la compilación de Windows (IL2CPP)**

![Opción de compatibilidad con la compilación de la Plataforma universal de Windows para Unity](../images/Unity_Install_Option_UWP.png)

4. Si ha instalado Unity sin estas opciones, puede agregarlas a través del menú **"Agregar módulos"** en Unity Hub:

![Opción de compatibilidad con la compilación de Windows para Unity](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [Uso del complemento OpenXR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> Aunque se recomienda usar OpenXR para todos los proyectos nuevos, Unity 2020.3 LTS también admite el complemento [XR de Windows.](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr) Este complemento es totalmente compatible, aunque no recibirá nuevas características como la compatibilidad con AR Foundation 4.0.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Si necesita usar Unity 2019, puede usar **Unity 2019 LTS con XR integrado heredado.** Para empezar a trabajar con XR integrado heredado en Unity 2019.4 LTS, haga clic aquí:

> [!div class="nextstepaction"]
> [Configuración de XR integrado heredado](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity ha dejado de ser compatible con XR integrado heredado a partir de Unity 2019.  Aunque Unity 2019 ofrece un nuevo marco de complementos XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de Azure Spatial Anchors con AR Foundation 2.  En Unity 2020, Azure Spatial Anchors se admite en el marco del complemento XR.

Si va a desarrollar aplicaciones para HoloLens (1ª generación), estos cascos seguirán siendo compatibles con Unity 2019 LTS con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.

## <a name="unity-20211"></a>Unity 2021.1

Si está probando las primeras compilaciones de **Unity 2021.1,** debe pasar al complemento **OpenXR,** ya que el complemento XR de Windows está en desuso.  A partir de Unity 2021.2, el complemento OpenXR será la única ruta de acceso para el desarrollo de Mixed Reality, ya que ya no se admite el complemento XR de Windows.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Si ya tiene un proyecto con Unity 2018.4 LTS, el motor de Unity seguirá siendo compatible durante 2 años después de su lanzamiento.  Unity 2018 LTS llegará al final del servicio en la primavera de 2021.
