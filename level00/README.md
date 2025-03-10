<h1 align="center"> level00 </h1>

```shell
find / -user flag00 2> /dev/null
```
result:
```
/usr/sbin/john
```

Let's look at it:
```
cat /usr/sbin/john
```
result:
```
cdiiddwpgswtgt
```

Authentication failure if we use it as password.


We can try Cesar cypher:
https://www.dcode.fr/caesar-cipher


The most logical solution:
🠞15 (🠜11)	nottoohardhere


It work !
