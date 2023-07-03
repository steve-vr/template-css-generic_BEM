# template-css-generic_BEM
Development of multifunctional css with methodology BEM

####Antes de ejecutar esta prueba:
- Instala live SASS https://www.youtube.com/watch?v=MQAMyk1hIj0&ab_channel=divcode
- Ejecuta "watch sass" en todos los archivos scss de la carpeta "exampleheaders"
- Ahora ya puedes realizar la prueba

####__Prueba__
* Ingresa a exampleheaders.html
* **Nota:** Los headers son independientes y tienen los mismo nombres de clase.
* __Como 1ra prueba de lo mencionado anteriormente puedes colocar un bloque html como este:__
```
    <div class="latinosbet">
        ......
    </div>
```
   * 3.1.- Este bloque lo ingresas dentro del bloque coliseosport, aqui un ejemplo:
```
    <div class="coliseosport">
        <header class="header">
            ....
        </header>
        <div class="latinosbet">
            <header class="header">
            .....
            </header>
        </div>
    </div>
```
   * 3.2.-Como se puede observar no hay ningun tipo de conflicto css por mas de que tengan el mismo nombre de clases como  **```.btn .login o .btn .singup```** 
    y esto es debido a que **```<div class="coliseosport">```** y **```<div class="latinosbet">```** tienen su propio **contexto css**.

4.- Para entender mejor lo que significa "**contexto css**", inspeccione la pagina y seleccione el bloque **```<div class="coliseosport"> <header class="header">```**.

5.- Al seleccionar este elemento y al observar sus styles puede visualizar **```".coliseosport .header { ... }```**", haga lo mismo para los diferentes elementos, EJ: **```.latinosbet .header { ... }, .goldenbet .header { ... }```**.

6.- Cada uno de esto tiene declarado al elemento padre o elemento principal de   todo el bloque sea:  **```.latinosbet, .goldenbet```**, etc y esto significa que el diseño, tamaño, o cualquier otra carateristica de un boton, selector, input, etc, va a depender del elemento padre principal para poder ser modificado solo si se encuentra dentro de este.

7.- __¿Por que declarar de esta manera mi estructura html y css?__
   * 7.1.- Contar con un orden y control para las estructuras html y css, para asi evitar **"desarrollar paginas desde 0"**.
   * 7.2.- Desarrollar las paginascon un patron definido para todo, **ya no necesitaremos preguntar que se hizo en "X" pagina o por que se hizo de esta manera**,lo cual ahorra MUCHO PERO MUCHO TIEMPO, menos conflictos en caso uno tenga que agregar cosas nuevas y menos ESTRES :)
   * 7.3.- Las paginas con las que trabajamos cuentan con integraciones de otras paginas desarrolladas(lobby-casino por ejemplo) y en caso que esta pagina tenga css globalizado con estilos diferentes como por ejemplo: "**```a{ color: red;}```**" , estos estilos sobreescribirian lo que tenemos y nos veriamos forzados a colocar **!important** lo cual ❌**NO SE DEBE NI DEBERIA DE COLOCARSE**❌, por ello la importancia de los "contextos css".(puedes ver este mismo ejemplo de la etiqueta "a" en https://coliseosport.com y como se ve afectado al no contar con un **contexto css**.

###Estructura SCSS

En la carpeta **template-generic** tenemos los siguientes archivos:
* _variables.scss
* _global.scss
* _mixins.scss
* _placeholder-selectors.scss


#####_variables.scss
* Archivo enfocado almancenar variables de sass con estilos predeterminados, la misma cuenta con la variable **$page** esta tiene condicionales @if @else con las cuales uno puede declarar variables especificas para esa **"page"**.
* Para mas detalles ingresa a **components/_variables.scss**
#####_global.scss
* Archivo enfocado en el manejo global de las principales clases css para los elementos como "button", "select", "input", ....
* El **#{$body}**  es el nombre que se declara para el contexto en el cual se encuentra.
* Ej: **$body** : ".coliseosport"; 
* Ingresa a **css/exampleheaders/style-coliseo.scss** para mas detalles.
#####_mixins.scss
* Creamos componentes reutilizables, con la opcion de que estos pueden cambiar dependiendo de los parametros que contenga, similar a una funcion de JS
#####_placeholder-selectors.scss
* Creamos componentes reutilizables que solo exiten cuando un los declara directamente en una clase css


__PROXIMAMENTE__:
* Explicacion y funciones que cumpliran los mixins.
* Como es que atravez de los mixin el desarrollo de paginas se reduce.
* Sistema de plantillas a a travez de los mixins(actualmente esta funcionando con los ```.header```)

NOTAS:  
clase "link" usualmente es para los links y la lista de links de lo footers
en caso de usar boostrap podemos omitir algunas cosas escritas aqui, dependera y esta por verse aun
-por temas de rendimiento siempre verificar si los logo o imagenes extra pesan mas de 1mb, solo las que si puedan hacerse como el logo 

La propiedad disabled se puede utilizar en varias etiquetas HTML para deshabilitar el comportamiento o la interacción con los elementos. Algunas de las etiquetas HTML que admiten la propiedad disabled son:

-Disabled - (in process)
**```✅<button> ✅<input> ✅<select>```**
**```❌<textarea> ❌<optgroup> ❌<option>```**
```
    in mode default:
      color: inherit
      background-color:inherit;
    in mode specific:
      color: $color-disabled;
      background-color : $bgc-disabled;  
```
-!!!PROHIBIDO USAR HEIGHT: autowellfix, EN SAGARIA TOMA EL TAMAÑO TOTAL - 