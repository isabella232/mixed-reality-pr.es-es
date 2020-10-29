---
title: Preguntas más frecuentes sobre la instalación de Windows Mixed Reality
description: Obtenga respuestas a preguntas comunes sobre la instalación al trabajar con Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
appliesto:
- Windows 10
ms.openlocfilehash: 2e7276e7d734770e29ce41db9a19ef40555fea30
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692343"
---
# <a name="windows-mixed-reality-setup-faq"></a>Preguntas más frecuentes sobre la instalación de Windows Mixed Reality

A continuación se muestra información para ayudar a solucionar los problemas que se pueden encontrar al configurar el casco envolvente de Windows Mixed Reality.

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>Aparece un mensaje que indica "no pudimos descargar el software de la realidad mixta de Windows" o el programa de instalación está atascado en la página "se bloqueó la carga mientras hacemos algunas descargas".

Pruebe lo siguiente:
* Vaya a **configuración > actualizar & seguridad > Windows Update** y asegúrese de que Windows Update está activado. A continuación, descargue e instale las actualizaciones que estén esperando para ser instaladas.
* Asegúrese de que el equipo está conectado a Internet y tiene al menos 2 GB de espacio de almacenamiento libre.
* Reinicie el equipo e inténtelo de nuevo. Es posible que tenga que repetir varias veces o ejecutar el solucionador de problemas de Windows Update para borrar las actualizaciones pendientes. 

> [!NOTE]
> * Si se encuentra en una red administrada por la empresa, consulte con el administrador. Es posible que necesiten habilitar Windows Mixed Reality. ¿Busca las instrucciones para profesionales de ti? Consulte **[este artículo](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)** .
> * Si la conexión de red Wi-Fi está establecida en medido, cámbiela a desmedido. **[Más información](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>Aparece un mensaje que indica "se produjo un error y no pudimos iniciar Windows Mixed Reality".

Pruebe lo siguiente:
1. Desconecte el casco del equipo (ambos cables).
2. Reinicie el equipo.
3. Vaya a **configuración > Update & security > Windows Update** y asegúrese de que Windows Update está activado. A continuación, descargue e instale las actualizaciones que estén esperando para ser instaladas.
4. Vuelva a conectar los auriculares al equipo e intente realizar de nuevo la instalación.

Si los pasos anteriores no funcionan, intente desinstalar y reinstalar Windows Mixed Reality. Vaya a **configuración > realidad mixta > desinstalar** y seleccione **desinstalar** . Luego, reinicie el equipo. Para volver a iniciar el proceso de instalación, simplemente conecte el casco a su PC.

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>Aparece un mensaje que indica que mi PC no puede ejecutar Windows Mixed Reality.

Si recibe este mensaje, el equipo no cumple los [requisitos mínimos](https://support.microsoft.com/help/4039260) necesarios para ejecutar Windows Mixed Reality. Esto podría deberse a que la configuración de hardware del equipo no es compatible con Windows Mixed Reality, o a que es necesario [actualizar a la versión más reciente de Windows](https://support.microsoft.com/help/12373).

Notas sobre tarjetas de gráficos:

* Si la instalación de Windows Mixed Reality indica que la tarjeta gráfica no cumple los requisitos y cree que lo hace, asegúrese de que el casco esté conectado a la tarjeta correcta.
* Consulte con el fabricante de la tarjeta gráfica para obtener la actualización del controlador más reciente. Windows Mixed Reality requiere un controlador de tarjeta de gráficos que admita al menos WDDM 2,2.

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>Aparece un mensaje que indica que "ya está casi ahí — este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality".

Si recibe este mensaje, el equipo no cumple los requisitos mínimos necesarios para la mejor experiencia en Windows Mixed Reality. Es posible que el equipo pueda ejecutar un casco envolvente, pero es posible que no pueda ejecutar ciertas aplicaciones o que tenga problemas de rendimiento.

## <a name="my-xbox-controller-isnt-working"></a>El controlador Xbox no funciona.

Pruebe lo siguiente:

* Asegúrese de que el controlador esté encendido, totalmente cargado y conectado al equipo.
* Reemplace las baterías del controlador.
* Si usa un controlador de Bluetooth, vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** del equipo y asegúrese de que están emparejados (debe verlos en la página).

[Más información acerca de los controladores de Xbox](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>Mis controladores de movimiento no funcionan.
 
Pruebe lo siguiente:

* Asegúrese de que los controladores están encendidos y totalmente cargados.
* Reemplace las baterías de los controladores.
* Apague y encienda los controladores mientras los mantiene delante. Mantenga presionado el botón de Windows durante 4 segundos para desactivar un controlador y, a continuación, mantenga presionado el botón en 2 segundos para activarlo. 
* Vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** del equipo y asegúrese de que están emparejados (debe verlos en la página).

[Más información acerca de los controladores de movimiento](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Aparece un mensaje que dice "conectar los auriculares" aunque he enchufado los auriculares

Pruebe lo siguiente:

* Asegúrese de que el casco esté conectado a los puertos correctos del equipo. Debe estar conectado a la tarjeta de gráficos discretos del equipo y a un puerto USB 3,0. Aquí se indica cómo identificar los puertos correctos:
    * Los puertos USB 3,0 tienen un logotipo especial con una marca "SS" (que indica "SuperSpeed"). La pieza interior del puerto suele ser azul, mientras que los puertos USB 2,0 más antiguos suelen estar en blanco o negro en el interior.
    * Si el equipo tiene dos puertos HDMI, use el que se conecta a la tarjeta gráfica, no la placa base del equipo. No siempre es obvio qué es, aunque los puertos discretos se encuentran a menudo en una ranura de expansión del equipo. Si intenta un puerto y no funciona, pruebe el otro.
* Vaya al sitio web del fabricante del casco y actualice los controladores y el firmware del casco.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Obtengo un mensaje de error al intentar crear un límite.

Estas son algunas directrices para crear un límite:

* No se acerque demasiado a una pared u otro obstáculo.
* Asegúrese de mantener el casco en el alto de waist y mire hacia el equipo mientras realiza un seguimiento del límite.
* Asegúrese de que el sensor no esté bloqueado y de que haya suficiente luz.
* El espacio en el que se realiza el seguimiento debe ser mayor de 3 metros cuadrados.
* El espacio no debe ser demasiado grande o demasiado complicado, sino una forma geométrica simple sin muchos giros y vueltas.
* No vuelva a cruzar su propia ruta de acceso mientras realiza el seguimiento.
* Si se queda atascado en una esquina, empiece de nuevo.

**Si hago clic en "sentado y solo en posición", ¿qué tipo de experiencia tendré?**

"Sentado y solo con la posición" significa que usará los auriculares sin límite. Deberá permanecer en un solo lugar, ya que no tendrá ningún límite que le ayude a evitar obstáculos físicos. Además, algunas aplicaciones y juegos pueden estar diseñados para usarse con un límite, por lo que es posible que no funcionen según lo previsto.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>¿Cómo puedo obtener una vista más clara en el casco?

Intente ajustar el ajuste del casco. Ajuste su posición en su superficie moviéndola hacia arriba, hacia abajo o hacia la izquierda y a la derecha, y ajuste las correas para que se sientan perfectamente.

Si el casco lo admite, también puede ajustar la configuración de la calibración. Si el casco tiene un botón para ajustar la calibración, úselo. Si no es así, vaya a **configuración > realidad mixta > calidad visual** y ajuste la calibración allí. Para obtener más información sobre la calibración de un dispositivo específico, consulte con el fabricante del casco.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>¿Qué idiomas se admiten en Windows Mixed Reality?

Windows Mixed Reality está disponible en los idiomas siguientes. Si el equipo está configurado en un idioma diferente, puede seguir usando Windows Mixed Reality, pero la interfaz aparecerá en inglés (Estados Unidos), y los comandos de voz y el dictado no estarán disponibles.

* Chino simplificado (China)
* Inglés (Australia)
* Inglés (Canadá)
* Inglés (Gran Bretaña)
* Spanish (Traditional Sort) - Spain
* Francés (Canadá)
* Francés (Francia)
* Alemán (Alemania)
* Italiano (Italia)
* Japonés (Japón)
* Español (México)
* Español (España)

También puede usar el dictado en uno de los idiomas de Windows Mixed Reality admitidos enumerados anteriormente, simplemente seleccionar **micrófono**  en el teclado en pantalla.

Windows Mixed Reality también está disponible en los siguientes idiomas sin comandos de voz ni características de dictado:

* Chino tradicional (Taiwán y Hong Kong)
* Neerlandés (Países Bajos)
* Coreano (Corea)
* Ruso (Rusia)

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>Al conectar los auriculares, no sucede nada: el portal de realidad mixta no se abre.

Portal de realidad mixta, la aplicación que le guía a través de la configuración de Windows Mixed Reality, está diseñada para abrirse automáticamente cuando conecta un casco compatible. Si no se abre, vaya a **Inicio** y escriba **portal de realidad mixta** en el cuadro de **búsqueda**  para abrir la aplicación desde allí. Si no encuentra el portal de realidad mixta, es posible que deba [actualizar a la versión más reciente de Windows](https://support.microsoft.com/help/12373) o que el casco no esté correctamente conectado al equipo.

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer"></a>No puedo oír ningún sonido en el casco o el sonido se reproduce a través del equipo.

Si el casco envolvente no incluye auriculares integrados, deberá conectar los auriculares con el conector de audio del casco. (El conector suele encontrarse detrás del parasol o los lentes del casco; consulte con el fabricante del casco si tiene problemas para encontrarlo). 

Algunos auriculares de audio tienen botones físicos para controlar el volumen. Si el audio no funciona, compruebe si el volumen está desactivado o silenciado.

Windows Mixed Reality está diseñado para reproducir sonido a través de los auriculares inmersivo cuando está en su equipo y tiene auriculares conectados a él. Al desconectar o voltear el parasol, el audio cambiará al dispositivo de reproducción de Windows predeterminado. Puede cambiar esta configuración en **configuración > realidad mixta > audio y voz** .

> [!NOTE]
> * El audio espacial de realidad mixta de Windows funciona mejor con los auriculares incorporados o conectados directamente a los auriculares más inmersivo. Es posible que los altavoces o auriculares conectados al equipo no funcionen bien para el audio espacial.
> * Windows Mixed Reality no es compatible con los auriculares de audio Bluetooth.

## <a name="speech-commands-arent-working"></a>Los comandos de voz no funcionan.

Para usar comandos de voz, la configuración de idioma y voz del equipo debe establecerse en uno de los [idiomas](#what-languages-are-supported-in-windows-mixed-reality) admitidos en Windows Mixed Reality. Para comprobarlo, vaya a **configuración > time & language > Region & Language** and **Settings > Time & Language > Speech** .

Si el casco no tiene un micrófono integrado, deberá adjuntar auriculares con un micrófono al casco o a su PC. Para que la entrada de MIC cambie automáticamente al casco al desgaste, vaya a **configuración > realidad mixta > audio y voz** , y asegúrese de que, **cuando se use el casco, cambie al micrófono mic** está encendido.

Algunos auriculares de audio tienen un botón físico para silenciar y dessilenciar el micrófono. Si los comandos de voz no funcionan, compruebe si el MIC está silenciado.

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La pantalla del montaje del cabezal no funciona después de apagar y realizar un inicio rápido.

Pruebe esto:

* Desconecte el cable de la pantalla y el cable USB de la pantalla del montaje principal y vuelva a conectarlos.

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>Mi Wi-Fi se ralentiza cuando utilizo Windows Mixed Reality

Si usa una conexión Wi-Fi de 2,4 GHz, es posible que los controladores de movimiento ralenticen la red Wi-Fi. Pruebe una de las siguientes opciones:

* Cambie a una conexión Wi-Fi de 5 GHz, si hay alguna disponible. Más información
* Use un adaptador Bluetooth independiente para conectar sus controladores de movimiento al equipo. [Consulte los adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> Los auriculares más recientes se emparejan directamente con los controladores a través de un chip Bluetooth integrado y no deben experimentar este problema. 

## <a name="see-also"></a>Consulte también
* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)
* [Solución de problemas](troubleshooting-windows-mixed-reality.md)

