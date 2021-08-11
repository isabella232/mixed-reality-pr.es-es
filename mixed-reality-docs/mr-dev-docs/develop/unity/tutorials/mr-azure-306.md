---
title: 'HoloLens de primera generación y Azure (306): streaming de vídeo'
description: Complete este curso para aprender a implementar Azure Media Services dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, media services, streaming de vídeo, 360, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 3f3567c140c3162258475c28c2ef149039e3c40ed418ed2801ac8c40dda00a8f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224378"
---
# <a name="hololens-1st-gen-and-azure-306-streaming-video"></a>HoloLens (1.ª generación) y Azure 306: streaming de vídeo

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br> 

![final product -start ](images/AzureLabs-Lab6-00.png)
 ![ final product -start](images/AzureLabs-Lab6-01.png)

En este curso aprenderá a conectar su Azure Media Services a una experiencia de realidad virtual de Windows Mixed Reality para permitir la reproducción de vídeo en streaming de 360 grados en cascos envolventes. 

**Azure Media Services** son una colección de servicios que le ofrecen servicios de streaming de vídeo de calidad de difusión para llegar a públicos más grandes en los dispositivos móviles más populares de hoy en día. Para obtener más información, visite la [página Azure Media Services .](https://azure.microsoft.com/services/media-services)

Una vez completado este curso, tendrá una aplicación de casco envolvente de realidad mixta, que podrá hacer lo siguiente:

1. Recupere un vídeo de 360 grados de **un Azure Storage**, a través de Azure **Media Service**.

2. Muestra el vídeo recuperado de 360 grados dentro de una escena de Unity.

3. Navegue entre dos escenas, con dos vídeos diferentes.

En la aplicación, es usted el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con unity Project. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar la aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (306): Vídeo en streaming</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de escribir (mayo de 2018). Puede usar el software más reciente, como se muestra en el artículo instalación de las herramientas [,](../../install-the-tools.md)aunque no se debe suponer que la información de este curso coincida perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [Windows Mixed Reality envolvente envolvente (VR)](../../../discover/immersive-headset-hardware-details.md)
- Acceso a Internet para la instalación y recuperación de datos de Azure
- Dos vídeos de 360 grados en formato mp4 (puede encontrar algunos vídeos sin regalías [en esta página de descarga)](https://www.mettle.com/360vr-master-series-free-360-downloads-page)

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
2.  Configure y pruebe el casco envolvente Mixed Reality envolvente.

    > [!NOTE]
    > No necesitará **controladores** de movimiento para este curso. Si necesita soporte técnico para configurar el casco envolvente, haga clic en el vínculo sobre cómo [configurar Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Capítulo 1: Azure Portal: creación de la cuenta de Azure Storage

Para usar el **Azure Storage ,** deberá crear y configurar una cuenta de Storage **en** el Azure Portal.

1.  Inicie sesión en [Azure Portal](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida ayuda a su instructor o a uno de los procedimientos para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic **en Storage en** el menú izquierdo.

    ![Azure Storage Configuración de la cuenta](images/AzureLabs-Lab6-02.png)

3.  En la **pestaña Storage,** haga clic en **Agregar**.

    ![Azure Storage Configuración de la cuenta](images/AzureLabs-Lab6-03.png)

4.  En la **pestaña Crear cuenta de** almacenamiento:

    1.  Inserte un **nombre** para la cuenta, tenga en cuenta que este campo solo acepta números y letras minúsculas.

    2.  En **Modelo de implementación,** seleccione **Resource Manager.**

    3.  En **Tipo de cuenta,** **seleccione Storage (uso general v1)**.

    4.  En **Rendimiento,** seleccione **Estándar*.**

    5.  En **Replicación,** **seleccione Almacenamiento con redundancia local (LRS).**

    6.  Deje **Transferencia segura requerida como** **Deshabilitado.**

    7.  Seleccione una opción en **Suscripción**.

    8.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.

    9.  Determine la **ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

5.  Deberá confirmar que ha comprendido los Términos y condiciones aplicados a este servicio.

    ![Azure Storage Configuración de la cuenta](images/AzureLabs-Lab6-04.png)

6.  Una vez que haya hecho clic en **Crear**, tendrá que esperar a que se cree el servicio, esto puede tardar un minuto.

7.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Azure Storage Configuración de la cuenta](images/AzureLabs-Lab6-05.png)

8.  En este momento no es necesario seguir el recurso, simplemente pase al siguiente capítulo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capítulo 2: Azure Portal: creación de Media Service

Para usar Azure Media Service, deberá configurar una instancia del servicio para que esté disponible para la aplicación (donde el titular de la cuenta debe ser un administrador).

1.  En Azure Portal, haga clic en **Crear un** recurso en la esquina superior izquierda y busque Media **Service y** presione **Entrar.** El recurso que desea actualmente tiene un icono de color rojo; Haga clic en esta opción para mostrar una página nueva.

    ![Azure Portal](images/AzureLabs-Lab6-06.png)

2.  La nueva página proporcionará una descripción de **Media Service.** En la parte inferior izquierda de este símbolo del sistema, haga clic en **el botón** Crear para crear una asociación con este servicio.

    ![Azure Portal](images/AzureLabs-Lab6-07.png)

3.  Una vez que haya hecho clic en **Crear** un panel, aparecerá donde debe proporcionar algunos detalles sobre el nuevo servicio multimedia:

    1.  Inserte el nombre **de cuenta deseado para** esta instancia de servicio.

    2.  Seleccione una opción en **Suscripción**.

    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común. 
    
    > Si desea obtener más información sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar grupos de recursos de Azure.](/azure/azure-resource-manager/resource-group-portal)

    4.  Determine la **ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    5.  En la **Storage Cuenta,** haga clic en la sección Please select... (Seleccionar por **favor)** y, a continuación, haga clic en Storage **account** (Cuenta de Storage) que creó en el último capítulo.

    6.  También deberá confirmar que ha comprendido los Términos y condiciones aplicados a este servicio.

    7.  Haga clic en **Crear**.

        ![Azure Portal](images/AzureLabs-Lab6-08.png)

4.  Una vez que haya hecho clic en **Crear**, tendrá que esperar a que se cree el servicio, esto puede tardar un minuto.

5.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Azure Portal](images/AzureLabs-Lab6-09.png)

6.  Haga clic en la notificación para explorar la nueva instancia del servicio.

    ![Azure Portal](images/AzureLabs-Lab6-10.png)

7.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio.

8.  En la nueva página de Media Service, en el panel de la izquierda, haga clic en el vínculo **Activos,** que está a punto de la mitad del proceso.

9.  En la página siguiente, en la esquina superior izquierda de la página, haga clic **Upload**.

    ![Azure Portal](images/AzureLabs-Lab6-11.png)

10. Haga clic en **el icono Carpeta** para examinar los archivos y seleccione el primer vídeo de 360 que desea transmitir. 
    
    > Puede seguir este vínculo [para descargar un vídeo de ejemplo](https://vimeo.com/214401712).

    ![Azure Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Los nombres de archivo largos pueden causar un problema con el codificador: para asegurarse de que los vídeos no tienen problemas, considere la posibilidad de reducir la longitud de los nombres de los archivos de vídeo.

11. La barra de progreso se volverá verde cuando el vídeo haya terminado de cargarse.

    ![Azure Portal](images/AzureLabs-Lab6-13.png)

12. Haga clic en el texto anterior (**yourservicename - Assets**) para volver a la **página Activos.**

13. Observará que el vídeo se ha cargado correctamente. Haga clic en él.

    ![Azure Portal](images/AzureLabs-Lab6-14.png)

14. La página a la que se le redirige mostrará información detallada sobre el vídeo. Para poder usar el vídeo, debe codificarlo;  para ello, haga clic en el botón Codificar situado en la parte superior izquierda de la página.

    ![Azure Portal](images/AzureLabs-Lab6-15.png)

15. Aparecerá un nuevo panel a la derecha, donde podrá establecer opciones de codificación para el archivo. Establezca las siguientes propiedades (algunas ya estarán establecidas de forma predeterminada):

    1.  **Nombre del codificador *multimedia Media Encoder Standard***

    2.  **Codificación de *contenido preestablecido MP4 adaptable de velocidad de bits múltiple***

    3.  **Nombre de *trabajo Media Encoder Standard procesamiento de Video1.mp4***

    4.  **Nombre del recurso multimedia de *Video1.mp4 salida: Media Encoder Standard codificada***

        ![Azure Portal](images/AzureLabs-Lab6-16.png)

16. Haga clic en el botón **Crear**.

17. Observará una barra con el trabajo **Codificación** agregado, haga clic en esa barra y aparecerá un panel con el progreso de codificación que se muestra en ella.

    ![Azure Portal](images/AzureLabs-Lab6-17.png)

    ![Azure Portal](images/AzureLabs-Lab6-18.png)

18. Espere a que se complete el trabajo. Una vez hecho esto, no dude en cerrar el panel con la "X" en la parte superior derecha de ese panel.

    ![Azure Portal](images/AzureLabs-Lab6-19.png)

    ![Azure Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > El tiempo que tarda, depende del tamaño del archivo del vídeo. Este proceso puede tardar bastante tiempo.

19. Ahora que se ha creado la versión codificada del vídeo, puede publicarla para que sea accesible. Para ello, haga clic en el vínculo azul **Activos** para volver a la página de recursos.

    ![Azure Portal](images/AzureLabs-Lab6-21.png)

20. Verá el vídeo junto con otro, que es de tipo de recurso mp4 de **velocidad de bits _múltiple._**

    ![Azure Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Es posible que observe que el nuevo recurso, junto con el vídeo inicial, es Desconocido y tiene "0" bytes para su **tamaño,** solo tiene que actualizar la ventana para que se actualice. 

21. Haga clic en este nuevo recurso.

    ![Azure Portal](images/AzureLabs-Lab6-23.png)

22. Verá un panel similar al que usó antes, solo que se trata de un recurso diferente. Haga clic **en el** botón Publicar situado en la parte superior central de la página.

    ![Azure Portal](images/AzureLabs-Lab6-24.png)

23. Se le pedirá que establezca un **localizador**, que es el punto de entrada, en los archivos de los recursos. Para el escenario, establezca las siguientes propiedades:

    1.  **Tipo de localizador**  >  **Progresiva.**

    2.  La **fecha** **y hora** se establecerán por usted, desde la fecha actual, a una hora en el futuro (cien años en este caso). Déjelo tal y como está o cámbielo para que se adapte.

    > [!NOTE]
    > Para obtener más información sobre los localizadores y lo que puede elegir, visite la [documentación Azure Media Services .](/azure/media-services/media-services-concepts)

24. En la parte inferior de ese panel, haga clic en el **botón** Agregar.

    ![Azure Portal](images/AzureLabs-Lab6-25.png)

25. El vídeo ya está publicado y se puede transmitir mediante su punto de conexión. Más abajo de la página se encuentra **una sección** Archivos. Aquí es donde estarán las distintas versiones codificadas del vídeo. Seleccione la resolución más alta posible (en la imagen siguiente es el archivo 1920x960) y aparecerá un panel a la derecha. Allí encontrará una dirección **URL de descarga.** Copie este **punto de** conexión, ya que lo usará más adelante en el código.

    ![Azure Portal](images/AzureLabs-Lab6-26.png)    

    ![Azure Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > También puede presionar el botón **Reproducir** para reproducir el vídeo y probarlo.

26. Ahora debe cargar el segundo vídeo que usará en este laboratorio. Siga los pasos anteriores y repita el mismo proceso para el segundo vídeo. Asegúrese de copiar también el segundo **punto de** conexión. Use el vínculo [siguiente para descargar un segundo vídeo](https://vimeo.com/214402865).

27. Una vez publicados ambos vídeos, está listo para pasar al capítulo siguiente.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3: Configuración de unity Project

A continuación se muestra una configuración típica para desarrollar con la Mixed Reality y, como tal, es una buena plantilla para otros proyectos.

1.  Abra **Unity y** haga clic en **Nuevo.** 

    ![Azure Portal](images/AzureLabs-Lab6-28.png)

2.  Ahora deberá proporcionar un nombre de Project Unity, inserte **MR \_ 360VideoStreaming.**. Asegúrese de que el tipo de proyecto está establecido en **3D.** Establezca la ubicación en un lugar adecuado para usted (recuerde que más cerca de los directorios raíz es mejor). A continuación, haga **clic en Crear proyecto.**

    ![Azure Portal](images/AzureLabs-Lab6-29.png)

3.  Con Unity abierto, merece la pena comprobar que el **editor de scripts** predeterminado está establecido en **Visual Studio.** Vaya a **_Editar_ *preferencias*** y, a continuación, en la nueva ventana, vaya **a Herramientas externas.** Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![Azure Portal](images/AzureLabs-Lab6-30.png)

4.  A continuación, vaya a ***File* *Build Configuración*** (Compilación de archivos) y cambie la plataforma a Universal Windows **Platform**(Plataforma universal) haciendo clic en el botón Switch **Platform (Cambiar plataforma).**

5.  Asegúrese también de que:

    1. **El dispositivo de** destino se establece **en Cualquier dispositivo.**
    
    2.  **Tipo de** compilación se establece en **D3D.**

    3.  **El SDK** se establece en **Instalado más reciente.**

    4.  **Visual Studio versión está** establecida en **Instalado más reciente.**

    5.  **Build and Run (Compilar y** ejecutar) está establecido **en Local Machine (Máquina local).**

    6.  No se preocupe de configurar **Scenes** en este momento, ya que los configurará más adelante.

    7.  Por ahora, la configuración restante se debe dejar como predeterminada.

        ![Configuración de la aplicación unity Project](images/AzureLabs-Lab6-31.png)

6.  En la **ventana Build Configuración** (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra **el inspector.** 

7. En este panel, es necesario comprobar algunas configuraciones:

    1.  En la **pestaña Otros Configuración** datos:

        1.  **La versión** **del entorno de** ejecución de scripting debe ser **estable** (equivalente a .NET 3.5).

        2. **El back-end de** scripting debe **ser .NET.**

        3. **El nivel de compatibilidad de** api debe ser **.NET 4.6.**

            ![Configuración de la aplicación unity Project](images/AzureLabs-Lab6-32.png)

    2.  Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración**), marque **Virtual Reality Supported (Compatible con Virtual Reality)** y asegúrese de que se agrega el **SDK** Windows Mixed Reality virtual.

        ![Configuración de la aplicación unity Project](images/AzureLabs-Lab6-33.png)

    3.  En la **pestaña Configuración,** en **Funcionalidades**, compruebe:

        - **InternetClient**

            ![Configuración de la aplicación unity Project](images/AzureLabs-Lab6-34.png)

8.  Una vez que haya realizado esos cambios, cierre la **ventana Compilar Configuración** datos.

9.  Guarde la Project **Archivo* *Guardar Project**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capítulo 4: Importación del paquete InsideOutSphere Unity

> [!IMPORTANT]
> Si desea omitir el componente *De* configuración de Unity de este curso y continuar directamente en el código, no dude en descargar este [paquete .unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)importarlo en el proyecto como un paquete personalizado y, [**a**](https://docs.unity3d.com/Manual/AssetPackages.html)continuación, continuar desde el capítulo **5.** Todavía tendrá que crear una aplicación de Unity Project.

Para este curso, deberá descargar un paquete de recursos de Unity denominado [**InsideOutSphere.unitypackage.**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)

Cómo importar **unitypackage:**

1.  Con el panel de Unity delante  de usted, haga clic en Activos en el menú de la parte superior de la pantalla y, a continuación, haga clic en Importar **paquete > paquete personalizado.**

    ![Importación del paquete InsideOutSphere Unity](images/AzureLabs-Lab6-35.png)

2.  Use el selector de archivos para seleccionar el **paquete InsideOutSphere.unitypackage** y haga clic **en Abrir.** Se le mostrará una lista de componentes para este recurso. Para confirmar la importación, haga clic **en Importar**.

    ![Importación del paquete InsideOutSphere Unity](images/AzureLabs-Lab6-36.png)

3.  Una vez que haya terminado de importarse, observará que se han agregado tres carpetas nuevas, **Materials**, **Models** y **Prefabs,** a la **carpeta Assets.** Este tipo de estructura de carpetas es típico de un proyecto de Unity.

    ![Importación del paquete InsideOutSphere Unity](images/AzureLabs-Lab6-37.png)

    1.  Abra la **carpeta** Models y verá que se ha importado el modelo **InsideOutSphere.**

    2.  Dentro de **la carpeta Materials** encontrará el material *Lambert1* de **InsideOutSpheres,** junto con un material denominado *ButtonMaterial*, que se usa en GazeButton, que verá pronto.

    3.  La **carpeta Prefabs** contiene el objeto **prefab InsideOutSphere** que contiene el modelo **InsideOutSphere** *y* *GazeButton.*

    4.  **No se incluye ningún código,** para escribir el código siguiendo este curso.


4.  Dentro de **la jerarquía**, seleccione el **objeto Cámara** principal y actualice los componentes siguientes:

    1.  **Transformación**

        1.  Position = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotación = **X**: 0, **Y**: 0, **Z**: 0.

        3. Escala **X:** 1, **Y**: 1, **Z**: 1.

    2.  **Cámara**

        1. **Borrar marcas:** color sólido.

        2.  **Planes de recorte:** Cerca: 0,1, Lejos: 6.

            ![Importación del paquete InsideOutSphere Unity](images/AzureLabs-Lab6-38.png)

5.  Vaya a la **carpeta Prefab** y arrastre el prefab **InsideOutSphere** al Panel **de jerarquía.**

    ![Importación del paquete InsideOutSphere Unity](images/AzureLabs-Lab6-39.png)

6.  Expanda el **objeto InsideOutSphere** dentro de **la jerarquía** haciendo clic en la flecha pequeña situada junto a él. Verá un objeto **secundario debajo** de él denominado **GazeButton.** Esto se usará para cambiar las escenas y, por tanto, los vídeos.

    ![Importación del paquete InsideOutSphere Unity](images/AzureLabs-Lab6-40.png)

7.  En la ventana Inspector, haga clic en el componente Transform de **InsideOutSphere** y asegúrese de que se establecen las siguientes propiedades:

    |            |    TRANSFORMACIÓN: POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRANSFORMACIÓN: ROTACIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORMACIÓN: ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importación del paquete InsideOutSphere Unity](images/AzureLabs-Lab6-41.png)

8.  Haga clic en el objeto secundario **GazeButton** y establezca **su transformación** de la siguiente manera:

    |            |    TRANSFORMACIÓN: POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    TRANSFORMACIÓN: ROTACIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMACIÓN: ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importación del paquete InsideOutSphere Unity](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capítulo 5: Creación de la clase VideoController

La **clase VideoController** hospeda los dos puntos de conexión de vídeo que se usarán para transmitir el contenido desde Azure Media Service.

Para crear esta clase:

1.  Haga clic con el botón derecho en **la carpeta asset**, que se encuentra en el panel **Project** y haga clic en Crear **> carpeta**. Asigne a la carpeta el **nombre Scripts**.

    ![Creación de la clase VideoController](images/AzureLabs-Lab6-43.png)

    ![Creación de la clase VideoController](images/AzureLabs-Lab6-44.png)

2.  Haga doble clic en la **carpeta Scripts** para abrirlo.

3.  Haga clic con el botón derecho en la carpeta y, a continuación, haga clic **> script \# de C.** Asigne al script el nombre **VideoController.**

    ![Creación de la clase VideoController](images/AzureLabs-Lab6-45.png)

4.  Haga doble clic en el nuevo script **VideoController** para abrirlo **con Visual Studio 2017.**

    ![Creación de la clase VideoController](images/AzureLabs-Lab6-46.png)

5.  Actualice los espacios de nombres en la parte superior del archivo de código como se muestra a continuación:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Escriba las siguientes variables en la **clase VideoController,** junto con el **método Awake():**

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  Ahora es el momento de escribir los puntos de conexión de los vídeos de Azure Media Service:

    1.  El primero en la *variable video1endpoint.*
    
    2.  Segundo en la *variable video2endpoint.*

    > [!WARNING]
    > Hay un problema conocido con el uso *de https* en Unity, con la versión 2017.4.1f1. Si los vídeos proporcionan un error al reproducirse, pruebe a usar "http" en su lugar.

8.  A continuación, se debe editar el método **Start().** Este método se desencadenará cada vez que el usuario cambie de escena (por lo tanto, cambie el vídeo) mediante el botón de mirada.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Siguiendo el **método Start(),** inserte el método *IEnumerator* **PlayVideo(),** que se usará para iniciar vídeos sin problemas (por lo que no se ve ningúnttertter).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. El último método que necesita para esta clase es **el método ChangeScene(),** que se usará para intercambiar entre escenas.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > El **método ChangeScene()** usa una característica útil de C \# denominada operador *condicional*. Esto permite comprobar las condiciones y, a continuación, los valores devueltos en función del resultado de la comprobación, todo dentro de una sola instrucción. Siga este [vínculo para obtener más información sobre el operador condicional](/dotnet/csharp/language-reference/operators/conditional-operator).

11. Guarde los cambios en Visual Studio antes de volver a Unity.

12. De nuevo en el Editor de Unity, haga clic y arrastre la clase **VideoController** [from]{.underline} de la carpeta **Scripts** al objeto **Cámara** principal en el Panel **de** jerarquía.

13. Haga clic en **la cámara principal** y mire el panel **inspector**. Observará que dentro del componente script recién agregado, hay un campo con un valor vacío. Se trata de un campo de referencia, que tiene como destino las variables públicas dentro del código.

14. Arrastre el **objeto InsideOutSphere** desde el **Panel de** jerarquía a la ranura **de Sphere,** como se muestra en la imagen siguiente.

    ![Creación de la clase VideoController ](images/AzureLabs-Lab6-47.png)
     ![ Creación de la clase VideoController](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capítulo 6: Creación de la clase Gaze

Esta clase es responsable de crear un **raycast** que se proyectará hacia delante desde la cámara principal **para** detectar qué objeto está mirando el usuario. En este caso, **Raycast** deberá identificar si el usuario está mirando el objeto **GazeButton** en la escena y desencadenar un comportamiento.

Para crear esta clase:

1.  Vaya a la **carpeta Scripts** que creó anteriormente.

2.  Haga clic con el botón derecho **en Project** panel, **Crear* \# *Script C**. Asigne al script el nombre **Gaze**.

3.  Haga doble clic en el nuevo ***Gaze** _ script para abrirlo con _ *Visual Studio 2017.**

4.  Asegúrese de que el siguiente espacio de nombres está en la parte superior del script y quite cualquier otro:

    ```csharp
    using UnityEngine;
    ```

5.  A continuación, agregue las siguientes variables dentro de la **clase Gaze:**

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  Ahora es necesario agregar código para los métodos **Awake()** y **Start().**

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Agregue el código siguiente en el **método Update()** para proyectar un raycast y detectar el destino alcanzado:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Guarde los cambios en Visual Studio antes de volver a Unity.

9.  Haga clic en la **clase Gaze y** arrástrela desde la carpeta Scripts hasta el objeto Cámara principal del Panel **de** jerarquía.

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capítulo 7: Configuración de las dos escenas de Unity

El propósito de este capítulo es configurar las dos escenas, cada una que hospeda un vídeo para transmitir. Duplicará la escena que ya ha creado, de modo que no tenga que volver a configurarla, aunque después editará la nueva escena, de modo que el objeto *GazeButton* esté en una ubicación diferente y tenga una apariencia diferente. Esto es para mostrar cómo cambiar entre escenas.

1.  Para ello, vaya **a Archivo > Guardar escena como...**. Aparecerá una ventana guardar. Haga clic en **el botón Nueva** carpeta.

    ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-49.png)

2.  Asigne a la carpeta el nombre **Scenes**.

3.  La **ventana Guardar escena** seguirá abierta. Abra la carpeta **Scenes recién** creada.

4.  En el campo de texto Nombre **de archivo:** , escriba **VideoScene1** y, a continuación, presione **Guardar**.

5.  De nuevo en Unity, abra la **carpeta Scenes** y haga clic con el botón izquierdo en el **archivo VideoScene1.** Use el teclado y presione **Ctrl + D para** duplicar esa escena.

    > [!TIP]
    > El **comando Duplicate** también se puede realizar navegando a Editar > **Duplicado.**

6.  Unity incrementará automáticamente el número de nombres de escena, pero lo comprobará de todos modos para asegurarse de que coincide con el código insertado anteriormente.

    >  Debe tener **VideoScene1** y **VideoScene2**.

7.  Con las dos escenas, vaya a **File > Build Configuración**. Con la **ventana Build Configuración** (Compilar) abierta, arrastre las escenas a la sección Scenes in Build **(Escenas en compilación).**

    ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Puede seleccionar ambas escenas de la carpeta **Scenes** manteniendo presionado el **botón Ctrl** y, a continuación, hacer clic con el botón izquierdo en cada escena y, por último, arrastrar ambas.

8.  Cierre la **ventana Configuración** compilación y haga doble clic **en VideoScene2**.

9.  Con la segunda escena abierta, haga clic en el objeto secundario **GazeButton** de **InsideOutSphere** y establezca su transformación de la siguiente manera:

    |            |    TRANSFORMACIÓN: POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    TRANSFORMACIÓN: ROTACIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMACIÓN: ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Con el **elemento secundario GazeButton** aún seleccionado, mire **el inspector** y el filtro **de malla.** Haga clic en el pequeño destino situado junto al campo de referencia **Malla:**

    ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-51.png)

11. Aparecerá **una ventana** emergente Seleccionar malla. Haga doble clic **en la malla** Cubo de la lista de **recursos**.

    ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-52.png)

12. El **filtro de malla** se actualizará y ahora será un **cubo**. Ahora, haga clic en **el icono de** engranaje situado junto a **Colisionador de sphere** y haga clic en Quitar **componente** para eliminar el colisionador de este objeto.

    ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-53.png)

13. Con **GazeButton aún** seleccionado, haga clic en **el botón Agregar** componente situado en la parte inferior del **inspector.** En el campo de búsqueda, escriba **el** cuadro y **Box Collider** será una opción; haga clic en ella para agregar un colisionador de box **al** **objeto GazeButton.**

    ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-54.png)

14. **GazeButton** ahora está parcialmente actualizado, para que sea diferente; sin embargo, ahora creará un **nuevo material**, para que sea completamente diferente y sea más fácil de reconocer como un objeto diferente que el objeto de la primera escena.

15. Vaya a la **carpeta Materials** , en el panel **Project .** Duplique el material **buttonmaterial** (presione **Ctrl** D en el teclado o haga clic con el botón izquierdo en material y, a continuación, en la opción de menú Editar  +   archivo, **seleccione Duplicar).**  

    ![Capítulo 7: Configuración de las dos escenas de ](images/AzureLabs-Lab6-55.png)
     ![ Unity, capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-56.png)

16. Seleccione el nuevo **ButtonMaterial** Material (aquí denominado **ButtonMaterial 1)** y, en **inspector,** haga clic en la ventana de color **Albedo.** Aparecerá un elemento emergente, donde puede seleccionar otro color (elija el que quiera) y, a continuación, cierre el elemento emergente. El material será su propia instancia y será diferente del original.

    ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-57.png)

17. Arrastre el **nuevo material** al elemento secundario **GazeButton** para actualizar completamente su aspecto, de modo que se pueda distinguir fácilmente del botón de las primeras escenas.

    ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-58.png)

18. En este punto, puede probar el proyecto en el Editor antes de compilar el proyecto de UWP.

    -  Presione el **botón Reproducir** en el **editor** y use el casco.

        ![Capítulo 7: Configuración de las dos escenas de Unity](images/AzureLabs-Lab6-59.png)

19. Mire los dos objetos **GazeButton** para cambiar entre el primer y el segundo vídeo.

## <a name="chapter-8---build-the-uwp-solution"></a>Capítulo 8: Compilación de la solución para UWP

Una vez que se haya asegurado de que el editor no tiene errores, está listo para compilar.

Para compilar:

1.  Guarde la escena actual haciendo clic en **Archivo > Guardar**.

2.  Active la casilla denominada **Proyectos de Unity C \#** (esto es importante porque le permitirá editar las clases una vez completada la compilación).

3.  Vaya a **File > Build Configuración** y haga clic en Build **(Compilar).**

4.  Se le pedirá que seleccione la carpeta donde desea compilar la solución.

5.  Cree una **carpeta BUILDS** y, dentro de esa carpeta, cree otra carpeta con el nombre adecuado que prefiera.

6.  Haga clic en la nueva carpeta y, **a** continuación, haga clic en Seleccionar carpeta para elegir esa carpeta y comenzar la compilación en esa ubicación.

    ![Capítulo 8: Compilación de la solución para ](images/AzureLabs-Lab6-60.png)
     ![ UWP, capítulo 8: Compilación de la solución para UWP](images/AzureLabs-Lab6-61.png)

7.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una Explorador de archivos **en** la ubicación de la compilación.

## <a name="chapter-9---deploy-on-local-machine"></a>Capítulo 9: Implementación en la máquina local

Una vez completada la compilación, **aparecerá Explorador de archivos** ventana en la ubicación de la compilación. Abra la carpeta en la que llamó y creó y, a continuación, haga doble clic en el archivo de solución (.sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.

Lo único que queda por hacer es implementar la aplicación en el equipo (o en la *máquina local).*

Para implementar en la máquina local:

1.  En **Visual Studio 2017,** abra el archivo de solución que se acaba de crear.

2.  En la **Plataforma de soluciones,** **seleccione x86, Máquina local.**

3.  En Configuración **de la solución,** **seleccione Depurar**.

    ![Capítulo 9: Implementación en la máquina local](images/AzureLabs-Lab6-62.png)

4.  Ahora tendrá que restaurar los paquetes en la solución. Haga clic con el botón derecho en **la solución y** haga clic en Restaurar NuGet **paquetes para la solución...**

    > [!NOTE] 
    > Esto se hace porque los paquetes creados por Unity deben estar destinados para trabajar con las referencias de las máquinas locales.

5.  Vaya al **menú Compilar y** haga clic en Deploy Solution **(Implementar solución)** para realizar la instalación local de la aplicación en el equipo. Visual Studio compilará e implementará la aplicación.

6.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

    ![Capítulo 9: Implementación en la máquina local](images/AzureLabs-Lab6-63.png)

Al ejecutar la aplicación Mixed Reality, estará dentro del modelo **InsideOutSphere** que usó en la aplicación. Esta esfera será donde se transmitirá el vídeo, proporcionando una vista de 360 grados, del vídeo entrante (que se rodó para este tipo de perspectiva). No se sorprenda si el vídeo tarda un par de segundos en cargarse, la aplicación está sujeta a la velocidad de Internet disponible, ya que el vídeo debe capturarse y descargarse, por lo que se transmitirá a la aplicación.
Cuando esté listo, cambie las escenas y abra el segundo vídeo, para lo que debe mirar la esfera roja. A continuación, no dude en volver atrás con el cubo azul de la segunda escena.

## <a name="your-finished-azure-media-service-application"></a>La aplicación de Azure Media Service finalizada
 
Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Media Service para transmitir 360 vídeos.

![resultado del laboratorio](images/AzureLabs-Lab6-00.png)

![resultado del laboratorio](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

**Ejercicio 1**

Solo es posible usar una sola escena para cambiar los vídeos de este tutorial. Experimente con la aplicación y conséctela en una sola escena. Quizás incluso agregue otro vídeo a la combinación.

**Ejercicio 2**

Experimente con Azure y Unity e intente implementar la capacidad de la aplicación para seleccionar automáticamente un vídeo con un tamaño de archivo diferente, en función de la intensidad de una conexión a Internet.