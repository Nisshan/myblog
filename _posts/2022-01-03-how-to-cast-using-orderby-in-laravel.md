---
layout: post
title:  "How to order string column in mysql as integer"
date:   2021-12-20 23:01:57 +0545
categories: how cache can slow you
---

# How to cast mysql string into integer type while ordering in laravel.

Sometime we need to cast the type to different one to perform an order function in laravel when using mysql. I do not recommend this way of type casting of column but sometime this might be the fastest and easiest thing to do to make the code executable the way you want.

So I recently faced the a problem. I had a string field in database which only stores the integer value but when ordering the value by laravel ``` orderBy() ``` function it does not perform as expected as integer and strings are sorted in different way.

1, 2, 3, 4, 10, 20, 22, 100 would be sorted as 1, 10, 100, 2, 20 ,22, 3, 4 in the above problem. so you can use ``` orderByRaw()``` in laravel as shown in example below.

```php

    $orders = Order::orderByRaw('CAST(order_no as unsigned)'. $dir)->get()

```

**$dir** is the direction in which the sort will be performed.


Read about [How Cache Can Slow You Down]({% post_url 2021-12-20-slower-cache %}) when not setup properly.




