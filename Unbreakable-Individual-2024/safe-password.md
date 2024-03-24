#  safe-password  (osint) - 50 p
**Flag : <span style="color:rgb(60, 179, 113)">CTF{fdc852bc63a266c8c38db64bef90d62d53ddeef00aa85df7b941ac780b3d75d8}</span>**
## Solution


The challenge gives us a list of passwords and tells us to find the one that appeared over 80 times before. 

First of all, I went to [HaveIBeenPwned](https://haveibeenpwned.com/Passwords) to check the password, but if you do that takes a lot of time. I found a script called [Pwned](https://github.com/sameera-madushan/Pwned) which can test the password in the terminal, but takes too long.

I wrote this Python script to automate the process
```py
import os
import subprocess

def execute_pwned():
    # Get the directory and file paths 
    script_dir = os.path.dirname(os.path.realpath(__file__))
    filename = os.path.join(script_dir, 'leaked.txt')
    
    with open(filename, 'r') as file:
        for line in file:
            password = line.strip()
            subprocess.run(['python3', 'pwned.py', '-p', password])

if __name__ == "__main__":
    execute_pwned()
```

![pwned](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/98fca694-4195-437c-9069-379ec0c3f09a)


After that, I found only `Bubblegum123!` was leaked and I run this bash command to find SHA256



```bash
echo -n "Bubblegum123!" | sha256sum 
```
alternatively you can use a tool online [SHA256 Online](https://emn178.github.io/online-tools/sha256.html)
