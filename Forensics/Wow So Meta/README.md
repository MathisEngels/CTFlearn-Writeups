# WOW.... So Meta
[Link to the challenge](https://ctflearn.com/challenge/348)

Let's find information inside the picture.

## Step 1
We are given an image. Let's download it and run basic commands (`file`, `strings`/`hexdump -C` and `exiftool`).

When running `exiftool`, I got the following output:
```bash
...
Creator Tool                    : Photos 1.5
Date Created                    : 2014:12:27 16:45:55
Warning                         : [minor] Fixed incorrect URI for xmlns:MicrosoftPhoto
Camera Serial Number            : flag{EEe_x_I_FFf}
Image Width                     : 800
Image Height                    : 307
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Date/Time Created               : 2014:12:27 16:45:55
Digital Creation Date/Time      : 2014:12:27 16:45:55
Image Size                      : 800x307
Megapixels                      : 0.246
```

The flag is in the `Camera Serial Number`.

## Solution
The flag is `flag{EEe_x_I_FFf}`