# Level 7

This new script requires a 4-digit code. Seems easy to bruteforce.

```bash
#!/bin/bash

for i in {0000..9999}; do
    ~/leviathan6 $i;
done
```

You'll get a shell. Use that to print the password file (ahy7MaeBo9).

And that was the end of this game! I wasn't familiar with `ltrace` before writing this walkthrough, so that's a cool tool to have at hand. The only level that made me struggle a little was 3; I spotted the problem with unescaped filenames at first glance but I couldn't quite figure out how to exploit that.
