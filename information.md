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

![kitteh!](https://github.com/blackholeorbit/nullbit/blob/main/Images/cat.jpg "a title")

At first glance it just looked like an ordinary picture, but I noticed the monitor in the background. Was there any information to glean from that? I took
note of it.

I changed directories and located the file. Since I couldn't necessarily trust the file extension, I used the 'file' command to gather more information.

```
kali@kali:~$ cd Downloads
kali@kali:~/Downloads$ ls
cat.jpg
kali@kali:~/Downloads$ file cat.jpg
cat.jpg: JPEG image data, JFIF standard 1.02, aspect ratio, density 1x1, segment length 16, baseline,
precision 8, 2560x1598, components 3
kali@kali:~/Downloads$ 
```
I didn't see anything that stood out there, so I ran exiftool and that resulted in something interesting. The 'License' line looked a little weird!

```
kali@kali:~/Downloads$ exiftool cat.jpg
ExifTool Version Number         : 12.16
File Name                       : cat.jpg
Directory                       : .
File Size                       : 858 KiB
File Modification Date/Time     : 2021:07:24 22:16:41+00:00
File Access Date/Time           : 2021:07:24 22:16:41+00:00
File Inode Change Date/Time     : 2021:07:24 22:16:47+00:00
File Permissions                : rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
kali@kali:~/Downloads$ 
```

I copied the field next to 'License' and browsed to [CyberChef](https://gchq.github.io/CyberChef/). I loaded up the Magic recipe and pasted that field into the 'Input' box and clicked 'Bake'. That resulted in capturing the flag.

----

### Flag:
```
picoCTF{the_m3tadata_1s_modified}
```

