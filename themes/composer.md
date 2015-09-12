## Distributed Themes via Composer

Wouldn't it be nice if we can install theme as simple as installing new packages (for Laravel etc). 

    $ composer require "stackie/adminlte-theme=^0.1"
    
This is available for Orchestra Platform, in fact you as the user can install AdminLTE theme for Orchestra Platform using the above command. Once you have done that you can run the following command.

    $ php artisan theme:detect
    
And activate the theme via:

    $ php artisan theme:activate backend adminlte

### Creating a New Theme

In this chapter, we will look at building a simple theme for Orchestra Platform. First let's create a new theme project and make it available for `patio`.

```
$ mkdir mini-theme
$ cd mini-theme
```

Once we're inside the folder, you can easily use `composer init` to start building the theme's `composer.json` file.
```
$ composer init

  Welcome to the Composer config generator

This command will guide you through creating your composer.json config.

Package name (<vendor>/<name>) [crynobone/mini-theme]:
Description []: Just another theme
Author [crynobone <crynobone@gmail.com>]:
Minimum Stability []: dev
Package Type []: orchestra-theme
License []: MIT

Define your dependencies.

Would you like to define your dependencies (require) interactively [yes]? yes
Search for a package: orchestra/theme-installer
Enter the version constraint to require (or leave blank to use the latest version): ^1.0
Search for a package:
Would you like to define your dev dependencies (require-dev) interactively [yes]? no

{
    "name": "crynobone/mini-theme",
    "description": "Just another theme",
    "type": "orchestra-theme",
    "require": {
        "orchestra/theme-installer": "^1.0"
    },
    "license": "MIT",
    "authors": [
        {
            "name": "crynobone",
            "email": "crynobone@gmail.com"
        }
    ],
    "minimum-stability": "dev"
}

Do you confirm generation [yes]? yes
```

To enable Composer to know that this package should be installed as Orchestra Platform theme you need to add `"type": "orchestra-theme"` and include the [Theme Installer Plugin](https://github.com/orchestral/theme-installer).