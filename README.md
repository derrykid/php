# PHP cheatsheet


### Comments
```
// one line comment

/*
This is a multiple-lines comment block
*/
```

### PHP File identifier
```php
// opening tag
<?php

// Enable strict typing (first line of PHP file)
<?php
 declare (strict_types=1);

// inclue a PHP file
require 'app/Product.php'

// Create a namespace
namespace APP;

// Use a namespace
use APP\Product;

//naming variable, functions, class
$firstName = "Mike"; // camelCase
function updateProduct(); // camelCase
class ProductItem // StudlyCaps
const ACCESS_KEY = "123abc"; // all uppder case with underscore seperators
```

### Output & Input
```php
echo "Hello World";

// Debug output
var_dump($names);
print_r($products);

// Input from console
$name = readline('What is your name: ');
```
### Variable Declaration
```php
$name = 'Mike'; // string
$isActive = true; //boolean
$number = 25; //integer
$amount = 99.95; //float

$fruits = array('peach', 'apple', 'banana'); //array
$fruits = ['orange', 'apple', 'banana'] //array


// type conversion
$age = 26; // integer
echo (string)$age; // will echo out $age as string once, but $age is still integer
$age = (int)readline('Your age: ');
echo "Your age is" . (string)$age;

echo gettype($age); //int
echo is_int($age); //true
echo isfloat(12.5); //true
echo is_string($name); //true
```

