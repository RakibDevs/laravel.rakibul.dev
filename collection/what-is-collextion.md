---
description: >-
  কালেকশন (collection) মূলত php ডেটা অ্যারে দিয়ে কাজ করার জন্য সুবিধাজনক API
  wrapper । চলুন তাহলে দেখে নেয়া যাক কালেকশন দিয়ে কিভাবে কাজ করে।
---

# কালেকশন \(collection\) কি?

যেকোন অ্যারে কে `collect()` হেল্পার দিয়ে খুব সহজেই কালেকশন এ রুপান্তর করা যায়। যেমন,

```php
$arr = [1,2,3];
$coll = collect([1,2,3]);

/*
Illuminate\Support\Collection {#1277 ▼
  #items: array:3 [▼
    0 => 1
    1 => 2
    2 => 3
  ]
}
*/
```

প্রশ্ন হচ্ছে php এর ডিফল্ট অ্যারে ফাংশনগুলো দিয়েই তো কাজ হয়ে যায়,   কালেকশন ব্যবহার করবো কেন?

আচ্ছা ধরুন, দুটো অ্যারে থেকে কমন ভ্যালুগুলো শাফল করে দেখাতে হবে। কিভাবে করবেন? কনভেনশনাল php তে আমরা এভাবে লিখতে পারি,

```php
shuffle(arsort(array_unique(array_merge($array1,$array2))));
```

এত্তগুলো **ব্র্যাকেট!!** আচ্ছা এবার যদি আরেকটু কমপ্লেক্স করে লিখতে বলা হয়, ১০ কিংবা তারও বেশি ব্র্যাকেট!  কি! খেই হারিয়ে ফেললেন? পড়তেও দাঁতমুখ ভাঙ্গার যোগার না?

এবার তাহলে চলুন কালেকশন দিয়ে করে দেখি,

```php
collect($array1)
     ->merge($array2)
     ->unique()
     ->sort()
     ->shuffle();
```

সহজ মনে হচ্ছে না? 

আবার যেমন নিচের কোডটুকু দেখুন, এখানে কোথায় প্যারামিটার বসাতে হবে এই নিয়েই দ্বিধা-দ্বন্দ্বে ভুগতে থাকেন অনেকে।

```php
array_walk ( $array , $callback );
array_map ( $callback , $array);
array_merge ( $array ,$array2 );// return a new array
array_push ($array ,$value); // not return a new array
```

লারাভেল কালেকশন কাজটি অনেক সহজ করে দিয়েছে। খুবই সিম্পল ও সহজ সমাধান

```php
collect($array)
    ->each($callback)
    ->map($callback)
    ->merge($array2)
    ->push($value)
```

