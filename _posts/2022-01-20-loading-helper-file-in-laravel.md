---
layout: post
title:  "Creating and including helper file in laravel"
date:   2022-01-20 21:00:00 +0545
categories: including helper in laravel
---

# Creating and including helper file in laravel application

- Create a file name with .php extension and place it to the directory you want inside the application.
I usually name it helpers and put my helpers.php in 'app/helpers.php'
- Open composer.json from your project and add your helpers.php to autoload part of composer as below.

```json 
"autoload": {
        "psr-4": {
            "Nisshan\\NepaliCalendar\\": "src",
            "Nisshan\\NepaliCalendar\\Database\\Factories\\": "database/factories"
        },
        "files": [
            "src/helpers.php"
        ]
 },

```
- After adding path to composer run composer dump-autoload then you can use your helper function inside your application
by calling the name of function you created.

  
# Defining and Calling of Functions

- This Example doesn't look practical but, it does a simple work of converting date to the format passed with date 
value in function.
- If format is not passed it will take the default value provided into the function.
- Function is wrapped in function_exists check to avoid definition collisions but can also be optional if you are confident that the same definition 
does not exist in another part of the application.

```php
use Carbon\Carbon;

if(! function_exists(formatDate)){
    function formatDate($date, $format = 'M d, Y')
    {
        return Carbon::parse($date)->format($format);
    }
}
```

## Note : Adding helpers to your package is same as adding it to the laravel application.
