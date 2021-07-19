# GandalfTheWise
[Link to the challenge](https://ctflearn.com/challenge/936)

The flag is hidden inside the file.

# Step 1
We are given an image. I downloaded it and viewed it, nothing interesting.

Then I used basic commands (`file`, `strings`/`hexdump -C`, `exiftool`).

`file Gandalf.jpg` gave me this output:
```bash
Gandalf.jpg: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, comment: "Q1RGbGVhcm57eG9yX2lzX3lvdXJfZnJpZW5kfQo=", comment: "xD6kfO2UrE5SnLQ6WgESK4kvD/Y/rDJPXNU45k/p", comment: "h2riEIj13iAp29VUPmB+TadtZppdw3AuO7JRiDyU", baseline, precision 8, 225x225, components 3
```
which contains 3 interesting comments:
- `Q1RGbGVhcm57eG9yX2lzX3lvdXJfZnJpZW5kfQo=`
- `xD6kfO2UrE5SnLQ6WgESK4kvD/Y/rDJPXNU45k/p`
- `h2riEIj13iAp29VUPmB+TadtZppdw3AuO7JRiDyU`

## Step 2
The first flag is encoded in Base64 (spotted because it ends with `=` which are padding characters).

So let's decode it:
```bash
$ echo "Q1RGbGVhcm57eG9yX2lzX3lvdXJfZnJpZW5kfQo=" | base64 -d
CTFlearn{xor_is_your_friend}
```

This may be a hint: I need to use XOR to solve this CTF!

I might as well decode the 2 other comments, they might be base64 encoded as well!

```bash
$ echo "xD6kfO2UrE5SnLQ6WgESK4kvD/Y/rDJPXNU45k/p" | base64 -d
?>?|픬NR??:Z+?/???2O\?8?O?

$ echo "h2riEIj13iAp29VUPmB+TadtZppdw3AuO7JRiDyU" | base64 -d
?j???? )??T>`~M?mf?]?p.;?Q?<?
```

Even decoded, the 2 comments don't make sense.

## Step 3
But if I needed to use XOR, I needed to have data as hex or decimal. So, once again, I decoded the 2 comments from Base64 to Hex.

So I had:
- `xD6kfO2UrE5SnLQ6WgESK4kvD/Y/rDJPXNU45k/p => c4 3e a4 7c ed 94 ac 4e 52 9c b4 3a 5a 01 12 2b 89 2f 0f f6 3f ac 32 4f 5c d5 38 e6 4f e9`
- `h2riEIj13iAp29VUPmB+TadtZppdw3AuO7JRiDyU => 87 6a e2 10 88 f5 de 20 29 db d5 54 3e 60 7e 4d a7 6d 66 9a 5d c3 70 2e 3b b2 51 88 3c 94`

## Step 4
Now that I had those 2 hex values, I could XOR them using xor.pw and I had the following result: `43 54 46 6c 65 61 72 6e 7b 47 61 6e 64 61 6c 66 2e 42 69 6c 62 6f 42 61 67 67 69 6e 73 7d`.

## Step 5
Using CyberChef, I converted this hex value to ASCII and got the flag!

## Solution
The flag is `CTFlearn{Gandalf.BilboBaggins}`