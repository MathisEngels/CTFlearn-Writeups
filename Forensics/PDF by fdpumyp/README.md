# PDF by fdpumyp
[Link to the challenge](https://ctflearn.com/challenge/957)

Let's find data inside a PDF.

## Step 1
We are given a PDF file. I downloaded it and viewed it, nothing interesting.

Then I used some basic commands (`file`, `strings`/`hexdump -C` and `exiftool`).

When I used `strings dontopen.pdf` I got an interesting output:
```
...
<</Length 138/DL 138/Params<</Size 138>>>>
stream
== SECRET DATA DONT LOOK AT THIS ==
external:Q1RGbGVhcm57KV8xbDB3M3kwVW0wMG15MTIzfQ==
pin:1234
password:MTIzMVdST05HOWlzamRuUEFTU1dPUkQ=
endstream
endobj
...
```

Looks like I found 3 strings:
- `external = Q1RGbGVhcm57KV8xbDB3M3kwVW0wMG15MTIzfQ==`
- `pin = 1234`
- `password = MTIzMVdST05HOWlzamRuUEFTU1dPUkQ=`

## Step 2
`external` and `password` ends with `=` which told me they are base64 encoded.

After decoded them, I got: (using `base64 -d`)
- `external = CTFlearn{)_1l0w3y0Um00my123}`
- `password = 1231WRONG9isjdnPASSWORD`

The flag was found!

## Solution
The flag is `CTFlearn{)_1l0w3y0Um00my123}`