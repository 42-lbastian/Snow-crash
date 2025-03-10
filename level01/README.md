<h1 align="center"> level01 </h1>

We can look a the passwd file:
```shell
cat /etc/passwd
```

One line is suspect:
```
flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash
```
It is hashed, but we can use John the Ripper. Let's put in in a file, then:
```shell
john --show level01
```

Result:
```
flag01:abcdefg
```

It work !
