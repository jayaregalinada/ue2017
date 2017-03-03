# UE 2017

### Basic Nginx Configuration
Inside `location / { } ` block just replace it to: `try_files $uri $uri/ /index.php?$query_string;` should look like this:

```nginx
...
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

...
```


### Specified key was too long

> [Illuminate\Database\QueryException]
> SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 767 bytes (SQL: alter table users add unique users_email_unique(email))
> 
> [PDOException]
> SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 767 bytes

In case when you run `php artisan migrate` you might get this kind of error. However, below is a solution from [Laravel News](https://laravel-news.com/laravel-5-4-key-too-long-error). Just edit your `app\providers\AppServiceProvider.php` file and inside the `boot` method set a default string length:

``` php
use Illuminate\Support\Facades\Schema;

...
public function boot()
{
    Schema::defaultStringLength(191);
}
...
```
