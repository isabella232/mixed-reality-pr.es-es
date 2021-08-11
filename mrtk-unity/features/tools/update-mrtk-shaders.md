---
title: Herramienta de actualización de sombreador
description: Documentación sobre cómo actualizar sombreadores estándar de MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 9ed8a1e439b2bf911d8144a90259d99bf38b12e0404d9ad3365152bed633042c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197078"
---
# <a name="updating-shaders"></a>Actualizar sombreadores

A partir de la versión 2.6.0, los sombreadores MRTK se están control de versiones a través de MRTK. Archivo Shaders.sentinel. Al actualizar a una nueva versión de MRTK, puede aparecer el mensaje siguiente.

![Actualización del símbolo del sistema de sombreadores](../images/tools/UpdateShaderPrompt.png)

Al seleccionar **Sí** se indica a MRTK que sobrescriba el contenido de **los** sombreadores  >  **MRTK** de recursos con la versión más  >   reciente. Al seleccionar **No** se conservarán los archivos actuales. **Ignore** creará un archivo ( ) en `IgnoreUpdateCheck.sentinel` **Assets**  >  **MRTK** Shaders (Sombreadores MRTK de  >  recursos), lo que suprimirá las futuras comprobaciones de actualización del sombreador.

> [!IMPORTANT]
> Al sobrescribir los archivos del sombreador, se perderán las modificaciones personalizadas. Asegúrese de realizar una copia de seguridad de los archivos de sombreador modificados antes de actualizar.
>
> Si el proyecto se ha configurado para usar la canalización de representación universal (URP), anteriormente canalización de representación ligera (LWRP), vuelva **a** ejecutar Mixed Reality > **Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline**(Actualizar sombreador estándar de MRTK para canalización de representación ligera).

At también es posible comprobar si hay actualizaciones del sombreador en cualquier momento mediante **Mixed Reality** Toolkit Utilities Check for Shader Updates (Buscar actualizaciones del sombreador) en la barra de menús  >    >    >   del Editor de Unity.

![Comprobación de actualizaciones del sombreador](../images/tools/ShaderUpdateMenu.png)

**Comprobar las actualizaciones del sombreador** no tiene en cuenta `IgnoreUpdateCheck.sentinel` el archivo y permite la actualización del sombreador a petición.

> [!NOTE]
> No es necesario comprobar las actualizaciones del sombreador al importar los archivos .unitypackage de MRTK.
