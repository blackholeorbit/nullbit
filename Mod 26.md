# Mod 26

**Site**: [picoCTF](https://www.picoctf.org/)

**Category**: Cryptography

**Author**: Pandu

**OS used**: Kali Linux

----

## Challenge Description

Cryptography can be easy, do you know what ROT13 is? cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_Ncualgvd}

## Solution:

The description is pretty telling, letting us know we'll need to use ROT13 to decipher. ROT13 is a simple letter substitution cipher that replaces a letter with the 13th letter after it in the alphabet.

I browsed to [Cyberchef](https://gchq.github.io/CyberChef/), selected ROT13 from the recipe list and pasted the text from the description into the 'Input' field. Once I  clicked 'Bake' the flag was exposed.


----

### Flag:

```
picoCTF{next_time_I'll_try_2_rounds_of_rot13_Aphnytiq}
```
