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
composer create-project --prefer-dist laravel/laravel tall-stack-app
cd tall-stack-app
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

