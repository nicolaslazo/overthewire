# Level 21

> There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

First I set up a daemon that returns the previous password once
`echo GbKksEFF4yrVs6il55v6gwY5aVje5f0j | nc -l -p 33446 &`

And when you run `./suconnect 33446` it returns the new password.
