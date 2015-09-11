# Tips and Tricks

* [Disable normal user from using the backend](#disable-normal-user-from-using-the-backend)

## Disable normal user from using the backend


```php
Foundation::when('orchestra::*', function (Request $request, Response $response) {
    if (Auth::isNot('Administrator')) {
        $response->headers->set('Location', handles('app::/');
    }
});
```