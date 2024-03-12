*Date: 2023-06-15 19:30* 
*Type:* #lecture 
*Class:* [[📌CS 311 MOC]] 

*Determining the speed of an Algorithm*

Algorithm analysis and [[Big-O]] are intrinsically connected.

## Worst Case Runtime

The **worst case** runtime of an algorithm is the function $T:N \to N$ defined as: $T(N):=$ Maximum number of primitive steps executed by the algorithm, on *any input* of size `n`.

Primitive Step:
- variable assignment: `x=10`
- arithmetic: `x+42`
- comparisons: `x>10`

Non-primitive Steps:
- Loops
- subroutines: `Math.pow(x,52)`, `object.foo()`

>What is the worst case runtime of the following code?
```java
for (int i=1; i<=n; i++){
	print("Hello") //constant time
}
```

Let c be the time taken by a single iteration of the loop.^[we use c because of our definition from [[Big-O]] makes it super easy to set up the equation $f(n)\leq c*g(n)$ ]

$$T(n) = \sum_{i=1}^{n} c = c*n \epsilon O(n)$$

A loop is literally the programming version of a summation above. We are doing a loop (summation) `n` times, and for each time we are doing `c` operations, which gives the $\sum_{i=1}^nc$ , once we simplify it we get $c*n$ which fits the definition of $c*g(n)$ which gives us that $T(n)=c*n\epsilon O(n)$ 

>What is the worst case runtime of the following code?
```java
for (int i=1; i<=n; i++){
	for (int j=1; j<=n; j++){
		print("hello!")
	}
}
```

Suppose the inner loop takes $c_{1}$ time per iteration. 
Suppose the outer loop takes $c_{2}$ time per iteration, excluding the inner loop.
$$
T(n)=\sum_{i=1}^n\left( c_{2}+ \sum_{j=1}^{n}c_{1} \right) =\sum_{i=1}^{n}(c_{2}+n*c_{1}) = c_{1}*n+c_{1}*n^2 \epsilon O(n^2)
$$
This follows the same explanation as above, because its just $c_{1}*n+c_{1}*n^2$ which is in the form of $c*g(n)$ so that is equal to $O(n^2)$.

>Slightly challenging more variation:
```java
for (int i=1; i<=n; i++){
	for (int j=1; j<=i; j++){ //depends on i
		print("hello!");
	}
}
```

Let $c_{1}$ and $c_{2}$ be the inner and outer loop respectively.

$$
T(n) = \underbrace{ \sum_{i=1}^n \left( c_{2}+\sum_{j=1}^ic_{1} \right) }_{ \text{The Loops} }  = \underbrace{ \sum_{i=1}^nc_{2}+\sum_{i=1}^n\sum_{j=1}^ic_{1} }_{ \text{distribute summation} } = \underbrace{ c_{2}*n + \sum_{i=1}^nc_{1}*i }_{ \text{simplify} } = c_{2}*n+c_{1}\underbrace{ \sum_{i=1}^ni }_{ \text{identity} } = \underbrace{ c_{2}*n+c_{1}\left( \frac{n(n+1)}{2} \right) }_{ f(n)\leq c*g(n) } \epsilon O(n^2)
$$

> What is the best & worst case runtime?
```java
myFunction(array A){
	if (A[0] == 0) return 0;
	int max = A[0];
	for (int i=0; i<n; i++) {
		if (max < A[i])
			max = A[i];
	}
	return max;
}
```

The best case is $O(1)$, no matter the input size, that first condition is just a *comparison*, which is a primitive step that executes in 1 step no matter the length of the array (`n`).

The worst case is $O(n)$, as we previously showed a loop that runs `n` times and does a constant number of primitive steps within the loop runs in $c*n$ which is $O(n)$. 

> What is the worst case runtime in terms of n?
```java
for (int i=n; i>=1; i/=2) { //starts at n and divides by 2
	print("Hello!");
}
```

| iteration | 1   | 2             | 3               | 4               | ... | k   |
| --------- | --- | ------------- | --------------- | --------------- | --- | --- |
| i         | n   | $\frac{n}{2}$ | $\frac{n}{2^2}$ | $\frac{n}{2^3}$ | ... | 1 = $\frac{n}{2^{k-1}}$    |

$$
1 = \frac{n}{2^{k-1}} \implies\underbrace{  2^{k-1} = n  }_{ \text{multipy by denominator} }\implies \underbrace{ k-1 = \log_{2}n }_{ \text{get rid of exponent} } \implies k=\log_{2}n
$$
$T(n) \epsilon O(\log n)$ , All $\log n$ is the same, the base does not matter.

Dividing something in half is the same as a binary search (in essance) which is therefore $\log_{2}n$, so think logs when seeing division.

> What is the worst case runtime of the following?
```java
public MyFunction2(array A){
	n = A.length;
	if (n < 5 || A[0]%2 == 0){
		for (int i=n; i>=1; i/=3){
			foo(A) //O(n^2)
		}
	}
	else {
		bar(A) //O(nlogn)
	}
}
```

the for loop is the same as the previous example where it is being divided by a number each iteration which points to $O(\log n)$, the base does not matter. The loop then performs a $O(n^2)$ operation, so it is $O(\log n) * O(n^2) = O(n^2\log n)$. So the problem now is $O(n^2\log n)$ or $O(n\log n)$ bigger? We can tell that a exponential is bigger with our eyes, so $O(n^2\log n)$ is bigger, but we might have to mathematically prove that with a definition in the future.

> Another loop within a loop example:
```java
i = 1;
while (i<=n) {
	for (int j=1; j<=i; j++) {
		print("Hello!")
	}
	i = 2*i;
}
```

We can represent the inner loop as follows:
$$
c_{2}+\sum_{j=1}^ic_{1} = c_{2}+c_{1}*i
$$

and now for figuring out how many times the outer loop will iterate:

| iteration | 1               | 2               | 3                 | 4                 | ... | k                           |
| --------- | --------------- | --------------- | ----------------- | ----------------- | --- | --------------------------- |
| operations         | $c_{2}+c_{1}*1$ | $c_{2}+c_{1}*2$ | $c_{2}+c_{1}*2^2$ | $c_{2}+c_{1}*2^3$ | ... | $c_{2}+c_{1}*2^{\log_{2}n}$ |

$$
\underbrace{ c_{2}*\log_{2}n }_{ \text{pull out all c2 terms} } + \underbrace{ c_{1}\sum_{j=0}^{\log_{2}n}2^j }_{ \text{geometric series} } = c_{2}*\log_{2}n + c_{1}(2n-1) \implies \underbrace{ c_{2}*\log_{2}n+c_{1}*2n-c_{1} }_{ c*g(n) \text{ where 2n > }\log_{2}n } \implies \epsilon O(n)
$$
