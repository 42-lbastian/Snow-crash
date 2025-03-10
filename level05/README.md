<h1 align="center"> level05 </h1>

```shell
find / -user flag05 2> /dev/null
```

We have ```/usr/sbin/openarenaserver```

```shell
#!/bin/sh

for i in /opt/openarenaserver/* ; do
	(ulimit -t 5; bash -x "$i")
	rm -f "$i"
done
```
