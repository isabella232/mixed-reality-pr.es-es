---
title: Actualización de aplicaciones de SteamVR para Windows Mixed Reality
description: Procedimientos recomendados para actualizar la aplicación de SteamVR para maximizar la compatibilidad con Windows Mixed Reality cascos.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, Compatibilidad, porte, HoloLens 1.ª generación, casco de realidad mixta, casco de windows de realidad mixta, migración, Windows 10, steam, controladores de movimiento, hápticos
ms.openlocfilehash: ee72994691970a3701ec8462ab0f42b6d1da1820589ca68a92c9a78fe1c18a41
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196195"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Actualización de aplicaciones de SteamVR para Windows Mixed Reality

Animamos a los desarrolladores a probar y optimizar sus experiencias de SteamVR para que se ejecuten Windows Mixed Reality cascos. En esta documentación se tratan las mejoras comunes que puede realizar para que sus experiencias se ejecuten de forma excelente Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Instrucciones de configuración inicial

Para empezar a probar el juego o la aplicación en Windows Mixed Reality asegúrese de seguir primero nuestra guía [de introducción.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

## <a name="controller-models"></a>Modelos de controlador

1. Si la aplicación representa modelos de controlador:
    * Uso de los [Windows Mixed Reality de controlador de movimiento](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * Use IVRRenderModel::GetComponentState para obtener transformaciones locales en partes de componentes (por ejemplo, posición de puntero)
2. Las experiencias que tienen una noción de entrega deben obtener sugerencias de las API de entrada para diferenciar los controladores [(ejemplo de Unity)](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controles

Al diseñar o ajustar el diseño del control, tenga en cuenta el siguiente conjunto de comandos reservados:
1. Al hacer clic en **el botón de posición análogo izquierdo y derecho,** se reserva para el panel de **Steam**.

> [!NOTE]
> Si usa un controlador HP Reverb G2, al hacer clic en el botón de menú derecho se reserva el panel **de Steam.**

2. El **Windows de inicio** siempre devolverá a los usuarios al Windows Mixed Reality inicio.

Si es posible, el valor predeterminado es teleportación basada en el clic de posición para que coincida con [Windows Mixed Reality comportamiento](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) de teleportación de inicio.

## <a name="tooltips-and-ui"></a>Información sobre herramientas e interfaz de usuario

Muchos juegos de realidad virtual aprovechan las superposiciones y la información sobre herramientas del controlador de movimiento para enseñar a los usuarios sus aplicaciones o juegos los comandos más importantes. Al optimizar la aplicación para Windows realidad mixta, se recomienda revisar esta parte de la experiencia para asegurarse de que la información sobre herramientas se asigna Windows modelos de controlador.

Además, si hay algún punto en su experiencia en el que muestre imágenes de los controladores, asegúrese de proporcionar imágenes actualizadas mediante los controladores Windows Mixed Reality movimiento.

## <a name="haptics"></a>Haptics

A partir de la Windows 10 actualización de abril de [2018,](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)ahora se admiten los hápticos para las experiencias de SteamVR Windows Mixed Reality. Si la aplicación o el juego de SteamVR ya incluye compatibilidad con hápticos, ahora debería funcionar (sin ningún trabajo adicional) con Windows Mixed Reality [de movimiento.](../../design/motion-controllers.md)

Windows Mixed Reality controladores de movimiento usan un motor háptico estándar, en lugar de los accionadores lineales que se encuentran en otros controladores de movimiento de SteamVR. Esto puede dar lugar a una experiencia de usuario ligeramente diferente de la esperada. Por lo tanto, se recomienda probar y ajustar el diseño háptico con Windows Mixed Reality de movimiento. Por ejemplo, a veces los pulsaciones hapticas cortas (5-10 ms) son menos perceptibles en Windows Mixed Reality de movimiento. Para generar un pulso más perceptible, experimente con el envío de un "clic" más largo (40-70 ms) para dar más tiempo al motor para que se en marcha antes de que se le diga que apague de nuevo.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Inicio de aplicaciones de SteamVR desde Windows Mixed Reality menú Inicio

En el caso de las experiencias de realidad virtual distribuidas a través de Steam, hemos actualizado [Windows Mixed Reality para SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto con las [versiones Windows versión más recientes.](https://insider.windows.com) Los títulos de SteamVR ahora se muestran automáticamente Windows Mixed Reality menú Inicio en la lista "Todas las aplicaciones".

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality logotipo

Para mostrar Windows Mixed Reality compatibilidad con el título, vaya al vínculo "Editar página de la Tienda" en la página de aterrizaje de la aplicación, seleccione la pestaña "Información básica" y desplácese hacia abajo hasta "Virtual Reality". Desactive la opción "Ocultar Windows Mixed Reality" y, a continuación, publique en el almacén.

## <a name="bugs-and-feedback"></a>Errores y comentarios

Sus comentarios son muy valiosos cuando se trata de mejorar la Windows Mixed Reality de SteamVR. Envíe todos los comentarios y errores a través [del Centro de opiniones sobre Windows](/windows/mixed-reality/enthusiast-guide/filing-feedback). Estas son algunas sugerencias sobre cómo hacer que los comentarios [de SteamVR sean lo más útiles posible.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)

Si tiene preguntas o comentarios que compartir, también puede comunicarse con nosotros en nuestro foro [de Steam.](https://steamcommunity.com/app/719950/discussions/)

## <a name="faqs-and-troubleshooting"></a>Preguntas más frecuentes y solución de problemas

Si tiene problemas generales para configurar o reproducir su experiencia, consulte los pasos de solución de problemas [más recientes.](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)

## <a name="see-also"></a>Consulta también

* [Instalación de las herramientas](../install-the-tools.md)
* [Historial de controladores de cascos y controladores de movimiento](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality de compatibilidad de hardware de equipo mínimo](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)