# Description

Can you figure out what is in the eax register? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Download the assembly dump here.

# Solution

```wget https://artifacts.picoctf.net/c/510/disassembler-dump0_b.txt```

```cat disassembler-dump0_b.txt```

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/8fd75e2f-4a72-4ac9-82c3-f0950f79ee13)

You can see where "eax" is there is "DWORD PTR [rbp-0x4]". So it is pointed to [rbp-0x4] which has a value of 0x9fe1a.

To convert this hex to decimal you can use an online tool, or various method in the command line to do this. I initially used the printf method.

```printf "%d" 0x9fe1a```

The contents of that command wrapped in picoCTF{} is the flag.

n being the number found from the conversion.

Flag: ```picoCTF{n}```
