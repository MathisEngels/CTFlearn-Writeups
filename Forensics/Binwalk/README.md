# Binwalk
[Link to the challenge](https://ctflearn.com/challenge/108)

We need to extract the hidden files.

## Step 1
We are given a `.jpeg` file.

I used basic commands to get an idea of the file. (`file`, `strings`, `exiftool`). 

But the information is mainly classic.

## Step 2
I used `foremost -v` (an equivalent of `binwalk`) to extract any hidden file.

I got 2 PNGs. The bigger one is the Purple thing image, the original one. The second png is the hidden file:
<p align="center">
    <img src="00000299.png">
</p>

which is the flag.


## Solution
The flag is `ABCTF{b1nw4lk_is_us3ful}`