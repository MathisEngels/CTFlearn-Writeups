# Tux!
[Link to the challenge](https://ctflearn.com/challenge/973)

We are told the flag is in the penguin!

## Step 1
We are given a file. I downloaded it and view it, nothing interesting.

Then I used some basic commands (`file`, `strings`/`hexdump -C` and `exiftool`).

`exiftool Tux.png` gave me an interesting comment:
`Comment                         : ICAgICAgUGFzc3dvcmQ6IExpbnV4MTIzNDUK.`

## Step 2
This comment could be encoded in Base64. So I tried to decode it:

```
$ echo 'ICAgICAgUGFzc3dvcmQ6IExpbnV4MTIzNDUK' | base64 -d
      Password: Linux12345
```

So we are given a password `Linux12345` but for what?

## Step 3
Then I had the idea to look for hidden files running `binwalk`.

```bash
pi@bootleg:~ $ binwalk Tux.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01
5488          0x1570          Zip archive data, encrypted at least v1.0 to extract, compressed size: 39, uncompressed size: 27, name: flag
5679          0x162F          End of Zip archive, footer length: 22
```

So there's a Zip archive. Let's extract it using
`binwalk -e Tux.jpg`.


## Step 4
I got 2 files out of this extraction:
- `flag`
- `1570.zip`

`flag` is just an empty file. So let's try to unzip `1570.zip`.

```bash
$ unzip 1570.zip
Archive:  1570.zip
[1570.zip] flag password: 
```

Looks like I have to use the password I got earlier (`Linux12345`)

After extracting this archive, it overrode the file `flag` (depending on your input) previously empty. 

When I `cat`ed the new `flag` file. The flag was there!

## Solution
The flag is `CTFlearn{Linux_Is_Awesome}`
