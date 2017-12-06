# https://goo.gl/tNjs7W

## [Google Optimize](https://www.google.com/analytics/optimize/)

Es una herramienta para realizar "experimentos" y determinar estadísticamente si la hipótesis generadas por el analista aplica para el público objetivo de el sitio o APP.

[A modo de resumen, es una herramienta que nos ayuda a encontrar el mensaje adecuado para nuestro público objetivo.](https://services.google.com/fh/files/misc/case-study-all-killer-no-filler-the-next-web-finds-the-right-message-with-google-optimize-360.pdf)


Antes de usar la herramienta vamos a aprender a generar hipótesis:

### Hipótesis
La fórmula es:

Si________[ hago esto ]________,entonces ________ [ esto ] ________ va a pasar. 

Ejemplo:

Si **cambio la imagen principal por una más vendedora**, entonces **el porcentaje de rebote bajará 50%**.

#### [Tips para generar hipótesis eficientes](https://www.sciencebuddies.org/blog/a-strong-hypothesis)

---
### Iniciar sesión en Optimize 
https://optimize.google.com/optimize/home/

Deben tener una cuenta de Google (Gmail o corporativo) para poder acceder a la herramienta. 

### Comparación entre versión Free vs 360

<table class="nice-table">
  <thead>
    <tr>
      <th> </th>
      <th class="align-center">Optimize</th>
      <th class="align-center">Optimize 360</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pensado para</th>
      <td class="align-center">Pequeñas y medianas empresas que van a empezar a experimentar.</td>
      <td class="align-center">Empresas y negocios más grandes que necesitan pruebas más sofisticadas.</td>
    </tr>
    <tr>
      <th>Pruebas A/B</th>
      <td class="align-center">√</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Integración nativa con Google Analytics</th>
      <td class="align-center">√</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Segmentación básica de URL</th>
      <td class="align-center">√</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Segmentación según el comportamiento del usuario y la tecnología</th>
      <td class="align-center">√</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Segmentación geográfica</th>
      <td class="align-center">√</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Segmentación técnica (JavaScript, cookies, capa de datos)</th>
      <td class="align-center">√</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Segmentación por audiencia de Google Analytics</th>
      <td class="align-center">–</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Compatibilidad con aplicaciones web</th>
      <td class="align-center">√</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Pruebas multivariante (PMV)</th>
      <td class="align-center">Hasta 16 combinaciones.</td>
      <td class="align-center">Hasta 36 combinaciones.</td>
    </tr>
    <tr>
      <th>Objetivos del experimento</th>
      <td class="align-center">Hasta 3 objetivos preconfigurados.</td>
      <td class="align-center">Hasta 10 objetivos preconfigurados.<br>
      Se pondrán a su disposición objetivos adicionales una vez haya comenzado a utilizarlo.</td>
    </tr>
    <tr>
      <th>Experimentos simultáneos</th>
      <td class="align-center">Hasta 3.</td>
      <td class="align-center">Más de 100.*</td>
    </tr>
    <tr>
      <th>Administración</th>
      <td class="align-center">Administración básica con usuarios ilimitados.</td>
      <td class="align-center">Administración de Suite Analytics 360.</td>
    </tr>
    <tr>
      <th>Servicios de implementación</th>
      <td class="align-center">–</td>
      <td class="align-center">√</td>
    </tr>
    <tr>
      <th>Asistencia y servicios</th>
      <td class="align-center">
      <p>Centro de ayuda de autoservicio y<br>
        foro de la comunidad.<br>
        <a href="https://www.google.com/analytics/partners" target="_blank">Partners certificados</a></p>
      </td>
      <td class="align-center">Servicio, asistencia y<br>
      acuerdos de nivel de servicio para empresas.</td>
    </tr>
    <tr>
      <th>Opciones de pago</th>
      <td class="align-center">Gratuito.</td>
      <td class="align-center">Facturación mensual.</td>
    </tr>
  </tbody>
</table>

<p>* Hasta 24 experimentos por vista de Analytics de forma predeterminada. Existe la posibilidad de solicitar más experimentos.</p>

##### [Más información en este enlace.](https://support.google.com/360suite/optimize/answer/7084762?hl=es&ref_topic=6314903)


---


## Tipos de experimentos

### A/B/n

![abn]

#### Pregunta: ¿Cuál versión ganó? 

Versión 1

![abn1]

Versión 2

![abn2]

**Pista: la versión ganadora tuvo mejores resultados en Desktop, pero perdió en Mobile.**

Marquen sus resultados en la siguiente página:
https://www.behave.org/test/hero-image-won-desktop-lost-mobile/


### [Crear una prueba ABn](https://support.google.com/360suite/optimize/answer/6211930)

---



### Redirect tests

![redirect]

#### Pregunta: ¿Cuál versión ganó? 

Version 1

![redirect1]

Versión 2

![redirect2]

Votar en el siguiente enlace: https://www.behave.org/test/format-drove-conversions/

En un rest de redirección, la estructura suele ser la siguiente:

Original – www.example.com/landing1

Variante – www.example.com/landing2

### [Crear una test de redirección](https://support.google.com/360suite/optimize/answer/6361119)
---


### Tests Multivariados

![mvt]

Ejemplo:

En la imagen anterior se tiene: 
2 secciones
3 imágenes principales a probar

Dando un total de 6 combinaciones posibles (3x2)

### [Crear un Test Multivariado](https://support.google.com/360suite/optimize/answer/6370723)

---
Información útil:

Imagen a usar para el test ABn
![util1]

Color del botón:
rgb(0, 54, 74)

--- 
### Reportes en Optimize

Vista general:

![reporte1]

Performance por cada variación:

![reporte]



[abn]: https://lh3.googleusercontent.com/PTDoVeRc36TC8XkrGbtZ-3ktY1VISHxTIxh2esgy1xJgmTg0Q9NeGYO5ETAkCQ=w250
[abn1]: https://www.behave.org/wp-content/uploads/2017/10/version-a-loser.png
[abn2]: https://www.behave.org/wp-content/uploads/2017/11/version-b-winner.jpg
[redirect]: https://lh3.googleusercontent.com/_GrZ6NO0PPKTJ6UME2MGZyUV_YRZM-YcbGqA6u4dT6nKwX1zom5Msrp3jIDm9Zzzzmw=w300
[redirect1]: https://www.behave.org/wp-content/uploads/2016/10/Verizon-TOTW-A-768x572.jpg
[redirect2]: https://www.behave.org/wp-content/uploads/2016/10/Verizon-TOTWB-768x443.jpg
[mvt]: https://lh3.googleusercontent.com/0DFXWcktU0F_vLLCehjRBWT3zuBs-uelTtogk1tV4HxJUpH8t4m1BzFSTtodDQjDpw=w500

[util1]: https://media.licdn.com/media/AAEAAQAAAAAAAAwQAAAAJDhlYmIyMWNlLTY4MjktNDkzMS05MTI1LTJiMWNlZDNhNTA4Zg.jpg
[reporte]: https://lh3.googleusercontent.com/F9jUVXvr-ldtDYlqavdhl8jWS3OMXcwaBh8x3A_1BJSGuS3NfI1OVx4nsj2g6v08PIo=w1200
[reporte1]: https://lh3.googleusercontent.com/UJUYYurt2THv7e-x-OYsEqOMkLJEIit5MGMD3DWoHa9G_iCQ80zlVJH5NNX-qDDgtG4=w700
