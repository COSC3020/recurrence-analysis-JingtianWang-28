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

///


        for(var i = 0; i < n*n; i++) { //n^2
            for(var j = 0; j < n; j++) { // n
                for(var k = 0; k < n*n; k++) { // n^2
                    count = count + 1; // 1
        mystery(n / 3)mystery(n / 3)mystery(n / 3) // *3 and each time recursive the input size will be n to n/3

$total loop = n^2*n*n^2 =n^5 $

T(n) = runtime of function when input size n,there is three times recursive calls, each time is n/3

by def of master theorem, $T(n) = aT(n/b) + f(n)$

T(n) = $3 * T(n/3) + (n^5)$

T(n) = $O(n^5)$

///
substitution method
set $T(n) =< cn^5$
$T(n) = cn^5 +3/9(cn^5) +((3/9)^2)cn^5 + ((3/9)^3)cn^5  ....$
$T(n) = cn^5 (1+(3/9)+((3/9)^2)+((3/9)^3)...)$
$T(n) = 1+n+n^2+n^3...$
$T(n) = cn^5 (1/(1-3/9))$
$T(n) = 3/2(cn^5)$
3/2 is a constant may re write as $O(n^5)$

https://www.youtube.com/watch?v=zeVYepdQ9lY&ab_channel=GateSmashers
https://www.cs.cornell.edu/courses/cs3110/2008fa/lectures/lec19.html#:~:text=A%20shorter%20path%20to%20the%20goal%20is%20to,controlling%20performance.%20Derive%20a%20recurrence%20from%20the%20code.

Sources: chatgept provide me with ideas for proof methods. And complete the assignment through the examples and theorems on the above website.

Plagiarism Statement: “I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.”
