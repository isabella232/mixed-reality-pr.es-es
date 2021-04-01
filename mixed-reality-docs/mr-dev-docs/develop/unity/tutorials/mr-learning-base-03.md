---
title: 'Tutoriales de introducción: 3. Configuración de los perfiles de MRTK'
description: En este curso se muestra cómo configurar los perfiles Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, spatial awareness
ms.localizationpriority: high
ms.openlocfilehash: 994d2d42d8b6939496e84a730c4a73eff39c72e3
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550325"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Configuración de los perfiles de MRTK

## <a name="overview"></a>Introducción

En este tutorial, aprenderá a personalizar y configurar los perfiles de MRTK.

Los <a href="/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">perfiles de MRTK</a> constituyen un árbol de perfiles anidados que componen la información de configuración sobre cómo se deben inicializar los sistemas y las características de MRTK. El perfil de nivel superior, el perfil Configuration (Configuración), contiene perfiles anidados para cada uno de los sistemas básicos principales. Cada perfil anidado está diseñado para configurar el comportamiento de su sistema correspondiente.

En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial. Puedes seguir estos mismos principios para personalizar cualquier parámetro o valor de los perfiles de MRTK.

Como lo visto al implementar el proyecto en HoloLens 2 durante el [tutorial anterior](mr-learning-base-02.md#congratulations), la malla <a href="/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> es una colección de mallas que representan la geometría del entorno. Es una visualización útil para ver inicialmente, pero normalmente está desactivada para evitar la distracción visual y el impacto adicional en el rendimiento al tenerla activada.

## <a name="objectives"></a>Objetivos

* Obtener información sobre cómo personalizar y configurar los perfiles de MRTK
* Ocultar la malla de reconocimiento espacial

## <a name="changing-the-spatial-awareness-display-option"></a>Cambio de la opción de visualización del reconocimiento espacial

Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son los siguientes:

1. Clonar el perfil de configuración predeterminado
2. Habilitar el sistema de reconocimiento espacial.
3. Clonar el perfil del sistema de reconocimiento espacial predeterminado.
4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado.
5. Cambiar la visibilidad de la malla de reconocimiento espacial.

> [!NOTE]
> De forma predeterminada, los perfiles de MRTK no son editables. Estas son las plantillas de perfil predeterminadas que se deben clonar para poder editarse. Hay varias capas anidadas de perfiles. Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios parámetros.

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar el perfil de configuración predeterminado

> [!NOTE]
> El perfil de configuración es el perfil de nivel superior. Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.

En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, cambie el valor del perfil de configuración **MixedRealityToolkit** a **DefaultHoloLens2ConfigurationProfile**:

![Componente MixedRealityToolkit de Unity con DefaultHoloLens2ConfigurationProfile seleccionado](images/mr-learning-base/base-03-section1-step1-1.png)

Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):

![Botón Copy & Customize (Copiar y personalizar) del componente MixedRealityToolkit de Unity](images/mr-learning-base/base-03-section1-step1-2.png)

En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_HoloLens2ConfigurationProfiley_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultHololens2ConfigurationProfile**:

![Ventana emergente para clonar el perfil de configuración de MixedRealityToolkit de Unity](images/mr-learning-base/base-03-section1-step1-3.png)

El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:

![Componente MixedRealityToolkit de Unity con HoloLens2ConfigurationProfile personalizado recién creado aplicado](images/mr-learning-base/base-03-section1-step1-4.png)

En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.

> [!TIP]
> Recuerde guardar el trabajo a lo largo del tutorial.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar el sistema de reconocimiento espacial

En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):

![Componente MixedRealityToolkit de Unity con el sistema de reconocimiento espacial habilitado](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> En el caso de los proyectos futuros, si la aplicación no necesita responder al entorno ni interactuar con él, se recomienda mantener el reconocimiento espacial desactivado para reducir el costo de rendimiento.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar el perfil del sistema de reconocimiento espacial predeterminado

En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![Componente MixedRealityToolkit de Unity con la pestaña Spatial Awareness (Reconocimiento espacial) seleccionada](images/mr-learning-base/base-03-section1-step3-1.png)

En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![Ventana emergente para clonar el perfil del sistema de reconocimiento espacial de MixedRealityToolkit de Unity](images/mr-learning-base/base-03-section1-step3-2.png)

Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessSystemProfile personalizado recién creado aplicado](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado

Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expande la sección **Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality) y, a continuación, haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![Componente MixedRealityToolkit de Unity con la sección Windows Mixed Reality Spatial Mesh Observer (Observador de malla espacial de Windows Mixed Reality) expandida](images/mr-learning-base/base-03-section1-step4-1.png)

En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Ventana emergente para clonar el perfil del observador de la malla espacial de MixedRealityToolkit de Unity](images/mr-learning-base/base-03-section1-step4-2.png)

Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessMeshObserverProfile personalizado recién creado aplicado](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Cambiar la visibilidad de la malla de reconocimiento espacial

En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:

![Componente de MixedRealityToolkit de Unity con Display Option (Opción de visualización) de Spatial Mesh Observer (Observador de malla espacial) establecida en Occlusion (Oclusión)](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional. Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.

Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados. Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada. Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) en el [portal de documentación de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a clonar, personalizar y configurar los perfiles de MRTK y sus opciones.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 4. Posicionamiento de los objetos en la escena](mr-learning-base-04.md)