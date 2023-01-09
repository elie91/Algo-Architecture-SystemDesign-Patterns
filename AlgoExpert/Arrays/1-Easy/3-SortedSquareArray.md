# Sorted Square Array

<div class="html">
<p>
  Write a function that takes in a non-empty array of integers that are sorted
  in ascending order and returns a new array of the same length with the squares
  of the original integers also sorted in ascending order.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [1, 2, 3, 5, 6, 8, 9]
</pre>
<h3>Sample Output</h3>
<pre>[1, 4, 9, 25, 36, 64, 81]
</pre>
</div>
<h2>Hints</h2>

  While the integers in the input array are sorted in increasing order, their
  squares won't necessarily be as well, because of the possible presence of
  negative numbers.


  Traverse the array value by value, square each value, and insert the squares
  into an output array. Then, sort the output array before returning it. Is this
  the optimal solution?

  To reduce the time complexity of the algorithm mentioned in Hint #2, you need
  to avoid sorting the ouput array. To do this, as you square the values of the
  input array, try to directly insert them into their correct position in the
  output array.


  Use two pointers to keep track of the smallest and largest values in the input
  array. Compare the absolute values of these smallest and largest values,
  square the larger absolute value, and place the square at the end of the
  output array, filling it up from right to left. Move the pointers accordingly,
  and repeat this process until the output array is filled.

  O(n) time | O(n) space - where n is the length of the input array

```javascript
// O(n log(n)) time because of the sorting at the end | O (n) space
function sortedSquaredArrayBad(array) {
  const sortedSquares = new Array(array.length).fill(0);

  for (let i = 0; i < array.length; i++) {
    const value = array[i];
    sortedSquares[i] = value * value;
  }
  sortedSquares.sort((a, b) => a - b);
  return sortedSquares;
}

// O(n) time | O(n) space
function sortedSquaredArray(array) {
  const sortedSquares = new Array(array.length).fill(0);
  let smallerValueIdx = 0;
  let largerValueIdx = array.length - 1;

  for (let i = array.length - 1; i >= 0; i--) {
    const smallerValue = array[smallerValueIdx];
    const largerValue = array[largerValueIdx];

    if (Math.abs(smallerValue) > Math.abs(largerValue)) {
      sortedSquares[i] = smallerValue * smallerValue;
      smallerValueIdx++
    } else {
      sortedSquares[i] = largerValue * largerValue;
      largerValueIdx--;
    }
  }
  return sortedSquares;
}
```