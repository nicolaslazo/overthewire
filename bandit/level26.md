# Level 26

> Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

We can check `/etc/passwd` to see each user's default shell:

```bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext```

This is the contents of `/usr/bin/showtext`:

```bash
#!/bin/sh

export TERM=linux

more ~/text.txt
exit 0
```

This one was so outlandish I had to look up some help. Apparently the entry point is shrinking the terminal to the point `more` needs to paginate the content of `/home/bandit26/text.txt` and pressing `v` will open the text editor. I know that to switch files from vim you have to use `:e filename` and switched to `/etc/bandit_pass/bandit26`.
