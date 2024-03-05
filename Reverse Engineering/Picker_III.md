# Description

Can you figure out how this program works to get the <br>
flag? <br>
Connect to the program with netcat: <br>
$ nc saturn.picoctf.net 49706 <br>
The program's source code can be downloaded here.

# Solution

```wget https://artifacts.picoctf.net/c/526/picker-III.py```

By looking at the code ```cat picker-III.py``` it can be seen that you can run help to get more information. When running the script, ```python3 picker-III.py```, and typing help you get this message:

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/cb2fde0c-3b02-452f-a7ba-b6ddd861eeea)

The third function is `write_variable` so by typing 3 you can execute the functin. It then asks for the thing to be written to and then what you want to write to it.

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/1d517faf-f26d-46f3-88ec-c1184940ea4c)

By doing this on getRandomNumber and overwriting it with the win function you could now call the fourth function to get the functionality of the win function.

Now by running 4 you can get flag.txt, but to get the real flag you need to move to the netcat connection:

```nc saturn.picoctf.net 49706```

By doing the same proccess here and running for you should get a series of hex numbers:

```0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x37 0x68 0x31 0x35 0x5f 0x31 0x35 0x5f 0x77 0x68 0x34 0x37 0x5f 0x77 0x33 0x5f 0x67 0x33 0x37 0x5f 0x77 0x31 0x37 0x68 0x5f 0x75 0x35 0x33 0x72 0x35 0x5f 0x31 0x6e 0x5f 0x63 0x68 0x34 0x72 0x67 0x33 0x5f 0x32 0x32 0x36 0x64 0x64 0x32 0x38 0x35 0x7d```

By putting this into [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')) you can get the decoded output which is the flag.

Flag: ```picoCTF{7h15_15_wh47_w3_g37_w17h_u53r5_1n_ch4...dd285}```
