# Doorman

[![CI](https://github.com/silverstripe/doorman/actions/workflows/ci.yml/badge.svg)](https://github.com/silverstripe/doorman/actions/workflows/ci.yml)

Child process management. Compatible from PHP `5.3` to PHP `7`. Needs no extensions.

> `2.x` supports PHP `5.5.9` and upwards. If you need PHP `5.3/4` support, use a `1.x` release.

## Usage

```php
use AsyncPHP\Doorman\Manager\ProcessManager;
use AsyncPHP\Doorman\Task\ProcessCallbackTask;

$task1 = new ProcessCallbackTask(function () {
    print "in task 1";
});

$task2 = new ProcessCallbackTask(function () {
    print "in task 2";
});

$manager = new ProcessManager();

$manager->addTask($task1);
$manager->addTask($task2);

while ($manager->tick()) {
    usleep(250);
}
```

You can find more in-depth documentation in [docs/en](docs/en/introduction.md).

Want to know how it works, without digging through the code? [Read this](https://medium.com/@assertchris/multi-process-php-94a4e5a4be05)...

## Motivation

There are many great libraries that do something similar to this. They usually require additional extensions. This library aims to make child process management simple, and supported everywhere.

Other great libraries that do similar stuff:

- [React](https://github.com/reactphp/child-process)
- [Icicle](https://github.com/icicleio/concurrent)

## Versioning

This library follows [Semver](http://semver.org). According to Semver, you will be able to upgrade to any minor or patch version of this library without any breaking changes to the public API. Semver also requires that we clearly define the public API for this library.

All methods, with `public` visibility, are part of the public API. All other methods are not part of the public API. Where possible, we'll try to keep `protected` methods backwards-compatible in minor/patch versions, but if you're overriding methods then please test your work before upgrading.

## Thanks

I'd like to thank [SilverStripe](http://www.silverstripe.com) for letting me work on fun projects like this. Feel free to talk to me about using the [framework and CMS](http://www.silverstripe.org) or [working at SilverStripe](http://www.silverstripe.com/who-we-are/#careers).
