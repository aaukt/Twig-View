# Slim Framework Twig View

[![Build Status](https://travis-ci.org/slimphp/Twig-View.svg?branch=master)](https://travis-ci.org/slimphp/Twig-View)

This is a Slim Framework view layer built on top of the Twig templating component. You can use this component to create and render templates in your Slim Framework application.

## Install

Via [Composer](https://getcomposer.org/)

```bash
$ composer require slim/twig-view
```

Requires PHP 5.4.0 or newer.

## Usage

```php
// Create Slim app
$app = new \Slim\App();

// Register Twig View helper
$app->register(new \Slim\Views\Twig('path/to/templates', [
    'cache' => 'path/to/cache'
]));

// Define named route
$app->get('/hello/{name}', function ($request, $response, $args) {
    $this['view']->render('profile.html', [
        'name' => $args['name']
    ]);
})->setName('profile');

// Run app
$app->run();
```

## Custom template functions

This component exposes a custom `url_for()` function to your Twig templates. You can use this function to generate complete URLs to any Slim application named route. This is an example Twig template:

    {% extends "layout.html" %}

    {% block body %}
    <h1>User List</h1>
    <ul>
        <li><a href="{{ 'profile'|url_for({ "name": "josh" }) }}">Josh</a></li>
    </ul>
    {% endblock %}

## Testing

```bash
phpunit
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email security@slimframework.com instead of using the issue tracker.

## Credits

- [Josh Lockhart](https://github.com/codeguy)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
