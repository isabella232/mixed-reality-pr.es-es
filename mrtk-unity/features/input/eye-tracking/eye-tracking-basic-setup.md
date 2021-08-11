---
title: Configuración básica de seguimiento ocular
description: Configuración del seguimiento de los ojos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, seguimiento ocular,
ms.openlocfilehash: d8b47639729381a41e4fe1e1db86700bf9323860553934a6da4dfa4b15de49eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197461"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Introducción al seguimiento ocular en MRTK

En esta página se explica cómo configurar la escena de MRTK de Unity para usar el seguimiento ocular en la aplicación.
A continuación se da por supuesto que está empezando con una escena nueva.
Como alternativa, puede consultar nuestros ejemplos de seguimiento ocular de [MRTK](../../example-scenes/eye-tracking-examples-overview.md) ya configurados con una gran cantidad de ejemplos excelentes sobre los que puede basar directamente.

## <a name="eye-tracking-requirements-checklist"></a>Lista de comprobación de requisitos de seguimiento de los ojos

Para que el seguimiento de los ojos funcione correctamente, se deben cumplir los siguientes requisitos.
Si no está de acuerdo con el seguimiento de los HoloLens 2 y cómo se configura el seguimiento de los ojos en MRTK, no se preocupe.
A continuación se detalla cómo abordar cada uno de ellos.

1. Se _debe agregar un "proveedor de datos de_ mirada con los ojos" al sistema de entrada. Esto proporciona datos de seguimiento ocular de la plataforma.
2. La _funcionalidad "GazeInput"_ debe estar habilitada en el manifiesto de aplicación.
   **Esta funcionalidad se puede establecer en Unity 2019, pero en Unity 2018 y versiones anteriores esta funcionalidad solo está disponible en Visual Studio y a través de la herramienta de compilación MRTK.**
3. El HoloLens **debe** calibrarse con los ojos para el usuario actual. Consulte nuestro ejemplo para detectar si un usuario está calibrado con los [ojos o no.](eye-tracking-is-user-calibrated.md)

### <a name="a-note-on-the-gazeinput-capability"></a>Una nota sobre la funcionalidad GazeInput

Las herramientas de compilación proporcionadas por MRTK (es decir, Mixed Reality Toolkit -> Utilities -> Build Window) pueden habilitar automáticamente la funcionalidad GazeInput. Para ello, debe asegurarse de que la "Funcionalidad de entrada de mirada" está activada en la pestaña "Opciones de compilación de Appx":

![Herramientas de compilación de MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

Estas herramientas encontrarán el manifiesto de AppX una vez completada la compilación de Unity y agregarán manualmente la funcionalidad GazeInput.
**Antes de Unity 2019,** esta herramienta NO estaba activa cuando se usaba la ventana de compilación integrada de Unity (es decir, archivo -> compilación Configuración).

Antes de Unity 2019, al usar la ventana de compilación de Unity, la funcionalidad deberá agregarse manualmente después de la compilación de Unity, como se muestra a continuación:

1. Abra el proyecto Visual Studio compilado y, a continuación, abra _"Package.appxmanifest"_ en la solución.
2. Asegúrese de activar la casilla _"GazeInput"_ en _Funcionalidades._ Si no ve una funcionalidad _"GazeInput",_ compruebe que el sistema cumple los [requisitos previos](/windows/mixed-reality/develop/install-the-tools) para usar MRTK (en particular, la versión del SDK de Windows).

_Tenga en cuenta lo siguiente:_ Solo tiene que hacerlo si compila en una nueva carpeta de compilación.
Esto significa que si ya había creado el proyecto de Unity y configurado appxmanifest antes y ahora tiene como destino la misma carpeta de nuevo, no tendrá que volver a aplicar los cambios.

## <a name="setting-up-eye-tracking-step-by-step"></a>Configuración paso a paso del seguimiento de los ojos

### <a name="setting-up-the-scene"></a>Configuración de la escena

Para configurar _MixedRealityToolkit,_ simplemente haga clic _en "Mixed Reality Toolkit -> Configurar..."._ en la barra de menús.

![Configuración de MRTK](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>Configuración de los perfiles de MRTK necesarios para el seguimiento ocular

Después de configurar la escena de MRTK, se le pedirá que elija un perfil para MRTK.
Simplemente puede seleccionar _DefaultMixedRealityToolkitConfigurationProfile_ y, a continuación, seleccionar la _opción "Copiar & Personalizar"._

![Perfil de MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider&quot;></a>Creación de un &quot;proveedor de datos de mirada con los ojos&quot;

- Haga clic en _la pestaña &quot;Entrada&quot;_ en el perfil de MRTK.
- Para editar el valor predeterminado ( _&quot;DefaultMixedRealityInputSystemProfile"),_ haga clic en el _botón "Clonar"_ situado junto a él. Aparece _el menú "Clonar_ perfil". Simplemente haga clic _en "Clonar"_ en la parte inferior de ese menú.
- Haga doble clic en el nuevo perfil de entrada, expanda _"Proveedores de_ datos de entrada" y seleccione _"+ Agregar proveedor de datos"._
- Cree un nuevo proveedor de datos:
  - En **Tipo,** _seleccione "Microsoft.MixedReality.Toolkit. WindowsMixedReality.Input"_  ->  _'WindowsMixedRealityEyeGazeDataProvider'_
  - En **Plataformas,** seleccione _"Windows Universal"._

![Proveedor de datos MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulación del seguimiento ocular en el editor de Unity

Puede simular la entrada de seguimiento ocular en el editor de Unity para asegurarse de que los eventos se desencadenan correctamente antes de implementar la aplicación en el HoloLens 2.
La señal de mirada con los ojos se simula simplemente usando la ubicación de la cámara como origen de la mirada con los ojos y el vector hacia delante de la cámara como dirección de la mirada con los ojos.
Aunque esto es excelente para las pruebas iniciales, tenga en cuenta que no es una buena imitación para los movimientos rápidos de los ojos.
Para ello, es mejor garantizar pruebas frecuentes de las interacciones basadas en los ojos en el HoloLens 2.

1. **Habilite el seguimiento ocular simulado:**
    - Haga clic en la _pestaña "Entrada"_ en el perfil de configuración de MRTK.
    - Desde allí, vaya a _"Input Data Providers"_(Proveedores de datos de  ->  _entrada) "Input Simulation Service" (Servicio de simulación de entrada)._
    - Clone _"DefaultMixedRealityInputSimpulationProfile"_ para realizar cambios en él.
    - Active la _casilla "Simular posición de los ojos"._

    ![Simulación de ojos de MRTK](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **Deshabilitar el cursor de mirada** con la cabeza predeterminado: en general, se recomienda evitar mostrar un cursor de mirada con los ojos o si es absolutamente necesario para que sea _muy_ sutil.
Se recomienda ocultar el cursor de mirada con la cabeza predeterminado que está asociado al perfil de puntero de mirada de MRTK de forma predeterminada.
    - Vaya al perfil de configuración de MRTK -> _'Input'_  ->  _'Pointers'_
    - Clone _"DefaultMixedRealityInputPointerProfile"_ para realizar cambios en él.
    - En la parte superior de _"Pointer Configuración",_ debe asignar un objeto prefab de cursor invisible a _"GazeCursor"._ Para ello, seleccione el prefab _"EyeGazeCursor"_ de MRTK Foundation.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Habilitación de la mirada con los ojos en el proveedor de mirada

En HoloLens v1, la mirada con la cabeza se usó como técnica de apuntamiento principal.
Aunque la mirada con la cabeza sigue estando disponible a través de _GazeProvider_ en MRTK, que está conectado a la [cámara,](https://docs.unity3d.com/ScriptReference/Camera.html)puede comprobar el uso de la mirada con los ojos activando la casilla _"IsEyeTrackingEnabled"_ en la configuración de mirada del perfil de puntero de entrada.

>[!NOTE]
>Los desarrolladores pueden alternar entre la mirada con los ojos y la mirada con la cabeza en el código cambiando la propiedad _"IsEyeTrackingEnabled"_ de _"GazeProvider"._  

>[!IMPORTANT]
>Si no se cumple alguno de los requisitos de seguimiento ocular, la aplicación volverá automáticamente a la mirada basada en la cabeza.

### <a name="accessing-eye-gaze-data"></a>Acceso a los datos de mirada con los ojos

Ahora que la escena está configurada para usar el seguimiento ocular, echemos un vistazo a cómo acceder a ella en los scripts: Acceso a los datos de seguimiento de los ojos a través de [EyeGazeProvider](eye-tracking-eye-gaze-provider.md) y [selecciones](eye-tracking-target-selection.md)de destino compatibles con los ojos.

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Prueba de la aplicación de Unity en un HoloLens 2

La compilación de la aplicación con seguimiento ocular debe ser similar a la forma en que compilaría otras aplicaciones HoloLens 2 MRTK. Asegúrese de que ha habilitado la funcionalidad *"Entrada* de mirada", tal y como se describió anteriormente en la sección [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability)(Nota sobre la funcionalidad GazeInput).

#### <a name="eye-calibration"></a>Calibración de los ojos

Por último, no olvide realizar la calibración de los ojos en la HoloLens 2.
El sistema de seguimiento ocular no devolverá ninguna entrada si el usuario no está calibrado.
La manera más fácil de llegar a la calibración es volteando el visor y retrociendo.
Debería aparecer una notificación del sistema que le da la bienvenida como nuevo usuario y le pide que pase por la calibración de los ojos.
Como alternativa, puede encontrar la calibración de los ojos en la configuración del sistema: Configuración > System > Calibration > Run eye calibration (Calibración del sistema > calibración de los ojos).

#### <a name="eye-tracking-permission"></a>Permiso de seguimiento ocular

Al iniciar la aplicación en el HoloLens 2 por primera vez, aparecerá un mensaje en el que se le pedirá al usuario permiso para usar el seguimiento ocular.
Si no aparece, suele ser una indicación de que no se estableció la funcionalidad _"GazeInput"._

Después de que el símbolo del sistema de permisos se muestre una vez, no se volverá a mostrar automáticamente.
Si _"ha denegado el_ permiso de seguimiento ocular", puede restablecerlo en Configuración -> Privacidad -> Apps.

---

Esto debería comenzar a usar el seguimiento ocular en la aplicación mrtk de Unity.
No olvide consultar nuestros tutoriales y ejemplos de seguimiento ocular de [MRTK](../../example-scenes/eye-tracking-examples-overview.md) que muestran cómo usar la entrada de seguimiento ocular y proporcionar scripts que puede reutilizar en sus proyectos.

---
[Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit).](eye-tracking-main.md)