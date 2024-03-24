## wifibasic (Network, Wireless) - 50 p
**Flag : <span style="color:rgb(60, 179, 113)">CTF{73841584e4c011c940e91c76bf1c12a7a4850e4b3df0a27ba8a35388c316d468}</span>**

## Solution
After reading the description, I found out that I need PSK, ESSID and BSSID to complete the missing keys in the script
```py
from hashlib import sha256


BSSID = ""

ESSID = ""

PSK = ""


def calculate_sha256(bssid, essid, psk):

    input_string = bssid + essid + psk
    
    hash_result = sha256(input_string.encode()).hexdigest()
    
    return hash_result
    

sha256_sum = calculate_sha256(BSSID, ESSID, PSK)

print('CTF{'+sha256_sum+'}')
```

Using `aircrack-ng wifiland.cap -w /usr/share/wordlists/rockyou.txt`, I found the PSK= `tinkerbel`, BSSID and ESSID.
```
# BSSID             ESSID               Encryption
1 02:00:00:00:00:00 BitSentinelRulez    WPA (1 handshake)
2 02:00:00:00:01:00 Unbreakabl3         Unknown
3 02:00:00:00:02:00 YetAnotherHacker    WPA (0 handshake)
4 02:00:00:00:03:00 Unbreakable         Unknown
5 02:00:00:00:04:00 TargetHiddenSSID    WPA (1 handshake)
```

![aircrack-ng](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/ae174f9d-439f-410d-baed-1f0814753bd3)

After that fill information in a script and receive the flag.

The final script can be like this:
```py
from hashlib import sha256

BSSID = "02:00:00:00:04:00"

ESSID = "TargetHiddenSSID"

PSK = "tinkerbell"

def calculate_sha256(bssid, essid, psk):

    input_string = bssid + essid + psk

    hash_result = sha256(input_string.encode()).hexdigest()

    return hash_result

sha256_sum = calculate_sha256(BSSID, ESSID, PSK)

print('CTF{'+sha256_sum+'}')
```

