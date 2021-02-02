# Level 18

> There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new
>
> NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

The previous level prints an RSA private key instead of a plaintext password, so to log in I had to dump that into a file, change its permissions to 400 to satisfy `ssh`'s security requirements and used that as my identity file.

I used diff to see what changed between files.

```diff passwords.old passwords.new```
