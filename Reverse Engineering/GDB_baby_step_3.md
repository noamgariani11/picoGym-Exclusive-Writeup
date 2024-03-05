# Description

Now for something a little different. 0x2262c96b is <br>
loaded into memory in the main function. Examine byte-<br>
wise the memory that the constant is loaded in by <br>
using the GDB command x/4xb addr. The flag is the <br>
four bytes as they are stored in memory. If you find the <br>
bytes 0x11 0x22 0x33 0x44 in the memory location, your <br>
flag would be: picoCTF{0x11223344}. <br>
Debug this.

# Solution

```wget https://artifacts.picoctf.net/c/531/debugger0_c```

```sudo chmod +x debugger0_c```

```gdb --args ./debugger0_c```

```layout asm```

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/09b33b7c-502d-4627-a698-a6e551575231)

A breakpoint was made with ```b *(main+25)``` because that was after the memory load. The addr in this case would be rbp. Since this is little endian 4 bytes will be subtracted from the base pointer (rbp). So the command will go from ```x/4xb $rbp``` to ```x/4xb-4 $rbp```.

After running with the command ```run``` in gdb with the breakpoint then you can retreive the bytes stored in memory with this command ```x/4xb-4 $rbp``` to get the flag.

```0x6b 0x.. 0x.. 0x22```

x/4xb: The x stands for the examination of memory in gdb. The 4 shows how many bytes will be displayed. The x after the / means that it will show it in hex. The b means that it will be displayed in bytes.

Flag: ```picoCTF{0x6b...22}```
