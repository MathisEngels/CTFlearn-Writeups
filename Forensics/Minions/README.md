# Minions
[Link to the challenge](https://ctflearn.com/challenge/955)

The flag is encoded (multiple times) and hidden in a file.

## Step 1
We are given an image. I downloaded it, viewed it but nothing interesting.

I used basic commands (`file`, `strings`/`hexdump -C`, `exiftool`).

`strings Hey_You.png` gave me an interesting output:
```
...
IEND
Rar!
$You_Still_Here/Nothing_Here_16/..txt
Ac]I
https://mega.nz/file/wZw2nAhS#i3Q0r-R8psiB8zwUrqHTr661d8FiAS1Ott8badDnZkoH
You_Still_Here/Nothing_Here_1
You_Still_Here/Nothing_Here_10
You_Still_Here/Nothing_Here_11
You_Still_Here/Nothing_Here_12
You_Still_Here/Nothing_Here_13
You_Still_Here/Nothing_Here_14
...
```

It proved there's an archive hidden in this file but we can also see a link.

## Step 2
I downloaded the new file (`Only_Few_Steps.jpg`) and ran the same basic commands but no results.

I used `binwalk` on both files to see if anything is hidden.

```
 $ binwalk Hey_You.png 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 1144 x 1056, 8-bit/color RGBA, non-interlaced
91            0x5B            Zlib compressed data, compressed
868059        0xD3EDB         RAR archive data, version 5.x

$ binwalk Only_Few_Steps.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01
30            0x1E            TIFF image data, little-endian offset of first image directory: 8
426           0x1AA           Copyright string: "Copyright (c) 1998 Hewlett-Packard Company"
141318        0x22806         RAR archive data, version 5.x
```

So there's an archive in both files.
I extracted this data using `binwalk -e`.

## Step 3
### Hey You
In `_Hey_You.extracted` there's another archive called `D3EDB.rar`. I unrared it using `7z e D3EDB.rar`.

Then I used `ls -laR` to list everything recursively.

We don't see anything besides a `..txt` which contains a new link: `https://mega.nz/file/wZw2nAhS#i3Q0r-R8psiB8zwUrqHTr661d8FiAS1Ott8badDnZko`

This new link redirected me to the `Only_Few_Steps.jpg` image.

With nothing left in this archive, I tried the other one.

### Only Few Steps
In `_Only_Few_Steps.extracted` there's another archive called `22806.rar`. I unrared it using `7z e 22806.rar`.

But there's only an image called `YouWon(Almost).jpg` but it's totally empty.

The thing is, if you don't unrar this archive with `unrar`, the file will always be empty.

I opened it with my Windows machine and I had the file (non-empty this time).

<p align="center">
    <img src="YouWon_Almost.jpg">
</p>

## Step 4
Then I used the basic command on this image (same as before).

Using `strings YouWon(Almost).jpg` I had the following output:

```
...
.))i
KE&h
(4Q@
*Jc}
DSJ"]
CTF{VmtaU1IxUXhUbFZSYXpsV1RWUnNRMVpYZEZkYWJFWTJVVmhrVlZGVU1Eaz0=)
@9B:
XdYcY#`
Zs(u!
+R}*F>L
...
```

The CTF value 
`CTF{VmtaU1IxUXhUbFZSYXpsV1RWUnNRMVpYZEZkYWJFWTJVVmhrVlZGVU1Eaz0=)`
seems encoded in base64.

## Step 5
I decoded it by doing: 
```bash
$ echo "VmtaU1IxUXhUbFZSYXpsV1RWUnNRMVpYZEZkYWJFWTJVVmhrVlZGVU1Eaz0=" | base64 -d
VkZSR1QxTlVRazlWTVRsQ1ZXdFdabEY2UVhkVVFUMDk=
```

It was still encoded, so I decoded again.
```bash
$ echo "VkZSR1QxTlVRazlWTVRsQ1ZXdFdabEY2UVhkVVFUMDk=" | base64 -d
VFRGT1NUQk9VMTlCVWtWZlF6QXdUQT09
```
And again..

```bash
$ echo "VFRGT1NUQk9VMTlCVWtWZlF6QXdUQT09" | base64 -d
TTFOSTBOU19BUkVfQzAwTA==

$ echo "TTFOSTBOU19BUkVfQzAwTA==" | base64 -d
M1NI0NS_ARE_C00L
```
The flag is there!

## Solution
The flag is `CTF{M1NI0NS_ARE_C00L}`