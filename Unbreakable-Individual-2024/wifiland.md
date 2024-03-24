## wifiland (Network, Wireless) - 50p
**Flag : <span style="color:rgb(60, 179, 113)">CTF{b67842d03eadce036c5506f2b7b7bd25aaab4d1f0ec4b4f490f0cb19ccd45c70}</span>**

## Solution
After reading the description, I found out that I need `ip_client` and `ip_target` to complete the missing keys in the script
```py
from hashlib import sha256

ip_client = ""
ip_target = ""

def calculate_sha256(ip_client, ip_target):

    input_string = ip_client + ip_target
    
    hash_result = sha256(input_string.encode()).hexdigest()
    
    return hash_result

sha256_sum = calculate_sha256(ip_client, ip_target)

print('CTF{'+sha256_sum+'}')
```

Using `aircrack-ng wifiland.cap -w /usr/share/wordlists/rockyou.txt`, I found the PSK= `12345678`.
```
   #  BSSID              ESSID                     Encryption

   1  02:00:00:00:00:00  BitSentinelRulez          Unknown
   2  02:00:00:00:05:00  wifiland                  WPA (1 handshake)

```
Next step is to set the password
by going to `Edit -> Preferences -> Protocols -> IEEE 802.11 -> Decryption keys ->
Edit` and adding the password.

After setting the password, we can see the decrypted traffic. We can easily see the client's and target's ip. 

The final script can be like this:
```py
from hashlib import sha256

ip_target = "93.184.216.34"
ip_client = "10.0.3.19"

def calculate_sha256(ip_client, ip_target):

    input_string = ip_client + ip_target
    
    hash_result = sha256(input_string.encode()).hexdigest()
    
    return hash_result

sha256_sum = calculate_sha256(ip_client, ip_target)

print('CTF{'+sha256_sum+'}')
```

