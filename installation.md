# Installation

Getting started with Orchestra Platform 3 is as much identical to getting started with Orchestra Platform 2. Therefore you need to have some minimum knowledge on [Laravel 5](http://laravel.com), [Composer](https://getcomposer.org) and [Packagist](https://packagist.org).

I would highly recommend watching [Laravel 5 Fundamentals](https://laracasts.com/series/laravel-5-fundamentals) and [What's New in Laravel 5.1](https://laracasts.com/series/whats-new-in-laravel-5-1) video series from [Laracasts](https://laracasts.com) in order to get familiar with Laravel 5 to understand some of the approach we use in Orchestra Platform 3.

## Downloading via Composer

Firstly, run the following command to download Orchestra Platform 3 using Composer:

    $ composer create-project orchestra/platform patio "3.1.x" --prefer-dist

This composer command would create a new project for you on `patio` folder using the latest development build, `--prefer-dist` is another option that you can use to indicate that you want to download a distributed version instead of cloning the repository, otherwise use `--prefer-source`.
