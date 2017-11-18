# *Material de la clase: https://goo.gl/DyioCv*

# Tamaño de muestra


¿Por que es necesario tomar una muestra ahora que todas las herramientas estan en la nube y pueden escalar sin mayor complicacion? :weary:

Todo se resume a numeros:

   https://www.mousestats.com/pricing a Nov-17
   ![mt_price]

   https://qualaroo.com/pricing/ a Nov-17
   ![qr_price]

:moneybag: No se tomara al presupuesto como parte del problema; sin embargo, asumiremos que trabajaremos con las membresias gratuitas.

		Es recomendable definir el tamaño de la muestra
		para que el analisis de los mapas y cuestionarios
		sea lo mas significativo estadisticamente, 
		es decir, para tomar decisiones sobre datos
		cualitativos en base a un indicador numerico.


## Actividad: Conseguiremos data para hallar la poblacion

:warning: Se sugiere [solicitar acceso a la cuenta Demo
de Analytics](https://support.google.com/analytics/answer/6367342#access) para seguir los siguientes ejemplos.
		
Con el acceso a la cuenta DEMO daremos los siguientes pasos:

		Behavior / Site Content / All pages / Content Grouping = Product Categories

   ![ga_prod_cat]

[Con este enlace se puede acceder a los mismos datos](https://analytics.google.com/analytics/web/?utm_source=demoaccount&utm_medium=demoaccount&utm_campaign=demoaccount#report/content-pages/a54516992w87479473p92320289/%3Fexplorer-segmentExplorer.segmentId%3Danalytics.pageGroup2%26explorer-table.plotKeys%3D%5B%5D/) y al dar clic al grupo con mayor cantidad de "entrances" [observamos el grupo de paginas donde podemos lanzar los heatmaps o cuestionarios.](https://analytics.google.com/analytics/web/?utm_source=demoaccount&utm_medium=demoaccount&utm_campaign=demoaccount#report/content-pages/a54516992w87479473p92320289/%3Fexplorer-table.plotKeys%3D%5B%5D%26_r.drilldown%3Danalytics.pageGroup2%3ABrands/)

   ![ga_brand_yt]

Con esto hemos hallado el tamaño de la poblacion, para las páginas con pocas sesiones se sugiere primero encontrar el tamaño de la muestra y luego implementarla al 100% de sesiones. Para las páginas con gran cantidad de sesiones, se sugiere solo aplicar los heatmaps o cuestionarios hasta donde la formula indique.
   
   
## Calculando el tamaño de la muestra

   ![sample]


## [Para calcular la muestra en base a los grupos de paginas usaremos calculadoras online](https://www.surveymonkey.com/mp/sample-size-calculator/).

Siguiendo el ejemplo:

| Indicador | Valor |
| --------- |:-----:|
| Poblacion | 18,797 |
| Error     | 1% |
| Proporcion | 50%  |
| Nivel Conf | 99%  |


**El resultado da una muestra de 8,827 resultados** para los mapas o cuestionarios en la pagina 	

**/google+redesign/shop+by+brand/youtube**

https://shop.googlemerchandisestore.com/Google+Redesign/Shop+by+Brand/YouTube
![sample_yt]


| Supuesto | Respuesta |
| -------- |:---------:|
| Con 8,827 clics el Heatmap es estadisticamente significativo | No |
| Con data de 8,827 personas el Heatmap es estadisticamente significativo | Si |
| Esto solo aplica a Heatmaps | No |
| Esto aplica a cuestinonarios tambien | Si |
| Esto aplica para analizar data de reportes de GA | Depende |




---

Ir a [Mapas de calor](https://github.com/acamposc/managementsociety/blob/master/herramientas/4_heatmaps.md)

[mt_price]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/3_mousestats_pricing.png 
[qr_price]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/3_qualaroo_pricing.png
[ga_prod_cat]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/3_product_category.png
[ga_brand_yt]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/3_brand.png
[sample]: https://faculty.elgin.edu/dkernler/statistics/ch01/images/strata-sample.gif
[sample_yt]: https://github.com/acamposc/managementsociety/blob/master/herramientas/img/3_sample_yt.png
