---
title: 'HoloLens (1ª generación) y Azure 303: comprensión del lenguaje natural (LUIS)'
description: Complete este curso para aprender a implementar Azure Language Understanding Intelligence Service (LUIS) dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, language understanding intelligence service, luis, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 443b5f2c186fbbb0a3e979b48ccc20b4c3d3b4f0bd9c93950e27e1f86d610c07
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218245"
---
# <a name="hololens-1st-gen-and-azure-303-natural-language-understanding-luis"></a>HoloLens (1ª generación) y Azure 303: Comprensión del lenguaje natural (LUIS)

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro y que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

En este curso, aprenderá a integrar Language Understanding en una aplicación de realidad mixta mediante Azure Cognitive Services, con Language Understanding API.

![Resultado del laboratorio](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* es un servicio de Microsoft Azure, que proporciona a las aplicaciones la capacidad de hacer significado a través de la entrada del usuario, por ejemplo, mediante la extracción de lo que una persona podría querer, en sus propias palabras. Esto se logra a través del aprendizaje automático, que comprende y aprende la información de entrada y, a continuación, puede responder con información detallada y pertinente. Para más información, visite la [página de Azure Language Understanding (LUIS).](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)

Una vez completado este curso, tendrá una aplicación de casco envolvente de realidad mixta que podrá hacer lo siguiente:

1.  Capture la voz de entrada del usuario mediante el micrófono conectado al casco envolvente. 
2.  Envíe el dictado capturado a *Azure Language Understanding Intelligent Service* *(LUIS).* 
3.  Pida a LUIS que extraiga el significado de la información de envío, que se analizará, e intente determinar la intención de la solicitud del usuario.

El desarrollo incluirá la creación de una aplicación en la que el usuario podrá usar la voz o la mirada para cambiar el tamaño y el color de los objetos de la escena. No se cubrirá el uso de controladores de movimiento.

En la aplicación, es usted el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con su instancia de Unity Project. Es su trabajo usar los conocimientos que obtenga de este curso para mejorar la aplicación de realidad mixta.

Prepárese para entrenar a LUIS varias veces, que se trata en el [capítulo 12.](#chapter-12--improving-your-luis-service) Se obtienen mejores resultados cuantas más veces se haya entrenado LUIS.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>REALIDAD Y Azure 303: Comprensión del lenguaje natural (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en Windows Mixed Reality envolventes (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga el curso, verá notas sobre los cambios que podría necesitar emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algún eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de la escritura (mayo de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) como se muestra en el artículo Instalación de las herramientas, aunque no se debe suponer que la información de este curso coincidirá perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR).
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- Un [casco Windows Mixed Reality envolvente (VR)](../../../discover/immersive-headset-hardware-details.md) o Microsoft HoloLens con el modo de desarrollador habilitado [](/hololens/hololens1-hardware)
- Un conjunto de auriculares con un micrófono integrado (si el casco no tiene un micrófono y altavoces integrados)
- Acceso a Internet para la instalación de Azure y la recuperación de LUIS

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar problemas al compilar este proyecto, se recomienda encarecidamente crear el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación). 
2.  Para permitir que la máquina habilite dictado, vaya a Windows Configuración > Privacy > Speech (Privacidad > **Voz), Inking & Typing** (Escritura de &) y presione el botón **Turn On speech services and typing suggestions**(Activar servicios de voz y sugerencias de escritura).
3.  El código de este tutorial le permitirá grabar desde el dispositivo de **micrófono predeterminado** establecido en el equipo. Asegúrese de que el dispositivo de micrófono predeterminado está establecido como el que desea usar para capturar la voz.
4.  Si el casco tiene un micrófono integrado, asegúrese de que la opción "Cuando uso el casco, cambie al micrófono del *casco"* esté activada en la configuración *Portal de realidad mixta* casco.

    ![Configuración de cascos envolventes](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capítulo 1: Configuración de Azure Portal

Para usar *el Language Understanding* en Azure, deberá configurar una instancia del servicio para que esté disponible para la aplicación.

1.  Inicie sesión en [Azure Portal](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los proctores para configurar la nueva cuenta.

2.  Una vez que haya  iniciado sesión, haga clic en Nuevo en la esquina superior izquierda y busque Language Understanding *y* haga clic en **Entrar.** 

    ![Creación de un recurso de LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > Es posible que **la** palabra Nuevo se haya reemplazado **por Crear un recurso** en los portales más recientes.
 
3.  La nueva página de la derecha proporcionará una descripción de la Language Understanding servicio. En la parte inferior izquierda de esta página, seleccione el **botón** Crear para crear una instancia de este servicio.

    ![Creación del servicio LUIS: aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  Una vez que haya hecho clic en Crear:

    1. Inserte el nombre **deseado para** esta instancia de servicio.
    2. Seleccione una opción en **Suscripción**.
    3. Seleccione el **plan de** tarifa adecuado para usted; si es la primera vez que crea un servicio *de LUIS,* debe estar disponible un nivel gratuito (denominado F0). La asignación gratuita debe ser más que suficiente para este curso.
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común. 

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. Determine la **ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    6. También deberá confirmar que ha comprendido los términos y condiciones aplicados a este servicio.
    7. Seleccione **Crear**.

        ![Creación del servicio LUIS: entrada del usuario](images/AzureLabs-Lab3-03.png)
 
5.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.
6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal. 
 
    ![Nueva imagen de notificación de Azure](images/AzureLabs-Lab3-04.png)

7.  Haga clic en la notificación para explorar la nueva instancia de servicio.

    ![Notificación de creación de recursos correcta](images/AzureLabs-Lab3-05.png)
 
8.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia de servicio de LUIS. 
 
    ![Acceso a claves de LUIS](images/AzureLabs-Lab3-06.png)

9.  En este tutorial, la aplicación tendrá que realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio.
10. En  la página Inicio rápido, del servicio de API de *LUIS,* vaya al primer *paso,* Tomar las claves y haga clic en Claves **(también** puede hacerlo haciendo clic en el hipervínculo azul Claves, que se encuentra en el menú de navegación de servicios, que se indica mediante el icono de clave). Esto revelará las claves de *servicio*.
11. Tome una copia de una de las claves mostradas, ya que la necesitará más adelante en el proyecto. 
12. En la *página Servicio,* haga clic en *Language Understanding Portal* para que se le redirija a la página web que usará para crear el nuevo servicio, dentro de la aplicación de LUIS. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capítulo 2: El portal de Language Understanding

En esta sección aprenderá a crear una aplicación de LUIS en el portal de LUIS. 

> [!IMPORTANT]
> Tenga en cuenta que la configuración de *entidades,* intenciones y *expresiones* dentro de este capítulo es solo el primer paso para compilar el servicio LUIS: también deberá volver a entrenar el servicio varias veces, para que sea más preciso.  El reentrenamiento del servicio se trata en [el último capítulo](#chapter-12--improving-your-luis-service) de este curso, así que asegúrese de completarlo.

1.  Al llegar a *Language Understanding Portal,* es posible que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que su Azure Portal. 

    ![Página de inicio de sesión de LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Si es la primera vez que usa LUIS, deberá desplazarse hacia abajo hasta la parte inferior de la página principal para buscar y hacer clic en el botón Crear **aplicación de LUIS.**

    ![Página Crear aplicación de LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Una vez que haya iniciado sesión, **haga Mis aplicaciones** (si no está en esa sección actualmente). A continuación, puede hacer clic **en Crear nueva aplicación.**

    ![LUIS: imagen de mis aplicaciones](images/AzureLabs-Lab3-09.png)
 
4.  Asigne un nombre a la *aplicación.*
5.  Si la aplicación debe entender un idioma diferente del inglés, debe cambiar *la referencia cultural* al idioma adecuado.
6.  Aquí también puede agregar una *descripción de* la nueva aplicación de LUIS.

    ![LUIS: creación de una aplicación](images/AzureLabs-Lab3-10.png)

7.  Una vez que **presione Listo,** entrará en la *página Compilación* de la nueva *aplicación de LUIS.*
8.  Hay algunos conceptos importantes que comprender aquí:

    -   *Intención*, representa el método al que se llamará después de una consulta del usuario. Una *intención* puede tener una o varias *entidades*.
    -   *La* entidad , es un componente de la consulta que describe la información relevante para *la intención*.
    -   *Las expresiones* son ejemplos de consultas proporcionadas por el desarrollador que LUIS usará para entrenarse a sí mismo.

Si estos conceptos no están perfectamente claros, no se preocupe, ya que este curso los aclarará aún más en este capítulo.

Comenzará por crear las *entidades necesarias* para compilar este curso.

9.  En el lado izquierdo de la página, haga clic en *Entidades* y, a continuación, haga clic **en Crear nueva entidad.**

    ![Creación de una entidad](images/AzureLabs-Lab3-11.png)

10. Llame al nuevo color de *entidad,* establezca su tipo en *Simple y,* a continuación, presione **Listo.**

    ![Creación de una entidad simple: color](images/AzureLabs-Lab3-12.png)
 
11. Repita este proceso para crear tres (3) entidades simples más denominadas:

    -   *upsize*
    -   *Downsize*
    -   *Destino*

El resultado debe ser parecido a la imagen siguiente:

![Resultado de la creación de entidades](images/AzureLabs-Lab3-13.png)
 
En este momento puede empezar a crear *intents*. 

> [!WARNING]
> No elimine la **intención None.**

12. En el lado izquierdo de la página, haga clic en **Intents (Intenciones)** y, a continuación, haga clic **en Create new intent (Crear nueva intención).**

    ![Creación de nuevas intenciones](images/AzureLabs-Lab3-14.png)

13. Llame al nuevo *objeto Intent* **ChangeObjectColor.**

    > [!IMPORTANT]
    > Este *nombre* de intención se usa en el código más adelante en este curso, por lo que para obtener mejores resultados, use este nombre exactamente como se proporciona.

Una vez que confirme el nombre, se le dirigirá a la página Intenciones.

![LUIS: página de intenciones](images/AzureLabs-Lab3-15.png)

Observará que hay un cuadro de texto que le pide que escriba 5 o más *expresiones diferentes.*

> [!NOTE]
> LUIS convierte todas las expresiones en minúsculas.

14. Inserte la siguiente *expresión en* el cuadro de texto superior (actualmente con el texto Escriba *unos 5 ejemplos...* ), y presione **Entrar**:

```
The color of the cylinder must be red
```

Observará que la nueva *expresión aparecerá en* una lista debajo.

Después del mismo proceso, inserte las seis (6) expresiones siguientes:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Para cada expresión que ha creado, debe identificar qué palabras debe usar LUIS como entidades. En este ejemplo, debe etiquetar todos los colores como una entidad *de color* y toda la referencia posible a un destino como entidad *de* destino.

15. Para ello, intente hacer clic en la palabra *cilindro* en la primera expresión y seleccione *destino*.

    ![Identificar destinos de expresión](images/AzureLabs-Lab3-16.png)
 
16. Ahora haga clic en la *palabra rojo* en la primera expresión y seleccione *el color*.

    ![Identificar entidades de expresión](images/AzureLabs-Lab3-17.png)
 
17. Etiquete también la línea siguiente, donde *el cubo* debe ser un *destino* y *el negro* debe ser un *color*. Observe también el uso de las palabras *"this",* *"it"* y *"this object",* que se proporcionan, por lo que también hay disponibles tipos de destino no específicos. 

18. Repita el proceso anterior hasta que todas las expresiones tengan etiquetadas las entidades. Consulte la imagen siguiente si necesita ayuda.

    > [!TIP]
    > Al seleccionar las palabras que quiere etiquetar como entidades:
    > - Para palabras únicas, solo tiene que hacer clic en ellas.
    > - Para un conjunto de dos o más palabras, haga clic al principio y, a continuación, al final del conjunto.

    > [!NOTE]
    > Puede usar el botón de *alternancia Vista* de tokens para cambiar entre **entidades y vistas de tokens.**

19. Los resultados deben ser los que se muestran en las imágenes siguientes, en las que se **muestra la vista Entidades o tokens**:

    ![Tokens & vistas de entidades](images/AzureLabs-Lab3-18.png)
  
20. En este punto, presione el **botón Train** (Entrenar) situado en la parte superior derecha de la página y espere a que el pequeño indicador de redondeo que contiene se vuelva verde. Esto indica que LUIS se ha entrenado correctamente para reconocer esta intención.

    ![Entrenamiento de LUIS](images/AzureLabs-Lab3-19.png)
 
21. Como ejercicio, cree una nueva intención denominada **ChangeObjectSize**, con el destino *Entities*, *upsize* y *downsize*.
22. Siguiendo el mismo proceso que la intención anterior, inserte las ocho (8) expresiones siguientes para *cambio de* tamaño:

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. El resultado debe ser como el de la imagen siguiente:

    ![Configuración de las entidades o tokens ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. Una vez creadas y entrenadas ambas intenciones, **ChangeObjectColor** y **ChangeObjectSize,** haga clic en el botón **PUBLICAR** en la parte superior de la página.

    ![Publicación del servicio LUIS](images/AzureLabs-Lab3-21.png)

25. En la *página* Publicar, finalizará y publicará la aplicación de LUIS para que el código pueda acceder a ella.

    1. Establezca la lista desplegable *Publicar en* como **Producción.**
    2. Establezca la *zona horaria* en la zona horaria.
    3. Active la casilla **Incluir todas las puntuaciones de intención predichos.**
    4. Haga clic **en Publicar en el espacio de producción.**

        ![Configuración de publicación](images/AzureLabs-Lab3-22.png)

26. En la sección *Recursos y claves*:

    1.  Seleccione la región que estableció para la instancia de servicio en Azure Portal.
    2.  Observará un **Starter_Key** siguiente, ignór guardarlo.
    3.  Haga clic **en Agregar** clave e inserte *la clave* que obtuvo en Azure Portal cuando creó la instancia de servicio. Si azure y el portal de LUIS han iniciado sesión en el mismo usuario, se le  proporcionan menús desplegables para Nombre de *inquilino,* Nombre de suscripción y Clave que desea usar (tendrá el mismo nombre que proporcionó anteriormente en Azure Portal. 

    > [!IMPORTANT] 
    > Debajo *de* Punto de conexión , tome una copia del punto de conexión correspondiente a la clave que ha insertado; pronto la usará en el código.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capítulo 3: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity y* haga clic en **Nuevo.** 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab3-24.png)

2.  Ahora deberá proporcionar un nombre de Project Unity e insertar **MR_LUIS**. Asegúrese de que el tipo de proyecto está establecido en **3D.** Establezca Ubicación **en un** lugar adecuado para usted (recuerde que es mejor estar más cerca de los directorios raíz). A continuación, haga **clic en Crear proyecto.**

    ![Proporcione detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a Editar > preferencias y, a continuación, en la nueva ventana, vaya a **Herramientas externas**. Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab3-26.png)
 
4.  A continuación, vaya a **File > Build Configuración and switch** the platform to Universal Windows **Platform**(Plataforma Windows universal) haciendo clic en el **botón Cambiar** plataforma.

    ![Cree Configuración ventana y cambie la plataforma a UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Vaya a **Archivo > compilación Configuración** y asegúrese de que:

    1. **Dispositivo de destino** está establecido en **Cualquier dispositivo**

        > Para la Microsoft HoloLens, establezca **Dispositivo de destino** en *HoloLens*.

    2. **Tipo de** compilación se establece en **D3D**
    3. **El SDK** se establece en **Instalado más reciente.**
    4. **Visual Studio versión está** establecida en **La versión más reciente instalada**
    5. **Build and Run (Compilar y** ejecutar) está establecido en **Local Machine (Máquina local).**
    6. Guarde la escena y agrégréla a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.
        
            ![Haga clic en el botón Agregar escenas abiertas.](images/AzureLabs-Lab3-28.png)

        2. Cree una nueva carpeta para esta y cualquier  escena futura y, a continuación, seleccione el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![Creación de una nueva carpeta de scripts](images/AzureLabs-Lab3-29.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo *Nombre* de archivo: texto, **escriba MR_LuisScene** y, a continuación, **presione Guardar.**

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab3-30.png)

    7. El resto de la configuración, *en Build Configuración*, se debe dejar como valor predeterminado por ahora.

6. En la *ventana Build Configuración* (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra *el inspector.* 

    ![Abra la configuración del reproductor.](images/AzureLabs-Lab3-31.png) 
 
7. En este panel, es necesario comprobar algunas configuraciones:

    1. En la **pestaña Otros Configuración** datos:

        1. **La versión del entorno de** ejecución de scripting debe ser **estable** (equivalente a .NET 3.5).
        2. **El back-end de** scripting debe **ser .NET**
        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![Actualice otras opciones.](images/AzureLabs-Lab3-32.png)
      
    2. En la **pestaña Configuración,** en **Funcionalidades**, compruebe:

        1. **InternetClient**
        2. **Micrófono**

            ![Actualización de la configuración de publicación.](images/AzureLabs-Lab3-33.png)

    3. Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración**), marque **Virtual Reality Supported (Compatible con Virtual Reality)** y asegúrese de que se agrega el **SDK** Windows Mixed Reality virtual.

        ![Actualice el X R Configuración.](images/AzureLabs-Lab3-34.png)

8.  De nuevo en *build Configuración* Unity C# Projects (Proyectos de C# de _Unity)_ ya no está en gris; Marque la casilla situada junto a esto. 
9.  Cierre la ventana Build Settings (Configuración de compilación).
10. Guarde la escena y Project (**FILE > SAVE SCENE /FILE > SAVE PROJECT**).

## <a name="chapter-4--create-the-scene"></a>Capítulo 4: Creación de la escena

> [!IMPORTANT]
> Si desea omitir el componente De configuración de *Unity* de este curso y continuar directamente en el código, no dude en descargar este [paquete de Unity,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)importarlo en el proyecto como un paquete personalizado y, a continuación, continuar desde el capítulo [5.](#chapter-5--create-the-microphonemanager-class) [](https://docs.unity3d.com/Manual/AssetPackages.html) 

1.  Haga clic con el botón derecho en un área vacía del *Panel de* jerarquía, en **Objeto 3D**, agregue un **plano**.

    ![Cree un plano.](images/AzureLabs-Lab3-35.png)

2.  Tenga en cuenta que al  hacer clic con el botón derecho en la jerarquía de nuevo para crear más objetos, si todavía tiene seleccionado el último objeto, el objeto seleccionado será el elemento primario del nuevo objeto. Evite hacer clic con el botón izquierdo en un espacio vacío dentro de la jerarquía y, a continuación, haga clic con el botón derecho.

3.  Repita el procedimiento anterior para agregar los objetos siguientes:

    1. *Sphere*
    2. *Cilindro*
    3. *Cubo*
    4. *Texto 3D*

4.  La jerarquía de *escena resultante* debe ser como la de la imagen siguiente:

    ![Configuración de la jerarquía de escena.](images/AzureLabs-Lab3-36.png)
 
5.  Haga clic con **el** botón izquierdo en la cámara principal para seleccionarla y, en el panel *inspector,* verá el objeto Cámara con todos sus componentes.
6.  Haga clic en **el botón Agregar** componente situado en la parte inferior del panel *inspector*.

    ![Agregar origen de audio](images/AzureLabs-Lab3-37.png)
 
7.  Busque el componente denominado *Origen de audio*, como se muestra anteriormente.
8.  Asegúrese también de  que el componente Transformar de la cámara principal está establecido en (0,0,0),  para ello, presione el icono de engranaje situado junto al componente Transformación de la cámara y seleccione **Restablecer**.  A *continuación,* el componente Transformar debe tener el siguiente aspecto:

    1.  *La* posición se establece **en 0, 0, 0**.
    2.  *La* rotación se establece **en 0, 0, 0**.

    > [!NOTE] 
    > Para la Microsoft HoloLens, también tendrá que cambiar lo siguiente, que forman parte del componente **Cámara,** que se encuentra en la **cámara principal**:
    > - **Borrar marcas:** Color sólido.
    > - **Fondo** "Negro, Alfa 0": color hexadecimal: #00000000.

9.  Haga clic con el botón izquierdo **en el plano** para seleccionarlo. En el *panel inspector,* establezca *el componente Transformar* con los valores siguientes:

    |   Eje X    | Eje Y |   Eje Z    |
    |:-----:|:----------------------:|:-----:|
    | 0     | -1                     | 0     |


10. Haga clic con el botón izquierdo **en sphere** para seleccionarlo. En el *panel inspector,* establezca *el componente Transformar* con los valores siguientes:

    |   Eje X    | Eje Y |   Eje Z    |
    |:-----:|:----------------------:|:-----:|
    | 2     | 1                      | 2     |

11. Haga clic a la izquierda **en el cilindro** para seleccionarlo. En el *panel inspector,* establezca *el componente Transformar* con los valores siguientes:

    |   Eje X    | Eje Y |   Eje Z    |
    |:-----:|:----------------------:|:-----:|
    | -2    | 1                      | 2     |

12. Haga clic con el botón **izquierdo en el** cubo para seleccionarlo. En el *panel inspector,* establezca *el componente Transformar* con los valores siguientes:

    |        | Transformación: *posición* |       |  \| |       | Transformación: *rotación* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **S**                   | **Z** |  \| | **X** | **S**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Haga clic con el botón izquierdo **en el objeto Nuevo** texto para seleccionarlo. En el *panel inspector,* establezca *el componente Transformar* con los valores siguientes:

    |       | Transformación: *posición* |       |  \| |       | Transformación: *escala* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **S**                  | **Z** |  \| | **X** | **S**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0,1   | 0,1                 | 0,1   | 

14. Cambie **el tamaño de** fuente del componente Text **Mesh** a **50**.
15. Cambie el *nombre* del objeto **Text Mesh** a **Dictation Text**.

    ![Creación de un objeto Text 3D](images/AzureLabs-Lab3-38.png)
 
16. La estructura del Panel de jerarquía debe tener ahora el siguiente aspecto:

    ![malla de texto en la vista de escena](images/AzureLabs-Lab3-38b.png)


17. La escena final debe ser como la imagen siguiente:

    ![Vista de escena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capítulo 5: Creación de la clase MicrophoneManager

El primer script que va a crear es la *clase MicrophoneManager.* A continuación, creará la clase *LuisManager*, la clase *Comportamientos* y, por último, la clase *Gaze* (no dude en crear todas ellas ahora, aunque se tratarán a medida que llegue a cada capítulo).

La *clase MicrophoneManager* es responsable de:

-   Detectar el dispositivo de grabación conectado al casco o la máquina (el que sea el predeterminado).
-   Capture el audio (voz) y use el dictado para almacenarlo como una cadena.
-   Una vez que la voz se haya pausado, envíe el dictado a la *clase LuisManager.* 

Para crear esta clase: 

1.  Haga clic con el botón derecho *en Project panel*, cree > **carpeta**. Llame a la carpeta **Scripts**. 

    ![Cree la carpeta Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  Con la **carpeta Scripts** creada, haga doble clic en ella para abrirla. A continuación, dentro de esa carpeta, haga clic con el botón derecho **en Crear > script de C#.** Asigne al script el nombre *MicrophoneManager.* 

3.  Haga doble clic *en MicrophoneManager* para abrirlo con *Visual Studio*.
4.  Agregue los siguientes espacios de nombres a la parte superior del archivo:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  A continuación, agregue las siguientes variables dentro de *la clase MicrophoneManager:*

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  Ahora es necesario agregar código para los métodos *Awake()* y *Start().* Se llamará a estos cuando se inicialice la clase:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  Ahora necesita el método que usa la aplicación para iniciar y detener la captura de voz y pasarla a la clase *LuisManager,* que compilará pronto. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  Agregue un *controlador de dictado que* se invocará cuando se detenga la voz. Este método pasará el texto de dictado a la *clase LuisManager.*

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > Elimine el *método Update(),* ya que esta clase no lo usará.

9.  Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*

    > [!NOTE]
    > En este momento observará que aparece un error en el panel de consola *del editor de Unity.* Esto se debe a que el código hace referencia *a la clase LuisManager* que creará en el capítulo siguiente.

## <a name="chapter-6--create-the-luismanager-class"></a>Capítulo 6: Creación de la clase LUISManager

Es el momento de crear la clase *LuisManager,* que realizará la llamada al servicio de Luis de Azure. 

El propósito de esta clase es recibir el texto de dictado de la clase *MicrophoneManager* y enviarlo a la API de *Azure Language Understanding que* se va a analizar.

Esta clase deserializará la *respuesta JSON* y llamará a los *métodos adecuados* de la clase Behaviours para desencadenar una acción.

Para crear esta clase: 

1.  Haga doble clic en **la carpeta Scripts** para abrirlo. 
2.  Haga clic con el botón derecho en **la carpeta Scripts** y haga clic > script de **C#.** Asigne al script el nombre *LuisManager.* 
3.  Haga doble clic en el script para abrirlo con Visual Studio.
4.  Agregue los siguientes espacios de nombres a la parte superior del archivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Comenzará por crear tres  clases dentro de la clase *LuisManager* (dentro del mismo archivo de script, por encima del *método Start()* que representará la respuesta JSON deserialización de Azure.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  A continuación, agregue las siguientes variables dentro de la *clase LuisManager:*
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Asegúrese de colocar el punto de conexión de LUIS en ahora (que tendrá desde el portal de LUIS).

8.  Ahora es necesario agregar código para el método *Awake().* Se llamará a este método cuando se inicialice la clase:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Ahora necesita los métodos que usa esta aplicación para enviar el dictado recibido de la clase *MicrophoneManager* a *LUIS* y, a continuación, recibir y deserializar la respuesta. 
10. Una vez determinado el valor de intent y las entidades asociadas, se pasan a la instancia de la clase *Behaviours* para desencadenar la acción prevista.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. Cree un nuevo método denominado *AnalyseResponseElements()* que leerá *el elemento AnalysedQuery resultante* y determinará las entidades. Una vez determinadas esas entidades, se pasarán a la instancia de la *clase De comportamientos* que se usará en las acciones.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > Elimine los *métodos Start()* *y Update(),* ya que esta clase no los usará.

12. Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*

> [!NOTE]
> En este momento observará que aparecen varios errores en el panel de consola *del editor de Unity.* Esto se debe a que el código hace referencia *a la clase Comportamientos* que creará en el capítulo siguiente.

## <a name="chapter-7--create-the-behaviours-class"></a>Capítulo 7: Creación de la clase De comportamientos

La *clase Behaviours* desencadenará las acciones mediante las entidades proporcionadas por la *clase LuisManager.*

Para crear esta clase: 

1.  Haga doble clic en **la carpeta Scripts** para abrirlo. 
2.  Haga clic con el botón derecho en **la carpeta Scripts** y haga clic > script de **C#.** Asigne al script *el nombre Comportamientos.* 
3.  Haga doble clic en el script para abrirlo con *Visual Studio*.
4.  A continuación, agregue las siguientes variables dentro *de la clase Behaviours:*

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Agregue el *código del método Awake().* Se llamará a este método cuando se inicialice la clase:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  La clase *LuisManager* (que creó anteriormente) llama a los métodos siguientes para determinar qué objeto es el destino de la consulta y, a continuación, desencadenar la acción adecuada.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  Agregue el *método FindTarget()* para determinar cuál de *los GameObjects* es el destino de la intención actual. Este método establece de forma predeterminada que el *destino gameObject* se "mire" si no se define ningún destino explícito en las entidades.

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > Elimine los *métodos Start()* *y Update(),* ya que esta clase no los usará.

8.  Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*

## <a name="chapter-8--create-the-gaze-class"></a>Capítulo 8: Creación de la clase Gaze

La última clase que necesitará para completar esta aplicación es la *clase Gaze.* Esta clase actualiza la referencia a *GameObject* actualmente en el foco visual del usuario.

Para crear esta clase: 

1.  Haga doble clic en **la carpeta Scripts** para abrirlo. 
2.  Haga clic con el botón derecho en **la carpeta Scripts** y haga clic > script de **C#.** Asigne al script el nombre *Gaze*. 
3.  Haga doble clic en el script para abrirlo con *Visual Studio*.
4.  Inserte el código siguiente para esta clase:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*

## <a name="chapter-9--completing-the-scene-setup"></a>Capítulo 9: Finalización de la configuración de la escena

1.  Para completar la configuración de la escena, arrastre cada script que haya creado desde la carpeta Scripts hasta el objeto **Cámara** principal del *Panel de jerarquía*.
2.  Seleccione la **cámara** principal y observe el *Panel del inspector,* debería poder ver cada script que ha adjuntado y observará que hay parámetros en cada script que aún no se han establecido.

    ![Establecer los destinos de referencia de la cámara.](images/AzureLabs-Lab3-41.png)

3.  Para establecer estos parámetros correctamente, siga estas instrucciones:

    1. *MicrophoneManager*:

        - En el *Panel de jerarquía,* arrastre el **objeto Texto de dictado** al cuadro Valor del parámetro **Texto** de dictado.

    2. *Comportamientos*, desde el *Panel de jerarquía*:

        - Arrastre el **objeto Sphere** al cuadro *Destino de* referencia de Sphere.
        - Arrastre el **cilindro al** cuadro Destino de referencia *de* cilindro.
        - Arrastre el **cubo al** cuadro *Destino de* referencia de cubo.

    3. *Mirada:*

        - Establezca distancia *máxima de mirada* en **300** (si aún no lo está). 

4.  El resultado debe ser parecido a la imagen siguiente:

    ![Mostrar los destinos de referencia de la cámara, ahora establecidos.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capítulo 10: Prueba en el editor de Unity

Compruebe que la configuración de la escena está correctamente implementada.

Asegúrese de que:

-   Todos los scripts están asociados al **objeto Cámara** principal. 
-   Todos los campos del *panel inspector de la* cámara principal se asignan correctamente.

1.  Presione el **botón Reproducir** en el Editor *de Unity.* La aplicación debe ejecutarse dentro del casco envolvente conectado.

2.  Pruebe algunas expresiones, como:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Si ve un error en la consola de Unity sobre el cambio predeterminado del dispositivo de audio, es posible que la escena no funcione según lo previsto. Esto se debe a la forma en que el portal de realidad mixta trata los micrófonos integrados para los cascos que los tienen. Si ve este error, simplemente detenga la escena e inténtenla de nuevo y las cosas deberían funcionar según lo previsto.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capítulo 11: Compilación y instalación local de la solución para UWP

Una vez que haya asegurado que la aplicación funciona en el Editor de Unity, estará listo para compilar e implementar.

Para compilar:

1.  Guarde la escena actual haciendo clic en **Archivo > Guardar**.
2.  Vaya a **Archivo > compilación Configuración**.
3.  Marque el cuadro denominado **Proyectos de C#** de Unity (útil para ver y depurar el código una vez creado el proyecto de UWP.
4.  Haga clic en **Agregar escenas abiertas** y, a continuación, haga clic **en Compilar.**

    ![Ventana de Configuración compilación](images/AzureLabs-Lab3-43.png)

4.  Se le pedirá que seleccione la carpeta donde desea compilar la solución. 

5.  Cree una *carpeta BUILDS* y, dentro de esa carpeta, cree otra carpeta con el nombre adecuado que prefiera. 
6.  Haga **clic en Seleccionar** carpeta para comenzar la compilación en esa ubicación.
 
    ![Create Builds Folder (Crear carpeta de ](images/AzureLabs-Lab3-44.png)
     ![ compilaciones), seleccione Builds Folder (Carpeta de compilaciones).](images/AzureLabs-Lab3-45.png)
 
7.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), debería abrir una Explorador de archivos **en** la ubicación de la compilación.

Para implementar en la máquina local:

1.  En *Visual Studio*, abra el archivo de solución que se ha creado en el [capítulo anterior.](#chapter-10--test-in-the-unity-editor)
2.  En la **Plataforma de soluciones,** **seleccione x86**, **Máquina local.**
3.  En Configuración **de la solución,** **seleccione Depurar**.

    > Para la Microsoft HoloLens, es posible que le resulte más fácil establecer esta opción en Equipo remoto *para* que no se le aterrizó en el equipo. Sin embargo, también tendrá que hacer lo siguiente:
    > - Conozca la **dirección IP de** su HoloLens, que se puede encontrar en Configuración > Network & Internet > Wi-Fi > Opciones avanzadas *;* IPv4 es la dirección que debe usar. 
    > - Asegúrese **de que el modo de** desarrollador está en **on**; se encuentra *en Configuración > actualización & seguridad > para desarrolladores*.

    ![Implementación de una aplicación](images/AzureLabs-Lab3-46.png)
 
4.  Vaya al menú **Compilar y haga** clic en Deploy Solution **(Implementar solución)** para realizar la instalación local de la aplicación en el equipo.
5.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.
6.  Una vez iniciada, la aplicación le pedirá que autorice el acceso al _micrófono_. Use los *controladores de movimiento*, la entrada *de* voz o *el teclado* para presionar el **botón SÍ.** 

## <a name="chapter-12--improving-your-luis-service"></a>Capítulo 12: Mejora del servicio LUIS

>[!IMPORTANT] 
> Este capítulo es increíblemente importante y puede que deba iterar varias veces, ya que ayudará a mejorar la precisión del servicio LUIS: asegúrese de completarlo.

Para mejorar el nivel de comprensión proporcionado por LUIS, debe capturar nuevas expresiones y usarlas para volver a entrenar la aplicación de LUIS.

Por ejemplo, es posible que haya entrenado a LUIS para que comprenda "Aumentar" y "Aumentar tamaño", pero ¿no quiere que la aplicación también entienda palabras como "Ampliar"?

Una vez que haya usado la aplicación varias veces, LUIS recopilará todo lo que ha dicho y estará disponible en el PORTAL de LUIS.

1.  Vaya a la aplicación del portal siguiendo [este vínculo](https://www.luis.ai/home)e inicie sesión.
2.  Una vez que haya iniciado sesión con sus credenciales de MS, haga clic en el *nombre de la aplicación.*
3.  Haga clic en **el botón Revisar expresiones de** punto de conexión situado a la izquierda de la página.

    ![Revisión de expresiones](images/AzureLabs-Lab3-47.png)
 
4.  Se le mostrará una lista de las expresiones que la aplicación de realidad mixta ha enviado a LUIS.

    ![Lista de expresiones](images/AzureLabs-Lab3-48.png)
 
Observará algunas entidades *resaltadas.* 

Al mantener el puntero sobre cada palabra resaltada, puede revisar cada expresión y determinar qué entidad se ha reconocido correctamente, qué entidades son incorrectas y qué entidades se pierden.

En el ejemplo anterior, se encontró que la palabra "arpa" se había resaltado como destino, por lo que era necesario corregir el error, lo que se realiza al mantener el puntero sobre la palabra con el mouse y hacer clic en Quitar **etiqueta**.

![Comprobar expresiones Quitar ](images/AzureLabs-Lab3-49.png)
 ![ imagen de etiqueta](images/AzureLabs-Lab3-50.png)
 
5.  Si encuentra expresiones que son completamente incorrectas,  puede eliminarlas mediante el botón Eliminar del lado derecho de la pantalla.

    ![Eliminación de expresiones incorrectas](images/AzureLabs-Lab3-51.png)

6.  O bien, si cree que LUIS ha interpretado la expresión correctamente, puede validar su comprensión mediante el botón Agregar **a intención** alineada.

    ![Agregar a la intención alineada](images/AzureLabs-Lab3-52.png)

7.  Una vez que haya ordenado todas las expresiones mostradas, intente volver a cargar la página para ver si hay más disponibles.
8.  Es muy importante repetir este proceso tantas veces como sea posible para mejorar la comprensión de la aplicación. 

**¡Que te diviertas!**

## <a name="your-finished-luis-integrated-application"></a>La aplicación integrada de LUIS finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Language Understanding Intelligence Service para comprender lo que dice un usuario y actuar sobre esa información.

![Resultado del laboratorio](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

Al usar esta aplicación, es posible que observe que si mira el objeto Floor y le pide que cambie su color, lo hará. ¿Puede averiguar cómo impedir que la aplicación cambie el color del suelo?

### <a name="exercise-2"></a>Ejercicio 2

Pruebe a ampliar las funcionalidades de LUIS y de la aplicación, agregando funcionalidad adicional para los objetos de la escena. Por ejemplo, cree nuevos objetos en el punto de acceso de mirada, en función de lo que diga el usuario y, a continuación, pueda usar esos objetos junto con los objetos de escena actuales, con los comandos existentes.