# sided-curl (Web) - 370 p 
**Flag : <span style="color:rgb(60, 179, 113)">CTF{36555d5ff86de7b5a572f4c01cbfc8c677b1c1287d9c043618442d248d940b65}</span>**
## Solution

First I tested what is happening if I ad `.` to the url resulting `https://google.com/.`. I`ve seen that every time we use an link it adds `.png` at the final.
![curl](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/8415011c-40c8-4fa4-9972-6372594584c7)

After this,I added `127.0.0.1:8000` , the local host mentioned and `/admin#` to see admin login details.
![image](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/077e6c3c-0993-4053-a22f-ffbabf4e8002)


I assumed that to login into the admin panel `admin.php` I need to set `username` and `password` to `admin`.
![image](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/54afff1e-1a2b-4d52-9aa8-66e2de95b8f8)

After the `URL TOO LONG` error I tried to short it by changing `127.0.0.1:8000` to `0:8000`.
![image](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/f2d27706-2b9e-42cb-9ad8-5d68516b010f)