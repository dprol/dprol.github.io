---
layout: post
title: Riesgos de la anonimización de datos
description: >
  Con la palabra anonimización se reconoce el dato disociado, como aquel que no permite la identificación de un afectado o interesado.
excerpt_separator: <!--more-->
---
Estos son algunos ejemplos de riesgos referentes a la preservación de la privacidad o anonimización que consiste en alterar o introducir ruido en los datos para que la reidentificación de los usuarios no sea posible:
<!--more-->

* Ejemplo 1: A partir de las compras obtener el cliente que ha realizado las compras.

  Campos:

  - order_id: identificador de la compra
  - user_id: identificador del cliente
  - order_dow: el día de la semana en el que la compra fue realizada
  - order_hour_of_day: la hora del día en la que la compra fue realizada
  - days_since_prior: los días que pasaron desde la última compra
  - product_id: identificador del producto
  - product_name: nombre del producto
  - add_to_cart_order: orden en el cual cada producto fue añadido al carro
  - reordered: 1 si el producto ya había sido comprado, 0 si no

Riesgos:

El contexto puede llevar a la identificación. Por ejemplo, en el caso de que en este sitio de compras online se puedan dejar reseñas, aunque elimines el username y los IDs sean aleatorios, no deja de ser posible establecer una relación entre este sitio de compras y un usuario de amazon con reseñas similares.

Vemos que entre los campos no se encuentran datos que pueden ser considerados de identificación personal como nombre, fecha de nacimiento, número de teléfono, número de cédula de ciudadanía, correo electrónico o dirección de domicilio pero podemos saber muchas cosas de alguien sin que nos proporcione estos datos. Es decir, estamos dejando rasgos nuestros a la plataforma que otras pueden aprovechar para hacer match con los datos que tengan de ti. La conclusión aquí es que solo eliminar los nombres no hace nada por la privacidad y anonimización de los datos.

En el caso de que se almacenemos transacciones anonimizadas pero atribuidas a un user id, podemos encontrarnos otra base de datos dentro de la misma empresa que también haga un match entre tu user id y datos personales por lo que te vuelves indentificable.



* Ejemplo 2: Clientes y compras que han realizado en el último año.

  Campos:

  - order_id: identificador de la compra
  - user_id: identificador del cliente
  - order_dow: el día de la semana en el que la compra fue realizada
  - order_hour_of_day: la hora del día en la que la compra fue realizada
  - days_since_prior: los días que pasaron desde la última compra
  - product_id: identificador del producto
  - product_name: nombre del producto
  - add_to_cart_order: orden en el cual cada producto fue añadido al carro
  - reordered: 1 si el producto ya había sido comprado, 0 si no
  - order_date: fecha en la que han realizado la compra

Riesgos:

Un riesgo para la empresa es el siguiente: quieres anonimizar los datos pero tampoco quieres data no relevante por lo que tienes que mantener relaciones lógicas entre los datos para tomar decisiones informadas por esos datos.

Tras la anonimización existe siempre un riesgo de reidentificación de la información, (lo que hoy es anónimo dentro de 5 años puede que no lo sea por el avance de la tecnología) lo que nos obliga a realizar un análisis de riesgos para eliminarlo o minimizarlo (riesgo residual aceptable), e incluso realizar una evaluación de impacto.

Que los registros puedan vincularse a uno o varios interesados, es decir, que las compras de un ID puedan vincularse.

* Ejemplo 3: A partir del barrio de un conjunto de datos queremos estimar el coste máximo que pueden realizar.

  Campos:

  - Zipcode: código postal
  - id: indentificador de la propiedad
  - home_name: nombre de la propiedad
  - neighbourhood: barrio
  - neighbourhood_group: distrito
  - city: ciudad
  - state: comunidad autónoma o estado
  - country: país
  - country_code: código del país
  - latitude: latitud
  - ongitude: longitud
  - Home: nombre de la propiedad
  - List Price: precio de compra
  - Square Feet: superficie
  - Days-on-market: cuántos días lleva en el mercado
  - Size: tamaño
  - Location: ubicación
  - Number of bedrooms/bathrooms: número de habitaciones/baños
  - Home type: tipo de casa

Riesgos:

Que los registros del barrio permitan singularizarse en uno o varios interesados, es decir, que podamos extraer de este dataset algunos registros que identifiquen a una persona. La K-anonimidad puede ser útil para resolver este problema de la singularidad, pues los mismos atributos son compartidos por K usuarios y por lo tanto no es posible señalar unívocamente a un individuo dentro de un grupo de K usuarios.

Que del análisis de los registros de los barrios algunos o todos puedan inferirse a un usuario. En este caso, los datos utilizados para el análisis de datos se anonimizan para los propósitos del análisis aunque existe riesgo porque al estar todos los individuos en un mismo grupo, si el atacante conoce a qué grupo pertenece un individuo le será fácil extraer valor de esta identificación. Por ejemplo, si el atacante conoce que un individuo de 40 años de edad, con residencia en X ciudad, fue incluido en este análisis, sabrá con absoluta certeza que se encuentra en el rango de 40-49 y, por tanto, vive en X barrio por el nivel de renta medio en ese barrio.
