# Simple Programming
[Link to the challenge](https://ctflearn.com/challenge/174)

We need to make a script.

## Step 1
We are given a file with a bunch of lines containing 0's and 1's.

Let's make a quick python script to count how many lines there are when:
- The number of 0's (of the line) % 3 == 0
- The number of 1's (of the line) % 2 == 0

## Step 2
The script:
```python
file = open("data.dat")
count = 0

for line in file:
    if line.count("0") % 3 == 0 or line.count("1") % 2 == 0:
        count += 1
file.close()
print(count)
```
Gives the flag.

## Solution
The flag is `6662`