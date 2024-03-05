# Description

This service can provide you with a random number, <br>
but can it do anything else? <br>
Connect to the program with netcat: <br>
$ nc saturn.picoctf.net 51291 <br>
The program's source code can be downloaded here.

# Solution

```wget https://artifacts.picoctf.net/c/515/picker-I.py```

The source code of the program can now be seen and ran locally. When looking you can see getRandomNumber() function, win() function (that prints the flag), and this:

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/7714e588-81ea-4951-9b72-886711fa83ba)

If you run ```python3 picker-I.py``` and put a random input it says that it is not defined. If you put in the recommendation of getRandomNumber it gives 4 which is what was seen in the function in the code. So by inputting win you could get the flag to print. When done locally it will say that there is no file flag, so you need to run it with netcat:

```nc saturn.picoctf.net 51291```

Input the string "win" to call the win function and it gives this text:

```0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x63 0x65 0x34 0x62 0x35 0x64 0x35 0x62 0x7d```

This is in hexadecimal, so you can input this into [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')) with the decoding from hex to get the flag.

Flag: ```picoCTF{4_d14m0nd_1n_7h3_r0u...5d5b}```
