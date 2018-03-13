# Request handler callable

[Psr-15](https://www.php-fig.org/psr/psr-15/) request handler proxying a callable.

**Require** php >= 7.0

**Installation** `composer require ellipse/handlers-callable`

**Run tests** `./vendor/bin/kahlan`

- [Using callables as request handlers](https://github.com/ellipsephp/handlers-callable#using-callables-as-request-handlers)

## Using callables as request handlers

The class ```Ellipse\Handlers\CallableRequestHandler``` can be wrapped around a callable in order to use it as a request handler.

As any request handler ```->handle()``` method, the callable takes an implementation of `Psr\Http\Message\ServerRequestInterface` as parameter and should return an implementation of `Psr\Http\Message\ResponseInterface`.

```php
<?php

namespace App;

use Psr\Http\Message\ServerRequestInterface;

use Ellipse\Handlers\CallableRequestHandler;

// This middleware is wrapped around the given callable.
$handler = new CallableRequestHandler(function (ServerRequestInterface $request) {

    // ...

    return $response;

});

// The handler ->handle() method proxy the callable.
$response = $handler->handle($request);
```
