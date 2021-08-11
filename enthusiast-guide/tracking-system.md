---
title: Funcionamiento del seguimiento de la interacción directa
description: Información sobre el sistema de seguimiento interno basado en cámara que se usa Windows Mixed Reality cascos.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, inside-out, inside out, tracking, camera
ms.openlocfilehash: 579ef23c1eca2c184d07878c4e71ce298c5ad9922255b5e43643458a256b61bf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197869"
---
# <a name="inside-out-tracking"></a>Seguimiento de la interacción directa

## <a name="how-does-inside-out-tracking-work"></a>¿Cómo funciona el seguimiento interno?

**Respuesta rápida: el** sistema de seguimiento usa dos cámaras de baja resolución de luz visible para observar las características de su entorno. A continuación, las cámaras fusionan la información con los datos de IMU para determinar una posición precisa del dispositivo en su entorno.

**Más detalles:** El sistema de seguimiento usa dos cámaras en blanco y negro de baja resolución para identificar las características del entorno con luz visible. El sistema trianitlará su posición en función de las características observadas, lo que complementa la información mediante la conversión de datos de IMU de alta velocidad para generar una estimación de posición continua para el HMD en su entorno. La información de posición la usan ambas aplicaciones para representar una escena y el sistema para corregir esta representación para cualquier predicción errónea en el tiempo y la posición. El equipo almacena información del entorno para que el sistema de seguimiento pueda recuperar datos específicos del entorno, como la ubicación física de los límites de la sala. Si usa el dispositivo en varias salas, puede configurar límites diferentes en cada sala y el sistema de seguimiento puede recuperar el límite específico de la sala específica.

Dado que el seguimiento Windows Mixed Reality cascos envolventes funciona como el seguimiento [en Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), puede resultar útil este vídeo:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>¿Qué es necesario para que el seguimiento funcione bien?

Hay dos cuestiones que debe abordar para asegurarse de que el seguimiento funcione bien para usted:
1. Asegúrese de que el equipo cumple los requisitos para ejecutar Windows Mixed Reality. Si el equipo cumple los requisitos mínimos de Windows Mixed Reality, el seguimiento tendrá suficientes recursos para ejecutarse bien en el equipo.
2. Asegúrese de que el entorno es adecuado para el tipo de seguimiento visual que emplea el dispositivo. Debe usar el dispositivo en un entorno con suficiente luz. Dado que el dispositivo funciona observando el entorno en una luz visible, debe haber suficiente luz para que se pueda observar el entorno. También debe haber suficientes características visuales distintivas (es decir, decoración, puntos de contraste, entre otras) para que el sistema de seguimiento funcione.

## <a name="how-much-light-is-enough-light"></a>¿Cuánta luz es suficiente?

Si puede moverse cómodamente por el entorno sin sentir que está demasiado oscuro y si puede observar las características de otras personas frente a la sala, es probable que el sistema de seguimiento tenga suficiente luz. Tenga en cuenta que hay demasiada luz; si mira el sol, las cámaras pueden saturarse y no realizar un seguimiento confiable. 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>¿Cuál es el número recomendado de características ambientales?

El producto se ha diseñado para funcionar en entornos normales. Considere el siguiente experimento de reflexión: si estuviera en una sala en blanco con paredes blancas, un suelo blanco y un suelo blanco, el sistema de seguimiento no encontraría características de las que realizar el seguimiento y se produciría un error. Si estuviera en una sala cubierta por el trabajo de arte y la decoración, el sistema de seguimiento encontraría muchas características de las que realizar un seguimiento y funcionaría bien. Normalmente, se ha demostrado que las oficinas y las casa con decoración tienen suficientes detalles de características para realizar un seguimiento correcto.

## <a name="how-fast-can-i-move-with-the-device"></a>¿Con qué rapidez puedo moverme con el dispositivo?

El dispositivo está diseñado para admitir el movimiento en exceso de lo que normalmente experimenta el movimiento de la cabeza humana. No dude en moverse a su medida. Tenga en cuenta que ha reducido el conocimiento del entorno físico mientras está en un casco envolvente, por lo que debe asegurarse de que se mueve de forma segura en su entorno.

## <a name="where-will-tracking-not-work"></a>¿Dónde funcionará el seguimiento?

El seguimiento no funcionará en una sala oscura donde las cámaras no puedan ver suficientes características debido a la poca luz. El seguimiento no funcionará bien (o a veces funciona en absoluto) en vehículos móviles, como aviones, camiones, tren, automóviles o ascensores. El seguimiento también puede producir errores en situaciones en las que hay demasiada luz o una diferencia de luz fuerte. Por ejemplo, si hay un flujo directo de luz en una sala, las cámaras pueden reducir la exposición para reducir la saturación y no verán características naturales normales. Se recomienda mantener la iluminación relativamente uniforme y, si tiene que desenlazar o encontrar cosas descomprimiblemente brillantes, es posible que el sistema de seguimiento no lo haga bien. 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>¿Cuál es la diferencia entre 3DOF y 6DOF?

En primer lugar, doF es una forma breve de "grados de libertad". Al analizar los sistemas de seguimiento, esto significa los grados o los tipos de movimiento que se pueden detectar. Estos movimientos se desglosan en dos categorías principales: "rotación" y "rotación con traducción". 3DOF hace referencia a 3 grados de libertad y representa las rotaciones de cada eje. En pocas palabras, el seguimiento de 3DOF le permite mirar a la izquierda o a la derecha, subir o bajar, e inclinar la cabeza (enrollar) de lado a lado. No se puede traducir o avanzar o retroceder en 3DOF. 6DOF es corto para 6 grados de libertad. Se basa en las rotaciones de 3DOF y le agrega traducciones. Esto significa que puede avanzar o retroceder, retroceder a la izquierda o a la derecha y agacharse y ponerse de pie. El seguimiento de tres DOF es el tipo de seguimiento que normalmente encontraría en un producto de realidad virtual basado en teléfonos o móviles, mientras que 6DOF se encontrará en plataformas de REALIDAD virtual más eficaces. Algunas experiencias están adaptadas a 3DOF y solo permitirán movimiento 3DOF (rotaciones), incluso si el dispositivo admite el seguimiento de 6DOF. Un ejemplo de esto sería ver un vídeo de 360 en Windows Mixed Reality. El vídeo le permitirá mirar a su alrededor, pero no le permitirá recorrer su entorno.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Las cosas se están torcándose o ateando en el casco. ¿Mi seguimiento no funciona?

Hay un par de orígenes de este tipo de error. Es importante atribuir lo que observa a la causa correcta para que se pueda solucionar. Consulte la sección [de solución de](tracking.md) problemas para comprender por qué puede ocurrir esto.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>¿Puedo aportar mi propia tecnología de seguimiento a Windows Mixed Reality?

Esta funcionalidad no se admite actualmente.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>¿Por qué veo la interfaz de usuario que dice "No se encuentra el límite?"

Puesto que el límite de seguridad es específico de una ubicación física, si usa el dispositivo en una ubicación diferente, el sistema no puede encontrar los límites. Además, una vez que haya configurado el límite, el sistema siempre lo buscará, incluso si usa el dispositivo en una ubicación física diferente. Verá esta interfaz de usuario cada vez que use el dispositivo en una ubicación diferente y aún no haya configurado un límite en esa ubicación. Puede configurar límites en cada ubicación en la que use el dispositivo y el dispositivo recuperará los límites específicos de la ubicación.

Si usa el dispositivo en una ubicación en la que ha configurado previamente un límite y el dispositivo todavía no lo encuentra, puede configurar nuevos límites o borrar todos los datos del entorno para quitar todos los límites del dispositivo. Consulte la [sección de solución](tracking.md) de problemas para comprender por qué el sistema no puede encontrar los límites y los pasos para corregirlo.

## <a name="how-do-i-set-up-tracking"></a>Cómo configurar el seguimiento?

El seguimiento en Windows Mixed Reality es fácil de usar, no se requiere ninguna infraestructura ni configuración. Si lo decide, puede configurar un límite virtual para su uso. Consulte la sección sobre [cómo configurar el límite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) para obtener más información.

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Cómo datos claros del entorno y el seguimiento?

El sistema de seguimiento almacena algunos datos del entorno para que pueda recuperar la ubicación física real de cosas como los límites de seguridad. Esta información, incluidos los límites de seguridad, se puede quitar en cualquier momento. Si se quita esta información, el sistema ya no reconocerá el espacio ni recuperará los límites de seguridad. Si desea usar límites de seguridad después de borrar los datos del entorno, tendrá que volver a configurarlo. Consulte la sección sobre [cómo configurar el límite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) para configurar un nuevo límite. Para quitar todos estos datos, abra Configuración, vaya a "Mixed Reality" y seleccione la sección Entorno del menú del lado izquierdo. Seleccione el botón con la etiqueta "Borrar datos del entorno" para quitar todos los datos de entorno y de seguimiento.

## <a name="see-also"></a>Consulte también
* [Solución de problemas del sistema de seguimiento](tracking.md)
* [Controladores de movimiento](controllers-in-wmr.md)
* [Ambiente principal de Windows Mixed Reality](your-mixed-reality-home.md)
* [Uso de juegos y aplicaciones en Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
