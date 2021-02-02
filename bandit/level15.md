# Level 15

> The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

We can use `netcat` to send arbitrary data to a port
```echo 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e | nc localhost 30000```
