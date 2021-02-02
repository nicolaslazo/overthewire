# Level 9

> The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

I'm sure there's some way to make this cleaner, but this is what I did:
1- Sort the file for `uniq`
2- Use `uniq` to count the occurrences of each line
3- Sort in reverse, to have the line with one occurrence at the top
4- Use `head -n 1` to fetch that line
All put together:
`sort data.txt | uniq -c | sort -r | head -n 1`
