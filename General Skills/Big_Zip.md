# Description

Unzip this archive and find the flag.
* Download zip file

# Solution

```wget https://artifacts.picoctf.net/c/503/big-zip-files.zip``` 

```unzip big-zip-files.zip```

```rm big-zip-files.zip```

Unlike [First Find](https://github.com/noamgariani11/picoGym-Exclusive/blob/main/General%20Skills/First_Find.md) this is a much bigger folder so it is not as feasible to just look through the files. Using grep is kind of a must with this one.

Although, ```grep -R pico```, once again provided the flag.

I used this command to get just the flag itself:

```grep -R pico | grep -oE picoCTF{.*} --color=none```

Here are some other ways you can acheive the same thing but with a different method:
* ```grep -R pico | rev | cut -d " " -f1 | rev```
* ```grep -R pico | grep -oE '[^ ]+$' --color=none```
* ```grep -R pico | sed 's/.* //g'```
* ```grep -R pico | awk 'NF>1{print $NF}'```

Flag: ```picoCTF{gr3p_15_m4g1c_ef87...}```
