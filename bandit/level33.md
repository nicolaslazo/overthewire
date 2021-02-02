# Level 33

> After all this git stuff its time for another escape. Good luck!

> WELCOME TO THE UPPERCASE SHELL

Oh yeah! I remember seeing this one! Sadly I'll have to admit I couldn't figure out the solution and had to cheat a little. I knew it had to be something that didn't involve using alphabetic characters, but I'd forgotten about $0. 

Since this is passed as an argument to sh after some text transformation I could use special variables. In sh, all $N from 1-9 represent the arguments passed to the command, but the peculiarity about $0 is that it returns the name of the program itself. The uppercase version of $0 is $0, and if you have something like
```sh -c $0```

It evaluates as
```sh -c sh```

Returning a working shell.

And that was the last game in this series! Apparently more might be coming so even if it hasn't updated in years I'll leave the next password here for future reference: c9c3199ddf4121b10cf581a98d51caee
