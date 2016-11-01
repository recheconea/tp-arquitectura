# 75.73 - Arquitectura de software
## Node.JS y modelo compartido

![logo](https://github.com/recheconea/tp-arquitectura/blob/master/resources/logo.png)

## Indice

- [¿Cuáles son las características principales de Node.JS que lo diferencian de otras plataformas?](#cuales-son-las-caracteristicas-principales-de-nodejs-que-lo-diferencian-de-otras-plataformas) 
- [Patrones de uso o buenas prácticas de desarrollo sobre Node.JS](#patrones-de-uso-o-buenas-practicas-de-desarrollo-sobre-nodejs) 
- [Compartir el modelo entre el cliente y el server](#compartir-el-modelo-entre-el-cliente-y-el-server) 
- [Desarrollo con Node.JS](#desarrollo-con-nodejs) 

## ¿Cuáles son las características principales de Node.JS que lo diferencian de otras plataformas?

Las principales caracteristicas de Node.JS son:
 - Programación asincrónica
 	- **Describir caracteristica**
 - Desarrollado en javascript
 	- **Describir caracteristica**
 - Programación orientada a eventos
 	- **Describir caracteristica**
 - Uso del motor V8
 	- **Describir caracteristica**
 - Mayor velocidad de respuesta
 	- **Describir caracteristica**

## Patrones de uso o buenas prácticas de desarrollo sobre Node.JS
 
#### Siempre iniciar un nuevo proyecto con npm init

El comando _npm init_ generará un archivo package.json válido para su proyecto, deduciendo propiedades comunes del directorio de trabajo.

```
$ mkdir my-awesome-app
$ cd my-awesome-app
$ npm init --yes
```

#### Usar metodos asincrónicos

Los dos aspectos más potentes de Node.js son IO no bloqueante y runtime asíncrono. Ambos aspectos de Node.js son lo que le dan la velocidad y la solidez para atender solicitudes más rápido que otros lenguajes.

Con el fin de aprovechar estas características siempre tiene que utilizar métodos asíncronos en su código. A continuación se muestra un ejemplo que muestra la buena y mala forma de leer archivos de un sistema.

Leer un archivo del disco sincrónicamente no es una buena práctica.

```javascript
var data = fs.readFileSync('/path/to/file');
console.log(data);
// use the data from the file
```

Lee un archivo del disco asincrónicamente es una buena práctica.

```javascript
fs.readFile('/path/to/file', function (err, data) {
    // err will be an error object if an error occurred
    // data will be the file that was read
    console.log(data);
});
``` 
Cuando se invoca una función síncrona, todo el hilo de ejecución se detiene. Por ejemplo, utilizando la lectura sincronica se detiene la ejecución de cualquier otro código que podría estar ejecutándose mientras el archivo se lee. Esto significa que no se servirá a ningún usuario durante este tiempo. Si su archivo tarda cinco minutos en leerse, ningún usuario recibe servicio durante cinco minutos.

Por el contrario, de manera asincrónica se lee el archivo sin detener el hilo de ejecución. Esto significa que si su archivo tarda cinco minutos en leer en la memoria, todos los usuarios continúan recibiéndo servicio.

#### Siempre chequear errores en los Callbacks

Es conveniente chequear los errores en los callbacks debido a que cuando se ejecute esta funcion de callback, esta puede no ejecutarse de manera correcta. Al no chequear este error se estaría asumiendo que la ejecución siempre es exitosa, lo cual genera un riesgo al estar sembrando el código de posibles bus.
Un ejemplo de como utilizar esta buena práctica es el siguiente.

```javascript
myAsyncFunction({
        some: 'data'
    }, function(err, someReturnedData) {

        if(err){
            // don't use someReturnedData
            // it's not populated
            return;
        }

        // do something with someReturnedData
        // we know there was no error

    }
});
```

## Compartir el modelo entre el cliente y el server
	
	Dado una arquitectura cliente/servidor, existen varias maneras de compartir el modelo. En el caso donde el cliente sea un browser y el servidor este realizado en Node.js, una opción es utilizar desde el lado del browser una página del tipo SPA, esto

  b. ¿Es siempre conveniente compartir el modelo entre client y server? Mencionar al menos 1 caso en que lo sea, y otro caso en que no lo sea

## Desarrollo con Node.JS 

Dado el siguiente enunciado: FIUBA desea construir un sistema que permita, para un cuatrimestre dado, enumerar los cursos ofrecidos por materia y la inscripción a los cursos.

  a. Desarrolle un sistema simple utilizando Node.JS, haciendo uso de lo investigado. No se requiere que el sistema persista datos en un almacenamiento durable (i.e. Base de datos).


## Referencias
- [Node.JS](https://nodejs.org)
- [Wikipedia-Node.js](https://es.wikipedia.org/wiki/Node.js)
- [Wikipedia-SPA](https://es.wikipedia.org/wiki/Single-page_application)
- [Heroku](https://blog.heroku.com/node-habits-2016)
- [https://github.com/alanjames1987/Node.js-Best-Practices](https://github.com/alanjames1987/Node.js-Best-Practices)
- [http://thenodeway.io/](http://thenodeway.io/)
- [http://jeffamcgee.com/sharing-models-between-node-and-the-browser.html](http://jeffamcgee.com/sharing-models-between-node-and-the-browser.html)