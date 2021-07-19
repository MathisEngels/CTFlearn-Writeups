# Modern Gaius Julius Caesar
[Link to the challenge](https://ctflearn.com/challenge/885)

A Caesar cipher?

## Step 1
We are given a string `BUH'tdy,|Bim5y~Bdt76yQ` and told from the description that we now have a keyboard, etc.

This one is tricky for non-American players.

We can guess that `BUH` is equal to `CTF`.
Let's try to find any link.

After a while, trying a lot of different methods, and reading the comment section, I found out that it's a Caesar cipher of 2 using an American keyboard.

I needed to shift each character to the right by 2 and I got the flag!

## Solution
The flag is `CTFlearn{Cyb3r_Cae54r}`