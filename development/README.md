# Development

Before we start writing any code, let's prefer our installation for development. First of all let's install [Studio Component](https://github.com/orchestral/studio) as dev dependency.

    $ composer require --dev "orchestra/studio=~3.1"
    
Now, as we all know `--dev` dependency is typically not available when we deploy to production, as this would minimize the amount of packages need to be pull for production. In order to register the component only for development usage let's create a new `app.php` configuration file for `local` environment.

    $ cd resources/config
    $ mkdir local
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