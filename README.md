# Laravel CoreUI integration

This is a very opinionated package designed to help our freshman year's students with rapid prototyping of web applications.

The package is based upon [CoreUI](https://coreui.io/), with every plugin we deemed unnecessary removed.
It builds upon the latest LTS and stable releases of [Laravel](https://laravel.com). As of now, those are respectively `5.5` and `5.7`.

It also incorporates a replacement command for Laravel's `make:auth` command that uses CoreUI styled views for a more consistent user experience.

## Installation

```bash
$ composer require hz-bho-ict/laravel-core-ui
$ php artisan vendor:publish --provider="HzHboIct\LaravelCoreUI\ServiceProvider" --tag=assets
```

## Usage

To use the template, create a blade file and extend the layout with `@extends('coreui::page')`.

This template yields multiple sections, all of them optional:

`section`|explanation
---|---
`title`|for `<title>` tag
`content`|for all of the content
`css`|for extra CSS files (loads after CoreUI!)
`js`|for extra JavaScript (loads after CoreUI!)

A page can look like this:

```php
@extends('coreui:master')

@push('css')
    <link rel="stylesheet" type="text/css" href="/url/to/stylesheet.css">
@endpush

@section('title', 'Dashboard')

@section('content')
    <h1>Dashboard</h1>
    <p>Welcome to this awesome web app!</p>
@endsection

@push('js')
    <script src="/url/to/script.js"></script>
@endpush
```

## CoreUI authentication views

There's a command `make:coreui` that behaves just like the built-in `make:auth` command, but it replaces the default views with [CoreUI styled ones](https://coreui.io/demo/login.html)

```bash
$ php artisan make:coreui
```

## Configuration

To edit site title, menu and many other things, publish the configuration file:

```bash
$ php artisan vendor:publish --provider="HzHboIct\LaravelCoreUI\ServiceProvider" --tag=config
```

You can now edit it at `config/coreui.php`.

## Customized views

If you need complete control of the provided views, run:

```bash
$ php artisan vendor:publish --provider="HzHboIct\LaravelCoreUI\ServiceProvider" --tag=views
```

You can now edit them under `resources/views/vendor/coreui`.

## Updating the package

To update the package, run the following command. Note that this **will** overwrite any changes you've made in the published files.

```bash
$ php artisan vendor:publish --provider="HzHboIct\LaravelCoreUI\ServiceProvider" --tag=assets --force
```

## License

This packaged is licensed under the MIT License. Please note that CoreUI has different licensing, explained [here](https://coreui.io/pro/license/).

If your application is free of charge and is used by one client only, you're free to do that. If any other circumstances apply, please consult the mentioned CoreUI licensing page.

## Acknowledgements

Heavily inspired by [Jeroen Noten](https://github.com/jeroennoten)'s [Laravel-AdminLTE](https://github.com/jeroennoten/Laravel-AdminLTE) package.
