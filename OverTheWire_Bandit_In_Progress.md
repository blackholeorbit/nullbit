# OverTheWire - Bandit

**Site**: [OverTheWire-Bandit](https://overthewire.org/wargames/bandit/)

**Category**: Wargame

**Authors**: 
    Steven “Steven” Van Acker, morla
    
**OS used**: Kali Linux

----

## Challenge Description

Bandit Level 0
Level Goal

The goal of this level is for you to log into the game using SSH. The host to which you need to
connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0.
Once logged in, go to the Level 1 page to find out how to beat Level 1.

Commands you may need to solve this level

ssh

## Solution:

I fired up Kali Linux and opened a terminal, using the ssh protocol to connect to the specified server. I was greeted with the following banner.
Note that for brevity purposes, post connection banners won't be listed again.

==In addition, per the request of the OTW staff, I will NOT be listing the flags/passwords==.


```
┌──(kali㉿kali)-[~]
└─$ ssh bandit0@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org's password: 
Linux bandit.otw.local 5.4.8 x86_64 GNU/Linux

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to Steven or morla on
irc.overthewire.org.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ and /proc/ is disabled
  so that users can not snoop on eachother. Files and directories with
  easily guessable or short names will be periodically deleted!

  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few usefull tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /usr/local/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /usr/local/pwndbg/
    * peda (https://github.com/longld/peda.git) in /usr/local/peda/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /usr/local/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)
    * checksec.sh (http://www.trapkit.de/tools/checksec.html) in /usr/local/bin/checksec.sh

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us through IRC on
  irc.overthewire.org #wargames.

  Enjoy your stay!

bandit0@bandit:~$
```
Note that now I'm connected, the username has changed to bandit0. I used the 'ls' command (list) and found a file named 'readme'. I wonder
what we can do with this?

```
bandit0@bandit:~$ls
readme
```
Using the 'cat' command (short for concatenate), I was able to discover the password for the next level in the challenge.

```
bandit0@bandit:~$ cat readme
<!-- This is commented out. -->

bandit0@bandit:~$ 
GNU bash, version 4.4.12(1)-release (x86_64-pc-linux-gnu)
bandit0@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
I logged out of the connection so I could use the password I just grabbed and enter level 1. I used the arrow up key to show the last ssh command,
changing the '0' to a '1'. After connecting, I entered the password from level 0 and entered.

```
┌──(kali㉿kali)-[~]
└─$ ssh bandit1@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit1@bandit.labs.overthewire.org's password:
```
I used the now familiar 'ls' command and located a file. The name was '-'. I tried using 'cat -' but that resulted in no response. I wasn't sure
how to handle this, so I hit a search engine looking for answers. What I discovered was that since I was using '-' after cat, it was expecting
a option. I found that using './' after cat would tell the command to look for a file by that name
in the current director. And just like that, the password was revealed!
```
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat -
^X^C
bandit1@bandit:~$ cat ./-
<!-- This is commented out. -->
bandit1@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```

I copied the password and proceeded to the next level after logging out.

```
┌──(kali㉿kali)-[~]
└─$ ssh bandit2@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit2@bandit.labs.overthewire.org's password:

```
After connecting to level 2, I ran the 'ls' command and it found a file with spaces in the name. I tried the 'strings' command but that
didn't work. Having previously used just the 'cat' command with a file that contained spaces, I knew that alone would fail. I decided
to hit the man pages for some research.

```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ strings spaces in this filename
strings: 'spaces': No such file
strings: 'in': No such file
strings: 'this': No such file
strings: 'filename': No such file
bandit2@bandit:~$ man cat
```
Nothing obvious stuck out on the man pages for cat, so I hit a search engine again, looking for clues. Inside a stackflow forum post, I
found something that might help. Using an apostrophe before and after the file name would allow cat to read the contents, so I gave that
a try.

```
bandit2@bandit:~$ cat 'spaces in this filename'
<!-- This is commented out. -->

bandit2@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
I copied the password for the next level and proceeded, after logging out of the current ssh session.

```       
┌──(kali㉿kali)-[~]
└─$ ssh bandit3@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit3@bandit.labs.overthewire.org's password:
```
Pasting the password from level 2 into the prompt, I gained access to level 3. Using the 'ls' command revealed a directory called
'inhere'. I used the 'cd' command to move into that and ran 'ls' again. The 'inhere' directory appeared to be empty.

From past experience, I knew that using the '-a' option after 'ls' would show everything, including hidden files. The '-a' option
worked, exposing a hidden file aptly named '.hidden'. Using the 'cat' command on it let the cat out of the bag - pun intended!

```
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
bandit3@bandit:~/inhere$ cat .hidden
<!-- This is commented out. -->
bandit3@bandit:~/inhere$ exit
logout
Connection to bandit.labs.overthewire.org closed.

```
After copying the password from that hidden file in level 3, I sshed into level 4.

```         
┌──(kali㉿kali)-[~]
└─$ ssh bandit4@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit4@bandit.labs.overthewire.org's password:

bandit4@bandit:~$
```
The 'ls' command showed a directory called 'inhere'. Using the 'cd' command to move into that directory, I ran 'ls' again and
it listed ten files. I looked back to the clues on the OTW site for this level and read "The password for the next level is
stored in the only human-readable file in the inhere directory".

```
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ 

```
Taking a look at the man pages for cat didn't point me in a helpful direction. Since I'm not too familiar with the find command
yet, even though something told me I needed to use it, I was determined to use my friend cat. After searching through forums, I
found a post that described what a double dash meant. This instructs the cat command not to try and parse what comes after any 
command line options, so I gave that a try.

```
bandit4@bandit:~/inhere$ cat -- -file00
�/`2ғ�%��rL~5�g��� �����
bandit4@bandit:~/inhere$ cat -- -file01
��p,k�;��r*��   �.!��C��J       �dx,�
bandit4@bandit:~/inhere$ cat -- -file02
e�)�#��5��
          ��p��V�_���ׯ�mm
bandit4@bandit:~/inhere$ cat -- -file03
������h!TQO�`�4"aל�߂phT��,�A
bandit4@bandit:~/inhere$ cat -- -file04
?�
bandit4@bandit:~/inhere$ cat -- -file05
�r�l$�?h�9('���!y�e�#�x�O��=�
bandit4@bandit:~/inhere$ cat -- -file06
ly���~��A�f����-E�{���m�����ܗM
bandit4@bandit:~/inhere$ cat -- -file07
<!-- This is commented out. -->
bandit4@bandit:~/inhere$ logout
Connection to bandit.labs.overthewire.org closed.
```
I'm sure this is a sloppy way of discovering the password, but it eventually worked!

----

# To Be Continued...



