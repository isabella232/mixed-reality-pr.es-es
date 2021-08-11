---
title: Estabilidad de hologramas
description: El HoloLens estabilizar automáticamente los hologramas, pero hay pasos que los desarrolladores pueden seguir para mejorar aún más la estabilidad del holograma.
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: hologramas, estabilidad, hololens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, velocidad de fotogramas, representación, reproducción, separación de colores
appliesto:
- HoloLens
ms.openlocfilehash: a9a260208764db86d3a2d945cb6a1a611e66848889dfc228d9341f10b8e054ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198826"
---
# <a name="hologram-stability"></a>Estabilidad de hologramas

Para lograr hologramas estables, HoloLens una canalización de estabilización de imágenes integrada. La canalización de estabilización funciona automáticamente en segundo plano, por lo que no es necesario realizar ningún paso adicional para habilitarla. Sin embargo, debe usar técnicas que mejoren la estabilidad del holograma y eviten escenarios que reduzcan la estabilidad.

## <a name="hologram-quality-terminology"></a>Terminología de calidad del holograma

La calidad de los hologramas es el resultado de un buen entorno y un buen desarrollo de aplicaciones. Las aplicaciones que se ejecutan en una constante de 60 fotogramas por segundo en un entorno donde HoloLens puede realizar un seguimiento del entorno garantiza que el holograma y el sistema de coordenadas correspondientes estén sincronizados. Desde la perspectiva de un usuario, los hologramas diseñados para ser estacionados no se moverán en relación con el entorno.

La siguiente terminología puede ayudarle a identificar problemas con el entorno, velocidades de representación incoherentes o bajas, o cualquier otra cosa.
* **Precisión.** Una vez que el holograma está bloqueado y se coloca en el mundo real, debe permanecer donde se coloca en relación con el entorno circundante e independiente del movimiento del usuario o de los cambios de entorno pequeños y dispersos. Si un holograma aparece más adelante en una ubicación inesperada, es un problema *de* precisión. Estos escenarios pueden ocurrir si dos salas distintas son idénticas.
* **Jitter.** Los usuarios observan la vibración como una vibración de alta frecuencia de un holograma, lo que puede ocurrir cuando se degrada el seguimiento del entorno. Para los usuarios, la solución ejecuta la [optimización del sensor](/hololens/hololens-updates).
* **Judder.** Las frecuencias de representación bajas tienen como resultado un movimiento desigual e imágenes dobles de hologramas. Judder es especialmente visible en hologramas con movimiento. Los desarrolladores necesitan mantener [una constante de 60 FPS.](hologram-stability.md#frame-rate)
* **Deriva.** Los usuarios ven el desviado cuando parece que un holograma se aleja de donde se colocó originalmente. El desviado se produce cuando se coloca hologramas lejos de los [anclajes](../../design/spatial-anchors.md)espaciales, especialmente en partes sin colocar del entorno. La creación de hologramas cerca de los delimitadores espaciales reduce la probabilidad de desviarse.
* **Jumpiness.** Cuando un holograma "aparece" o "salta" de su ubicación en ocasiones. La preparación puede producirse a medida que el seguimiento ajusta los hologramas para que coincidan con la comprensión actualizada del entorno.
* **Nadar.** Cuando parece que un holograma se desvía correspondiente al movimiento de la cabeza del usuario. La nada se produce cuando la aplicación no ha implementado completamente la [reproducción](hologram-stability.md#reprojection)y si el HoloLens no está calibrado [para](/hololens/hololens-calibration) el usuario actual. El usuario puede volver a ejecutar la [aplicación de](/hololens/hololens-calibration) calibración para corregir el problema. Los desarrolladores pueden actualizar el plano de estabilización para mejorar aún más la estabilidad.
* **Separación de colores.** Las pantallas de HoloLens son pantallas secuenciales de color, que son canales de color flash de rojo-verde-azul-verde a 60 Hz (los campos de color individuales se muestran a 240 Hz). Cada vez que un usuario realiza un seguimiento de un holograma en movimiento con los ojos, los bordes inicial y final de ese holograma se separan en sus colores constituyentes, lo que produce un efecto de efecto tortico. El grado de separación depende de la velocidad del holograma. En algunos casos poco frecuentes, mover la cabeza rápidamente mientras se observa un holograma estacionado también puede dar lugar a un efecto de efecto, que se denomina *[separación de color.](hologram-stability.md#color-separation)*

## <a name="frame-rate"></a>Velocidad de fotogramas

La velocidad de fotogramas es el primer pilar de la estabilidad del holograma. Para que los hologramas aparezcan estables en el mundo, cada imagen que se presenta al usuario debe tener los hologramas dibujados en el lugar correcto. Se muestra en HoloLens actualización 240 veces por segundo, mostrando cuatro campos de color independientes para cada imagen recién representado, lo que da lugar a una experiencia de usuario de 60 FPS (fotogramas por segundo). Para proporcionar la mejor experiencia posible, los desarrolladores de aplicaciones deben mantener 60 FPS, lo que se traduce en proporcionar de forma coherente una nueva imagen al sistema operativo cada 16 milisegundos.

**60 FPS** Para dibujar hologramas para que parezcan estar en el mundo real, HoloLens representar imágenes desde la posición del usuario. Puesto que la representación de imágenes tarda tiempo, HoloLens predice dónde estará la cabeza de un usuario cuando las imágenes se muestran en las pantallas. Sin embargo, este algoritmo de predicción es una aproximación. HoloLens hardware que ajusta la imagen representado para tener en cuenta la discrepancia entre la posición de la cabeza predicho y la posición de la cabeza real. El ajuste hace que la imagen que ve el usuario aparezca como si se representara desde la ubicación correcta y los hologramas se sientan estables. Las actualizaciones de imagen funcionan mejor con pequeños cambios y no pueden corregir completamente ciertas cosas de la imagen representado, como motion-parallax.

Al representar a 60 FPS, está haciendo tres cosas para ayudar a crear hologramas estables:
1. Minimizar la latencia general entre la representación de una imagen y la imagen que ve el usuario. En un motor con un juego y un subproceso de representación que se ejecuta en lockstep, la ejecución a 30FPS puede agregar 33,3 ms de latencia adicional. La reducción de la latencia reduce el error de predicción y aumenta la estabilidad del holograma.
2. Esto hace que cada imagen que llegue a los ojos del usuario tenga una cantidad coherente de latencia. Si se representa a 30 fps, la pantalla todavía muestra imágenes a 60 FPS, lo que significa que la misma imagen se mostrará dos veces seguidas. El segundo fotograma tendrá una latencia de 16,6 ms más que el primer fotograma y tendrá que corregir una cantidad de error más marcada. Esta incoherencia en la magnitud del error puede provocar un judder de 60 Hz no deseado.
3. Al reducir la aparición de interrupciones, que se caracterizan por un movimiento desigual e imágenes dobles. El movimiento de hologramas más rápido y las velocidades de representación más bajas se asocian a interrupciones más pronunciadas. El esfuerzo por mantener 60 FPS en todo momento ayudará a evitar el uso de judder para un holograma en movimiento determinado.

**Coherencia de velocidad de fotogramas** La coherencia de la velocidad de fotogramas es tan importante como un número alto de fotogramas por segundo. En ocasiones, los fotogramas eliminados son inevitables para cualquier aplicación con contenido enriquecido y el HoloLens implementa algunos algoritmos sofisticados para recuperarse de problemas ocasionales. Sin embargo, una velocidad de fotogramas fluctuante constantemente es mucho más perceptible para un usuario que la ejecución coherente a velocidades de fotogramas inferiores. Por ejemplo, una aplicación que se representa sin problemas durante cinco fotogramas (60 FPS mientras duren estos cinco fotogramas) y, a continuación, quita todos los demás fotogramas para los 10 fotogramas siguientes (30 FPS durante la duración de estos 10 fotogramas) parecerá más inestable que una aplicación que se representa de forma coherente a 30 FPS.

En una nota relacionada, el sistema operativo limita las aplicaciones a 30 FPS cuando se ejecuta la captura [de realidad](/hololens/holographic-photos-and-videos) mixta.

**Análisis de rendimiento** Hay diferentes tipos de herramientas que se pueden usar para realizar pruebas comparativas de la velocidad de fotogramas de la aplicación, como:
* GPUView
* Depurador de gráficos de Visual Studio
* Profilers integrados en motores 3D como Unity

## <a name="hologram-render-distances"></a>Distancias de representación de hologramas

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

El sistema visual humano integra varias señales dependientes de la distancia cuando se fija y se centra en un objeto.
* [Alojamiento:](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) el foco de un ojo individual.
* [Convergencia:](https://en.wikipedia.org/wiki/Convergence_(eye)) dos ojos que se mueven hacia dentro o hacia el exterior hasta el centro de un objeto.
* [Visión binocular:](https://en.wikipedia.org/wiki/Stereopsis) disparidades entre las imágenes de los ojos izquierdo y derecho que dependen de la distancia de un objeto desde el punto de fijación.
* Sombreado, tamaño angular relativo y otras indicaciones monoculares (un solo ojo).

La convergencia y el hospedaje son únicos porque sus indicaciones adicionales de la retinal relacionadas con cómo cambian los ojos para percibir objetos a distancias diferentes. En la visualización natural, la convergencia y el hospedaje están vinculados. Cuando los ojos ven algo cerca (por ejemplo, la punta), los ojos cruzan y se alojan en un punto cercano. Cuando los ojos ven algo a infinito, los ojos se vuelven paralelos y el ojo se adapta al infinito. 

Los usuarios HoloLens siempre se alojarán a 2,0 m para mantener una imagen clara porque las pantallas HoloLens se fijan a una distancia óptica de aproximadamente 2,0 m del usuario. Los desarrolladores de aplicaciones controlan dónde convergen los ojos de los usuarios colocando contenido y hologramas a varias profundidades. Cuando los usuarios se alojan y convergen a distancias diferentes, se rompe el vínculo natural entre las dos indicaciones, lo que puede provocar molestias visuales o agotamiento, especialmente cuando la magnitud del conflicto es grande. 

La incomodidad del conflicto entre el ambiente y la vida puede evitarse o minimizarse manteniendo el contenido convergente lo más cerca posible de 2,0 m (es decir, en una escena con mucha profundidad coloca las áreas de interés cerca de 2,0 m, siempre que sea posible). Cuando el contenido no se puede colocar cerca de 2,0 m, las molestias del conflicto entre el hospedaje y la vida son mayores cuando la mirada del usuario hacia delante y hacia atrás entre distintas distancias. En otras palabras, es mucho más cómodo ver un holograma estático que se mantiene a 50 cm de distancia que mirar un holograma a 50 cm que se acerca y se aleja del usuario con el tiempo.

Colocar contenido a 2,0 m también es ventajoso porque las dos pantallas están diseñadas para superponerse por completo a esta distancia. En el caso de las imágenes colocadas fuera de este plano, a medida que se desplazan fuera del lado del marco holográfico, aparecerán de una pantalla mientras siguen estando visibles en la otra. Este binocular puede ser perjudicial para la percepción de profundidad del holograma.

**Distancia óptima para colocar hologramas respecto al usuario**

![Distancia óptima para colocar hologramas respecto al usuario](images/distanceguiderendering-750px.png)

**Planos de recorte** Para obtener la máxima comodidad, se recomienda recortar la distancia de representación a 85 cm con atenuación de contenido a partir de 1 m. En las aplicaciones en las que los hologramas y los usuarios son tanto estacionados, los hologramas se pueden ver cómodamente como unos 50 cm. En esos casos, las aplicaciones deben colocar un plano de recorte no superior a 30 cm y el desvanecimiento debe comenzar al menos a 10 cm de distancia del plano de recorte. Siempre que el contenido esté más cerca de 85 cm, es importante asegurarse de que los usuarios no se acerquen o se acerquen con frecuencia a los hologramas o que los hologramas no se acerquen o se acerquen más al usuario, ya que es más probable que estas situaciones causen molestias a causa del conflicto entre la permanencia y el hospedaje. El contenido debe diseñarse para minimizar la necesidad de interacción más cercana a 85 cm del usuario, pero cuando el contenido se debe representar más cerca de 85 cm, una buena regla general para los desarrolladores es diseñar escenarios en los que los usuarios o hologramas no se muevan en profundidad más del 25 % del tiempo.

**Procedimientos recomendados** Cuando no se pueden colocar hologramas a 2 m y no se pueden evitar conflictos entre convergencia y alojamiento, la zona óptima para la colocación del holograma está entre 1,25 m y 5 m. En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios a interactuar a más de 1 m de distancia (por ejemplo, ajustar el tamaño del contenido y los parámetros de selección de ubicación predeterminados).

## <a name="reprojection"></a>Reproducción
HoloLens una sofisticada técnica de estabilización holográfica asistida por hardware conocida como reproyecto. La reproducción tiene en cuenta el movimiento y el cambio del punto de vista (CameraPose) a medida que la escena se anima y el usuario mueve la cabeza.  Las aplicaciones deben realizar acciones específicas para usar mejor la reproducción.


Hay cuatro tipos principales de reproducción
* **Reproducción de profundidad:**  Genera los mejores resultados con la menor cantidad de esfuerzo de la aplicación.  Todas las partes de la escena representada se estabilizan de forma independiente en función de su distancia con el usuario.  Algunos artefactos de representación pueden ser visibles cuando hay cambios nítidos en profundidad.  Esta opción solo está disponible en HoloLens 2 cascos envolventes.
* **Reproducción plana:**  Permite a la aplicación un control preciso sobre la estabilización.  La aplicación establece un plano y todo en ese plano será la parte más estable de la escena.  Cuando más un holograma esté fuera del plano, menos estable será.  Esta opción está disponible en todas las Windows de MR.
* **Reproducción planar automática:**  El sistema establece un plano de estabilización mediante información en el búfer de profundidad.  Esta opción está disponible en HoloLens generación 1 y HoloLens 2.
* **Ninguno:** Si la aplicación no hace nada, se usa Planar Reprojection con el plano de estabilización fijo a 2 metros en la dirección de la mirada con la cabeza del usuario, lo que suele producir resultados no estándar.

Las aplicaciones deben realizar acciones específicas para habilitar los distintos tipos de reproducción.
* **Reproducción de profundidad:** La aplicación envía su búfer de profundidad al sistema para cada fotograma representado.  En Unity, la reproducción de profundidad se realiza con la opción **Búfer** de profundidad compartido en el **panel Windows Mixed Reality Configuración** en Administración de complementos **XR**.  Las aplicaciones de DirectX llaman a CommitDirect3D11DepthBuffer.  La aplicación no debe llamar a SetFocusPoint.
* **Reproducción plana:** En cada fotograma, las aplicaciones le dicen al sistema la ubicación de un plano para estabilizarse.  Las aplicaciones de Unity llaman a SetFocusPointForFrame y deben tener **deshabilitado el búfer de profundidad** compartido.  Las aplicaciones de DirectX llaman a SetFocusPoint y no deben llamar a CommitDirect3D11DepthBuffer.
* **Reproducción planar automática:** Para habilitarlo, la aplicación debe enviar su búfer de profundidad al sistema como lo haría para la reproducción de profundidad. Las aplicaciones que usan Mixed Reality Toolkit (MRTK) pueden configurar el proveedor de configuración de la cámara para que use La reproducción automática. [](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) Las aplicaciones nativas deben establecer `DepthReprojectionMode` en [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) en `AutoPlanar` cada fotograma. Para HoloLens generación 1, la aplicación no debe llamar a SetFocusPoint.

### <a name="choosing-reprojection-technique"></a>Elección de la técnica de reproducción

Tipo de estabilización |    Cascos envolventes |    HoloLens generación 1 | HoloLens 2
--- | --- | --- | ---
Reproducción de profundidad |    Recomendado |   N/D |   Recomendado<br/><br/>Las aplicaciones de Unity deben usar Unity 2018.4.12+, Unity 2019.3+ o Unity 2020.3+. De lo contrario, use Reproyecto automático planar.
Reproducción plana automática | N/D |   Valor predeterminado recomendado |   Se recomienda si la reproducción de profundidad no da los mejores resultados<br/><br/>Se recomienda que las aplicaciones de Unity usen Unity 2018.4.12+, Unity 2019.3+ o Unity 2020.3+.  Las versiones anteriores de Unity funcionarán con resultados de reproducción ligeramente degradados.
Reproducción plana |   No recomendado |   Se recomienda si Planar automático no está dando los mejores resultados | Use si ninguna de las opciones de profundidad ofrece los resultados deseados.    

### <a name="verifying-depth-is-set-correctly"></a>Comprobar que la profundidad está establecida correctamente
            
Cuando un método de reproducción usa el búfer de profundidad, es importante comprobar el contenido del búfer de profundidad que representa la escena de representación de la aplicación.  Varios factores pueden causar problemas. Si hay una segunda cámara que se usa para representar superposiciones de interfaz de usuario, por ejemplo, es probable que sobrescriba toda la información de profundidad de la vista real.  Los objetos transparentes a menudo no establecen profundidad.  Algunas representaciones de texto no establecerán la profundidad de forma predeterminada.  Habrá problemas visibles en la representación cuando la profundidad no coincida con los hologramas representados.
            
HoloLens 2 un visualizador para mostrar dónde está y no se establece la profundidad, que se puede habilitar desde Portal de dispositivos.  En la pestaña **Views**  >  **Hologram Stability (Estabilidad del** holograma de vistas), active la casilla Mostrar visualización de profundidad en **casco.**  Las áreas que tengan la profundidad establecida correctamente serán azules.  Los elementos representados que no tienen un conjunto de profundidad están marcados en rojo y deben ser corregidos.  

> [!NOTE]
> La visualización de la profundidad no se mostrará en Captura de realidad mixta.  Solo es visible a través del dispositivo.
            
Algunas herramientas de visualización de GPU permitirán la visualización del búfer de profundidad.  Los desarrolladores de aplicaciones pueden usar estas herramientas para asegurarse de que la profundidad se establece correctamente.  Consulte la documentación de las herramientas de la aplicación.

### <a name="using-planar-reprojection"></a>Uso de Reproyecto planar
> [!NOTE]
> En el caso de los cascos envolventes de escritorio, establecer un plano de estabilización suele ser contraproducente, ya que ofrece menos calidad visual que proporcionar el búfer de profundidad de la aplicación al sistema para habilitar la reproducción basada en profundidad por píxel. A menos que se ejecute HoloLens, por lo general debe evitar establecer el plano de estabilización.

![Plano de estabilización para objetos 3D](images/stab-plane-500px.jpg)

El dispositivo intentará elegir automáticamente este plano, pero la aplicación debe ayudar seleccionando el punto de enfoque en la escena. Las aplicaciones de Unity que se ejecutan HoloLens deben elegir el mejor punto de enfoque en función de la escena y pasarlo a [SetFocusPoint().](../unity/focus-point-in-unity.md) Se incluye un ejemplo de cómo establecer el punto de enfoque en DirectX en la plantilla de cubo de giro predeterminada.

Unity envía el búfer de profundidad a Windows para habilitar la reproducción por píxel al ejecutar la aplicación en un casco envolvente conectado a un equipo de escritorio, lo que proporciona una calidad de imagen aún mejor sin que la aplicación lo haga explícitamente. Solo debe proporcionar un punto de enfoque cuando la aplicación se ejecute en un HoloLens o se invalidará la reproducción por píxel.


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

La colocación del punto de enfoque depende en gran medida de lo que esté mirando el holograma. La aplicación tiene el vector de mirada como referencia y el diseñador de aplicaciones sabe qué contenido quiere que observe el usuario.

Lo más importante que un desarrollador puede hacer para estabilizar los hologramas es representar a 60 FPS. Si se deja por debajo de 60 FPS, se reducirá drásticamente la estabilidad del holograma, independientemente de la optimización del plano de estabilización.

**Procedimientos recomendados** No hay ninguna manera universal de configurar el plano de estabilización y es específico de la aplicación. Nuestra recomendación principal es experimentar y ver lo que funciona mejor para su escenario. Sin embargo, intente alinear el plano de estabilización con tanto contenido como sea posible porque todo el contenido de este plano está perfectamente estabilizado.

Por ejemplo:
* Si solo tiene contenido plano (aplicación de lectura, aplicación de reproducción de vídeo), alinee el plano de estabilización con el plano que tiene el contenido.
* Si hay tres esferas pequeñas que están bloqueadas por el mundo, haga que el plano de estabilización se "corte" a través de los centros de todas las esferas que están actualmente en la vista del usuario.
* Si la escena tiene contenido en profundidades considerablemente diferentes, favorezca más objetos.
* Asegúrese de ajustar el punto de estabilización de cada fotograma para que coincida con el holograma que el usuario está mirando.

**Cosas que se deben evitar** El plano de estabilización es una excelente herramienta para lograr hologramas estables, pero si se usa incorrectamente, puede provocar una inestabilidad grave de la imagen.
* No se "desaprenda y se olvide". Puede terminar con el plano de estabilización detrás del usuario o conectado a un objeto que ya no está en la vista del usuario. Asegúrese de que el plano de estabilización normal está establecido frente a la cámara hacia delante (por ejemplo, -camera.forward).
* No cambie rápidamente el plano de estabilización entre extremos
* No deje el plano de estabilización establecido en una distancia o orientación fijas.
* No permita que el plano de estabilización pase por el usuario
* No establezca el punto de enfoque cuando se ejecute en un equipo de escritorio en lugar de en un HoloLens y, en su lugar, confíe en la reproducción basada en profundidad por píxel.

## <a name="color-separation"></a>Separación de colores 

Debido a la naturaleza de las HoloLens, a veces se puede percibir un artefacto denominado "separación de colores". Se manifiesta como la imagen que se separa en colores base individuales: rojo, verde y azul. El artefacto puede ser especialmente visible al mostrar objetos en blanco, ya que tienen grandes cantidades de rojo, verde y azul. Se pronuncia más cuando un usuario realiza un seguimiento visual de un holograma que se mueve a alta velocidad a través del marco holográfico. Otra manera en que el artefacto se puede manifiesto es desaformar o desaformar objetos. Si un objeto tiene contraste alto o colores puros, como rojo, verde, azul, separación de colores, se percibirá como deformación de diferentes partes del objeto.

**Ejemplo del aspecto que podría tener la separación de color de un cursor de redondeo blanco bloqueado por la cabeza cuando un usuario gira la cabeza hacia el lado:**

![Ejemplo del aspecto que podría tener la separación de color de un cursor de redondeo blanco bloqueado por la cabeza cuando un usuario gira la cabeza hacia el lado.](images/colorseparationofroundwhitecursor-300px.png)

Aunque es difícil evitar completamente la separación de colores, hay varias técnicas disponibles para mitigarla.

**La separación de colores se puede ver en:**
* Objetos que se mueven rápidamente, incluidos los objetos bloqueados con la cabeza, como el [cursor](../../design/cursors.md).
* Objetos que están considerablemente lejos del plano [de estabilización.](hologram-stability.md#reprojection)

**Para atenuar los efectos de la separación de colores:**
* Haga que el objeto relame la mirada del usuario. Debería aparecer como si hubiera cierta inercia y se adjuntara a la mirada "en la ventana". Este enfoque ralentiza el cursor (reduce la distancia de separación) y lo coloca detrás del punto de mirada probable del usuario. Siempre y cuando se resalte rápidamente cuando el usuario deje de desplazar la mirada, parece natural.
* Si desea mover un holograma, intente mantener su velocidad de movimiento por debajo de 5 grados por segundo si espera que el usuario lo siga con los ojos.
* Use *luz* en lugar *de geometría* para el cursor. Una fuente de iluminación virtual conectada a la mirada se percibe como un puntero interactivo, pero no provocará la separación de colores.
* Ajuste el plano de estabilización para que coincida con los hologramas que el usuario está mirando.
* Haga que el objeto sea rojo, verde o azul.
* Cambie a una versión desenfoque del contenido. Por ejemplo, un cursor blanco redondeado podría cambiarse a una línea ligeramente desenfoque orientada en la dirección del movimiento.

Como antes, la representación a 60 FPS y el establecimiento del plano de estabilización son las técnicas más importantes para la estabilidad del holograma. Si se enfrenta a una separación de color apreciable, primero asegúrese de que la velocidad de fotogramas cumple las expectativas.

## <a name="see-also"></a>Consulte también
* [Descripción del rendimiento de Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Color, luz y materiales](../../design/color-light-and-materials.md)
* [Interacciones instintivas](../../design/interaction-fundamentals.md)
* [Estabilización de hologramas de MRTK](/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization)