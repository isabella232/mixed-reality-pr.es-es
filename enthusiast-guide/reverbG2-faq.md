---
title: Preguntas más frecuentes de la reverberación de HP G2
description: Preguntas más frecuentes sobre el uso de la reverberación de HP G2 auriculares
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, rendimiento
appliesto:
- Windows 10
ms.openlocfilehash: 82f9accc8e24574faf7c826aff1908bea7350b08
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049481"
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

Si ve un error 7-14 "algo ha ido mal", realice los pasos siguientes:

- Asegúrese de que tiene los controladores más recientes instalados.
- Intente conectar el cable a otro puerto USB-3,0.
- Use USB C en un adaptador incluido para probar distintos puertos.

Intente conectar el cable a un concentrador USB diferente.  

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

Aunque muchos juegos funcionarán inmediatamente con los controladores de movimiento de HP, algunos juegos dependen de las características de los controladores existentes y, por tanto, pueden tener algunos problemas:

- Se muestra un modelo incorrecto: la corrección requiere una actualización del juego. Por lo general, esto no bloquea ninguna característica del juego, pero podría provocar confusión o incluso artefactos visuales.
- Dependencia en el panel táctil o más general en el diseño de entrada del controlador. SteamVR permite crear enlaces personalizados para evitar este tipo de problema:
    - Windows Mixed Reality para SteamVR incluye enlaces personalizados para algunos juegos. Estos enlaces se usan automáticamente cuando se inicia el juego y no se necesita ninguna acción del usuario.