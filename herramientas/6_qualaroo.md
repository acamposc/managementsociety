# *Material de la clase: https://goo.gl/DyioCv*


# Micro surveys (seguimos en Mousestats)

    Se da por entendido que ya se tiene:
    - Una cuenta de Mousestats.
    - Un contenedor de GTM.
    - Un sitio web donde poder publicar.
    
Para empezar: [Iniciar sesion en mousestats.com](https://ssl.mousestats.com/user/login) 

### Overview

Cuando se necesite recopilar informacion de los usuarios del Sitio / APP se pueden activar los Micro Surveys que se mostraran de la siguiente manera:

 ![mt_ms_ex]

### Configurando el cuestionario

1. Elegir una pagina.

http://attachmedia.com/blog/estudio-sobre-que-y-como-comparten-contenidos-los-blogueros-e-influencers/

Criterio: `Dentro de la estrategia`, la ultima publicacion del blog debe recibir pauta hasta que salga la proxima.

2. Elegir preguntas.

   2.1 Configurar la pagina y la cantidad de respuestas a conseguir.
   
   ![mt_ms_prop_prim]
   
   2.2 Pregunta de una seleccion.
   
   ![mt_ms_step1]
   
   2.3 Otra pregunta de una seleccion.
   
   ![mt_ms_step2]

   2.4 Pregunta seleccion multiple.
   
   ![mt_ms_step3]
   
   2.5 Pregunta abierta. :email:`En este caso la usamos para capturar correos.`
      
   ![mt_ms_step4]

   2.6 Pregunta tipo `mensaje`.
   
   ![mt_ms_step5]

Los resultados se ven de la siguiente manera:

 ![mt_ms_results]

¡Con esto damos fin a Mousestats!

![potato]

---

# Qualaroo

Es una herramienta que cumple eficientemente con lanzar cuestionarios en cualquier sitio web. [Tiene una amplia documentacion con videos e imagenes para cada situacion e integracion posible.](https://help.qualaroo.com/hc/en-us)

Como una de sus principales ventajas ofrece enviar las respuestas a Google Analytics como Eventos, evitando tener que revisar los reportes de Qualaroo.

 ![qr_ga]

### Instalar Qualaroo
[Pueden usar esta guia para colocarlo por GTM.](https://help.qualaroo.com/hc/en-us/articles/201405386)

 ![qr_gtm]

[O usar esta otra guia para instalarlo directamente en el codigo fuente.](https://help.qualaroo.com/hc/en-us/articles/201405336-Installing-the-JavaScript-on-your-Site)

 ![qr_js]

¿Existe alguna diferencia entre uno y otro metodo de instalacion?

- **No.**

#### Consideraciones

- [En caso de instalar Qualaroo por GTM, es necesario tomar en cuenta un ajuste al momento de publicar las etiquetas para registrar los las respuestas directamente en Google Analytics.](https://help.qualaroo.com/hc/en-us/articles/201696503)

- [Para tener las respuestas de los cuestionarios de Qualaroo en Google Analytics se debe realizar la siguiente configuracion:](https://help.qualaroo.com/hc/en-us/articles/202028108-Publishing-Qualaroo-Data-To-Google-Universal-Analytics)
    
    1. En el Dashboard, ir a `Site Settings`.
     
     ![qr_ga_site_set]
     
    2. Activar la etiqueta de `Universal Analytics`. 
    
     ![qr_ga_check]
     
     La imagen es referencial.

- La data de eventos almacenada en Google Analytics no afecta el rebote; en ciertos casos si una sesion solo interactua con el cuestionario pero no con el sitio, el reporte de GA indicará que la sesion ha rebotado.

- En caso de tener una masa critica significativa, se puede [construir Segmentos Avanzados en Google Analytics](https://support.google.com/analytics/answer/3124493?hl=es) que hayan contestado determinada respuesta y [construir audiencias de Remarketing en base a estas audiencias.](https://support.google.com/analytics/answer/6015314)
 
 Se puede configurar un segmento de la siguiente manera:
 ![qr_ga_segment]
 
 Y crear la audiencia de Remarketing a partir de este segmento:
 ![qr_ga_audience]
 
 [Tomar en cuenta que para que una lista sea util debe tener en  Display debe tener 100 usuarios activos en los ultimos 30 dias y para que sea util en Search debe tener al menos 1,000.](https://support.google.com/adwords/answer/2472738?hl=en)
 
- [La informacion enviada desde Qualaroo hacia Google Analytics sigue un patron:](https://help.qualaroo.com/hc/en-us/articles/202028108-Publishing-Qualaroo-Data-To-Google-Universal-Analytics)
        
        When a survey is displayed to user
        Category: "Qualaroo"
        Action: "Saw survey"
        Label: The survey's name
        
        When user closes a survey
        Category: "Qualaroo"
        Action: "Closed survey"
        Label: The survey's name

        When user minimizes a survey
        Category: "Qualaroo"
        Action: "Minimized survey"
        Label: The survey's name

        When user maximizes a survey
        Category: "Qualaroo"
        Action: "Maximized survey"
        Label: The survey's name
        
        When user answers a question
        Category: "Qualaroo - THE NAME OF THE SURVEY"
        Action: The question
        Label: The answer

### Empezando con Qualaroo

El dashboard: 
Desde aqui se accede a los sitios y las opciones de configuracion de la cuenta.
 
 ![qr_dashb]

Para crear un cuestionario se debe dar clic al siguiente boton:
 
 ![qr_create]

Inmediatamente se abre **el editor del cuestionario.**
 
 ![qr_create_questions]

Aqui es donde se puede ver el flujo del cuestionario; es decir, todos los pasos.

Dentro del editor, vamos a llenar las preguntas y el mensaje final del cuestionario.

![qr_create_question1]
 
Las preguntas se veran de la siguiente manera:

 ![qr_create_nudge]

### Tipos de preguntas

**Seleccion simple**
 
 ![qr_seleccion_simple]

**Seleccion multiple**
 
 ![qr_seleccion_multiple]


##### Podemos saltar preguntas, dependiendo de la secuencia deseada en el cuestionario.
 
 ![qr_skip]


**Texto simple**
 
 ![qr_texto_simple]
 
**Texto (mas de una linea)**
 
 ![qr_texto_multiple]

**Fecha**

 ![qr_date]
 
**Net Promoter Score**

 ![qr_nps]

**Matriciales**

 ![qr_matrix]
 
 Para configurar este tipo de preguntas se llenan los campos de la siguiente manera:
 
 ![qr_matrix_rows]
 
 Se usan especialmente cuando se desea evaluar varios factores en una sola pregunta.
 Las matrices usualmente se usan para preguntas que apunten a formar [Escalas de Likert](https://es.wikipedia.org/wiki/Escala_Likert) en el analisis.
 
### Link Surveys

 Este tipo de cuestionarios se activan con el fin de ser enviados a una base. Se suele hacer por correo.
 
 Como primer paso, luego del boton "Create new survey!" elegimos Link Survey
 
 ![qr_link]
 
 Segundo paso, configurar la(s) preguntas:
 
 ![qr_link_editor]
 
 Tercer paso, definir donde aparecera el cuestionario:
 
 ![qr_link_target]
 
 Cuarto paso, definir el diseño del cuestionario:
 
 ![qr_link_edit_nudge]
 
 Penultimo paso, coger el enlace que vamos a enviar a la base:
 
 ![qr_link_link]
 
 Ultimo paso, revisar como se ve antes de enviarlo.
 
 ![qr_link_demo]
 

### [¿Que preguntas deberia hacer?¿En que casos usarlas?](https://help.qualaroo.com/hc/en-us/articles/201483927)
Se sugiere revisar este documentacion.

### [¿Cual es un ratio de respusta aceptable?](https://help.qualaroo.com/hc/en-us/articles/201484047-What-is-typically-considered-a-good-response-rate-)

- La respuesta esta entre 1 y 4 por ciento respecto a las vistas del nudge de Qualaroo en las paginas de destino.
- Y en promedio 20% en las paginas de confirmacion de compra o confirmacion de registro.

Si los ratios estan por debajo de los mencionados, se sugiere evaluar si:

- La pregunta esta bien formulada.
- Se muestra en el momento indicado.
- Se deberia mostrar a un segmento de la audiencia.


¡Con esto damos fin a Qualaroo!

![potato]

---

**Extra**

##### [Ver 60 segundos del proximo video acerca de la regla de los 5 usuarios.](http://www.youtube.com/watch?v=/qOWbkdMy1Js?t=30m10s)

<a href="http://www.youtube.com/watch?feature=player_embedded&v=qOWbkdMy1Js?t=30m10s" target="_blank"><img src="http://img.youtube.com/vi/qOWbkdMy1Js/0.jpg" alt="IMAGE ALT TEXT HERE" width="300" height="200" border="10" /></a>

**Resumen:** la regla dice que con 5 usuarios representativos de tu audiencia se pueden encontrar 80% de los puntos criticos a mejorar en la experiencia de una pagina / sitio / app.


##### [Qualaroo orientado a Conversion Rate Optimization (2m21s)](https://www.youtube.com/watch?v=ALEcoZrptvQ)

<a href="http://www.youtube.com/watch?feature=player_embedded&v=ALEcoZrptvQ" target="_blank"><img src="http://img.youtube.com/vi/ALEcoZrptvQ/0.jpg" alt="IMAGE ALT TEXT HERE" width="300" height="200" border="10" /></a>

Question guide for Qualaroo
https://www.youtube.com/watch?v=KCJRBhWiy-8&t=387s


---
[potato]: https://i.pinimg.com/originals/a2/db/bb/a2dbbbd88508277c701bd1919f6e5b12.jpg
[mt_ms_ex]: https://www.mousestats.com/docs/Attachments/Blog/micro2.png
[mt_ms_results]: https://www.mousestats.com/static/theme/salesv2/serviceScreenshots/microsurveys.gif
[mt_ms_prop_prim]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/mt_ms_create.png
[mt_ms_step1]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/mt_ms_one_choice.png
[mt_ms_step2]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/mt_ms_one_choice_2.png
[mt_ms_step3]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/mt_ms_multiple_choice.png
[mt_ms_step4]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/mt_ms_text_fields.png
[mt_ms_step5]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/mt_ms_message.png
[mt_ms_types]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/mt_ms_question_types.png
[mt_ms_actions]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/mt_ms_question_step.png
[qr_gtm]: https://help.qualaroo.com/hc/article_attachments/115006184163/Screen_Shot_2017-04-21_at_2.56.12_PM.png
[qr_js]: http://help.qualaroo.com/hc/en-us/article_attachments/200437208/Get_code_for_flawedartist.com_-_Qualaroo.png
[qr_ga]: https://help.qualaroo.com/hc/en-us/article_attachments/200525488/Events_action.png
[qr_ga_site_set]: https://help.qualaroo.com/hc/en-us/article_attachments/200452338/Dashboard_-_Qualaroo.png
[qr_ga_check]: https://help.qualaroo.com/hc/en-us/article_attachments/200536187/Recording_integration-1.png
[qr_ga_audience]: https://lh5.ggpht.com/s7F5Sm4aX-icik8kLyaWxjePxEiG-dlk_Y-r39IJGhPJX2C2MlFkTr_J1tFTmYHcAhPjRU_oeQ=w895
[qr_ga_segment]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/6_2_qr_analytics_segment_example.png
[qr_dashb]: https://help.qualaroo.com/hc/en-us/article_attachments/200446626/Dashboard_-_Qualaroo-8.png
[qr_create]: https://help.qualaroo.com/hc/en-us/article_attachments/200540177/Dashboard_-_Qualaroo-1.png
[qr_create_questions]: https://help.qualaroo.com/hc/en-us/article_attachments/200393609/Screen_Shot_2014-08-26_at_3.28.41_PM.png
[qr_create_question1]: https://help.qualaroo.com/hc/en-us/article_attachments/200494873/Create_-_Qualaroo-1.png
[qr_create_nudge]: https://help.qualaroo.com/hc/en-us/article_attachments/200393629/Screen_Shot_2014-08-26_at_3.31.23_PM.png
[qr_seleccion_simple]: https://help.qualaroo.com/hc/en-us/article_attachments/200437328/Screen_Shot_2014-02-09_at_12.38.50_PM.png
[qr_seleccion_multiple]: https://help.qualaroo.com/hc/en-us/article_attachments/200494983/Screen_Shot_2014-02-09_at_12.28.55_PM.png
[qr_texto_simple]: https://help.qualaroo.com/hc/en-us/article_attachments/200500717/Screen_Shot_2014-02-09_at_12.43.00_PM.png
[qr_texto_multiple]: https://help.qualaroo.com/hc/en-us/article_attachments/200500707/Screen_Shot_2014-02-09_at_12.40.51_PM.png
[qr_date]: https://help.qualaroo.com/hc/en-us/article_attachments/200406096/Screen_Shot_2014-02-09_at_12.45.08_PM.png
[qr_nps]: https://help.qualaroo.com/hc/en-us/article_attachments/202087306/Screen_Shot_2015-11-30_at_4.44.42_PM.png
[qr_skip]: https://help.qualaroo.com/hc/en-us/article_attachments/200495013/CreateBranching_logic_survey_-_Qualaroo.png
[qr_matrix]: https://help.qualaroo.com/hc/article_attachments/115003764566/Screen_Shot_2017-03-14_at_12.40.54_PM.png
[qr_matrix_rows]: https://help.qualaroo.com/hc/article_attachments/115003764686/Screen_Shot_2017-03-14_at_2.08.17_PM.png
[qr_link]: https://help.qualaroo.com/hc/article_attachments/115017577623/mceclip0.png
[qr_link_editor]: https://help.qualaroo.com/hc/article_attachments/115006989526/Screen_Shot_2017-05-02_at_12.35.23_PM.png
[qr_link_target]: https://help.qualaroo.com/hc/article_attachments/115006990626/Screen_Shot_2017-05-02_at_1.52.28_PM.png
[qr_link_edit_nudge]: https://help.qualaroo.com/hc/article_attachments/115006992186/Screen_Shot_2017-05-02_at_1.58.26_PM.png
[qr_link_link]: https://help.qualaroo.com/hc/article_attachments/115006980923/Screen_Shot_2017-05-02_at_2.08.39_PM.png
[qr_link_demo]: https://help.qualaroo.com/hc/article_attachments/115006992806/Screen_Shot_2017-05-02_at_2.02.21_PM.png

