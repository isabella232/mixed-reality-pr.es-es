---
title: Elección de una versión de Unity y un complemento XR
description: Manténgase al día con las recomendaciones más recientes de los complementos de Unity y XR para HoloLens desarrollo de aplicaciones.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603686"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Elección de una versión de Unity y un complemento XR

Aunque actualmente se recomienda instalar **Unity 2020.3 LTS** con el complemento openXR de Mixed Reality más reciente para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (recomendado)

La configuración de Unity recomendada actualmente de Microsoft para el desarrollo de HoloLens 2 y Windows Mixed Reality es **Unity 2020.3 LTS** con la versión Mixed Reality complemento OpenXR más reciente. Debe **usar** la versión de revisión de Unity 2020.3.8f1 o posterior para evitar problemas de rendimiento conocidos con compilaciones anteriores de 2020.3.

> [!IMPORTANT]
> Unity 2020 no admite el destino HoloLens (1.ª generación). Estos cascos siguen siendo compatibles con **[Unity 2019 LTS](#unity-20194-lts)** con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.

La mejor manera de instalar y administrar Unity es a través de **Unity Hub:**

1. Instale <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub.**</a>
2. Seleccione la **pestaña Installs (Instala)** y elija **Add (Agregar).**
3. Seleccione **Unity 2020.3 LTS** y haga clic **en Siguiente.**

![Instalación de la nueva versión de Unity Hub](images/unity-hub-img-01.png)

4. Compruebe los siguientes componentes en **"Plataformas":**
    * **Compatibilidad con la compilación de la Plataforma universal de Windows**
    * **Compatibilidad con la compilación de Windows (IL2CPP)**

![Opción de compatibilidad con la compilación de la Plataforma universal de Windows para Unity](../images/Unity_Install_Option_UWP.png)

5. Si anteriormente instaló Unity sin estas opciones, puede agregarlas a través del menú **"Agregar módulos"** en Unity Hub:

![Opción de compatibilidad con la compilación de Windows para Unity](../images/Unity_Install_Option_UWP2.png)

Una vez que tenga Unity 2020.3 instalado, empezar a crear un proyecto o actualizar uno existente mediante el complemento Mixed Reality OpenXR:

> [!div class="nextstepaction"]
> [Configuración del proyecto con el complemento OpenXR](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> Aunque se recomienda usar OpenXR para todos los proyectos nuevos, Unity 2020.3 LTS también admite Windows [complemento XR.](xr-project-setup.md?tabs=windowsxr) Este complemento es totalmente compatible, aunque no recibirá nuevas características como la compatibilidad con AR Foundation 4.0.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Si necesita usar Unity 2019, puede usar **Unity 2019 LTS con XR integrado heredado.** Para empezar a trabajar con XR integrado heredado en Unity 2019.4 LTS, haga clic aquí:

> [!div class="nextstepaction"]
> [Configuración del proyecto con XR integrado heredado](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity ha dejado de ser compatible con XR integrado heredado a partir de Unity 2019.  Aunque Unity 2019 ofrece un nuevo marco de complementos XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de Azure Spatial Anchors con AR Foundation 2.  En Unity 2020, Azure Spatial Anchors se admite en el marco del complemento XR.

Si está desarrollando aplicaciones para HoloLens (1.ª generación), estos cascos seguirán siendo compatibles con Unity 2019 LTS con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.

## <a name="unity-20212"></a>Unity 2021.2

Si está probando las primeras compilaciones de **Unity 2021.2,** introducción al Mixed Reality [**de OpenXR.**](xr-project-setup.md?tabs=openxr) El complemento OpenXR es la única ruta de acceso para el desarrollo de realidad mixta en Unity 2021.2 y versiones posteriores, ya que la versión final de Unity para admitir el complemento XR de Windows era Unity 2021.1.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS ha llegado al final de la ventana de soporte técnico de Long-Term de dos años de Unity y ya no recibe actualizaciones de Unity, aunque los proyectos seguirán en ejecución.

Si tiene un proyecto de Unity 2018, debe considerar la posibilidad de planear una migración hacia Unity 2020.3 LTS y el complemento OpenXR Mixed Reality.