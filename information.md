# information

**Site**: [picoCTF](https://www.picoctf.org/)

**Category**: Forensics

**Author**: SUSIE

**OS used**: Kali Linux

----

## Challenge Description

Files can always be changed in a secret way. Can you find the flag? [cat.jpg](http://www.com/)


## Solution:

Clicking the link downloaded a picture of a cat:

![kitteh!](https://github.com/blackholeorbit/nullbit/blob/main/cat.jpg "a title")

At first glance it just looked like an ordinary picture, but I noticed the monitor in the background. Was there any information to glean from that? I took
note of it.

I changed directories and located the file. Since I couldn't necessarily trust the file extension, I used the 'file' command to gather more information.

```
kali@kali:~$ cd Downloads
kali@kali:~/Downloads$ ls
cat.jpg
kali@kali:~/Downloads$ file cat.jpg
cat.jpg: JPEG image data, JFIF standard 1.02, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 2560x1598, components 3
kali@kali:~/Downloads$ 
```



----

### Flag:
```
[flag]
```

