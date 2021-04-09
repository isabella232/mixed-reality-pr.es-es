---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097821"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento XR para Unity 2019/2020 y Windows](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar el perfil de configuración predeterminado

> [!NOTE]
> El perfil de configuración es el perfil de nivel superior. Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.

En la ventana Hierarchy (Jerarquía), seleccione el objeto **MixedRealityToolkit**. Después, en la ventana Inspector, compruebe que el perfil de configuración de **MixedRealityToolkit** esté definido como **DefaultXRSDKConfigurationProfile**:

![Componente MixedRealityToolkit de Unity con DefaultHoloLens2ConfigurationProfile seleccionado](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):

![Botón Copy & Customize (Copiar y personalizar) del componente MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

En la ventana Clone Profile (Clonar perfil), escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_XRSDKConfigurationProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultXRSDKConfigurationProfile**:

![Ventana emergente para clonar el perfil de configuración de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:

![Componente MixedRealityToolkit de Unity con HoloLens2ConfigurationProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.

> [!TIP]
> Recuerde guardar el trabajo a lo largo del tutorial.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar el sistema de reconocimiento espacial

En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):

![Componente MixedRealityToolkit de Unity con el sistema de reconocimiento espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> En el caso de los proyectos futuros, si la aplicación no necesita responder al entorno ni interactuar con él, se recomienda mantener el reconocimiento espacial desactivado para reducir el costo de rendimiento.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar el perfil del sistema de reconocimiento espacial predeterminado

En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![Componente MixedRealityToolkit de Unity con la pestaña Spatial Awareness (Reconocimiento espacial) seleccionada](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

En la ventana Clone Profile (Clonar perfil), escriba un valor de **Profile Name** (Nombre de perfil) adecuado; por ejemplo, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultXRSDKSpatialAwarenessSystemProfile**:

![Ventana emergente para clonar el perfil del sistema de reconocimiento espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessSystemProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado

Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expanda la sección **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality del SDK de XR) y, a continuación, haga clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![Componente MixedRealityToolkit de Unity con la sección Windows Mixed Reality Spatial Mesh Observer (Observador de malla espacial de Windows Mixed Reality) expandida](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Ventana emergente para clonar el perfil del observador de la malla espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessMeshObserverProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Cambiar la visibilidad de la malla de reconocimiento espacial

En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:

![Componente de MixedRealityToolkit de Unity con Display Option (Opción de visualización) de Spatial Mesh Observer (Observador de malla espacial) establecida en Occlusion (Oclusión)](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional. Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.

Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados. Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada. Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) en el [portal de documentación de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar el perfil de configuración predeterminado

> [!NOTE]
> El perfil de configuración es el perfil de nivel superior. Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.

En la ventana Hierarchy (Jerarquía), seleccione el objeto **MixedRealityToolkit**. Después, en la ventana Inspector, compruebe que el perfil de configuración de **MixedRealityToolkit** esté definido como **DefaultOpenXRConfigurationProfile**:

![Componente MixedRealityToolkit de Unity con el perfil de OpenXR predeterminado seleccionado](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):

![Botón Copy & Customize (Copiar y personalizar) del componente MixedRealityToolkit de Unity para el perfil de OpenXR](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

En la ventana Clone Profile (Clonar perfil), escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_OpenXRConfigurationProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultOpenXRConfigurationProfile**:

![Ventana emergente para clonar el perfil de configuración de MixedRealityToolkit de Unity para el perfil de OpenXR](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:

![Componente MixedRealityToolkit de Unity con OpenXR personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.

> [!TIP]
> Recuerde guardar el trabajo a lo largo del tutorial.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar el sistema de reconocimiento espacial

En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):

![Componente MixedRealityToolkit de Unity con el sistema de reconocimiento espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> En el caso de los proyectos futuros, si la aplicación no necesita responder al entorno ni interactuar con él, se recomienda mantener el reconocimiento espacial desactivado para reducir el costo de rendimiento.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar el perfil del sistema de reconocimiento espacial predeterminado

En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![Componente MixedRealityToolkit de Unity con la pestaña Spatial Awareness (Reconocimiento espacial) seleccionada](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

En la ventana Clone Profile (Clonar perfil), escriba un valor de **Profile Name** (Nombre de perfil) adecuado; por ejemplo, GettingStarted_OpenXRSpatialAwarenessSystemProfile. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultXRSDKSpatialAwarenessSystemProfile**:

![Ventana emergente para clonar el perfil del sistema de reconocimiento espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessSystemProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado

Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expanda la sección **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality del SDK de XR) y, a continuación, haga clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![Componente MixedRealityToolkit de Unity con la sección Windows Mixed Reality Spatial Mesh Observer (Observador de malla espacial de Windows Mixed Reality) expandida](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Ventana emergente para clonar el perfil del observador de la malla espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessMeshObserverProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Cambiar la visibilidad de la malla de reconocimiento espacial

En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:

![Componente de MixedRealityToolkit de Unity con Display Option (Opción de visualización) de Spatial Mesh Observer (Observador de malla espacial) establecida en Occlusion (Oclusión)](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional. Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.

Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados. Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada. Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) en el [portal de documentación de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).


# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar el perfil de configuración predeterminado

> [!NOTE]
> El perfil de configuración es el perfil de nivel superior. Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.

En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, cambie el valor del perfil de configuración **MixedRealityToolkit** a **DefaultHoloLens2ConfigurationProfile**:

![Componente MixedRealityToolkit de Unity con DefaultHoloLens2ConfigurationProfile seleccionado](../images/mr-learning-base/base-03-section1-step1-1.png)

Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):

![Botón Copy & Customize (Copiar y personalizar) del componente MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step1-2.png)

En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_HoloLens2ConfigurationProfiley_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultHololens2ConfigurationProfile**:

![Ventana emergente para clonar el perfil de configuración de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step1-3.png)

El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:

![Componente MixedRealityToolkit de Unity con HoloLens2ConfigurationProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step1-4.png)

En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.

> [!TIP]
> Recuerde guardar el trabajo a lo largo del tutorial.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar el sistema de reconocimiento espacial

En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):

![Componente MixedRealityToolkit de Unity con el sistema de reconocimiento espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> En el caso de los proyectos futuros, si la aplicación no necesita responder al entorno ni interactuar con él, se recomienda mantener el reconocimiento espacial desactivado para reducir el costo de rendimiento.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar el perfil del sistema de reconocimiento espacial predeterminado

En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![Componente MixedRealityToolkit de Unity con la pestaña Spatial Awareness (Reconocimiento espacial) seleccionada](../images/mr-learning-base/base-03-section1-step3-1.png)

En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![Ventana emergente para clonar el perfil del sistema de reconocimiento espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step3-2.png)

Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessSystemProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado

Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expande la sección **Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality) y, a continuación, haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![Componente MixedRealityToolkit de Unity con la sección Windows Mixed Reality Spatial Mesh Observer (Observador de malla espacial de Windows Mixed Reality) expandida](../images/mr-learning-base/base-03-section1-step4-1.png)

En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Ventana emergente para clonar el perfil del observador de la malla espacial de MixedRealityToolkit de Unity](../images/mr-learning-base/base-03-section1-step4-2.png)

Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:

![Componente MixedRealityToolkit de Unity con MixedRealitySpatialAwarenessMeshObserverProfile personalizado recién creado aplicado](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Cambiar la visibilidad de la malla de reconocimiento espacial

En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:

![Componente de MixedRealityToolkit de Unity con Display Option (Opción de visualización) de Spatial Mesh Observer (Observador de malla espacial) establecida en Occlusion (Oclusión)](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional. Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.

Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados. Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada. Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) en el [portal de documentación de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).
