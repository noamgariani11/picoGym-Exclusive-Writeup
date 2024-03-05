# Description

Can you figure out what is in the eax register at the end of the 
main function? Put your answer in the picoCTF flag format: <br>
picoCTF{n} where n is the contents of the eax register in the <br>
decimal number base. If the answer was 0x11 your flag would <br>
be picoCTF{17}. <br>
Disassemble this.

# Solution

```wget https://artifacts.picoctf.net/c/512/debugger0_a```

```sudo chmod +x debugger0_a```

```gdb --args ./debugger0_a```

In gdb I then wrote ```layout asm```:

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/ba050121-1f18-4746-aadc-514c4518b056)

You can leave gdb by clicking the letter 'q'.

Note that you can also find the same thing with this command:
```objdump -D debugger0_a | less``` then searching for the main function.

```printf "%d" 0x86342```

The decimal conversion of that hex value is the flag.

I used this command to get just the flag in a flag.txt file:

```printf "picoCTF{%d}\n" 0x86342 | tee flag.txt```

This both prints the flag and puts it into flag.txt file.

Flag: ```picCTF{n}```
