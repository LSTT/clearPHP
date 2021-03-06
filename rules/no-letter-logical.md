<!-- PHP Manual -->
# No Letters For Logical Operators

Logical operators comes in two flavors : lettered, also known as boolean, `and`, `or` and `xor`. And with symbols, also known as logical operators, `&&`, `||`, `^`, respectively. However, there is a catch : they are not exchangeable. 

In the documentation, the example shows the difference of precedence : 

```php
<?php
// --------------------
// "||" has a greater precedence than "or"

// The result of the expression (false || true) is assigned to $e
// Acts like: ($e = (false || true))
$e = false || true;

// The constant false is assigned to $f and then true is ignored
// Acts like: (($f = false) or true)
$f = false or true;

var_dump($e, $f);
?>
```

In the result `$e` is `true`, `$f` is `false`. Most of the time, expected precedence is the one associated with the logical operators `&&`, `||`, `^`. It is recommended to use them. 

## Rule Details

This rule require that logical operators uses `&&`, `||`, `^`, instead of `and`, `or` and `xor`. The followings is wrong. 

```php
<?php

$a = 1 and 2 or 3 xor 4;

// mixing style is bad too
$a = 1 and 2 or 3 xor 4;

?>
```

The following patterns are considered OK :

```php
<?php

$a = 1 && 2 || 3 ^ 4;

?>

```
<!--
### Options
-->
## When Not To Use It

When logical operations are never mixed with assignations or ternary operators, this rule may be skipped. However, this is an easily broken pre-requisite.


## Further Reading
* [Logical operators](http://php.net/language.operators.logical)
* ['AND' vs '&&' as operator](http://stackoverflow.com/questions/2803321/and-vs-as-operator)
