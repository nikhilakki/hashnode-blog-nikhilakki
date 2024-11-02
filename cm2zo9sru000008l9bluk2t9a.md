---
title: "What is Blade?"
datePublished: Sat Nov 02 2024 04:37:38 GMT+0000 (Coordinated Universal Time)
cuid: cm2zo9sru000008l9bluk2t9a
slug: what-is-blade
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730300390021/a9c5ff4e-7e18-413f-a45e-9be81ce0e14a.png
tags: laravel, php, blade-templates, blade-laravel

---

**Blade** is the simple, powerful templating engine provided with **Laravel**, a popular PHP framework. It allows developers to write dynamic HTML templates by mixing plain HTML with PHP code in a clean, expressive syntax. Blade templates are compiled into plain PHP and cached for better performance.

### Key Features of Blade:

1. **Template Inheritance**: Blade makes it easy to define a layout or base structure and then extend it in child views.
    
2. **Display Dynamic Data**: You can easily output dynamic content using Blade’s curly brace syntax (`{{ }}`).
    
3. **Control Structures**: Blade offers clean directives for loops, conditionals, and more.
    
4. **Components and Slots**: Blade allows reusable components and slots for organizing and reusing UI elements.
    
5. **Custom Directives**: You can define custom Blade directives for repetitive logic.
    
6. **No Performance Overhead**: Since Blade templates are compiled into plain PHP, it doesn't add any significant performance overhead.
    

### Key Syntax and Examples:

#### 1\. **Template Inheritance:**

Template inheritance allows you to create a common layout that other views can extend.

* **Layout Template (resources/views/layouts/app.blade.php):**
    
    ```php-template
    htmlCopy code<html>
    <head>
        <title>@yield('title')</title>
    </head>
    <body>
        <header>
            <!-- Common header content -->
        </header>
    
        <div class="container">
            @yield('content')
        </div>
    
        <footer>
            <!-- Common footer content -->
        </footer>
    </body>
    </html>
    ```
    
* **Child View (resources/views/pages/home.blade.php):**
    
    ```php
    @extends('layouts.app')
    
    @section('title', 'Home Page')
    
    @section('content')
        <h1>Welcome to the Home Page</h1>
        <p>This is some content for the home page.</p>
    @endsection
    ```
    

#### 2\. **Outputting Dynamic Data:**

You can output PHP variables using Blade’s curly brace syntax.

```php-template
<h1>{{ $title }}</h1> <!-- Echoes the value of $title -->
```

To escape HTML characters, Blade automatically handles escaping. If you want to render raw HTML, you can use `{!! !!}`.

```php-template
{!! $htmlContent !!}
```

#### 3\. **Control Structures:**

Blade offers clean syntax for control structures like `if`, `foreach`, `for`, etc.

* **Conditionals:**
    
    ```php-template
    @if ($isLoggedIn)
        <p>Welcome back, user!</p>
    @else
        <p>Please log in.</p>
    @endif
    ```
    
* **Loops:**
    
    ```php
    @foreach ($users as $user)
        <p>{{ $user->name }}</p>
    @endforeach
    ```
    

#### 4\. **Components and Slots:**

You can create reusable components with Blade.

* **Component (resources/views/components/alert.blade.php):**
    
    ```xml
    <div class="alert alert-{{ $type }}">
        {{ $message }}
    </div>
    ```
    
* **Using the Component (in a Blade view):**
    
    ```xml
    <x-alert type="success" :message="$successMessage" />
    ```
    

#### 5\. **Custom Blade Directives:**

Blade allows you to define your custom directives.

```php-template
Blade::directive('datetime', function ($expression) {
    return "<?php echo ($expression)->format('m/d/Y H:i'); ?>";
});
```

In your Blade view:

```php
@datetime($user->created_at)
```

### Why Use Blade?

* **Readable and Clean**: Blade templates are easy to read and write compared to raw PHP.
    
* **Template Inheritance**: Makes building consistent layouts easy.
    
* **Reusability**: Components and sections allow you to reuse code efficiently.
    
* **Tight Integration**: Blade is tightly integrated with Laravel, making it the default and easiest way to build views in Laravel applications.
    

Blade simplifies building dynamic, maintainable, and structured views in Laravel applications by combining PHP logic and HTML in a clean, organized manner.

#### Image attribution

1. [Laravel logo](https://en.wikipedia.org/wiki/Laravel#/media/File:Laravel.svg)
    
2. [Blade image](https://www.freepik.com/free-vector/barber-blade-white-background_19785353.htm#fromView=search&page=1&position=22&uuid=53b5b105-c03e-44ed-a2a9-578b3073c629)
    
3. [PHP Logo](https://en.wikipedia.org/wiki/PHP#/media/File:PHP-logo.svg)