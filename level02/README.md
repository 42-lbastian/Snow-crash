<h1 align="center"> level02 </h1>

```
ls -la
```

We have a .pcap file, a network capture, we can use Wireshark to read it.
To download it from vm machine:
```shell
scp -P 22222 level02@localhost:/home/user/level02/level02.pcap .
```

We open the file with Wireshark, then Analyze -> Follow -> TCP stream

![Screenshot from 2025-03-10 12-49-03](https://github.com/user-attachments/assets/e5d286d9-eb78-4c79-b0d5-d21a43392c26)

The password ft_wandr...NDRel.L0L isn't working.

Unscroll Data section on the main window of Wireshark to see hex code of character

The hex code of the char . is 7F, the DEL char. It mean the user just delete char.

So password is ```ft_waNDReL0L=```

It work !
