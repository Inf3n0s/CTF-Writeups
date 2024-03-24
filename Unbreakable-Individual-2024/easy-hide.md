# easy-hide (Forensics) - 55 p
**Flag : <span style="color:rgb(60, 179, 113)">UNR{sunIZZsunshine}</span>**

## Solution
```
└──╼ $binwalk -e strange-final.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 500 x 500, 8-bit/color RGBA, non-interlaced
1416          0x588           Zlib compressed data, default compression
21346         0x5362          Zip archive data, at least v2.0 to extract, uncompressed size: 467256, name: strange-picture.jpg
487799        0x77177         End of Zip archive, footer length: 22
```
After I downloaded the image, I noticed that it was too big for an image so I extracted it with `binwalk`.

In the output folder, I see a new file called `strange-picture.jpg` which is broken.
```
└──╼ $xxd strange-picture.jpg 
00000000: 6272 6f6b 656e 7a69 6e73 6964 6572 6570  brokenzinsiderep
00000010: 0001 0000 ffe2 01d8 4943 435f 5052 4f46  ........ICC_PROF
00000020: 494c 4500 0101 0000 01c8 0000 0000 0430  ILE............0
00000030: 0000 6d6e 7472 5247 4220 5859 5a20 07e0  ..mntrRGB XYZ ..
00000040: 0001 0001 0000 0000 0000 6163 7370 0000  ..........acsp..
```
The reason is the first bytes of images which are overwritten and we need to fix that.

I noticed that the image in the folder was broken so I used [jpegfix](https://github.com/KeeeX/jpegfix) to fix it.
>npx @keeex/jpegfix -i strange-picture.jpg

After the image was fixed I opened it and got the flag.

![image](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/3e053d61-2da7-4170-b9a5-da4dbbae1c31)