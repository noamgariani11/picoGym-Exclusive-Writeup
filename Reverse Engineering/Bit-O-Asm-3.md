# Description

Can you figure out what is in the eax register? Put your answer <br>
in the picoCTF flag format: picoCTF{n} where n is the contents <br>
of the eax register in the decimal number base. If the answer <br>
was 0x11 your flag would be picoCTF{17}. <br>
Download the assembly dump here.

# Solution

```wget https://artifacts.picoctf.net/c/530/disassembler-dump0_c.txt```

```cat disassembler-dump0_c.txt```

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/491d697f-1a78-4386-8087-933e537b1f7a)

This is the key part to look at: 
```
<+15>:    mov    DWORD PTR [rbp-0xc], 0x9fe1a
<+22>:    mov    DWORD PTR [rbp-0x8], 0x4
<+29>:    mov    eax, DWORD PTR [rbp-0xc]
<+32>:    imul   eax, DWORD PTR [rbp-0x8]
<+36>:    add    eax, 0x1f5
```

In <+29> mov is used to copy the data from the DWORD PTR [rbp-0xc] into eax. This is 0x9fe1a.

To convert this hex to decimal you can use an online tool, or various method in the command line to do this. I initially used the printf method.

```printf "%d" 0x9fe1a```

Then in <+32> imul is used to multiply data from DWORD PTR [rbp-0x8] which is 0x4 into what is currently in eax.

```printf "%d" 0x4```

Then multiply whatever was got from ```printf "%d" 0x9fe1a``` and ```printf "%d" 0x4```.

Lastly in <+36> add is used to add what is currently in eax with 0x1f5.

```printf "%d" 0x1f5```

Than take that value and add it to the value that was previously got.

This is the final value needed for the flag.

Like the hint mentioned:

"Not everything in this disassembly listing is optimal."

Which is why there are many parts of the asm that is not used.

The contents of that command wrapped in picoCTF{} is the flag.

n being the number found from the conversion.

Flag: ```picoCTF{n}```
