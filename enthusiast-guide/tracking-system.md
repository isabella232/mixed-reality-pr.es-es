---
title: Funcionamiento del seguimiento de la interacción directa
description: Información sobre el sistema de seguimiento interno basado en la cámara que se usa en los auriculares con Windows Mixed Reality.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, Inside-Out, interior Out, Tracking, Camera
ms.openlocfilehash: af7553b27bec63c2ae83bed390c17e1fcf006954
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725876"
---
# <a name="inside-out-tracking"></a>Seguimiento de la interacción directa

## <a name="how-does-inside-out-tracking-work"></a>¿Cómo funciona el seguimiento interno?

**Respuesta rápida:** el sistema de seguimiento usa dos cámaras ligeras de baja resolución visibles para observar las características de su entorno. A continuación, las cámaras disfunden la información con los datos de IMU para determinar una posición precisa del dispositivo en el entorno.

**Más detalles:** El sistema de seguimiento utiliza dos cámaras de blanco y negro de baja resolución para identificar las características de su entorno en la luz visible. El sistema triangular su posición en función de las características observadas, que, a continuación, complementa la información mediante la fusión de datos de IMU de alta tasa para producir una estimación de supuestos continuos para el HMD de su entorno. Ambas aplicaciones usan la información de pose para representar una escena y el sistema para corregir esta representación para cualquier predicción incorrecta en el tiempo y la posición. Su PC almacena información de entorno para que el sistema de seguimiento pueda recuperar datos específicos del entorno, como la ubicación física de los límites de la habitación. Si usa el dispositivo en varios salones, puede configurar límites diferentes en cada habitación y el sistema de seguimiento puede recordar el límite específico para el salón específico.

Dado que el seguimiento de los auriculares de la realidad mixta de Windows funciona como el seguimiento en [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), es posible que este vídeo le resulte útil:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>¿Qué es necesario para que el seguimiento funcione correctamente?

Hay dos preocupaciones para asegurarse de que el seguimiento funcione correctamente:
1. Asegúrese de que su equipo cumple los requisitos para ejecutar Windows Mixed Reality. Si su equipo cumple los requisitos mínimos para Windows Mixed Reality, el seguimiento tendrá recursos suficientes para ejecutarse correctamente en su PC.
2. Asegúrese de que su entorno sea adecuado para el tipo de seguimiento visual que emplea el dispositivo. Debe usar el dispositivo en un entorno con suficiente luz. Dado que el dispositivo funciona observando el entorno en la luz visible, debe haber suficiente luz para que se pueda observar el entorno. También debe haber suficientes características visuales distintivas (es decir, decoraciones, puntos de contraste, etc.) para que el sistema de seguimiento funcione.

## <a name="how-much-light-is-enough-light"></a>¿Cuánta luz tiene suficiente luz?

Si puede desplazarse de un lado a otro, sin sentir que es demasiado oscuro, y si puede observar las características de otras personas de todo el salón, es probable que el sistema de seguimiento tenga suficiente luz. Tenga en cuenta que se trata de algo tan ligero: Si está mirando a la luz del sol, las cámaras pueden saturarse y no realizar un seguimiento confiable. 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>¿Cuál es el número recomendado de características del entorno?

El producto se ha diseñado para funcionar en entornos normales. Tenga en cuenta el siguiente experimento de pensamiento: si se encontraba en un salón en blanco con paredes blancas, un límite superior blanco y un suelo blanco, el sistema de seguimiento no encontraría ninguna característica para realizar el seguimiento y produciría un error. Si se encontraba en una habitación que se encontraba en el trabajo y la decoración de arte, el sistema de seguimiento encontraría muchas características para realizar el seguimiento y funcionaría bien. Normalmente, normalmente se ha demostrado que las oficinas y los hogares representativos tienen suficientes detalles de las características para realizar un seguimiento adecuado.

## <a name="how-fast-can-i-move-with-the-device"></a>¿Con qué rapidez puedo migrar con el dispositivo?

El dispositivo está diseñado para admitir el movimiento en exceso de lo que suele experimentar el movimiento de cabeza humana. No dude en continuar. Tenga en cuenta que ha reducido el conocimiento de su entorno físico en un casco envolvente, por lo que debe asegurarse de que está migrando de forma segura en su entorno.

## <a name="where-will-tracking-not-work"></a>¿Dónde no funcionará el seguimiento?

El seguimiento no funcionará en un salón oscuro en el que las cámaras no puedan ver suficientes características debido a la poca luz. El seguimiento no funcionará bien (o a veces en absoluto) en el traslado de vehículos como aviones, buses, trenes, automóviles o ascensores. También puede producirse un error en situaciones en las que haya demasiada luz o una diferencia fuerte clara. Por ejemplo, si hay un flujo directo de luz solar en una habitación, las cámaras pueden reducir la exposición para reducir la saturación y no verán las características naturales normales. Se recomienda que se ajuste a la iluminación relativamente uniforme y, en caso de que tenga que Squint o encuentre cosas inadecuadamente brillantes, es posible que el sistema de seguimiento no sea correcto. 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>¿Cuál es la diferencia entre 3DOF y 6DOF?

En primer lugar, DOF está a mano para "Degrees of Freedom". Al hablar de los sistemas de seguimiento, esto significa los grados o tipos de movimiento que se pueden detectar. Estos movimientos se dividen en dos categorías principales: ' Rotation ' y ' Rotation with Translation '. 3DOF hace referencia a 3 grados de libertad y representa las rotaciones de cada eje. En pocas palabras, el seguimiento de 3DOF le permite mirar a la izquierda o a la derecha, arriba o abajo e inclinar el lado lateral (rollo). No se puede traducir o recorrer hacia delante o hacia atrás en 3DOF. 6DOF es la abreviatura de 6 grados de libertad. Se basa en las rotaciones de 3DOF y se agregan a las traducciones de ti. Esto significa que puede recorrer hacia delante o hacia atrás, Strafe hacia la izquierda o la derecha, y Crouch. El seguimiento de tres DOF es el tipo de seguimiento que normalmente encontraría en un producto o dispositivo de VR basado en móviles, mientras que 6DOF se encontrará en plataformas de VR más eficaces. Algunas experiencias se adaptan a 3DOF y solo permiten el movimiento 3DOF (giros), incluso si el dispositivo admite el seguimiento de 6DOF. Un ejemplo de esto sería ver un vídeo de 360 en Windows Mixed Reality. El vídeo le permitirá buscar, pero no le permitirá recorrer el entorno.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Las cosas están vibrando o retrasando el casco. ¿Mi seguimiento no funciona?

Hay un par de orígenes de este tipo de error. Es importante atribuir lo que está observando a la causa correcta para que se pueda solucionar. Consulte la sección de [solución de problemas](tracking.md) para ayudar a comprender por qué esto puede ocurrir.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>¿Puedo traer mi propia tecnología de seguimiento a Windows Mixed Reality?

Esta funcionalidad no se admite actualmente.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>¿Por qué veo la interfaz de usuario que dice "no se encuentra el límite?"

Dado que el límite de seguridad es específico de una ubicación física, si está usando el dispositivo en una ubicación diferente, el sistema no puede encontrar los límites. Además, una vez que haya configurado el límite, el sistema siempre lo buscará, incluso si usa el dispositivo en una ubicación física diferente. Verá esta interfaz de usuario siempre que use el dispositivo en una ubicación diferente y no haya configurado todavía un límite en esa ubicación. Puede configurar límites en cada ubicación en la que use el dispositivo y el dispositivo recordará los límites específicos de la ubicación.

Si usa el dispositivo en una ubicación en la que ha configurado previamente un límite y el dispositivo todavía no puede encontrarlo, puede configurar nuevos límites o borrar todos los datos de entorno para quitar todos los límites del dispositivo. Consulte la sección de [solución de problemas](tracking.md) para saber por qué el sistema no puede encontrar los límites y pasos para corregirlo.

## <a name="how-do-i-set-up-tracking"></a>¿Cómo configurar el seguimiento?

El seguimiento en Windows Mixed Reality es fácil de usar, no se requiere ninguna infraestructura o configuración. Si elige, puede configurar un límite virtual para su uso. Vea la sección sobre [Cómo configurar el límite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) para obtener más información.

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Cómo borrar los datos de entorno y seguimiento?

El sistema de seguimiento almacena algunos datos de entorno para que pueda recuperar la ubicación física del mundo real de cosas como los límites de seguridad. Esta información, incluidos los límites de seguridad, se puede quitar en cualquier momento. Si se quita esta información, el sistema ya no reconocerá el espacio ni recuperará los límites de seguridad. Si desea usar límites de seguridad después de borrar los datos del entorno, tendrá que configurarlo de nuevo. Consulte la sección sobre cómo configurar [el límite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) para configurar un nuevo límite. Para quitar todos estos datos, abra configuración, vaya a "Mixed Reality" (realidad mixta) y seleccione la sección entorno en el menú del lado izquierdo. Seleccione el botón "borrar datos de entorno" para quitar todos los datos de seguimiento y de entorno.

## <a name="see-also"></a>Consulte también
* [Solución de problemas del sistema de seguimiento](tracking.md)
* [Controladores de movimiento](controllers-in-wmr.md)
* [Ambiente principal de Windows Mixed Reality](your-mixed-reality-home.md)
* [Uso de juegos y aplicaciones en Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
