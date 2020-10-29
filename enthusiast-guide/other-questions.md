---
title: Otras preguntas
description: Solución avanzada de problemas de realidad mixta de Windows que va más allá de nuestra documentación de soporte técnico estándar para el consumidor.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, desinstalación de Windows Mixed Reality, idiomas admitidos
appliesto:
- Windows 10
ms.openlocfilehash: a8a035a4d113a0a53f41079709660f65bfa278a0
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692471"
---
# <a name="other-questions"></a>Otras preguntas

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>No se admite el controlador de gráficos (obtengo errores de controlador de gráficos).

Busque y ejecute "dxdiag":
1.  Si el resultado es "Rendering básico", el controlador de gráficos no está instalado. Para solucionar este error:
    * Vaya a **Device Manager > acción > buscar cambios de hardware** .
    * Use Windows Update para actualizar el controlador.
    * Si esto no soluciona el problema, vaya al sitio web del fabricante e instale la actualización del controlador más reciente. 
    * Si no hay ninguna actualización disponible para la GPU, es posible que WMR no sea compatible con el dispositivo. Si cree que debería ser, póngase en contacto [con el soporte técnico](https://support.microsoft.com).
2.  Si obtiene un "WDDM 2,1" o una versión anterior, el controlador de gráficos está instalado, pero es posible que no sea la versión más reciente. Para obtener la versión más reciente:
    * Use Windows Update para actualizar el controlador.
    * Si esa actualización no soluciona el problema, vaya al sitio web del fabricante e instale la actualización del controlador más reciente. 
    * Si no hay ninguna actualización disponible para la GPU, es posible que WMR no sea compatible con el dispositivo. Si cree que debería ser, póngase en contacto [con el soporte técnico](https://support.microsoft.com).
    
Si la instalación de Windows Mixed Reality indica que la tarjeta gráfica no cumple los requisitos y cree que lo hace, asegúrese de que el casco esté conectado a la tarjeta correcta.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>La actualización de firmware de Samsung Odyssey o Odyssey + auriculares está bloqueada.

Samsung posee y publica las actualizaciones de firmware de los auriculares que se entregan a través de las aplicaciones complementarias "Samsung HMD Odyssey Setup" y "Samsung HMD Odyssey + Setup". Para obtener más detalles y obtener ayuda con los problemas de actualización de firmware de Samsung, póngase en contacto con el servicio de atención al cliente de Samsung.

Si el proceso de actualización de firmware se está bloqueando y no ha habido ningún progreso durante más de cinco minutos:
* Desconecte temporalmente todos los demás dispositivos USB y vuelva a intentar la actualización del firmware.
* Conecte sus auriculares Samsung a otro puerto USB 3,0 en su PC.
* Deshabilite o desinstale cualquier software instalado que pueda interferir con las actualizaciones de firmware, como App Center AORUS de Gigabyte.
* Use otro equipo para realizar la actualización de firmware de auriculares de Samsung.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Cómo tener acceso al escritorio de mi PC en la realidad mixta
Inicie la aplicación de escritorio en el botón auriculares desde **Windows > todas las aplicaciones > Desktop** para tener acceso al escritorio de su PC en realidad mixta.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>¿Cómo puedo ver varios monitores en realidad mixta?
De forma predeterminada, la aplicación de escritorio cambia automáticamente para mostrar el monitor con el foco. Si desea ver todos los monitores en realidad mixta: 
* Haga clic en el icono de monitor en la esquina superior izquierda de la aplicación.
* Deshabilitar "cambiar automáticamente el monitor".
* Elija el monitor que desea ver.
* Inicie otra instancia de la aplicación de escritorio.
* Elija el monitor que desea ver en la instancia.
* Repita el procedimiento para todos los monitores físicos.
Tenga en cuenta que tendrá que volver a seleccionar el monitor para que se muestre en cada aplicación de escritorio cada vez que reinicie la realidad mixta. 

## <a name="my-desktop-app-only-shows-a-black-screen"></a>La aplicación de escritorio solo muestra una pantalla en negro.
Si su equipo tiene una GPU híbrida de NVIDIA, el problema puede deberse al dispositivo NVIDIA que ejecuta el runtimebroker.exe en la GPU discreta en lugar de la integrada. Para corregir este problema, siga estas instrucciones en "[Cómo crear la configuración de Optimus para un nuevo programa?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)". para agregar C:\windows\system32\runtimebroker.exe y forzarlo a que se ejecute en el procesador de "gráficos integrados". 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Mi Wi-Fi se ralentiza cuando utilizo Windows Mixed Reality.

Si usa una conexión Wi-Fi de 2,4 GHz, los controladores de movimiento pueden ralentizar la red Wi-Fi. Pruebe una de las siguientes opciones:
* Cambie a una conexión Wi-Fi de 5 GHz, si hay alguna disponible. [Más información](https://support.microsoft.com/en-us/help/4000461).
* Use un adaptador Bluetooth independiente para conectar sus controladores de movimiento al equipo. Consulte [adaptadores recomendados](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Aparece un mensaje que indica que se ha incorporado el equipo. ¿Por qué?

Si usa un equipo portátil, Windows Mixed Reality funciona mejor cuando el equipo está totalmente cargado y conectado. 

## <a name="what-is-the-experience-options-setting"></a>¿Cuál es la configuración de opciones de experiencia?

Esta opción de configuración ( **configuración > la realidad mixta > las opciones de experiencia > experiencia** ) permite cambiar la configuración de rendimiento de Windows Mixed Reality. Esto le permite elegir la mejor experiencia para la configuración de hardware en una amplia variedad de contenido. Estas son las opciones:
* Automático: Windows Mixed Reality determinará la mejor experiencia para la configuración de hardware. Para la mayoría de los usuarios, esta es la mejor opción para empezar.
* 60Hz: establece la frecuencia de actualización en 60 Hz y desactiva ciertas características, como captura de vídeo y vista previa en el portal de realidad mixta.
* 90Hz: establece la frecuencia de actualización en 90Hz.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>¿Qué idiomas se admiten en Windows Mixed Reality?

Windows Mixed Reality está disponible en los idiomas siguientes:
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

Puede usar Windows Mixed Reality si el equipo está configurado en un idioma diferente, pero la interfaz aparecerá en inglés (Estados Unidos), y los comandos de voz y el dictado no estarán disponibles. El teclado Windows Mixed Reality en pantalla solo es inglés (Estados Unidos). Para escribir texto en otro idioma, use un teclado físico conectado a su PC. También puede usar dictado en uno de los idiomas admitidos de Windows Mixed Reality enumerados anteriormente, simplemente seleccionar micrófono en el teclado en pantalla.

Windows Mixed Reality también está disponible en los siguientes idiomas sin comandos de voz ni características de dictado:
* Chino tradicional (Taiwán y Hong Kong)
* Neerlandés (Países Bajos)
* Coreano (Corea)
* Ruso (Rusia)

## <a name="i-have-questions-about-my-headset-hardware"></a>Tengo preguntas sobre el hardware de auriculares.

Para obtener más información sobre el casco, consulte con el fabricante. Puede haber una guía de producto en el cuadro o puede probar el sitio web del fabricante.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Cómo desinstalar Windows Mixed Reality

1. Desconecte el casco del equipo.
2. Cierre el portal de Windows Mixed Reality.
2. Vaya a  **inicio > configuración > realidad mixta** y seleccione "desinstalar".

Cuando esté listo para empezar a usar el casco de nuevo, conéctelo y el portal de Windows Mixed Reality le guiará a través del programa de instalación.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Aparece el mensaje "no se pudo finalizar la desinstalación de Windows Mixed Reality".

Es posible que algunos archivos, incluida la información sobre su entorno, sigan estando en el equipo. Esto puede causar problemas si decide volver a instalar Windows Mixed Reality más tarde. Puede quitar manualmente cualquier información restante de Windows Mixed Reality del equipo modificando el registro y usando Windows PowerShell para ejecutar comandos. _Si modifica el registro de forma incorrecta, pueden producirse problemas graves. Asegúrese de seguir estos pasos con cuidado. Para una mayor protección, haga una copia de seguridad del registro antes de modificarlo para poder restaurarlo en caso de que se produzcan problemas._ Para obtener más información, vea [Cómo realizar una copia de seguridad del registro y volver a narrarlo en Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Para desinstalar Windows Mixed Reality con estos comandos:
1. Reinicia tu equipo.
2. En el cuadro de **búsqueda** , escriba "regedit" y, a continuación, seleccione "sí".
3. Quite estos valores del registro:
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>y, a continuación, elimine "FirstRunSucceeded".</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\speechandaudio</b>, elimine "PreferDesktopSpeaker" y "PreferDesktopMic".</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b>y, a continuación, elimine "DisableSpeechInput". Nota: los elementos del registro en HHKEY_CURRENT_USER deben eliminarse para cada cuenta de usuario del equipo que haya usado Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>, elimine "DeviceID" y "MODE".</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>y, a continuación, elimine "OnDeviceLearningCompleted".</li> 
   </ul>
4. Quite las claves del registro siguientes: <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. Cierre el editor del registro.
6. Vaya a **C:\Users\nombre name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** y elimine "RoomBounds.jsen". Repita este paso para cada usuario que haya usado Windows Mixed Reality.
7. Abra el símbolo del sistema de administrador y vaya a **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** . Elimine el contenido de la carpeta "HeadTracking Data" (pero no la carpeta).
8. Escriba "PowerShell" en el cuadro de búsqueda, haga clic con el botón derecho en "Windows PowerShell" y seleccione "ejecutar como administrador".
9. En Windows PowerShell: <ul>
   <li>En el símbolo del sistema, copie y pegue <b>DISM/online/Get-Capabilities</b>y, a continuación, presione Entrar.</b></li> 
   <li>Copie la identidad de capacidad que comienza con analógico. Holographic. Desktop (si no está allí, significa que este elemento no está instalado. En ese caso, vaya al paso 10).</li> 
   <li>Copie y pegue el siguiente símbolo del sistema y, a continuación, presione ENTRAR: <b>DISM/online/Remove-Capability/CapabilityName: la identidad de la capacidad copiada en el último paso</b></li>
   </ul>
10. Reinicie el equipo.

