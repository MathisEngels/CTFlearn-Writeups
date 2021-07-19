# Suspecious message
[Link to the challenge](https://ctflearn.com/challenge/887)

Encryption using a matrix of letters?

## Step 1
We are given a string: `MQDzqdor{Ix4Oa41W_1F_B00h_m1YlqPpPP}` and an image.

The image is a matrix of letters.

<p align="center">
    <img src="photo.png">
</p>

I didn't know anything using some of this. I tried to run commands (`file`, `strings`, `hexdump -C`, `exiftool`, `binwalk`, `foremost`) on the file but nothing came out.

## Step 2
So I tried to Google for a cipher using a matrix of letters.

After looking for `cipher using 5 by 5 letters`. I found out a cipher called `Polybius square`.

Using [dcode.fr]("https://www.dcode.fr/polybius-cipher") a french decoding website. I was able to get the flag!

## Solution
The flag is `CTFLEARN{PL4YF41R_1S_C00L_C1PHERRRR}`