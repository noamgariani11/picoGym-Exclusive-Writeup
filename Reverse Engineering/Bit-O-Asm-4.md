# Description

Can you figure out what is in the eax register? Put your answer <br>
in the picoCTF flag format: picoCTF{n} where n is the contents <br>
of the eax register in the decimal number base. If the answer <br>
was 0x11 your flag would be picoCTF{17}. <br>
Download the assembly dump here.

# Solution

```wget https://artifacts.picoctf.net/c/511/disassembler-dump0_d.txt```

```cat disassembler-dump0_d.txt```

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/6304e442-e648-4caf-9568-9de5c6d48155)

0x9fe1a = 654874

0x65 = 101

By subtracting 0x65 from 0x9fe1a as seen on <+31> is what is in the eax register. Once converted to decimal it provides the flag.

Flag: ```picoCTF{n}```
