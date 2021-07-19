# Pho is Tasty!
[Link to the challenge](https://ctflearn.com/challenge/971)

The flag is hidden in the image!

## Step 1
We are given an image. I downloaded it and viewed it, nothing interesting.

Then I run some basics commands (`file`, `strings`/`hexdump -C` and `exiftool`).

`file`, `strings` and `exiftool` didn't give me much. But `hexdump -C` produced a good output:

```bash
00000030  38 20 43 6f 6c 6f 72 20  50 61 6c 65 74 74 65 3a  |8 Color Palette:|
00000040  1d 09 43 04 15 54 02 06  46 14 0d 6c 16 0e 65 06  |..C..T..F..l..e.|
00000050  19 61 17 1f 72 1b 18 6e  01 0c 7b 04 07 49 0f 03  |.a..r..n..{..I..|
00000060  5f 02 0e 4c 16 18 6f 1f  04 76 19 0c 65 1f 06 5f  |_..L..o..v..e.._|
00000070  18 01 50 11 10 68 13 14  6f 1a 02 21 04 02 21 13  |..P..h..o..!..!.|
00000080  14 21 0b 14 7d ff db 00  84 00 08 08 08 08 08 08  |.!..}...........|
00000090  09 0a 0a 09 0c 0d 0c 0d  0c 12 10 0f 0f 10 12 1b  |................|
000000a0  13 15 13 15 13 1b 29 19  1e 19 19 1e 19 29 24 2c  |......)......)$,|
```

When we look more closely, we can read the flag.

## Solution
The flag is `CTFlearn{I_Love_Pho!!!}`
