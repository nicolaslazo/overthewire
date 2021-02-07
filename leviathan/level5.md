# Level 5

```
leviathan4@leviathan:~$ ls -la
total 24
drwxr-xr-x  3 root root       4096 Aug 26  2019 .
drwxr-xr-x 10 root root       4096 Aug 26  2019 ..
-rw-r--r--  1 root root        220 May 15  2017 .bash_logout
-rw-r--r--  1 root root       3526 May 15  2017 .bashrc
-rw-r--r--  1 root root        675 May 15  2017 .profile
dr-xr-x---  2 root leviathan4 4096 Aug 26  2019 .trash
leviathan4@leviathan:~$ cd .trash/
leviathan4@leviathan:~/.trash$ ls
bin
leviathan4@leviathan:~/.trash$ file bin 
bin: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=00ce1aa55b0e691470f61baff0ee59a6c33fcb50, not stripped
leviathan4@leviathan:~/.trash$ ./bin 
01010100 01101001 01110100 01101000 00110100 01100011 01101111 01101011 01100101 01101001 00001010
```

Translate the binary to text using [an online converter](https://binarytotext.net/) and you get Tith4cokei.
