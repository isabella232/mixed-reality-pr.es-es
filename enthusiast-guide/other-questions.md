---
title: Preguntas más frecuentes sobre hardware inmersivo realted
description: Sugerencias Windows Mixed Reality solución de problemas adicionales que van más allá de nuestra documentación estándar de soporte técnico al consumidor.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Uninstalling Windows Mixed Reality, Supported Languages
appliesto:
- Windows 10
ms.openlocfilehash: ede2620ca6a47b085a3d7b54fd6df073bfaa528e
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196600"
---
# <a name="other-questions"></a>Otras preguntas

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>No se admite el controlador de gráficos (obtendro errores de controlador de gráficos).

Busque y ejecute "dxdiag":

1.  Si el resultado es "Representador básico", el controlador de gráficos no está instalado. Para solucionar este error:
    * Vaya a Administrador de dispositivos > Action > Scan for Hardware Changes (Buscar **cambios de hardware).**
    * Use Windows Update para actualizar el controlador.
    * Si esto no soluciona el problema, vaya al sitio web del fabricante e instale la actualización del controlador más reciente. 
    * Si no hay ninguna actualización disponible para la GPU, es posible que WMR no sea compatible con el dispositivo. Si cree que debe ser así, póngase en contacto con el [soporte técnico.](https://support.microsoft.com)
2.  Si obtiene una versión "WDDM 2.1" o una versión anterior, el controlador de gráficos está instalado, pero es posible que no sea la versión más reciente. Para obtener la versión más reciente:
    * Use Windows Update para actualizar el controlador.
    * Si esa actualización no corrige el problema, vaya al sitio web del fabricante e instale la actualización del controlador más reciente. 
    * Si no hay ninguna actualización disponible para la GPU, es posible que WMR no sea compatible con el dispositivo. Si cree que debe ser así, póngase en contacto con el [soporte técnico.](https://support.microsoft.com)

Si Windows Mixed Reality configuración indica que la tarjeta gráfica no cumple los requisitos y cree que sí, asegúrese de que el casco está conectado a la tarjeta correcta.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>La actualización del firmware del casco Samsung Samsung Samsung+ está bloqueada.

Samsung posee y publica las actualizaciones de firmware de los cascos que se entregan a través de sus aplicaciones complementarias de dispositivo "Samsung HMD Setup" y "Samsung HMD Ctrl+Setup". Para obtener más detalles y ayuda con los problemas de actualización de firmware de Samsung, póngase en contacto con el servicio de atención al cliente de Samsung.

Si el proceso de actualización del firmware se está atascando y no ha habido ningún progreso durante más de cinco minutos:

* Desconecte temporalmente todos los demás dispositivos USB y vuelva a intentar la actualización del firmware.
* Conecte los cascos Samsung a un puerto USB 3.0 diferente en el equipo.
* Deshabilite o desinstale cualquier software instalado que pueda interferir con las actualizaciones de firmware, como AORUS de Gigabyte App Center.
* Use otro equipo para actualizar el firmware de los cascos Samsung.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Cómo acceder a mi equipo de escritorio en realidad mixta?
Inicie la aplicación de escritorio en el casco desde **Windows Button > Todas** las aplicaciones > Desktop para acceder al escritorio del equipo en realidad mixta.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>¿Cómo puedo ver varios monitores en Mixed Reality

De forma predeterminada, la aplicación de escritorio cambia automáticamente para mostrar el monitor con el foco. Si desea ver todos los monitores en realidad mixta:

* Seleccione el icono de monitor en la esquina superior izquierda de la aplicación.
* Deshabilite "Monitor de cambio automático".
* Elija el monitor que desea ver.
* Inicie otra instancia de la aplicación de escritorio.
* Elija el monitor que desea ver en esa instancia.
* Repita con todos los monitores físicos.
Tendrá que volver a seleccionar el monitor para mostrarlo en cada aplicación de escritorio cada vez que reinicie la realidad mixta.

## <a name="my-desktop-app-only-shows-a-black-screen"></a>Mi aplicación de escritorio solo muestra una pantalla negra

Si el equipo tiene una GPU híbrida de Nvidia, el dispositivo Nvidia que ejecuta el runtimebroker.exe en la GPU discreta en lugar de en la integrada puede ser el responsable. Para corregir este problema, siga estas instrucciones en["Cómo create Optimus settings for a new program?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)(¿Crear una configuración óptima para un nuevo programa?) " para agregar C:\windows\system32\runtimebroker.exe y forzar que se ejecute en el procesador "Gráficos integrados". 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Mi Wi-Fi se ralentiza cuando uso Windows Mixed Reality.

Si usa una conexión de 2,4 GHz Wi-Fi, los controladores de movimiento podrían ralentizar la red Wi-Fi:

* Cambie a una conexión de Wi-Fi de 5 GHz, si hay una disponible. [Más información](https://support.microsoft.com/help/4000461).
* Use un adaptador Bluetooth independiente para conectar los controladores de movimiento al equipo. Consulte los [adaptadores recomendados.](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>He recibido un mensaje que dice que debo conectarme y cargar mi PC. ¿Por qué?

Si usa un equipo portátil, Windows Mixed Reality funciona mejor cuando el equipo está totalmente cargado y conectado.

## <a name="what-is-the-experience-options-setting"></a>¿Cuál es la configuración de opciones de experiencia?

**La > Mixed Reality > Headset display > Experience le** permite cambiar la configuración de rendimiento Windows Mixed Reality Mixed Reality. Esto le permite elegir la mejor experiencia para la configuración de hardware en una variedad de contenido. Tiene tres opciones de experiencia entre las que elegir:
* Automático: Windows Mixed Reality determinará la mejor experiencia para la configuración de hardware. Para la mayoría de las personas, esta es la mejor opción para empezar.
* 60 Hz: establece la frecuencia de actualización en 60 Hz y desactiva determinadas características, como la captura de vídeo y la vista previa en Portal de realidad mixta.
* 90 Hz: establece la frecuencia de actualización en 90 Hz.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>¿Qué idiomas se admiten en Windows Mixed Reality

Windows Mixed Reality está disponible en los siguientes idiomas:

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

Puede usar Windows Mixed Reality si el equipo está establecido en un idioma diferente. Sin embargo, la interfaz aparecerá en inglés (Estados Unidos), y los comandos de voz y dictado no estarán disponibles. El Windows Mixed Reality en pantalla es solo inglés (Estados Unidos). Para escribir texto en otro idioma, use un teclado físico conectado al equipo. También puede usar el dictado en uno de los idiomas admitidos Windows Mixed Reality mencionados anteriormente: solo tiene que seleccionar el micrófono en el teclado en pantalla.

Windows Mixed Reality también está disponible en los siguientes idiomas sin comandos de voz ni características de dictado:
* Chino tradicional (Taiwán y Hong Kong)
* Neerlandés (Países Bajos)
* Coreano (Corea)
* Ruso (Rusia)

## <a name="i-have-questions-about-my-headset-hardware"></a>Tengo preguntas sobre el hardware del casco.

Para más información sobre el casco, consulte con el fabricante. Puede haber una guía de producto en el cuadro o puede probar el sitio web del fabricante.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Cómo desinstalar Windows Mixed Reality?

1. Desconecte el casco del equipo.
2. Cierre Windows Mixed Reality Portal.
2. Vaya a  **Inicio > configuración > Mixed Reality** seleccione "Desinstalar".

Cuando esté listo para empezar a usar el casco de nuevo, conéctelo y Windows Mixed Reality Portal le llevará a través de la configuración.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>He recibido el mensaje "No hemos podido finalizar la desinstalación Windows Mixed Reality".

Algunos archivos, incluida la información sobre su entorno, pueden seguir estando en el equipo. Esto puede causar problemas si decide volver a instalar Windows Mixed Reality más adelante. Puede quitar manualmente cualquier información de Windows Mixed Reality restante del equipo modificando el Registro y usando Windows PowerShell para ejecutar comandos. _Si modifica incorrectamente el registro, pueden producirse problemas graves. Asegúrese de seguir estos pasos con cuidado. Para mayor protección, haga una copia de seguridad del registro antes de modificarlo para poder restaurarlo si se produce un problema._ Para obtener más información, [vea Copia de seguridad y restauración del Registro en Windows.](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows) 

Para desinstalar La realidad mixta de Windows mediante estos comandos:
1. Reinicia tu equipo.
2. En el **cuadro** Buscar, escriba "regedit" y seleccione "Sí".
3. Quite estos valores del Registro:
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, elimine "FirstRunSucceeded".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, elimine "PreferDesktopSpeaker" y "PreferDesktopMic".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>y, a continuación, elimine "DisableSpeechInput". Nota: Los elementos del Registro HHKEY_CURRENT_USER deben eliminarse para cada cuenta de usuario del equipo que haya usado Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, elimine "DeviceID" y "Mode".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, elimine "OnDeviceLearningCompleted".</li> 
   </ul>
4. Quite las siguientes claves del Registro: <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. Cierre el Editor del Registro.
6. Vaya a **C:\Users\user name\AppData\Local\Packages\Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy\LocalState** y elimine "RoomBounds.json". Repita esta acción para cada usuario que haya usado Windows Mixed Reality.
7. Abra el símbolo del sistema de administración y vaya a **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors**. Elimine el contenido de la carpeta "Datos de HeadTracking" (pero no la propia carpeta).
8. Escriba "powershell" en el "cuadro de búsqueda", haga clic con el botón derecho en "Windows PowerShell" y seleccione "Ejecutar como administrador".
9. En Windows PowerShell: <ul>
   <li>En el símbolo del sistema, copie y pegue <b>Dism /online /Get-Capabilities</b>y presione Entrar.</b></li> 
   <li>Copie la identidad de funcionalidad que comienza por Analog.Holographic.Desktop. Si no está ahí, el elemento no está instalado y puede ir directamente al paso 10).</li> 
   <li>Copie y pegue el siguiente símbolo del sistema y presione Entrar: <b>Dism /online /Remove-Capability /CapabilityName: la identidad</b> de funcionalidad copiada en el último paso</li>
   </ul>
10. Reinicie el equipo.

