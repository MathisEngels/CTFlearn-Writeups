# The Credit Card Fraudster
[Link to the challenge](https://ctflearn.com/challenge/970)

We need to write a script!

## Step 1
In the description we are given multiple pieces of information:
- The card number is a multiple of 123457.
- The card number has a valid Luhn Check digit
- The card number looks like `543210******1234`

We need to find the right card number.

So I made my own small python script.

## Step 2
The script (I didn't implement Luhn Check):
```python
card_num = 5432100000001234

for i in range(999999):
    temp = card_num + (10000 * i)
    if (temp % 123457 == 0):
        print(temp)
```
The output:
```bash
5432100810111234
5432102044681234
5432103279251234
5432104513821234
5432105748391234
5432106982961234
5432108217531234
5432109452101234
```

Now that I had 8 possible answers, I tried and found the right one, so I found the flag.

## Solution
The flag is `CTFlearn{5432103279251234}`