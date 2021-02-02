# Level 7

> The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, and 33 bytes in size.

Running `find / -user bandit7 -group bandit6 -size 33c` returns only one valid filename, `/var/lib/dpkg/info/bandit7.password`.
