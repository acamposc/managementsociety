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

#### Tambien se puede incluir mayor cantidad de informacion de los usuarios en la seccion TAGs.
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

¿En que ocasiones deberia extender la implementacion a este punto?

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
Ejemplo para diarios:
```javascript
MouseStats_Commands.push(["tag", "seccion", "deportes"]);
```




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



