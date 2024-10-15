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
Let's go down the code and list everything we see. 

if $n \leq 1$ 

$3T(\frac{n}{3}) + n^5$ else 

To find the complexity, we need to isolate it more. 

_T_(n) = $3T(\frac{n}{3}) + n^5$

= 3(3T(\frac{\frac{n}{3}}{3}) + (\frac{n}{3})^5) + n^5$

= 9T(\frac{n}{3}) + \frac{3n^5}{3^5} + n^5$

Can remove $`n^5`$ so it is easier. 

= 9T(\frac{n}{3}) + \frac{3}{3^5} \cdot n^5 + n^5$

With this being shortened we can determine a sum 

= 3^iT(\frac{n}{3^i}) + \displaystyle\sum_{j=0}^{i-1}\frac{3^j}{(3^j)^5} \cdot n^5$ 




