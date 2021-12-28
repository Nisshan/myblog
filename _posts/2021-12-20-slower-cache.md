---
layout: post
title:  "How Cache Can Slow You Down"
date:   2021-12-20 23:01:57 +0545
categories: how cache can slow you
---

**What I Am Working On**

I am Working on [Deltasales App](https://deltatechnepal.com/product/delta-sales-crm){:target="_blank"} currently and it is a multitannacy app developed using laravel.


**How Our App Functions**

Company can register and they can have a subdomain from which they can access the web and all the modules which they subscribe to. 

Every Company that register will have 2 default roles and over that the company can create multiple custom roles based on their requirement and the module they choose.

This can grow in huge number based on the company hierarchy and the number of modules they are subscribed to.


**My Observation**

One thing I noticed was high consumption of memory. Every Rerquest was consuming above **800 MB** of memory. 

I knew it is very high consumption even our app has lots of data to be loaded per request.

<!-- 
**What was actually happening**

We are using spatie roles and permission packages for managing our roles and permission.
Basically spatie roles and permission caches all the data of roles and permission for all the company available in our database. -->

**What Went Wrong**

We are using spatie roles and permission packages for managing our roles and permission.

The main problem was everything in roles and permissin was being cached without applying the company filter from the data.

So, Basically every roles and permission data of all the companies was being cached to the filesystem and loaded in subsequent requests which consumed more memory and took more processing time when compared to the retrival of database.

**How I Managed To Reduce The Memory Use**

I applied global scope to roles and permission model by extending them and using companyId as filter key and removed cache from file system to Inmemory.

It reduced the memory uses drastically from **800 MB** to about **40 MB** but the downside is the database is being hit everytime when permission is checked which is almost in every request.

Still it improved a lot of initial load time and memory consumption.

**What I Tried To Change Cache Key Of Spatie Dynamically**

I tried to setup unique cache key on ```boot()``` method of **AppServiceProvider** using function
```config(['key' => 'value'])```  which seems to change the config file but does not seems to work as expeced.


**What Is Working But Is Yet To Implement**

Creating a helper function to create a consistant unique cache key and using it directly into the config file provided by the package caches the cache based on the filter per company. 

This needs to be tested more as it might create problems in other parts of system and while forgeting the cache of specific company.

What this will do is increase the memory consumption to about **40-50 MB**  but will decrease the cuncurrent request made to the database and reduce the load time

