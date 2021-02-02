# Level 31

> There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo. The password for the user bandit30-git is the same as for the user bandit30.

```
bandit30@bandit:/tmp/fafafa/repo$ cat README.md 
just an epmty file... muahaha
bandit30@bandit:/tmp/fafafa/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
bandit30@bandit:/tmp/fafafa/repo$ git log
commit 3aefa229469b7ba1cc08203e5d8fa299354c496b
Author: Ben Dover <noone@overthewire.org>
Date:   Thu May 7 20:14:54 2020 +0200

    initial commit of README.md
```

Well that doesn't help. 

Messing with the files in `.git`, I found this:

```
bandit30@bandit:/tmp/fafafa/repo/.git$ cat packed-refs
# pack-refs with: peeled fully-peeled 
3aefa229469b7ba1cc08203e5d8fa299354c496b refs/remotes/origin/master
f17132340e8ee6c159e0a4a6bc6f80e1da3b1aea refs/tags/secret
```

Call `git show secret` to reveal the password to the next level.
