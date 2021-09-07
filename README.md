# PHP cheatsheet

### strict type
```
declare(strict_types=1);
```
###  opening tag
```
<?php

// if your php file are coded entire in php, you shall not have closing tag
?>
```
###  echo & print - echo is preferred way cuz echo is faster than print
```
echo 'Hello World'; // single quote or double quote is ok, have semicoloum.
echo 'Hello', ' ', 'World'; // You cannot do this with print

# escaping apostrophe
echo "John's home"; // use double quote
echo 'John/'s home'; // use backslash character

print 'Hello world'; // in addition, 'print' has a return value of '1'
echo print 'Hello world'; /*Hello world1*/
```

### variables
```
$name
$_POST
// cannot start with a number
e.g. $123name
// cannot include special characters
e.g. $cool#@a
```
variables are being assigned by value, not by variable
```
$x = 1;
$y = $x;
$x = 3;

echo $y; // will print 1, not 3

# if you want to assign a variable by a variable.

$x = 1;
$y = &$x; // every time $x changes, $y changes.
```

### variable within texts
```
$firstname = 'Gio';
echo 'Hello $firstname'; // Hello $firstname
echo "Hello $firstname'; // Hello Gio
echo "Hello {$firstname}'; // Hello Gio, more clarity with curly brackets
echo 'Hello ' . $firstname; // Hello Gio
```

### embed in HTML
```
// for example, within h1 tag
<h1>
<?php echo "Hello world"; ?>
</h1>

// if want to echo in chosen tags; not recommend to echo out html tags in php
<?php
echo '<p>' . $x . '</p>;
?>
```

### comments
```
// comments - 1 line
#  comments - 1 line
/**/   comments - multi lines

/**  duck block
*		 usually for documentation
*/
```
### Constant - cannot change once define
```
define('name', 'value'); // constant is case sensitive
echo name; // you don't need the '$' in front;
defined('name'); // check if it's defined

const STATUS_NAME = 'paid'; // 2nd way to define
echo STATUS_NAME;


// predefined and magic constant
echo PHP_VERSION; // predefined constant
echo __LINE__; // magic constant
echo __FILE__; 


# variable variable
$foo - 'bar';
$$foo = 'baz'; // equals $bar = 'baz';

echo $bar; // 'baz'
```

### Data types - dynamic type
php type is actually not defined until the value is given. Type Coercion/type casting is acceptable.
```
$value = 2; // int
echo (string)$value; // echo out 2
echo gettype((string)$value); // int(2);
```

####  4 Scalar types
```
# boolean - true / false
$completed = true; // echo out 1 ; false echo nothing. (everytime you try to print, php will try to cast it into string)


# following are false. Anything else will evaluate as true
integer 0 or -0
floats 0.0 -0.00
'' = false
'0'
[] // empty string
null = false


# int = 1, 2, 3, 0, -1 (no decimal)
$x = 2_000; // readibility; PHP 7 and higher

# float = 1.6 -13.22 // avoid directly compare 2 floats. It might cause unexpected error

# string = "Gio"
$first = 'Will';
$last = 'Smith';
$fullname = "{$fist}_{$last}"; // Will_Smith

$name = $first . ' ' . $last;
echo $name;

echo $name[0]; // 'W'
echo $name[-1]; // 'h'

// Herodoc - with variable; will echo out everything also the value of variable
$x = 1;
$text = <<<TEXT
Line 1 $x
Line 2 $y ' "
TEXT;

echo nl2br($text);

// Nowdoc - w/o variable; echo everything w/o the value of variable
$x = 1;
$text = <<<'TEXT'
Line 1 $x
Line 2 $y
TEXT;

echo nl2br($text);


// find out what type it is
var_dump($completed); // bool(true);
echo gettype($completed);

```
### array - list of string, numbers etc
```
$companies = [1, 2, 3, 9.12, 'true'];
echo #companies; // error
print_r($companies);

$programming = ['php', 'java', 'python'];
$programming = array('a', 'b', 'c');

# change the element inside array
$programming[1] = 'C++';

# count how many elements in array
echo count($programming);

# make array more readable
echo '<pre>';
print_r($programming);
echo '</pre>';

# push element into array
$programming[] = 'C';
array_push($programming, 'C++', 'C', 'GO');

# name your keys - associative arrays
$data = [
	'John' => '21',
	'Jack' => '28'
];

// add new one
$data['Will'] = '31';

// specify a key
$newname = 'Ray';
$data[$newname] = '28';

# multi-dimensional arrays
$data = [
	'John' =>[
			'age' => 22,
			'marriage' => 'married',
			'job' => 'engineer'
		],
	'Jack' =>[
			'age' => 24,
			'marriage' => 'married',
			'job' => 'teacher'
		],
];
echo $data[1][0]; // 24

// remove one element from array, array will be reindexed.
array_shift($data); // remove 1st one
array_pop($data);   // remove last one

// check if a key exists in array. If you want to check if a key exists, better run this way.
// cuz isset() will check if a key it's null or not. might return error in some cases
$array = ['a' => 1, 'b' => null];
array_key_exists('a', $array);

```
### Operators
```
# arithmetic operators (+ - * /  % **)
10 + 1 // 11
10 - 1 // 9
10 * 2 // 20
10 / 5 // 2
10 / 3 // 1
10 ** 2 // 100

# assignment operators (= += -= *= /= %= **=)
$x = 1;
$x += 1; // $x = $x + 1
$x -= 1; // $x = $x - 1
$x *= 1; // $x = $x * 1
$x /= 1; // $x = $x / 1
$x %= 1; // $x = $x % 1
$x **= 1; // $x = $x ** 1

# String operators/ concatenation operator
$x = 'Hello';
$x .= 'World';
echo $x; // 'HelloWorld'

# Comparison operators (== === != !=== <> >= <= < > <==> ?? ?:)
$x = 5;
$y = '5';

var_dump($x == $y); // bool(true)
var_dump($x === $y); // bool(false)


# ternary operator
$result = $y === false ? 'y is number' : 'y is string'; // y is string

# null coalescing operator - mainly used to work with null
$x = null;
$y = $x ?? 'Hello'; // 'Hello'

// if $x is null, then $y is the value after '??'. Otherwise it's the value of $x.


```
# object
# callable
# iterable
#### 2 special types
```
# resource
# null
```
