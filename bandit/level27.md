# Level 27

> Good job getting a shell! Now hurry and grab the password for bandit27!

We have the password for this level, but we're still stuck with the custom shell. Let's go back to vim and replace it with bash

```
:set shell=/bin/bash
:shell
```

Let's see the tools we're given for this level:

```
bandit26@bandit:~$ ./bandit27-do 
Run a command as another user.
  Example: ./bandit27-do id
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
3ba3118a22e93127a4ed485be72ef5ea
```

It seems like the password is hashed. A [rainbow table](https://crackstation.net/) doesn't seem to return anything, and bruteforcing it would take too long. 

...the hash itself was the password. Thank god I tried that before spending three hours on this one.
