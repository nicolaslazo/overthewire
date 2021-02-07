# Level 1

```
leviathan0@leviathan:~$ ls -la
total 24
drwxr-xr-x  3 root       root       4096 Aug 26  2019 .
drwxr-xr-x 10 root       root       4096 Aug 26  2019 ..
drwxr-x---  2 leviathan1 leviathan0 4096 Aug 26  2019 .backup
-rw-r--r--  1 root       root        220 May 15  2017 .bash_logout
-rw-r--r--  1 root       root       3526 May 15  2017 .bashrc
-rw-r--r--  1 root       root        675 May 15  2017 .profile
leviathan0@leviathan:~$ ls -la .backup
total 140
drwxr-x--- 2 leviathan1 leviathan0   4096 Aug 26  2019 .
drwxr-xr-x 3 root       root         4096 Aug 26  2019 ..
-rw-r----- 1 leviathan1 leviathan0 133259 Aug 26  2019 bookmarks.html
```

We didn't get any hints as to what to do but looking for hidden files in the home directory I could find this bookmarks file.

```
leviathan0@leviathan:~/.backup$ cat bookmarks.html | grep pass
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is rioGegei8m" ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71">password to leviathan1</A>
```

Seems like using grep with "pass" was enough. Moving to level 2
