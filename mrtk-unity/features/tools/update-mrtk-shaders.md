---
title: Herramienta de actualización de sombreador
description: Documentación sobre cómo actualizar sombreadores estándar de MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647101"
---
# <a name="updating-shaders"></a>Actualizar sombreadores

A partir de la versión 2.6.0, los sombreadores MRTK se están control de versiones a través de MRTK. Archivo Shaders.sentinel. Al actualizar a una nueva versión de MRTK, puede aparecer el mensaje siguiente.

![Actualización del símbolo del sistema de sombreadores](../images/tools/UpdateShaderPrompt.png)

Al seleccionar **Sí** se indica a MRTK que sobrescriba el contenido de **los** sombreadores  >  **MRTK** de recursos con la versión más  >   reciente. Al seleccionar **No,** se conservarán los archivos actuales. **Omitir** creará un archivo ( ) en `IgnoreUpdateCheck.sentinel`   >  **Sombreadores MRTK** de recursos  >  , lo que suprimirá futuras comprobaciones de actualización del sombreador.

> [!IMPORTANT]
> Al sobrescribir los archivos del sombreador, se perderán las modificaciones personalizadas. Asegúrese de realizar una copia de seguridad de los archivos de sombreador modificados antes de actualizar.
>
> Si el proyecto se ha configurado para usar la canalización de representación universal (URP), anteriormente canalización de representación ligera (LWRP), vuelva **a** ejecutar Mixed Reality > **Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline**(Actualizar el sombreador estándar de MRTK para la canalización de representación ligera).

At también es posible comprobar si hay actualizaciones de sombreador en cualquier momento mediante **Mixed Reality** Toolkit Utilities Check for Shader Updates (Comprobar actualizaciones del sombreador) en la barra de menús del  >    >    >   Editor de Unity.

![Comprobación de actualizaciones del sombreador](../images/tools/ShaderUpdateMenu.png)

**La comprobación de actualizaciones del sombreador** no tiene en `IgnoreUpdateCheck.sentinel` cuenta el archivo y permite la actualización del sombreador a petición.

> [!NOTE]
> No es necesario comprobar las actualizaciones del sombreador al importar los archivos .unitypackage de MRTK.
