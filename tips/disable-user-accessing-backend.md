## Disable normal user from using the backend

There might be situation where you actually want to avoid normal user from accessing the backend. This can be done by including the following snippet in your `AppServiceProvider` etc.

```php
Foundation::when('orchestra::*', function (Request $request, Response $response) {
    if (Auth::isNot('Administrator')) {
        $response->headers->set('Location', handles('app::/');
    }
});
```