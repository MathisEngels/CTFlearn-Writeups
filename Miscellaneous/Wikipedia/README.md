# Wikipedia
[Link to the challenge](https://ctflearn.com/challenge/168)

We need to find the flag using an IP address and Wikipedia.

## Attention
Wikipedia EN is different from Wikipedia FR which means, if you search for the same user on Wikipedia EN and Wikipedia FR, it won't be the same.

As a French person, I went to fr.wikipedia.org and tried to find anything but it didn't work.

Use en.wikipedia.org.

## Step 1
We are given the following IP address: `128.125.52.138`.

I went to en.wikipedia.org and paste the IP address in the search bar.

We can find that a contribution has been made with this IP ([link](https://en.wikipedia.org/wiki/Special:Contributions/128.125.52.138)).

When we click on `diff`, we can see what changes the user made.

And I found the flag.

## Solution
The flag is `cNi76bV2IVERlh97hP`

