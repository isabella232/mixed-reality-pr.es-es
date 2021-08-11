---
title: Navegación de seguimiento ocular
description: Uso de la orientación con los ojos para la navegación en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking,
ms.openlocfilehash: e1ca34054a019e26bebf14282cd351467e5c65e2c2c3fa4f35647dd5aba680ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197121"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Navegación compatible con los ojos en MRTK

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Imagine está leyendo información en una pizarra y cuando llega al final del texto mostrado, el texto se desplaza automáticamente hacia arriba para mostrar más contenido. O bien, puede acercar con fluidez dónde está mirando. El mapa también ajusta automáticamente el contenido para mantener las cosas de interés dentro del campo de vista. Otra aplicación interesante es la observación con manos libres de hologramas 3D al incorporar automáticamente las partes del holograma que está viendo al frente. Estos son algunos de los ejemplos que se describen en esta página en el contexto de la navegación con los ojos.

En las descripciones siguientes se supone que ya está familiarizado con cómo configurar el [](eye-tracking-target-selection.md) seguimiento de los ojos en la escena de [MRTK](eye-tracking-basic-setup.md) y con los conceptos básicos de acceso a los datos de seguimiento de los ojos en MRTK Unity.
Los ejemplos que se de analizan a continuación forman parte de la escena `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes/EyeTrackingDemo-03-Navigation).

**Resumen:** Desplazamiento automático de texto, desplazamiento panorámico compatible con la mirada con los ojos y zoom de un mapa virtual, rotación 3D dirigida a mirada con manos libres.

## <a name="auto-scroll"></a>Desplazamiento automático

El desplazamiento automático permite al usuario desplazarse por los textos sin mover un dedo.
Simplemente continúe leyendo y el texto se desplazará hacia arriba o hacia abajo automáticamente en función de dónde esté buscando el usuario.
Puede empezar desde el ejemplo proporcionado en `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).
En este ejemplo se [usa un componente TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) para permitir la carga y el formato flexibles de texto nuevo.
Para habilitar el desplazamiento automático, simplemente agregue los dos scripts siguientes al componente de colisionador del cuadro de texto:

### <a name="scrollrecttransf"></a>ScrollRectTransf

Para desplazarse por [textmesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) o, en general, hablando un [componente RectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html) puede usar el script [ScrollRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)
Si desea desplazarse a través de una textura en lugar de [rectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html), use [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) en lugar de [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf).
A continuación, los parámetros [de ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) que están disponibles en el Editor de Unity se explican con más detalle:

Parámetros | Descripción
:---- | :----
LimitPanning | Si está habilitada, detendrá el contenido desplazable en su límite.
RectTransfToNavigate | Referencia a [RectTransform para](https://docs.unity3d.com/ScriptReference/RectTransform.html) desplazarse.
RefToViewport | Referencia al [rectTransform primario](https://docs.unity3d.com/ScriptReference/RectTransform.html) del contenido desplazable para determinar el desplazamiento y el límite correctos.
AutoGazeScrollIsActive | Si está habilitado, el texto se desplazará automáticamente si el usuario examina una región activa *(por* ejemplo, la parte superior e inferior del panel de desplazamiento si la velocidad de desplazamiento vertical no es cero).
ScrollSpeed_x | Si se establece en un valor distinto a cero, se habilitará el desplazamiento horizontal. Los valores negativos significan un cambio en la dirección de desplazamiento: de izquierda a derecha frente a derecha a izquierda.
ScrollSpeed_y | Si se establece en un valor distinto a cero, se habilitará el desplazamiento vertical. Los valores negativos significan un cambio en la dirección de desplazamiento: arriba hacia abajo frente a abajo hasta arriba.
MinDistFromCenterForAutoScroll | Distancia mínima normalizada en x e y desde el centro del cuadro de acceso del destino (0, 0) para desplazarse. Por lo tanto, los valores deben oscilar entre 0 (desplazamiento siempre) y 0,5 (sin desplazamiento).
UseSkimProofing | Si está habilitada, evita los movimientos de desplazamiento repentinos al mirar rápidamente. Sin embargo, esto puede hacer que el desplazamiento tenga menos capacidad de respuesta. Se puede ajustar con el *valor SkimProofUpdateSpeed.*
SkimProofUpdateSpeed | Mientras menor sea el valor, más lento se acelerará el desplazamiento después de la reducción horizontal. Valor recomendado: 5.

![Configuración de desplazamiento compatible con los ojos en Unity](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

La asociación _del componente EyeTrackingTarget_ permite controlar de forma flexible los eventos relacionados con la mirada con los ojos.
En el ejemplo de desplazamiento se muestra  el texto de desplazamiento que se inicia cuando el usuario examina el panel y se detiene cuando el usuario está *mirando* fuera de él.
![Configuración de desplazamiento compatible con los ojos en Unity: EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Desplazamiento panorámico y zoom compatibles con la mirada

Quién no ha usado un mapa virtual antes para buscar su casa o explorar lugares completamente nuevos? El seguimiento de los ojos le permite profundizar directamente en exactamente las partes que le interesan y, una vez acercado, puede seguir sin problemas el curso de una calle para explorar su barrio.
Esto no solo es útil para explorar mapas geográficos, sino también para consultar detalles en fotografías, visualizaciones de datos o incluso imágenes médicas en vivo. Para usar esta funcionalidad en la aplicación es fácil. Para el contenido representado en una [textura]( https://docs.unity3d.com/ScriptReference/Texture.html) (por ejemplo, una foto, datos transmitidos), simplemente agregue el script [PanZoomTexture.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture)
Para [rectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html) use [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf). Al ampliar la [funcionalidad de](#auto-scroll) desplazamiento automático, básicamente se permite desplazarse vertical y horizontalmente al mismo tiempo y ampliar el contenido en torno al punto de enfoque actual del usuario.

Parámetros | Descripción
:---- | :----
LimitPanning | Si está habilitada, detendrá el contenido desplazable en su límite.
HandZoomEnabledOnStartup | Indica si los gestos con las manos se habilitan automáticamente para realizar un gesto de zoom. Es posible que desee deshabilitarlo al principio para evitar desencadenar accidentalmente acciones de zoom.
RepresentadorOfTextureToBeNavigated | Representador al que se hace referencia de la textura que se va a navegar.
Zoom_Acceleration | Aceleración del zoom que define la integridad de la asignación de funciones de velocidad logística.
Zoom_SpeedMax | Velocidad máxima de zoom.
Zoom_MinScale | Escala mínima de la textura para acercar, por ejemplo, 0,5f (la mitad del tamaño original).
Zoom_MaxScale | Escala máxima de la textura para alejar: por ejemplo, 1f (el tamaño original) o 2,0f (el doble del tamaño original).
Zoom_TimeInSecToZoom | Zoom con tiempo: una vez desencadenado, se realizará un zoom de entrada y salida durante la cantidad de tiempo especificada en segundos.
Zoom_Gesture | Tipo de gesto de mano que se usa para acercar o alejar.
--- | ---
Pan_AutoScrollIsActive | Si está habilitado, el texto se desplazará automáticamente si el usuario examina una región activa *(por* ejemplo, la parte superior e inferior del panel de desplazamiento si la velocidad de desplazamiento vertical no es cero).
Pan_Speed_x | Si se establece en un valor distinto a cero, se habilitará el desplazamiento horizontal. Los valores negativos significan un cambio en la dirección de desplazamiento: de izquierda a derecha frente a derecha a izquierda.
Pan_Speed_y | Si se establece en un valor distinto a cero, se habilitará el desplazamiento vertical. Los valores negativos significan un cambio en la dirección de desplazamiento: arriba hacia abajo frente a abajo hasta arriba.
Pan_MinDistFromCenter | Distancia mínima normalizada en x e y desde el centro del cuadro de acceso del destino (0, 0) para desplazarse. Por lo tanto, los valores deben oscilar entre 0 (desplazamiento siempre) y 0,5 (sin desplazamiento).
UseSkimProofing | Si está habilitada, evita los movimientos de desplazamiento repentinos al mirar rápidamente. Sin embargo, esto puede hacer que el desplazamiento tenga menos capacidad de respuesta. Se puede ajustar con el *valor SkimProofUpdateSpeed.*
SkimProofUpdateSpeed | Mientras menor sea el valor, más lento se acelerará el desplazamiento después de la reducción horizontal. Valor recomendado: 5.

![Configuración de zoom y panorámica compatible con los ojos en Unity](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Rotación 3D basada en la atención

Imagine un objeto 3D y las partes que desea ver más estrechamente se dirigen hacia usted, como si el sistema le leyese la mente y sepa que debes convertir el elemento hacia ti.
Esta es la idea de las rotaciones 3D basadas en atención que permiten investigar todos los lados de un holograma sin mover un dedo.
Para habilitar este comportamiento, simplemente agregue el script [OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) a la parte de GameObject con un [componente Collider.](https://docs.unity3d.com/ScriptReference/Collider.html)
Puede ajustar varios parámetros que se enumeran a continuación para limitar la rapidez y en qué direcciones girará el holograma.

Como puede imaginar, tener este comportamiento activo en todo momento puede resultar rápidamente bastante distraída en una escena abarrotado.
Este es el motivo por el que es posible que quiera empezar con este comportamiento deshabilitado y, a continuación, habilitarlo rápidamente mediante comandos de voz.
Como alternativa, agregamos un ejemplo en `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) para usar [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) para el que puede seleccionar un destino centrado y que se sobresalte delante de usted, simplemente diga *"Ven a mí".*

Una vez en el modo cercano, el modo de rotación automática se habilita automáticamente.
En ese modo, puede observarlo desde todos los lados, ya sea simplemente inclinado hacia atrás y mirando hacia atrás, recorriendo su alrededor o alcanzando para agarrarlo y girarlo con la mano. Al descartar el destino (mire & o diga *"Enviar* atrás"), volverá a su ubicación original y dejará de reaccionar a usted desde lejos.

Parámetros | Descripción
:---- | :----
SpeedX | Velocidad de rotación horizontal.
Rápida | Velocidad de rotación vertical.
InverseX | Para invertir la dirección de rotación horizontal.
Inverso | Para invertir la dirección de rotación vertical.
RotationThreshInDegrees | Si el ángulo entre "Mirada al destino" y "Cámara a destino" es menor que este valor, no haga nada. Esto es para evitar pequeñas rotaciones de vibración.
MinRotX | Ángulo de rotación horizontal mínimo. Esto es para limitar la rotación en distintas direcciones.
MaxRotX | Ángulo de rotación horizontal máximo. Esto es para limitar la rotación en distintas direcciones.
MinRoty | Ángulo de rotación vertical mínimo para limitar la rotación alrededor del eje X.
MaxRoty | Ángulo de rotación vertical máximo para limitar la rotación alrededor del eje Y.

![Configuración de rotación 3D compatible con los ojos en Unity](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

En resumen, los scripts anteriores deben permitirle empezar a usar la mirada con los ojos para varias tareas de navegación de entrada, como desplazar texto, zoom y texturas de desplazamiento, así como rotar la investigación de hologramas 3D.

### <a name="see-also"></a>Consulte también

- [Configuración básica de MRTK para usar el seguimiento de los ojos](eye-tracking-basic-setup.md)
- [Selección de destino compatible con los ojos](eye-tracking-target-selection.md)

---
[Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit)](eye-tracking-main.md)
