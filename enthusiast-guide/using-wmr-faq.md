---
title: Preguntas más frecuentes sobre el uso de Windows Mixed Reality
description: Obtenga respuestas a preguntas habituales al trabajar con Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
appliesto:
- Windows 10
ms.openlocfilehash: 75ed2699cc34af5f526e0799b762d45ef36e99b9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725676"
---
# <a name="using-windows-mixed-reality-faq"></a>Preguntas más frecuentes sobre el uso de Windows Mixed Reality

Si necesita ayuda con el uso de un auricular envolvente de Windows Mixed Reality, consulte estos temas para obtener información general y solucionar problemas.

¿Aún necesita ayuda? Para la solución avanzada de problemas, consulte este artículo.

## <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Veo un mensaje que indica "pérdida de seguimiento" o "no tenemos límite para este espacio".

Seleccione **inicio > portal de realidad mixta** en el escritorio. Seleccione **menú** y, a continuación, seleccione **ejecutar el programa de instalación** para crear un nuevo límite. Windows Mixed Reality admite varias ubicaciones e identificará el espacio en el que se encuentra en el inicio, siempre y cuando la habitación no haya cambiado.  


## <a name="i-cant-hear-any-sound-or-the-sound-is-coming-from-my-computer-instead-of-my-headset"></a>No puedo oír ningún sonido o el sonido proviene del equipo en lugar de los auriculares

Si el casco envolvente no incluye auriculares integrados, deberá conectar los auriculares con el conector de audio del casco. (El conector suele encontrarse detrás del parasol o los lentes del casco; consulte con el fabricante del casco si tiene problemas para encontrarlo). 

Algunos auriculares de audio tienen botones físicos para controlar el volumen. Si el audio no funciona, compruebe si el volumen está desactivado o silenciado.

Windows Mixed Reality está diseñado para reproducir sonido a través de los auriculares inmersivo cuando está en su equipo y tiene auriculares conectados a él. Cuando saque el casco o gire el parasol hacia arriba, el audio cambiará al dispositivo de reproducción de Windows predeterminado. Puede cambiar esta configuración en **configuración > realidad mixta > audio y voz**.

> [!NOTE]
> * El audio espacial de realidad mixta de Windows funciona mejor con los auriculares incorporados o conectados directamente a los auriculares más inmersivo. Es posible que los altavoces o auriculares conectados al equipo no funcionen bien para el audio espacial.
> * Windows Mixed Reality no es compatible con los auriculares de audio Bluetooth.

## <a name="speech-commands-arent-working"></a>Los comandos de voz no funcionan

Para usar comandos de voz, la configuración de idioma y voz del equipo debe establecerse en una [región e idioma de Windows Mixed Reality compatible](other-questions.md#what-languages-are-supported-in-windows-mixed-reality). Para comprobar la región y el idioma de Windows, seleccione **configuración > tiempo & idioma > región & idioma**. Para comprobar el idioma de la voz, seleccione **configuración > tiempo & idioma > la voz**.

Si el casco no tiene un micrófono integrado, conecte un par de auriculares con un micrófono a su auricular o PC. Seleccione **configuración > realidad mixta > audio y voz** para cambiar automáticamente la entrada de MIC al casco cuando los auriculares están conectados. Asegúrese de que **, al gastar el casco, cambie al micrófono mic** está encendido.

Algunos auriculares de audio tienen un botón físico para silenciar y dessilenciar el micrófono. Si los comandos de voz no funcionan, compruebe si el MIC está silenciado.

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>El límite siempre es visible. ¿Cómo puedo hacer que salga?

Cuando esté cerca del límite, aparecerá. Si el límite incluye alguna sección que tiene una forma estrecha o irregular, puede acabar cerca de ella y hacer que aparezca, con más frecuencia de lo que desea. Para corregirlo, intente crear el límite de nuevo, con una forma más grande y más normal. Seleccione **inicio > portal de realidad mixta** en el escritorio y, a continuación, seleccione **ejecutar el programa de instalación**. 

También puede desactivar temporalmente el límite del portal de realidad mixta: seleccione el **menú** y, a continuación, use el control de alternancia para desactivar el límite. Cuando el límite esté desactivado, tendrá que permanecer en un lugar para evitar obstáculos.

## <a name="im-having-trouble-with-my-motion-controllers"></a>Tengo problemas con los controladores de movimiento

Si los controladores de movimiento no funcionan correctamente, no se está conectando, o si no ve una imagen de los controladores cuando tiene el casco:

* Asegúrese de que los controladores estén encendidos. Para activarlas, mantenga presionado el botón de **Windows** durante 2 segundos.
* Seleccione **inicio > portal de realidad mixta** en su equipo y, a continuación, seleccione **menú** . debería ver los controladores de movimiento enumerados, junto con un mensaje de estado:
    * Listo: todos los controladores están establecidos.
    * Seguimiento perdido: el portal de realidad mixta no puede encontrar los controladores. Manténgalos delante del casco y reinícielos presionando el botón **Windows** durante 4 segundos y, luego, de nuevo durante 2 segundos.
    * Batería baja: Reemplace las baterías del controlador.
* Si usa Wi-Fi, intente conectar el equipo a una red Wi-Fi de 5 GHz para reducir las interferencias inalámbricas. 
* Para los auriculares más recientes que se emparejan directamente con los controladores, seleccione el **"..."** en el **portal de realidad mixta** y elija **configurar controladores**. Esto le llevará a la aplicación de auriculares para emparejar los controladores con los auriculares.  
* Para auriculares más antiguos que no tienen Bluetooth integrado para que los controladores se emparejen directamente:  
    * Seleccione configuración > dispositivos > Bluetooth & otros dispositivos del equipo y asegúrese de que los controladores aparecen como emparejados.Si no es así, deberá emparejarlos. 
    * Si tiene otros dispositivos Bluetooth emparejados con su PC, como los auriculares o los controladores de juegos, intente quitar algunos. Seleccione **configuración > dispositivos > Bluetooth & otros dispositivos** del equipo, seleccione los dispositivos y, a continuación, seleccione **quitar dispositivo**.
    * Quite los altavoces y auriculares Bluetooth de la **configuración > dispositivos > Bluetooth & otros dispositivos** y apague los dispositivos. 
    * Si usa un adaptador Bluetooth USB, asegúrese de que está conectado a un puerto USB 2,0 negro. Asegúrese también de que el adaptador está enchufado en la medida de lo posible desde cualquier otro transmisor inalámbrico o unidad flash USB, incluido el conector USB del casco. 
    * Si su equipo tiene Bluetooth integrado y tiene problemas de conexión, pruebe a usar un adaptador de Bluetooth USB en su lugar. (Para ello, también debe desactivar la radio Bluetooth integrada en [Device Manager](https://support.microsoft.com/help/4026149)y, a continuación, emparejar los demás dispositivos Bluetooth con el adaptador nuevo).
* Si la aplicación de configuración está abierta en la página Bluetooth & otros dispositivos, ciérrela.

## <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Tengo problemas al usar el casco

Para obtener información general acerca de la comodidad en Windows Mixed Reality, vea [Windows mixed reality sobre el estado de los auriculares, la seguridad y la comodidad](wmr-health-safety-comfort.md). Para obtener más información sobre el casco específico, consulte con el fabricante del casco.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Mis objetos visuales son entrecortado, se cargan lentamente o no parecen buenos

Si los objetos visuales de realidad mixta no tienen el aspecto adecuado:

* Asegúrese de que el casco está enchufado en la tarjeta gráfica correcta del equipo. Algunos equipos tienen tarjetas de gráficos integradas y discretas. Por lo general, la tarjeta discreta proporcionará el mejor rendimiento. [Más información sobre el hardware de PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Cierre las aplicaciones no utilizadas en el escritorio.
* Ajuste el ajuste del casco: muévalo hacia abajo, a la izquierda y a la derecha, y asegúrese de que se ajusta perfectamente.
* Ajuste la configuración visual de los auriculares (**configuración > realidad mixta > pantalla de auriculares**). Cuando **calidad visual** esté establecida en **automático**, elegiremos la mejor experiencia de realidad mixta para tu equipo. Para obtener una experiencia con más detalles visuales, establezca **calidad visual** en **alta**. Si los objetos visuales son entrecortado, puede que desee seleccionar un valor inferior.
* Intente ajustar la calibración del casco. Las lentes deben ajustarse para que coincidan con la distancia de Interpupillary (IPD), la distancia entre los alumnos. Si no conoce el IPD, un Optometrist puede medirlo por usted. También hay sitios web diseñados para medir IPD. Una vez que conozca el IPD, use el botón de calibración del casco para realizar ajustes. Si el casco no tiene un botón de calibración, seleccione la **configuración > realidad mixta > auriculares para mostrar** y ajustar el control de calibración.

## <a name="i-have-questions-about-my-headset-hardware"></a>Tengo preguntas sobre el hardware de auriculares

Para obtener más información sobre el casco, consulte con el fabricante. Puede haber una guía de producto en el cuadro o puede probar el sitio web del fabricante.

## <a name="the-floor-in-mixed-reality-seems-to-be-in-the-wrong-spot"></a>El suelo de la realidad mixta parece estar en la zona equivocada

Si el piso parece estar desactivado (por ejemplo, parece que está flotando), seleccione **inicio > ajuste** de la habitación mientras usa los auriculares para realizar cambios.

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Aparece un mensaje que indica que se ha incorporado el equipo. ¿Por qué?

Si usa un equipo portátil, Windows Mixed Reality funciona mejor cuando el equipo está totalmente cargado y conectado.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Cómo desinstalar Windows Mixed Reality

Seleccione **inicio > configuración > realidad mixta** y, a continuación, seleccione **desinstalar**. Asegúrese de desconectar el casco del equipo y cerrar el portal de realidad mixta antes de desinstalar.

Cuando esté listo para empezar a usar el casco de nuevo, conéctelo y el portal de realidad mixta le guiará a través del programa de instalación.

> [!NOTE]
> Si ve un mensaje que dice "no pudimos acabar de quitar Windows Mixed Reality", esto significa que algunos archivos, incluida la información sobre su entorno, pueden seguir estando en el equipo. Esto puede causar problemas si decide volver a instalar Windows Mixed Reality más adelante.
> 
> Para obtener información sobre cómo quitar manualmente cualquier información restante de Windows mixed reality de su equipo, consulte **[este artículo](installation_errors.md)**.

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Mi Wi-Fi se ralentiza cuando utilizo Windows Mixed Reality

Si usa una conexión Wi-Fi a 2,4 GHz, los controladores de movimiento pueden ralentizar la red Wi-Fi:

<!-- TODO: Use Windows Mixed Reality PC hardware guidelines interlink -->
* Cambie a una conexión de Wi-Fi de 5 GHz, si hay alguna disponible. [Más información](https://support.microsoft.com/help/4000461)
* Use un adaptador Bluetooth independiente para conectar sus controladores de movimiento al equipo. [Consulte los adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

## <a name="what-is-the-experience-options-setting"></a>¿Cuál es la configuración de opciones de experiencia?

La configuración de las opciones de experiencia (**configuración > la realidad mixta > las opciones de experiencia > experiencia**) le permite cambiar la configuración de rendimiento de Windows Mixed Reality. Esto le permite elegir la mejor experiencia posible para la configuración de hardware en una variedad de contenido. La experiencia 90-Hz está disponible para todos los sistemas, pero es posible que desee probar la configuración automática primero para ver la configuración que prefiera.

Estas son las opciones:

* Automática o dejar que Windows decida: Windows Mixed Reality determinará la mejor experiencia para la configuración de hardware. Para la mayoría de los usuarios, esta es la mejor opción para empezar.
* 60 Hz: establece la frecuencia de actualización en 60 Hz y desactiva ciertas características, como la captura de vídeo y la vista previa en el portal de realidad mixta.
* 90 Hz: establece la frecuencia de actualización en 90 Hz si el casco puede ejecutarse a esa velocidad. Si los problemas de cable impiden que los auriculares se ejecuten a 90 Hz, es posible que vea un error al iniciar con este modo seleccionado. 

## <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Aparece un mensaje que indica "poner en el casco" aunque tengo el casco encendido

Al colocar el casco, Windows Mixed Reality necesita un poco de tiempo para volver a cargar el espacio. Esta operación puede tardar unos segundos. Si este mensaje no desaparece, asegúrese de que se ha quitado el adhesivo protector del sensor de proximidad, que se encuentra en el interior del casco, entre las lentes. Si se ha quitado la etiqueta y sigue teniendo problemas, póngase en contacto con el fabricante del casco. Si presiona **Win + Y** en el teclado, se activarán manualmente los auriculares para que se ejecuten si el sensor de proximidad no se activa automáticamente. 

¿Aún necesita ayuda? Para la solución avanzada de problemas, consulte [este artículo](troubleshooting-windows-mixed-reality.md).

## <a name="see-also"></a>Consulte también
* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)