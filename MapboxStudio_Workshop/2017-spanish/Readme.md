# Caso Práctico (Basado en los colores de la imagen)

## Resultado al que se quiere llegar.

![seleccion_037](https://cloud.githubusercontent.com/assets/12261974/24294336/fdead1b6-1063-11e7-8346-8adb54a33c50.png)

## Colores y fuentes a utilizar.

![buho](https://cloud.githubusercontent.com/assets/12261974/24238519/893e117a-0f78-11e7-8140-e60e802790ba.png)

![seleccion_009](https://cloud.githubusercontent.com/assets/12261974/24238486/665062da-0f78-11e7-81b4-53571fc9003a.png)

## Crear un nuevo estilo.

![seleccion_062](https://cloud.githubusercontent.com/assets/12261974/23900269/7eac8578-0886-11e7-92dc-6181d239c7c0.png)

- Hacer clic en la sección **Styles**, luego hacer clic en el botón **New Style**.
- Optamos por elegir el estilo **Basic**, luego hacer clic en **Create**.

## Personalizar su estilo.

### 1. Estilo del ambiente y agua.

![seleccion_004](https://cloud.githubusercontent.com/assets/12261974/24236679/e9d7063e-0f70-11e7-929f-0eb9eeb2542d.png)

- Haga clic en **background**, en la **Lista de capas**.
- Cuando el panel de **Estilo de capa** se muestre, cambie el campo **Color** con el valor **#584F52**.

![seleccion_005](https://cloud.githubusercontent.com/assets/12261974/24236856/b8bf942a-0f71-11e7-85e2-b3fee320cf1e.png)

- Haga clic en **water**, en la **Lista de capas**.
- Cuando el panel de **Estilo de capa** se muestre, cambie el campo **Color** con el valor **#0A6AA0**.
- Haga clic en **waterway**, en la **Lista de capas**.
- Cuando el panel de **Estilo de capa** se muestre, cambie el campo **Color** con el valor **#0A6AA0**.

### 2. Estilo en parques nacionales.

A continuación, cambiar el color de **landuse_park** y **landuse_overlay_national_park**, en el panel **Estilo de capa**.

![seleccion_006](https://cloud.githubusercontent.com/assets/12261974/24237272/9ee9e3f0-0f73-11e7-95c0-c10c0dbac60a.png)

- Seleccionar tanto el **landuse_park** y la capa **landuse_overlay_national_park**.
  - **Consejo**: Puede seleccionar varias capas a la vez manteniendo pulsada la tecla Ctrl, mientras hace clic para seleccionar capas. 
- Cuando el panel de **Estilo de capa** se muestre, cambie el campo **Color** de relleno con el valor: **#78706E**. 
- Cambie el campo **1px stroke** con el valor: **#1B2126**.

### 3. Cambiar las fuentes y opciones.

![seleccion_007](https://cloud.githubusercontent.com/assets/12261974/24237843/086aa150-0f76-11e7-910c-15453cdf0bce.png)

- Haga clic en **Properties**, el cual se encuentra en la parte inferior de la **Lista de capas**.
- Cuando la **Lista de propiedades** se abre, hacer clic en **Colors**. 
- Se muestra el panel de **Estilo de capa**, en la parte superior, en **Filtro de tipo de capas** hacer clic en **T(Capa de símbolo)**. Esto mostrará el color de texto de los objetos que sean de este tipo de capa **T**. 
- Cambie el campo **Text color** a **#FBFBFB**.
- Cambie el campo **Text halo color** a **#000000**.

![seleccion_008](https://cloud.githubusercontent.com/assets/12261974/24238397/1c9d8d98-0f78-11e7-89ec-2bd49ac77e4a.png)

- Hacer clic en  **Properties**
- Luego, hacer clic en **Font stacks**. 
- Se muestra el panel de **Estilo de capa**, en la parte superior, en **Filtro de tipo de capas** hacer clic en **T(Capa de símbolo)**. 
- Hacer los siguientes cambios: 
  - Cambiar el primer campo **Text font** a la fuente **Roboto Bold Condensed**. 
  - Cambiar el segundo campo **Text font** a la fuente **Roboto Black**.
  - Cambiar el tercer campo **Text font** a la fuente **Roboto Bold Condensed Italic**.

![seleccion_010](https://cloud.githubusercontent.com/assets/12261974/24238875/b2c961ec-0f79-11e7-9927-3b8ec0dd46cc.png)

- En la **Lista de capas**, Hacer clic en **country_label**. 
- Desplácese hacia abajo para encontrar la propiedad **transform**, y luego hacer clic en la opción **T (Mayúscula)**.

### 4. Etiquetas de carreteras.

![seleccion_011](https://cloud.githubusercontent.com/assets/12261974/24239376/b1f82832-0f7b-11e7-9acc-6b87196ebbf4.png)

- En la **Lista de capas**, hacer clic en **road_major_label**. 
- Cuando el panel de **Estilo de capa** se muestre, cambie el campo **Color** a **#C6A04F**.

### 5. Estilos por nivel de zoom.

![seleccion_012](https://cloud.githubusercontent.com/assets/12261974/24251589/a44232a0-0fa8-11e7-8864-b1539a29d692.png)

- En la **Lista de capas**, hacer clic en **background**.
- Cuando el panel de **Estilo de capa** se muestre, hacer clic en el icono situado junto al campo **Color**.
- Hacer clic en el botón **Enable zoom function**.
- Añadir una parada adicional haciendo clic en **Add stop**.
- Editar cada parada (el campo de la izquierda indica el nivel de zoom y el campo de la derecha indica el color).
  - Editar la primera parada, nivel de zoom con el valor de **0** y el color: **#584F52**.
  - Editar la segunda parada, nivel de zoom con el valor de **4** y el color: **#78706E**.
  - Editar la tercera parada, nivel de zoom con el valor de **10** y el color: **#969393**.
  - Editar la cuarta parada, nivel de zoom con el valor de **18** y el color: **#BABBBB**.
- Acercar la imagen para ver el cambio de color de fondo gradualmente a medida que aumenta el nivel de zoom.


### 6. Estilos en los edificios.

![seleccion_013](https://cloud.githubusercontent.com/assets/12261974/24252043/50b4eda6-0faa-11e7-9958-e3064d5ba3a5.png)

A continuación, se le cambia el color de los edificios para reflejar el estilo de la imagen del búho.

- En la **Lista de capas**, Hacer clic en **building**.
- Cuando el panel de **Estilo de capa** se muestre, cambie el campo **Color** con el valor **#0685BF**.
- Cambie el campo **Opacity** al valor **0.6**.
- Cambie el campo 1**px stroke** al valor **#0685BF**.

![seleccion_014](https://cloud.githubusercontent.com/assets/12261974/24252343/3737107e-0fab-11e7-85f8-8769140637a1.png)

- En la **Lista de capas**, hacer clic en la capa **building**.
- Cuando el panel de **Estilo de capa** se muestre, hacer clic en el icono situado junto al campo **Opacity**.
- Haga clic en el botón **Enable zoom function**. 
- Editar cada parada (el campo de la izquierda indica el nivel de zoom y el campo de la derecha indica la opacidad).
  - Editar la primera parada, nivel de zoom con el valor de **15** y la opacidad **0**.
  - Editar la segunda parada, nivel de zoom con el valor de **16** y la opacidad **0.6**.
- Acercar la imagen para ver como los edificios se desvanecen entre nivel de zoom de 15 a 16.


![seleccion_018](https://cloud.githubusercontent.com/assets/12261974/24262434/f6f2d076-0fc7-11e7-9586-4f188b4a787d.png)

### 7. Tilesets de Puntos de interés (PDI).
[Recursos:](https://www.dropbox.com/sh/qokfgtbkpwa9hco/AABCIkic-NT59QGJdURDSCsVa?dl=0):

- PDI de tipo atm (Cajero automático) en con extensión geojson.
- Archivo con extensión SVG: bank-15.svg, bank-15-blue.svg.

![seleccion_020](https://cloud.githubusercontent.com/assets/12261974/24292214/57ebcc24-105a-11e7-9ffc-212046e2efcb.png)

- Hacer clic en la sección **Tileset**.
- Luego, clic en el botón **New tileset**.
- Seleccionar el archivo, y luego hacer clic en el botón **Upload**.

![seleccion_021](https://cloud.githubusercontent.com/assets/12261974/24292370/0ca3516e-105b-11e7-971d-18bb81700d79.png)

La subida del archivo a su **Lista de Tilesets** esta siendo procesado (Esto se identifica cuando el circulo al costado de la campana es de color azul, cuando es de color verde, indica que el archivo ya fue actualizado en la **Lista de Tilesets**).

![seleccion_022](https://cloud.githubusercontent.com/assets/12261974/24292547/cf3aa10a-105b-11e7-9c8a-f49c570a6e82.png)

- Hacer clic en la sección **Styles**.
- Hacer clic en el proyecto en el que esta trabajando.
- Luego hacer clic en el botón **Edit**.
- En la **Lista de capas**, en la parte superior, hacer clic en el botón**New Layer**.
- Ahora, en el panel de **Estilo de capas**, hacer clic en el campo **Source**.
- Hacer clic en el archivo **atm**, el cual se subió como un nuevo tileset,

![seleccion_023](https://cloud.githubusercontent.com/assets/12261974/24292753/aaa556a4-105c-11e7-9d16-d81e3451197c.png)

- En el panel de **Estilo de capas**, en la parte de **Type**, hacer clic en el botón **T** (Para que la nueva capa se de tipo **Símbolo**).
- Luego, hacer clic en el botón **Create Layer**.

![seleccion_026](https://cloud.githubusercontent.com/assets/12261974/24292899/3e751c02-105d-11e7-9f5e-06ac3932917c.png)

- Hacer clic en la nueva capa creada **atm**.
- Se ubica en la pestaña **Style*, dentro de ella en la pestaña **Icon**.
- Hacer clic en el campo **Image**.
- Clic en el botón **Add SVG images**.
- Seleccionar los archivos **bank-15-blue**, **bank-15**.
- Luego, hacer clic en la imagen **bank-15-blue**.

![seleccion_027](https://cloud.githubusercontent.com/assets/12261974/24293167/73c0066e-105e-11e7-96f4-be633082284b.png)

- Hacer clic en el icono situado junto al campo **Image**.
- Haga clic en el botón **Enable zoom function**. 
- Editar cada parada (el campo de la izquierda indica el nivel de zoom y el campo de la derecha indica la imagen a mostrar).
  - Editar la primera parada, nivel de zoom con el valor de **10** y la imagen a mostrar **bank-15-blue**.
  - Editar la segunda parada, nivel de zoom con el valor de **15** y la imagen a mostrar  **bank-15**.
- Acercar la imagen para ver los Puntos de interés (PDI), en este caso, de tipo atm (Cajero automático), que cambia de imagen entre nivel de zoom de 10 a 15.


![seleccion_032](https://cloud.githubusercontent.com/assets/12261974/24293618/a571835c-1060-11e7-98f1-526a30b7fdef.png)

- Hacer clic en el icono situado junto al campo **Opacity**.
- Haga clic en el botón **Enable zoom function**. 
- Editar cada parada (el campo de la izquierda indica el nivel de zoom y el campo de la derecha indica la opacidad).
  - Editar la primera parada, nivel de zoom con el valor de **12** y la opacidad **0**.
  - Editar la segunda parada por lo que el nivel de zoom es **16** y la opacidad **1**.
- Acercar la imagen para ver como los iconos se desvanecen en el nivel de zoom entre 12 y 16.

![seleccion_030](https://cloud.githubusercontent.com/assets/12261974/24293693/130a9642-1061-11e7-8d54-957ae81348ba.png)

- En el panel de **Estilo de capa**, se ubica en la pestaña **Style**, dentro de ella en la pestaña **Text**.
- Luego hacer clic en el campo **Text field**.
- En el nuevo panel que se abre, hacer clic en **name**.

![seleccion_031](https://cloud.githubusercontent.com/assets/12261974/24293796/81c5680a-1061-11e7-9ba6-6330865c68a6.png)

- Hacer clic en el icono situado junto al campo **Opacity**.
- Haga clic en el botón **Enable zoom function**. 
- Editar cada parada (el campo de la izquierda indica el nivel de zoom y el campo de la derecha indica la opacidad).
  - Editar la primera parada por lo que el nivel de zoom es **12** y la opacidad es **0**.
  - Editar la segunda parada por lo que el nivel de zoom es **16** y la opacidad es **1**.
- Acercar la imagen para ver como los nombres de los cajeros automáticos se desvanecen en el nivel de zoom entre 12 y 16.

![seleccion_033](https://cloud.githubusercontent.com/assets/12261974/24293896/f5b55b1c-1061-11e7-9a48-43367d72772b.png)

- Hacer clic en el icono situado junto al campo **Size**.
- Haga clic en el botón **Enable zoom function**. 
- Editar cada parada (el campo de texto de la izquierda es el nivel de zoom y el campo de texto de la derecha es el tamaño de letra).
  - Editar la primera parada por lo que el nivel de zoom es **12** y el tamaño de letra es de **10px**.
  - Editar la segunda parada por lo que el nivel de zoom es **18** y el tamaño de letra es de **16px**.
- Acercar la imagen para ver como el tamaño de las letras de los nombres de los cajeros automáticos cambia en el nivel de zoom entre 12 y 18.

![seleccion_034](https://cloud.githubusercontent.com/assets/12261974/24294106/02b7c308-1063-11e7-8dbb-50aee378df7d.png)

- Hacer clic en el campo **Color**  y poner el valor de **#1B2126**.

![seleccion_035](https://cloud.githubusercontent.com/assets/12261974/24294139/3712a7e4-1063-11e7-8b5f-33cf179686d0.png)

- Hacer clic en el campo **Font**.
- Luego, hacer clic en el tipo de letra **Merriweather Heavy**.

![seleccion_036](https://cloud.githubusercontent.com/assets/12261974/24294207/89f3cd94-1063-11e7-8333-03c7172bc374.png)

- Se ubica en la pestaña **Style*, dentro de ella en la pestaña **Position**.
- En el campo **Text anchor**, hacer clic en la opción **Top**.

## Más recursos

- [Manual Mapbox Studio](https://www.mapbox.com/help/studio-manual/).
- [Maki Icons](https://www.mapbox.com/maki-icons/editor/).