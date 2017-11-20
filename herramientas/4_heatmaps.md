# *Material de la clase: https://goo.gl/DyioCv*


# Mapas de calor

    Se da por entendido que ya se tiene:
    - Una cuenta de Mousestats.
    - Un contenedor de GTM.
    - Un sitio web donde poder publicar.
    
Para empezar: [Iniciar sesion en mousestats.com](https://ssl.mousestats.com/user/login) 

### Overview

  ![mt_over]

### Instalar Mousestats en un sitio web

Para empezar es necesario ubicar y copiar el codigo que aparece en la Vista General de Mousestats.
En caso se vaya a usar el codigo a continuacion, cambiar el **id de usuario** caso contrario no va a funcionar.

```javascript
<!--  MouseStats:Begin  -->
<script type="text/javascript">var MouseStats_Commands=MouseStats_Commands?MouseStats_Commands:[]; (function(){function b(){if(void 0==document.getElementById("__mstrkscpt")){var a=document.createElement("script");a.type="text/javascript";a.id="__mstrkscpt";a.src=("https:"==document.location.protocol?"https://ssl":"http://www2")+".mousestats.com/js/4/7/<YOUR MOUSTATS ID HERE>.js?"+Math.floor((new Date).getTime()/6E5);a.async=!0;a.defer=!0;(document.getElementsByTagName("head")[0]||document.getElementsByTagName("body")[0]).appendChild(a)}}window.attachEvent?window.attachEvent("onload",b):window.addEventListener("load", b,!1);"complete"===document.readyState&&b()})(); </script>
<!--  MouseStats:End  -->
```

[Luego se puede proceder a instalar usando Google Tag Manager.](http://www.mousestats.com/docs/wiki/31/google-tag-manager-gtm-integration) 
La regla a usar en GTM depende de donde se quiera capturar data, tambien se puede usar "All pages".

### [Instalar Mousestats en un sitio web que use Wordpress](http://www.mousestats.com/docs/wiki/9/mousestats-wordpress-integration)
Existe un plugin oficial de Mousestats para Wordpress, es una alternativa a implementarlo por GTM.

### Integracion avanzada con Google Analytics
#### Objetivo:
    1. Encontrar usuarios con un comportamiento interesante en GA.
    2. Obtener su Mousestats ID en GA.
    3. Ver un playback de su sesion en Mousestats.
    
#### ¿Como se logra esto?
    El ID de usuario de Mousestats se pinta en una Dimension Personalizada de Google Analytics.
    
   ![mt_ga_custom_dimension] 
    
#### [Pasos para integrar Mousestats con GA usando GTM.](http://www.mousestats.com/docs/wiki/32/google-analytics-integration-using-gtm)

### Identificar a un usuario en Mousestats
:warning:Para habilitar esta caracteristica **se debe tener un identificador del usuario** como correo electronico o un id de base de datos disponible cuando navega la web.

[Instruccion: colocar la siguiente linea de codigo luego de haber colocado la etiqueta de Mousestats](http://www.mousestats.com/docs/wiki/27/identify-a-user)

```javascript
<!--  MouseStats:Begin  -->
<script type="text/javascript">var MouseStats_Commands=MouseStats_Commands?MouseStats_Commands:[]; (function(){function b(){if(void 0==document.getElementById("__mstrkscpt")){var a=document.createElement("script");a.type="text/javascript";a.id="__mstrkscpt";a.src=("https:"==document.location.protocol?"https://ssl":"http://www2")+".mousestats.com/js/4/7/<YOUR MOUSTATS ID HERE>.js?"+Math.floor((new Date).getTime()/6E5);a.async=!0;a.defer=!0;(document.getElementsByTagName("head")[0]||document.getElementsByTagName("body")[0]).appendChild(a)}}window.attachEvent?window.attachEvent("onload",b):window.addEventListener("load", b,!1);"complete"===document.readyState&&b()})(); </script>
<!--  MouseStats:End  -->

MouseStats_Commands.push(["identify", "john.doe@example.com"]);
```
Esta data se puede encontrar en la seccion TAGs (dentro de Mousestats).

### Agregar otra informacion de usuario
Tambien se puede incluir mayor cantidad de informacion de los usuarios en la seccion TAGs.
![mt_tags]

Ejemplos de tags a usar:
```javascript
MouseStats_Commands.push(["tag", "paidMember"]);

MouseStats_Commands.push(["tag", "returningVisitor"]);
```

Para tener la informacion organizada se sugiere usar la siguiente forma:
```javascript
MouseStats_Commands.push(["tag", "email", "user@mysite.com"]);
```
En estos casos la consulta se debe realizar de la siguiente manera `"email:user@mysite.com"`; es decir, `key:value`.

#### ¿En que ocasiones deberia extender la implementacion a este punto?

Cuando se desea:

- :watermelon:Analizar el comportamiento de los usuarios diferenciandolos en base a definiciones de negocio.
	
	* Ejemplo 1: ¿En un ecommerce el comportamiento en el checkout sera igual para el que no esta registrado y compra sin registrarse?
	![macys_checkout]
	
	* Ejemplo 2: ¿La navegacion de un usuario de Netflix sera igual en su periodo de 30 dias gratis vs el de un usuario con plan Premium? [Referencia sobre los planes de Netflix.](https://help.netflix.com/en/node/24926)
	![netflix_plans]
	
	* Ejemplo 3: ¿Sera similar la navegacion entre distintos usuarios de una misma cuenta de Netlfix?
	![netflix_users]

- :banana:Segmentando los reportes de Mousestats en base a intencionalidad:

	Esto aplica tanto para los negocios que pueden identificar a sus usuarios por correo o id como para los que no pueden.
	*Para ahondar en esto se sugiere tener en mente el flujo deseado de navegacion en la Web o APP y la intencionalidad en la que se encuentra el publico que deseo analizar.*
	
	#### Online Customer Journey 
	![goal_flow]
	Para llegar al grafico mostrado con las etapas de interes en el flujo de la navegacion se puede seguir la siguiente ruta en Analytics: **Conversions / Goals / Goal Flow**
	
	Tambien es necesario considerar que para tener data en esta seccion se debe configurar el embudo de conversiones en la cuenta de Analytics del negocio. [Referencia para configurar objetivos en Google Analytics de manera eficiente.](http://attachmedia.com/blog/como-definir-y-medir-objetivos-para-sitios-web-en-google-analytics/?utm_source?=github&utm_medium=clase_arturo&utm_campaing=managementsociety)
	
	#### Intencionalidad
	![see_think_do]
	
	En caso no las tengamos definidas podemos usar de referencia el [Framework See Think Do Care](https://www.thinkwithgoogle.com/intl/en-145/perspectives/global-articles/kpis-essential-framework/) para definir no solo los KPIs importantes a seguir sino en que pasos del Customer Journey se encuentran las primeras tres etapas: 
	
	* See: Podemos analizar el comportamiento de los usuarios cuando las paginas de destino son de campañas de Display orientadas a generar Awareness. 
	* Think: Podemos analizar el comportamiento cuando: se navega entre paginas de detalle de producto o se tienen formularios para conseguir leads.
	* Do: La idea es analizar el proceso de checkout y la compra. 
	
	Este Framework usualmente se usa para definir la estrategia de publicidad pero en este caso lo usamos para decidir donde ejecutar los heatmaps, cuestionarios, otro ejemplo es segmentar los playbacks para no ver los de sesiones que no llegan al checkout o que rebotan.


Para poder segmentar los reportes de Mousestats a este nivel se debe tener definido las variables de navegacion, como ejemplo quedan las siguientes:

Ejemplo para travel:
```javascript
MouseStats_Commands.push(["tag", "tipo de viaje", "ida y vuelta"]);
```
Ejemplo para seguros:
```javascript
MouseStats_Commands.push(["tag", "categoria", "ida y vuelta"]);
```
Ejemplo para sitios de contenido:
```javascript
MouseStats_Commands.push(["tag", "seccion", "deportes"]);
```
Ejemplo para educacion:
```javascript
MouseStats_Commands.push(["tag", "carrera", "marketing"]);
```

### Tipos de mapas de calor

1. Area stats
 ![mt_element_analysis]
 
 La idea es simple, solo basta con seleccionar las zonas que se desea comparar dentro de un mismo diseño.
 
	 Preguntas de negocio a contestar con este tipo de analisis:
	 - ¿Donde da clic la gente? ¿Que call to action dentro del mismo landing page funciona mejor?
	 - ¿Que imagen capta mas atencion dentro de la misma pagina?
	 - ¿Que frase capta mas atencion?
	 - ¿Que color/tamaño/fuente del copy consigue mas atencion?
 
 
2. Attention heatmaps
 ![mt_attention_heatmaps]
 
  El algoritmo de Mousestats define las areas importantes en base a donde se logra mayor atencion en la vista de una pagina.
 
	 Preguntas de negocio a contestar con este tipo de analisis:
	 - ¿Donde me conviene colocar el llamado a la accion?
	 - ¿Que tanto me conviene tener un banner en la parte superior de la pagina?
	 - ¿La gente mira el carruesel de imagenes? ¿le dan clic si quiera?
	 - ¿Hay contenido que merece ser eliminado?

3. Scroll heatmaps
 ![mt_scroll_heatmaps]
 
	 Preguntas de negocio a contestar con este tipo de analisis:
	 - ¿Que tan abajo de la pagina me conviene poner un anuncio publicitario?
	 - ¿Hay demasiado contenido en la pagina o conviene colocar mas?
	 - ¿Que tan esencial es poner la informacion mas importante above the fold?


4. Click heatmaps
 ![mt_click_heatmaps]
 
	 Preguntas de negocio a contestar con este tipo de analisis:
	 - ¿Como simplificar la interfaz sin arruinar la experiencia del usuario?
	 - ¿Que elementos son inutiles en el diseño?
	 - ¿Que colores / imagenes / botones confunden?
	 - ¿Deberia volver este elemento un enlace?
 
5. Move heatmaps
 ![mt_move_heatmaps]

	 Preguntas de negocio a contestar con este tipo de analisis:
	 - ¿Que secciones no se leen?
	 - ¿Que elemento llama mas la atencion?
	 

6. Viewport Overlap

	 ![mt_viewport]

	 Preguntas de negocio a contestar con este tipo de analisis:
	 - ¿Que contenido ven todos los usuarios en general?


### Hora de crear un Heatmap

1. Elegir una pagina.

 ![atm_analytics_pages]

	Reportes de Google Analytics a revisar:

	a. Behavior / Site Content / All pages

	b. Behavior / Site Content / Landing pages

2. Revisar el tipo de dispositivo.

 ![atm_analytics_devices]

	Reportes de Google Analytics a revisar:

	a. Behavior / Site Content / All pages / Dimension secundaria: Device Category
 
	b. Behavior / Site Content / Landing pages / Dimension secundaria: Device Category

3. Revisar la pagina.

 ![atm_guia_ux]

  #### http://attachmedia.com/guia-ux/

4. Revisar que la etiqueta de Mousestats este implementada.

 ![atm_gtm_preview]

5. En `Mousestats / Heatmaps / Create new project`

	5.1 **Page URL**: Colocar la URL completa de la pagina a analizar (incluyendo el encabezado http / https)
	
	5.2 **Limit**: Modificar el limite de vistas a usarse para este reporte.
	
	5.3 **Screen Width Range**: Modificar el tamaño de pantalla para diferenciar dispositivos. 
	Se recomienda configurar un mapa por tipo de dispositivo.
	
	5.4 Crear el mapa.


 ![mt_hm_step1]
 
 ![mt_hm_step2]


6. Volviendo a la vista general de Heatmaps podemos editar la configuracion:
 
 ![mt_hm_options]
 
 Se sugiere siempre subir una version propia de la pantalla. Esta opcion solo se habilita una vez que el proyecto ha sido creado.
 
 ![mt_hm_retake]

:lollipop:Y el proyecto ha sido creado. 

 ![mt_hm_esperar]

:hourglass_flowing_sand:Ahora solo queda esperar que la gente pase por la pagina y acumular datos.
 
 ![meme_esperar]

Una vez se tienen datos se puede compartir directamente el reporte a traves de un enlace sin necesidad de dar los accesos de la cuenta:
 
 ![mt_hm_share]
 
 [Pueden ver el mapa de la Guia UX a traves de este enlace.](https://ssl.mousestats.com/project/clicks/5648789896264721916/?accessKey=cb7747b235719a63f59f1e0bef2dc152)

Se puede anular el acceso a la data a traves de los enlaces compartidos.
 
 ![mt_hm_revoke]

Con esto damos fin a la configuracion de heatmaps.

 ![potato]

[Documentacion de Heatmaps de Mousestats.](http://www.mousestats.com/docs/wiki/11/heatmap-projects)


---

# Form Analytics

 ![mt_fa_screen]

### Tipos de reportes

1. Conversion

   3 metricas se ven en el grafico principal.

   1. **Form Views**: Desde que aparece el formulario en una pagina.
   2. **Form Starts**: Desde que se hace clic sobre uno de los campos de un formulario.
   3. **Conversions**: Envios de formulario en el navegador.

   Timings:
  
   ![mt_form_timings]
  
   Otros insights:
  
   ![mt_form_otros]

2. Abandonos de formulario.
   Por defecto, Mousestats cogera el nombre del input para mostrarlo en el grafico. 

   ![mt_form_drop]
  
   

### Configurar Form Analytics

1. Elegir una pagina.

 ![atm_analytics_pages]

	Reportes de Google Analytics a revisar:

	a. Behavior / Site Content / All pages / Solo mostrar las paginas con formularios

	b. Behavior / Site Content / Landing pages / Funciona cuando son landing pages con formularios


2. Revisar la pagina. `La pagina debe tener un formulario para que este reporte funcione correctamente`

 ![atm_contacto]

  #### http://attachmedia.com/contacto

3. En `Mousestats / Form Analytics / Create new project`
 
 ![mt_form_config]
 

	3.1 **Page URL**: Colocar la URL completa de la pagina a analizar (incluyendo el encabezado http / https)
	
	3.2 **Limit**: Modificar el limite de vistas a usarse para este reporte.
	
	3.3 **Advanced / Form id**: Se recomienda colocar el id del formulario en caso exista o en caso se tenga mas de un formulario html en una pagina.
	
	3.4 Crear el reporte.


Consideraciones:
 - No todos los formularios tienen IDs, motivo por el cual es opcional colocarlo. 
 
 ![mt_form_html_form]
 
 [Mas informacion sobre los formularios HTML en este enlace.](https://www.w3schools.com/html/html_forms.asp)

 - No todos los desarrollos funcionan igual, a pesar de seguir una misma estructura es probable que Mousestats no pueda capturar las "Conversiones". 
  En estos casos se sugiere realizar el siguiente ajuste:
  
  Ejecutar el siguiente codigo cuando un formulario hace un envio satisfactorio de datos ("submit event")  
  ```javascript
  try { MouseStatsFormAnalytics.Submitted(); } catch(e) { };
  ```
  
  En caso de tener mas de un formulario en una pagina, para diferenciarlos se sugiere colocar el ID de la siguiente manera:
  
  ```javascript
  try { MouseStatsFormAnalytics.Submitted($("#formA")[0]); } catch(e) { };
  ```
  
  [Documentacion oficial de Mousestats sobre el registro de Conversiones](http://www.mousestats.com/docs/wiki/22/mark-a-form-as-submitted-manually)
  
  
  
  
  
  
---

Ir a [Cuestionarios](https://github.com/acamposc/managementsociety/blob/master/herramientas/5_cuestionarios.md)

[mt_over]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_overview.png
[mt_ga_custom_dimension]: https://www.mousestats.com/docs/Attachments/DocumentResources/GADimensions.png
[mt_tags]: http://www.mousestats.com/docs/Attachments/Images/TagData.png
[macys_checkout]: https://assets.econsultancy.com/public/imgur/swS6IYs.png
[netflix_plans]: https://www.cutcabletoday.com/wp-content/uploads/2016/05/Netflix-plans-1024x600.jpg
[netflix_users]: https://iwsmt-content-ok2nbdvvyp8jbrhdp.stackpathdns.com/942015193464.jpg
[see_think_do]: https://www.kaushik.net/avinash/wp-content/uploads/2013/07/see_think_do_optimal_digital_marketing_strategy-2.png
[goal_flow]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_goal_flow_analytics.png
[mt_element_analysis]: https://www.mousestats.com/static/theme/salesv2/serviceScreenshots/areastats.gif
[mt_attention_heatmaps]: https://www.mousestats.com/static/theme/salesv2/serviceScreenshots/attention.gif
[mt_scroll_heatmaps]: https://www.mousestats.com/static/theme/salesv2/serviceScreenshots/scroll.gif
[mt_click_heatmaps]: https://www.mousestats.com/static/theme/salesv2/serviceScreenshots/clicks.gif
[mt_move_heatmaps]: https://www.mousestats.com/static/theme/salesv2/serviceScreenshots/move.gif
[mt_viewport]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_viewport.png
[meme_esperar]: https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTH8cRv_Re4oo-DOVAm80K-EBeM36AulnLBrTyjpMNwU0hUrmlOZw
[atm_analytics_pages]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_analytics_attachmedia.png
[atm_analytics_devices]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_attachmedia_guia_ux_devices.png
[atm_guia_ux]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_attachmedia_guiaux.png
[atm_gtm_preview]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_attachmedia_gtm_preview.png
[mt_hm_step1]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_heatmaps_atm_guia_ux.png
[mt_hm_step2]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_heatmaps_atm_guia_ux_2.png
[mt_hm_options]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_heatmaps_atm_options.png
[mt_hm_retake]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_heatmaps_atm_guia_ux_retake_screenshot.png
[mt_hm_esperar]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_heatmaps_atm_esperar.png
[mt_hm_share]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_heatmaps_atm_share.png
[mt_hm_revoke]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_heatmaps_atm_share_revoke.png
[potato]: https://i.pinimg.com/originals/a2/db/bb/a2dbbbd88508277c701bd1919f6e5b12.jpg
[mt_fa_screen]: https://www.mousestats.com/docs/Attachments/Blog/fa-conversion.png
[atm_contacto]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/5_mousestats_form_analytics_attachmedia_contacto.png
[mt_form_config]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/5_mousestats_form_config.png
[mt_form_html_form]: https://www.htmlgoodies.com/img/2010/06/HTML-Forms-From-Basics-to-Style-Layouts-Figure2.gif
[mt_form_drop]: http://www.mousestats.com/docs/Attachments/Images/formanalyticsTitles.png
[mt_form_timings]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/5_mousestats_form_conv_timing.png
[mt_form_otros]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/5_mousestats_form_conv_otros.png

