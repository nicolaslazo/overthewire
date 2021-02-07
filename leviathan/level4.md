# Level 4

```
leviathan3@leviathan:~$ ls -la
total 32
drwxr-xr-x  2 root       root        4096 Aug 26  2019 .
drwxr-xr-x 10 root       root        4096 Aug 26  2019 ..
-rw-r--r--  1 root       root         220 May 15  2017 .bash_logout
-rw-r--r--  1 root       root        3526 May 15  2017 .bashrc
-r-sr-x---  1 leviathan4 leviathan3 10288 Aug 26  2019 level3
-rw-r--r--  1 root       root         675 May 15  2017 .profile
leviathan3@leviathan:~$ file level3 
level3: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=ed9f6a6d1c89cf1f3f2eff370de4fb1669774fd5, not stripped
leviathan3@leviathan:~$ ./level3 
Enter the password> asldfkjasd
bzzzzzzzzap. WRONG
leviathan3@leviathan:~$ ltrace ./level3 
__libc_start_main(0x8048618, 1, 0xffffd694, 0x80486d0 <unfinished ...>
strcmp("h0no33", "kakaka")                                                                              = -1
printf("Enter the password> ")                                                                          = 20
fgets(Enter the password> kakaak
"kakaak\n", 256, 0xf7fc55a0)                                                                      = 0xffffd4a0
strcmp("kakaak\n", "snlprintf\n")                                                                       = -1
puts("bzzzzzzzzap. WRONG"bzzzzzzzzap. WRONG
)                                                                              = 19
+++ exited (status 0) +++
leviathan3@leviathan:~$ ltrace ./level3 
__libc_start_main(0x8048618, 1, 0xffffd694, 0x80486d0 <unfinished ...>
strcmp("h0no33", "kakaka")                                                                              = -1
printf("Enter the password> ")                                                                          = 20
fgets(Enter the password> kakaka
"kakaka\n", 256, 0xf7fc55a0)                                                                      = 0xffffd4a0
strcmp("kakaka\n", "snlprintf\n")                                                                       = -1
puts("bzzzzzzzzap. WRONG"bzzzzzzzzap. WRONG
)                                                                              = 19
+++ exited (status 0) +++
leviathan3@leviathan:~$ ltrace ./level3 
__libc_start_main(0x8048618, 1, 0xffffd694, 0x80486d0 <unfinished ...>
strcmp("h0no33", "kakaka")                                                                              = -1
printf("Enter the password> ")                                                                          = 20
fgets(Enter the password> snlprintf
"snlprintf\n", 256, 0xf7fc55a0)                                                                   = 0xffffd4a0
strcmp("snlprintf\n", "snlprintf\n")                                                                    = 0
puts("[You've got shell]!"[You've got shell]!
)                                                                             = 20
geteuid()                                                                                               = 12003
geteuid()                                                                                               = 12003
setreuid(12003, 12003)                                                                                  = 0
system("/bin/sh"$ 
```

That was weirdly easy compared to the last one... the password is vuH0coox6m.
