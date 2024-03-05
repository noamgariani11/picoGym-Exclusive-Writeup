# Description

I thought that my password was super-secret, but it turns out <br>
that passwords passed over the AIR can be CRACKED, <br>
especially if I used the same wireless network password as <br>
one in the rockyou.txt credential dump. <br>
Use this 'pcap file' and the rockyou wordlist. The flag should <br>
be entered in the picoCTF{XXXXXX} format.

# Solution

I looked at this hint:

"Aircrack-ng can make a pcap file catch big air...and crack a password."

Along with the description mentioning rockyou.txt made this challenge quite straightforward.

```wget https://artifacts.picoctf.net/c/41/wpa-ing_out.pcap```

Then I just ran aircrack-ng with the rockyou word list and the pcap.

```aircrack-ng -w /usr/share/wordlists/rockyou.txt wpa-ing_out.pcap```

This gave the key/password. I then put it in the picoCTF{} format as described in the description and it was the correct flag.

Flag: ```picoCTF{mick...}```
