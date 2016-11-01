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
 - Desarrollado en javascript
 - Programación orientada a eventos
 - Uso del motor V8
 - Velocidad

## Patrones de uso o buenas prácticas de desarrollo sobre Node.JS
 
#### Start every new project with npm init
 
#### Always Use Asynchronous Methods 
The two most powerful aspect of Node.js are it's non-blocking IO and asynchronous runtime. Both of these aspects of Node.js are what give it the speed and robustness to serve more requests faster than other languages.

In order to take advantage of these features you have to always use asynchronous methods in your code. Below is an example showing the good and bad way to read files from a system.

The Bad Way reads a file from disk synchronously.

```javascript
var data = fs.readFileSync('/path/to/file');
console.log(data);
// use the data from the file
``` 
The Good Way reads a file from disk asynchronously.

```javascript
fs.readFile('/path/to/file', function (err, data) {
    // err will be an error object if an error occurred
    // data will be the file that was read
    console.log(data);
});
``` 
When a synchronous function is invoked the entire runtime halts. For example, above The Bad Way halts the execution of any other code that could be running while the file is read into memory. This means no users get served during this time. If your file takes five minutes to read into memory no users get served for five minutes.

By contrast The Good Way reads the file into memory without halting the runtime by using an asynchronous method. This means that if your file takes five minutes to read into memory all your users continue to get served.




#### Always Check for "error" in Callbacks

As stated above, by convention an error is always the first parameter passed to any callback function. This is great for making sure your site doesn't crash and that you can detect errors when they happen.

Now that you know what they are you should start using them. If your database query errors out you need to check for that before using the results. I'll give you an example.

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

  a. Seleccionar una de esas formas y describirla brevemente
  b. ¿Es siempre conveniente compartir el modelo entre client y server? Mencionar al menos 1 caso en que lo sea, y otro caso en que no lo sea
aasd

## Desarrollo con Node.JS 

Dado el siguiente enunciado: FIUBA desea construir un sistema que permita, para un cuatrimestre dado, enumerar los cursos ofrecidos por materia y la inscripción a los cursos.
  a. Desarrolle un sistema simple utilizando Node.JS, haciendo uso de lo investigado. No se requiere que el sistema persista datos en un almacenamiento durable (i.e. Base de datos).


## Referencias
- [Node.JS](https://nodejs.org)
- [Wikipedia](https://es.wikipedia.org/wiki/Node.js)
- [Heroku](https://blog.heroku.com/node-habits-2016)
- [https://github.com/alanjames1987/Node.js-Best-Practices](https://github.com/alanjames1987/Node.js-Best-Practices)