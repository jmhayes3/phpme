# phpme
An exploration of PHP and the TALL stack. 

The TALL Stack:
* Tailwind CSS: A utility-first CSS framework.
* Alpine.js: A lightweight JavaScript framework.
* Laravel: A PHP framework for web artisans.
* Livewire: A full-stack framework for Laravel that makes building dynamic interfaces simple without leaving the comfort of Laravel.


## Setup

### Composer

Download Composer:

```sh
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```

Verify hash:

```sh
php -r "if (hash_file('sha384', 'composer-setup.php') === 'HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```

Install Composer:

```sh
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

### Laravel

Create new Laravel application:

```sh
composer create-project --prefer-dist laravel/laravel phpme
cd phpme
```

Setup env:

```sh
cp .env.example .env
```

Generate application key:

```sh
php artisan key:generate
```

### Tailwind

Install:

```sh
npm install -D tailwindcss postcss autoprefixer
```

Initialize Tailwind:

```sh
npx tailwindcss init
```

Setup tailwind.config.js to purge unused styles in production:
```js
module.exports = {
    purge: [
        './resources/**/*.blade.php',
        './resources/**/*.js',
        './resources/**/*.vue',
    ],
    darkMode: false, // or 'media' or 'class'
    theme: {
        extend: {},
    },
    variants: {
        extend: {},
    },
    plugins: [],
};
```

Update `resources/css/app.css` to include Tailwind directives:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Livewire

Install:

```sh
composer require livewire/livewire
```

Add Livewire's JavaScript library and styles to `resources/views/layouts/app.blade.php` file:
```php
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>Laravel</title>

    <!-- Fonts -->
    <link href="https://fonts.googleapis.com/css?family=Nunito:200,600" rel="stylesheet">

    <!-- Styles -->
    <link href="{{ mix('css/app.css') }}" rel="stylesheet">

    @livewireStyles
</head>
<body>
    <div id="app">
        @yield('content')
    </div>

    <!-- Scripts -->
    <script src="{{ mix('js/app.js') }}" defer></script>

    @livewireScripts
</body>
</html>
```

### Alpine

Install:

```sh
npm install alpinejs
```

Add Alpine.js to `resources/js/app.js` file:

```js
require('./bootstrap');
import Alpine from 'alpinejs';

window.Alpine = Alpine;

Alpine.start();
```

### NPM

Add helper scripts to `package.json`:

```json
"scripts": {
    "dev": "npm run development",
    "development": "mix",
    "watch": "mix watch",
    "hot": "mix watch --hot",
    "prod": "npm run production",
    "production": "mix --production"
}
```

Compile assets:

```sh
npm install && npm run dev
```

## Run

Serve the application using Laravel's built-in server:

```sh
php artisan serve
```

Navigate to http://localhost:8000!

## Notes

If laravel-mix is not installed by default, run:

```sh
npm install laravel-mix --save-deps
```
