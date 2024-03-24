# rfc-meta (misc,web) - 325p
**Flag : <span style="color:rgb(60, 179, 113)">CTF{5ba73b7f830badc3e9d32e85bcdcc172bc417afbabc92ea7a343bc3b79fd722e4c44c}</span>**

## Solution

First touch when I try to access the `/` endpoint, redirects me to page=1, and step by step to page=15 which redirects us to the `/home` endpoint.

We can see in the HTTP request a set `4354467b35` which if you have enough experience you will know is Hex encoded


![image](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/cbeb3682-971a-4130-ba21-5dfe12754718)

I collect all of the data from each request, concatenated them and put them on CyberChef which decrypts the flag.

![image](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/19e4c790-0806-4cb6-ba5f-b974fa0227c5)
