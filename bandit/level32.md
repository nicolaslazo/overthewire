# Level 32

> There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo. The password for the user bandit31-git is the same as for the user bandit31.

```
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

```
echo "May I come in?" > key.txt
git add key.txt
git commit -m "Created key.txt"
git push
```

This warning may pop up when you try to add `key.txt`:
```
bandit31@bandit:/tmp/ewewew/repo$ git add key.txt 
The following paths are ignored by one of your .gitignore files:
key.txt
Use -f if you really want to add them.
```

Follow the advice and include the `-f` flag.
