# PikesPeak
[Link to the challenge](https://ctflearn.com/challenge/935)

Data is hidden in the image.

## Step 1
We are given a jpg file.

I downloaded it and viewed it. Nothing interesting.

Then I used some basic commands (`file` and `strings`).

The output of `strings PikesPeak.jpg | grep CTFlearn` gave me the flag.

Note:
I could have used `grep -i ctf` and get the flag. Even if there's a lot of fake flags, the only one respecting the format is `CTFlearn{Gandalf}`

## Solution
The flag is `CTFlearn{Gandalf}`