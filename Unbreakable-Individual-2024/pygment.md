# pygment (web) - 305p
**Flag : <span style="color:rgb(60, 179, 113)">ctf{2ae4644b1e4cbc1f560c52f3ee0985043d3e0acf0f766851382974646578ec39}</span>**

## Solution


Using the details of the warning, we could understand that first, we need to define the 'a' and 'b' arrays. 
```
Warning: Undefined array key "a" in /var/www/html/index.php on line 77 Warning: Undefined array key "b" in /var/www/html/index.php on line 77 Fatal error: Uncaught RuntimeException: sh: 1: pygmentize: not found in /var/www/html/index.php:63 Stack trace: #0 /var/www/html/index.php(77): Pygmentize::highlight(NULL, NULL) #1 {main} thrown in /var/www/html/index.php on line 63 
```

I found this on [Github](https://github.com/dedalozzo/pygmentize/issues/1), it is an issue about **Remote Code Execution**, the challenge is vulnerable to PHP functions and injection.

![pygment-2](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/6c93ac03-10f8-4ff2-bc0c-74abf62bf1df)

Then was easy to get the flag using the command 'cat%20flag.php' and then opening the inspect elements.

![pygment-3](https://github.com/Inf3n0s/CTF-Writeups/assets/75357316/edb9598a-2740-4496-bf03-2bf7641110da)



