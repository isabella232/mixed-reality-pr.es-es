---
ms.openlocfilehash: 0ef22142ac2efc3ef47ece2619d31dbeddcff8fe
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192672"
---
# <a name="project-settings"></a>[Configuración del proyecto](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. Revise los pasos de portabilidad más indicados anteriormente

Revise los pasos comunes indicados anteriormente para asegurarse de que el entorno de desarrollo está configurado correctamente. En el paso #3, si usa Visual Studio, debe seleccionar la carga de trabajo **desarrollo de juegos con Unity** . Puede anular la selección del componente "Editor de Unity opcional", ya que va a instalar una versión más reciente de Unity en el paso siguiente.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. actualizar a la última compilación pública de Unity con compatibilidad con Windows MR
1. Descargue la última [compilación pública recomendada de Unity](../../install-the-tools.md) con compatibilidad de realidad mixta.
2. Guarde una copia del proyecto antes de empezar.
3. Revise la [documentación](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponible en Unity en la actualización si el proyecto se compiló con una versión anterior de Unity.
4. Siga las [instrucciones](https://docs.unity3d.com/Manual/APIUpdater.html) del sitio de Unity para usar su actualizador de API automática.
5. Compruebe si hay cambios adicionales que necesite realizar para que el proyecto se ejecute y, a continuación, trabaje con los errores y advertencias restantes. 

> [!Note] 
> Si tiene un middleware del que depende, compruebe que está usando la versión más reciente (más información en el paso 3 a continuación).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. actualizar el middleware a las versiones más recientes

Con cualquier actualización de Unity, existe la posibilidad de actualizar uno o más paquetes de middleware de los que depende su juego o aplicación. Además, al estar al día con el middleware más reciente, se aumenta la probabilidad de éxito a lo largo del resto del proceso de portabilidad.

### <a name="4-target-your-application-to-run-on-win32"></a>4. dirigir la aplicación para que se ejecute en Win32

Desde dentro de la aplicación Unity:

* Vaya a archivo-> configuración de compilación
* Seleccione "PC, Mac, Linux independiente"
* Establecer la plataforma de destino en "Windows"
* Establecer la arquitectura en "x86" seleccionar "cambiar plataforma"

> [!NOTE] 
> Si la aplicación tiene dependencias en servicios específicos del dispositivo, como la realización de una coincidencia de vapor, deberá deshabilitarlos en este paso. Puede enlazar a los servicios equivalentes que Windows proporciona más adelante.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. configurar el hardware de Windows Mixed Reality
1. Revisión de los pasos de la [configuración de auriculares inmersivo](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Obtener información sobre cómo [usar el simulador de realidad mixta de Windows](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) y [navegar por la Página principal de Windows Mixed Reality](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. dirigir la aplicación para que se ejecute en Windows Mixed Reality
1. En primer lugar, debe quitar o compilar condicionalmente cualquier otra compatibilidad de biblioteca específica de un SDK de VR determinado. Esos activos cambian con frecuencia la configuración y las propiedades del proyecto de manera que sean incompatibles con otros SDK de VR, como Windows Mixed Reality.
    * Por ejemplo, si el proyecto hace referencia al SDK de SteamVR, tendrá que actualizar el proyecto para usar en su lugar las API de VR comunes de Unity que admiten tanto Windows Mixed Reality como SteamVR.
    * Pronto estarán disponibles los pasos específicos para excluir condicionalmente otros SDK de VR.
2. En el proyecto de Unity, [el destino es el SDK de Windows 10](../../unity/tutorials/holograms-100.md#target-windows-10-sdk) .
3. Para cada escena, [Configure la cámara](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera) .

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. usar la fase para colocar contenido en el piso

Puede crear experiencias de realidad mixta en una amplia gama de [escalas de experiencia](../../../design/coordinate-systems.md).

Si va a migrar una **experiencia de escalado de** una instalación, debe asegurarse de que Unity está establecido en el tipo de espacio de seguimiento **estacionario** :

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

En el código anterior se establece el sistema de coordenadas universal de Unity para realizar el seguimiento del [marco estacionario de referencia](../../../design/coordinate-systems.md#spatial-coordinate-systems). En el modo de seguimiento estacional, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el avance es-Z) aparece delante del usuario cuando se inicia la aplicación. Para recentrar el origen del usuario, puede llamar a la XR de Unity [. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) .

Si va a migrar una experiencia **de escalado permanente** o una **experiencia a escala de habitación**, colocará contenido en relación con el piso. Por lo tanto, se trata del piso del usuario mediante la **[fase espacial](../../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa el origen del nivel de suelo definido por el usuario y el límite de sala opcional, configurado durante la primera ejecución. Para estas experiencias, debe asegurarse de que Unity está establecido en el tipo de espacio de seguimiento de **RoomScale** . Aunque RoomScale es el valor predeterminado, querrá establecerlo explícitamente y asegurarse de que se devuelve true para detectar situaciones en las que el usuario ha desplazado el equipo fuera del salón que han calibrado:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento de RoomScale, el contenido colocado en el plano y = 0 aparecerá en el suelo. El origen en (0,0) será el lugar específico en el piso en el que se encuentra el usuario durante la configuración de la habitación, con-Z que representa la dirección de avance que estaban teniendo lugar durante la instalación.

En el código de script, puede llamar al método TryGetGeometry en el tipo UnityEngine. experimental. XR. Boundary para obtener un polígono de límite, especificando un tipo de límite de TrackedArea. Si el usuario definía un límite (se obtiene una lista de vértices), es seguro ofrecer una experiencia de **escalado** a la habitación al usuario, donde puede recorrer la escena que cree.

El sistema representará automáticamente el límite cuando el usuario lo aproxime. No es necesario que la aplicación use este polígono para representar el límite.

Para obtener más información, consulte la página [de los sistemas de coordenadas en Unity](../../unity/coordinate-systems-in-unity.md) .

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Ejemplo de resultados:

![Ejemplo de resultados](../../porting-apps/images/largestrectangle-400px.jpg)

El algoritmo se basa en un blog de Daniel Smilkov: [el rectángulo más grande de un polígono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. trabajar con el modelo de entrada

Cada juego o aplicación que tiene como destino un HMD existente tendrá un conjunto de entradas que controla, los tipos de entradas que necesita para la experiencia y las API específicas a las que llama para obtener esas entradas. Hemos invertido en intentar que sea tan sencillo y sencillo como sea posible para aprovechar las ventajas de las entradas disponibles en Windows Mixed Reality.

Lea la [Guía de portabilidad de entrada para Unity](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input) en la pestaña adyacente para obtener detalles sobre cómo Windows Mixed Reality expone la entrada y cómo se asigna a lo que la aplicación puede hacer hoy.

### <a name="9-performance-testing-and-tuning"></a>9. pruebas y ajuste del rendimiento

Windows Mixed Reality estará disponible en una amplia gama de dispositivos, que abarcan desde equipos de juegos de alta gama, hasta grandes equipos estándar de mercado. En función del mercado de destino, hay una diferencia significativa en los presupuestos de proceso y gráficos disponibles para la aplicación. Durante este proceso de migración, es probable que se esté aprovechando un equipo Premium y que haya presupuestos de cálculo y gráficos significativos disponibles para la aplicación. Si quiere que la aplicación esté disponible para un público más amplio, debe probar y generar el perfil de la aplicación en [el hardware representativo que](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)quiere usar como destino.

Tanto [Unity](https://docs.unity3d.com/Manual/Profiler.html) como [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) incluyen los generadores de rendimiento y las directrices de publicación de [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) e [Intel](https://software.intel.com/articles/vr-content-developer-guide) sobre la optimización y la generación de perfiles de rendimiento. Hay una explicación exhaustiva del rendimiento disponible al [comprender el rendimiento de la realidad mixta](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). Además, hay detalles específicos para Unity en [recomendaciones de rendimiento para Unity](../../unity/performance-recommendations-for-unity.md).

# <a name="input-mapping"></a>[Asignación de datos de entrada](#tab/input)

Puede trasladar la lógica de entrada a Windows Mixed Reality mediante uno de estos dos enfoques: la entrada general de Unity. GetButton/GetAxis API que abarcan varias plataformas, o el XR específico de Windows. WSA. API de entrada que ofrecen datos más completos específicamente para los controladores de movimiento y las manos de HoloLens.

> [!IMPORTANT]
> Si usa controladores de HP reverberación G2, consulte [este artículo](../../unity/unity-reverb-g2-controllers.md) para obtener instrucciones adicionales de asignación de entrada.

## <a name="unity-xr-input-apis"></a>API de entrada de Unity XR

En el caso de los proyectos nuevos, se recomienda usar las nuevas API de entrada de XR desde el principio. 

Puede encontrar más información sobre las [API de XR aquí](https://docs.unity3d.com/Manual/xr_input.html).

## <a name="inputgetbuttongetaxis-apis"></a>API de entrada. GetButton/GetAxis

Unity usa actualmente sus API de entrada general. GetButton/Input. GetAxis para exponer la entrada para [el SDK de Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) y [el SDK de OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Si las aplicaciones ya usan estas API para la entrada, esta es la ruta más sencilla para admitir controladores de movimiento en Windows Mixed Reality: solo debe reasignar botones y ejes en el administrador de entrada.

Para obtener más información, consulte la [tabla de asignación de ejes y botones de Unity](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) y la [información general de las API comunes de Unity](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR específico de Windows. WSA. API de entrada

> [!CAUTION]
> Si el proyecto usa cualquiera de las de XR. Las API de WSA, se están desinstalando en favor del SDK de XR en futuras versiones de Unity. En el caso de los proyectos nuevos, se recomienda usar el SDK de XR desde el principio. Puede encontrar más información sobre el [sistema de entrada de XR y las API aquí](https://docs.unity3d.com/Manual/xr_input.html).

Si la aplicación ya compila la lógica de entrada personalizada para cada plataforma, puede optar por usar las API de entrada espacial específicas de Windows en el espacio de nombres **UnityEngine. XR. WSA. Input** . Esto le permite tener acceso a información adicional, como la precisión de la posición o el tipo de origen, lo que permite indicar a las manos y controladores de HoloLens.

> [!NOTE]
> Si usa controladores de reverberación de HP G2, todas las API de entrada seguirán funcionando excepto para **InteractionSource. supportsTouchpad**, que devolverá FALSE sin datos de Touchpad.

Para obtener más información, vea la información [General de las API de UnityEngine. XR. WSA. Input](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Replanteamiento de control frente a pose de puntero

Windows Mixed Reality admite controladores de movimiento en diversos factores de forma, con el diseño de cada controlador diferente en su relación entre la posición del usuario y la dirección de "avance" natural que deben usar las aplicaciones para apuntar al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de supuestos que puede investigar para cada origen de interacción:

* La representación del **control**, que representa la ubicación de la palma de una mano detectada por un HoloLens o la palma que contiene un controlador de movimiento.
    * En los auriculares más envolventes, este planteamiento se usa mejor para presentar **la mano del usuario** o **un objeto mantenido en la mano del usuario**, como un arma o una pistola.
    * La **posición del puño**: Palm centroide cuando mantiene el controlador de forma natural, se ajusta hacia la izquierda o derecha para centrar la posición dentro del control.
    * **Eje derecho de la orientación del puño**: cuando se abre por completo la mano para formar una postura plana de 5 dedos, el rayo perpendicular a la palma (hacia delante de la mano izquierda y hacia atrás desde la mano derecha)
    * El **eje hacia delante de la orientación del puño**: al cerrar la mano (como si contiene el controlador), el rayo que señala "reenviar" a través del tubo formado por los dedos no Thumb.
    * **Eje hacia arriba de la orientación del puño**: el eje hacia arriba implícito por las definiciones derecha y hacia delante.
    * Puede acceder a la representación del puño a través de la API de entrada entre proveedores (XR) de Unity **[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o a través de la API específica de Windows (**SourceState. SourcePose. TryGetPosition/Rotation**, que solicita la pose de control).
* Representación del **puntero** que representa la punta del controlador que señala hacia delante.
    * Esta representación se usa mejor para Raycast cuando se **señala a la interfaz de usuario** cuando se representa el propio modelo del controlador.
    * Actualmente, la pose de puntero solo está disponible a través de la API específica de Windows (**sourceState. sourcePose. TryGetPosition/Rotation**, lo que solicita la pose de puntero).

Estas coordenadas de pose se expresan en coordenadas universales de Unity.
