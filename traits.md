---
description: >-
  একই কোড বারবার লিখতে কার না বিরক্ত লাগে! কিন্তু এমন যদি হয়, কোড একবার মাত্র
  লিখেই বিভিন্ন class-এ ব্যবহার করা যাবে তাহলে কেমন হবে?
---

# লারাভেল-এ Traits কেন লিখবো?

ধরুন, 

```php
<?php
 
namespace App\Traits;
 
trait StoreImage {
 
    public function storeImage(Request $request) {
       //
    }
 
}
```

পিএইচপি তে Traits হচ্ছে কিছু মেথডের কালেকশন যা পুনরায় ব্যবহার করা যায়।

