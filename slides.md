---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://lh3.googleusercontent.com/j7kP11pwz9CRMZ7G_91Bsp8D9uZitIBxytJTcpXL3ecJ2QeEg4-2m_kB28rKF0ISlK-3PfuYNxKjkige-VIJobFuO4PXyertOQb4NeQJRzKfnQG--dpBtolW9C21kQlY9cilOuYpNR4VpPrKmXWch-mHfphjPjCQTYImXV4gvGvwJ3my5eVFRI9A5hvYbMlK0Wj0ak5h9ejoWS0bx8Z3gY7X2_HBtIlK4bwQFThQDPZvhEaFePClwBkgEodx4nI29DKmXyI_rTYez8LqDsU6dU-E9w7E5mfL-X98XOFzZ-yj0Q_a0JIOI-Imz_Gu7lQAY2huBm5sfAylOC9C2zr6Bx6K2_q2qqyw3UxzeHcBpbJem5RCf7mQaRJ5ivDdmKL9O3HnqHLu_4mARBlYm_2t3VgR2Zmdyp3fRnbW4FhW9BbO3quNmT_49fGxLfQ4WvSFdOPfbkj3ZfZIQVh1V-2zGqUlnZyJXnGXyWaTe7ZwyvbXHt_CdHgJhXWeZfGqwLgdeTgE1W57N1el6cTBXJSdS1OohMu6mFvG0azDbj_F6CJY23qHpm5HimYWAFxt8s1PotKaZAR_JsRnFUBQMIyw90NFGEa0p720oPCTmxwaX2sKxiLGHneDZFqStEdqXTeP1KcuwACfTZZRqANozyPeZyE5Z3b6U-WiMJlhdCsX6pdQmTqYZDCISA28eEDFZw6hydXFiuTxUxGfRPVBSzVL930nhyebvFIqs3J1ujl0iil0Y_aKJ3NkA6vEjb88rjp1xFXVNYNfh38h49iV24jCp8nQnA14ovUjOVMhMw6VJHGHLW3Zy4nEiFzvR73sEEKVU1nkhADsne4uIh1XdKU7zLvfOs7XvulHisoQGhwV9m5Jc4nn0R7l5P9iY8dgZge9yEHQR3PNp-QuLYCBOHgPvlzcB6l2cMvbyOsXbDg223aaafvt4TFKX_Xk0No_bh6CmpFmWtOLuvnxIqFQDB0y=w1406-h937-no?authuser=0
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
image: https://imagenes.elpais.com/resizer/Dd_m0ujUDvbO3BAEQpcGVNwRcZI=/1200x0/arc-anglerfish-eu-central-1-prod-prisa.s3.amazonaws.com/public/CYLY3NVHQKJ6QNFCHIVCHJ5B6I.jpg
---

# ¿Por qué mockerar?

- No disponer de una api que nos sirva datos.
- Es acceso a la api no está disponible en desarrollo
- Problemas de red que nos imposibilita el acceso a la api
- Test lentos por culpa comunicación con la api

---
layout: center
class: text-center
---

# Herramientas de mocking

## JSON Server
## MSW mock server worker

---

# JSON Server

## Verbos permitidos

- GET
- POST
- PUT
- PATCH
- DELETE

## Funcionalidades

Filtrar, paginar, ordernar, buscar, middlewares, ...

## Instalación

```js
npm install json-server
```


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
  <img src="https://sigdeletras.com/images/blog/202011_fakeapi/json-server.png">
</div>

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
  <img src="https://sigdeletras.com/images/blog/202011_fakeapi/rutas.png">
</div>

---
layout: center
class: text-center
---

## Veamos ejemplo de uso
