# Two Number Sum 

<div class="html">
<p>
  Write a function that takes in a non-empty array of distinct integers and an
  integer representing a target sum. If any two numbers in the input array sum
  up to the target sum, the function should return them in an array, in any
  order. If no two numbers sum up to the target sum, the function should return
  an empty array.
</p>
<p>
  Note that the target sum has to be obtained by summing two different integers
  in the array; you can't add a single integer to itself in order to obtain the
  target sum.
</p>
<p>
  You can assume that there will be at most one pair of numbers summing up to
  the target sum.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [3, 5, -4, 8, 11, 1, -1, 6]
<span class="CodeEditor-promptParameter">targetSum</span> = 10
</pre>
<h3>Sample Output</h3>
<pre>[-1, 11] <span class="CodeEditor-promptComment">// the numbers could be in reverse order</span>
</pre>
</div>

<h2>Hints</h2>

Try using two for loops to sum all possible pairs of numbers in the input array. What are the time and space implications of this approach?


Realize that for every number X in the input array, you are essentially trying to find a corresponding number Y such that X + Y = targetSum. With two variables in this equation known to you, it shouldn't be hard to solve for Y.


Try storing every number in a hash table, solving the equation mentioned in Hint #2 for every number, and checking if the Y that you find is stored in the hash table. What are the time and space implications of this approach?

O(n) time | O(n) space - where n is the length of the input array

```javascript
// O(n) time (Linear) | O(n) space (Linear)
function twoNumberSum(array, targetSum) {
  const nums = {};

  for (const num of array) {
    const diff = targetSum - num;
    if (diff in nums) {
      return [diff, num]
    } else {
      nums[num] = true;
    }
  }

  return [];
}

// O(n log(n)) time (Log-linear) | O(1) space (Constant)
function twoNumberSumWithoutHashMap(array, targetSum) {
  array.sort((a, b) => a - b);
  let left = 0;
  let right = array.length - 1;

  while (left < right) {
    const currentSum = array[left] + array[right];
    if (currentSum === targetSum) {
      return [array[left], array[right]]
    }
    if (currentSum < targetSum) {
      left++
    }
    if (currentSum > targetSum) {
      right++
    }
  }

  return [];
}

```