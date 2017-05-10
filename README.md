Swift Module: Consumir Servicio POST de un API REST
===========

## Descripción

<p align="justify">
	Para el desarrollo de aplicaciones móviles es indispensable usar servicios. 
	Steve Jobs decía que los dispositivos móviles deberían ser una extensión o de nuestra <b>Mac</b>. Nada menos cierto el dispositivo móvil podría hacer consultas, cálculos de algoritmos pesados etc. pero debido a que nuestros recursos son limitados buscaremos aprovecharlos de la mejor manera.
	De aquí la necesidad de que tengamos un <b>Back-End</b> que se encargue de hacer las estas consultas y cálculos para entregarnos la información <b>digerida</b>, y así entregarle una respuesta rápida y eficaz al usuario.
</p>

## Framework vs API
<p align="justify">
Imagina que vives en 1970 y estás decidido a reutilizar tu código entonces crear la función seno(), coseno(), tangente(), le agregas Float obtenerRadio(diámetro: Float). Y así todas estas funciones las unes y crearas una <b>librería</b> posteriormente una empresa se interesa en el trabajo y contrata a más programadores los cuales hacen librerías para: manejo de imágenes, conexión a internet, sockets, etc. Pues el conjunto de todas estas librerías se conoce como <b>Framework</b>.
Ahora ya tienes tu framework y es más fácil para ti programar, pero te das cuenta que todavía así puedes ahorras más tiempo pues existen pasos repetitivos que te gustaría sólo <i>implementar</i>.

Supongamos que desarrollas Web y no te gusta hacer estilos (CSS) entonces programas tus funciones para que cuando tu agregues ciertas lineas a tu código tu página sea responsiva. Entoncesentonces apoyado de tu Framework haces los cálculos necesarios, tomas en cuenta todos los posibles casos, las medidas y después de mucho trabajo lo logras. Ahora cuando quieres estilos simplemente tomas y lo implementas lo que podría ser un Boostrap.

El framework está compuesto de librerías y éstas a su vez de funciones que hacen bien una sola cosa.
Las APIs se valen de estas funciones que vienen en los Frameworks y construyen una solución con un fin. Si hablamos de Construir un API Rest nos otros haríamos las consultas a la base, haríamos el tratamiento de esa información y tendríamos todo listo sólo para que el desarrollador móvil llegue y consuma esos datos de manera transparente, sin la necesidad de hacer el tratamiento de esa información (validación de login, actualización de los datos, eliminación de datos, consumo de información ordenada alfabeticamente) y menos sin la necesidad de hacer las funciones básicas de suma, conexión HTTP, algoritmos de ordenamiento como SORT etc.


Básicamente un API es algo pre-programado que nos otros sólo llegamos e implementamos.
</p>

## ¿Qué es un API REST?

<p align="justify">
Es cualquier interfaz entre sistemas que use HTTP para obtener datos o generar operaciones sobre esos datos en todos los formatos posibles, como XML y JSON.
</p>

<p align="justify">
&#9642; Protocolo cliente/servidor sin estado: cada petición HTTP contiene toda la información necesaria para ejecutarla, lo que permite que ni cliente ni servidor necesiten recordar ningún estado previo para satisfacerla. Aunque esto es así, algunas aplicaciones HTTP incorporan memoria caché. Se configura lo que se conoce como protocolo cliente-caché-servidor sin estado: existe la posibilidad de definir algunas respuestas a peticiones HTTP concretas como cacheables, con el objetivo de que el cliente pueda ejecutar en un futuro la misma respuesta para peticiones idénticas. De todas formas, que exista la posibilidad no significa que sea lo más recomendable.
</p>

<p align="justify">
&#9642; Las operaciones más importantes relacionadas con los datos en cualquier sistema REST y la especificación HTTP son cuatro: POST (crear), GET (leer y consultar), PUT (editar) y DELETE (eliminar).
</p>

<p align="justify">
&#9642; Los objetos en REST siempre se manipulan a partir de la URI. Es la URI y ningún otro elemento el identificador único de cada recurso de ese sistema REST. La URI nos facilita acceder a la información para su modificación o borrado, o, por ejemplo, para compartir su ubicación exacta con terceros. 
</p>

<p align="justify">
&#9642; Interfaz uniforme: para la transferencia de datos en un sistema REST, este aplica acciones concretas (POST, GET, PUT y DELETE) sobre los recursos, siempre y cuando estén identificados con una URI. Esto facilita la existencia de una interfaz uniforme que sistematiza el proceso con la información.
</p>

<p align="justify">
&#9642; Sistema de capas: arquitectura jerárquica entre los componentes. Cada una de estas capas lleva a cabo una funcionalidad dentro del sistema REST.
</p>

<p align="justify">
&#9642; Uso de hipermedios: hipermedia es un término acuñado por Ted Nelson en 1965 y que es una extensión del concepto de hipertexto. Ese concepto llevado al desarrollo de páginas web es lo que permite que el usuario puede navegar por el conjunto de objetos a través de enlaces HTML. En el caso de una API REST, el concepto de hipermedia explica la capacidad de una interfaz de desarrollo de aplicaciones de proporcionar al cliente y al usuario los enlaces adecuados para ejecutar acciones concretas sobre los datos.
</p>

## Herramientas

<p align="justify">
Antes de consumir los servicios nos gustaría probarlos para este fin, existen <i>clientes HTTP</i> que se instalan como <i>plugins</i> en nuestros Navegadores Web y que nos facilitan la tarea del consumo de servicios.
<p>

Para este ejemplo usaré <b>POSTMAN</b> pero existe otros como <i>Advanced REST client</i>:

<p align="center">
  <img src="https://github.com/ginppian/Swift-Modules-Consum-REST-Service-With-POST/blob/master/tuto1.png" width="568" height="320" />
</p>

<p align="justify">
También necesitaremos una URL que contenga un Servicio y nos regrese un objeto JSON.
</p>

Para este caso usaré la siguiente: 

```
https://offercity.herokuapp.com/api/mostrarEstablecimiento
```

Con el siguiente token:

```
c31e7cc5503e222a6d2ab594c845730272273a5bdcdbd1b97e29df7e19b3ecdadf021fe6a05a0da5c7046e670d89365181d15d037262822231735da484398578
```

## Desarrollo

### PASO 1

* Abrimos *POSTMAN*
* Pegamos la URL
* En este caso como enviamos un *TOKEN* necesitamos hacerlo por el método *POST* pero puede ser *GET* o cualquier otro de los descritos anteriormente.

* Nos vamos a *Body* y seleccionamos *application/x-www-form-urlencoded* que es parte de nuestras **cabeceras HTTP** o **Headers**. La definición formal sobre este parámetro del reader nos dice:

```
"The values are encoded in key-value tuples separated by '&', with a '=' between the key and the value. Non-alphanumeric characters are percent encoded: this is the reason why this type is not suitable to use with binary data (use application/form-data instead)."
```

algo así como que la forma de empaquetar los datos va a ser por duplas.

* Más abajo donde dice *New key* escribimos *token* que es el parámetro que nos pide nuestra API para devolvernos información (esto ya no es parte de las *cabeceras HTTP* sino de nuestro **Body**) y a continuación copiamos todo el token que se encuentra más arriba y lo pegamos en *value*.

* Procedemos a darle *SEND* o enviar, y se vería algo así:

<p align="center">
  <img src="https://github.com/ginppian/Swift-Modules-Consum-REST-Service-With-POST/blob/master/tuto2.png" width="981" height="705" />
</p>

### Paso 2

A continuación instalaremos un *Pod* llamado [Alamofire](https://github.com/Alamofire/Alamofire) el cual nos permite descargar la información de manera eficiente sin mucho trabajo y de manera Asincrona.

* Creamos un nuevo proyecto de Xcode
* Abrimos una terminal y nos movemos a la carpeta donde se encuentra nuestro proyecto
* Escribimos:
```
pod init
```
lo cual creará un archivo llamado *Podfile* lo abrimos
* En su *GitHub* nos dice que en el archivo *Podfile* entre el nombre de nuestro proyecto y el *end* escribamos *pod 'Alamofire', '~> 4.4'* de esta manera:

```
# Uncomment the next line to define a global platform for your project
# platform :ios, '9.0'

target 'REST' do
  # Comment the next line if you're not using Swift and don't want to use dynamic frameworks
  use_frameworks!

  # Pods for REST
  pod 'Alamofire', '~> 4.4'
end
```

guardamos y cerramos.

* A continuación escribimos:
```
pod install
```
lo cual nos instalará el pod.

### Paso 3

Implementación.

* Nos vamos a nuestro *ViewController* e importamos *Alamofire*

```
import Alamofire
```

puede que nos aparezca un circulo de ERROR pero es normal, necesitamos correr el proyecto si queremos que desaparezca.

* Agregamos los *HEADERS*

```
    let headers: HTTPHeaders = [
        "Content-Type": "application/x-www-form-urlencoded",
        "Accept": "application/json",
    ]
```

* Agregamos los *Parametros* o el *BODY*

```
    let params : Parameters = ["token": "c31e7cc5503e222a6d2ab594c845730272273a5bdcdbd1b97e29df7e19b3ecdadf021fe6a05a0da5c7046e670d89365181d15d037262822231735da484398578"]
```

* Agregamos la *URL*:
```
    let url = "https://offercity.herokuapp.com/api/mostrarEstablecimiento"
```
* A continuación dentro de nuestro constructor o *ViewDidLoad* escribimos: *Alamofire.request* a continuación ponemos un punto, y veremos que Xcode nos auto acompleta las posibles opciones:

<p align="center">
  <img src="https://github.com/ginppian/Swift-Modules-Consum-REST-Service-With-POST/blob/master/tuto3.png" width="957" height="168" />
</p>

vemos que la opción que más se acopla a nuestras necesidades es la tercera.

* A continuación llenamos los parámetros de esta manera:

```
Alamofire.request(self.url, method: .post, parameters: self.params, encoding: URLEncoding.httpBody, headers: self.headers)
```

* Una vez terminada la sentencia escribimos *.response* y veremos que nos aparecen estas opciones:

<p align="center">
  <img src="https://github.com/ginppian/Swift-Modules-Consum-REST-Service-With-POST/blob/master/tuto4.png" width="957" height="168" />
</p>

Alamofire nos lo describe de la siguiente manera:

```
// Response Handler - Unserialized Response
func response(
    queue: DispatchQueue?,
    completionHandler: @escaping (DefaultDataResponse) -> Void)
    -> Self

// Response Data Handler - Serialized into Data
func responseData(
    queue: DispatchQueue?,
    completionHandler: @escaping (DataResponse<Data>) -> Void)
    -> Self

// Response String Handler - Serialized into String
func responseString(
    queue: DispatchQueue?,
    encoding: String.Encoding?,
    completionHandler: @escaping (DataResponse<String>) -> Void)
    -> Self

// Response JSON Handler - Serialized into Any
func responseJSON(
    queue: DispatchQueue?,
    completionHandler: @escaping (DataResponse<Any>) -> Void)
    -> Self

// Response PropertyList (plist) Handler - Serialized into Any
func responsePropertyList(
    queue: DispatchQueue?,
    completionHandler: @escaping (DataResponse<Any>) -> Void))
    -> Self
```

para nuestro proposito usaremos *.responseJSON*

* En el *Complation Handler* escribiremos *{response in}*
de tal manera que nuestro código se vea así:

```
import UIKit
import Alamofire

class ViewController: UIViewController {
    
    let headers: HTTPHeaders = [
        "Content-Type": "application/x-www-form-urlencoded",
        "Accept": "application/json",
        ]
    
    let params : Parameters = ["token": "c31e7cc5503e222a6d2ab594c845730272273a5bdcdbd1b97e29df7e19b3ecdadf021fe6a05a0da5c7046e670d89365181d15d037262822231735da484398578"]
    
    let url = "https://offercity.herokuapp.com/api/mostrarEstablecimiento"
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        Alamofire.request(self.url, method: .post, parameters: self.params, encoding: URLEncoding.httpBody, headers: self.headers)
            
            .responseJSON(completionHandler: { response in
            
            })

    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }

}
```

* Pues al parecer tenemos todo listo. 
Por último para desplegar algunos resultado escribimos este código dentro del *Complation Handler*:

```
                print("resquest: \(response.request)")  // original URL request
                print("response: \(response.response)") // URL response
                print("data: \(response.data)")     // server data
                print("result: \(response.result)")   // result of response serialization
                print("result.value: \(response.result.value)")
```

de tal manera el código de nuestro *ViewController* se vería algo así:

```
import UIKit
import Alamofire

class ViewController: UIViewController {
    
    let headers: HTTPHeaders = [
        "Content-Type": "application/x-www-form-urlencoded",
        "Accept": "application/json",
        ]
    
    let params : Parameters = ["token": "c31e7cc5503e222a6d2ab594c845730272273a5bdcdbd1b97e29df7e19b3ecdadf021fe6a05a0da5c7046e670d89365181d15d037262822231735da484398578"]
    
    let url = "https://offercity.herokuapp.com/api/mostrarEstablecimiento"
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        Alamofire.request(self.url, method: .post, parameters: self.params, encoding: URLEncoding.httpBody, headers: self.headers)
            
            .responseJSON(completionHandler: { response in
                print("resquest: \(response.request)")  // original URL request
                print("response: \(response.response)") // URL response
                print("data: \(response.data)")     // server data
                print("result: \(response.result)")   // result of response serialization
                print("result.value: \(response.result.value)")
            })

    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }

}
```

### Paso 4

Si construimos y corremos nuestro código, veremos que en la consola de Xcode se despliega algo como esto:

<p align="center">
  <img src="https://github.com/ginppian/Swift-Modules-Consum-REST-Service-With-POST/blob/master/tuto5.png" width="957" height="168" />
</p>

Se despliegan los mismo resultados que en *POSTMAN* con esto podemos empezar a trabajar con esa información. El siguiente paso será desplegarla en Tablas o algún otro tipo de interface.

## Conclusiones

* Las APIs REST son indispensables en el desarrollo de aplicaciones móviles, ya que nuestro dispositivo es una *terminal* o *extensión* de algo más grande.

* El uso de herramientas como *POSTMAN* nos permite saber si la información está siendo debidamente *TRATADA* o habría que modificar algo en el *API* o *BACK-END* antes de llevarlo a la *implementación* y que sea más costoso.

* El uso de *Pods* como [Alamofire](https://github.com/Alamofire/Alamofire) nos hace más fácil la implementación, nos ahorra tiempo de producción y nos evita dolores de cabeza.

### Contacto

Twitter: @ginppian





