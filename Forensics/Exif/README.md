# Exif
[Link to the challenge](https://ctflearn.com/challenge/303)

## Step 1
We are given an image.
I downloaded it and use basic commands on it (`file`, `strings` and `exiftool`).

`file` and `strings` doesn't give much information but `exiftool` gives an interesting result.
Output:
```bash
...
Components Configuration        : Y, Cb, Cr, -
Flashpix Version                : 0100
Owner Name                      : flag{3l1t3_3x1f_4uth0r1ty_dud3br0}
GPS Latitude Ref                : South
GPS Longitude Ref               : East
Quality                         : 60%
DCT Encode Version              : 100
APP14 Flags 0                   : [14], Encoded with Blend=1 downsampling
APP14 Flags 1                   : (none)
Color Transform                 : YCbCr
...
```
And I got the flag!

## Solution
The flag is `flag{3l1t3_3x1f_4uth0r1ty_dud3br0}`