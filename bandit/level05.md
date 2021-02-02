# Level 5

> The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

There seem to be ten files here, all starting with a hyphen. First I'd run `file -- *` to see the file types

```
-file00: data
-file01: data
-file02: data
-file03: data
-file04: data
-file05: data
-file06: data
-file07: ASCII text
-file08: data
-file09: data
```

`-file07` looks promising. Use `cat -- -file07` to see its contents.
