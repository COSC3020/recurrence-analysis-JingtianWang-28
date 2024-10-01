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
total loop = n^5 = $O(n^5)$
T(n) = $3 * T(n/3) + 1 * n^5 * log(n)$
T(n) = $log(n^5)$
