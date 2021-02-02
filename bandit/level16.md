# Level 16

> The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.
>
> Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

`netcat` wouldn't work here, so I googled "netcat with SSL" and found [this very helpful thread](https://serverfault.com/questions/102032/connecting-to-https-with-netcat-nc) that showed the basic syntax for SSL negotiation. The command wouldn't work like that so I had to add `-ign_eof` like suggested.

```echo BfMYroe26WYalil77FoDi9qh59eK5xNr | openssl s_client -connect localhost:30001 -ign_eof```
