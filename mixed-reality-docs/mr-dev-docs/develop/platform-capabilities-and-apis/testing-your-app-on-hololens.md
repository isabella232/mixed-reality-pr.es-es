---
title: Prueba de una aplicación en HoloLens
description: Obtenga información sobre instrucciones generales y sugerencias para probar y optimizar el rendimiento de HoloLens aplicaciones de realidad mixta.
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, pruebas
ms.openlocfilehash: 2f423560191fea8b516db80d533898b5a1f15973442e7bb6cd8878d486e0ffba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212106"
---
# <a name="testing-your-app-on-hololens"></a>Prueba de una aplicación en HoloLens

Probar HoloLens aplicaciones es similar a probar Windows aplicaciones. Todavía debe tener en cuenta la funcionalidad, la interoperabilidad, el rendimiento, la seguridad, la confiabilidad, y así sucesivamente. Sin embargo, algunas áreas que no se abren en aplicaciones de PC o teléfono requieren un control especial. Las aplicaciones holográficas deben ejecutarse sin problemas en un conjunto diverso de entornos. También deben mantener el rendimiento y la comodidad del usuario en todo momento. Esta guía le ayudará a probar estas áreas.

## <a name="performance"></a>Rendimiento

Las aplicaciones holográficas deben ejecutarse sin problemas en un conjunto diverso de entornos. También deben mantener el rendimiento y la comodidad del usuario en todo momento. El rendimiento es tan importante para la experiencia del usuario con una aplicación holográfica que tenemos un tema completo dedicado a ella. Asegúrese de leer y seguir la descripción [del rendimiento de Mixed Reality](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Prueba de 3D en 3D

1. **Pruebe la aplicación en tantos espacios diferentes como sea posible.** Pruebe en salas grandes, salas pequeñas, salas, cocinas, habitaciones, oficinas, y así sucesivamente. También debe tener en cuenta las salas con características no estándar, como las paredes no verticales, las paredes curvas y los suelos no horizontales. ¿Funciona bien al realizar la transición entre habitaciones, plantas, pasando por casa o casa?
2. **Pruebe la aplicación en distintas condiciones de iluminación.** ¿Responde correctamente a diferentes condiciones ambientales, como la iluminación, las superficies negras y las superficies transparentes o reflectantes, como los reflejos y las paredes de cristal?
3. **Pruebe la aplicación en condiciones de movimiento diferentes.** Coloque el dispositivo y pruebe los escenarios en varios estados de movimiento. ¿Responde correctamente a un movimiento diferente o a un estado estable?
4. **Pruebe cómo funciona la aplicación desde distintos ángulos.** Si tiene un holograma bloqueado en el mundo, ¿qué ocurre si el usuario va detrás de él? ¿Qué ocurre si hay algo entre el usuario y el holograma? ¿Qué ocurre si el usuario examina el holograma por encima o por debajo?
5. **Use indicaciones espaciales y de audio.** Asegúrese de que la aplicación usa indicaciones espaciales y de audio para evitar que el usuario se pierda.
6. **Pruebe la aplicación en distintos niveles de ruido ambiental.** Si ha implementado comandos de voz, intente invocarlos con distintos niveles de ruido ambiental.
7. **Pruebe la aplicación sentado y de pie.** Asegúrese de realizar pruebas desde las posiciones de posición y de posición.
8. **Pruebe la aplicación desde distancias diferentes.** ¿Se pueden leer e interactuar elementos de la interfaz de usuario desde lejos? ¿Reacciona la aplicación a que los usuarios se acercan demasiado a los hologramas?
9. **Pruebe la aplicación con interacciones comunes de la barra de aplicaciones**. Todos los iconos de aplicación y [](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) las aplicaciones universales 2D tienen una barra de aplicaciones que le permite controlar la posición de las aplicaciones en el mundo mixto. Asegúrese de que al hacer clic en Quitar finaliza correctamente el proceso de la aplicación y botón Atrás se admite en el contexto de la aplicación universal 2D. Pruebe a escalar y mover la aplicación [en](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) el modo ajustar mientras está activa y mientras se trata de un icono de aplicación suspendida.

### <a name="environmental-test-matrix"></a>Matriz de pruebas ambientales

![Matriz de pruebas de entorno para HoloLens desarrollo de aplicaciones](images/environment-matrix-600px.png)

## <a name="comfort"></a>Comodidad

1. **Recortar planos.** Tenga cuidado con el [lugar en el que se representan los hologramas.](hologram-stability.md#hologram-render-distances)
2. **Evite el movimiento virtual incoherente con el movimiento real de la cabeza.** Evite mover la cámara de forma que no sea representativa del movimiento real del usuario. Si la aplicación requiere mover al usuario a través de una escena, haga que el movimiento sea predecible, minimice la aceleración y deje que el usuario controle el movimiento.
3. **Siga las directrices de calidad del holograma.** Es menos probable que las aplicaciones de rendimiento que implementan la guía de calidad [del holograma](hologram-stability.md) resulten en incomodidad del usuario.
4. **Distribuya hologramas horizontalmente en lugar de verticalmente.** Forzar al usuario a dedicar largos períodos de tiempo a buscar o bajar puede provocar una agotamiento en el cuello.

## <a name="input"></a>Entrada

### <a name="interaction-models"></a>Modelos de interacción

Asegúrese de que las interacciones del holograma funcionan con el modelo [de interacción elegido.](../../design/interaction-fundamentals.md)
También es una buena idea validar con diferentes accesorios, como el mouse y el teclado, si son necesarios para admitir la accesibilidad.

**Valide si la aplicación tiene un comportamiento diferente con el mouse y la función táctil.** Identifica las incoherencias y ayuda con las decisiones de diseño para que la experiencia sea más natural para los usuarios. Por ejemplo, desencadenar una acción basada en el puntero.


### <a name="custom-voice-commands"></a>Comandos de voz personalizados

[La entrada de](../../design/voice-input.md) voz es una forma natural de interacción. La experiencia del usuario puede ser mágica o confusa en función de la elección de los comandos y de cómo los exponga. Por lo general, no debe usar comandos de voz del sistema como "Seleccionar" o "Hola Cortana" como comandos personalizados. Estos son algunos puntos a tener en cuenta:
1. **Evite usar comandos que suenen de forma similar.** Puede desencadenar el comando incorrecto.
2. **Elija palabras con enriquecciones fonéticas cuando sea posible.** Minimiza o evita activaciones falsas.

### <a name="peripherals"></a>Periféricos

Los usuarios pueden interactuar con la aplicación a través [de periféricos](../../discover/hardware-accessories.md). Las aplicaciones no necesitan hacer nada especial para aprovechar esa funcionalidad, pero hay un par de cosas que merece la pena comprobar.
1. **Valide las interacciones personalizadas.** Elementos como métodos abreviados de teclado personalizados para la aplicación.
2. **Valide el cambio de tipos de entrada.** Intentando usar varios métodos de entrada para completar una tarea, como voz, gesto, mouse y teclado en el mismo escenario.

## <a name="system-integration"></a>Integración del sistema

### <a name="battery"></a>Batería

Pruebe la aplicación sin una fuente de alimentación conectada para comprender la rapidez con la que agota la batería. Se puede comprender fácilmente el estado de la batería si se observan las lecturas del LED de energía. 

![Estados LED que indican la energía de la batería](images/batterypowerledindication-500px.png)<br>

*Estados LED que indican la energía de la batería*

### <a name="power-state-transitions"></a>Transiciones de estado de energía

Los escenarios clave de validación funcionan según lo previsto al realizar la transición entre estados de energía. Por ejemplo, ¿la aplicación permanece en su posición original? ¿Conserva correctamente su estado? ¿Sigue funcionando según lo previsto?
1. **Stand-by/Resume.** Para entrar en espera, se puede presionar y soltar el botón de encendido inmediatamente. El dispositivo también entrará en espera automáticamente después de 3 minutos de inactividad. Para reanudar desde el modo de espera, se puede presionar y soltar el botón de encendido inmediatamente. El dispositivo también se reanudará si lo conecta o lo desconecta de una fuente de alimentación.
2. **Apagar o reiniciar.** Para apagarlo, mantenga presionado el botón de encendido continuamente durante 6 segundos. Para reiniciar, presione el botón de encendido.

### <a name="multi-app-scenarios"></a>Escenarios de varias aplicaciones

Valide la funcionalidad de la aplicación principal al cambiar entre aplicaciones, especialmente si ha implementado una tarea en segundo plano. Copiar y pegar y Cortana integración también merece la pena comprobar si procede.

## <a name="telemetry"></a>Telemetría

Use la telemetría y el análisis para guiarlo. La integración de análisis en la aplicación le ayudará a obtener información sobre la aplicación de los evaluadores beta y los usuarios finales. Estos datos se pueden usar para ayudar a optimizar la aplicación antes del envío a la Tienda y para futuras actualizaciones. Hay muchas opciones de análisis. Si no está seguro de por dónde empezar, consulte [App Ideas](https://www.visualstudio.com/products/application-insights-vs.aspx).

Preguntas que se deben tener en cuenta:
1. ¿Cómo usan los usuarios el espacio?
2. ¿Cómo coloca la aplicación objetos en el mundo? ¿puede detectar problemas?
3. ¿Cuánto tiempo dedican a diferentes fases de la aplicación?
4. ¿Cuánto tiempo dedican a la aplicación?
5. ¿Cuáles son las rutas de uso más comunes que los usuarios están intentando?
6. ¿Los usuarios alcanzan estados o errores inesperados?

## <a name="emulator-and-simulated-input"></a>Emulator entrada simulada

El [emulador HoloLens es](using-the-hololens-emulator.md) una excelente manera de probar eficazmente la aplicación holográfica con diferentes tipos de características y espacios de usuario simulados. Estas son algunas sugerencias para usar eficazmente el emulador para probar la aplicación:
1. **Use las salas virtuales del emulador para expandir las pruebas.** El emulador incluye un conjunto de salas virtuales que puede usar para probar la aplicación en incluso más entornos.
2. **Use el emulador para ver la aplicación desde todos los ángulos.** Las claves PageUp/PageDn harán que el usuario simulado sea más alto o más corto.
3. **Pruebe la aplicación con una aplicación HoloLens.** El HoloLens Emulator es una excelente herramienta para ayudarle a iterar rápidamente en una aplicación y detectar nuevos errores, pero asegúrese de que también realiza pruebas en un HoloLens físico antes de enviarlo a Windows Store. Esto es importante para asegurarse de que el rendimiento y la experiencia son excelentes en hardware real.

## <a name="automated-testing-with-perception-simulation"></a>Pruebas automatizadas con Simulación de percepción

Es posible que algunos desarrolladores de aplicaciones quieran automatizar las pruebas de sus aplicaciones. Además de las pruebas [](perception-simulation.md) unitarias simples, puede usar la pila de simulación de percepción HoloLens para automatizar la entrada humana y mundial a la aplicación. La API de simulación de percepción puede enviar entradas simuladas al emulador de HoloLens o a un HoloLens.

## <a name="windows-app-certification-kit"></a>Kit para la certificación de aplicaciones en Windows

Para ofrecer a la aplicación la mejor oportunidad de publicarse en [Windows Store,](../../distribute/submitting-an-app-to-the-microsoft-store.md)valide y pruebe localmente antes de enviarla para su certificación. Si la aplicación tiene como destino el Windows. Familia de dispositivos [holográficos, Windows App Certification Kit](/windows/uwp/debug-test-perf/windows-app-certification-kit) solo ejecutará pruebas de análisis estático local en el equipo. No se ejecutará ninguna prueba en el HoloLens.

## <a name="see-also"></a>Consulte también

* [Envío de una aplicación a Windows Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)