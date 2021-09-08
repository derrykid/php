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

# increment/ decrement operators (++ --)
$x = 5;
echo $x++; // echo 5
echo $x;   // echo 6, because $x does the increment after it.

$y = 5;
echo ++$y; // echo 6; because $y does increment first

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

# error control operators (@) - error messages that might be generated will be ignored.
$x = @file('foo.txt');

# logical operator (&& || ! and or xor)
$x = true;
$y = false;
($x && $y) // false
($x || $y) // true
($x && !$y) // true

// short circuiting of logical operator
$x = true;
function hello(){
		echo 'hello';
		return false;
}

var_dump($x && hello()); // bool(true). The 'hello' will not be printed.

# object
# callable
# iterable
```
#### 2 special types
```
# resource
# null
```

### Control structures (if / else / elseif / else if)
```
# if statement
$score = 85;
if ($score >= 90){
	echo 'A';
}
```
embed in HTML
```
// not good for reading
<body>
	<?php
	$score = 74;
	if ($score >= 90){
			echo '<strong>A</strong>';
	} elseif ($score >= 60) {
			echo '<strong>Pass</strong>';	
			} else ($score < 60){
			echo '<strong>Fail</strong>';
	}
</body>

# php alternative syntax. Use ':' instead of curly bracket
<body>
	<?php $score = 74 ?>
	<?php if ($score >= 90): ?>
			<strong>A</strong>
	<?php elseif ($score >= 60): ?>
			<strong>Pass</strong>
	<?php elseif ($score >= 60): ?>
			<strong>Fail</strong>
	<?php endif ?>    // endif in the last tag
</body>
```
### Loops
```
# while loop (run when the condition is true)
$i = 0;
while ($i <= 15){
	echo $i ++;
}

# do while (do a least once)
$i = 0;
do {
	echo $i++;
} while ($i <= 15);

# for
for ($i = 0; $i < 15; $i++){
	echo $i;
}

# foreach (iterate over arrays or objects)
$programming = ['php', 'java', 'c++', 'go'];
foreach($programming as $language){
	echo $language . '<br />';
}


$programming = ['php', 'java', 'c++', 'go'];
foreach($programming as $key => $language){
	echo $key . ': ' . $language . '<br />';
}

unset($language);
// $language variable is not destroyed after the foreach loop, which means there are value in the variable. In this case, an array. Be aware of this, otherwise you might get into some unexpected errors. Or use the unset() to destroy it.

# iterate over associative array
$user = [
		'name' => 'Gio',
		'email'=> 'gio@gmail.com',
		'skills' => ['php', 'go', 'c'],
];

// use json_encode to print the value
foreach($user as $key => $value){
 echo $key . ' : ' . json_encode($value) . '<br />';
}

// use implode() function
foreach($user as $key => $value){
	if(is_array($value)){
			$value = implode(",", $value);
	}
	echo $key . ": " . $value . "<br />";
}

// simply iterate the value
foreach($user as $key => $value){
    echo $key . ': ' ;
    if (is_array($value)){
      foreach($value as $skills){
          echo $skills . ',';
      }
    } else {
        echo $value;                                                        
    } 
    echo "<br />";
    } 
```
### Switch (expression does loose comparision)
```
$paymentstatus = 'paid';

switch($paymentstatus){
		case 'paid':
			echo 'Paid';
			break;    // otherwise, the code will continue running

		case 'declined':
		case 'rejected':
			echo 'Payment declined';
			break;		// you can have 2 cases with same execusion simutaneously

		case 'pending':
			echo 'Pending payment':
			break;

		default:
			echo 'Unknow payment status';

}
```

### Match - exhaustive, have to list all possibilities. php 8+ (it does strict comparison)
```
$paymentstatus = 1;
$paymentstatus = match($paymentstatus){
	1 =>	'paid',
	2, 3 =>  'declined',
	0 => 'pending',
	default => 'Unknown error', // optional
};
```

### include files (require, require_once, include, include_once)
```
include 'file.php';

// require vs include
// include results in warnning, while requires give you error and stop execusion.
// default directory will be written in 'include_path' under php.ini file

# require_once  vs require
require 'file.php';
// variable in another php files will override if you 'require'.
// it's recommended to use 'require_once' to avoid function error with overriding the variables.

# using include within HTML for re-usability
<body>
	<?php include './nav.php' ?>
</body>

# include content into a string
ob_start();
include './nav.php';
$nav = ob_get_clean(); // return the contents of the file, HTML will not be rendered.

var_dump($nav);
```

### functions
```
function foo(){
	echo 'Hello World';
	/* return 'Hello World'; */ this will work. However, you have to store the value inside a variable and echo it outside the func.
}

foo(); 	// call the function
```
```
# return type
function foo(): int|float {  // specify the type ': int'. Use '|' to accept multiple types
// or use mixed to accept diff types
		return 1;
}

# nullable by appending '?'. So it can return 'null' or 'int' in this case.
function foo(): ?int {
		return;
}


```
