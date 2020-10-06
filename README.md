# Guidelines and Best Practices for Building robust Web Applications in Laravel
What follows are guidelines and best practices to consider while building web applications using Laravel framework.
Laravel is a free, open-source PHP web framework, created by Taylor Otwell and intended for the development of web applications following the model–view–controller (MVC) architectural pattern and based on Symfony (Wikipedia).
This guide is highly opinionated. Thus, treat this as a general guideline to follow, and not as a hard and fast rule book.

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
All controllers MUST start with a singular noun followed by the word "Controller" at the end, and MUST be in PascalCase.

Do
```php
class PostController extends Controller
```

Don't
```php
class Posts_Controller extends Controller
class post_controller extends Controller
class Posts extends Controller
```

### Models
All models MUST be in singular form and MUST use PascalCasing.

Do
```php
class User extends Models
```

Don't
```php
class Users extends Models
class UserModel extends Models
class user_model extends Models
```

#### Model Properties
All model properties SHOULD be in snake_case.

Do
```php
public $first_name
public $published_at
```

Don't
```php
public $firstName
public $publishedAt
```


#### Relationships: hasOne and belongsTo
All methods defining hasOne or belongsTo relationship MUST be in singular form.

Do
```php
// ...
    public function post()
    {
        return $this->hasOne(App\Models\Post::class);
    }
// ...
```

Don't
```php
// ...
    public function posts()
    {
        return $this->hasOne(App\Models\Post::class);
    }
// ...
```

#### Relationships: hasMany, belongsToMany
All methods defining hasMany or belongsToMany relationship MUST be in singular form.

Do
```php
// ...
    public function users()
    {
        return $this->hasMany(App\Models\Post::class);
    }
//  ...
```

Don't
```php
// ...
    public function user()
    {
        return $this->hasMany(App\Models\Post::class);
    }
// ...
```


### Controllers/Models Methods
All methods in Controllers and Models MUST be in camelCase.

Do
```php
// ...
    public function scopeActive($q)
    {
        return $q->where('active', 1);
    }
// ...
```

Don't
```php
// ...
    public function scope_active($q)
    {
    }
// ....
    public function ScopeActive($q)
    {
    }
// ...
```

### Variables
All variables SHOULD be in camelCase.

Do
```php
$popularPosts
```

Don't
```php
$popular_posts
$PopularPosts
```

Avoid abbreviations as much as possible.

Do
```php
$invoiceAccountId
```

Don't
```php
$invAccId
```


### Routes
All routes SHOULD be in plural form of the resource it's manipulating, and SHOULD be in lower case. They MUST use kebab-casing.

Do
```php
Route::get('/users', 'UserController@index');
Route::get('/user-policies', 'UserPolicyController@index');
```

Don't
```php
Route::get('/user', 'UserController@index');
Route::get('/user_all', 'UserController@index');
Route::get('/user_policies', 'UserController@index');
```

#### Route Names
All route names MUST use snake_casing and dot notation. They SHOULD be in singular form.

Do
```php
Route::get('/users/active', 'UserController@index')->name('user.active');
Route::get('/users/user-policies', 'UserPolicyController@index')->name('user.user_policy');
```

Don't
```php
Route::get('/users/active', 'UserController@index')->name('users_active');
Route::get('/users/user-policies', 'UserPolicyController@index')->name('user.user_policies');
Route::get('/users/user-policies', 'UserPolicyController@index')->name('users-user-policies');
```

### Views
All view files / folders MUST use snake_casing. 

Do
```
user_policies/show.blade.php
user_policies.blade.php
```

Don't
```
user-policies/show.blade.php
UserPolicies/show.blade.php
userPolicies.blade.php
```

#### Parameters
All view parameters SHOULD BE in camelCase.

Do
```php
return view('index.blade.php' [
   'firstName' => 'Taylor',
   'lastName' => 'Otwell'
]);
```

Don't
```php
return view('index.blade.php' [
   'first_name' => 'Taylor',
   'last-name' => 'Otwell'
]);
```


### Database
#### Tables
Database tables SHOULD be in plural form and SHOULD use snake_casing.

Do
```
users
user_policies
```

Don't
```
user
userPolicies
```

Pivot tables SHOULD be in singular form and in alphabetical order.

Do
```
post_user
```

Don't
```
user_post
posts_users
```

#### Columns
All columns SHOULD be in snake_case and SHOULD NOT contain model name.

Do
```
first_name
address
country
```

Don't
```
firstName
user_address
user_country
```

Primary `id` column in the table SHOULD be named just 'id' in lower case and SHOULD NOT contain any prefix or a suffix.

Do
```
id
```

Don't
```
post_id
postID
```

Foreign key columns SHOULD use singular model name with '_id' suffix.

Do
```
post_id
```

Don't
```
postId
fk_post_id
```



