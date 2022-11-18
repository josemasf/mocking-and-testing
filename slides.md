---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /imgs/bg-title.jpg
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
favicon: 'https://josemariasantos.com/favicon.svg'
fonts:
  sans: 'Montserrat'
  serif: 'Slabo'
  mono: 'Fira Code'
---

# Mocking and testing

<div class="text-slate-200">
Creación de entornos para desarrollo y testing sin dependecias externas
</div>

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
  <div>
    <div class="bg-slate-700">
        <div class="max-w-sm rounded overflow-hidden shadow-lg border-white">
        <img class="w-full" src="/logos/logo-vista.png" alt="Vistalegre">
        <div class="px-6 py-4 text-center">
          <div class="font-bold text-xl mb-2">Vistalegre Solutions</div>    
        </div>
        <div class="px-6 pt-4 text-center">
          <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">2007 - 2017</span>    
        </div>
      </div>
    </div>
  </div>
  <div>
    <div class="bg-slate-700">
      <div class="max-w-sm rounded overflow-hidden shadow-lg border-white">
        <img class="w-full" src="/logos/logo-ofg.png" alt="OFG">
        <div class="px-6 py-4 text-center">
          <div class="font-bold text-xl mb-2">OFG</div>    
        </div>
        <div class="px-6 pt-4 text-center">
          <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">2017 - 2018</span>    
        </div>
      </div>
    </div>
  </div>
  <div>
    <div class="bg-slate-700">
      <div class="max-w-sm rounded overflow-hidden shadow-lg border-white">
        <img class="w-full " src="/logos/logo-inno.png" alt="OFG">
        <div class="px-6 py-4 text-center">
          <div class="font-bold text-xl mb-2">Innovation strategies</div>    
        </div>
        <div class="px-6 pt-4 text-center">
          <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">2018 - ?</span>    
        </div>
      </div>
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
image: /imgs/tarantino.webp
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
  <img src="/imgs/json-server.png">
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
  <img src="/imgs/rutas.png">
</div>


---
layout: center
class: text-center
---

## Veamos ejemplo de uso


---
layout: cover
class: text-center
background: /imgs/testing-bg.webp
---

# Testing

---
layout: image-right
image: /imgs/first-principies.jpg
---

# Principios FIRST testing unitario

- Fast (rápido)
- Independent (independiente)
- Repeatable (repetible)
- Self-validating (auto evaluable)
- Timely (oportuno)

---
layout: image-right
image: /imgs/flash.jpg
---
# Fast (rápido)

Una de las ventajas que nos ofrecen los test unitarios es la posibilidad de ejecutar un gran número de tests en cuestión de segundos. Todas las pruebas de nuestro proyecto, o al menos las relacionadas con el código, que estemos desarrollando deberían poder ejecutarse en un abrir y cerrar de ojos.

Esto nos posibilita ejecutar los tests muy frecuentemente y con ello detectar bugs de forma muy rápida y sencilla.

Por ejemplo, podríamos ejecutar todos los tests cada vez que hagamos un push a una rama sin preocuparnos del tiempo de ejecución de este proceso.

<!--
- Test runner rápido
- No tener dependencias que bloqueen
-->

---
layout: image-right
image: /imgs/independiente.jpg
---

# Independent (independiente)

Por muchas pruebas unitarias que tengamos, todas deben de ser independientes de las otras.

En el momento que un test falla por el orden en el que se ha ejecutado, tenemos claro que ese test está mal desarrollado. El resultado no debe verse alterado ejecutando los tests en un orden y otro o incluso de forma independiente.

> En vitest podemos indicar  un flag para lanzar de forma random la suite de test


```ts
  vitest --sequence.shuffle
```
---
layout: image-right
image: /imgs/repetible.jpg
---

# Repeatable (repetible)

> En mi local funciona

El resultado de las pruebas debe ser el mismo independientemente del servidor en el que se ejecute. Las pruebas no deben tener dependencias de servidor, configuración de usuario, hora de ejecución…


---

# Self-validating (auto evaluable)

Uno de los puntos a favor de pruebas automatizadas es que podemos ejecutarlas simplemente al pulsar un botón o incluso hacer que se ejecuten de forma automática tras otro proceso, como podría ser un push a una rama.

Todo esto podría pasar mientras nosotros estamos realizando otra tarea, sin preocuparos de dicha ejecución.

<div class="grid place-content-center">
  <img src="/imgs/test-pr.png" />
</div>

---
layout: image-right
image: /imgs/oportunos.jpg
---

# Timely (oportuno)

Esta última característica se basa en cuándo deberíamos tener desarrolladas las pruebas, que deben estar desarrolladas lo antes posible y siempre antes de subir código a producción.

Debemos evitar dejarlas para el final por dos simples motivos:

- No podremos realizar pruebas de regresión durante la fase de desarrollo.
- Una vez tenemos el código funcionando se suelen buscar excusas para dedicar el tiempo a otras tareas y no a escribir tests.

<!--
No romper cosas antiguas desarrolladas
-->

---
class: text-center
---

# Testing library & Vitest

  <div grid="~ cols-2 gap-2  content-center" m="-t-2">  

  Vitest test runner de Vite 

  Testing-library suite de paquetes para el testing UI centrado en el usuario
  <div class="grid place-content-center">
  	<img border="rounded" class="h-48" src="/imgs/vitests.png">
  </div>
  <div class="grid place-content-center">
  	<img border="rounded" class="h-48" src="/imgs/testing-lib.jpg">
  </div>
  </div>


---
layout: image-right
image: /imgs/vitest-logo.png
---
# Vitest

- Misma configuración para test, dev y producción
- Multiplataforma Vue, React, Svelte, ...
- Jest, Chai, happy-dom
- Tests concurrentes
- Multihilo
- Muy rápido

> Entorno UI muy potente

---

# Flag que más uso en cli


```
--ui
```
Abre el entorno visual donde podemos editar tests, ver errores de consola o log que tengamos.

```
--environment jsdom
```
Indica que debe emular el DOM. Por defecto corre sobre node a secas.

```
--mode XXX
```
Indicamos el modo en el que queremos usar los test. DEV, PROD, PERSONALIZADO, ...

```
run
```
Sin guiones, lanzará los tests sin el modo watch. Una vez que cabe el script se para.

```
--coverage
```
Analiza cuanto cubren nuestros tests sobre el código.

---

# En los tests

- `describe` nos permite envolver test relacionados
- `it` es un alias para la palabra test, simplifica lectura de enunciado
- `expect` lo usamos para evaluar algo
- `beforeAll` - `afterAll` - `beforeEach` - `afterEach` ejecutar algo antes o depués de los test. Limpiar mocks


---
layout: image-right
image: /imgs/testing-lib.svg
---

# Testing-library

El foco en esta librería está puesto en el usuario, y por ello los tests están enfocados a como un usuario percibe la aplicación

Esto nos permite no estar acoplados a detalles de implementación que en futuros refactores nos harían que se rompiesen nuestros test


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
image: /imgs/msw.jpg
---

# Mock Service Worker

Mock Service Worker es una biblioteca de simulación de API para el navegador y Node.js que utiliza un Service Worker para interceptar las solicitudes que realmente sucedieron.

Esto significa que no hay solicitudes de resguardos de clientes y una resiliencia inigualable cuando se trata de solicitar integridad, ya que su aplicación ahora realiza solicitudes de la misma manera que lo hace en producción.

---

<div class="h-full mb-3" >
	<img src="/imgs/msw-flow.png" class="scale-75 bg-white" />
</div>

---

# Mocks

1. Directorio de mocks

```
src/mocks
```

2. Handlers

```
src/mocks/handlers.js
```

---

# Handlers


``` ts
const handlers = [
  rest.get('https://ipay.stage.iberostar.com/api/MasterData/Hotels', (req, res, context) => {
    return res(context.status(200), context.json(mockServer.Hotels))
  }),
  rest.get('https://ipay.stage.iberostar.com/api/MasterData/Hotels/:id', (req, res, context) => {
    const { id } = req.params
    return res(context.status(200), context.json(mockServer.Hotels[id - 1]))
  }),  
  rest.get(
    'https://ipay.stage.iberostar.com/api/Ingenico/HotelConfiguration?hotelId=:idHotel&accountId=:idAccount',
    (req, res, context) => {
      const { idHotel } = req.params
      if (idHotel === 2) return res(context.status(404), context.text('No configurations and default merchant found'))
      else return res(context.status(200), context.json(mockServer.Summary))
    }
  ),  
  rest.put('https://ipay.stage.iberostar.com/api/Ingenico/HotelConfiguration', (req, res, context) => {
    return res(context.status(200), context.json(req.bodyUsed))
  }),
  rest.post('https://ipay.stage.iberostar.com/api/Ingenico/HotelConfiguration', (req, res, context) => {
    return res(context.status(200), context.json(req.bodyUsed))
  }),
]

```

---

<div grid="~ cols-2 gap-4">
  <div>
    Futura versión con breaking changes en response.
  </div>
 <div>     
  <Tweet id="1592826838073880576" scale="0.85"  />
  </div>
</div>

---

# Utilidad para test y para dev

> npm install msw --save-dev

<div grid="~ cols-2 gap-4">
 <div>      

  ## Test

  ``` ts
  ///AreaHotels.test.ts
  
  import { handlers, rest } from '@/mocks/handlers'
  import { setupServer } from 'msw/node'

  const server = setupServer(...handlers)
  ```  

  ``` ts
  it('should render empty pos-table with no data', async ()  {
    server.use(
      rest.get(`${process.env.VITE_API_ENDPOINT}/MasterData/Hotels`, (_req, res, context) => {
        return res(context.status(404), context.json([]))
      })
    )
     await waitFor(() = {
      expect(getByText(/Data no available/i)).toBeInTheDocument()
    })
  })

  ```  
   
 </div>
 <div>
  
  ## Dev

  ```    
    npx msw init public/ --save 
  ```

  ```ts
  ///main.ts

  if (env.MODE === 'development') {
    const worker = setupWorker(...handlers)
    worker.start()
  }
  ```

 </div>
</div>

---
layout: center
class: text-center
---

## Veamos ejemplo de uso

---
layout: cover
class: text-center
background: /imgs/mother-object.webp
---

# Patrón Mother Object

---

# Definición

> An object mother is a kind of class used in testing to help create example objects that you use for testing.
>
> -- <cite>Martin Fowler</cite> [24 Octubre 2006](https://martinfowler.com/bliki/ObjectMother.html) 

## Herramientas
  <div grid="~ cols-2 gap-2  content-center" m="-t-2">  

  [Faker-js](https://www.npmjs.com/package/@faker-js/faker?activeTab=readme)

  [Faker](https://www.npmjs.com/package/faker/v/2.1.3)
  <div class="grid place-content-center">
  	<img border="rounded" class="h-48" src="/imgs/faker-js.svg" alt="faker-js" />
  </div>
  <div class="grid place-content-center">
  	<img border="rounded" class="h-48" src="/imgs/faker.png" alt="faker">
  </div>
  </div>

---

# Implementación

<div grid="~ cols-2 gap-4">
 <div>   

```ts
//src/mocks/MotherObject.ts
import { Account } from '@/types'
import { faker } from '@faker-js/faker/locale/en'

export const ACCOUNTS: Account[] = []

export function createRandomAccount(): Account {
  return {
    id: faker.datatype.uuid(),
    name: faker.company.name(),
    credential: faker.internet.password(),
    key: faker.random.word(),
  }
}

Array.from({ length: 10 }).forEach(() => {
  ACCOUNTS.push(createRandomAccount())
})

```
   
 </div>
 <div>

```ts
//handlers
rest.get('/api/MasterData/accounts', (req, res, context) => {
    return res(context.status(200), context.json(ACCOUNTS))
  }),

```
 </div>
</div>

