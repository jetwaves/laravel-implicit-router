# route-to-controller
A simple Implicit Controller Router for Laravel whose version >= 5.2 ( 5.5 tested )



**CREDIT TO** [dingo/api](https://github.com/dingo/api) and [laravel framework](https://github.com/laravel/laravel)

---

## HOW TO USE: 
(exemple tested working well in Laravel 5.5 / should be the same in Laravel 5.2 5.3 5.4)

### Situation:
From Laravel 5.2, the feature [**implicit controller routing**](https://laravel.com/docs/5.1/controllers#implicit-controllers) has been removed.

But some projects have thousands of routing rules to declare.

### Solution:
1. run command:
        composer require jetwaves/route-to-controller dev-master
2. in your api.php or web.php in  routes,  add this following lines  (1).

        <?php
        $api = app('Jetwaves\RouteToController\Router');
        $api->controller('URI_PREFIX', 'App\Http\Controllers\TestController');
3. in your App/Http/Controllers/TestController.php,   add a function like

        <?php
        public function getShowMeTheMoney(Request $req){
            return '10000 gold';
        }
4. then we can access this controller by   http://hostname/URI_PREFIX/show-me-the-money and get the following response in your browser. Just like the implicit controller routing of Laravel 5.1 at old time. 
    
        10000 gold          
5. All Http method keywords are allowed to be the prefix of Camel Type function name to serve correspondent http methods.
6. When function does not exists, you'll get a 404 of laravel itself.
7. Declare explicit routes in the original way. (nothing changed)

---
### Middleware support:
code snippet (1) could be used in a closure of middlewares.

    <?php
    Route::middleware(['test'])->group(function () {
        $api = app('Jetwaves\RouteToController\Router');
        $api->controller('URI_PREFIX', 'App\Http\Controllers\TestController');
    });

        
when the 'test' middleware do  

    echo 'starcraft tricks :'
and you access http://hostname/URI_PREFIX/show-me-the-money,  you'il get 

    starcraft tricks : 10000 gold
in browser.



### ** Probably a ungraceful solution but save your time and life.   :-) **

***
## TODO:
1. Support some frequently used 'native' middleware declarations,  in the line of route declaration.
* Beautify the php source code and this readme file.
* Test if it's functional for lumen
* Show me your stars  8-D

 





