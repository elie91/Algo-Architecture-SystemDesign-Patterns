# Four Number Sum

<div class="html">
<p>
  Write a function that takes in a non-empty array of distinct integers and an
  integer representing a target sum. The function should find all quadruplets in
  the array that sum up to the target sum and return a two-dimensional array of
  all these quadruplets in no particular order.
</p>
<p>
  If no four numbers sum up to the target sum, the function should return an
  empty array.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [7, 6, 4, -1, 1, 2]
<span class="CodeEditor-promptParameter">targetSum</span> = 16
</pre>
<h3>Sample Output</h3>
<pre>[[7, 6, 4, -1], [7, 6, 1, 2]] <span class="CodeEditor-promptComment">// the quadruplets could be ordered differently</span>
</pre>
</div>

<h2>Hints</h2>

<p>
Using four for loops to calculate the sums of all possible quadruplets in the array would generate an algorithm that runs in O(n^4) time, where n is the length of the input array. Can you come up with something faster using fewer for loops?
</p>
<p>
You can calculate the sums of every pair of numbers in the array in O(n^2) time using just two for loops. Then, assuming that you've stored all of these sums in a hash table, you can fairly easily find which two sums can be paired to add up to the target sum: the numbers summing up to these two sums constitute candidates for valid quadruplets; you just have to make sure that no number was used to generate both of the two sums.
</p>
<p>
You can do everything described in Hint #2 with just two sibling for loops nested inside a third for loop. Your goal is to create a hash table mapping the sums of every pair of numbers in the array to an array of arrays, with each subarray representing the indices of each pair summing up to that number. Loop through the input array with a simple for loop. Inside this loop, loop through the input array again, starting at the index of the first loop. At each iteration, calculate the difference between the target sum and the sum of the two numbers represented by the indices of the for loops. If that difference is in the hash table that you're building, then valid quadruplets can be formed by combining the current pair of numbers with each pair stored in the hash table at the difference just calculated. Following this nested for loop, loop through the array again, this time starting at index zero all the way to the index of the first for loop. At each iteration, calculate the sum of the two numbers represented by the indices of the for loops and add it to the hash table if it isn't already there; then add the pair of indices to the array that the sum in the hash table maps to.
</p>
<h2>Optimal Space & Time Complexity</h2>

<div class="U1quNvMraAr3Hbq2JfVQ">Average: O(n^2) time | O(n^2) space - where n is the length of the input array
Worst: O(n^3) time | O(n^2) space - where n is the length of the input array</div>

```javascript
function hasZeroSumSubarray(nums) {
  const sumMap = new Map();
  let sum = 0;

  for (let i = 0; i < nums.length; i++) {
    sum += nums[i];
    if (sum === 0 || sumMap.has(sum)) {
      return true;
    }
    sumMap.set(sum, i);
  }

  return false;
}

```
<img src='../../images/zeroSumSubarray.png' />