# Level 2

This home dir has only a single file check: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=c735f6f3a3a94adcad8407cc0fda40496fd765dd, not stripped.

Let's get the hexdump to see if we can spot any interesting strings

```
...
00000500: 7cff ffff c605 34a0 0408 01c9 f3c3 6690  |.....4.......f.
00000510: b810 9f04 088b 1085 d275 05eb 938d 7600  .........u....v.
00000520: ba00 0000 0085 d274 f255 89e5 83ec 1450  .......t.U.....P
00000530: ffd2 83c4 10c9 e975 ffff ff8d 4c24 0483  .......u....L$..
00000540: e4f0 ff71 fc55 89e5 5351 83ec 20c7 45f0  ...q.U..SQ.. .E.
00000550: 7365 7800 c745 e973 6563 7266 c745 ed65  sex..E.secrf.E.e
00000560: 74c6 45ef 00c7 45e5 676f 6400 c745 e06c  t.E...E.god..E.l
00000570: 6f76 65c6 45e4 0083 ec0c 6890 8604 08e8  ove.E.....h.....
00000580: 3cfe ffff 83c4 10e8 44fe ffff 8845 f4e8  <.......D....E..
00000590: 3cfe ffff 8845 f5e8 34fe ffff 8845 f6c6  <....E..4....E..
000005a0: 45f7 0083 ec08 8d45 f050 8d45 f450 e8fd  E......E.P.E.P..
000005b0: fdff ff83 c410 85c0 752b e821 feff ff89  ........u+.!....
...
```

[Hey I recognise that!](https://www.youtube.com/watch?v=0Jx8Eay5fWQ)

```
leviathan1@leviathan:~$ ./check 
password: love
Wrong password, Good Bye ...
leviathan1@leviathan:~$ ./check 
password: secret
Wrong password, Good Bye ...
leviathan1@leviathan:~$ ./check 
password: sex
$ whoami
leviathan2
```

I hate that that actually worked. The password for the next level is ougahZi8Ta.
