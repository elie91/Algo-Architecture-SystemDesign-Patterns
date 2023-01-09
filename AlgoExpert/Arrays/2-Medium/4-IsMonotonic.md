# Is Monotonic

<div class="html">
<p>
  Write a function that takes in an array of integers and returns a boolean
  representing whether the array is monotonic.
</p>
<p>
  An array is said to be monotonic if its elements, from left to right, are
  entirely non-increasing or entirely non-decreasing.
</p>
<p>
  Non-increasing elements aren't necessarily exclusively decreasing; they simply
  don't increase. Similarly, non-decreasing elements aren't necessarily
  exclusively increasing; they simply don't decrease.
</p>
<p>Note that empty arrays and arrays of one element are monotonic.</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [-1, -5, -10, -1100, -1100, -1101, -1102, -9001]
</pre>
<h3>Sample Output</h3>
<pre>true
</pre>
</div>
<h2>Hints</h2>

<p>
You can solve this question by iterating through the input array from left to right once.
</p>
<p>
Try iterating through the input array from left to right, in search of two adjacent integers that can indicate whether the array is trending upward or downward. Once you've found the tentative trend of the array, at each element thereafter, compare the element to the previous one; if this comparison breaks the previously identified trend, the array isn't monotonic.
</p>
<p>
Alternatively, you can start by assuming that the array is both entirely non-decreasing and entirely non-increasing. As you iterate through each element, perform a check to see if you can invalidate one or both of your assumptions.
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(1) space - where n is the length of the array

```javascript
function isMonotonic(array) {
  // Write your code here.
  if(array.length <= 2) {
    return true
  }

  let direction = array[1] - array[0];
  for (let i = 2; i < array.length; i++) {
    if (direction === 0) {
      direction = array[i] - array[i - 1];
      continue;
    }
    if (breaksDirection(direction, array[i - 1], array[i])) {
      return false
    }
  }
  return true
  
}

function breaksDirection(direction, previousInt, currentInt) {
  const difference = currentInt - previousInt
  if(direction > 0) {
    return difference < 0
  } 
  return difference > 0
}

```