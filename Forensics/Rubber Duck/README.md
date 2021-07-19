# Rubber Duck
[Link to the challenge](https://ctflearn.com/challenge/933)

Data is hidden in the image.

## Step 1
We are given an image.
I downloaded it and view it. Nothing interesting so far.

Then, I tried to use some basic commands (`file`, `strings`/`hexdump -C` and `exiftool`).

When using `file RubberDuck.jpg` I got the following output:
```bash
RubberDuck.jpg: JPEG image data, JFIF standard 1.01, aspect ratio, density 72x72, segment length 16, comment: "CTFlearn{ILoveJakarta}", progressive, precision 8, 1536x2048, components 3
```

And `exiftool` gave me this result:
```bash
...
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 72
Y Resolution                    : 72
Comment                         : CTFlearn{ILoveJakarta}.
Profile CMM Type                : Apple Computer Inc.
Profile Version                 : 4.0.0
Profile Class                   : Display Device Profile
Color Space Data                : RGB
Profile Connection Space        : XYZ
Profile Date Time               : 2017:07:07 13:22:32
...
```

So the flag is clearly present.

## Solution
The flag is `CTFlearn{ILoveJakarta}`