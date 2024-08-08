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
