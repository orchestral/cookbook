# Themes

Themes are available by default on every Orchestra Platform installation and separated into two group;

* Frontend
* Backend

## Managing Themes

You can either manage themes via Artisan or Control extension.

### Artisan


```
 theme
  theme:activate        Set active themes in the application.
  theme:detect          Detect available themes in the application.
  theme:optimize        Pre-cache themes views in the application.
```

#### `php artisan theme:activate`

#### `php artisan theme:detect`


You can review this by running `php artisan theme:detect` from your working directory:

    $ php artisan theme:detect
    +----------+------------+----------+---------+
    | ID       | Theme Name | Frontend | Backend |
    +----------+------------+----------+---------+
    | default  | Default    |    ✓     |    ✓    |
    +----------+------------+----------+---------+
    
#### `php artisan theme:optimize`


### Control Extension
