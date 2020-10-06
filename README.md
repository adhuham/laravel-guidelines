# Guidelines and Best Practices for Building robust Web Application in Laravel
What follows are guidelines and best practices to consider while building web applications using Laravel framework.
Laravel is a free, open-source PHP web framework, created by Taylor Otwell and intended for the development of web applications following the model–view–controller (MVC) architectural pattern and based on Symfony (Wikipedia).
This guide includes both best practices and coding guidelines, some of which are highly opinionated. Thus, treat this guide as a general guideline to follow, not as a rule book.

## Naming Conventions
### Controllers
All controller names MUST start with a singular noun, followed by the word "Controller" at the end. They should be in PascalCase.

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
All model names MUST be in singular form in PascalCase.

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




