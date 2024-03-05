# Description

main calls a function that multiplies eax by a constant. <br>
The flag for this challenge is that constant in decimal <br>
base. If the constant you find is 0x1000, the flag will be <br>
picoCTF{4096}. <br>
Debug this.

# Solution

```wget https://artifacts.picoctf.net/c/532/debugger0_d```

```sudo chmod +x debugger0_d```

```gdb --args ./debugger0_d```

In gdb I then wrote ```layout asm```:

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/4695368e-cdec-4903-b770-d5ccab217220)

In main+38 it goes to func1 and on func1+14 it has an imul action which means multiplication and it is done on eax. The number is 0x3269 and when leaving gdb with 'q' you can put the following command to get the flag:

```printf "picoCTF{%d}\n" 0x3269 | tee flag.txt```

Note that this could also be done with ```objdump -D debugger0_d | less```, but this challenge was meant for learning gdb.

Flag: ```picoCTF{n}```
