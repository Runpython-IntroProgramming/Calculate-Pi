# Calculate &pi;

The purpose of this challenge is to practice using list comprehensions with input and output.

Write and submit a Python program that computes an approximate value of &pi; by calculating
the following sum:

![Pi Generator](http://www.texrendr.com/cgi-bin/mathtex.cgi?\%5Cpi%20%3D%204%20%5Cleft(1-%5Cfrac%7B1%7D%7B3%7D%2B%5Cfrac%7B1%7D%7B5%7D-%5Cfrac%7B1%7D%7B7%7D%20%2B%20%5Ccdots%20%20%2B%5Cfrac%7B(-1)%5En%7D%7B2n%2B1%7D%5Cright)%20%3D%204%20%5Csum_%7Bk%3D0%7D%5En%20%5Cfrac%7B(-1)%5Ek%7D%7B2k%2B1%7D)

            $$\pi = 4 \left(1-\frac{1}{3}+\frac{1}{5}-\frac{1}{7} + \cdots  +\frac{(-1)^n}{2n+1}\right) = 4 \sum_{k=0}^n \frac{(-1)^k}{2k+1}$$
            
This sum approaches the true value of \(\pi\) as n approaches \(\infty\).

The big "E" thing in that equation means "add that thing to the right over and over again, but keep
changing the value of k. The first value of k is zero, the last value is n and k goes up by one each time."

Your program must ask the user how many terms to use in the estimate of \(\pi\), then print the estimate
using six significant figures. For example:


        <pre><code>I will estimate pi. How many terms should I use? 100
How many sig figs should I use in the result? 8
The approximate value of pi is 3.1315929</code></pre>
        <h3>What the heck? How about an example to get me started?</h3>
        <p>
            While this task can be accomplished in only one line of Python code, you might use three or more to keep
            the program readable. Brevity is important, but not most important! Because this task is challenging, 
            I have an example of how you might implement a similar problem: computing an estimate for <em>Euler's
            number</em>, <em>e</em>. 
        </p>
        <p>
            One way to estimate <em>e</em> is to compute the reciprocal of the following:
        </p>

            $$p_n = 1-\frac{1}{1!}+\frac{1}{2!}-\frac{1}{3!}+\cdots+\frac{(-1)^n}{n!} = \sum_{k = 0}^n \frac{(-1)^k}{k!}$$

        <p>
            The true value of <em>e</em> begins with these digits (the true value is irrational and cannot be written with
            a finite number of digits): 2.7182818284590452353602874...
        </p>
        <p>
            A sample Python program for estimating the value of <em>e</em> might look like this:
        </p>
        <pre class="prettyprint lang-py">import math
n = int(input("I will estimate e. How many terms should I use? "))
sigfigs = int(input("How many sig figs should I use in the result? "))
e = 1.0/sum([((-1.0)**k)/math.factorial(k) for k in range(0,n)])
print("The approximate value of e is {0:.{precision}}".format(e, precision=sigfigs))
print("(The true value of e is {0:.{precision}})".format(math.e, precision=sigfigs))</pre>
        <p>
            One thing this example shows that you might be unfamiliar is the <code class="prettyprint">
            import math</code>. The Python import statement is used to load another Python program file at the 
            start of your program. In this case, <code class="prettyprint">math</code> is a standard Python
            library that contains a variety of common mathematical functions (we are using the factorial function).
            Look at the code example and notice that the name is prefaced with <code class="prettyprint">math.</code>
            Any time you load external libraries like this, you can refer to them using this style (there are other
            ways of doing this, but this is the simplest). 
        </p>
        <p>
            You can see all of the mathematical functions in <code class="prettyprint">math</code> by typing
            <code class="prettyprint">import math</code> in the Python console, then <code class="prettyprint">dir(math)</code>
            to see all of the functions it contains.
        </p>
        
