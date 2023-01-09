# Validate Subsequences

<div class="html">
<p>
  Given two non-empty arrays of integers, write a function that determines
  whether the second array is a subsequence of the first one.
</p>
<p>
  A subsequence of an array is a set of numbers that aren't necessarily adjacent
  in the array but that are in the same order as they appear in the array. For
  instance, the numbers <span>[1, 3, 4]</span> form a subsequence of the array
  <span>[1, 2, 3, 4]</span>, and so do the numbers <span>[2, 4]</span>. Note
  that a single number in an array and the array itself are both valid
  subsequences of the array.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [5, 1, 22, 25, 6, -1, 8, 10]
<span class="CodeEditor-promptParameter">sequence</span> = [1, 6, -1, 10]
</pre>
<h3>Sample Output</h3>
<pre>true
</pre>
</div>

<h2>Hints</h2>

You can solve this question by iterating through the main input array once.


Iterate through the main array, and look for the first integer in the potential subsequence. If you find that integer, keep on iterating through the main array, but now look for the second integer in the potential subsequence. Continue this process until you either find every integer in the potential subsequence or you reach the end of the main array.


To actually implement what Hint #2 describes, you'll have to declare a variable holding your position in the potential subsequence. At first, this position will be the 0th index in the sequence; as you find the sequence's integers in the main array, you'll increment the position variable until you reach the end of the sequence.

O(n) time | O(1) space - where n is the length of the array

```javascript
// My solution
function isValidSubsequence(array, sequence) {
  let pointer = 0;
  for (let i = 0; i < array.length; i++) {
    if (array[i] === sequence[pointer]) {
      pointer += 1
    }
    if (pointer === sequence.length) {
      return true;
    }
  }
  return false;
}

// AlgoExpert solution
function isValidSubsequence2(array, sequence) {
  let arrIndex = 0;
  let seqIndex = 0;

  while (arrIndex < array.length && seqIndex < sequence.length) {
    if (array[arrIndex] === sequence[seqIndex]) {
      seqIndex++
    }
    arrIndex++
  }
  return seqIndex === sequence.length;
}
```

