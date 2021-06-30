---
title: Terminología
description: Diferentes términos del sistema de entrada en MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, entrada,
ms.openlocfilehash: 33f423fba286e9e85e6d0bedac82bff0b7aae81f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121463"
---
# <a name="input-system"></a>Sistema de entrada

El sistema de entrada es uno de los sistemas más grandes de todas las características que ofrece MRTK.
Muchas cosas del kit de herramientas se crean sobre él (punteros, foco, objetos prefab). El código dentro del sistema de entrada es lo que permite interacciones naturales, como agarrar y girar entre plataformas.

El sistema de entrada tiene parte de su propia terminología que merece la pena definir:

- **Proveedores de datos**

    La configuración de entrada del perfil de entrada tiene referencias a entidades conocidas como proveedores de datos; otra palabra que describe estos son los administradores de dispositivos. Se trata de componentes cuyo trabajo es extender el sistema de entrada de MRTK mediante la interacción con un sistema subyacente específico. Un ejemplo de proveedor es el proveedor de Windows Mixed Reality, cuyo trabajo es hablar con las API de Windows Mixed Reality subyacentes y, a continuación, traducir los datos de esas API en conceptos de entrada específicos de MRTK a continuación. Otro ejemplo sería el proveedor de OpenVR (cuyo trabajo es hablar con la versión abstracta de Unity de las API de OpenVR y, a continuación, traducir esos datos en conceptos de entrada de MRTK).

- **Controller**

    Representación de un controlador físico (ya sea un controlador de 6 grados de libertad, una mano de estilo HoloLens 1 con compatibilidad con gestos, una mano totalmente articulada, un controlador de movimiento bisiesco, etc.). Los administradores de dispositivos generan controladores (es decir, el administrador de dispositivos WMR genera un controlador y administra su duración cuando ve que existe una mano articulada).

- **Puntero**

    Los controladores usan punteros para interactuar con objetos de juego. Por ejemplo, el puntero de interacción próxima es responsable de detectar cuándo la mano (que es un controlador) está cerca de los objetos que se anuncian como compatibles con "interacción cercana". Otros ejemplos de punteros son la teleportación o punteros lejanos (es decir, el puntero de rayo de la mano del shell) que usan raycasts lejanos para interactuar con contenido que es más largo que la longitud de los brazos del usuario.

    El administrador de dispositivos crea punteros y, a continuación, los asocia a un origen de entrada. Para obtener todos los punteros de un controlador, haga lo siguiente: `controller.InputSource.Pointers`

    Tenga en cuenta que un controlador se puede asociar a muchos punteros diferentes al mismo tiempo. Para asegurarse de que esto no se convierta en caos, hay un mediador de puntero que controla qué punteros pueden estar activos (por ejemplo, el mediador deshabilitará los punteros de interacción lejana cuando se detecte una interacción cercana).

- **centro de atención**

    Los eventos de puntero se envían a objetos en el **foco.** La selección del foco variará según el tipo de puntero; un puntero de rayos de mano usará raycasts, mientras que un puntero a rayas usará los esféricos. Un objeto debe implementar IMixedRealityFocusHandler para recibir el foco. Es posible registrar globalmente un objeto para recibir eventos de puntero sin filtrar, pero no se recomienda este enfoque.

    El componente que actualiza los objetos que están en el foco es [FocusProvider.](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Cursor**

    Una entidad asociada a un puntero que proporciona indicaciones visuales adicionales en torno a la interacción del puntero. Por ejemplo, FingerCursor representará un anillo alrededor del dedo y puede girar ese anillo cuando el dedo esté cerca de objetos "casi interactuables". Un puntero se puede asociar a un solo cursor en el momento.

- **Interacción y manipulación**

    Los objetos se pueden etiquetar con un script de interacción o manipulación. Puede ser a través de [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) , o algo como [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

    Por ejemplo, NearInteractionGrabbable y NearInteractionTouchable permiten que determinados punteros (especialmente los punteros de interacción cercanos) sepan en qué objetos se puede centrar.

    Interactable y ManipulationHandler son ejemplos de componentes que escuchan eventos de puntero para modificar objetos visuales de interfaz de usuario o mover, escalar o girar objetos de juego.

La imagen siguiente captura la compilación de alto nivel (de abajo hacia arriba) de la pila de entrada de MRTK:

![Diagrama del sistema de entrada](../features/images/input/MRTK_InputSystem.png)
