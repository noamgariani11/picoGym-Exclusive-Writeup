# Description

Can you figure out what is in the eax register? Put your answer <br>
in the picoCTF flag format: picoCTF{n} where n is the contents <br>
of the eax register in the decimal number base. If the answer <br>
was 0x11 your flag would be picoCTF{17}. <br>
Download the assembly dump here.

# Solution

```wget https://artifacts.picoctf.net/c/509/disassembler-dump0_a.txt```

```cat disassembler-dump0_a.txt```

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/8aa083f4-0847-481e-ace7-2a85d059c080)

Based on the contents of the asm and the description the contents of the eax register is 0x30.

To convert this hex to decimal you can use an online tool, or various method in the command line to do this. I initially used the printf method.

```printf "%d" 0x30```

The contents of that command wrapped in picoCTF{} is the flag. 

n being the number found from the conversion.

Flag: ```picoCTF{n}```
