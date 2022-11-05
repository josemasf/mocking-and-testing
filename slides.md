---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/imgs/bg-title.jpg
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS
css: unocss
---

# Mocking and testing

Creación de entornos para desarrollo sin dependecias externas

---

# Hola <mdi-hand-wave class="text-3xl text-yellow-400 animate-bounce "/>, Soy Jose


<div class="flex justify-center">
  <div class="flex flex-col md:flex-row md:max-w-md rounded-lg bg-white shadow-lg">
    <img class=" w-full h-96 md:h-auto object-cover md:w-48 rounded-t-lg md:rounded-none md:rounded-l-lg" src="https://avatars.githubusercontent.com/u/24436751?v=4" alt="" />
    <div class="p-6 flex flex-col justify-start">
      <h5 class="text-gray-900 text-xl text-center font-medium mb-2">Registros en Github</h5>
      <p class="text-gray-700 text-base mb-4">
        <img src="https://github-readme-stats.vercel.app/api/top-langs?username=josemasf&show_icons=true&locale=en&layout=compact" alt="josemasf" />
      </p>      
    </div>
  </div>
</div>



<div class="grid grid-cols-3 gap-4 mt-2 ">
  <div >
    <div class="text-center">
      <img
        src="assets/logos/logo-vista.png"
        class="rounded-full w-32 mb-4 mx-auto"
        alt="Avatar"
      />
      <h5 class="text-xl font-medium leading-tight mb-2">Vistalegre Solutions</h5>
      <p class="text-gray-500">10 años</p>
    </div>
  </div>
  <div >
    <div class="text-center">
      <img
        src="assets/logos/logo-ofg.png"
        class="rounded-full w-32 mb-4 mx-auto bg-white"
        alt="Avatar"
      />
      <h5 class="text-xl font-medium leading-tight mb-2">OFG</h5>
      <p class="text-gray-500">1 años</p>
    </div>
  </div>
  <div >
    <div class="text-center">
      <img
        src="assets/logos/logo-inno.png"
        class="rounded-full w-16 mb-4 mx-auto"
        alt="Avatar"
      />
      <h5 class="text-xl font-medium leading-tight mb-2">Innovations Strategies</h5>
      <p class="text-gray-500">4 años</p>
    </div>
  </div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
layout: image-right
image: /assets/imgs/tarantino.webp
---

# ¿Por qué mockear?

- No disponer de un api que nos sirva datos.
- Es acceso al api no está disponible en desarrollo
- Problemas de red que nos imposibilita el acceso al api
- Test lentos por culpa comunicación con el api

---
layout: center
class: text-center
---

# Herramientas de mocking

## JSON Server
## MSW mock server worker

---

# JSON Server

<div grid="~ cols-2 gap-4">
<div>      

  ## Verbos permitidos

  - GET
  - POST
  - PUT
  - PATCH
  - DELETE
   
</div>
<div>

  ## Funcionalidades

  Filtrar, paginar, ordenar, buscar, middlewares, ...

  ## Instalación

  ```js
  npm install json-server
  ```   
</div>
</div>


---

## Archivo JSON

```json
{
  "shop": [
    {
      "id": 1,
      "address": "Calle Juan Martín",
      "type": "frutería",
      "nombre": "Lola Castro Frutas",
      "latitude": 37.880273,
      "longitude": -4.792098
    }
  ],
  "products": [
    {
      "id": 1,
      "name": "manzanas",
      "shopId": 1
    },
    {
      "id": 2,
      "name": "peras",
      "shopId": 1
    }
  ]
}
```
---

## Comando de arranque

```ts    

  json-server --watch db.json --port 3000

```

<div>
  <img src="/assets/imgs/json-server.png">
</div>

<!--
npm init --y

npm install json-server

json-server --watch db.json --port 3000
-->

---

## Rutas personalizadas

```ts    
  //routes.json
{
  "/api/*": "/$1",
  "/shop/:type": "/shop?type=:type",
  "/shop/address/:address" :"/shop?address_like=:address"
}

```

## Script de arranque

```ts    
 json-server db.json --routes routes.json
```

<div>
  <img src="/assets/imgs/rutas.png">
</div>


---
layout: center
class: text-center
---

## Veamos ejemplo de uso


---
layout: cover
class: text-center
background: /assets/imgs/testing-bg.webp
---

# Testing

---
layout: image-right
image: /assets/imgs/first-principies.jpg
---

# Principios FIRST testing unitario

- Fast (rápido)
- Independent (independiente)
- Repeatable (repetible)
- Self-validating (auto evaluable)
- Timely (oportuno)

---

# Fast (rápido)

Una de las ventajas que nos ofrecen los test unitarios es la posibilidad de ejecutar un gran número de tests en cuestión de segundos. Todas las pruebas de nuestro proyecto, o al menos las relacionadas con el código, que estemos desarrollando deberían poder ejecutarse en un abrir y cerrar de ojos.

Esto nos posibilita ejecutar los tests muy frecuentemente y con ello detectar bugs de forma muy rápida y sencilla.

Por ejemplo, podríamos ejecutar todos los tests cada vez que hagamos un push a una rama sin preocuparnos del tiempo de ejecución de este proceso.

---

# Independent (independiente)

Por muchas pruebas unitarias que tengamos, todas deben de ser independientes de las otras.

En el momento que un test falla por el orden en el que se ha ejecutado, tenemos claro que ese test está mal desarrollado. El resultado no debe verse alterado ejecutando los tests en un orden y otro o incluso de forma independiente.

> En vitest podemos indicar  un flag para lanzar de forma random la suite de test


```ts
  vitest --sequence.shuffle
```


---

# Repeatable (repetible)

> En mi local funciona

El resultado de las pruebas debe ser el mismo independientemente del servidor en el que se ejecute. Las pruebas no deben tener dependencias de servidor, configuración de usuario, hora de ejecución…


---

# Self-validating (auto evaluable)

Uno de los puntos a favor de pruebas automatizadas es que podemos ejecutarlas simplemente al pulsar un botón o incluso hacer que se ejecuten de forma automática tras otro proceso, como podría ser un push a una rama.

Todo esto podría pasar mientras nosotros estamos realizando otra tarea, sin preocuparos de dicha ejecución.


---

# Timely (oportuno)

Esta última característica se basa en cuándo deberíamos tener desarrolladas las pruebas, que deben estar desarrolladas lo antes posible y siempre antes de subir código a producción.

Debemos evitar dejarlas para el final por dos simples motivos:

- No podremos realizar pruebas de regresión durante la fase de desarrollo.
- Una vez tenemos el código funcionando se suelen buscar excusas para dedicar el tiempo a otras tareas y no a escribir tests.


---
class: text-center
---

# Testing library & Vitest

  <div grid="~ cols-2 gap-2  content-center" m="-t-2">  

  Vitest test runner de Vite 

  Testing-library suite de paquetes para el testing UI centrado en el usuario
  <div class="grid place-content-center">
  	<img border="rounded" class="h-48" src="/assets/imgs/vitests.png">
  </div>
  <div class="grid place-content-center">
  	<img border="rounded" class="h-48" src="/assets/imgs/testing-lib.jpg">
  </div>
  </div>


---
layout: image-right
image: /assets/imgs/vitest-logo.png
---

# Vitest

- Misma configuración para test, dev y producción
- Multiplataforma Vue, React, Svelte, ...
- Jest, Chai, happy-dom
- Tests concurrentes
- Multihilo
- Muy rápido

---
layout: image-right
image: /assets/imgs/testing-lib.svg
---

# Testing-library

El foco en esta librería está puesto en el usuario, y por ello los tests están enfocados a como un usuario percibe la aplicación

Esto nos permite no estar acoplados a detalles de implementación que en futuros refactores nos harían que se rompiesen nuestros test

> Entorno UI muy potente

Debemos evitar:

- Estado interno de un componente
- Métodos internos de un componente
- Métodos de ciclo de vida de un componente
- Componentes secundarios

---
layout: center
class: text-center
---

## Veamos ejemplo de uso

---
layout: image-right
image: /assets/imgs/msw.jpg
---

# Mock Service Worker

Mock Service Worker es una biblioteca de simulación de API para el navegador y Node.js que utiliza un Service Worker para interceptar las solicitudes que realmente sucedieron.

Esto significa que no hay solicitudes de resguardos de clientes y una resiliencia inigualable cuando se trata de solicitar integridad, ya que su aplicación ahora realiza solicitudes de la misma manera que lo hace en producción.

---

<div>
	<img src="/assets/imgs/msw-flow.png" class="h-full bg-white" />
</div>
