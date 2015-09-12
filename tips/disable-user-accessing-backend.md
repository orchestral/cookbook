## Disable normal user from using the backend

There might be situation where you actually want to avoid normal user from accessing the backend. This can be done by including the following snippet in your `AppServiceProvider` etc.

```php
Foundation::when('orchestra::*', function () {
    if (Auth::isNot('Administrator')) {
        abort(403, 'Not authorized to be here!');
    }
});
```

`Foundation::when()` would trigger the callback when the request match Orchestra Platform URL routing when `router.matched` event is triggered. 

You can also modify the response object by type-hinting to `kernel.handled` event, to do so let's use `Foundation::whenOn()` instead:

```php
use Illuminate\Http\Request;
use Illuminate\Http\Response;

Foundation::whenOn('orchestra::*', 'kernel.handled', function (Request $req, Response $resp) {
    $resp->headers->set('X-BUILT-WITH', 'Orchestra Platform');
});
```

> Do note that the `kernel.handled` is execute after a response is return from Laravel middleware.