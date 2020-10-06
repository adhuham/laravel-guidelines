# Guidelines and Best Practices for Building robust Web Application in Laravel
What follows are guidelines and best practices to consider while building web applications using Laravel framework.
Laravel is a free, open-source PHP web framework, created by Taylor Otwell and intended for the development of web applications following the model–view–controller (MVC) architectural pattern and based on Symfony (Wikipedia).
This guide includes both best practices and coding guidelines, some of which are highly opinionated. Thus, treat this guide as a general guideline to follow, not as a rule book.

## Keywords Used
This guidline uses keywords from [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) specifications.
   
1. **MUST** This word, or the terms "REQUIRED" or "SHALL", mean that the
   definition is an absolute requirement of the specification.

2. **MUST NOT** This phrase, or the phrase "SHALL NOT", mean that the
   definition is an absolute prohibition of the specification.

3. **SHOULD** This word, or the adjective "RECOMMENDED", mean that there
   may exist valid reasons in particular circumstances to ignore a
   particular item, but the full implications must be understood and
   carefully weighed before choosing a different course.

4. **SHOULD NOT** This phrase, or the phrase "NOT RECOMMENDED" mean that
   there may exist valid reasons in particular circumstances when the
   particular behavior is acceptable or even useful, but the full
   implications should be understood and the case carefully weighed
   before implementing any behavior described with this label.
   
   
   

## Naming Conventions
### Controllers
All controller names MUST start with a singular noun, followed by the word "Controller" at the end, and MUST be in PascalCase.

Correct
```php
class PostController extends Controller
```

Wrong
```php
class Posts_Controller extends Controller
class post_controller extends Controller
class Posts extends Controller
```

### Models
All model names MUST be in singular form, and MUST use PascalCasing.

Correct
```php
class User extends Models
```

Wrong
```php
class Users extends Models
class UserModel extends Models
class user_model extends Models
```

### Controllers/Models Methods
All methods in Controllers and Models MUST be in camelCase.

Correct
```php
class User extends Model
{
    public function scopeActive($q)
    {
        return $q->where('active', 1);
    }
```

Wrong
```php
class User extends Model
{
    public function scope_active($q)
    {
....
class User extends Model
{
    public function ScopeActive($q)
    {
```

### Variables
All variables SHOULD generally use camelCase.

Correct
```php
$popularPosts
$activeUsers
```

Wrong
```php
$popular_posts
$ActiveUsers
```


### Routes
All routes SHOULD be in plural form of the resource it's manipulating, and SHOULD be in lower case. They MUST use kebab-casing.

Correct
```php
Route::get('/users', 'UserController@index');
Route::get('/user-policies', 'UserPolicyController@index');
```

Wrong
```php
Route::get('/user', 'UserController@index');
Route::get('/user_all', 'UserController@index');
Route::get('/userAll', 'UserController@index');
Route::get('/UserAll', 'UserController@index');
Route::get('/user_policies', 'UserController@index');

```

#### Route Names
All route names MUST use snake_casing and dot notation.

Correct
```php
Route::get('/users/active', 'UserController@index')->name('users.active');
Route::get('/users/user-policies', 'UserPolicyController@index')->name('users.user_policies');
```

Correct
```php
Route::get('/users/active', 'UserController@index')->name('users_active');
Route::get('/users/user-policies', 'UserPolicyController@index')->name('users-user-policies');
```

### Views
All view files and folders MUST use snake_casing. 

Correct
```
user_policies/show.blade.php
user_policies.blade.php
```

Wrong
```
user-policies/show.blade.php
UserPolicies/show.blade.php
userPolicies.blade.php
```


