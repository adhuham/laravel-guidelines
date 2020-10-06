# Guidelines and Best Practices for Building robust Web Application in Laravel
What follows are guidelines and best practices to consider while building web applications using Laravel framework.
Laravel is a free, open-source PHP web framework, created by Taylor Otwell and intended for the development of web applications following the model–view–controller (MVC) architectural pattern and based on Symfony (Wikipedia).
This guide includes both best practices and coding guidelines, some of which are highly opinionated. Thus, treat this guide as a general guideline to follow, not as a rule book.

## Keywords Used
This guidline uses keywords from (https://www.ietf.org/rfc/rfc2119.txt)[RFC 2119] specifications.
   
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




