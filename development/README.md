# Development Environment

Before we start writing any code, let's prepare our installation for development by installing [Studio Component](https://github.com/orchestral/studio).

    $ composer require --dev "orchestra/studio=~3.1"
    
Now, as we all know `--dev` dependency is typically not available when we deploy to production, as this would minimize the amount of packages need to be pull for production. In order to register the component only for development usage let's create a new `app.php` configuration file for `local` environment.

    $ cd resources/config
    $ mkdir local
    $ cd local
    $ touch app.php
    
> This just create a new file at `resources/config/local/app.php`

Now let's add the service provider:


```php
<?php

return [
    'providers' => append_config([
        Orchestra\Studio\StudioServiceProvider::class,
    ]),
];
```

You can now view the available command from `php artisan`:

```
key
  make:auth-controller  Create auth boilerplate controllers and views
  make:contract         Create a new Contract interface
  make:filter           Create a new Filter class
  make:menu             Create a new Menu handler class
  make:validator        Create a new Validator handler class
```