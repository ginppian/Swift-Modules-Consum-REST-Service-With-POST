Swift Module: Consumir Servicio POST de un API REST
===========

### Descripción

<p align="justify">
	Para el desarrollo de aplicaciones móviles es indispensable usar servicios. 
	Steve Jobs decía que los dispositivos móviles deberían ser una extensión o de nuestra <b>Mac</b>. Nada menos cierto el dispositivo móvil podría hacer consultas, cálculos de algoritmos pesados etc. pero debido a que nuestros recursos son limitados buscaremos aprovecharlos de la mejor manera.
	De aquí la necesidad de que tengamos un <b>Back-End</b> que se encargue de hacer las estas consultas y cálculos para entregarnos la información <b>digerida</b>, y así entregarle una respuesta rápida y eficaz al usuario.
</p>

### Framework vs API

### ¿Qué es un API REST?

<p align="justify">
Es cualquier interfaz entre sistemas que use HTTP para obtener datos o generar operaciones sobre esos datos en todos los formatos posibles, como XML y JSON.
</p>

<p align="justify">
&#25AA; Protocolo cliente/servidor sin estado: cada petición HTTP contiene toda la información necesaria para ejecutarla, lo que permite que ni cliente ni servidor necesiten recordar ningún estado previo para satisfacerla. Aunque esto es así, algunas aplicaciones HTTP incorporan memoria caché. Se configura lo que se conoce como protocolo cliente-caché-servidor sin estado: existe la posibilidad de definir algunas respuestas a peticiones HTTP concretas como cacheables, con el objetivo de que el cliente pueda ejecutar en un futuro la misma respuesta para peticiones idénticas. De todas formas, que exista la posibilidad no significa que sea lo más recomendable.
</p>

<p align="justify">
&#25AA; Las operaciones más importantes relacionadas con los datos en cualquier sistema REST y la especificación HTTP son cuatro: POST (crear), GET (leer y consultar), PUT (editar) y DELETE (eliminar).
</p>

<p align="justify">
&#25AA; Los objetos en REST siempre se manipulan a partir de la URI. Es la URI y ningún otro elemento el identificador único de cada recurso de ese sistema REST. La URI nos facilita acceder a la información para su modificación o borrado, o, por ejemplo, para compartir su ubicación exacta con terceros. 
</p>

<p align="justify">
&#25AA; Interfaz uniforme: para la transferencia de datos en un sistema REST, este aplica acciones concretas (POST, GET, PUT y DELETE) sobre los recursos, siempre y cuando estén identificados con una URI. Esto facilita la existencia de una interfaz uniforme que sistematiza el proceso con la información.
</p>

<p align="justify">
&#25AA; Sistema de capas: arquitectura jerárquica entre los componentes. Cada una de estas capas lleva a cabo una funcionalidad dentro del sistema REST.
</p>

<p align="justify">
&#25AA; Uso de hipermedios: hipermedia es un término acuñado por Ted Nelson en 1965 y que es una extensión del concepto de hipertexto. Ese concepto llevado al desarrollo de páginas web es lo que permite que el usuario puede navegar por el conjunto de objetos a través de enlaces HTML. En el caso de una API REST, el concepto de hipermedia explica la capacidad de una interfaz de desarrollo de aplicaciones de proporcionar al cliente y al usuario los enlaces adecuados para ejecutar acciones concretas sobre los datos.
</p>

