# Simple Stenography
[Link to the challenge](https://ctflearn.com/challenge/894)

We should use Steghide.

## Step 1
We are given an image. I downloaded it and viewed it, nothing interesting.

Then I used some basic commands (`file`, `strings`/`hexdump -C` and `exiftool`).

When I used `strings` or `exiftool`. I got a keyword: `myadmin`. Besides this, nothing else.

## Step 2
I tried to see if this file was hiding anything else.
`binwalk` didn't notice anything. So I tried `steghide`.

## Step 3
When using steghide, I needed to input a passphrase. I first tried with no passphrase but `steghide` couldn't find anything.

So I remembered `myadmin` I just found using `exiftool` and used it as the passphrase.

```bash
$ steghide info Minions1.jpg
Try to obtain hidden data ? (y/n) y
Enter passphrase: 
  file ? include "raw.txt":
    size: 58,0 Byte
    crypt: rijndael-128, cbc
    compression: yes 
```

So there's a file called `raw.txt` hidden in this file.

## Step 4
I decided to extract this file.
`steghide extract -sf Minions1.jpeg`

The `raw.txt` file now extracted, I `cat`ed it.
This is what `raw.txt` contained:
`AEMAVABGAGwAZQBhAHIAbgB7AHQAaABpAHMAXwBpAHMAXwBmAHUAbgB9`.

## Step 5
This string (the one in `raw.txt`) could be encoded in Base64. So I tried to decode it: `cat raw.txt | base64 -d`. And I got the flag!

## Solution
The flag is `CTFlearn{this_is_fun}`
