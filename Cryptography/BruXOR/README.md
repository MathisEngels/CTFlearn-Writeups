# BruXOR
[Link to the challenge](https://ctflearn.com/challenge/227)

XOR and Brute.

## Step 1
We are given 2 hints and 1 value:

Hints :
- We need to use XOR.
- We need to brute force.

And the value is `q{vpln'bH_varHuebcrqxetrHOXEj`.

So I created a script to brute force XOR on this string.

## Step 2
The python script: 
```python
cipher = "q{vpln'bH_varHuebcrqxetrHOXEj"

for i in range(100):
    s = ""
    for char_i in range(len(cipher)):
        s += chr(ord(cipher[char_i]) ^ i)
    if s.lower().find("flag{") != -1:
        print("V=", i, "S=", s)
    s = ""
```
Gaves the flag.

## Solution
The flag is `flag{y0u_Have_bruteforce_XOR}`