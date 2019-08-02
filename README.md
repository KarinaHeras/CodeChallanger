Damos por hecho que tenemos instalado Node y npm

## Comandos usados:

Instalamos el vue cli
`npm install -g vue-cli`

Usamos el cli para crear el esqueleto de nuestra app, de la manera mas sencilla posible, usando el webpack-simple como ejemplo sobre el que iterar luego

`vue init webpack-simple vue-axios`

Esto nos crea un ejemplo dentro de una carpeta, tendremos que hacer:

`cd nombre-de-la-carpeta`
`npm install`

Comprobemos si funciona:

`npm run dev`

Nos habrá abierto el navegador y veremos la pagina de ejemplo.

Instalamos Axios:

`npm install axios --save`

Para que funcione los estilos bootstrap dentro de
App.vue

Tenemos que añadir en index.html:

`<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">`
