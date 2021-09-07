# PHP cheatsheet

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
