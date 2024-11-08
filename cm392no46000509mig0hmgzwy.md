---
title: "What is Livewire?"
datePublished: Fri Nov 08 2024 18:30:16 GMT+0000 (Coordinated Universal Time)
cuid: cm392no46000509mig0hmgzwy
slug: what-is-livewire
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730300650694/28efbd64-348f-49e0-90aa-a4cb96c980aa.png
tags: laravel, php, livewire, laravel-livewire

---

**Livewire** is a full-stack framework for **Laravel** that allows developers to build dynamic and interactive user interfaces without needing to write a lot of JavaScript. It works by combining **server-side rendering** with client-side interactions using **AJAX** requests, which allows you to create reactive, real-time components within your Laravel application.

### Key Features of Livewire:

1. **Reactive Components**: You can create interactive components like forms, modals, or data tables that dynamically update without needing page reloads.
    
2. **Server-Side Logic**: Instead of handling the logic in JavaScript, you write your logic in PHP. Livewire sends AJAX requests to the server to execute the PHP code and updates the frontend seamlessly.
    
3. **Simple State Management**: Livewire components maintain their state on the server and automatically sync with the frontend.
    
4. **Tight Integration with Blade**: Livewire works directly with Laravel's Blade templating engine, allowing you to write PHP and HTML together with very little JavaScript.
    

### Example:

Here’s a simple example of a **Livewire counter component**:

1. **Create the Livewire Component**:
    
    ```bash
    php artisan make:livewire Counter
    ```
    
2. **In the Livewire Component (app/Http/Livewire/Counter.php):**
    
    ```php
    namespace App\Http\Livewire;
    
    use Livewire\Component;
    
    class Counter extends Component
    {
        public $count = 0;
    
        public function increment()
        {
            $this->count++;
        }
    
        public function render()
        {
            return view('livewire.counter');
        }
    }
    ```
    
3. **In the Blade View (resources/views/livewire/counter.blade.php):**
    
    ```php-template
    <div>
        <h1>{{ $count }}</h1>
        <button wire:click="increment">Increment</button>
    </div>
    ```
    
4. **In a Laravel Blade Template (resources/views/welcome.blade.php):**
    
    ```php-template
    <livewire:counter />
    ```
    

In this example, clicking the "Increment" button sends a request to the server to execute the `increment()` method on the `Counter` component, which updates the `$count` property and automatically updates the displayed value in the browser.

### When to Use Livewire:

* When you need dynamic and interactive UIs without complex front-end frameworks like Vue.js or React.
    
* When you want to leverage Laravel’s existing ecosystem and Blade templating.
    
* When you prefer to write PHP over JavaScript for frontend behavior.
    

### Benefits:

* Minimal JavaScript needed.
    
* Seamless integration with Laravel Blade templates.
    
* Simplifies the process of building dynamic, interactive components.
    

Livewire is particularly useful for Laravel developers who want to build reactive, interactive user interfaces without diving deep into frontend frameworks.

**Image attribution**

1. Livewire
    
2. [PHP Logo](https://en.wikipedia.org/wiki/PHP#/media/File:PHP-logo.svg)
    
3. [Laravel logo](https://en.wikipedia.org/wiki/Laravel#/media/File:Laravel.svg)