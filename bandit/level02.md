# Level 2

> The password for the next level is stored in a file called - located in the home directory

This may not be the most elegant solution to this problem, but I would use `find . -type f -exec cat {} \;`. Copy the password and move on to the next level.
