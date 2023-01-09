# First Duplicate Value

<div class="html">
<p>
  Given an array of integers between <span>1</span> and <span>n</span>,
  inclusive, where <span>n</span> is the length of the array, write a function
  that returns the first integer that appears more than once (when the array is
  read from left to right).
</p>
<p>
  In other words, out of all the integers that might occur more than once in the
  input array, your function should return the one whose first duplicate value
  has the minimum index.
</p>
<p>
  If no integer appears more than once, your function should return
  <span>-1</span>.
</p>
<p>Note that you're allowed to mutate the input array.</p>
<h3>Sample Input #1</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [2, 1, 5, 2, 3, 3, 4]
</pre>
<h3>Sample Output #1</h3>
<pre>2 <span class="CodeEditor-promptComment">// 2 is the first integer that appears more than once.</span>
<span class="CodeEditor-promptComment">// 3 also appears more than once, but the second 3 appears after the second 2.</span>
</pre>
<h3>Sample Input #2</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [2, 1, 5, 3, 3, 2, 4]
</pre>
<h3>Sample Output #2</h3>
<pre>3 <span class="CodeEditor-promptComment">// 3 is the first integer that appears more than once.</span>
<span class="CodeEditor-promptComment">// 2 also appears more than once, but the second 2 appears after the second 3.</span>
</pre>
</div>

<h2>Hints</h2>

<p>
The brute-force solution can be done in O(n^2) time. Think about how you can determine if a value appears twice in an array.
</p>
<p>
You can use a data structure that has constant-time lookups to keep track of integers that you've seen already. This leads the way to a linear-time solution.
</p>
<p>
You should always pay close attention to the details of a question's prompt. In this question, the integers in the array are between 1 and n, inclusive, where n is the length of the input array. The prompt also explicitly allows us to mutate the array. How can these details help us find a better solution, either time-complexity-wise or space-complexity-wise? 
</p>
<p>
Since the integers are between 1 and the length of the input array, you can map them to indices in the array itself by subtracting 1 from them. Once you've mapped an integer to an index in the array, you can mutate the value in the array at that index and make it negative (by multiplying it by -1). Since the integers normally aren't negative, the first time that you encounter a negative value at the index that an integer maps to, you'll know that you'll have already seen that integer.
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(1) space - where n is the length of the input array

```javascript
// O(n^2) time | O(1) space
function firstDuplicateValue(array) {

  let minIndexDuplicate = array.length;

  for (let i = 0; i < array.length; i++) {
    const value = array[i]
    for (let j = i + 1; j < array.length; j++) {
      const valueToCompare = array[j]
      if (value === valueToCompare) {
        minIndexDuplicate = Math.min(minIndexDuplicate, j)
      }
    }
  }

  if (minIndexDuplicate === array.length) {
    return -1
  }
  return array[minIndexDuplicate]
} 

```
```javascript
// O(n) time | O(n) space
function firstDuplicateValue(array) {

  const numsVisited = new Set();

  for (let i = 0; i < array.length; i++) {
    const value = array[i]
    if (numsVisited.has(value)) {
      return value
    }
    numsVisited.add(value)
  }
  
  return -1
}

```

```javascript
// O(n) time | O(1) space
function firstDuplicateValue(array) {
  for (const value of array) {
    const absValue = Math.abs(value);
    if (array[absValue - 1] < 0) {
      return absValue
    }
    array[absValue - 1] *= -1
  }
  return -1
}

```