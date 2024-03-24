#   improper-configuration  (mobile) - 255 p
**Flag : <span style="color:rgb(60, 179, 113)">wlwkfwo2-3cscase-wdc</span>**
## Solution

For this challenge, I will explain decompile the APK file and check what I found

For this step, I use [`apktool`](https://github.com/iBotPeaches/Apktool)

```bash
apktool d imroper-configuration.apk
```

After hours of searching for a standard form of flag with CTF{}, I grep the `app_name` from *`strings.xml`* and works.
