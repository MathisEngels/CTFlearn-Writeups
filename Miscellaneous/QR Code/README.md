# QR Code
[Link to the challenge](https://ctflearn.com/challenge/228)

Let's scan this QR Code.

## Step 1
We are given an image which is a QR Code. Let's scan it.

It returns the value `c3ludCB2ZiA6IGEwX29icWxfczBldHJnX2RlX3BicXI=`.

The value is ending by `=` which told me it was probably encoded in Base64.

## Step 2
Let's decode this using Base64 (using CyberChef) which gave me this:
`synt vf : a0_obql_s0etrg_de_pbqr`.

## Step 3
I guessed that `synt vf` was equal to `flag is`.
I found that there's a 13 number difference between the two.

- `s - 13 = f`
- `y - 13 = l`
- ...

## Step 4
It's known as ROT13, which is based on Caesar Cipher.

So I used this in CyberChef and got the flag.

## Solution
The flag is `n0_body_f0rget_qr_code`