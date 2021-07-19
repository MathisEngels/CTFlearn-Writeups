# Where Can My Robot Go?
[Link to the challenge](https://ctflearn.com/challenge/107)

We need to find where robots are allowed on the website.

## Step 1
All websites have to tell which path the robots can go and they use `robots.txt` at the root of the website.
In our case, the file is located at `https://ctflearn.com/robots.txt`.

When we access this URL, we get:
```
User-agent: *
Disallow: /70r3hnanldfspufdsoifnlds.html
```

## Step 2
The disallowed path seems weird so I wanted to see what's over there.

And we get the flag.

## Solution
The flag is `CTFlearn{r0b0ts_4r3_th3_futur3}`