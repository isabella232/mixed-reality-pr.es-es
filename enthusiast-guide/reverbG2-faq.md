---
title: Preguntas más frecuentes de la reverberación de HP G2
description: Preguntas más frecuentes sobre el uso de la reverberación de HP G2 auriculares
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, rendimiento
appliesto:
- Windows 10
ms.openlocfilehash: 241fb95d92c771af727cc50287e4d1b2526123a5
ms.sourcegitcommit: c7b5790a26472c5a08c959189a574fb15f9046d2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "95002979"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>Preguntas más frecuentes de la reverberación de HP G2

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>¿Hay un orden específico que debe seguir para conectar los cables de auriculares a un PC?

HP recomienda:

- Conecte el cable de 6 metros al casco antes de conectarse al equipo o a la fuente de alimentación.
- Deje el cable de 6 metros conectado al casco después de la instalación inicial.
- Cuando el casco no esté en uso, desconecte el adaptador de alimentación del cable de 6 metros.

## <a name="what-should-i-do-to-get-a-crisper-image"></a>¿Qué debo hacer para obtener una imagen más nítida?

Hay algunas cosas que puede probar si cree que la pantalla tiene un aspecto un poco borroso:

- Asegúrese de que el casco está en su cabeza correctamente para que los ojos estén centrados en lo que respecta a los lentes.
- Intente ajustar el IPD (distancia interpupillary). Tenga en cuenta que la reverberación G2 usa un IPD de hardware. Para cambiarlo, busque el ajuste de IPD en el casco.
- Si necesita gafas o contactos, siguen siendo necesarios.
- Compruebe sus lentes si es necesario limpiarlas (solo microfiber tela).
- Debido al diseño avanzado de los auriculares, puede que haya alguna imagen secundaria con fantasma en los primeros minutos en que se inicia el dispositivo mientras está en frío hasta que las pantallas LCD tienen la oportunidad de prepararse.

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>Obtengo un error 7-14 "algo ha ido mal" al conectar mis auriculares

El Código 7-14 algo ha salido mal, lo que significa que no se encontraron algunos componentes USB2 necesarios.  Debido al cable extra largo de la reverberación de HP G2, algunas de las tolerancias para las señales USB son más estrictas.  Esto significa que un puerto del equipo puede funcionar de forma más confiable que otro.

Si ve un error 7-14 "algo ha ido mal", realice los pasos siguientes:

- Asegúrese de que tiene los controladores más recientes instalados para el casco y la controladora USB.
- Asegúrese de que está usando un controlador USB de Microsoft. Debe haber una "Microsoft" en el nombre del dispositivo "controlador de host extensible".
- Intente conectar el cable a un puerto USB-3,0 diferente en el equipo. (Pruebe los puertos USB tipo-C y tipo a)
- Use el USB C incluido en un adaptador para probar distintos puertos.
- Intente conectar los auriculares a través de un concentrador USB al equipo.

> [!NOTE]
> HP recomienda usar solo controladores USB integrados en la placa base con dispositivos de reverberación G2.
> Si no puede conectar el dispositivo, póngase en contacto [con el soporte técnico de HP](https://support.hp.com/us-en) .

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>Obtengo un error 13-14 "algo salió mal" cuando mi PC se reanuda de la hibernación (S4)

A veces, durante el proceso de reanudación, la tarjeta de vídeo no puede establecer una conexión, por lo que desconectar el tipo USB C del equipo y volver a conectarlo puede ayudarle a establecer una conexión.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>En el portal de realidad mixta se dice "no se puede ejecutar la realidad mixta en este casco", pero funciona bien con mis auriculares de WMR anteriores

Esto puede ocurrir porque la reverberación de HP G2 requiere un equipo más eficaz para garantizar la mejor experiencia. Para obtener más información, revise los requisitos mínimos del [equipo](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) .

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>Parece que la pantalla izquierda está ajustada y la pantalla derecha está descentrada y media negra

Esto puede ocurrir cuando el casco no se está ejecutando en la resolución nativa. Debido a la naturaleza de las pantallas de alta resolución en la reverberación de HP G2 HMD, no todos los sistemas podrán representar la resolución nativa. Existe una corrección en un futuro Windows Update que solucionará el problema de representación cuando el casco no esté en la resolución nativa.

Hay varias razones por las que el sistema no se puede representar en la resolución nativa:

- Es posible que el DisplayPort del sistema no sea compatible con 1,3 o que no admita las 4 calles.
- Si usa un adaptador, es posible que no admita HBR3 compatible o que no admita las 4 calles.
- Si el sistema tiene una GPU híbrida, podría estar limitando el ancho de banda disponible para el DisplayPort.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>¿Por qué los modelos de controlador de movimiento de HP no aparecen correctamente en un juego?

Aunque la mayoría de los juegos no muestran los controladores ni usan los modelos instalados por el controlador, algunos juegos usan sus propias versiones de los modelos de controlador, ya sean para personalizarlos o para mostrar ayuda contextual para las entradas disponibles. Normalmente, esto no bloquea ninguna de las características de los juegos, pero podría provocar confusiones o incluso artefactos visuales. Esto solo se puede solucionar con una actualización del propio juego.

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>Mis juegos de SteamVR no parecen funcionar correctamente con los controladores de movimiento de HP

Mientras los desarrolladores trabajan para actualizar sus juegos para la compatibilidad con HP Motion Controller, hemos proporcionado enlaces de controlador personalizados para muchos de los juegos más populares en vapor. Con "Windows Mixed Reality for SteamVR" totalmente actualizado a la versión 1.2.444, estos enlaces se deben recoger automáticamente cuando se ejecuta el juego. Sin embargo, si el juego no parece registrar las acciones en este momento, puede buscar manualmente perfiles de enlace personalizados mediante el menú de configuración de SteamVR.
Para hacer esto

- Abra el menú SteamVR presionando el botón de menú del controlador de movimiento derecho.
- Seleccione el icono "configuración" en la esquina inferior derecha del menú SteamVR
- Selección de la pestaña "controladores"
- Selección de la opción "administrar enlaces de controlador"

Desde aquí puede cambiar el enlace del controlador activo a "personalizado", que abrirá la opción para probar los enlaces de juegos de la comunidad.
Si aún no se ha compartido ningún enlace de juego personalizado para este juego (o si no está totalmente satisfecho con los que ha intentado), también puede crear sus propios enlaces de juego personalizados e incluso ayudar al resto de la comunidad compartiendo estos archivos después de algunas sesiones de juego.