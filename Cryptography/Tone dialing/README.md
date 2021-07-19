# Tone dialing
[Link to the challenge](https://ctflearn.com/challenge/889)

A wav file 🤔

## Step 1
We are given a file, a wav file. I downloaded it and used some basic commands (`file`, `strings`/`hexdump -C`, `exiftool` and `binwalk`).

Nothing so far. The flag is probably not hidden in the file but in the content. So I listened to it.

It sounds like an old phone when you click on the buttons.

## Step 2
I googled if a cipher using dial tone existed.

I came across the [Dual-tone multi-frequency signaling]("https://en.wikipedia.org/wiki/Dual-tone_multi-frequency_signaling"). It looked like it could be the answer.

After looking for a decoder. I found this [one]("http://dialabc.com/sound/detect/").

## Step 3
After decoding the wav file, I got this output:
`67847010810197110123678289808479718265807289125`.

It's just a serie of numbers.

When I saw this serie of numbers, I had multiple ideas to decode it:
- Base64 encoded?
- T9 encoded?
- Hex values?

## Step 4
It can't be Base64 encoded because this serie of numbers is only numbers and 47 characters long. This means it needs at one `=` as a padding character.

It can't be hex values because it's only a number, no alpha characters would be odds. So this serie of numbers must be only decimal.

I was heavily confident in T9 encoding. Using dcode.fr I tried to decode it but the output doesn't mean anything.

## Step 5
After trying all this, I tried to find a way to convert numbers to characters.

ASCII is obviously the solution!

Formatting the string gave me this:
`67 84 70 108 101 97 110 123 67 82 89 80 84 79 71 82 65 80 72 89 125`. Then I converted it and got the flag!

## Solution
The flag is `CTFlean{CRYPTOGRAPHY}`.