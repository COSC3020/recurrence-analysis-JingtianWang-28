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

When n <= 1, the function does not perform any operation and returns, and the time complexity is O(1)

        for(var i = 0; i < n*n; i++) { //n^2
            for(var j = 0; j < n; j++) { // n
                for(var k = 0; k < n*n; k++) { // n^2
                    count = count + 1; // 1
        mystery(n / 3)mystery(n / 3)mystery(n / 3) // *3 and each time recursive the input size will be n to n/3

$total loop = n^2*n*n^2 =n^5 operations $

T(n) represents the function running time when the input is n. T(n) ∈ O(1)

When n>1, the recursive relation consists of three mystery(n/3) calls and nested loops of O(n^5)

The recursive relation is $T(n) = $3T(n/3) + (n^5)$

Expand $T(n/3) = 3T(n/9)+((n/3)^5) = 3T(n/9)+(n^5/3^5)$

Substitute into the original formula $T(n) = 3(3T(n/9)+(n^5/3^5)+(n^5/3^5))$

$T(n) = 9T(n/9)+(n^5/3^4)+(n^5)$

Continue to expand $T(n/9) = 3T(n/27)+((n/9)^5) = 3T(n/27)+(n^5/9^5)$

Substituting into the original formula, $T(n) = 9(3T(n/27)+(n^5/9^5))+(n^5/3^4)+(n^5)$

$T(n) = 27T(n/27)+(n^5/9^4)+(n^5/3^4)+(n^5)$

= $3^i T(n/3^i)+ n^5 sig(i,k=0) (1/3^4(k-1) )$


#
At each level of recursion, the workload of the non-recursive part is O(n^5) and the number of recursive calls increases by three times each time. The recursion continues until n becomes small enough to reach the baseline case T(1) ∈ O(1)

After k expansions, the recursive relation is $ T(n) = 3^k(T)*(n/3^k)+(n^5(1+(1/3^5)+(1/9^5)+...))$

When the recursion ends, $n/3^k <= 1$, which gives $k=log_3(n)$, so at the bottom layer T(1) ∈ O(1)

The time complexity of the non-recursive part is a geometric series $O(n^5(1+(1/3^5)+(1/9^5)+...))$ and eventually converges to a constant. The workload of each layer is dominated by O(n^5). There are O(log n) layers of recursion, so the total time complexity is $T(n) ∈ O(n^5 log_n)$

$T(n) ∈ O(n^5)$


///

https://www.youtube.com/watch?v=zeVYepdQ9lY&ab_channel=GateSmashers
https://www.cs.cornell.edu/courses/cs3110/2008fa/lectures/lec19.html#:~:text=A%20shorter%20path%20to%20the%20goal%20is%20to,controlling%20performance.%20Derive%20a%20recurrence%20from%20the%20code.

Sources: chatgept provide me with ideas for proof methods. And complete the assignment through the examples and theorems on the above website.

Plagiarism Statement: “I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.”
