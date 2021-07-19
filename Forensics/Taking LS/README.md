# Taking LS
[Link to the challenge](https://ctflearn.com/challenge/103)

The flag is somewhere in the zip file.

## Step 1
We are given a `The flag.zip` archive.

I've run basic commands like `file`, `strings` and `exiftool`.

`exiftool` and `file` don't give me much besides knowing the file is not empty/corrupted and I need at least v1 to extract it.

`strings` (or `hexdump -C`) give me more information about files inside the archive.

```bash
...
dbcc
__MACOSX/The Flag/._The Flag.pdfUX
cg`b`
bI4%
The Flag/UX
The Flag/.DS_StoreUX
__MACOSX/UX
__MACOSX/The Flag/UX
__MACOSX/The Flag/._.DS_StoreUX
The Flag/.ThePassword/UX
<M^I2
The Flag/.ThePassword/ThePassword.txtUX
M^Ii
The Flag/The Flag.pdfUX
```
Apprently there's a `.ThePassword` folder.

## Step 2

I unzipped the file (with `unzip`) and got 2 folders:
- __MACOSX (Default folder created for MacOS user, so we don't care)
- TheFlag (interesting!)

## Step 3
I'm now under `TheFlag/`. I used `ls -laR` to list everything inside the folder (including hidden files).
`l` is used to get more information about the file/folder listed.
`a` is to list ALL the file (even the hidden one (with they start with .)).
`R` is used to list recursively.

And I got the following output:
```bash
$ ls -laR
.:
total 40
drwxr-xr-x 3 pi pi  4096 oct.  30  2016  .
drwxr-xr-x 9 pi pi  4096 juil. 15 16:59  ..
-rw-r--r-- 1 pi pi  6148 oct.  30  2016  .DS_Store
-rw-r--r-- 1 pi pi 16647 oct.  30  2016 'The Flag.pdf'
drwxr-xr-x 2 pi pi  4096 oct.  30  2016  .ThePassword

./.ThePassword:
total 12
drwxr-xr-x 2 pi pi 4096 oct.  30  2016 .
drwxr-xr-x 3 pi pi 4096 oct.  30  2016 ..
-rw-r--r-- 1 pi pi   42 oct.  30  2016 ThePassword.txt
```

## Step 4

So there's a PDF file (`The Flag.pdf`). The PDF needs a password to be opened.

There's also a txt file (`ThePassword.txt` under `.ThePassword`).

I `cat`ed this file, to see what's inside:
```bash
Nice Job!  The Password is "Im The Flag".
```

Now that I had the password, I could open the PDF.

## Step 5
After entering the password, I get the flag.

## Solution
The flag is `ABCTF{T3Rm1n4l_is_C00l}`