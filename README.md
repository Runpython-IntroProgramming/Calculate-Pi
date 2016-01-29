# Calculate &pi;

The purpose of this challenge is to practice using list comprehensions with input and output.

Write and submit a Python program that computes an approximate value of &pi; by calculating
the following sum:

![Pi Generator](http://www.texrendr.com/cgi-bin/mathtex.cgi?\%5Cpi%20%3D%204%20%5Cleft(1-%5Cfrac%7B1%7D%7B3%7D%2B%5Cfrac%7B1%7D%7B5%7D-%5Cfrac%7B1%7D%7B7%7D%20%2B%20%5Ccdots%20%20%2B%5Cfrac%7B(-1)%5En%7D%7B2n%2B1%7D%5Cright)%20%3D%204%20%5Csum_%7Bk%3D0%7D%5En%20%5Cfrac%7B(-1)%5Ek%7D%7B2k%2B1%7D)

<!-- $$\pi = 4 \left(1-\frac{1}{3}+\frac{1}{5}-\frac{1}{7} + \cdots  +\frac{(-1)^n}{2n+1}\right) = 4 \sum_{k=0}^n \frac{(-1)^k}{2k+1}$$ -->
            
This sum approaches the true value of &pi; as n approaches &infin;.

The big "E" thing in that equation means "add that thing to the right over and over again, but keep
changing the value of k. The first value of k is zero, the last value is n and k goes up by one each time."

Your program must ask the user how many terms to use in the estimate of &pi;, how many decimal
places, then print the estimate using that many decimal places. Exactly like this:


```
I will estimate pi. How many terms should I use? 100
How many decimal places should I use in the result? 7
The approximate value of pi is 3.1315929
```

## What the heck? How about an example to get me started?

While this task can be accomplished in only one line of Python code, you might use three or more to keep
the program readable. Brevity is important, but not most important! Because this task is challenging, 
I have an example of how you might implement a similar problem: computing an estimate for *Euler's
number*, *e*. 

One (admittedly silly) way to estimate *e* is to compute the **reciprocal** of the following:

![Reciprocal of e](http://www.texrendr.com/cgi-bin/mathtex.cgi?\p_n%20%3D%201-%5Cfrac%7B1%7D%7B1!%7D%2B%5Cfrac%7B1%7D%7B2!%7D-%5Cfrac%7B1%7D%7B3!%7D%2B%5Ccdots%2B%5Cfrac%7B(-1)%5En%7D%7Bn!%7D%20%3D%20%5Csum_%7Bk%20%3D%200%7D%5En%20%5Cfrac%7B(-1)%5Ek%7D%7Bk!%7D)

<!-- $$p_n = 1-\frac{1}{1!}+\frac{1}{2!}-\frac{1}{3!}+\cdots+\frac{(-1)^n}{n!} = \sum_{k = 0}^n \frac{(-1)^k}{k!}$$ -->

The true value of *e* begins with these digits (the true value is irrational and cannot be written with
a finite number of digits): 2.7182818284590452353602874...

A sample Python program for estimating the value of <em>e</em> might look like this:
```python 
import math
n = int(input("I will estimate e. How many terms should I use? "))
decimals = int(input("How many decimal places should I use in the result? "))
e = 1.0/sum([((-1.0)**k)/math.factorial(k) for k in range(0,n)])
print("The approximate value of e is {0}".format(round(e, decimals)))
print("(The true value of e is {0})".format(round(math.e, decimals)))
```

The line:

```python
e = 1.0/sum([((-1.0)**k)/math.factorial(k) for k in range(0,n)])
```

does all the work. Let's break it down.

1. ```((-1.0)**k)/math.factorial(k)``` computes the value of each element (*k*) in the series.
2. ```for k in range(0,n)``` generates *n* values of *k*.
3. ```[((-1.0)**k)/math.factorial(k) for k in range(0,n)]``` is a *list comprehension* that 
   generates a list of all *n* elements (numbers).
4. ```sum([((-1.0)**k)/math.factorial(k) for k in range(0,n)])``` takes the list of elements
   and computes the *sum* of them (this is the big "E" in the formula).
5. ```1.0/sum([((-1.0)**k)/math.factorial(k) for k in range(0,n)])``` takes the *reciprocal* of
   that sum!

### Decimal Places

Notice how the example code prints the results with a specific number of decimal places. Your code
will need to do something similar. Remember how to do this!

### Importing Libraries

One thing this example shows that you may still be unfamiliar with is ```import math```. 
The Python import statement is used to load another Python program file at the 
start of your program. In this case, ```math``` is a standard Python
library that contains a variety of common mathematical functions (we are using the factorial function
in the example).
Look at the code example and notice that ```factorial``` is prefaced with ```math.```.
Any time you load external libraries like this, you can refer to them using this style (there are other
ways of doing this, but this is the simplest). 

You can see all of the mathematical functions in <code class="prettyprint">math</code> by typing
```python
import math
```
in the Python console, then 
```python
dir(math)
```
to see all of the functions it contains.

