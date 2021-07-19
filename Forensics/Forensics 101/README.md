# Forensics 101
[Link to the challenge](https://ctflearn.com/challenge/96)

The flag is somewhere in the picture.

## Step 1
We are given `95f6edfb66ef42d774a5a34581f19052.jpg`.

<p align="center">
  <img src="95f6edfb66ef42d774a5a34581f19052.jpg">
</p>

## Step 2
To get an idea of the given file, I used `file`:
```bash
95f6edfb66ef42d774a5a34581f19052.jpg: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, progressive, precision 8, 236x218, components 3
```
Nothing really interesting, let's continue.


## Step
Then I continue my routine by executing `strings` on the image.

At the end of the output, we have:
```
...
n%CeoQ=m8
`"n<P
 i}\D
8kF=
~9%]Tn
flag{wow!_data_is_cool}
$lqU
AG{u
Xm*CnC
@'hnQ
ax+p
bdQG
D_ O
```
We just found the flag.

## Solution
The flag is `flag{wow!_data_is_cool}`