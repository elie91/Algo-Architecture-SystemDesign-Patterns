# Spiral Traverse

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
You can think of the spiral that you have to traverse as a set of rectangle perimeters that progressively get smaller (i.e., that progressively move inwards in the two-dimensional array).
</p>
<p>
Going off of Hint #1, declare four variables: a starting row, a starting column, an ending row, and an ending column. These four variables represent the bounds of the first rectangle perimeter in the spiral that you have to traverse. Traverse that perimeter using those bounds, and then move the bounds inwards. End your algorithm once the starting row passes the ending row or the starting column passes the ending column.
</p>
<p>

You can solve this problem both iteratively and recursively following very similar logic.
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(n) space - where n is the total number of elements in the array

```javascript
function spiralTraverse(array) {

  const result = [];

  let startRow = 0;
  let endRow = array.length - 1
  
  let startCol = 0;
  let endCol = array[0].length - 1;


  while (startRow <= endRow && startCol <= endCol) {
    for (let col = startCol; col <= endCol; col++) {
      result.push(array[startRow][col])
    }

    for (let row = startRow + 1; row <= endRow; row++) {
      result.push(array[row][endCol])
    }

    for (let col = endCol - 1; col >= startCol; col--) {
      // Handle the edge case when there's a single row
      // in the middle of the matrix. In this case, we don't
      // want to double-count the values in this row, which
      // we've already counted in the first for loop above.
      // See Test Case 8 for an example of this edge case.
      if (startRow === endRow) break;
      result.push(array[endRow][col])
    }

    for (let row = endRow - 1; row > startRow; row--) {
      // Handle the edge case when there's a single column
      // in the middle of the matrix. In this case, we don't
      // want to double-count the values in this column, which
      // we've already counted in the second for loop above.
      // See Test Case 9 for an example of this edge case.
      if (startCol === endCol) break;
      result.push(array[row][startCol])
    }

    startRow++;
    endRow--;
    startCol++;
    endCol--; 
  }
  
   return result
}

// Do not edit the line below.
exports.spiralTraverse = spiralTraverse;


```