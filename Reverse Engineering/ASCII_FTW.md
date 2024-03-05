# Description

This program has constructed the flag using hex ascii values. <br>
Identify the flag text by disassembling the program. <br>
You can download the file from here.

# Solution

```wget https://artifacts.picoctf.net/c/508/asciiftw```

```file asciiftw``` shows that this is a "ELF 64-bit LSB pie executable".

```sudo chmod +x asciiftw```

Then I ran the file: ```./asciiftw```. This said that it started with 70 and the description said that it was in hex. This makes sense since 70 in hex is "p" which is the start of picoCTF.

I then ran objdump.

```objdump -d asciiftw```

I looked at the main function:

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/5247c3b0-d716-45d7-a683-644801ba62ef)

And it looks like all the rest of the hex values are just there.

I then put it into it's on text file just so I don't have to run objdump ever time.

```objdump -d asciiftw > disassembled_asciiftw.txt```

I first used grep to get main function and "-A" to get 40 lines under. I tested with 10, 20, 30, 40 until I saw that it included all of the flag.

```cat disassembled_asciiftw.txt | grep "<main>:" -A 40```

I then saw that all of the hex charaters of the flag have movb in front of them so I just used grep to get ever line with movb.

```cat disassembled_asciiftw.txt | grep "<main>:" -A 40 | grep movb```

I then used cut to get everything after the $ sign which would almost get me just the hex.

```cat disassembled_asciiftw.txt | grep "<main>:" -A 40 | grep movb | cut -d "$" -f2```

Then I cut but the the comma as the delimeter which then gave me just the desired hex.

```cat disassembled_asciiftw.txt | grep "<main>:" -A 40 | grep movb | cut -d "$" -f2 | cut -d "," -f1```

I now just had to put it the right format to decode the hex. Since it each value was on a newline I used tr to get rid of each newline.

```cat disassembled_asciiftw.txt | grep "<main>:" -A 40 | grep movb | cut -d "$" -f2 | cut -d "," -f1 | tr -d "\n"```

There was no spaces between the values so I used sed to replace every "0x" with " 0x". 

```cat disassembled_asciiftw.txt | grep "<main>:" -A 40 | grep movb | cut -d "$" -f2 | cut -d "," -f1 | tr -d "\n" | sed 's\0x\ 0x\g'```

Although this left a space at the start that I didn't want so I used sed to get rid of that as well. "^ " is the space at the begining and nothing between \\ signifies the deletion of the space.

```cat disassembled_asciiftw.txt | grep "<main>:" -A 40 | grep movb | cut -d "$" -f2 | cut -d "," -f1 | tr -d "\n" | sed 's\0x\ 0x\g' | sed 's\^ \\g'```

Now it is in the correct format to decode into hex. So I used xxd to reverse the hex to ascii which gave the flag.

```cat disassembled_asciiftw.txt | grep "<main>:" -A 40 | grep movb | cut -d "$" -f2 | cut -d "," -f1 | tr -d "\n" | sed 's\0x\ 0x\g' | sed 's\^ \\g' | xxd -p -r```

I'm sure there are more efficient ways to do this however this is the first way I went about doing it. Also it's good to note that you don't need spaces for xxd to work I just wanted to do it.

Here is alternative method I did that is shorter:

```objdump -d asciiftw | grep movb | grep -oE 0x.*, | tr -d "," | tr -d "\n" | xxd -p -r```

This was another method I did:

```objdump -d asciiftw | grep movb | tail -n +2 | grep -oE 0x.. | sed -n 'p;n' | xxd -p -r```

This also technically works and is shorter:

```objdump -d asciiftw | grep movb | grep -oE 0x.*, | xxd -p -r```

The only difference is you don't have to remove new lines or commas, xxd deals with that when it converts from hex to ascii. Any of these methods will give the flag.

Flag: ```picoCTF{ASCII_IS_EASY_8960...}```
