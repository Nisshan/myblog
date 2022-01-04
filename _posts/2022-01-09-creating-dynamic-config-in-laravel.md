---
layout: post
title:  "Creating dynamic config in laravel"
date:   2022-01-09 23:01:57 +0545
categories: laravel dynamic config
---

In laravel sometimes we need to to load the app settings through out the app and to do that querying everytime for a specific value might be little more than what we need and can have some negative impact on query time.

If You have a setting table with app settings then you can convert that in a way where you can access them as config theoughout the app.

Below snippet shows how you can use the data as config file 


```php

    $settings = Setttings::get();

    foreach ($settings as $key => $value)
    {
        Config::set('settings.'.$key, $value);   
    }

```


You can change the settings data from your setting model/table using the above snippet by placing it into the boot method of **AppServiceProvider**. Now you can access the field as config anywhere in your app by using 

```php 

config('settings.your_field_name');

```
