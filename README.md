# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Answer: 
**I am starting this over and from a different approach**

$T(n) = 1, \text{ if } n \leq 1$
   
$T(n) = 3T\left(\frac{n}{3}\right) + n^5, \text{ when } n > 1$

**Expand the Recurrence and understand the pattern:**

$T(n) = 3T\left(\frac{n}{3}\right) + n^5$

$= 3\left(3T\left(\frac{n}{9}\right) + \left(\frac{n}{3}\right)^5\right) + n^5$

$= 9T\left(\frac{n}{9}\right) + 3\left(\frac{n^5}{3^5}\right) + n^5$

$= 9T\left(\frac{n}{9}\right) + \frac{n^5}{3^4} + n^5$

**Which will lead us to the substitution**

$= 3^i T\left(\frac{n}{3^i}\right) + \sum_{j=0}^{i-1} 3^j \left(\frac{n}{3^j}\right)^5$

_i_ represents the number of times we apply the recurrence. 

**Simplify the Summation Term:** 

$\sum_{j=0}^{i-1} \left(\frac{n^5}{3^4j}\right)$

This also can be simplfied to $ r = (\frac{1}{3^4})$

**Evaluate the Geometric Series:** 

The sum of the geometric series $\sum_{j=0}^{i-1} r^j$ where r < 1 is: 

$\sum_{j=0}^{i-1} (\frac{n^5}{3^4j}) = n^5 \sum_{j=0}^{i-1} (\frac{1}{3^4})^j = n^5 * (\frac{1 - (\frac{1}{3^4})^k)}{1 - (\frac{1}{3^4})}})$
Sources: 
I looked at Nolan Berg's raw repo for this so that I could write all the functions down. I did most of the work on my iPad and was having a hard time transferring it over to Git Hub. I also looked back at the slides in class to assist me with this. 

Plagiarism Statement: 
“I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.”






