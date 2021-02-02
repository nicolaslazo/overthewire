# Level 13

> The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

First I reversed the hexdump

```xxd -r data.txt > something```

The file seems to be in gzip format

```
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ file something 
something: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ mv something something.gz
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ gunzip something.gz 
```

More work seems to be needed

```
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ file something 
something: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ mv something something.bz2
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ bzip2 -d something.bz2
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ file something 
something: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ mv something something.gz
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ gunzip something.gz 
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ file something 
something: POSIX tar archive (GNU)
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ tar xf something 
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ ls
data5.bin  data.txt  something
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ tar xf data5.bin
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ ls
data5.bin  data6.bin  data.txt  something
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ mv data6.bin data6.bz2
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ ls
data5.bin  data6  data.txt  something
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ file data6 
data6: POSIX tar archive (GNU)
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ tar xf data6
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ ls
data5.bin  data6  data8.bin  data.txt  something
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ mv data8.bin data8.gz
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ gunzip data8.gz 
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ ls
data5.bin  data6  data8  data.txt  something
bandit12@bandit:/tmp/alskdfjaslkdfjkas$ cat data8 
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```
