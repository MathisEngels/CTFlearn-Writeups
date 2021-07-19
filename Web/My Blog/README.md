# My Blog
[Link to the challenge](https://ctflearn.com/challenge/979)

The description tells us to look at our memory or something in this field.

## Step 1
We are given the URL https://noxtal.com/.

When I went to the website, I concluded it was just a standard website/blog.

Going into the developer console, we can access what data are stored (under Application, on Chrome) on the browser.

If we look at the LocalStorage, we find an entry called `flag` which contains the flag!

## Solution
The flag is `CTFlearn{n7f_l0c4l_570r463_15n7_53cur3_570r463}`