---
ms.openlocfilehash: e7f298b9d587df2243601670e187c109bb674a278deb67862b517568ca5198d7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213523"
---
# <a name="project-settings"></a>[Configuración del proyecto](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. Revise los pasos comunes de porte mencionados anteriormente.

Revise los pasos comunes enumerados anteriormente para asegurarse de que el entorno de desarrollo está configurado correctamente. En el #3 paso, si usa Visual Studio debe seleccionar la carga de **trabajo Desarrollo de juegos con Unity.** Puede anular la selección del componente "Editor de Unity opcional", ya que instalará una versión más reciente de Unity en el paso siguiente.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. Actualización a la compilación pública más reciente de Unity con Windows mr.
1. Descargue la última [compilación pública recomendada de Unity con](../../install-the-tools.md) compatibilidad con realidad mixta.
2. Guardar una copia del proyecto antes de empezar
3. Revise la [documentación disponible](https://docs.unity3d.com/Manual/UpgradeGuides.html) en Unity sobre la actualización si el proyecto se creó en una versión anterior de Unity.
4. Siga las [instrucciones](https://docs.unity3d.com/Manual/APIUpdater.html) del sitio de Unity para usar su actualizador de API automático.
5. Compruebe y compruebe si hay cambios adicionales que debe realizar para que el proyecto se ejecute y revise los errores y advertencias restantes. 

> [!Note] 
> Si tiene middleware del que depende, compruebe que usa la versión más reciente (más detalles en el paso 3 a continuación).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. Actualización del middleware a las versiones más recientes

Con cualquier actualización de Unity, existe la posibilidad de que necesite actualizar uno o varios paquetes de middleware de los que depende el juego o la aplicación. Además, estar al día con el middleware más reciente aumenta la probabilidad de éxito durante el resto del proceso de porte.

### <a name="4-target-your-application-to-run-on-win32"></a>4. Destino de la aplicación para que se ejecute en Win32

Desde dentro de la aplicación de Unity:

* Vaya a File -> Build Configuración
* Seleccione "PC, Mac, Linux independiente"
* Establezca la plataforma de destino en "Windows"
* Establezca arquitectura en "x86" Seleccione "Cambiar plataforma"

> [!NOTE] 
> Si la aplicación tiene dependencias en servicios específicos del dispositivo, como la realización de coincidencias desde Steam, deberá deshabilitarlas en este paso. Puede enlazar a los servicios equivalentes que Windows proporciona más adelante.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. Configuración del hardware Windows Mixed Reality de datos
1. Revisión de los pasos de la [configuración del casco envolvente](/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Más información [sobre el uso del simulador Windows Mixed Reality](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) y navegación por el Windows Mixed Reality [inicio](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Destino de la aplicación para que se ejecute en Windows Mixed Reality
1. En primer lugar, debe quitar o compilar condicionalmente cualquier otra compatibilidad de biblioteca específica de un SDK de VR determinado. Estos recursos cambian con frecuencia la configuración y las propiedades del proyecto de maneras incompatibles con otros SDK de VR, como Windows Mixed Reality.
    * Por ejemplo, si el proyecto hace referencia al SDK de SteamVR, deberá actualizar el proyecto para usar en su lugar las API comunes de REALIDAD virtual de Unity que admiten tanto Windows Mixed Reality como SteamVR.
    * Pronto se van a seguir pasos específicos para excluir condicionalmente otros SDK de VR.
2. En el proyecto de Unity, [el destino es Windows 10 SDK.](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. Para cada escena, [configure la cámara.](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. Use la fase para colocar contenido en el suelo

Puede crear experiencias Mixed Reality en una amplia gama de [escalas de experiencia.](../../../design/coordinate-systems.md)

Si va a portar una **experiencia** de escalado asentado, debe asegurarse de que Unity está establecido en el tipo de espacio de seguimiento **stationary:**

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Este código anterior establece el sistema de coordenadas universales de Unity para realizar un seguimiento del [marco de referencia insalte.](../../../design/coordinate-systems.md#spatial-coordinate-systems) En el modo de seguimiento estacionado, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (hacia delante es -Z) aparece delante del usuario cuando se inicia la aplicación. Para hacer más reciente el origen de la sesión del usuario, puede llamar a XR de [Unity. Método InputTracking.Recenter.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

Si va a porte una experiencia **de** escalado permanente o de escala de **habitación,** colocará contenido relativo a la planta. Para razonar sobre la planta del usuario, se usa la fase espacial **[,](../../../design/coordinate-systems.md#spatial-coordinate-systems)** que representa el origen de nivel de planta definido del usuario y el límite opcional de la sala, que se configura durante la primera ejecución. Para estas experiencias, debe asegurarse de que Unity está establecido en el tipo de espacio de seguimiento **RoomScale.** Aunque RoomScale es el valor predeterminado, querrá establecerlo explícitamente y asegurarse de que vuelve a ser true para detectar situaciones en las que el usuario ha alejado el equipo de la sala que calibraron:

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

Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento RoomScale, el contenido situado en el plano y=0 aparecerá en el suelo. El origen en (0, 0, 0) será el lugar específico en la planta donde el usuario se encuentra durante la instalación de la sala, con -Z que representa la dirección hacia delante a la que se encontraban durante la instalación.

En el código de script, puede llamar al método TryGetGeometry en el tipo UnityEngine.Experimental.XR.Boundary para obtener un polígono de límite, especificando un tipo de límite TrackedArea. Si el usuario definió un límite (se obtiene una lista de vértices), es seguro ofrecer al usuario una experiencia de escala de habitación, donde puede recorrer la escena que cree. 

El sistema representará automáticamente el límite cuando el usuario se acerque a él. La aplicación no necesita usar este polígono para representar el propio límite.

Para más información, consulte la página [Sistemas de coordenadas en Unity.](../../unity/coordinate-systems-in-unity.md)

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Ejemplo de resultados:

![Ejemplo de resultados](../../porting-apps/images/largestrectangle-400px.jpg)

El algoritmo se basa en un blog de Daniel Smilkov: [El rectángulo más grande de un polígono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. Trabajar a través del modelo de entrada

Cada juego o aplicación destinado a un HMD existente tendrá un conjunto de entradas que controla, los tipos de entradas que necesita para la experiencia y las API específicas a las que llama para obtener esas entradas. Hemos invertido en intentar que sea lo más sencillo y sencillo posible aprovechar las ventajas de las entradas disponibles en Windows Mixed Reality.

Lea la guía [de porte de](../porting-guides.md?tabs=input) entrada de Unity en la pestaña adyacente para obtener más información sobre cómo Windows Mixed Reality expone la entrada y cómo se asigna a lo que puede hacer la aplicación hoy en día.

### <a name="9-performance-testing-and-tuning"></a>9. Pruebas y optimización del rendimiento

Windows Mixed Reality estará disponible en una amplia clase de dispositivos, desde equipos de juegos de gama alta hasta equipos estándar del mercado. En función del mercado al que se va a dirigir, hay una diferencia significativa en los presupuestos de gráficos y proceso disponibles para la aplicación. Durante este ejercicio de porte, es probable que esté aprovechando un equipo Premium y haya tenido presupuestos de gráficos y proceso significativos disponibles para la aplicación. Si quiere que la aplicación esté disponible para un público más amplio, debe probar y crear perfiles de la aplicación en el hardware representativo al [que desea dirigirse.](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)

Tanto [Unity](https://docs.unity3d.com/Manual/Profiler.html) como [Visual Studio](/visualstudio/profiling/index) incluyen los perfiles de rendimiento y las directrices de publicación de [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) e [Intel](https://software.intel.com/articles/vr-content-developer-guide) sobre la generación de perfiles y la optimización de rendimiento. Hay una amplia explicación del rendimiento disponible en [Descripción del rendimiento para Mixed Reality](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). Además, hay detalles específicos de Unity en [Rendimiento Recomendaciones para Unity.](../../unity/performance-recommendations-for-unity.md)

# <a name="input-mapping"></a>[Asignación de datos de entrada](#tab/input)

Puede portabilidad de la lógica de entrada a Windows Mixed Reality mediante uno de estos dos enfoques: las API input.GetButton/GetAxis generales de Unity que abarcan varias plataformas o la XR específica Windows de Unity. Wsa. API de entrada que ofrecen datos más completos específicamente para controladores de movimiento y HoloLens manos.

> [!IMPORTANT]
> Si usa controladores HP Reverb G2, consulte [este](../../unity/unity-reverb-g2-controllers.md) artículo para obtener instrucciones de asignación de entrada adicionales.

## <a name="unity-xr-input-apis"></a>API de entrada XR de Unity

Para los proyectos nuevos, se recomienda usar las nuevas API de entrada XR desde el principio. 

Puede encontrar más información sobre las [API de XR aquí.](https://docs.unity3d.com/Manual/xr_input.html)

## <a name="inputgetbuttongetaxis-apis"></a>API Input.GetButton/GetAxis

Unity usa actualmente sus API input.GetButton/Input.GetAxis generales para exponer la entrada para el SDK de [Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) y [el SDK de OpenVR.](https://docs.unity3d.com/Manual/OpenVRControllers.html) Si las aplicaciones ya usan estas API para la entrada, esta es la ruta de acceso más fácil para admitir controladores de movimiento en Windows Mixed Reality: solo debe volver a asignar botones y ejes en el Administrador de entrada.

Para más información, consulte la tabla de [asignación de ejes o botones](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) de Unity y la [introducción a las API comunes de Unity.](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows XR específico. Wsa. API de entrada

> [!CAUTION]
> Si el proyecto usa cualquiera de las XR. Las API de WSA se están eliminando gradualmente en favor del SDK de XR en futuras versiones de Unity. Para los proyectos nuevos, se recomienda usar el SDK de XR desde el principio. Puede encontrar más información sobre el sistema [de entrada XR y las API aquí.](https://docs.unity3d.com/Manual/xr_input.html)

Si la aplicación ya compila lógica de entrada personalizada para cada plataforma, puede elegir usar las API de entrada espaciales específicas de Windows en el espacio de nombres **UnityEngine.XR.WSA.Input.** Esto le permite acceder a información adicional, como la precisión de la posición o el tipo de origen, lo que le permite diferenciar las manos y los controladores en HoloLens.

> [!NOTE]
> Si usa controladores HP Reverb G2, todas las API de entrada seguirán funcionando excepto **InteractionSource.supportsTouchpad,** que devolverá false sin datos del panel táctil.

Para más información, consulte la [introducción a las API UnityEngine.XR.WSA.Input.](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)

## <a name="grip-pose-vs-pointing-pose"></a>Posición de control frente a posición de apuntar

Windows Mixed Reality admite controladores de movimiento en una variedad de factores de forma, y el diseño de cada controlador difiere en su relación entre la posición de la mano del usuario y la dirección "hacia delante" natural que las aplicaciones deben usar para señalar al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de poses que puede investigar para cada origen de interacción:

* El **control posa**, que representa la ubicación de la mano detectada por una HoloLens o la mano que mantiene un controlador de movimiento.
    * En los cascos envolventes, esta  posición se usa mejor para representar la mano del usuario o un objeto que se mantiene en la mano del **usuario,** como un revólver o un revólver.
    * Posición **del control:** centroide de la mano al mantener el controlador de forma natural, ajustado a la izquierda o derecha para centrar la posición dentro del control.
    * Eje **derecho** de la orientación del control: cuando se abre completamente la mano para formar una posición plana de 5 dedos, el rayo que es normal para la mano (hacia delante desde la mano izquierda, hacia atrás desde la mano derecha).
    * Eje **hacia** delante de la orientación del control: cuando cierra la mano parcialmente (como si sostendía el controlador), el rayo que señala "hacia delante" a través del metro formado por los dedos que no son de posición.
    * Eje **Up de la orientación del control:** eje Up implícito en las definiciones Right y Forward.
    * Puede acceder a la posición de control a través de la API de entrada entre proveedores de Unity **[(XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o a través de la API específica de Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** solicitando la posición de control).
* El **puntero posa**, que representa la punta del controlador que apunta hacia delante.
    * Esta posición se usa mejor para la difusión por **rayos al apuntar a la interfaz** de usuario cuando se representa el propio modelo de controlador.
    * Actualmente, la posición del puntero solo está disponible a través de la API específica de Windows **(sourceState.sourcePose.TryGetPosition/Rotation,** que solicita la posición de puntero).

Todas estas coordenadas de posición se expresan en coordenadas del mundo de Unity.