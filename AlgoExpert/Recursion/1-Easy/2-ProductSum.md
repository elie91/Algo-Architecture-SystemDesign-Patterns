# Product Sum

<div class="html">
<p>
  Write a function that takes in a "special" array and returns its product sum.
</p>
<p>
  A "special" array is a non-empty array that contains either integers or other
  "special" arrays. The product sum of a "special" array is the sum of its
  elements, where "special" arrays inside it are summed themselves and then
  multiplied by their level of depth.
</p>
<p>
  The depth of a "special" array is how far nested it is. For instance, the
  depth of <span>[]</span> is <span>1</span>; the depth of the inner array in
  <span>[[]]</span> is <span>2</span>; the depth of the innermost array in
  <span>[[[]]]</span> is <span>3</span>.
</p>
<p>
  Therefore, the product sum of <span>[x, y]</span> is <span>x + y</span>; the
  product sum of <span>[x, [y, z]]</span> is <span>x + 2 * (y + z)</span>; the
  product sum of <span>[x, [y, [z]]]</span> is <span>x + 2 * (y + 3z)</span>.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [5, 2, [7, -1], 3, [6, [-13, 8], 4]]
</pre>
<h3>Sample Output</h3>
<pre>12 <span class="CodeEditor-promptComment">// calculated as: 5 + 2 + 2 * (7 - 1) + 3 + 2 * (6 + 3 * (-13 + 8) + 4)</span>
</pre>
</div>

<h2>Hints</h2>

<p>
Initialize the product sum of the "special" array to 0. Then, iterate through all of the array's elements; if you come across a number, add it to the product sum; if you come across another "special" array, recursively call the productSum function on it and add the returned value to the product sum. How will you handle multiplying the product sums at a given level of depth?
</p>
<p>
Have the productSum function take in a second parameter: the multiplier, initialized to 1. Whenever you recursively call the productSum function, pass in the multiplier incremented by 1.
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(d) space - where n is the total number of elements in the array, including sub-elements, and d is the greatest depth of "special" arrays in the array

```javascript
function productSum(array, depth = 1) {
 
  let sum = 0
  for (let i = 0; i < array.length; i++) {
    const element = array[i]
    if (!Array.isArray(element)) {
      sum += element
    } else {
      sum = sum += (productSum(element, depth + 1))    
    }
  }

  return sum * depth
}

// Do not edit the line below.
exports.productSum = productSum;

```