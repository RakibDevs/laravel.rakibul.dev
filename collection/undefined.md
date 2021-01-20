---
description: >-
  কালেকশন (collection) হচ্ছে ডেটা নিয়ে কাজ করার জন্য খুবই দরকারি কিছু মেথড।
  কালেকশন মেথড দিয়ে আপনি খুব সহজেই যেকোন অ্যারে থেকে ফিল্টার থেকে শুরু করে
  কাস্টমাইজ ম্যাপিং পর্যন্ত সবই  করতে পারবেন।
---

# কালেকশন মেথড

![Scope of Collection.  Source: London Library](../.gitbook/assets/scope.jpg)

কালেকশন \(collection\) হচ্ছে অ্যারে ডেটা প্রসেসিং এর জন্য একটি শক্তিশালী মাধ্যম। ডেটা ফিল্টারিং, স্লাইসিং, ম্যাপিং কি নেই এতে? চলুন তাহলে দেখে নেয়া যাক, লারাভেল কালেকশন্ মেথডগুলি দিয়ে আসলে আমরা কি কি করতে পারি।

ধরুন আপনার একটি লাইব্রেরীতে কিছু সংখ্যক বই রাখা আছে। বইগুলি এমনভাবে সাজানো,

```php
// list of php books
$books = [
    [
        'title'  => 'The Joy of PHP Programming',
        'author' => 'Alan Forbes',
        'edition' => 5,
        'price'  => 2111 // price in BDT
    ],
    [
        'title'  => 'PHP & MySQL Novice to Ninja',
        'author' => 'Tom Butler & Kevin Yank',
        'edition' => 6,
        'price'  => 1726 // price in BDT
    ],
    [
        'title'  => 'Head First PHP & MySQL',
        'author' => 'Lynn Beighley & Michael Morrison',
        'edition' => 1,
        'price'  => 4627 // price in BDT
    ],
    [
        'title'  => 'PHP: A Beginner’s Guide',
        'author' => 'Vikram Vaswani',
        'edition' => 1,
        'price'  => 3500 // price in BDT
    ]
        
]
```

`$book` অ্যারে কে কিভাবে কালেকশন করতে হয় আমরা আগেই শিখেছি। আরও একবার দেখে নেই।

```php
$books = collect($books);
```

**filter\(\)**

এখন যদি শুধুমাত্র প্রথম সংস্করণের বই এর তালিকা চাওয়া হয় তাহলে কিভাবে করবেন?`filter()` মেথড কাজটি বেশ সহজ করে দিয়েছে।

```php
$filter = $books->filter(function($value, $key) {
        return $value['edition'] == 1;
});
 
$filter->all();

// output

$output =
[
    [
        'title'  => 'Head First PHP & MySQL',
        'author' => 'Lynn Beighley & Michael Morrison',
        'edition' => 1,
        'price'  => 4627 // price in BDT
    ],
    [
        'title'  => 'PHP: A Beginner’s Guide',
        'author' => 'Vikram Vaswani',
        'edition' => 1,
        'price'  => 3500 // price in BDT
    ]
        
]

```

**contains\(\)**

কোন একটি ভ্যালু কালেকশনে  আছে কি না  তা এই [`contains()`](https://laravel.com/docs/8.x/collections#method-contains) মেথড দিয়ে পাওয়া যায়। এটি বুলিয়ান রেজাল্ট রিটার্ন করে। যেমন,

```php
$books->contains('title', 'Head First PHP & MySQL'); // TRUE
$books->contains('title', 'Boss of PHP'); // FALSE
```

**only\(\)**

কোন কালেকশনের শুধুমাত্র স্পেসিফিক ভ্যালুগুলি দেখতে চাইলে [`only()`](https://laravel.com/docs/8.x/collections#method-only),

```php
$filtered = $books->only(['title', 'price']);

$filtered->all();

// output
[
    [
        'title'  => 'The Joy of PHP Programming',
        'author' => 'Alan Forbes'
    ],
    [
        'title'  => 'PHP & MySQL Novice to Ninja',
        'author' => 'Tom Butler & Kevin Yank'
    ],
    [
        'title'  => 'Head First PHP & MySQL',
        'author' => 'Lynn Beighley & Michael Morrison'
    ],
    [
        'title'  => 'PHP: A Beginner’s Guide',
        'author' => 'Vikram Vaswani'
    ]
        
]
```

আবার কালেকশন থেকে কোন কী বাদ দিতে চাইলে [`except()`](https://laravel.com/docs/8.x/collections#method-except) মেথড ব্যবহার করতে পারেন। `except()` মেথডের মতই [`forget()`](https://laravel.com/docs/8.x/collections#method-forget) মেথড কাজ করে। তবে এক্ষেত্রে কালেকশন মডিফাই হয়ে যায় অর্থাৎ পূর্বের কালেকশনটি আর ফেরত পাওয়া যাবে না।

 **implode\(\)**

কালেকশনের সব থেকে মজার মেথড এটি। পিএইচপি [`implode()`](https://laravel.com/docs/8.x/collections#method-implode) এর মতই লারাভেল `implode()` মেথড কাজ করে। যেমন, লাইব্রেরিতে রাখা বইগুলির নাম কমা আকারে দেখাতে হবে সেক্ষেত্রে,

```php
$books->implode('title', ', ');

// output
/* 
    The Joy of PHP Programming, PHP & MySQL Novice to Ninja, 
    Head First PHP & MySQL, PHP: A Beginner’s Guide
*/
```

তবে যদি বইয়ের নামের তালিকার অ্যারে দরকার হয় তাহলে [`pluck()`](https://laravel.com/docs/8.x/collections#method-pluck) মেথড ব্যবহার করতে হবে। 

```php
$books->pluck('title');
$books->all();

// output
[
    'The Joy of PHP Programming', 
    'PHP & MySQL Novice to Ninja', 
    'Head First PHP & MySQL', 
    'PHP: A Beginner’s Guide'
];
```

