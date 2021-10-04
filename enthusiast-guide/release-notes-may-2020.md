---
title: 'Notas de la versión: mayo de 2020'
description: Manténgase al día de las notas Windows Mixed Reality de la versión de Windows 10 de mayo de 2020.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: notas de la versión, versión, windows 10, compilación, 19h1, os, mayo de 2020
ms.openlocfilehash: 462fcbfa10cfff8df23c970fd54ee0754a4d9472
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439177"
---
# <a name="windows-10-release-notes---may-2020"></a>Windows 10 notas de la versión: mayo de 2020

La actualización Windows 10 mayo de **2020 (v2004)** incluye nuevas características para cascos de Windows Mixed Reality (VR), como la capacidad de iniciar aplicaciones Win32 en el ambiente principal. HoloLens (1.ª generación) se encuentra en mantenimiento a largo plazo (LTS), con actualizaciones de mantenimiento que se lanzarán mensualmente.

Al actualizar a la versión más reciente del equipo Windows Mixed Reality cascos envolventes (VR), abra Configuración > **Update & Security** y seleccione Buscar **actualizaciones.** En un Windows 10, también puede instalar manualmente la actualización de Windows 10 de mayo de **2020** mediante la herramienta Windows [de creación de medios](https://www.microsoft.com/software-download/windows10).

**Versión más reciente de Desktop:** Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Actualizaciones de cascos Windows Mixed Reality envolventes

### <a name="introducing-the-new-microsoft-edge"></a>Presentación de la nueva versión de Microsoft Edge

Como [se anunció anteriormente,](/windows/mixed-reality/new-microsoft-edge)hemos realizado actualizaciones para mejorar la compatibilidad con el nuevo explorador Microsoft Edge en Windows Mixed Reality. La nueva Microsoft Edge adopta el proyecto de código abierto Chromium para crear una mejor compatibilidad web para los clientes y una menor fragmentación de la web para todos los desarrolladores web. También admite WebXR, el nuevo estándar para crear experiencias web envolventes para cascos vr, en lugar de WebVR.

### <a name="improved-settings-for-wmr"></a>Mejoras Configuración wmr

Gracias a sus comentarios, hemos agregado y aclarado la configuración en la página de visualización casco:

* **Calidad visual de mi hogar:** el cambio de esta configuración solo afecta al entorno ambiente principal (Casa sobre el acantilado y Skyloft):

* **Ajuste el nivel de detalle y la** calidad de los efectos en el ambiente principal: esto cambia algunas de las representaciones que se usan en el hogar. En concreto, la calidad visual de los distintos materiales (bosque, concreto, entre otros) se escalará a medida que cambie esta configuración de baja a alta.

* **Cambiar la resolución de la** ventana de la aplicación: de forma predeterminada, la mayoría de las ventanas 2D iniciadas en el hogar se inician con una resolución de 720 p. Aunque puede cambiar el tamaño horizontalmente & verticalmente, también puede optar por que todos se inicien a 1080p en su lugar. Anteriormente, esta opción estaba disponible como opción Muy alta (beta) en Calidad visual. Lo hemos dividido correctamente como una configuración independiente ahora.

* **Opciones de experiencia:** estas opciones ajustan la experiencia de realidad mixta para reducir la carga en los sistemas en los que el hardware podría tener dificultades para mantenerse al día con 90 fps sin restricciones. Puede habilitar o deshabilitar explícitamente estas opciones adicionales, o bien elegir Let Windows decide and let our heuristics continue deciding when to toggle these on and off (Permitir a Windows decidir y dejar que nuestra heurística siga decidiendo cuándo activar y desactivar estas opciones).

* **Resolución:** si tiene un casco de alta resolución como HP Reverb, se admite su ejecución en su resolución nativa o con una resolución reducida por motivos de rendimiento. Los cascos anteriores, como Samsung Samsung Samsung y Samsung Samsung+ , solo admiten una única resolución para que no pueda cambiar esta configuración en esos cascos.

* **Velocidad de** fotogramas: ahora puede establecer manualmente la velocidad de fotogramas de la pantalla del casco o dejar que Windows use su heurística para determinar si 60 Hz o 90 Hz son más adecuados.

* **Calibración:** como antes, puede ajustar el IPD (distancia interpupillaria) si lo admite el casco.

* **Conmutación de entrada:** cambie el comportamiento del cambio de foco de entrada (Win+Y) para que sea automático (en función de los comentarios del sensor de presencia) o manual.

### <a name="new-cortana-app"></a>Nueva Cortana aplicación

Esta actualización de Windows incluye la versión más reciente de la aplicación Cortana, que actualmente es solo en inglés de Estados Unidos y ya no admite determinados comandos específicos de realidad mixta, como "Tomar una imagen" y "Tomar un vídeo". Puede usar el nuevo Cortana para iniciar aplicaciones y también admite nuevos comandos centrados en la productividad, como "¿Cuándo es mi próxima reunión?". o "Enviar un correo \< name \> electrónico a para que se esté ejecutando tarde".
    
### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Actualizaciones adicionales disponibles en la versión 19041.546 (publicada en octubre de 2020)

Esta actualización de mantenimiento mensual de escritorio incluye los siguientes cambios para Windows Mixed Reality dispositivos: 
* Reduce las distorsión y las aberraciones en Windows Mixed Reality pantallas montadas en la cabeza (HMD). 
* Agrega compatibilidad con los próximos controladores de movimiento Windows Mixed Reality HP. 
* Cambia el comportamiento de la configuración de frecuencia de actualización de 90 Hz en Windows Mixed Reality para que ya no vuelva a cambiar automáticamente a 60 Hz en determinados casos cuando no se puede lograr 90 Hz. 

### <a name="help-us-improve"></a>¡Ayúdenos a mejorar!

Buscamos continuamente mejorar la compatibilidad.  Si encuentra que la aplicación Win32 clásica favorita no se comporta correctamente mientras está Windows Mixed Reality, envíe comentarios a través de [nuestro Centro de opiniones](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

## <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión: mayo de 2019](release-notes-may-2019.md)
* [Notas de la versión (octubre de 2018)](release-notes-october-2018.md)
* [Notas de la versión: abril de 2018](release-notes-april-2018.md)
* [Notas de la versión (octubre de 2017)](release-notes-october-2017.md)
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte también
* [Compatibilidad con cascos envolventes (vínculo externo)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (vínculo externo)](https://support.microsoft.com/products/hololens)
* [Instalación de las herramientas](/windows/mixed-reality/develop/install-the-tools)
* [Envíenos sus comentarios.](/windows/mixed-reality/give-us-feedback)