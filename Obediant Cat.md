# Obediant Cat

**Category**: General Skills

**Author**: Syreal

**OS used**: Kali Linux

----

## Challenge Description
This file has a flag in plain sight (aka "in-the-clear"). [Download flag](http://www.com).

## Solution

After I clicked the "Download flag" link, that downloaded the file to the default location in Kali - the 'Downloads' directory. I opened a terminal and used
the 'pwd' command to figure out where I was in the file system. The command 'pwd' stands for 'print working directory'.

```
kali@kali:~$ pwd
/home/kali
```

I used the 'ls' command to list the contents of the Kali directory. Utilizing the 'cd' (change directory) command, I moved into the Downloads directory and
used 'ls' again to view the contents. And there's the file I needed - it's named 'flag'.
```
kali@kali:~$ ls 
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  thinclient_drives
kali@kali:~$ cd Downloads
kali@kali:~/Downloads$ ls
flag
```
I needed to open that file, so I used the 'cat' command (short for concatenate). That opened the file, revealing the flag.

```
kali@kali:~/Downloads$ cat flag
```
----

### Flag:
```
picoCTF{s4n1ty_v3r1f13d_2aa22101}
```


