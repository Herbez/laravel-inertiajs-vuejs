# THIS IS LARAVEL-INERTIAJS-VUEJS APPLICATION 

SETTING UP:
1. LARAVEL 11
2. INERTIA JS
3. VUE JS
4. VITE
5. TAILWIND CSS


## INSTALL COMPOSER GLOBALLY 
cmd>> composer global require laravel/installer
 
## CREATE LARAVEL PROJECT
cmd>> Laravel new project_name

## INSTALL VUE JS
cmd>> npm i vue@latest

## SERVER SIDE 
## -----------

## AT INERTIA WEBSITE -> BELLOW INSTALLATION -> SERVER SIDE  
cmd>> composer require inertiajs/inertia-laravel

## GO TO VIEWS -> CHANGE WELCOME TO APP.BLADE.PHP
-> Add this 

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0" />
    @vite('resources/js/app.js')
    @inertiaHead
  </head>
  <body>
    @inertia
  </body>
</html>

## CREATE HandleInertiaRequests
cmd>> php artisan inertia:middleware

## GO TO BOOTSTRAPP FOLDER -> app.php

Inside WithMiddleWare function, add:

-> use App\Http\Middleware\HandleInertiaRequests;

-> $middleware->web(append: [
        HandleInertiaRequests::class,
]);


## THE WE RENDER VUE JS COMPONENTS GO TO ROUTES -> Web.php
-> change return view('welcome');
-> To Inertia::render('');


## CLIENT SIDE 
## -----------

cmd>> npm install @inertiajs/vue3

## GO TO -> RESOURCES -> app.js 
-> paste this vue js code:
--------------------------

import { createApp, h } from 'vue'
import { createInertiaApp } from '@inertiajs/vue3'

createInertiaApp({
  resolve: name => {
    const pages = import.meta.glob('./Pages/**/*.vue', { eager: true })
    return pages[`./Pages/${name}.vue`]
  },
  setup({ el, App, props, plugin }) {
    createApp({ render: () => h(App, props) })
      .use(plugin)
      .mount(el)
  },
})

## INSIDE RESOURCES -> JS FOLDER 
-> CREATE folder called "pages" 
-> Inside CREATE Vue component "Home.vue"

## You can install Vetur or Volar extensions for VU2 JS


cmd 1 >> php artisan serve
cmd 2 >> npm run dev

>> There must be an error cause we have to install Vite plugin
>> vite is our assets manager

## OPEN NEW CMD:
-> npm i @vitejs/plugin-vue

## WE NEED TO VITE THAT WE ARE USING VUE
-> OPEN vite.config.js

## IMPORT TAILWIND CSS TO APP.JS
-> import '../css/app.css'

-> then we finish the set up


