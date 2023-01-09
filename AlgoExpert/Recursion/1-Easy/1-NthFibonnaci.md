# Nth Fibonnaci

<div class="html">
<p>
  The Fibonacci sequence is defined as follows: the first number of the sequence
  is <span>0</span>, the second number is <span>1</span>, and the nth number is the sum of the (n - 1)th
  and (n - 2)th numbers. Write a function that takes in an integer
  <span>n</span> and returns the nth Fibonacci number.
</p>
<p>
  Important note: the Fibonacci sequence is often defined with its first two
  numbers as <span>F0 = 0</span> and <span>F1 = 1</span>. For the purpose of
  this question, the first Fibonacci number is <span>F0</span>; therefore,
  <span>getNthFib(1)</span> is equal to <span>F0</span>, <span>getNthFib(2)</span>
  is equal to <span>F1</span>, etc..
</p>
<h3>Sample Input #1</h3>
<pre><span class="CodeEditor-promptParameter">n</span> = 2
</pre>
<h3>Sample Output #1</h3>
<pre>1 <span class="CodeEditor-promptComment">// 0, 1</span>
</pre>
<h3>Sample Input #2</h3>
<pre><span class="CodeEditor-promptParameter">n</span> = 6
</pre>
<h3>Sample Output #2</h3>
<pre>5 <span class="CodeEditor-promptComment">// 0, 1, 1, 2, 3, 5</span>
</pre>
</div>

<h2>Hints</h2>

<p>
The formula to generate the nth Fibonacci number can be written as follows: F(n) = F(n - 1) + F(n - 2). Think of the case(s) for which this formula doesn't apply (the base case(s)) and try to implement a simple recursive algorithm to find the nth Fibonacci number with this formula.
</p>
<p>
What are the runtime implications of solving this problem as is described in Hint #1? Can you use memoization (caching) to improve the performance of your algorithm?
</p>
<p>
Realize that to calculate any single Fibonacci number you only need to have the two previous Fibonacci numbers. Knowing this, can you implement an iterative algorithm to solve this question, storing only the last two Fibonacci numbers at any given time?
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(1) space - where n is the input number

```javascript
// O(2^n) time | O(n) space
// O(2^n) time because we call the function 2 times for each iteration
// O(n) space because of the call stack, the functions stays in memory until the functions above returns value
// so we store in the call stack, n time functions
function getNthFib(n) {
  if (n === 2) {
    return 1
  }
  if (n === 1) {
    return 0
  }
  return getNthFib(n - 1) + getNthFib(n - 2)
}

// Do not edit the line below.
exports.getNthFib = getNthFib;

```
```javascript
// O(n) time | O(n) space
function getNthFib(n, memoize = {1: 0, 2: 1}) {
  if (n in memoize) {
    return memoize[n]
  } else {
    memoize[n] = getNthFib(n - 1, memoize) + getNthFib(n - 2, memoize)
    return memoize[n]
  }
}

// Do not edit the line below.
exports.getNthFib = getNthFib;

```

```javascript
// O(n) time | O(1) space
function getNthFib(n) {
  const lastTwo = [0, 1]
  let counter = 3
  while (counter <= n) {
    const nextFib = lastTwo[0] + lastTwo[1]
    lastTwo[0] = lastTwo[1]
    lastTwo[1] = nextFib
    counter++
  }
  return n > 1 ? lastTwo[1] : lastTwo[0]
}

// Do not edit the line below.
exports.getNthFib = getNthFib;

```