# Intervention Image Symfony
## Symfony Integration for Intervention Image

[![Latest Version](https://img.shields.io/packagist/v/intervention/image-symfony.svg)](https://packagist.org/packages/intervention/image-symfony)
[![Monthly Downloads](https://img.shields.io/packagist/dm/intervention/image-symfony.svg)](https://packagist.org/packages/intervention/image-symfony/stats)

This package provides an integration to setup [Intervention
Image](https://image.intervention.io) easily to your Symfony framework application.

## Requirements

- Symfony >= 7

## Installation

In your existing Symfony application you can install this package using [Composer](https://getcomposer.org).

```bash
composer require intervention/image-symfony
```

After successful installation, you can activate the bundle in the file
`config/bundes.php` of your application by inserting the following line into
the array.

```php
return [
    // ...
    Intervention\Image\Symfony\InterventionImageBundle::class => ['all' => true],
];
```

## Configuration

By default, the bundle is configured to use the GD library with Intervention
Image. However, the package also offers other drivers. This can be easily
configured by creating a file `config/packages/intervention_image.yaml` and
setting the driver class as follows. 

```yaml
intervention_image:
  driver: Intervention\Image\Drivers\Imagick\Driver
```

You can choose between the two supplied drivers `Intervention\Image\Drivers\Gd\Driver` and
`Intervention\Image\Drivers\Imagick\Driver` for example.

## Getting Started

The integration is now complete and it is possible to access the [ImageManager](https://image.intervention.io/v3/basics/instantiation)
via dependency injection.

```php
use Intervention\Image\ImageManager;

class MyController extends AbstractController
{
    #[Route('/')]
    public function example(ImageManager $manager): Response
    {
        $image = $manager->read('images/example.jpg');
    }
}
```

Read the [official documentation of Intervention Image](https://image.intervention.io) for more information.

## Authors

This library is developed and maintained by [Oliver Vogel](https://intervention.io)

## License

Intervention Image Symfony is licensed under the [MIT License](LICENSE).
