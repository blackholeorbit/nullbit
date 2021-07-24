# Wave a Flag

**Site**: [picoCTF](https://www.picoctf.org/)

**Category**: General Skills

**Author**: SYREAL

**OS used**: Kali Linux

----

## Challenge Description
Can you invoke help flags for a tool or binary? [This program](http://www.com) has extraordinarily helpful information...

## Solution:

I clicked the link to download the file and then opened a terminal, entering the 'pwd' command to list the current directory. I typed 'ls' to list the
contents and 'cd' (change directory) to switch to the Downloads directory.

```
kali@kali:~$ pwd
/home/kali
kali@kali:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  thinclient_drives
kali@kali:~$ cd Downloads
```

Entering the 'ls' command revealed a file called 'warm'. Since there was no extension, I used the command 'file' to gather some information about it (binary).

```
kali@kali:~/Downloads$ ls
warm
kali@kali:~/Downloads$ file warm
warm: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter
/lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=3aa19b2a9cc4e093d64025eab8f510679b523455, with
debug_info, not stripped
```

Looking back at the description gave me a hint on the direction in which I needed to head (Can you invoke help flags for a tool or binary?). Using the 'strings'
command and piping it to 'less' exposed the flag.

```
kali@kali:~/Downloads$ strings warm | less

/lib64/ld-linux-x86-64.so.2
libc.so.6
puts
printf
__cxa_finalize
strcmp
__libc_start_main
GLIBC_2.2.5
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
=y       
=W       
=Z       
AWAVI
AUATL
[]A\A]A^A_
Hello user! Pass me a -h to learn what I can do!
Oh, help? I actually don't do much, but I do have this flag here: __picoCTF{b1scu1ts_4nd_gr4vy_30e77291}__
I don't know what '%s' means! I do know what -h means though!
;*3$"
GCC: (Ubuntu 7.5.0-3ubuntu1~18.04) 7.5.0
/usr/lib/gcc/x86_64-linux-gnu/7/include
/usr/include/x86_64-linux-gnu/bits
/usr/include
warm.c
stddef.h
types.h
libio.h
stdio.h
sys_errlist.h
_IO_buf_end
_old_offset
sys_nerr
_IO_save_end
short int
size_t
_IO_write_ptr
_flags
_IO_buf_base
_markers
_IO_read_end
stderr
_lock
long int
_cur_column
_IO_2_1_stderr_
_IO_FILE_plus
_pos
argv
_sbuf
_IO_FILE
unsigned char
argc
_IO_2_1_stdin_
_IO_marker
:
```
I used Ctrl + Z to return to the terminal.

----

### Flag:
```
picoCTF{b1scu1ts_4nd_gr4vy_30e77291}
```
