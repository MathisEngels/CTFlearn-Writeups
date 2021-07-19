# Snowboard
[Link to the challenge](https://ctflearn.com/challenge/934)

Another jpeg with data hidden inside.

## Step 1
We are given an image.

I downloaded it and view it, nothing interesting.

Let's run some basic commands (`file`, `strings`/`hexdump -C` and `exiftool`)

When we look at the output of `file Snowboard.jpeg`:
```bash
Snowboard.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 300x300, segment length 16, comment: "CTFlearn{CTFIsEasy!!!}", comment: "Q1RGbGVhcm57U2tpQmFuZmZ9Cg==", Exif Standard: [TIFF image data, little-endian, direntries=8, manufacturer=Canon, model=Canon EOS 6D Mark II, xresolution=138, yresolution=146, resolutionunit=2, software=GIMP 2.10.6, datetime=2019:05:07 14:37:21], progressive, precision 8, 1200x800, components 3
```

I spotted 2 comments:
- `CTFlearn{CTFIsEasy!!!}` it's a fake flag.
- `Q1RGbGVhcm57U2tpQmFuZmZ9Cg==` looks like it's Base64 encoded.
  
## Step 2
I decoded `Q1RGbGVhcm57U2tpQmFuZmZ9Cg==` using CyberChef and I had this result: `CTFlearn{SkiBanff}`. It's the flag!


## Solution
The flag is `CTFlearn{SkiBanff}`