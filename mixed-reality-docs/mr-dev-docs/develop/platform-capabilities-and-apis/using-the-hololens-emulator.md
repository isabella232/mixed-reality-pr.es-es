---
title: Uso del emulador de HoloLens
description: Obtenga información sobre el uso del emulador de HoloLens para probar aplicaciones de realidad mixta en el equipo sin un dispositivo HoloLens físico.
author: hamalawi
ms.author: moelhama
ms.date: 09/15/2021
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, emulator
ms.openlocfilehash: 815bae1235dce992277f68a078b3f4dd1e73a21d
ms.sourcegitcommit: 7dad5bde71d429bb23c72a4074e60b6668a7f091
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/16/2021
ms.locfileid: "127857544"
---
# <a name="using-the-hololens-emulator"></a>Uso del emulador de HoloLens

El emulador de HoloLens le permite probar aplicaciones holográficas en el equipo sin un dispositivo HoloLens físico e incluye el conjunto de herramientas de desarrollo de HoloLens. El emulador usa una máquina virtual de Hyper-V, lo que significa que los sensores de HoloLens leen las entradas humanas y del entorno desde el teclado, el mouse o el mando de Xbox. Ni siquiera es necesario modificar los proyectos para que se ejecuten en el emulador, ya que la aplicación no sabe que no se está ejecutando en un dispositivo HoloLens real.

Si buscas desarrollar aplicaciones para cascos envolventes (VR) de Windows Mixed Reality o juegos para PC de escritorio, consulta [Simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), que te permite simular cascos de escritorio.

## <a name="hololens-2-emulator-overview"></a>Introducción al emulador de HoloLens 2

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/HoloLens-2-Emulator-Overview/player?format=ny]

## <a name="installing-the-hololens-emulator"></a>Instalación del emulador de HoloLens
Descargue el emulador HoloLens.

Versiones:
* [Emulador de HoloLens 2 (Windows Holographic, versión 21H1, actualización de septiembre de 2021)](https://go.microsoft.com/fwlink/?linkid=2172762).
* [Emulador de HoloLens (primera generación) y plantillas de proyecto holográficas](https://go.microsoft.com/fwlink/?linkid=2065980).

Puedes encontrar notas de la versión y compilaciones anteriores del emulador de HoloLens en la página [Archivo del emulador de HoloLens](hololens-emulator-archive.md).

### <a name="hololens-emulator-system-requirements"></a>Requisitos del sistema del emulador de HoloLens

El emulador de HoloLens usa Hyper-V con RemoteFx (emulador de primera generación) o GPU-PV (emulador de HoloLens 2) para los gráficos acelerados mediante hardware. Para usar el emulador, asegúrate de que tu PC cumple los siguientes requisitos de hardware:
* Windows 10 Pro, Enterprise o Education de 64 bits
    >[!NOTE]
    >La edición Windows 10 Home no admite Hyper-V ni el emulador de HoloLens.  
    >El emulador de HoloLens 2 requiere la actualización de octubre de 2018 de Windows 10 u otra posterior.
* CPU de 64 bits
* CPU con cuatro núcleos (o varias CPU con un total de cuatro núcleos)
* 8 GB de RAM o más
* En el BIOS, las características siguientes deben estar [admitidas y habilitadas](/archive/blogs/iftekhar/enable-hardware-settings-in-bios-to-run-hyper-v):
   * Virtualización asistida por hardware
   * Traducción de direcciones de segundo nivel (SLAT)
   * Prevención de ejecución de datos (DEP) basada en hardware
* Requisitos de GPU
   * DirectX 11.0 o versiones posteriores
   * Controlador de gráficos WDDM 1.2 o posterior (primera generación)
   * Controlador de gráficos WDDM 2.5 (emulador de HoloLens 2)
   * El emulador puede funcionar con una GPU no admitida, pero será bastante más lento.

Si el sistema cumple los requisitos mencionados anteriormente, **asegúrese de que se ha habilitado la característica "Hyper-V" en el sistema**. Vaya a **Panel de control -> Programas -> Programas y características -> Activar o desactivar características de Windows** y asegúrese de que **Hyper-V** está seleccionado.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Implementación de aplicaciones en el emulador de HoloLens

1. Carga la solución de aplicación en Visual Studio.
    >[!NOTE]
    >Al usar Unity, compila el proyecto desde Unity y, luego, carga la solución compilada en Visual Studio como de costumbre.
2. Para el emulador de HoloLens (primera generación), asegúrese de que la plataforma esté establecida en **x86**. Para el emulador de HoloLens 2, asegúrate de que la plataforma esté establecida en **x86** o **x64**.
3. Seleccione la versión de **emulador de HoloLens** que quiera como dispositivo de destino para la depuración.
4. Dirígete a **Depurar > Iniciar depuración** o presiona **F5** para iniciar el emulador e implementar la aplicación para la depuración.

El emulador puede tardar un minuto o más en arrancar la primera vez que se inicia. Se recomienda mantener el emulador abierto durante la sesión de depuración para poder implementar rápidamente en él las aplicaciones.

## <a name="basic-emulator-input"></a>Entrada básica del emulador

Controlar el emulador es muy parecido a muchos videojuegos 3D comunes. Hay opciones de entrada disponibles para usar el teclado, el mouse o el mando de Xbox. Para controlar el emulador, se dirigen las acciones de un usuario simulado que lleva un dispositivo HoloLens. Tus acciones desplazan el usuario simulado por el entorno. Las aplicaciones que se ejecutan en el emulador responden como lo harían en un dispositivo real.

El cursor en HoloLens (primera generación) sigue el movimiento y el giro de la cabeza. En el emulador de HoloLens 2, el cursor sigue el movimiento y la orientación de las manos.

* **Andar hacia delante, hacia atrás, a la izquierda y a la derecha**: usa las teclas W, A, S y D del teclado o el stick izquierdo en un mando de Xbox.
* **Mirar hacia arriba, hacia abajo, a la izquierda y a la derecha**: haga clic y arrastre el mouse, use las teclas de dirección del teclado o el stick derecho en un mando de Xbox.
* **Gesto de pulsación en el aire**: haz clic con el botón derecho del mouse, presiona la tecla Entrar en el teclado o usa el botón A en un mando de Xbox.
* **Gesto de eclosionar/sistema**: presiona la tecla de Windows o la tecla F2 del teclado, o bien el botón B en un mando de Xbox.
* **Movimiento de mano para el desplazamiento**: mantenga presionada la tecla Alt y el botón derecho del mouse de forma simultánea y arrastre el mouse hacia arriba o hacia abajo. Si usa un mando de Xbox, mantenga presionado el gatillo derecho y el botón A, y mueva el stick derecho hacia arriba y hacia abajo.
* **Movimiento y orientación de las manos** (solo el emulador de HoloLens 2): mantenga presionada la tecla Alt y arrastre el mouse hacia arriba, hacia abajo, a la izquierda o a la derecha para mover la mano. También puede usar las teclas de dirección y Q o E para girar e inclinar la mano. En un mando de Xbox, mantenga presionado el botón superior izquierdo o derecho y use la palanca de mando izquierda para mover la mano a la izquierda, a la derecha, hacia delante y hacia atrás; igualmente, use la palanca de mando derecha para girarla. Mueva el DPad hacia arriba o hacia abajo para subir o bajar la mano.

¿Tienes un casco envolvente de Windows Mixed Reality?  A partir del emulador de HoloLens 2 (Windows Holographic, versión 2004), puedes usar el casco envolvente y los controladores de movimiento de Windows Mixed Reality para controlar el emulador de HoloLens 2 y verlo en modo estereoscópico.  Consulta [Uso de un casco envolvente y controladores de movimiento de Windows Mixed Reality con el emulador de HoloLens 2](#using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator).

## <a name="anatomy-of-the-hololens-2-emulator"></a>Anatomía del emulador de HoloLens 2

### <a name="main-window"></a>Ventana principal

![Ventana principal del emulador de HoloLens 2](images/emulator2-900px.png)

### <a name="toolbar"></a>Barra de herramientas

A la derecha de la ventana principal, se encuentra la barra de herramientas del emulador. La barra de herramientas contiene los siguientes botones:
* ![Icono Cerrar](images/emulator-close.png) **Cerrar**: cierra el emulador.
* ![Icono Minimizar](images/emulator-minimize.png) **Minimizar**: minimiza la ventana del emulador.
* ![Icono Simulación](images/emulator-simulation-panel.png) **Panel de control de simulación**: muestra u oculta el [panel de control de simulación](#simulation-control-panel) para configurar y controlar la [entrada al emulador](#basic-emulator-input).
* ![Icono Ajustar a la pantalla](images/emulator-fit.png) **Ajustar a la pantalla**: ajusta el emulador a la pantalla.
* ![Icono Zoom](images/emulator-zoom.png) **Zoom**: aumenta o reduce el emulador.
* ![Icono Ayuda](images/emulator-help.png) **Ayuda**: Abra la ayuda de los emuladores.
* ![Icono Open device portal](images/emulator-deviceportal.png) (Abrir portal de dispositivos) **Open Device Portal** (Abrir portal de dispositivos): abre el Portal de dispositivos Windows correspondiente al sistema operativo de HoloLens en el emulador.
* ![Icono Herramientas](images/emulator-tools.png) **Herramientas**: abre el panel **Herramientas adicionales**.

### <a name="simulation-control-panel"></a>Panel de control de simulación

El panel de control Simulación permite ver la posición y la orientación actuales del ser humano y los dispositivos de entrada simulados. También permite configurar la entrada simulada, como mostrar u ocultar una o ambas manos, y los dispositivos usados para controlar la entrada simulada, como el teclado o el mouse del equipo o el controlador para juegos.

![Panel de control de simulación](images/emulator-simulation-control-panel.png)

* Para mostrar u ocultar el panel de simulación, haga clic en el botón de la barra de herramientas o presione F7 en el teclado.
* Mantenga el puntero del mouse sobre un control o un campo para mostrar información sobre los controles del teclado, el mouse y el controlador para juegos de dicho control o campo.
* Para mostrar u ocultar una mano, activa o desactiva el conmutador adecuado de mano izquierda o mano derecha.
* Para controlar la mano, usa la tecla Alt izquierda o derecha del teclado o el gatillo izquierdo o derecho del controlador para juegos.
* Para dirigir toda la entrada a una o ambas manos, seleccione el botón de marcador en el conmutador de alternancia, que es lo mismo que mantener presionada la tecla Alt con la mano.
* Para controlar la dirección de la mirada, seleccione el marcador en la sección Ojos, que es lo mismo que mantener presionada la tecla Y del teclado.
* Para cargar una grabación de habitación, haga clic en el botón Cargar en la sección Grabación. Para más información, consulta [Habitaciones simuladas](#simulated-rooms).
* Para ajustar la velocidad a la que el humano o los dispositivos de entrada simulados se moverán o girarán en respuesta a una entrada del teclado, mouse o controlador para juegos, haga clic en el icono con forma de engranaje junto a Configuración de entrada y ajuste los controles deslizantes.
* De forma predeterminada, la entrada del teclado controla el humano simulado y la entrada simulada. Para que la entrada del teclado del equipo se envíe a HoloLens, desactiva la opción "Use keyboard for simulation" (Usar el teclado para la simulación). F4 es la tecla de método abreviado para esta configuración.
* Si el panel de simulación ya está visible, al presionar F8 el foco del teclado se moverá a este.
* Para desacoplar el panel de simulación de la ventana del emulador, haga clic en el botón de la parte inferior del panel o presione F9 en el teclado.  Al cerrar la ventana o presionar de nuevo F9, se vuelve a la ventana del emulador.
* El panel de control de simulación se puede iniciar como una aplicación independiente, que permite conectarse al emulador de HoloLens 2, un dispositivo de HoloLens 2 o una simulación de Windows Mixed Reality, y controlarlos, mediante la ejecución de PerceptionSimulationInput.exe desde %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\.

### <a name="account-tab"></a>Pestaña Cuenta

La pestaña Cuenta permite configurar el emulador para iniciar sesión con una cuenta Microsoft. Es útil para probar las API que requieren que el inicio de sesión del usuario se realice con una cuenta. Para activar o desactivar esta opción, es necesario cerrar completamente y reiniciar el emulador de HoloLens para que la configuración surta efecto. Si esta opción está habilitada, en los siguientes inicios del emulador se le solicitará que inicie sesión, igual que cuando un usuario inicia por primera vez HoloLens. Para escribir las credenciales con el teclado del equipo, primero desactiva "Use keyboard for simulation" (Usar el teclado para la simulación) en el panel de control de simulación o presiona F4 en el teclado para activar o desactivar la configuración de teclado.

### <a name="optional-settings-tab"></a>Pestaña Configuración opcional

En la pestaña Configuración opcional se muestra un control para habilitar o deshabilitar los gráficos acelerados de hardware. Los gráficos acelerados de hardware se usan de forma predeterminada, si son compatibles con el controlador del adaptador de gráficos del equipo. Si el controlador del adaptador de gráficos no es compatible con GPU-PV, esta opción no estará visible.

### <a name="diagnostics-tab"></a>Pestaña Diagnóstico

La pestaña Diagnostics (Diagnóstico) muestra la dirección IP del emulador en forma de un vínculo al Portal de dispositivos Windows junto con el estado de la GPU virtual.

### <a name="network-tab"></a>Pestaña Red

En la pestaña Red se muestran los detalles del adaptador de red para el emulador, así como los detalles del adaptador de red para el equipo host. En cuanto al emulador de HoloLens 2, esta pestaña solo aparecerá al ejecutar el emulador en la Actualización de mayo de 2019 de Windows 10 o en una versión más reciente.

### <a name="nat-configuration-tab"></a>Pestaña Configuración de NAT

Esta pestaña solo aparecerá al ejecutar el emulador en la Actualización de mayo de 2019 de Windows 10 o en una versión más reciente.

El emulador usa la conexión de red de tu PC y se asienta detrás de un NAT.  Esta pestaña te permite asignar puertos de tu PC host al emulador, lo que posibilita que dispositivos remotos se conecten a aplicaciones y servicios que se ejecutan en el emulador.

Por ejemplo, si quieres acceder al Portal de dispositivos del emulador desde un equipo remoto:

1. Agrega una entrada para el puerto 80 interno (el puerto en el que el Portal de dispositivos escucha) haciendo doble clic en una fila vacía de la tabla.  Para otras aplicaciones, escribe el número de puerto en el que la aplicación escucha.
2. Elige cualquier puerto externo disponible.  En este ejemplo, usaremos el puerto 8080 como puerto externo.
3. Selecciona el protocolo.  El valor predeterminado es TCP.  Dado que el Portal de dispositivos usa TCP, dejaremos el valor predeterminado.
4. Haz clic en "Aplicar cambios" para habilitar la asignación.  "Estado" cambiará de "Pendiente" a "Activo".
5. En el equipo remoto, abre un explorador y navega a (IP del equipo que ejecuta el emulador): 8080.  Aparecerá la interfaz del Portal de dispositivos.  La dirección IP que use en un equipo remoto debe ser la dirección IP del equipo en el que se ejecuta el emulador, no la del propio emulador.  Puedes recuperar la dirección IP a través de varios medios, como la aplicación de configuración del equipo en la categoría "Redes e Internet", "ipconfig" desde un símbolo del sistema y desde la pestaña Red del cuadro de diálogo de herramientas del emulador si buscas la entrada del adaptador de escritorio.

Ten en cuenta también que, si agregas una asignación de puerto para el Portal de dispositivos, puedes controlar el emulador de forma remota mediante la herramienta de control de simulación de percepción incluida en la instalación del emulador o con las API de simulación de percepción conectándote a la dirección IP del equipo host y el puerto externo del Portal de dispositivos, como 8080 en el ejemplo anterior.  Al usar el control de simulación de percepción para conectarte y controlar el emulador de forma remota, especifica solo la dirección IP del equipo y el puerto configurado.  No incluya "https://".

No hay asignaciones de puerto predeterminadas.  Las asignaciones que configures serán persistentes entre inicios del emulador de HoloLens 2 y se habilitarán automáticamente cuando el emulador se haya arrancado por completo.

Usa el botón "Exportar" para guardar las asignaciones en un archivo.  Después, puedes compartir este archivo con otros miembros del equipo que pueden usar el botón "Importar" para configurar automáticamente las mismas asignaciones.

![Pestaña "Configuración de NAT" del emulador de HoloLens](images/emulator-natconfig-500px.png)

### <a name="updates-tab"></a>Pestaña Actualizaciones

Esta pestaña solo aparecerá al ejecutar el emulador en la Actualización de mayo de 2019 de Windows 10 o en una versión más reciente.

En el inicio, el emulador comprobará si hay nuevas versiones.  Si está disponible una nueva versión, el emulador mostrará un mensaje que indicará la versión que tienes, junto con la versión disponible y preguntará si quieres actualizarla.  Si seleccionas "Sí", se descargará el instalador de la nueva versión.

La pestaña Actualizaciones te permite controlar si el emulador debe comprobar o no las nuevas versiones activando la casilla "Buscar actualizaciones automáticamente" en esta pestaña.  También te permite ver y descargar otras versiones del emulador disponibles, a partir de la actualización de septiembre de 2019.  En el caso de versiones distintas de la que se está ejecutando actualmente, se proporciona un vínculo de descarga.  Al hacer clic en este vínculo, se descargará el instalador de esa versión.

![Pestaña "Actualizaciones" del emulador de HoloLens](images/emulator-updates-500px.png)

### <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Uso de un casco envolvente y controladores de movimiento de Windows Mixed Reality con el emulador de HoloLens 2

A partir del emulador de HoloLens 2 (Windows Holographic, versión 2004), puedes usar los controladores de movimiento y el casco de Windows Mixed Reality para ver el emulador de HoloLens 2 en modo estereoscópico e interactuar con él.  Esto te permite realizar movimientos más rápidos y naturales con la cabeza y las manos sin un dispositivo HoloLens 2.  Recuerde que esto no reemplaza por completo a un dispositivo HoloLens 2, sino que tiene como objetivo proporcionar una experiencia mejorada que vaya más allá de la simple interacción con el emulador mediante el teclado, el mouse y el controlador para juegos en una ventana de escritorio 2D.  Para habilitar esta característica, haz lo siguiente:

1. Asegúrate de que Windows Mixed Reality esté configurado en el equipo y de que el casco envolvente de Windows Mixed Reality esté conectado.
2. Inicia el emulador de HoloLens 2.
3. Haz clic en el botón de la barra de herramientas o presiona F7 para abrir el panel de simulación.
4. Desplázate hasta la parte inferior del panel.
5. Activa la casilla con la etiqueta "Use HMD for simulation" (Usar HMD para la simulación).
6. Se iniciará Windows Mixed Reality y la pantalla del emulador cambiará ligeramente.  Si no tienes ningún casco, el emulador coloca ambos ojos en el centro de la cabeza y muestra un solo ojo.  Con un casco, el emulador genera una salida estereoscópica real, pero solo representa la vista de un ojo en la ventana de escritorio, mientras que la de ambos ojos se representa en el casco.
7. Tienes la opción de activar uno o ambos controladores de movimiento.  La entrada del controlador se asigna a la entrada de mano en el emulador.  Por ejemplo, para pulsar, presiona el gatillo del controlador de movimiento.  Para desplazarte, usa la palanca de mando.  Para consultar una lista completa de los controles, visita [Entrada de datos avanzada en el emulador de HoloLens y el simulador de Mixed Reality](advanced-hololens-emulator-and-mixed-reality-simulator-input.md).

¿Tienes problemas para ver el contenido en el casco?

- Si la pantalla está en blanco tanto en el casco como en el Portal de realidad mixta, pero el contenido se muestra en la ventana del emulador de HoloLens 2 del escritorio, comprueba que la aceleración de gráficos mediante hardware esté habilitada en el emulador.  La compatibilidad con cascos envolventes de Windows Mixed Reality requiere que la aceleración de gráficos mediante hardware esté habilitada en el emulador.
- Si ves contenido en el casco, pero los hologramas están borrosos o ves una imagen doble, sigue estos pasos para ajustar la vista estereoscópica para tus ojos:

1. Desactiva temporalmente "Use HMD for simulation" (Usar HMD para la simulación).
2. Inicia el Editor del Registro (regedit.exe).
3. Ve a HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation.
4. Crea un nuevo valor DWORD denominado "EnableEyePoseControl" y establece su valor en 1.
5. Habilita "Use HMD for simulation" (Usar HMD para la simulación) en el emulador.
6. Cuando aparezca el contenido en el casco, usa las teclas de dirección para ajustar la rotación de los ojos.  Mantén presionada la tecla Alt Izq para ajustar el ojo izquierdo y la tecla Alt Gr para ajustar el ojo derecho.  Usa las teclas "Q" y "E" para ajustar el giro de cada ojo y, de nuevo, mantén presionada la tecla Alt correspondiente a cada ojo.  Usa las teclas "+" y "-" para ajustar la distancia entre los ojos.  (Ten en cuenta que las teclas +/- del teclado numérico no funcionarán,  debes usar los botones del teclado principal).
7. Cuando la vista estereoscópica parezca correcta, presiona "S" para guardar los cambios.  La nueva configuración se guardará para futuros inicios del emulador.
8. Si quieres abandonar los cambios y volver a la configuración anterior, presiona "L" para cargar la configuración predeterminada o anterior.
9. Cambia el valor de "EnableEyePoseControl" del registro a 0, deshabilita la opción "Use HMD for simulation" (Usar HMD para la simulación) y vuelve a habilitarla.

Si guardó una configuración y quiere quitarla, puede eliminar el valor denominado "DisplayConfiguration" de HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation.  Si en este momento estás usando el casco con el emulador, tendrás que desactivar la opción "Use HMD for simulation" (usar HMD para la simulación) y volver a activarla para que este cambio se aplique.

## <a name="anatomy-of-the-hololens-first-gen-emulator"></a>Anatomía del emulador de HoloLens (primera generación)

### <a name="main-window"></a>Ventana principal

Cuando se inicie el emulador, verá una ventana que muestra el sistema operativo de HoloLens.

![Ventana principal del emulador de HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barra de herramientas

A la derecha de la ventana principal, encontrarás la barra de herramientas del emulador. La barra de herramientas contiene los siguientes botones:
* ![Icono Cerrar](images/emulator-close.png) **Cerrar**: cierra el emulador.
* ![Icono Minimizar](images/emulator-minimize.png) **Minimizar**: minimiza la ventana del emulador.
* ![Icono Human input](images/emulator-control.png) (Entrada humana) **Human input** (Entrada humana): se usan el mouse y el teclado para simular la [entrada humana al emulador](#basic-emulator-input).
* ![Icono Entrada mediante teclado y mouse](images/emulator-input.png) **Entrada mediante teclado y mouse**: la entrada de teclado y mouse se pasa directamente al sistema operativo de HoloLens como eventos de teclado y mouse, como si estuvieras conectado a un teclado y un mouse por Bluetooth.
* ![Icono Ajustar a la pantalla](images/emulator-fit.png) **Ajustar a la pantalla**: ajusta el emulador a la pantalla.
* ![Icono Zoom](images/emulator-zoom.png) **Zoom**: aumenta o reduce el emulador.
* ![Icono Ayuda](images/emulator-help.png) **Ayuda**: abre la Ayuda del emulador.
* ![Icono Open device portal](images/emulator-deviceportal.png) (Abrir portal de dispositivos) **Open Device Portal** (Abrir portal de dispositivos): abre el Portal de dispositivos Windows correspondiente al sistema operativo de HoloLens en el emulador.
* ![Icono Herramientas](images/emulator-tools.png) **Herramientas**: abre el panel **Herramientas adicionales**.

### <a name="simulation-tab"></a>Pestaña de simulación

La pestaña predeterminada dentro del panel **Herramientas adicionales** es la pestaña **Simulación**.

![Panel "Herramientas adicionales" del emulador de HoloLens](images/emulator-simulation-500px.png)

La pestaña Simulation (Simulación) muestra el estado actual de los sensores simulados usados para controlar el sistema operativo de HoloLens dentro del emulador. Al mantener el puntero del mouse sobre cualquier valor de esta pestaña, se proporciona información sobre herramientas que describe cómo controlar ese valor.

### <a name="room-tab"></a>Pestaña de habitación

El emulador simula una entrada del mundo real en forma de una malla de asignación espacial de habitaciones simuladas. Esta pestaña permite elegir una habitación para cargar distinta de la predeterminada.

![Pestaña de habitaciones del emulador de HoloLens](images/emulator-room-500px.png)

Para más información, consulta [Habitaciones simuladas](#simulated-rooms).

### <a name="account-tab"></a>Pestaña Cuenta

La pestaña Cuenta le permite configurar el emulador para iniciar sesión con una cuenta Microsoft. Es útil para probar las API que requieren que el inicio de sesión del usuario se realice con una cuenta. Después de activar la casilla de esta página, en los posteriores inicios del emulador se solicitará que inicie sesión, igual que cuando se inicia HoloLens por primera vez.

## <a name="simulated-rooms"></a>Habitaciones simuladas

Las habitaciones simuladas son útiles para probar la aplicación en varios entornos. Con el emulador se incluyen varias habitaciones. Una vez instalada la emulación, la encontrará en %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(versión)\Plugins\Rooms. Todas estas habitaciones se capturaron en entornos reales mediante un dispositivo HoloLens:

* **DefaultRoom.xef**: una pequeña sala de estar con un televisor, una mesita baja y dos sofás. Se carga de forma predeterminada cuando se inicia el emulador.
* **Bedroom1.xef**: un dormitorio pequeño con una mesa.
* **Bedroom2.xef**: un dormitorio con una cama queen-size, una cómoda, mesillas de noche y un vestidor.
* **GreatRoom.xef**: una habitación grande de espacios abiertos con salón, mesa de comedor y cocina.
* **LivingRoom.xef**: un salón con chimenea, sofá, sillones y una mesita baja con un jarrón.

También puede grabar sus propias habitaciones para usarlas en el emulador mediante la página Simulación del [Portal de dispositivos de Windows](using-the-windows-device-portal.md) del dispositivo HoloLens (primera generación).

En el emulador solo verá los hologramas que represente. Sin embargo, no verá la habitación simulada detrás de los hologramas. Esto es diferente del dispositivo HoloLens real, donde puedes ver que ambos se fusionan. Si quieres ver la habitación simulada en el emulador de HoloLens, debes actualizar la aplicación para representar la malla de asignación espacial en la escena.

## <a name="known-issues"></a>Problemas conocidos

* Al desinstalar el emulador de HoloLens 2, es posible que la imagen de disco duro (Flash.vhdx) se quede en tu disco duro, en la carpeta Windows Kits\10\Emulation\HoloLens\<build number>.  La eliminación de este archivo no implica ningún riesgo.
* La aceleración de gráficos mediante hardware puede hacer que las aplicaciones holográficas se bloqueen en algunos sistemas con gráficos de AMD o Intel.  Este problema se soluciona al deshabilitar la aceleración de gráficos mediante hardware en la ventana Herramientas del emulador.
* Después de instalar las actualizaciones más recientes de Windows a partir de julio de 2020, puede que la aceleración de gráficos por hardware en el emulador de HoloLens (primera generación) ya no esté disponible.
El componente RemoteFX necesario para la aceleración de gráficos por hardware está en desuso y se quitará en una versión futura de Windows.  Para volver a habilitar la aceleración de gráficos por hardware, use el [cmdlet Enable-VMRemoteFXPhysicalVideoAdapter de PowerShell](/powershell/module/hyper-v/enable-vmremotefxphysicalvideoadapter).  Para obtener información adicional, consulte la [documentación sobre el desuso y la eliminación de la compatibilidad de RemoteFX en Windows](https://support.microsoft.com/help/4570006/update-to-disable-and-remove-the-remotefx-vgpu-component).

## <a name="troubleshooting"></a>Solucionar problemas

Puede que al instalar el emulador recibas un mensaje de error, que indica que necesitas *"Visual Studio 2015 Update 1 y UWP Tools versión 1.2"* . Hay tres posibles causas de este error:
* No tiene una versión de Visual Studio lo bastante reciente (Visual Studio 2019, Visual Studio 2017 o Visual Studio 2015 Update 1 o posterior). Para corregir este problema, instala la versión más reciente de Visual Studio.
* Tiene una versión reciente de Visual Studio, pero no tiene instaladas las herramientas de la Plataforma universal de Windows (UWP). Esta es una característica opcional de Visual Studio. Para HoloLens (primera generación), necesitará las herramientas de UWP para Visual Studio 2015 o Visual Studio 2017.

Puede que también reciba un error al instalar el emulador en una SKU de Windows que no pertenezca a las ediciones Pro, Enterprise o Education, o si no tiene habilitada la característica Hyper-V.
* Lee la sección [Requisitos del sistema](#hololens-emulator-system-requirements) anterior para conocer el conjunto completo de requisitos.
* Asegúrate también de que la característica Hyper-V se haya habilitado en el sistema.

Si la instalación se completa correctamente, pero no aparece el emulador de HoloLens como una opción para implementar y depurar, compruebe lo siguiente:
* La configuración del proyecto de Visual Studio está establecida en x86 (HoloLens de primera generación) o en x86 o x64 (emulador de HoloLens 2).
* Si usas Visual Studio 2019, el conjunto de herramientas de plataforma en la configuración del proyecto está establecido en v142.

Si la instalación se completa correctamente, pero Visual Studio muestra un error al intentar iniciar el emulador de HoloLens, pruebe lo siguiente:
* Ejecuta Visual Studio como administrador.
* Si ha tenido instalado alguna vez Visual Studio 2019, compruebe que el valor del Registro "KitsRoot10" en HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots apunta a la carpeta Archivos de programa de 32 bits (por ejemplo, "C:\Archivos de programa (x86)\Windows Kits\10").  Si no es así, desinstale el emulador de HoloLens, cambie el valor del Registro por la carpeta Archivos de programa de 32 bits y vuelva a instalar el emulador de HoloLens.  Este problema se soluciona en Visual Studio 2019 16.0.3.

Si el emulador muestra el cuadro de diálogo de error "Codificación de bytes no válida" al inicio:
* Elimina todos los archivos de %localappdata%\Microsoft\XDE\HCS y vuelve a intentarlo.

Si la lista de destinos de depuración de Visual Studio está vacía (por ejemplo, la única opción es Iniciar) y has seguido todos los pasos anteriores de solución de problemas:
* Elimina la carpeta ConfigurationCache de %localappdata%\Microsoft\VisualStudio\\<*id. de instalación*>\CoreCon y vuelve a intentarlo.

Si el sistema se bloquea cuando se inicia el emulador, deshabilita la aceleración de hardware para los gráficos del emulador.
* Crea un valor DWORD del Registro llamado "DisableGPU" en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 y establece su valor en 1.

## <a name="see-also"></a>Consulta también
* [Introducción de datos avanzada en el emulador de HoloLens y el simulador de realidad mixta](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Historial de software del emulador de HoloLens](hololens-emulator-archive.md)
* [Asignación espacial en Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Asignación espacial en DirectX](../../develop/native/spatial-mapping-in-directx.md)