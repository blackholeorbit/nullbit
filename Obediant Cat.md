# Obediant Cat

**Site**: [picoCTF](https://www.picoctf.org/)

**Category**: General Skills

**Author**: SYREAL

**OS used**: Kali Linux

----

## Challenge Description
This file has a flag in plain sight (aka "in-the-clear"). [Download flag](http://www.com).

## Solution:

After I clicked the "Download flag" link, that downloaded the file to the default location in Kali - the 'Downloads' directory. I opened a terminal and used
the 'pwd' (print working directory) command to figure out where I was in the file system.

```
kali@kali:~$ pwd
/home/kali
```

I used the 'ls' command to list the contents of the Kali directory and then changed to that directory using the 'cd' command. Once in the Downloads directory, I typed
'ls' again to view the contents. And there's the file I was looking for - named 'flag'.
```
kali@kali:~$ ls 
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  thinclient_drives
kali@kali:~$ cd Downloads
kali@kali:~/Downloads$ ls
flag
```
I opened that file using the 'cat' command (short for concatenate), revealing the flag.

```
kali@kali:~/Downloads$ cat flag
```
----

### Flag:
```
picoCTF{s4n1ty_v3r1f13d_2aa22101}
```


