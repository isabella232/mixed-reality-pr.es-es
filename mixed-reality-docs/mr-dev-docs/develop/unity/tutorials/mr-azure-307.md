---
title: HoloLens (1.ª generación) y Azure 307- Machine Learning
description: Complete este curso para aprender a implementar Azure Machine Learning Studio (clásico) dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, machine learning, ml, machine learning studio, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 062be48afb69bf2c4fa2eddcd816070d4d2575da7f06fe4464fa87f85676796b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199176"
---
# <a name="hololens-1st-gen-and-azure-307-machine-learning"></a>HoloLens (1.ª generación) y Azure 307: Aprendizaje automático

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

![final product -start](images/AzureLabs-Lab7-0.png)

En este curso, aprenderá a agregar funcionalidades de Machine Learning (ML) a una aplicación de realidad mixta mediante Azure Machine Learning Studio (clásico).

*Azure Machine Learning Studio (clásico)* es un servicio de Microsoft que proporciona a los desarrolladores un gran número de algoritmos de aprendizaje automático, que pueden ayudar con la entrada, salida, preparación y visualización de datos. A partir de estos componentes, es posible desarrollar un experimento de análisis predictivo, iterar en él y usarlo para entrenar el modelo. Después del entrenamiento, puede hacer que el modelo sea operativo dentro de la nube de Azure, de modo que pueda puntuar datos nuevos. Para obtener más información, visite [la página Azure Machine Learning Studio (clásico).](https://azure.microsoft.com/services/machine-learning-studio/)

Una vez completado este curso, tendrá una aplicación de casco envolvente de realidad mixta y habrá aprendido a hacer lo siguiente:

1.  Proporcione una tabla de datos de ventas al portal *de Azure Machine Learning Studio (clásico)* y diseñe un algoritmo para predecir las ventas futuras de elementos populares.
2.  Cree una **aplicación Project Unity,** que puede recibir e interpretar los datos de predicción del ML servicio.
3.  Muestre los datos de predicado visualmente dentro de **unity Project**, proporcionando los artículos de ventas más populares, en un período.

En la aplicación, es usted el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con unity Project. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar la aplicación de realidad mixta.

Este curso es un tutorial independiente, que no implica directamente a ningún otro Mixed Reality Labs.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (307): Aprendizaje automático</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente Windows Mixed Reality cascos envolventes (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga el curso, verá notas sobre los cambios que tenga que emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algún eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de escribir (mayo de 2018). Puede usar el software más reciente, como se muestra en el artículo instalación de las herramientas [,](../../install-the-tools.md)aunque no se debe suponer que la información de este curso coincida perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [Windows Mixed Reality envolvente envolvente (VR)](../../../discover/immersive-headset-hardware-details.md) o Microsoft HoloLens con el modo de desarrollador habilitado [](/hololens/hololens1-hardware)
- Acceso a Internet para la instalación y la recuperación de ML Azure

## <a name="before-you-start"></a>Antes de comenzar

Para evitar problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capítulo 1: configuración Azure Storage cuenta

Para usar azure Traductor API, deberá configurar una instancia del servicio para que esté disponible para la aplicación.
1.  Inicie sesión en [Azure Portal.](https://portal.azure.com)

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los procedimientos para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic **en Storage Cuentas en** el menú de la izquierda.

    ![Azure Storage Configuración de la cuenta](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > Es posible que **la palabra Nuevo** se haya reemplazado por Crear un **recurso** en los portales más recientes.

3.  En la **pestaña Storage,** haga clic en **Agregar**.

    ![Azure Storage Configuración de la cuenta](images/AzureLabs-Lab7-2.png)

4.  En el **panel Crear Storage cuenta:**

    1.  Inserte un **nombre** para la cuenta, tenga en cuenta que este campo solo acepta números y letras minúsculas.
    2.  En **Modelo de implementación,** seleccione **Resource Manager.**
    3.  En **Tipo de cuenta,** **seleccione Storage (uso general v1)**.
    4.  En **Rendimiento**, seleccione **Estándar**.
    5.  En **Replicación,** seleccione Almacenamiento con redundancia geográfica con acceso de **lectura (RA-GRS).**
    6.  Deje **Transferencia segura requerida como** **Deshabilitado.**
    7.  Seleccione una opción en **Suscripción**.
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).
    
    5.  Determine la **ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

5.  También deberá confirmar que ha comprendido los Términos y condiciones aplicados a este servicio.

    ![Azure Storage Configuración de la cuenta](images/AzureLabs-Lab7-3.png)

6.  Una vez que haya hecho clic en **Crear**, tendrá que esperar a que se cree el servicio, esto puede tardar un minuto.

7.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Azure Storage Configuración de la cuenta](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a>Capítulo 2: The Azure Machine Learning Studio (clásico)

Para usar *el Azure Machine Learning*, deberá configurar una instancia del servicio Machine Learning que esté disponible para la aplicación.

1.  En Azure Portal, haga clic en **Nuevo** en la esquina superior izquierda y busque Machine Learning Studio Workspace (Área de trabajo de **Studio),** presione **Entrar.**

    ![The Azure Machine Learning Studio (clásico)](images/AzureLabs-Lab7-5.png)

2.  La nueva página proporcionará una descripción del servicio Machine Learning **área de trabajo de** Studio. En la parte inferior izquierda de este símbolo del sistema, haga clic en **el botón** Crear para crear una asociación con este servicio.

3.  Una vez que haya hecho clic **en** Crear, aparecerá un panel donde deberá proporcionar algunos detalles sobre el nuevo servicio **Machine Learning Studio:**

    1.  Inserte el nombre del área **de trabajo que desee** para esta instancia de servicio.

    2.  Seleccione una opción en **Suscripción**.

    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común. 

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    4.  Determine la **ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones. Debe usar el mismo grupo de recursos que usó para crear el Azure Storage en el capítulo anterior.

    5.  Para la **sección Storage** cuenta, haga clic en Usar existente y, a continuación, haga clic en el menú desplegable y, **desde** allí, haga clic en la cuenta de Storage que creó en el último capítulo.

    6.  Seleccione el plan de **tarifa del área de trabajo** adecuado en el menú desplegable.

    7.  En la **sección Plan de servicio web,** haga clic en **Crear**  nuevo e inserte un nombre para él en el campo de texto.

    8.  En la **sección Plan de tarifa del plan de servicio** web, seleccione el plan de tarifa que prefiera. Un nivel de pruebas de desarrollo **denominado DEVTEST Standard** debe estar disponible sin cargo alguno.

    9.  También deberá confirmar que ha comprendido los términos y condiciones aplicados a este servicio.

    10. Haga clic en **Crear**.

        ![El Azure Machine Learning Studio (clásico)](images/AzureLabs-Lab7-6.png)

4.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

5.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![El Azure Machine Learning Studio (clásico)](images/AzureLabs-Lab7-7.png)

6.  Haga clic en la notificación para explorar la nueva instancia de servicio.

    ![El Azure Machine Learning Studio (clásico)](images/AzureLabs-Lab7-8.png)

7.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio.

8.  En la página que se muestra, en la sección **Vínculos** adicionales, haga clic en Iniciar **Machine Learning Studio**, que dirigirá el explorador al portal de **Machine Learning Studio.**

    ![El Azure Machine Learning Studio (clásico)](images/AzureLabs-Lab7-9.png)

9.  Use el **botón Iniciar** sesión, en la parte superior derecha o en el centro, para iniciar sesión en Machine Learning Studio (clásico).

    ![El Azure Machine Learning Studio (clásico)](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a>Capítulo 3: The Machine Learning Studio (classic): Configuración del conjunto de datos

Una de las formas Machine Learning algoritmos es analizar los datos existentes e intentar predecir resultados futuros en función del conjunto de datos existente. Por lo general, esto significa que, entre más datos existentes tenga, mejor será el algoritmo para predecir resultados futuros.

Para este curso se proporciona una tabla de ejemplo denominada [ProductsTableCSV](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)y se puede descargar aquí.

> [!IMPORTANT]
> El archivo .zip anterior contiene **productsTableCSV** y **.unitypackage**, que necesitará en el [capítulo 6.](#chapter-6---importing-the-mlproducts-unity-package) Este paquete también se proporciona dentro de ese capítulo, aunque es independiente del archivo csv.

Este conjunto de datos de ejemplo contiene un registro de los objetos más vendidos cada hora de cada día del año 2017.
        
![The Machine Learning Studio (classic): Configuración del conjunto de datos](images/AzureLabs-Lab7-11.png)

Por ejemplo, el día 1 de 2017, a la 1 p. m. (hora 13), el artículo más vendido fue sal y sal.

Esta tabla de ejemplo contiene 9998 entradas.

1.  Vuelva al portal **de Machine Learning Studio (clásico)** y agregue esta tabla como un conjunto de datos **para** su ML. Para ello, haga clic en **el botón + Nuevo** en la esquina inferior izquierda de la pantalla.

    ![The Machine Learning Studio (classic): Configuración del conjunto de datos](images/AzureLabs-Lab7-12.png)

2.  Aparecerá una sección desde la parte inferior y, dentro de eso, habrá un panel de navegación a la izquierda. Haga **clic en Conjunto** de datos y, a la derecha, en Desde archivo **local.**

    ![The Machine Learning Studio (classic): Configuración del conjunto de datos](images/AzureLabs-Lab7-13.png)

3.  Upload el nuevo conjunto **de datos** siguiendo estos pasos:

    1. Aparecerá la ventana de carga, donde puede **examinar la** unidad de disco duro del nuevo conjunto de datos.

        ![The Machine Learning Studio (classic): Configuración del conjunto de datos](images/AzureLabs-Lab7-14.png)

    2.  Una vez seleccionada, y de nuevo en la ventana de carga, deje la casilla sin activar.

    3.  En el campo de texto siguiente, **escribaProductsTableCSV.csv** nombre del conjunto de datos (aunque se debe agregar automáticamente).

    4.  Mediante el menú desplegable de **Tipo**, seleccione Archivo CSV genérico con **un encabezado (.csv).**

    5.  Presione el tic en la parte inferior derecha de la ventana de carga y se **cargará** el conjunto de datos.

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a>Capítulo 4: El Machine Learning Studio (clásico): El experimento

Para poder compilar el sistema de aprendizaje automático, deberá crear un experimento para validar la teoría sobre los datos. Con los resultados, sabrá si necesita más datos o si no hay ninguna correlación entre los datos y un posible resultado.

Para empezar a crear un experimento:

1.  Haga clic de nuevo en **el botón +** Nuevo en la parte inferior izquierda de la página y, a continuación, haga clic en **Experimento** en  >  **blanco experimento**.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-15.png)

2.  Se mostrará una nueva página con un experimento en blanco:

3.  En el panel de la izquierda, expanda Conjuntos de datos **guardados** Mis conjuntos de datos y  >   arrastre **ProductsTableCSV** al lienzo **del experimento.**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-16.png)

4.  En el panel de la izquierda, expanda **Ejemplo de transformación de** datos y  >  **Dividir.** A continuación, **arrastre el elemento Split Data (Dividir** datos) al lienzo del **experimento.** El elemento Split Data (Dividir datos) dividirá el conjunto de datos en dos partes. Una parte que usará para entrenar el algoritmo de aprendizaje automático. La segunda parte se usará para evaluar la precisión del algoritmo generado.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-17.png)

5.  En el panel derecho (mientras el elemento Dividir datos del lienzo está seleccionado), edite la fracción de filas del primer conjunto de datos de salida **a** **0,7.** Esto dividirá los datos en dos partes, la primera parte será el 70 % de los datos y la segunda parte será el 30 % restante. Para asegurarse de que los datos se dividen aleatoriamente, asegúrese de que la **casilla División aleatoria** permanece activada.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-18.png)

6.  Arrastre una conexión desde la base del **elemento ProductsTableCSV** del lienzo hasta la parte superior del elemento Dividir datos. Esto conectará los elementos y enviará la salida del conjunto de datos **ProductsTableCSV** (los datos) a la entrada Split Data (Dividir datos).  

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-19.png)

7.  En el **panel Experimentos** del lado izquierdo, expanda **Machine Learning**  >  **Entrenar**. Arrastre el **elemento Train Model (Entrenar** modelo) al lienzo Experiment (Experimento). El lienzo debe tener el mismo aspecto que el siguiente.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-20.png)

8.  En la parte **inferior izquierda** _ del elemento _ *Split Data** arrastre una conexión a la parte **superior derecha** del elemento Train **Model (Entrenar** modelo). El entrenamiento del modelo usará la primera división del 70 % del conjunto de datos para entrenar el algoritmo.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-21.png)

9.  Seleccione el **elemento Train Model** (Entrenar modelo) en el lienzo y, en el panel Propiedades (en el lado derecho de la ventana del explorador), haga clic en el botón Launch column selector  **(Iniciar selector de columnas).**

10. En el cuadro de texto, **escriba product y,** a continuación, **presione Entrar,** *el* producto se establecerá como una columna para entrenar predicciones. A continuación, haga clic en **el tic** de la esquina inferior derecha para cerrar el cuadro de diálogo de selección.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-22.png)

11. Va a entrenar un algoritmo de regresión logística  **multiclase** para predecir el producto más vendido en función de la hora del día y la fecha. Sin embargo, está fuera del ámbito de este documento para explicar los detalles de los distintos algoritmos proporcionados por Azure Machine Learning [Studio;](/azure/machine-learning/studio/algorithm-cheat-sheet) sin embargo, puede obtener más información en la hoja de referencia de algoritmos Machine Learning.

12. En el panel de elementos del experimento de la izquierda, expanda **Machine Learning** Inicializar clasificación de modelos y arrastre el elemento Regresión logística multiclase al  >    >  lienzo del experimento. 

13. Conectar salida, desde la parte inferior de **Regresión** logística multiclase hasta la entrada superior izquierda del **elemento Entrenar** modelo.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-23.png)

14. En la lista de elementos de experimento del panel de la izquierda, expanda **Machine Learning** Puntuación y arrastre el elemento Score Model (Puntuar  >  modelo) al lienzo. 

15. Conectar salida, desde la parte inferior de **Train Model**(Entrenar modelo), a la entrada superior izquierda de Score **Model (Puntuar modelo).**

16. Conectar la salida inferior derecha de **Split Data**(Dividir datos) a la entrada superior derecha del elemento Score **Model (Puntuar** modelo).

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-24.png)

17. En la lista **de** elementos de experimento del panel de la izquierda, expanda **Machine Learning** Evaluar y arrastre el elemento Evaluate Model (Evaluar  >  modelo) al  lienzo.

18. Conectar la salida de Score **Model (Puntuar modelo)** a la entrada superior izquierda de **Evaluate Model (Evaluar modelo).**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-25.png)

19. Ha creado su primer Machine Learning experimento. Ahora puede guardar y ejecutar el experimento. En el menú de la parte inferior  de la página, haga clic en el botón Guardar para guardar el experimento y, a continuación, haga clic en **Ejecutar** para iniciar el experimento.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-26.png)

20. Puede ver el **estado del** experimento en la parte superior derecha del lienzo. Espere unos instantes a que finalice el experimento.

    > Si tiene un conjunto de datos grande (real), es probable que el experimento tarde horas en ejecutarse.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-27.png)

21. Haga clic con el botón derecho en el elemento **Evaluate Model** (Evaluar modelo) en el lienzo y, en el menú contextual, mantenga el mouse sobre **Evaluation Results**(Resultados de evaluación) y seleccione **Visualize (Visualizar).**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-28.png)

22. Los resultados de la evaluación se mostrarán mostrando los resultados previstos frente a los resultados reales. Esto usa el 30 % del conjunto de datos original, que se dividió anteriormente, para evaluar el modelo. Puede ver que los resultados no son excelentes, lo ideal sería que el número más alto de cada fila fuera el elemento resaltado en las columnas.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-29.png)

23. Cierre los **resultados**.

24. Para usar el modelo de Machine Learning recién entrenado, debe exponerlo como **un servicio web**. Para ello, haga clic en el elemento de menú Set Up Web Service (Configurar servicio **web)** en el menú de la parte inferior de la página y haga clic en **Predictive Web Service (Servicio web predictivo).**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-30.png)

25. Se creará una nueva pestaña y se combinará el modelo de entrenamiento para crear el nuevo servicio web. 

26. En el menú de la parte inferior de la página, haga clic **en Guardar** y, a continuación, **en Ejecutar.** Verá el estado actualizado en la esquina superior derecha del lienzo del experimento.

    ![The Machine Learning Studio (clásico): El experimento](images/AzureLabs-Lab7-31.png)

27. Una vez que haya terminado de ejecutarse, **aparecerá un botón Implementar** servicio web en la parte inferior de la página. Está listo para implementar el servicio web. Haga **clic en Implementar servicio web** (clásico) en el menú de la parte inferior de la página.

    ![The Machine Learning Studio (clásico): El experimento](images/AzureLabs-Lab7-32.png)

    > Es posible que el explorador le pida que permita un elemento emergente, que debe permitir **,** aunque es posible que tenga que presionar Implementar servicio **web** de nuevo, si no se muestra la página de implementación. 

28. Una vez creado el experimento, se le redirigirá a una página **del** panel en la que se mostrará la clave **de API.** Cópielo en un Bloc de notas por el momento, lo necesitará en el código muy pronto. Una vez que haya anotado la clave de API, haga clic en el botón **SOLICITUD/RESPUESTA** en la **sección Punto** de conexión predeterminado debajo de la clave.

    ![The Machine Learning Studio (clásico): El experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Si hace clic en Probar en esta página, podrá especificar los datos de entrada y ver la salida. Escriba el **día y** la **hora.** Deje la entrada **del** producto en blanco. A continuación, haga clic **en el botón** Confirmar. La salida de la parte inferior de la página mostrará el JSON que representa la probabilidad de que cada producto sea la opción elegida.

29. Se abrirá una nueva página web, en la que se mostrarán las instrucciones y algunos ejemplos sobre la estructura de solicitudes que requiere Machine Learning Studio (clásico). Copie el **URI de solicitud** que se muestra en esta página en el Bloc de notas.

    ![The Machine Learning Studio (clásico): El experimento](images/AzureLabs-Lab7-34.png)

Ahora ha creado un sistema de aprendizaje automático que proporciona el producto más probable que se venderá en función de los datos históricos de compra, correlacionados con la hora del día y el día del año.

Para llamar al servicio web, necesitará la dirección URL del punto de conexión de servicio y una clave de API para el servicio. Haga clic en **la pestaña Consumir,** en el menú superior.

La **página** Información de consumo mostrará la información que necesitará para llamar al servicio web desde el código. Tome una copia de la **clave principal y** la dirección URL de **solicitud-respuesta.** Los necesitará en el capítulo siguiente.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capítulo 5: Configuración de unity Project

Configure y pruebe el casco envolvente Mixed Reality envolvente.

> [!NOTE]
>  No necesitará **controladores** de movimiento para este curso. Si necesita soporte técnico para configurar el casco envolvente, haga clic [aquí.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

1.  Abra **Unity** y cree una nueva instancia de Unity Project **llamada MR \_ MachineLearning.** Asegúrese de que el tipo de proyecto está establecido en **3D.**

2.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar**  >  **preferencias** y, a continuación, en la nueva ventana, vaya a **Herramientas externas**. Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

3.  A continuación, vaya a **File**  >  **Build Configuración** and switch the platform to Universal Windows **Platform**,by click on the Switch Platform button( Cambiar **_plataforma)._**

4.  Asegúrese también de que:

    1.  **El dispositivo de** destino se establece **en Cualquier dispositivo.**

        > Para la Microsoft HoloLens, establezca **Dispositivo de destino** en *HoloLens*.

    2.  **Tipo de** compilación se establece en **D3D.**

    3.  **EL SDK** está establecido en **Instalado más reciente.**

    4.  **Visual Studio versión está** establecida en **Última instalación instalada.**

    5.  **Build and Run (Compilar** y ejecutar) se establece en **Local Machine (Máquina local).**

    6.  No se preocupe por configurar **escenas** en este momento, ya que se proporcionan más adelante.

    7.  Por ahora, la configuración restante se debe dejar como predeterminada.

        ![Configuración de unity Project](images/AzureLabs-Lab7-35.png)

5.  En la **ventana Build Configuración** (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra **el inspector.** 

6. En este panel, es necesario comprobar algunas configuraciones:

    1.  En la **pestaña Otros Configuración** datos:

        1.  **La versión** **del runtime de** scripting debe ser **experimental** (equivalente a .NET 4.6)

        2. **El back-end de** scripting debe ser **_.NET_**

        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![Configuración de unity Project](images/AzureLabs-Lab7-36.png)

    2.  En la **pestaña Publishing Configuración** (Configuración publicación), en **Capabilities (Funcionalidades),** active:

        - **InternetClient**

            ![Configuración de unity Project](images/AzureLabs-Lab7-37.png)

    3.  Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de **Publicar Configuración),** marque **Virtual Reality Supported (Compatible** con virtual Reality), asegúrese de que se agrega el **SDK** Windows Mixed Reality.

        ![Configuración de unity Project](images/AzureLabs-Lab7-38.png)

    

6.  De nuevo **en Build Configuración** Unity C# Projects (Proyectos de C# de *Unity)* ya no está en gris; Marque la casilla situada junto a esta. 

7.  Cierre la ventana Build Settings (Configuración de compilación).

8.  Guarde el Project (**ARCHIVO > GUARDAR PROYECTO**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capítulo 6: Importación del paquete de Unity mlproducts

Para este curso, deberá descargar un paquete de recursos de Unity denominado [**Azure-MR-307.unitypackage.**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage) Este paquete viene completo con una escena, con todos los objetos de esa precompilado, por lo que puede centrarse en que todo funcione. El script **ShelfKeeper** se proporciona, aunque solo contiene las variables públicas, para la estructura de configuración de la escena. Deberá realizar todas las demás secciones. 

Para importar este paquete:

1.  Con el panel de Unity delante  de usted, haga clic en Activos en el menú de la parte superior de la pantalla y, a continuación, haga clic en **Importar paquete, Paquete personalizado**.

    ![Importar el paquete de Unity mlproducts](images/AzureLabs-Lab7-39.png)

2.  Use el selector de archivos para seleccionar **el paquete Azure-MR-307.unitypackage** y haga clic **en Abrir**.

3.  Se mostrará una lista de componentes para este recurso. Para confirmar la importación, haga clic **en Importar**.

    ![Importar el paquete de Unity mlproducts](images/AzureLabs-Lab7-40.png)

4.  Una vez que haya terminado de importarse, observará que algunas carpetas nuevas han aparecido en el panel de Project **Unity.** Estos son los modelos 3D y los materiales respectivos que forman parte de la escena pre-made en la que trabajará. Escribirá la mayoría del código en este curso.

    ![Importar el paquete de Unity mlproducts](images/AzureLabs-Lab7-41.png)

5.  En la **carpeta Project Panel,** haga clic en la carpeta **Escenas** y haga doble clic en la escena dentro de **(denominada MR_MachineLearningScene**). Se abrirá la escena (vea la imagen siguiente). Si faltan los rombos rojos, simplemente haga clic en el botón **Gizmos,** en la parte superior derecha del **panel de juegos.**

    ![Importar el paquete de Unity mlproducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capítulo 7: Comprobación de los archivos DLL en Unity

Para aprovechar el uso de bibliotecas JSON (usadas para serializar y deserializar), se ha implementado un archivo DLL de Newtonsoft con el paquete que ha incluido. La biblioteca debe tener la configuración correcta, aunque merece la pena comprobar (especialmente si tiene problemas con el código que no funciona). 

Para ello:

-  Haga clic con el botón izquierdo en el archivo Newtonsoft dentro de la carpeta Complementos y mire el **panel Inspector**. Asegúrese de **que cualquier plataforma** esté marcada. Vaya a la **pestaña UWP y** asegúrese también **de que No procesar** está marcado.

    ![Importación de los archivos DLL en Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capítulo 8: Creación de la clase ShelfKeeper

La **clase ShelfKeeper** hospeda métodos que controlan la interfaz de usuario y los productos generados en la escena.

Como parte del paquete importado, se le habrá dado esta clase, aunque está incompleta. Ahora es el momento de completar esa clase:

1.  Haga doble clic en el script **ShelfKeeper,** en la **carpeta Scripts,** para abrirlo **con Visual Studio 2017**.

2.  Reemplace todo el código existente en el script por el código siguiente, que establece la hora y la fecha y tiene un método para mostrar un producto.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  Asegúrese de guardar los cambios **en** Visual Studio antes de volver a **Unity.**

4.  De nuevo en el Editor de Unity, compruebe que la **clase ShelfKeeper** tiene un aspecto similar al siguiente:

    ![Creación de la clase ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Si el script no tiene los destinos de referencia (es decir, *Fecha (Text Mesh)*), simplemente arrastre los objetos correspondientes desde el **Panel** de jerarquía hasta los campos de destino. Consulte a continuación para obtener una explicación, si es necesario:
    > 
    > 1.  Abra la **matriz Punto de** generación en el script del componente **ShelfKeeper** haciendo clic con el botón izquierdo en ella. Aparecerá una subsección denominada **Size**, que indica el tamaño de la matriz. Escriba **3 en** el cuadro de texto situado junto a **Tamaño** y presione **Entrar** y se crearán tres ranuras debajo.
    > 2. Dentro de **la jerarquía,** expanda el **objeto Visualización** de tiempo (haciendo clic con el botón izquierdo en la flecha situada junto a él). A continuación, haga clic en la cámara ***principal _ desde dentro de _* Hierarchy**, para que el **inspector** muestre su información.
    > 3. Seleccione la **cámara principal en** el Panel de **jerarquía.** Arrastre los objetos **Date** y **Time** desde el  **Panel** de jerarquía a las ranuras **Texto** de fecha y Texto de hora dentro del **Inspector** de la cámara principal **en** el **componente ShelfKeeper.**
    > 4. Arrastre los **puntos de generación** desde el **Panel** de jerarquía (debajo del objeto *Shelf)* a los destinos de referencia 3 **Element** debajo de la **matriz** **Spawn Point,** como se muestra en la imagen.
    > 
    >     ![Creación de la clase ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capítulo 9: Creación de la clase ProductPrediction

La siguiente clase que va a crear es **la clase ProductPrediction.**

Esta clase es responsable de:

-   Consultar la instancia **Machine Learning service,** proporcionando la fecha y hora actuales.

-   Deserializar la respuesta JSON en datos utilizables.

-   Interpretación de los datos, recuperación de los 3 productos recomendados.

-   Llamar a los **métodos de clase ShelfKeeper** para mostrar los datos en la escena.

Para crear esta clase:

1.  Vaya a la **carpeta Scripts,** en la **Project panel**.

2.  Haga clic con el botón derecho en la carpeta **Create**  >  **C# Script (Crear script de C#).** Llame al script **ProductPrediction**.

3.  Haga doble clic en el nuevo script **ProductPrediction** para abrirlo **con Visual Studio 2017**.

4.  Si aparece el **cuadro de diálogo** Modificación de archivo detectada, haga clic en * Recargar *_solución_*.

5.  Agregue los siguientes espacios de nombres a la parte superior de la clase ProductPrediction:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  Dentro de **la clase ProductPrediction,** inserte los dos objetos siguientes que se componen de varias clases anidadas. Estas clases se usan para serializar y deserializar el archivo JSON para Machine Learning Service.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  A continuación, agregue las siguientes variables por encima del código anterior (para que el código relacionado con JSON esté en la parte inferior del script, debajo del resto del código y fuera del camino):

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Asegúrese de insertar la clave **principal y** el punto de conexión de **solicitud-respuesta**, desde Machine Learning Portal, en las variables aquí. Las imágenes siguientes muestran de dónde habría tomado la clave y el punto de conexión. 
    >  
    > ![The Machine Learning Studio (clásico): El experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![The Machine Learning Studio (clásico): El experimento](images/AzureLabs-Lab7-53-2.png)

8.  Inserte este código dentro del **método Start().** Se **llama al método Start()** cuando se inicializa la clase :

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  El siguiente es el método que recopila la fecha y hora de Windows y lo convierte en un formato que nuestro experimento de Machine Learning puede usar para comparar con los datos almacenados en la tabla.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. Puede eliminar **el** **método Update(),** ya que esta clase no lo usará.

11. Agregue el método siguiente que comunicará la fecha y hora actuales al punto de conexión Machine Learning y recibirá una respuesta en formato JSON.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. Agregue el método siguiente, que es responsable de deserializar la respuesta JSON y comunicar el resultado de la deserialización a la **clase ShelfKeeper.** Este resultado serán los nombres de los tres elementos predichos para vender más en la fecha y hora actuales. Inserte el código siguiente en la **clase ProductPrediction,** debajo del método anterior.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. Guarde **Visual Studio** y vuelva a **Unity.**

14. Arrastre el script **de clase ProductPrediction** desde la **carpeta Script** hasta el **objeto Cámara** principal.

15. Guarde la escena y el proyecto **File**  >  **Save Scene/File**  >  **Save Project**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capítulo 10: Compilación de la solución para UWP

Ahora es el momento de compilar el proyecto como una solución para UWP, para que se pueda ejecutar como una aplicación independiente.

Para compilar:

1.  Guarde la escena actual haciendo clic en **Guardar** escenas  >  **de archivo.**

2.  Vaya a **File**  >  **Build Configuración**

3.  Active la casilla proyectos **de C#** de Unity (esto es importante porque le permitirá editar las clases una vez completada la compilación).

4.  Haga clic **en Add Open Scenes (Agregar escenas abiertas).**

5.  Haga clic en **Generar**.

    ![Compilación de la solución para UWP](images/AzureLabs-Lab7-54.png)

6.  Se le pedirá que seleccione la carpeta donde desea compilar la solución.

7.  Cree una **carpeta BUILDS** y, dentro de esa carpeta, cree otra carpeta con el nombre adecuado que prefiera.

8.  Haga clic en la nueva carpeta y, a continuación, haga clic **en Seleccionar carpeta** para comenzar la compilación en esa ubicación.

    ![Compilación de la solución para UWP](images/AzureLabs-Lab7-55.png)

    ![Compilación de la solución para UWP](images/AzureLabs-Lab7-56.png)

9.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una ventana de **Explorador de archivos** en la ubicación de la compilación (compruebe la barra de tareas, ya que es posible que no siempre aparezca encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-11---deploy-your-application"></a>Capítulo 11: Implementación de la aplicación

Para implementar la aplicación:

1.  Vaya a la nueva compilación de Unity (la **carpeta Aplicación)** y abra el archivo de solución **con Visual Studio**.

2.  Con Visual Studio abierto, debe restaurar paquetes de NuGet, lo que se puede hacer haciendo clic con el botón derecho en la solución MachineLearningLab_Build, desde el Explorador de soluciones (que se encuentra a la derecha de Visual Studio) y, a continuación, hacer clic en Restaurar paquetes NuGet:

    ![Agregar paquetes NuGet](images/AzureLabs-Lab7-57.png)

3.  En Configuración de la solución, **seleccione Depurar**.

4.  En la Plataforma de soluciones, **seleccione x86**, **Máquina local.** 

    > Para la Microsoft HoloLens, es posible que le resulte más fácil establecer esta opción en Equipo remoto *para* que no se le aterrizó en el equipo. Sin embargo, también tendrá que hacer lo siguiente:
    > - Conozca la **dirección IP de** su HoloLens, que se puede encontrar en Configuración > Network & Internet > Wi-Fi > Opciones avanzadas *;* IPv4 es la dirección que debe usar. 
    > - Asegúrese **de que el modo de** desarrollador está en **on**; se encuentra *en Configuración > actualización & seguridad > para desarrolladores*.

    ![Agregar paquetes NuGet](images/AzureLabs-Lab7-58.png)

5.  Vaya al **menú Compilar y** haga clic en Deploy **Solution** to sideload the application to your PC (Implementar solución para realizar la instalación local de la aplicación en el equipo).

6.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

Al ejecutar la aplicación Mixed Reality, verá el banco que se ha configurado en la escena de Unity y, desde la inicialización, se capturarán los datos configurados en Azure. Los datos se deserializarán dentro de la aplicación y los tres resultados principales de la fecha y hora actuales se proporcionarán visualmente, como tres modelos en el banco.


## <a name="your-finished-machine-learning-application"></a>La aplicación de Machine Learning finalizada
 
Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha la Azure Machine Learning para realizar predicciones de datos y mostrarla en la escena.

![Agregar paquetes NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Ejercicio

**Ejercicio 1**

Experimente con el criterio de ordenación de la aplicación y haga que las tres predicciones inferiores aparezcan en el espacio, ya que estos datos también podrían ser útiles.

**Ejercicio 2**

Con **tablas de Azure,** rellene una nueva tabla con información meteorológica y cree un experimento con los datos.