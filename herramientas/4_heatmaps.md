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

### Integracion avanzada con Google Analytics
#### Objetivo:
    1. Encontrar usuarios con un comportamiento interesante en GA.
    2. Obtener su Mousestats ID en GA.
    3. Ver un playback de su sesion en Mousestats.
    
#### ¿Como se logra esto?
    El ID de usuario de Mousestats se pinta en una Dimension Personalizada de Google Analytics.
    
[Pasos para integrar Mousestats con GA usando GTM.](http://www.mousestats.com/docs/wiki/32/google-analytics-integration-using-gtm)



---

Ir a [Cuestionarios](https://github.com/acamposc/managementsociety/blob/master/herramientas/5_cuestionarios.md)

[mt_over]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/4_mousestats_overview.png
[]: 
[]: 
