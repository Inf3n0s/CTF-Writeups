#  secrets-of-winter (steganography) -  155 p
**Flag : <span style="color:rgb(60, 179, 113)">ctf{g3t-3xiftool-to-f1ni$h-th3-ch4l1}</span>**

## Solution
Based on the category of the challenge first I started to zoom and change settings like brightness, exposure and contrast until I found the first 3 words of the flag **ctf{g3t-3xiftool-to**.

![secrets-of-winter -part1](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/f9a0e101-5cd2-453f-80c7-ba4a2956791f)

alternatively, you can use [`Stegsolve`](https://github.com/zardus/ctf-tools/tree/master/stegsolve)

After this, I used `exiftool` to some details about this image. I found out that there are two Base64 strings. 

![secrets-of-winter -part2](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/7d67da97-63b0-4cc5-a355-5f805a5f9d9d)

Using [CyberChef](https://cyberchef.org/), I found out the last 3 words of the flag **f1ni$h-th3-ch4l1}**

![secrets-of-winter -part3](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/e71e1e07-613f-4be7-b5d1-e0476fb22560)



