# Description

Unzip this archive and find the file named 'uber-secret.txt'
* Download zip file

# Solution

```wget https://artifacts.picoctf.net/c/500/files.zip```

```unzip file.zip```

![image](https://github.com/noamgariani11/picoGym-Exclusive/assets/91398631/f086585c-3950-49c2-8591-a97b6435c641)

You can see a directory called ".secret". A "." in front of the filename in Linux makes the directory/file hidden. So the flag is probably there. I assume uber-secret.txt based on this, but I was not going to go through the folders manually so I used grep.

```grep -R pico```

This command recursivly looks through every file for any mention of "pico". This command gives the flag.

It also showed that this wast the file path of the flag: ```files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt```. So the assumption previously made was correct on the location of the flag. If you wanted to see what was in the file without having to traverse to through the directories you could use this command:

```cat files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt```

This gives just the flag.

I also did, ```rm file.zip```, because it was not needed any more. Also because it said this when using grep -R "grep: files.zip: binary file matches".

I ran this command to get just the flag (with grep -R):

```grep -R pico | grep -oE picoCTF{.*} --color=none```

But it could have been done many ways, here are some examples using different functions:
* ```grep -R pico | tail -1 | cut -d ":" -f2```
* ```grep -R pico | sed -n 2p | cut -d ":" -f2```
* ```grep -R picoCTF | cut -d ":" -f2```

I am sure there are other methods, but these are just some that I typically use.
 
Flag: ```picoCTF{f1nd_15_f457_ab44...}```
