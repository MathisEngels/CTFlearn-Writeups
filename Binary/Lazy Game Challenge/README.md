# Lazy Game Challenge
[Link to the challenge](https://ctflearn.com/challenge/691)

This one was tricky. I had to see the comments.

## Step 1
I connected to the server using netcat: `nc thekidofarcrania.com 10001`.

When you connect, rules are displayed:
- You'll be given $500
- Place a Bet
- Guess the number, the computer thinks of!
- Computer's number changes every new time!
- You have to guess a number between 1-10
- You have only 10 tries !
- If you guess a number > 10, it still counts as a try!
- If you guess within the number of tries, you win money!

So what can we guess from those rules?
We'll win our bet if we get the right number. We only have 10 tries. The number above 10 also counts as a try and you have to guess within the 10 tries.

So I tried to break the rules.

## Step 2
So I placed a simple bet of $500 to see what happened and tried different numbers (-15, -5, 5, 15). Negative numbers still count as try, and >15 too.
When trying `5`, I actually won the jackpot and see how the winning part worked: my balance went from $500 to $1500 so my previous balance ($500) + 2 * mybet($500).

Let's try the losing part now.
I placed, once again, a bet of $500 and spammed >15 numbers until I was out of tries.
My balance went from $500 to $0 so my previous balance ($500) - mybet ($500).

I had the idea to try not a number but string for instance to do some injection but it didn't work, the input was sanitized and if it wasn't a number, it would say you try the number 0.

So, if I can't do anything with the guessing number input. What other input could I try to win this CTF?

## Step 3
When you connect to the server, it asked you if you are ready, a Y/N is excepted.

Once again, after trying to inject some code, I couldn't do anything (Maybe I just don't know enough and there's an exploit to be found!)

The last input possible is the bet amount one. So I tried to inject code but once again, it didn't work. 
The last idea I had in mind is: negative value for the betting amount.

So I placed -$500 and spammed negative guessing value.

After losing, my balance was $1000. So the server calculates the new balance for a loose game by doing: `new balance = previous balance - bet` but `- - = +`.

So now, I needed to see if I could bet more than I owned. 

Turns out it's possible. You can't bet more than you owned but `-$100 < $500`. So you can bet -$10000 without any problem.

## Step 4
I placed -$1000000000000 and spammed negative guessing value, again.

It worked and in the end, I had the flag!

## Solution
The flag is `CTFlearn{d9029a08c55b936cbc9a30_i_wish_real_betting_games_were_like_this!}`
