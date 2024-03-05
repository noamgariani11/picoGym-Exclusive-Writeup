# Description

Can you figure out what is in the eax register at the end of the <br>
main function? Put your answer in the picoCTF flag format: <br>
picoCTF{n} where n is the contents of the eax register in the <br>
decimal number base. If the answer was 0x11 your flag would <br>
be picoCTF{17}. <br>
Debug this.

# Solution

```wget https://artifacts.picoctf.net/c/520/debugger0_b```

```sudo chmod +x debugger0_b```

```gdb --args ./debugger0_b```

In gdb I then wrote ```layout asm```:

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/529261d5-f583-4a61-8b10-6bf30dcc8ccc)

Then you can create a breakpoint at main+59 right after the last operation with eax to stop the program after than point.

```b *(main+59)```

Then just run the ```run``` command in gdb and the program will stop at the break point. At this point you can just print out the eax register and it will give you the value of eax at the end of the main function.

```print $eax```

That number as n around picoCTF is the flag.

Flag: ```picoCTF{n}```
