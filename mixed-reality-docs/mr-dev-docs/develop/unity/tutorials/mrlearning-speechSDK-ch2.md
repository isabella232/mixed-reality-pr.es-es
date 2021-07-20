---
title: Ejecución de comandos mediante el reconocimiento de voz de Azure
description: Complete este curso para aprender a ejecutar comandos mediante el reconocimiento de voz de Azure en aplicaciones de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, speech recognition, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 8d031896a1725c0121272b68578016edf38a36cf
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656623"
---
# <a name="2-execute-commands-using-azure-speech-recognition"></a>2. Ejecución de comandos mediante el reconocimiento de voz de Azure

En este tutorial, agregarás la posibilidad de ejecutar comandos con el reconocimiento de voz de Azure, lo que te permitirá hacer que pase algo en función de la palabra o frase que definas.

## <a name="objectives"></a>Objetivos

* Aprender a usar el reconocimiento de voz de Azure para ejecutar comandos

## <a name="instructions"></a>Instrucciones

En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Wake Word Recognizer (Script)** (Reconocimiento de la palabra de activación de Lunarcom [script]) al objeto Lunarcom y configúralo como se indica a continuación:

* En el campo **Wake Word** (Palabra de activación), escribe una frase adecuada; por ejemplo, _Activate terminal_ (Activar terminal).
* En el campo **Dismiss Word** (Palabra de descarte), escribe una frase adecuada; por ejemplo, _Dismiss terminal_ (Descartar terminal).

![Editor de Unity con el componente Wake Word Recognizer (Script) (Reconocimiento de palabra de activación [script])](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> El componente Wake Word Recognizer (Script) (Reconocimiento de palabra de activación [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

Si ahora entras en el modo de juego, como en el tutorial anterior, el panel del terminal está habilitado de forma predeterminada, pero puedes deshabilitarlo diciendo la palabra de descarte: **Dismiss terminal** (Descartar terminal):

![Editor de Unity en modo de reproducción con la característica de reconocedor de voz en uso](images/mrlearning-speech/tutorial2-section1-step1-2.png)

Para volver a habilitarlo, indica la palabra de activación **Activate terminal** (Activar terminal):

![Editor de Unity en modo de reproducción con el terminal activo](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.

> [!TIP]
> Si prevé que no podrá conectarse a Azure con frecuencia, también puede implementar comandos de voz mediante MRTK, para lo que debe seguir las instrucciones de [Uso de comandos de voz](mr-learning-base-09.md).

## <a name="congratulations"></a>Enhorabuena

Has implementado comandos de voz con tecnología de Azure. Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.

En el próximo tutorial, aprenderás a traducir la voz mediante la traducción de voz de Azure.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 3. Adición del componente de traducción de voz de Azure Cognitive Services](mrlearning-speechSDK-ch3.md)
