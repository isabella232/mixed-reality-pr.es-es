---
title: 'HoloLens (primera generación) y Azure (309): Application Insights'
description: Complete este curso para aprender a recopilar análisis relacionados con el comportamiento del usuario dentro de una aplicación de realidad mixta, mediante Aplicación de Azure Ideas Service.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, application insights, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 549afbd1e5a3f42bb0540714500d31edf022d36511961e887ac9e927b9af1ea3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222332"
---
# <a name="hololens-1st-gen-and-azure-309-application-insights"></a>HoloLens (1ª generación) y Azure 309: Application Insights

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro y que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

![final product -start](images/AzureLabs-Lab309-00.png)

En este curso, aprenderá a agregar funcionalidades de Application Ideas a una aplicación de realidad mixta, mediante la API de Aplicación de Azure Ideas para recopilar análisis relacionados con el comportamiento del usuario.

Application Ideas es un servicio de Microsoft, que permite a los desarrolladores recopilar análisis de sus aplicaciones y administrarlos desde un portal fácil de usar. El análisis puede ser cualquier cosa, desde el rendimiento hasta la información personalizada que le gustaría recopilar. Para obtener más información, visite la [página de Ideas aplicación](https://azure.microsoft.com/services/application-insights/).

Una vez completado este curso, tendrá una aplicación de casco envolvente de realidad mixta que podrá hacer lo siguiente:

1.  Permite al usuario mirar y moverse por una escena.
2.  Desencadene el envío de análisis a *Application Ideas Service* mediante el uso de mirada y proximidad a objetos en la escena.
3.  La aplicación también llamará al servicio, capturando información sobre el objeto al que se ha acercado más el usuario, en las últimas 24 horas. Ese objeto cambiará su color a verde.

Este curso le enseñará a obtener los resultados de Application Ideas Service en una aplicación de ejemplo basada en Unity. Será su función aplicar estos conceptos a una aplicación personalizada que pueda estar creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (309): Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en Windows Mixed Reality cascos envolventes (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga el curso, verá notas sobre los cambios que podría necesitar emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algún eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de la escritura (julio de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) como se muestra en el artículo Instalación de las herramientas, aunque no se debe suponer que la información de este curso coincidirá perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR).
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [casco Windows Mixed Reality envolvente (VR)](../../../discover/immersive-headset-hardware-details.md) o Microsoft HoloLens con el modo de desarrollador habilitado [](/hololens/hololens1-hardware)
- Un conjunto de auriculares con un micrófono integrado (si el casco no tiene un micrófono y altavoces integrados)
- Acceso a Internet para la instalación de Azure y la recuperación de Ideas de aplicaciones

## <a name="before-you-start"></a>Antes de comenzar

Para evitar problemas al compilar este proyecto, se recomienda encarecidamente crear el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).

> [!WARNING] 
> Tenga en cuenta que los datos que van *a Application Ideas* tardan tiempo, así que tenga paciencia. Si desea comprobar si el servicio ha recibido los datos, consulte el capítulo [14,](#chapter-14---the-application-insights-service-portal)que le mostrará cómo navegar por el portal.

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: Azure Portal

Para usar *Application Ideas*, deberá crear y configurar un servicio application *Ideas en* el Azure Portal.

1.  Inicie sesión en [Azure Portal](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los proctores para configurar la nueva cuenta.

2.  Una vez que haya  iniciado sesión, haga clic en Nuevo en la esquina superior izquierda y busque *Application Ideas* y haga clic en **Entrar.**

    > [!NOTE]
    > Es posible que **la** palabra Nuevo se haya reemplazado **por Crear un recurso** en los portales más recientes.

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  La nueva página de la derecha proporcionará una descripción de la *Aplicación de Azure Ideas* service. En la parte inferior izquierda de esta página, seleccione **el botón** Crear para crear una asociación con este servicio.

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  Una vez que haya hecho clic en **Crear:**

    1.  Inserte el nombre **deseado para** esta instancia de servicio.

    2.  Como **Tipo de aplicación,** seleccione **General.**

    3.  Seleccione una suscripción **adecuada.**

    4.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5.  Seleccione una **ubicación**.

    6.  También deberá confirmar que ha comprendido los términos y condiciones aplicados a este servicio.

    7.  Seleccione **Crear**.

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia *de Application Ideas Service.*

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Mantenga esta página web abierta y fácil de acceder; volverá aquí con frecuencia para ver los datos recopilados.

    > [!IMPORTANT]
    > Para implementar Application Ideas, deberá usar tres (3) valores específicos: **Clave** de instrumentación, Id. de aplicación y Clave de **API.** A continuación verá cómo recuperar estos valores del servicio. Asegúrese de tener en cuenta estos valores en una Bloc de notas *en* blanco, ya que los usará pronto en el código.

9.  Para buscar la **clave de instrumentación**, deberá desplazarse hacia abajo en la lista de funciones de servicio y hacer clic en Propiedades **;** la pestaña mostrada mostrará la clave **de servicio**.

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. Un poco debajo **de Propiedades**, encontrará acceso **de API,** en el que debe hacer clic. El panel de la derecha proporcionará el identificador **de aplicación** de la aplicación.

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. Con el panel **Id.** de aplicación todavía abierto, haga clic en Crear clave **de API,** que abrirá el panel Crear clave *de* API.

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. En el panel Crear clave *de API* ahora abierto, escriba una descripción y marque las **tres casillas**.

13. Haga clic **en Generar clave.** Se creará y mostrará la clave de **API.** 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Esta es la única vez que **se mostrará** la clave de servicio, así que asegúrese de realizar una copia de ella ahora.

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity y* haga clic en **Nuevo.**

    ![Configuración del Project Unity](images/AzureLabs-Lab309-11.png)

2.  Ahora deberá proporcionar un nombre de Project Unity e insertar **MR \_ Azure Application \_ \_ Ideas**. Asegúrese de que *la plantilla* está establecida en **3D.** Establezca Ubicación *en un* lugar adecuado para usted (recuerde que es mejor estar más cerca de los directorios raíz). A continuación, haga **clic en Crear proyecto.**

    ![Configuración de unity Project](images/AzureLabs-Lab309-12.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar \> preferencias** y, a continuación, en la nueva ventana, vaya a **Herramientas externas.** Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![Configuración de unity Project](images/AzureLabs-Lab309-13.png)

4.  A continuación, vaya a **File \> Build Configuración** and switch the platform to Universal Windows **Platform**,by click on the Switch Platform button( Cambiar **plataforma).**

    ![Configuración de unity Project](images/AzureLabs-Lab309-14.png)

5.  Vaya a **File \> Build Configuración** (Compilación de archivos) y asegúrese de que:

    1.  **Dispositivo de destino** está establecido en **Cualquier dispositivo**

        > Para la Microsoft HoloLens, establezca **Dispositivo de destino** en *HoloLens*.

    2.  **Tipo de** compilación se establece en **D3D**

    3.  **El SDK** se establece en **Instalado más reciente.**

    4.  **Build and Run (Compilar** y ejecutar) se establece en **Local Machine (Máquina local).**

    5.  Guarde la escena y agrégréla a la compilación.

        1.  Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.

            ![Configuración de unity Project](images/AzureLabs-Lab309-15.png)

        2. Cree una carpeta para esto y cualquier escena  futura y, a continuación, haga clic en el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![Configuración de unity Project](images/AzureLabs-Lab309-16.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo Nombre de *archivo:* texto, escriba **ApplicationInsightsScene** y, a continuación, haga clic **en Guardar.**

            ![Configuración de unity Project](images/AzureLabs-Lab309-17.png)

6.  El resto de la configuración, en **Build Configuración**, se debe dejar como valor predeterminado por ahora.

7.  En la **ventana Build Configuración** (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra **el inspector.**

    ![Configuración de unity Project](images/AzureLabs-Lab309-18.png)

8. En este panel, es necesario comprobar algunas configuraciones:

    1.  En la **pestaña Otros Configuración** datos:

        1.  **La** **versión del runtime de** scripting debe ser Experimental (equivalente a **.NET 4.6),** lo que desencadenará la necesidad de reiniciar el editor.

        2.  **El back-end de scripting** debe ser **.NET**

        3.  **El nivel de compatibilidad de** API debe ser **.NET 4.6**

        ![Configuración de unity Project](images/AzureLabs-Lab309-19.png)

    2.  En la **pestaña Publishing Configuración** (Configuración publicación), en **Capabilities (Funcionalidades),** active:

        - **InternetClient**     

            ![Configuración de unity Project](images/AzureLabs-Lab309-20.png)

    3.  Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de **Publishing Configuración**), marque **Virtual Reality Supported (Compatible** con virtual Reality), asegúrese de que se ha agregado Windows Mixed Reality **SDK.**

        ![Configuración de unity Project](images/AzureLabs-Lab309-21.png)

9.  De nuevo **en build Configuración**, los proyectos de **C#** de Unity ya no están en gris; Marque la casilla situada junto a esta.

10.  Cierre la ventana Build Settings (Configuración de compilación).

11.  Guarde la escena y Project (**ARCHIVO GUARDAR** ESCENA /  >  **ARCHIVO GUARDAR**  >  **PROYECTO**).


## <a name="chapter-3---import-the-unity-package"></a>Capítulo 3: Importación del paquete de Unity

> [!IMPORTANT]
> Si quiere omitir los componentes de configuración de *Unity* de este curso y continuar directamente en el código, no dude en descargar este paquete [Azure-MR-309.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)impórtelo en el proyecto como un paquete [**personalizado.**](https://docs.unity3d.com/Manual/AssetPackages.html) También contendrá los archivos DLL del capítulo siguiente. Después de la importación, continúe desde [**el capítulo 6.**](#chapter-6---create-the-applicationinsightstracker-class)

> [!IMPORTANT]
> Para usar Application Ideas en Unity, debe importar el archivo DLL, junto con newtonsoft DLL. Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (del 4 al 7 de esta sección) ya no serán necesarios una vez resuelto el error.

Para importar Application Ideas en su propio proyecto, asegúrese de que ha descargado [".unitypackage", que contiene los complementos](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). A continuación, haga lo siguiente:

1.  Agregue **el paquete .unitypackage** a Unity mediante la opción de **menú Import Package Custom Package \> \> (Importar paquete personalizado** de recursos).

2.  En el **cuadro Importar paquete de Unity** que aparece, asegúrese de que todo lo que hay en (e incluido) **Complementos** está seleccionado.

    ![Importación del paquete de Unity](images/AzureLabs-Lab309-22.png)

3.  Haga clic **en el** botón Importar para agregar los elementos al proyecto.

4.  Vaya a la **carpeta Ideas** en **Complementos** en la Project y seleccione solo los siguientes *complementos:*

    -   Microsoft.ApplicationInsights

    ![Importación del paquete de Unity](images/AzureLabs-Lab309-23.png)

5.  Con este *complemento* seleccionado, asegúrese de que **cualquier** plataforma esté desactivada **y,** a continuación, asegúrese de que **WSAPlayer** también esté desactivado y, a continuación, haga clic en **Aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![Importación del paquete de Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Al marcar los complementos como este, se configuran para que solo se utilicen en el editor de Unity. Hay un conjunto diferente de archivos DLL en la carpeta WSA que se usará después de exportar el proyecto desde Unity.

6.  A continuación, debe abrir la **carpeta WSA,** dentro de **la Ideas** carpeta. Verá una copia del mismo archivo que acaba de configurar. Seleccione este archivo y, a continuación, en el inspector,  asegúrese de que **cualquier** plataforma está desactivada y, a continuación, asegúrese de que solo **WSAPlayer** está **activado.** Haga clic en **Aplicar**.

    ![Importación del paquete de Unity](images/AzureLabs-Lab309-25.png)

7. Ahora deberá seguir los pasos **del 4 al 6,** pero para los *complementos de Newtonsoft* en su lugar. Vea la captura de pantalla siguiente para ver el aspecto que debería tener el resultado.

    ![Importación del paquete de Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Capítulo 4: Configuración de la cámara y los controles de usuario

En este capítulo, configurará la cámara y los controles para permitir que el usuario vea y se mueva por la escena.

1.  Haga clic con el botón derecho en un área vacía en el Panel de jerarquía y, a continuación, **en Crear**  >  **vacío.**

    ![Configuración de la cámara y los controles De usuario](images/AzureLabs-Lab309-26.png)

2.  Cambie el nombre del nuevo Objeto GameObject vacío a **Elemento primario de la cámara.**

    ![Configuración de la cámara y los controles De usuario](images/AzureLabs-Lab309-27.png)

3.  Haga clic con el botón derecho en un área vacía en el Panel de jerarquía y, a continuación, en **Objeto 3D** y, a continuación, en **Sphere**.

4.  Cambie el nombre de sphere a **Right Hand**.

5.  Establezca la **escala de transformación** de la mano derecha en **0.1, 0.1, 0.1**

    ![Configuración de la cámara y los controles De usuario](images/AzureLabs-Lab309-28.png)

6.  Quite el **componente Colisionador de** esfera  de la mano derecha; para ello, haga clic en el engranaje del componente *Colisionador* de esfera y, a continuación, quite **el componente**.

    ![Configuración de la cámara y los controles De usuario](images/AzureLabs-Lab309-29.png)

7.  En el Panel de jerarquía, arrastre **los objetos Cámara** principal y **Mano** derecha al objeto Primario **de la** cámara.

    ![Configuración de la cámara y los controles De usuario](images/AzureLabs-Lab309-30.png)

8.  Establezca la **posición de transformación** de la cámara **principal** y el **objeto derecho** en **0, 0, 0**.

    ![Configuración de la cámara y los controles De usuario](images/AzureLabs-Lab309-31.png)

    ![Configuración de la cámara y los controles De usuario](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Capítulo 5: Configuración de los objetos en la escena de Unity

Ahora creará algunas formas básicas para la escena, con las que el usuario puede interactuar.

1.  Haga clic con el botón derecho en un área vacía en el *Panel de* jerarquía y, a continuación, en **Objeto 3D** y, a continuación, **seleccione Plano**.

2.  Establezca posición de **transformación de plano** en **0, -1, 0**.

3.  Establezca la escala **de transformación de plano** en **5, 1, 5**.

    ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-33.png)

4.  Cree un material básico para usarlo con el **objeto Plane,** de modo que las demás formas sean más fáciles de ver. Vaya al panel *de Project, haga* clic con el botón derecho y, a continuación, haga clic en Crear **,** seguido de **Carpeta** para crear una nueva carpeta. Asínte el **nombre Materials**.

    ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-34.png) ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-35.png)

5.  Abra la **carpeta Materials y,** a continuación, haga clic con el botón derecho en **Crear** y, después, **en Material** para crear un nuevo material. Así mismo, den el **nombre Azul.**

    ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-36.png) ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-37.png)

6.  Con el **nuevo** material azul seleccionado, mire *el inspector* y haga clic en la ventana rectangular junto **a Albedo**. Seleccione un color azul (la imagen siguiente es **Color hexadecimal: \# 3592FFFF).** Haga clic en el botón Cerrar una vez que haya elegido.

    ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-38.png)

7.  Arrastre el nuevo material desde la carpeta  **Materials** hasta el plano recién creado, dentro de la escena (o suéltelo en el objeto **Plano** dentro de *la jerarquía*).

    ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-39.png)

8.  Haga clic con el botón derecho en un área vacía en el Panel de jerarquía *y,* a continuación, en **Objeto 3D, Vuelva a .**

    -  Con la **Opción** seleccionada, cambie **su posición** *de* transformación a: **-10, 1, 0**.

9.  Haga clic con el botón derecho en un área vacía en el *Panel de jerarquía y,* a continuación, en **Objeto 3D, Cubo**.

    -  Con el **cubo** seleccionado, cambie **su posición** *de* transformación a: **0, 0, 10**.

10. Haga clic con el botón derecho en un área vacía en el Panel de jerarquía *y,* a continuación, en **Objeto 3D, Sphere**.

    -  Con sphere **seleccionado,** cambie su **posición de** *transformación* a: **10, 0, 0**.

    ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Estos *valores position* son *sugerencias.* Puede establecer las posiciones de los objetos en lo que quiera, aunque es más fácil para el usuario de la aplicación si las distancias de los objetos no están demasiado lejos de la cámara.

11. Cuando la aplicación se está ejecutando, debe ser capaz de identificar los objetos dentro de la escena. Para lograrlo, deben etiquetarse. Seleccione uno de los objetos y, en el *panel Inspector,* haga clic en Agregar **etiqueta...**, que intercambiará el inspector con el *panel* **Etiquetas & capas.**

    ![Configuración de los objetos en la escena de Unity ](images/AzureLabs-Lab309-41.png)![](images/AzureLabs-Lab309-42.png)

12. Haga clic **en el símbolo + (más)** y escriba el nombre de etiqueta como **ObjectInScene**.

    ![Configuración de los objetos en la escena de Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Si usa un nombre diferente para la etiqueta, deberá asegurarse de que este cambio también se realiza en los scripts *DataFromAnalytics*, *ObjectTrigger* y *Gaze*, más adelante, para que los objetos se detecten y se detecten en la escena.

13. Con la etiqueta creada, ahora debe aplicarla a los tres objetos. En la jerarquía , mantenga presionada la tecla  **Mayús,** haga clic en los objetos **Desenlace,** Cubo y Esfera y, a continuación, en *inspector*, haga clic en el menú desplegable junto a Etiqueta y, a continuación, haga clic en la etiqueta *ObjectInScene* que creó. 

    ![Configuración de los objetos en la escena de Unity ](images/AzureLabs-Lab309-44.png)![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Capítulo 6: Creación de la clase ApplicationInsightsTracker

El primer script que debe crear **es ApplicationInsightsTracker,** que es responsable de:

1.  Creación de eventos basados en interacciones del usuario que se envían a Aplicación de Azure Ideas.

2. Crear nombres de eventos adecuados, en función de la interacción del usuario.

3. Envío de eventos a la instancia de Application Ideas Service.

Para crear esta clase:

1.  Haga clic con el botón derecho *en Project panel y,* a continuación, **en Crear**  >  **carpeta.** Asigne a la carpeta el nombre **Scripts**.

    ![Creación de la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Creación de la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  Una vez creada la carpeta **Scripts,** haga doble clic en ella para abrirla. A continuación, en esa carpeta, haga clic con el botón derecho en **Crear**  >  **script de C#.** Asigne al script el nombre **ApplicationInsightsTracker.**

3.  Haga doble clic en el nuevo script **ApplicationInsightsTracker** para abrirlo con **Visual Studio**.

4.  Actualice los espacios de nombres en la parte superior del script para que sean los siguientes:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  Dentro de la clase , inserte las siguientes variables:

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > Establezca los **valores instrumentationKey, applicationId y API_Key** correctamente, mediante las claves de servicio de Azure Portal, como se mencionó en el capítulo [1,](#chapter-1---the-azure-portal)paso 9 en adelante. 

6.  A continuación, **agregue los métodos Start()** y **Awake(),** a los que se llamará cuando se inicialice la clase:

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  Agregue los métodos responsables de enviar los eventos y las métricas registrados por la aplicación:

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*

## <a name="chapter-7---create-the-gaze-script"></a>Capítulo 7: Creación del script de mirada

El siguiente script que se va a crear es el script **Gaze.** Este script es responsable de crear un *raycast* que se proyectará hacia delante desde la cámara principal *para* detectar qué objeto está mirando el usuario. En este caso, *Raycast* deberá identificar si el usuario está mirando un objeto con la etiqueta **ObjectInScene** y, a continuación, contar cuánto tiempo mira ese objeto. 

1.  Haga doble clic en la **carpeta Scripts** para abrirlo.

2.  Haga clic con el botón derecho en la **carpeta Scripts** y haga clic **en Crear** script de  >  **C#.** Asigne al script el nombre **Gaze**.

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Reemplace el código existente por el siguiente:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  Ahora es necesario agregar código para los métodos **Awake()** y **Start().**

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  Dentro de **la clase Gaze,** agregue el código siguiente en el **método Update()** para proyectar un *Raycast* y detectar el destino alcanzado:

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  Agregue el **método ResetFocusedObject()** para enviar datos a **Application Ideas** cuando el usuario haya visto un objeto.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  Ya ha completado el script **de mirada.** Guarde los cambios en *Visual Studio* antes de volver a *Unity.*

## <a name="chapter-8---create-the-objecttrigger-class"></a>Capítulo 8: Creación de la clase ObjectTrigger

El siguiente script que debe crear es **ObjectTrigger,** que es responsable de:

- Agregar los componentes necesarios para la colisión con la cámara principal.
- Detectar si la cámara está cerca de un objeto etiquetado **como ObjectInScene**.

Para crear el script:

1.  Haga doble clic en la **carpeta Scripts** para abrirlo.

2.  Haga clic con el botón derecho en la **carpeta Scripts** y haga clic **en Crear** script de  >  **C#.** Asigne al script el nombre **ObjectTrigger.**

3.  Haga doble clic en el script para abrirlo con Visual Studio. Reemplace el código existente por el siguiente:

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Capítulo 9: Creación de la clase DataFromAnalytics

Ahora deberá crear el script **DataFromAnalytics,** que es responsable de:

- Captura de datos de análisis sobre el objeto al que se ha acercado más la cámara.
- Mediante las *claves de servicio*, que permiten la comunicación con la Aplicación de Azure Ideas service.
- Ordenar los objetos de la escena, según cuál tenga el mayor número de eventos.
- Cambiar el color del material, del objeto más abordado, a *verde.*

Para crear el script:

1.  Haga doble clic en la **carpeta Scripts** para abrirlo.

2.  Haga clic con el botón derecho en la **carpeta Scripts** y haga clic **en Crear** script de  >  **C#.** Asigne al script el nombre **DataFromAnalytics.**

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Inserte los siguientes espacios de nombres:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Dentro del script, inserte lo siguiente:

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  Dentro de **la clase DataFromAnalytics,** justo después del **método Start(),** agregue el siguiente método denominado **FetchAnalytics().** Este método es responsable de rellenar la lista de pares clave-valor, con *un GameObject* y un número de recuento de eventos de marcador de posición. A continuación, inicializa **la corrotina GetWebRequest().** La estructura de consulta de la llamada *a Application Ideas* también se puede encontrar dentro de este método, como el punto de conexión de la dirección URL *de* consulta.

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  Justo debajo **del método FetchAnalytics(),** agregue un método denominado **GetWebRequest()**, que devuelve un *IEnumerator*. Este método es responsable de solicitar el número de veces que se ha llamado a un evento correspondiente a un *GameObject* específico en *Application Ideas*. Cuando se devuelven todas las consultas enviadas, se llama al método **DetermineWinner().**

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  El método siguiente **es DetermineWinner(),** que ordena la lista de pares *GameObject* *e Int,* según el recuento de eventos más alto. A continuación, cambia el color material de *ese GameObject* a *verde* (como comentarios para que tenga el recuento más alto). Esto muestra un mensaje con los resultados del análisis.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  Agregue la estructura de clase que se usará para deserializar el objeto JSON, recibido de *Application Ideas*. Agregue estas clases en la parte inferior del archivo de clase **DataFromAnalytics,** **fuera de** la definición de clase.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*

## <a name="chapter-10---create-the-movement-class"></a>Capítulo 10: Creación de la clase Movement

El script **de** movimiento es el siguiente script que tendrá que crear. Es el responsable de:

- Mover la cámara principal según la dirección hacia la que mira la cámara.
- Agregar todos los demás scripts a objetos de escena.

Para crear el script:

1.  Haga doble clic en la **carpeta Scripts** para abrirlo.

2.  Haga clic con el botón derecho en **la carpeta Scripts** y haga clic en **Crear** script  >  **de C#.** Asigne al script el nombre **Movement**.

3.  Haga doble clic en el script para abrirlo con *Visual Studio*.

4.  Reemplace el código existente por el siguiente:

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  Dentro de **la clase Movement,** *debajo* del método **Update()** vacío, inserte los métodos siguientes que permiten al usuario usar el controlador de mano para moverse en el espacio virtual:

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  Por último, agregue la llamada al método dentro **del método Update().**

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity.*

## <a name="chapter-11---setting-up-the-scripts-references"></a>Capítulo 11: Configuración de las referencias de scripts

En este capítulo, debe colocar el script **de** movimiento en el elemento primario **de** la cámara y establecer sus destinos de referencia. A continuación, ese script controlará la colocación de los demás scripts donde deben estar.

1.  En la **carpeta Scripts** del panel *Project*, arrastre el script **Movement** (Movimiento) al objeto **Camera Parent** (Primario de la cámara), ubicado en el Panel *de jerarquía.*

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-48.png)

2.  Haga clic en el **elemento primario de la cámara.** En el *Panel de jerarquía,* arrastre el objeto **De la** derecha desde el *Panel* de jerarquía hasta el destino de referencia, **Controlador**, en el *Panel inspector*. Establezca Velocidad **de usuario** en **5,** como se muestra en la imagen siguiente.

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Capítulo 12: Compilación del proyecto de Unity

Ya se ha completado todo lo necesario para la sección de Unity de este proyecto, por lo que es el momento de compilarlo desde Unity.

1.  Vaya a **Compilación Configuración**, (  >  **Compilación de Configuración**).

2.  En la ventana **Compilar Configuración,** haga clic en **Compilar**.

    ![Compilación de la solución Project Unity en UWP](images/AzureLabs-Lab309-50.png)

3.  Aparecerá **Explorador de archivos** ventana emergente, en la que se le pedirá una ubicación para la compilación. Cree una nueva carpeta (haciendo clic en **Nueva carpeta en** la esquina superior izquierda) y asínquela **COMPILACIONES.**

    ![Compilación de la solución Project Unity en UWP](images/AzureLabs-Lab309-51.png)

    1.  Abra la nueva **carpeta BUILDS** y cree otra carpeta (con **Nueva** carpeta una vez más) y así mismo denle el nombre Mr Azure **Application \_ \_ \_ Ideas**.

        ![Compilación de la solución Project Unity en UWP](images/AzureLabs-Lab309-52.png)

    2.  Con la carpeta **Mr \_ Azure Application \_ \_ Ideas** seleccionada, haga clic **en Seleccionar carpeta.** El proyecto va a tardar un minuto más o menos en compilarse.

4.  Después *de compilar*, **Explorador de archivos** mostrará la ubicación del nuevo proyecto.

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>Capítulo 13: Implementación de MR_Azure_Application_Insights aplicación en la máquina

Para implementar la **aplicación Mr Azure Application \_ \_ \_ Ideas** en la máquina local:

1.  Abra el archivo de solución de la aplicación **\_ mr. de Azure \_ \_ Ideas** aplicación **en Visual Studio**.

2.  En la **Plataforma de soluciones,** **seleccione x86, Máquina local.**

3.  En Configuración **de la solución,** **seleccione Depurar**.

    ![Compilación de la solución Project Unity en UWP](images/AzureLabs-Lab309-53.png)

4.  Vaya al **menú Compilar y** haga clic en Deploy Solution **(Implementar solución)** para realizar la instalación local de la aplicación en el equipo.

5.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

6. Inicie la aplicación de realidad mixta.

7. Moverse por la escena, acercarse a los objetos y mirarlos, cuando *Azure Insight Service* haya recopilado suficientes datos de eventos, establecerá el objeto que más se ha acercado a verde.

> [!IMPORTANT] 
> Aunque el tiempo medio  de espera de los eventos y las métricas que recopila el servicio tarda aproximadamente 15 minutos, en algunas ocasiones puede tardar hasta 1 hora.

## <a name="chapter-14---the-application-insights-service-portal"></a>Capítulo 14: Portal de Application Ideas Service

Una vez que haya paseado por la escena y haya mirado varios objetos, puede ver los datos recopilados en el portal *de Application Ideas Service.*

1.  Vuelva al portal de Application Ideas Service.

2.  Haga clic *en Explorador de métricas*.

    ![Análisis de los datos recopilados](images/AzureLabs-Lab309-54.png)

3.  Se abrirá en una pestaña que contiene el gráfico que representa los eventos *y las métricas relacionados* con la aplicación. Como se mencionó anteriormente, los datos pueden tardar algún tiempo (hasta 1 hora) en mostrarse en el gráfico.

    ![Análisis de los datos recopilados](images/AzureLabs-Lab309-55.png)

4.  Haga clic en *la barra Eventos* en Total *de* eventos por versión de la aplicación para ver un desglose detallado de los eventos con sus nombres.

    ![Análisis de los datos recopilados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Ha finalizado la aplicación Application Ideas Service.

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha application Ideas Service para supervisar la actividad del usuario dentro de la aplicación.

![resultado del curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

**Ejercicio 1**

Intente generar, en lugar de crear manualmente, los objetos ObjectInScene y establezca sus coordenadas en el plano dentro de los scripts. De esta manera, podría preguntar a Azure cuál era el objeto más popular (ya sea a partir de la mirada o los resultados de proximidad) y generar uno *adicional* de esos objetos.

**Ejercicio 2**

Ordene los resultados Ideas aplicación por tiempo, de modo que obtenga los datos más relevantes e implemente esa información confidencial en la aplicación.