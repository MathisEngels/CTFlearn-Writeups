# Git Is Good
[Link to the challenge](https://ctflearn.com/challenge/104)

Looks like we need to use Git.

## Step 1
We are given a zip archive.

I downloaded it and unzip it (using `unzip`).

## Step 2
I looked for what the archive contains using `ls -la`.

There's a `flag.txt` which just contains a fake flag. (`flag{REDACTED}`).

But I've seen a `.git` folder.

## Step 3
So I tried to use git cli. I'm not really familiar with git cli, just know it exists but only used a few times to change remote/branch/commit/push.

A quick `git help` helped me.

I first tried `git diff` but nothing appeared. So I tried `git show` and the flag appeared! The flag was a previous change.

## Solution
The flag is `flag{protect_your_git}`