---
title: Selección del destino de seguimiento de los ojos
description: Acceso a datos de mirada con los ojos y eventos específicos de mirada con los ojos para seleccionar destinos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking,
ms.openlocfilehash: aab2f35259db183f4f3edb4fffc2b3e7a066bccf9c69e492c90ee193388b8b7a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189605"
---
# <a name="eye-supported-target-selection"></a>Selección de destino compatible con los ojos

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

En esta página se de analizan las distintas opciones para acceder a los datos de mirada con los ojos y los eventos específicos de la mirada con los ojos para seleccionar destinos en MRTK. El seguimiento de los ojos permite selecciones de destino rápidas y sin esfuerzo  mediante una combinación de información sobre lo que un usuario está viendo con entradas adicionales, como el seguimiento de manos y los comandos _de voz:_

- Buscar & _"Seleccionar"_ (comando de voz predeterminado)
- Buscar & _"Desenlazar"_ o _"Pop"_ (comandos de voz personalizados)
- Buscar & Bluetooth botón
- Mire & Acercar (es decir, mantenga la mano delante de usted y lleve el dedo índice y el dedo índice)
  - Tenga en cuenta que para que esto funcione, es necesario deshabilitar los rayos [de las manos.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)

Para seleccionar contenido holográfico mediante la mirada con los ojos, hay varias opciones:

[**1. Use el puntero de foco principal:**](#1-use-generic-focus-and-pointer-handlers)

Esto se puede entender como el cursor priorizado.
De forma predeterminada, si las manos están a la vista, serían rayos de mano.
Si no hay manos a la vista, el puntero con prioridad sería la mirada con la cabeza o los ojos.
Por lo tanto, tenga en cuenta que, en función del diseño actual, la mirada con los ojos o la cabeza se suprime como entrada de cursor si se usan rayos de mano.

Por ejemplo:

Un usuario quiere seleccionar un botón holográfico lejano.
Como desarrollador, quiere proporcionar una solución flexible que permita al usuario realizar estas tareas en varias condiciones:

- Subir hasta el botón y subirlo
- Míralo desde una distancia y diga "seleccionar"
- Dirigir el botón mediante un rayo de mano y realizar una acción de acercamiento. En este caso, la solución más flexible es usar el controlador de foco principal, ya que le notificará cada vez que el puntero de foco principal con prioridad actual desencadene un evento. Tenga en cuenta que si los rayos de mano están habilitados, el puntero de foco de mirada con la cabeza o los ojos se deshabilita en cuanto las manos se ven.

> [!IMPORTANT]
> Tenga en cuenta que si los rayos de mano están habilitados, el puntero de foco de mirada con la cabeza o los ojos se deshabilita en cuanto las manos se ven. Si desea admitir una interacción [ _de "buscar_ y acercar", debe deshabilitar el rayo de mano](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray). En nuestras escenas de ejemplo de seguimiento de los ojos, hemos deshabilitado el rayo de la mano para permitir mostrar interacciones más complejas mediante los ojos y los movimientos de las manos; vea por ejemplo Posición compatible con los [ojos.](eye-tracking-eyes-and-hands.md)

[**2. Use el foco de los ojos y los rayos de las manos al mismo tiempo:**](#2-independent-eye-gaze-specific-eyetrackingtarget)

Puede haber instancias en las que quiera ser más específico qué tipo de punteros de foco pueden desencadenar determinados eventos y permitir el uso simultáneo de varias técnicas de interacción lejanas.

Por ejemplo: en la aplicación, un usuario puede usar rayos de mano lejanos para manipular algunas configuraciones mecánicas holográficas, por ejemplo, agarrar y retener algunas partes lejanas del motor holográfico y mantenerlas en su lugar. Al hacerlo, el usuario debe seguir una serie de instrucciones y registrar su progreso marcando algunas casillas. Si el usuario no tiene las manos ocupadas, sería instintivo tocar simplemente la casilla o seleccionarla con un rayo de mano. Sin embargo, si el usuario tiene las manos ocupadas, como en nuestro caso, con algunas partes holográficas del motor en su lugar, quiere permitir que el usuario se desplace sin problemas por las instrucciones con la mirada con los ojos y simplemente mire una casilla y diga "check it!".

Para habilitar esto, debe usar un script EyeTrackingTarget específico de los ojos que sea independiente de los principales focusHandlers de MRTK y que se analizará más adelante.

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. Usar controladores genéricos de puntero y foco

Si el seguimiento de los ojos está configurado correctamente (consulte Configuración básica de [MRTK](eye-tracking-basic-setup.md)para usar el seguimiento de los ojos), permitir a los usuarios seleccionar hologramas con los ojos es lo mismo que para cualquier otra entrada de foco (por ejemplo, mirada con la cabeza o rayo de la mano). Esto proporciona la gran ventaja de una manera flexible de interactuar con los hologramas mediante la definición del tipo de foco principal en el perfil de puntero de entrada de MRTK en función de las necesidades del usuario, al tiempo que deja el código intacto. Esto permite cambiar entre la mirada con la cabeza o los ojos sin cambiar una línea de código o reemplazar los rayos de las manos por el objetivo de los ojos para interacciones lejanas.

### <a name="focusing-on-a-hologram"></a>Centrarse en un holograma

Para detectar cuándo se centra un holograma, use la interfaz _"IMixedRealityFocusHandler",_ que proporciona dos miembros de interfaz: _OnFocusEnter_ y _OnFocusExit._

Este es un ejemplo sencillo de [ColorTap.cs para](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) cambiar el color de un holograma al ser visto.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a>Selección de un holograma centrado

Para seleccionar un holograma centrado, use _PointerHandler_ para escuchar eventos de entrada para confirmar una selección.
Por ejemplo, agregar _IMixedRealityPointerHandler_ hará que reaccionen a una entrada de puntero simple.
La _interfaz IMixedRealityPointerHandler_ requiere la implementación de los tres miembros de interfaz siguientes: _OnPointerUp_, _OnPointerDown_ y _OnPointerClicked_.

En el ejemplo siguiente, cambiamos el color de un holograma; para ello, lo miramos y nos acercamos o indicamos "seleccionar".
La acción necesaria para desencadenar el evento se define mediante la cual podemos establecer el tipo de en el Editor de Unity: de forma predeterminada, es la acción `eventData.MixedRealityInputAction == selectAction` `selectAction` "Seleccionar". Los tipos de [MixedRealityInputActions](../input-actions.md) disponibles se pueden configurar en el perfil de MRTK a través de acciones de entrada de entrada del perfil de configuración de _MRTK._  ->    ->  

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a>BaseEyeFocusHandler específico de la mirada con los ojos

Dado que la mirada con los ojos puede ser muy diferente a otras entradas de  puntero, es posible que quiera asegurarse de que solo reaccione a la entrada de foco si es la mirada con los ojos y actualmente es el puntero de entrada principal.
Para este propósito, usaría el que es específico del seguimiento de [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) los ojos y que deriva de [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .
Como se mencionó anteriormente, solo se desencadenará si el objetivo de la mirada con los ojos es actualmente la entrada del puntero principal (es decir, no hay ningún rayo de mano activo). Para obtener más información, [consulte Compatibilidad con la mirada con los ojos y los gestos de la mano.](eye-tracking-eyes-and-hands.md)

Este es un ejemplo de `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).
En esta demostración, hay dos hologramas 3D que se activarán en función de la parte del objeto que se examina: si el usuario mira el lado izquierdo del holograma, esa parte se moverá lentamente hacia la parte frontal orientada al usuario.
Si se mira el lado derecho, esa parte se moverá lentamente al frente.
Se trata de un comportamiento que es posible que no quiera tener activo en todo momento y también algo que es posible que no quiera desencadenar accidentalmente mediante un rayo de mano o la mirada con la cabeza.
Si se [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) adjunta, un Objeto GameObject gira mientras se mira.

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

Consulte la documentación de la API para obtener una lista completa de los eventos disponibles de [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :

- **OnEyeFocusStart:** Se desencadena una vez que el rayo de mirada *con los ojos* comienza a formar una intersección con el colisionador de este objetivo.
- **OnEyeFocusFocus:** Se *desencadena mientras* el rayo de mirada con los ojos forma una intersección con el colisionador de este objetivo.
- **OnEyeFocusStop:** Se desencadena una vez que el rayo de *mirada con los ojos deja* de formar intersección con el colisionador de este objetivo.
- **OnEyeFocusDwell:** Se desencadena una vez que el rayo de mirada con los ojos ha intersecado con el colisionador de este objetivo durante un período de tiempo especificado.

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. EyeTrackingTarget específico de la mirada con los ojos independiente

Por último, le proporcionamos una solución que le permite tratar la entrada basada en los ojos completamente independiente de otros punteros de foco a través del [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.

Esto tiene tres _ventajas:_

- Puede asegurarse de que el holograma solo reacciona a la mirada con los ojos del usuario.
- Esto es independiente de la entrada principal activa actualmente. Por lo tanto, puede procesar varias entradas a la vez, por ejemplo, combinando el objetivo rápido de los ojos con gestos de mano.
- Ya se han configurado varios eventos de Unity para que sea rápido y cómodo controlar y reutilizar los comportamientos existentes desde el Editor de Unity o mediante código.

También hay algunas _desventajas:_

- Más esfuerzo para controlar entradas independientes individualmente.
- No hay degradación elegante: solo admite la segmentación de los ojos. Si el seguimiento de los ojos no funciona, necesita alguna reserva adicional.

De forma similar a _BaseFocusHandler,_ _EyeTrackingTarget_ viene listo con varios eventos de Unity específicos de la mirada con los ojos que puede escuchar cómodamente a través del Editor de Unity (consulte el ejemplo siguiente) o mediante _AddListener()_ en el código:

- OnLookAtStart()
- WhileLookingAtTarget()
- OnLookAway()
- OnDwell()
- OnSelected()

A continuación, le llevamos a través de algunos ejemplos sobre cómo usar _EyeTrackingTarget._

### <a name="example-1-eye-supported-smart-notifications"></a>Ejemplo #1: notificaciones inteligentes compatibles con los ojos

En `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), puede encontrar un ejemplo de _"notificaciones inteligentes_ de notificación" que reaccionan a la mirada con los ojos.
Se trata de cuadros de texto 3D que se pueden colocar en la escena y que se amplían sin problemas y se dirigen hacia el usuario cuando se le mira para facilitar la legibilidad. Mientras el usuario lee la notificación, la información se muestra clara y clara. Después de leerla y alejarse de la notificación, la notificación se descartará automáticamente y se atenuará. Para lograr todo esto, hay algunos scripts de comportamiento genéricos que no son específicos del seguimiento de los ojos, como:

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

La ventaja de este enfoque es que varios eventos pueden reutilizar los mismos scripts. Por ejemplo, un holograma puede empezar a tener acceso al usuario en función de comandos de voz o después de presionar un botón virtual. Para desencadenar estos eventos, simplemente puede hacer referencia a los métodos que se deben ejecutar en el [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script que está asociado a GameObject.

Para el ejemplo de las _"notificaciones inteligentes de notificación",_ ocurre lo siguiente:

- **OnLookAtStart():** la notificación comienza a...
  - *FaceUser.Engage:* ... se dirige al usuario.
  - *ChangeSize.Engage:* ... aumentar el tamaño _(hasta una escala máxima especificada)._
  - *BlendOut.Engage:* ... comienza a combinarse en más _(después de estar en un estado de inactividad más sutil)._  

- **OnDwell():** informa al script _BlendOut_ de que la notificación se ha visto lo suficiente.

- **OnLookAway():** la notificación comienza a...
  - *FaceUser.Disengage:* ... volver a su orientación original.
  - *ChangeSize.Disengage:* ... reducir de nuevo a su tamaño original.
  - *BlendOut.Disengage:* ... comienza a combinarse: si _onDwell()_ se desencadenó, se mezcla completamente y se destruye; de lo contrario, vuelve a su estado de inactividad.

**Consideración de diseño:** La clave de una experiencia divertida aquí es ajustar cuidadosamente la velocidad de cualquiera de estos comportamientos para evitar causar molestias al reaccionar a la mirada del usuario demasiado rápido todo el tiempo.
De lo contrario, esto puede parecer muy abrumador rápidamente.

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>Ejemplo #2: la gema holográfica gira lentamente al mirarla

Al igual que en el ejemplo #1, podemos crear fácilmente un comentario de mantener el puntero para nuestras gemas holográficas en la escena (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) que girará lentamente en una dirección constante y a una velocidad constante (a diferencia del ejemplo de rotación anterior) cuando se `EyeTrackingDemo-02-TargetSelection` mira. Todo lo que necesita es desencadenar la rotación de la gema holográfica desde el evento _WhileLookingAtTarget()_ de _EyeTrackingTarget._ A continuación se incluyen algunos detalles más:

1. Cree un script genérico que incluya una función pública para rotar el GameObject al que está asociado. A continuación se muestra un ejemplo de _RotateWithConstSpeedDir.cs,_ donde podemos ajustar la dirección y la velocidad de rotación desde el Editor de Unity.

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. Agregue el script al GameObject de destino y haga referencia a la [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) _función RotateTarget()_ en el desencadenador UnityEvent, como se muestra en la captura de pantalla siguiente:

    ![Ejemplo de EyeTrackingTarget](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>Ejemplo #3: Selección de destino compatible  con la mirada con los ojos multimodal

En el ejemplo anterior, hemos mostrado lo fácil que es detectar si se busca un destino y cómo desencadenar una reacción a eso. A continuación, vamos a hacer que las gemas se desenlomen con el _evento OnSelected()_ de [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) . La parte interesante es *cómo se* desencadena la selección. permite [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) asignar rápidamente distintas formas de invocar una selección:

- _Gesto de acercar:_ al establecer "Seleccionar acción" en "Seleccionar", se usa el gesto de mano predeterminado para desencadenar la selección.
Esto significa que el usuario puede simplemente elevar la mano y acercar el dedo índice y el dedo para confirmar la selección.

- Diga _"Seleccionar":_ use el comando de voz _predeterminado "Seleccionar"_ para seleccionar un holograma.

- Diga _"Explode"_ o _"Pop":_ para usar comandos de voz personalizados, debe seguir dos pasos:
    1. Configuración de una acción personalizada como _"DestroyTarget"_
        - Vaya a _MRTK -> Input -> Input Actions_
        - Haga clic en "Agregar una nueva acción".

    2. Configure los comandos de voz que desencadenan esta acción, como _"Explode"_ o _"Pop"._
        - Vaya a _MRTK -> Input -> Speech_
        - Haga clic en "Agregar un nuevo comando de voz".
            - Asociación de la acción que acaba de crear
            - Asignar un _keycode para_ permitir desencadenar la acción a través de un botón

![Ejemplo eyeTrackingTarget de comandos de voz](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

Cuando se selecciona una gema, se expande, se hace un sonido y desaparece. Esto se controla mediante el [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script. Tiene dos opciones:

- **En el Editor de Unity:** Simplemente puede vincular el script que está asociado a cada una de nuestras plantillas de gema al evento De Unity OnSelected() en el Editor de Unity.
- **En el código:** Si no desea arrastrar y colocar objetos GameObject, también puede agregar un agente de escucha de eventos directamente al script.  
Este es un ejemplo de cómo lo hicimos en el [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>Ejemplo #4: Uso de los rayos de las manos y la entrada de mirada con los ojos juntos

Los rayos de las manos tienen prioridad sobre el objetivo de la mirada con la cabeza y los ojos. Esto significa que, si los rayos de las manos están habilitados, en el momento en que las manos se ven, el rayo de la mano actuará como puntero principal.
Sin embargo, puede haber situaciones en las que quiera usar rayos de mano mientras sigue detectando si un usuario está mirando un determinado holograma. Fácil. Básicamente, necesita dos pasos:

**1. Habilitar el** rayo de mano: para habilitar el rayo de mano, vaya a Mixed Reality Toolkit _-> Input -> Pointers_.
En _EyeTrackingDemo-00-RootScene,_ donde el Mixed Reality Toolkit se configura una vez para todas las escenas de demostración de seguimiento ocular, debería ver _EyeTrackingDemoPointerProfile_.
Puede crear un nuevo perfil de entrada _desde_ cero o adaptar el actual:

- **Desde cero:** En la _pestaña Punteros,_ seleccione _DefaultMixedRealityInputPointerProfile_ en el menú contextual.
Este es el perfil de puntero predeterminado que ya tiene habilitado el rayo de mano.
Para cambiar el cursor predeterminado (un punto blanco opaco), simplemente clone el perfil y cree su propio perfil de puntero personalizado.
A continuación, reemplace _DefaultCursor_ por _EyeGazeCursor_ en _Gaze Cursor Prefab_.  
- **En función del _elemento EyeTrackingDemoPointerProfile_ existente:** haga doble clic en _EyeTrackingDemoPointerProfile_ y agregue la siguiente entrada en _Opciones de puntero_:
  - **Tipo de controlador:** "Mano articulada", "Windows Mixed Reality"
  - **Entrega:** Cualquier
  - **Prefab de puntero:** DefaultControllerPointer

**2. Detectar que se** busca un holograma: use el script para habilitar la detección de que un holograma se ha visto como se [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) describió anteriormente. También puede echar un vistazo al script de ejemplo para obtener inspiración, ya que muestra un holograma después de la mirada con los ojos (por ejemplo, un cursor) independientemente de si los rayos de las manos están habilitados `FollowEyeGaze` o no.

Ahora, al iniciar las escenas de demostración de seguimiento ocular, debería ver un rayo procedente de las manos.
Por ejemplo, en la demostración de selección de destino de seguimiento de los ojos, el círculo semitransparente sigue la mirada con los ojos y las gemas responden a si se miran o no, mientras que los botones del menú de la escena superior usan el puntero de entrada principal (las manos) en su lugar.

---
[Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit).](eye-tracking-main.md)
