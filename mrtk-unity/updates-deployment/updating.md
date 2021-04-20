---
title: Actualización
description: Documentación para migrar desde una versión inferior de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742241"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a>Actualización de Microsoft Mixed Reality Toolkit

- [Actualización a una nueva versión de MRTK](#upgrading-to-a-new-version-of-mrtk)
- [De 2.3.0 a 2.4.0](#updating-230-to-240)
- [De 2.2.0 a 2.3.0](#updating-220-to-230)
- [De 2.1.0 a 2.2.0](#updating-210-to-220)
- [De 2.0.0 a 2.1.0](#updating-200-to-210)
- [RC2 a 2.0.0](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>Búsqueda de la versión actual 

Siga estas instrucciones para averiguar qué versión de MRTK está usando actualmente:

1. Apertura del proyecto de MRTK en Unity
2. Vaya a la carpeta "MixedRealityToolkit" en la ventana del proyecto.
3. Abra el archivo denominado "Version"

Si el archivo y la carpeta anteriores no existen, se encuentra en una versión más reciente de MRTK. En ese caso, pruebe lo siguiente:

1. Vaya a la carpeta "Mixed Reality Toolkit Foundation".
2. Haga clic en "package.js" para ver una vista previa en Unity o ábrala con un editor de texto.
3. Busque la línea con la palabra "version:" 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>Actualización a una nueva versión de MRTK

*Se recomienda encarecidamente ejecutar [](../features/tools/migration-window.md)* la herramienta de migración después de obtener la actualización de MRTK para corregir y actualizar automáticamente los componentes en desuso y ajustarse a los cambios importantes. La herramienta de migración forma parte del **paquete Herramientas.**

Las instrucciones siguientes describen la ruta de actualización de 2.4.0 a 2.5.0. Si el proyecto está en la versión 2.3.0 o anterior, siga leyendo los [](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) cambios entre versiones para comprender la ruta de actualización o lea las instrucciones de la versión anterior para realizar una actualización versión por versión. [](#updating-230-to-240)

### <a name="mixed-reality-feature-tool"></a>Herramienta de características de Mixed Reality
La manera más fácil de actualizar MRTK a una versión más reciente de MRTK es usar la herramienta de características de [Mixed Reality](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) para descargar los paquetes más recientes y cargarlos directamente en el proyecto de Unity.

Si el proyecto usó previamente archivos de recursos de Unity (.unitypackage), consulte [estas instrucciones.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool) 

### <a name="unity-asset-unitypackage-files"></a>Archivos de recursos de Unity (.unitypackage)

Otra ruta de actualización consiste en descargar manualmente los paquetes de Unity de MRTK y aplicarlos al proyecto. Consulte los pasos siguientes:

1. Guarde una copia del proyecto actual, en caso de que se presione algún grupo de seguridad en cualquier punto de los pasos de actualización.
1. Cerrar Unity
1. Dentro de *la carpeta Activos,* elimine las siguientes carpetas **MRTK,** junto con sus archivos .meta (es posible que el proyecto no tenga todas las carpetas enumeradas)
    - MRTK/Core
    - MRTK/Examples
    - MRTK/Extensions
    - MRTK/Providers
    - MRTK/SDK
    - MRTK/Services
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Si se realizaron modificaciones en los sombreadores MRTK, cree una copia de seguridad local antes de eliminar la carpeta MRTK/StandardAssets.
    - MRTK/Tools
    > [!IMPORTANT]
    > NO elimine la **carpeta MixedRealityToolkit.Generated** ni su archivo .meta.
1. Eliminación de la **carpeta Biblioteca**
    > [!IMPORTANT]
    > Algunas herramientas de Unity, como Unity Collab, guarda la información de configuración en la carpeta Biblioteca. Si usa una herramienta que lo hace, copie primero la carpeta de datos de la herramienta de La biblioteca antes de eliminarla y, después, restáurela después de volver a generar la biblioteca.
1. Volver a abrir el proyecto en Unity
1. Importación de los nuevos paquetes de Unity
    - Foundation: _importe primero este paquete._
    - Herramientas
    - (Opcional) Extensiones
    > [!NOTE]
    > Si se hubieran instalado extensiones adicionales, es posible que deban volver a importarse.
    - (Opcional) Ejemplos
1. Cierre Unity y elimine la **carpeta Biblioteca** (lea primero la nota siguiente). Este paso es necesario para forzar a Unity a actualizar su base de datos de recursos y conciliar los perfiles personalizados existentes.
1. Inicie Unity y para cada escena del proyecto.
    - Elimine **MixedRealityToolkit** y **MixedRealityPlayspace,** si está presente, de la jerarquía. Esto eliminará la cámara principal, pero se volverá a crear en el paso siguiente. Si alguna de las propiedades de la cámara principal se ha cambiado manualmente, estas se tendrán que volver a aplicar manualmente una vez creada la nueva cámara.
    - Seleccione **MixedRealityToolkit -> Agregar a la escena y configurar**
    - Seleccione **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (solo debe realizarse una vez): se actualizarán todos los perfiles de asignación de controladores personalizados con ejes y datos actualizados, a la vez que se mantienen intactas las acciones de entrada asignadas de forma personalizada.
1. Ejecute la [herramienta de migración](../features/tools/migration-window.md) y ejecute la herramienta en el proyecto *completo* para asegurarse de que todo el código se actualiza a la versión más reciente.
   La ventana de migración contiene una serie de controladores de migración diferentes, que se deben ejecutar cada uno por su cuenta. Este paso implica lo siguiente:
   - Seleccione el primer controlador de migración en la lista **desplegable Selección del controlador de** migración.
   - Haga clic en el botón "Proyecto completo".
   - Haga clic en el botón "Add full project for migration" (Agregar proyecto completo para la migración) (examinará todo el proyecto en busca de objetos que se van a migrar).
   - Haga clic en el botón "Migrar", que debe habilitarse si se han encontrado objetos migrables.
   - Repita los tres pasos anteriores para cada uno de los controladores de migración de la lista desplegable.
     (Vea [este problema que](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) trata el trabajo que se puede realizar para simplificar este proceso de migración en una versión futura).

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>Cambio de archivos de recursos de Unity a Mixed Reality Feature Tool

El cambio de archivos de recursos de Unity Mixed Reality paquetes de Feature Tool aporta una serie de ventajas:

- Actualización más sencilla
- Tiempos de compilación más rápidos
- Menos proyectos en la solución Visual Studio proyecto

Cambiar al uso de Mixed Reality Feature Tool requiere un conjunto único de pasos manuales.

1. Guarde una copia del proyecto actual.
1. Cerrar Unity
1. Dentro de *la carpeta Activos,* elimine las siguientes carpetas **MRTK,** junto con sus archivos .meta (es posible que el proyecto no tenga todas las carpetas enumeradas)
    - MRTK/Core
    - MRTK/Examples
    - MRTK/Extensions
    - MRTK/Providers
    - MRTK/SDK
    - MRTK/Services
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Si se realizaron modificaciones en los sombreadores MRTK, cree una copia de seguridad local antes de eliminar la carpeta MRTK/StandardAssets.
    - MRTK/Tools
    > [!IMPORTANT]
    > NO elimine la **carpeta MixedRealityToolkit.Generated** ni su archivo .meta.
1. Eliminación de la **carpeta Biblioteca**
    > [!IMPORTANT]
    > Algunas herramientas de Unity, como Unity Collab, guarda la información de configuración en la carpeta Biblioteca. Si usa una herramienta que lo hace, copie primero la carpeta de datos de la herramienta de La biblioteca antes de eliminarla y, después, restáurela después de volver a generar la biblioteca.
1. Volver a abrir el proyecto en Unity

Una vez que se hayan realizado los pasos anteriores, ejecute [Mixed Reality Feature Tool](#mixed-reality-feature-tool) e importe la versión deseada de Mixed Reality Toolkit.

## <a name="updating-230-to-240"></a>Actualización de 2.3.0 a 2.4.0

[Cambio de nombre de carpeta](#folder-renames-in-240) 
 [Cambios de API](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>Cambio de nombre de carpeta en la versión 2.4.0

Se ha cambiado el nombre de las carpetas de MixedRealityToolkit y se han movido a una jerarquía común en la versión 2.4. Si una aplicación usa rutas de acceso codificadas de forma fuerte a los recursos de MRTK, deberá actualizarse según la tabla siguiente.

| Carpeta anterior | Nueva carpeta |
| --- | --- |
| MixedRealityToolkit | MRTK/Core |
| MixedRealityToolkit.Examples | MRTK/Examples |
| MixedRealityToolkit.Extensions | MRTK/Extensions |
| MixedRealityToolkit.Providers | MRTK/Providers |
| MixedRealityToolkit.SDK | MRTK/SDK |
| MixedRealityToolkit.Services | MRTK/Services |
| MixedRealityToolkit.Tests | MRTK/Tests |
| MixedRealityToolkit.Tools | MRTK/Tools |

> [!IMPORTANT]
> contiene `MixedRealityToolkit.Generated` archivos generados por el cliente y permanece sin cambios.

### <a name="eye-gaze-setup-in-240"></a>Configuración de la mirada con los ojos en la versión 2.4.0

Esta versión de MRTK modifica los pasos necesarios para la configuración de la mirada con los ojos. La _casilla "IsEyeTrackingEnabled"_ se puede encontrar en la configuración de mirada del perfil de puntero de entrada. Al activar esta casilla, se habilitará la mirada con los ojos, en lugar de la mirada basada en la cabeza predeterminada.

Para obtener más información sobre estos cambios e instrucciones completas para la configuración del seguimiento ocular, consulte el artículo [seguimiento ocular.](../features/input/eye-tracking/eye-tracking-basic-setup.md)

### <a name="eye-gaze-pointer-behavior-in-240"></a>Comportamiento del puntero de mirada con los ojos en 2.4.0

El comportamiento del puntero predeterminado de la mirada con los ojos se ha modificado para que coincida con el comportamiento predeterminado del puntero de mirada con la cabeza. Un puntero de mirada con los ojos se suprimirá automáticamente una vez que se detecte una mano. El puntero de mirada con los ojos volverá a estar visible después de decir "Seleccionar".

Puede encontrar detalles sobre las configuraciones de mirada y mano en el [artículo sobre los ojos y las](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) manos.

### <a name="api-changes-in-240"></a>Cambios de API en la versión 2.4.0

**Clases de controlador personalizadas**

Anteriormente, las clases de controlador personalizadas tenían que definir `SetupDefaultInteractions(Handedness)` . Este método se ha quedado obsoleto en la versión 2.4, ya que el parámetro handedness era redundante con la propia entrega de la clase del controlador. El nuevo método no tiene parámetros. Además, muchas clases de controlador definieron esto de la misma manera ( ), por lo que la llamada completa se ha refactorizado en y se ha convertido en una invalidación opcional en lugar `AssignControllerMappings(DefaultInteractions);` `BaseController` de obligatoria.

**Propiedades de mirada con los ojos**

El `UseEyeTracking` nombre de la propiedad de la implementación de se ha cambiado a `GazeProvider` `IMixedRealityEyeGazeProvider` `IsEyeTrackingEnabled` .

Si lo hizo anteriormente...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

Haga esto ahora...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**Propiedades de WindowsApiChecker**

Las siguientes propiedades de WindowsApiChecker se han marcado como obsoletas. Use `IsMethodAvailable` o `IsPropertyAvailable` `IsTypeAvailable` .

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

No hay ningún plan para agregar propiedades a WindowsApiChecker para futuras versiones de contrato de API.

**GltfMeshPrimitiveAttributes de solo lectura**

Los atributos primitivos de la malla gltf que se solían establecer, ahora son de solo lectura. Sus valores se establecerán una vez cuando se deserialice.

### <a name="custom-button-icon-migration"></a>Migración de icono de botón personalizado

Anteriormente, los iconos de botón personalizados requerían asignar un nuevo material al representador de cuatro botones. Esto ya no es necesario y se recomienda mover texturas de icono personalizadas a iconSet. Se conservan los iconos y materiales personalizados existentes. Sin embargo, serán menos óptimos hasta que se actualicen.
Para actualizar los recursos de todos los botones del proyecto al nuevo formato recomendado, use ButtonConfigHelperMigrationHandler.
(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)

![Cuadro de diálogo actualizar ventana](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Si no se encuentra un icono en el conjunto de iconos predeterminado durante la migración, se creará un conjunto de iconos personalizado en MixedRealityToolkit.Generated/CustomIconSets. Un cuadro de diálogo indicará que esto ha tenido lugar.

![Notificación de icono personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>Actualización de 2.2.0 a 2.3.0

- [Cambios en la API](#api-changes-in-230)

### <a name="api-changes-in-230"></a>Cambios de API en la versión 2.3.0

**ControllerPoseSynchronizer**

El campo privado ControllerPoseSynchronizer.handedness se ha marcado como obsoleto. Esto debería tener un impacto mínimo en las aplicaciones, ya que el campo no es visible fuera de su clase.

Se ha quitado el setter de la propiedad ControllerPoseSynchronizer.Handedness pública ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**MSBuild para Unity**

Esta versión de MRTK usa una versión más reciente de MSBuild para Unity que las versiones anteriores. Durante la carga del proyecto, si la versión anterior aparece en el manifiesto del administrador de paquetes de Unity, aparecerá el cuadro de diálogo de configuración, con la opción Habilitar MSBuild para Unity activada. La aplicación realizará una actualización.

**ScriptingUtilities**

La clase ScriptingUtilities se ha marcado como obsoleta y se ha reemplazado por ScriptUtilities, en el ensamblado Microsoft.MixedReality.Toolkit.Editor.Utilities. La nueva clase refina el comportamiento anterior y agrega compatibilidad para quitar definiciones de scripting.

Aunque el código existente seguirá funcionando en la versión 2.3.0, se recomienda actualizar a la nueva clase.

**ShellHandRayPointer**

Los miembros lineRendererSelected y lineRendererNoTarget de la clase ShellHandRayPointer se han reemplazado por lineMaterialSelected y lineMaterialNoTarget, respectivamente ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).

Reemplace lineRendererSelected por lineMaterialSelected o lineRendererNoTarget por lineMaterialNoTarget para resolver errores de compilación.

**StartupBehavior del observador espacial**

Los observadores espaciales basados en la clase ahora respetan el valor de StartupBehavior cuando se vuelve a habilitar `BaseSpatialObserver` ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).

No se requiere ningún cambio para aprovechar esta corrección.

**Se han actualizado los requisitos previos del control de la experiencia de usuario para usar PressableButton.**

Los siguientes elementos prefab ahora usan el componente PressableButton en lugar de TouchHandler para la interacción cercana ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))

- AnimationButton
- Botón
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- CheckBox
- RadialSet
- ToggleButton
- ToggleSwitch
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

El código de la aplicación puede requerir la actualización debido a este cambio.

**Espacio de nombres WindowsMixedRealityUtilities**

El espacio de nombres de WindowsMixedRealityUtilities ha cambiado de Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input a Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).

Actualice las #using para resolver errores de compilación.

## <a name="updating-210-to-220"></a>Actualización de 2.1.0 a 2.2.0

- [Cambios en la API](#api-changes-in-220)

### <a name="api-changes-in-220"></a>Cambios de API en la versión 2.2.0

**IMixedRealityBoundarySystem.Contains**

Anteriormente, este método tomaba una enumeración experimental específica definida por Unity. Ahora toma una enumeración definida por MRTK que es idéntica a la enumeración de Unity. Este cambio ayuda a preparar MRTK para las FUTURAS API de límites de Unity.

**MixedRealityServiceProfileAttribute**

Para describir mejor los requisitos para admitir un perfil, MixedRealityServiceProfileAttribute se ha actualizado para agregar una colección opcional de tipos excluidos. Como parte de este cambio, se ha cambiado la propiedad ServiceType de Type a Type[] y se ha cambiado el nombre a RequiredTypes.

También se ha agregado una segunda propiedad, ExcludedTypes.

## <a name="updating-200-to-210"></a>Actualización de 2.0.0 a 2.1.0

- [Cambios en la API](#api-changes-in-210)
- [Cambios de perfil](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>Cambios de API en la versión 2.1.0

**BaseNearInteractionTouchable**

se `BaseNearInteractionTouchable` ha modificado para marcar el método como `OnValidate` virtual. Las clases que `BaseNearInteractionTouchable` extienden (por ejemplo: `NearInteractionTouchableUnityUI` ) se han actualizado para reflejar este cambio.

**ColliderNearInteractionTouchable**

La clase `ColliderNearInteractionTouchable` está desusada. Actualice las referencias de código para usar `BaseNearInteractionTouchable` .

**IMixedRealityMouseDeviceManager**

**_Añadido_**

`IMixedRealityMouseDeviceManager` se han agregado las `CursorSpeed` propiedades `WheelSpeed` y . Estas propiedades permiten a las aplicaciones especificar un valor multiplicador por el que se escalará la velocidad del cursor y la rueda, respectivamente.

Se trata de un cambio importante y requiere que se modifiquen las implementaciones existentes del administrador de dispositivos del mouse.

>[!NOTE]
>Este cambio no es compatible con versiones anteriores de la versión 2.0.0.

**_Obsoleto_**

La `MouseInputProfile` propiedad se ha marcado como obsoleta y se quitará de una versión futura de Microsoft Mixed Reality Toolkit. Se recomienda que el código de aplicación ya no use esta propiedad.

**Interactuable**

Los siguientes métodos y propiedades han quedado en desuso y se quitarán de una versión futura de Microsoft Mixed Reality Toolkit. La recomendación es actualizar el código de la aplicación según las instrucciones contenidas en el atributo Obsoleto y que se muestran en la consola.

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

**NearInteractionTouchableSurface**

La `NearInteractionTouchableSurface` clase se ha agregado y ahora actúa como clase base para y `NearInteractionTouchable` `NearInteractionTouchableUnityUI` .

### <a name="profile-changes-in-210"></a>Cambios de perfil en la versión 2.1.0

**Perfil de seguimiento de manos**

La malla de mano y las visualizaciones conjuntas ahora tienen un editor y una configuración de reproductor independientes. El perfil de seguimiento de manos se ha actualizado para permitir establecer estas visualizaciones en . Nothing, Everything, Editor o Player.

![Modos de visualización con la mano](../release-notes/images/HandTrackingVisualizationModes.png)

Es posible que sea necesario actualizar los perfiles de seguimiento de mano personalizados para que funcionen correctamente con la versión 2.1.0.

>[!NOTE]
>Este cambio no es compatible con versiones anteriores de la versión 2.0.0.

**Perfil de simulación de entrada**

Se ha actualizado el sistema de simulación de entrada, que cambia algunos valores en el perfil de simulación de entrada. Algunos cambios no se pueden migrar automáticamente y los usuarios pueden encontrar que los perfiles usan valores predeterminados.

1. Todos los enlaces keycode y de botón del mouse del perfil se han reemplazado por una estructura genérica, que almacena el tipo de enlace (clave o mouse), así como el código de enlace real (KeyCode o número de botón del `KeyBinding` mouse respectivamente). La estructura tiene su propio inspector, que permite la visualización unificada y ofrece una herramienta de "enlace automático" para establecer rápidamente los enlaces de teclado presionando la clave correspondiente en lugar de seleccionarla en una lista desplegable enorme.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` anteriormente se incluía en la `MouseLookButton` enumeración como `InputSimulationMouseButton.Focused` , ahora es una opción independiente. Cuando esté habilitada, la cámara seguirá girando con el mouse después de soltar el botón hasta que se presione la tecla de escape.
1. `HandDepthMultiplier` El valor predeterminado se ha reducido de 0,1 a 0,03 para dar cabida a algunos cambios en la simulación de entrada. Si la cámara se mueve demasiado rápido al desplazarse, intente reducir este valor.
1. Se han quitado las teclas para girar las manos, la rotación de las manos ahora también se controla mediante el mouse. Mantener presionado (Ctrl) junto con la tecla de manipulación de la mano `HandRotateButton` izquierda/derecha (LShift/Espacio) habilitará la rotación de la mano.
1. Se ha introducido un nuevo eje "UpDown" en la lista de ejes de entrada. Esto controla el movimiento de la cámara en vertical y tiene como valor predeterminado las teclas Q/E, así como los botones del desencadenador del controlador.

Para obtener más información sobre estos cambios, consulte el artículo sobre [el servicio de simulación de](../features/input-simulation/input-simulation-service.md) entrada.

**Perfil del proveedor de datos del mouse**

El perfil del proveedor de datos del mouse se ha actualizado para exponer las propiedades `CursorSpeed` y `WheelSpeed` nuevas. Los perfiles personalizados existentes tendrán automáticamente valores predeterminados proporcionados. Cuando se guarde el perfil, estos nuevos valores se conservarán.

**Perfil de asignación de controlador**

Algunos ejes y tipos de entrada se han actualizado en la versión 2.1.0, especialmente en torno a la plataforma OpenVR. Asegúrese de seleccionar **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** al actualizar. Esto actualizará los perfiles de asignación de controladores personalizados con los ejes y los datos actualizados, al tiempo que deja intactas las acciones de entrada asignadas de forma personalizada.

## <a name="updating-rc2-to-200"></a>Actualización de RC2 a 2.0.0

Entre las versiones RC2 y 2.0.0 del kit de herramientas de Microsoft Mixed Reality, se realizaron cambios que pueden afectar a los proyectos existentes. En este documento se describen esos cambios y cómo actualizar los proyectos a la versión 2.0.0.

- [Cambios en la API](#api-changes-in-200)
- [Cambios en el nombre del ensamblado](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>Cambios de API en la versión 2.0.0

Desde el lanzamiento de RC2, ha habido una serie de cambios en la API, incluidos algunos que pueden interrumpir los proyectos existentes. En las secciones siguientes se describen los cambios que se han producido entre las versiones RC2 y 2.0.0.

**MixedRealityToolkit**

Las siguientes propiedades públicas del objeto MixedRealityToolkit han quedado en desuso.

- `RegisteredMixedRealityServices` ya no contiene la colección de servicios de extensiones registrados y proveedores de datos.

Para acceder a los servicios de extensión, use `MixedRealityServiceRegistry.TryGetService<T>` . Para acceder a los proveedores de datos, convierte la instancia de servicio en [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) y usa `GetDataProvider<T>` .

Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) o en su lugar para las siguientes propiedades en [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) desuso

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

La [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) clase es el reemplazo de los accessors del sistema estático (por ejemplo, BoundarySystem) que se encuentran en el objeto `MixedRealityToolkit` .

>[!IMPORTANT]
>Los accessors del sistema han quedado en desuso en la versión 2.0.0 y se quitarán en una versión futura `MixedRealityToolkit` de MRTK.

En el ejemplo de código siguiente se muestra el patrón antiguo y el nuevo.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

El uso de la nueva clase CoreSystem garantizará que el código de la aplicación no necesite actualizarse si cambia la aplicación para usar un registrador de servicios diferente (por ejemplo, uno de los administradores de servicios experimentales).

**IMixedRealityRaycastProvider**

Con la adición de IMixedRealityRaycastProvider, se cambió el perfil de configuración del sistema de entrada. Si tiene un perfil personalizado, puede recibir los errores de la siguiente imagen al ejecutar la aplicación.

![Selección del proveedor de Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

Para corregirlos, agregue una instancia de IMixedRealityRaycastProvider al perfil del sistema de entrada.

![Selección del proveedor de Raycast 2](../release-notes/images/SelectRaycastProvider.png)

**Sistema de eventos**

- Los `IMixedRealityEventSystem` métodos de API `Register` `Unregister` antiguos y se han marcado como obsoletos. Se conservan por compatibilidad con versiones anteriores.
- `InputSystemGlobalListener` se ha marcado como obsoleto. Su funcionalidad no ha cambiado.
- `BaseInputHandler` La clase base se ha cambiado de `InputSystemGlobalListener` a `InputSystemGlobalHandlerListener` . Se trata de un cambio importante para cualquier descendiente de `BaseInputHandler` .

**_Motivación detrás del cambio_**

La API anterior del sistema de eventos y podría causar varios problemas en tiempo de `Register` `Unregister` ejecución, siendo principalmente:

- Si un componente se registra para eventos globales, recibiría eventos de entrada globales de *todos los* tipos.
- Si uno de los componentes de un objeto se registra para eventos de entrada globales, todos los componentes de este objeto recibirán eventos de entrada globales de *todos los* tipos.
- Si dos componentes del mismo objeto se registran en eventos globales y, a continuación, uno está deshabilitado en tiempo de ejecución, el segundo deja de recibir eventos globales.

Nueva API `RegisterHandler` y `UnregisterHandler` :

- Proporciona un control explícito y granular sobre qué eventos de entrada se deben escuchar globalmente y cuáles deben centrarse.
- Permite que varios componentes del mismo objeto escuche eventos globales de forma independiente entre sí.

**_Migración_**

- Si ha llamado a `Register` / `Unregister` la API directamente antes, reemplace estas llamadas por llamadas a `RegisterHandler` / `UnregisterHandler` . Use interfaces de controlador que implemente como parámetros genéricos. Si implementa varias interfaces y varias de ellas escuchan eventos de entrada globales, llame `RegisterHandler` a varias veces.
- Si ha heredado de , cambie `InputSystemGlobalListener` la herencia a `InputSystemGlobalHandlerListener` . Implemente `RegisterHandlers` `UnregisterHandlers` métodos abstractos y . En la llamada de implementación ( ) para registrarse en todas las interfaces de controlador para las `inputSystem.RegisterHandler` que desea escuchar eventos `inputSystem.UnregisterHandler` globales.
- Si ha heredado de `BaseInputHandler` , implemente los `RegisterHandlers` métodos `UnregisterHandlers` abstractos y (igual que para `InputSystemGlobalListener` ).

**_Ejemplos de migración_**

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

**Reconocimiento espacial**

Las interfaces IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver han realizado varios cambios importantes, como se describe a continuación.

**_Cambios_**

Se ha cambiado el nombre de los métodos siguientes para describir mejor su uso.

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` se ha cambiado el nombre a `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` para aclarar su uso.

**_Adiciones_**

En función de los comentarios de los clientes, se ha agregado soporte técnico para la eliminación sencilla de los datos de reconocimiento espacial observados anteriormente.

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**Solucionadores**

Algunos componentes del solucionador y la clase de administrador SolverHandler han cambiado para corregir varios errores y para un uso más intuitivo.

**_SolverHandler_**

- La clase ya no se extiende desde `ControllerFinder`
- `TrackedObjectToReference` propiedad pública en desuso y se ha cambiado el nombre a `TrackedTargetType`
- `TrackedObjectType` en desuso a & de controlador derecho. En su lugar, use los valores o y actualice la nueva propiedad para limitar el seguimiento al controlador izquierdo `MotionController` o `HandJoint` `TrackedHandedness` derecho.

**_InBetween_**

- `TrackedObjectForSecondTransform` propiedad pública en desuso y se ha cambiado el nombre a `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` se ha quitado. Para actualizar el solucionador, modifique las propiedades públicas (es decir, `SecondTrackedObjectType`)

**_Surface Surface (Surface )Surface (Surface )Surface (Surface_**

- `MaxDistance` propiedad pública en desuso y se ha cambiado el nombre a `MaxRaycastDistance`
- `CloseDistance` propiedad pública en desuso y se ha cambiado el nombre a `ClosestDistance`
- El valor predeterminado `RaycastDirectionMode` de es ahora qué raycasts en la dirección de la transformación de destino con seguimiento `TrackedTargetForward` hacia delante
- `OrientationMode` Se ha cambiado el nombre de los valores de enumeración y , `Vertical` `Full` a y `TrackedTarget` `SurfaceNormal` respectivamente.
- `KeepOrientationVertical` se ha agregado la propiedad public para controlar si la orientación de GameObject asociada sigue siendo vertical.

**Botones**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) ahora tiene `DistanceSpaceMode` la propiedad establecida en como valor `Local` predeterminado. Esto permite escalar los botones mientras se pueden presionar.

**Esfera de recorte**

La interfaz ClippingSphere ha cambiado para reflejar las API que se encuentran en ClippingBox y ClippingPlane.

La propiedad Radius de ClippingSphere ahora se calcula implícitamente en función de la escala de transformación. Antes de que los desarrolladores tengan que especificar el radio de ClippingSphere en el inspector. Si desea cambiar el radio, solo tiene que actualizar la escala de transformación de la transformación como lo haría normalmente.

**NearInteractionTouchable y PokePointer**

- NearInteractionTouchable ya no controla el lienzo de la interfaz de usuario de Unity. La clase NearInteractionTouchableUnityUI debe usarse ahora para los elementos táctiles de la interfaz de usuario de Unity.
- ColliderNearInteractionTouchable es la nueva clase base para los dispositivos táctiles basados en colisiondores, es decir, todos los que se pueden tocar excepto NearInteractionTouchableUnityUI.
- BaseNearInteractionTouchable.DistFront se ha movido y se ha cambiado el nombre a Contrapunto.TouchableDistance Esta es la distancia y con la que el usuario puede interactuar con los objetos táctiles. Anteriormente, cada elemento táctil tenía su propia distancia máxima de interacción, pero ahora se define en el elemento Depointer, lo que permite una mejor optimización.
- Se ha cambiado el nombre de BaseNearInteractionTouchable.DistBack aThreshold. Esto deja claro que La propiedad DebounceThreshold es el homólogo de DebounceThreshold. Se activa un control táctil cuando se cruza el control DebounceThreshold y se libera cuando se cruza DebounceThreshold.

**ReadOnlyAttribute**

El `Microsoft.MixedReality.Toolkit` espacio de nombres se ha agregado a , y `ReadOnlyAttribute` `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute` .

**PointerClickHandler**

La clase `PointerClickHandler` está desusada. Debe `PointerHandler` usarse en su lugar, proporciona la misma funcionalidad.

**Compatibilidad con el clicker de HoloLens**

Las asignaciones del controlador del clicker de HoloLens han cambiado de ser sin control [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) a ser un control sin [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) control. Para tener esto en cuenta, se ejecutará un actualizador automático la primera vez que abra el perfil de ControllerMapping. Abra los perfiles personalizados al menos una vez después de actualizar a 2.0.0 para desencadenar este paso de migración único.

**InteractableHighlight**

La clase `InteractableHighlight` está desusada. En `InteractableOnFocus` su `FocusInteractableStates` lugar, se deben usar la clase y el recurso. Para crear un nuevo recurso para , haga clic con el botón derecho en la ventana del proyecto y seleccione Create Mixed Reality Toolkit Interactable Theme (Crear un tema `Theme` `InteractableOnFocus`   >    >  *interactuable*  >  del kit de herramientas).

**HandInteractionPanZoom**

`HandInteractionPanZoom` se ha movido al espacio de nombres de la interfaz de usuario, ya que no era un componente de entrada. `HandPanEventData` también se ha movido a este espacio de nombres y se ha simplificado para que se corresponda con otros datos de eventos de la interfaz de usuario.

### <a name="assembly-name-changes-in-200"></a>Cambios en el nombre del ensamblado en la versión 2.0.0

En la versión 2.0.0, todos los nombres de ensamblado oficial de Mixed Reality Toolkit y sus archivos de definición de ensamblado asociados (.asmdef) se han actualizado para ajustarse al siguiente patrón.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

En algunos casos, se han combinado varios ensamblados para crear una mejor unidad de su contenido. Si el proyecto usa archivos .asmdef personalizados, es posible que deba actualizarse.

En las tablas siguientes se describe cómo se asignan los nombres de archivo RC2 .asmdef a la versión 2.0.0. Todos los nombres de ensamblado coinciden con el nombre de archivo .asmdef.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | Microsoft.MixedReality.Toolkit.asmdef |
| MixedRealityToolkit.Core.BuildAndDeploy.asmdef | Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef |
| MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef | Quitado, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef |
| MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef | Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef
| MixedRealityToolkit.Core.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef |
| MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef | Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef |
| MixedRealityToolkit.Core.UtilitiesAsync.asmdef | Microsoft.MixedReality.Toolkit.Async.asmdef |
| MixedRealityToolkit.Core.Utilities.Editor.asmdef | Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef |
| MixedRealityToolkit.Utilities.Gltf.asmdef | Microsoft.MixedReality.Toolkit.Gltf.asmdef |
| MixedRealityToolkit.Utilities.Gltf.Importers.asmdef | Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef |

**MixedRealityToolkit.Providers**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Providers.OpenVR.asmdef | Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef |
| MixedRealityToolkit.Providers.WindowsMixedReality.asmdef | Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef |
| MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef | Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef |

**MixedRealityToolkit.Services**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Services.BoundarySystem.asmdef | Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef |
| MixedRealityToolkit.Services.CameraSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef |
| MixedRealityToolkit.Services.DiagnosticsSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef |
| MixedRealityToolkit.Services.InputSimulation.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef |
| MixedRealityToolkit.Services.InputSimulation.Editor.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef |
| MixedRealityToolkit.Services.InputSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef |
| MixedRealityToolkit.Services.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef |
| MixedRealityToolkit.Services.SceneSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef |
| MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef |
| MixedRealityToolkit.Services.TeleportSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef |

**MixedRealityToolkit.SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.SDK.asmdef | Microsoft.MixedReality.Toolkit.SDK.asmdef |
| MixedRealityToolkit.SDK.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef |

**MixedRealityToolkit.Examples**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Examples.asmdef | Microsoft.MixedReality.Toolkit.Examples.asmdef |
| MixedRealityToolkit.Examples.Demos.Gltf.asmdef | Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef |
| MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef | Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef | Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef |