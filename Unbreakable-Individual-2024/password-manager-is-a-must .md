#  password-manager-is-a-must (forensics) - 50 p
**Flag : <span style="color:rgb(60, 179, 113)">CTF{c112b162e0567cbc5ae20558511ab3932446a708bc40a97e88e3faac7c242423}</span>**
## Solution

This was my favourite one

For this challenge, I will explain two alternative ways to get the flag

First of all, I searched about `kdbx file` and I didn't find too much, but in the past, I solved a challenge on Hackthebox called [Keeper](https://www.hackthebox.com/machines/keeper), where it's something similar to this one. I let a useful writeup for that challenge here to understand better the concepts [Keeper - Writeup](hhttps://medium.com/@amrsadek208/keeper-hack-the-box-write-up-db365f189538)

Let's dive into the solution

I will use [Keepass-dump-masterkey](https://github.com/matro7sh/keepass-dump-masterkey) 

```
└──╼ $ python3 poc.py File.dmp 

2024-03-24 22:18:31,636 [.] [main] Opened File.dmp
Possible password: ●hesecretpass
Possible password: ●!esecretpass
Possible password: ●6esecretpass
Possible password: ●7esecretpass
Possible password: ●\esecretpass
Possible password: ●#esecretpass
Possible password: ●yesecretpass
Possible password: ●kesecretpass
Possible password: ●9esecretpass
Possible password: ●;esecretpass
Possible password: ●Hesecretpass
Possible password: ●[esecretpass
Possible password: ●Iesecretpass
Possible password: ●2esecretpass
Possible password: ● esecretpass
```
And the password is guessy `thesecretpass`, connect to a password manager and find the flag.


or easy alternative you can use a simple command to grep the flag
```bash
└──╼ $ strings File.dmp | grep -i CTF{
CTF{c112b162e0567cbc5ae20558511ab3932446a708bc40a97e88e3faac7c242423}
```