# I'm a dump
[Link to the challenge](https://ctflearn.com/challenge/883)

Looks like we'll need to use strings/hexdump.

## Step 1
We are given a file, I downloaded it and use `strings file | grep -i CTF` and got an output: `CTFlearnH`. It looks like the flag can be found using `strings file`.

After typing `strings file` and searching where the `CTFLearnH` is, I got this:

```
...
_ITM_registerTMCloneTable
u3UH
CTFlearnH
{fl4ggyfH
l4g}H
[]A\A]A^A_
;*3$"
GCC: (Arch Linux 9.3.0-1) 9.3.0
init.c
...
```
Those lines are interesting:
- `CTFlearnH`
- `{fl4ggyfH`
- `l4g}H`

In the description of this CTF, we are told that the format must be `CTFLearn{*}`
With a small format, I got the flag.

## Solution
The flag is `CTFlearn{fl4ggyl4g}`