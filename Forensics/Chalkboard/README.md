# Chalkboard
[Link to the challenge](https://ctflearn.com/challenge/972)

There's an equation somewhere inside the picture. We must solve it (description).

## Step 1
We are given an image. I downloaded it and view it, nothing interesting.

Then I used some basic commands (`file`, `strings`, and `exiftool`).

`exiftool` gives an interesting output:
```
...
X Resolution                    : 1
Y Resolution                    : 1
Comment                         : The flag for this challenge is of the form:..CTFlearn{I_Like_Math_x_y}..where x and y are the solution to these equations:..3x + 5y = 31..7x + 9y = 59...
Image Width                     : 640
Image Height                    : 316
...
```

From this output, we know the format for the flag should be `CTFlearn{_Like_Math_x_y}` where `x` and `y` are the result of this equation:
```
3x + 5y = 31
7x + 9y = 59
```

## Step 2
Using [WolframAlpha](https://www.wolframalpha.com/) we can solve this equation really quickly.

I typed `3x + 5y = 31 ; 7x + 9y = 59` and got `x = 2` and `y = 5`.

And there is the flag!

## Solution
The flag is `CTFlearn{_Like_Math_2_5}`
