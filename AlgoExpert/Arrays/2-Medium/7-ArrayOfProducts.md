# Array Of Products

<div class="html">
<p>
  Write a function that takes in a non-empty array of integers and returns an
  array of the same length, where each element in the output array is equal to
  the product of every other number in the input array.
</p>
<p>
  In other words, the value at <span>output[i]</span> is equal to the product of
  every number in the input array other than <span>input[i]</span>.
</p>
<p>Note that you're expected to solve this problem without using division.</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [5, 1, 4, 2]
</pre>
<h3>Sample Output</h3>
<pre>[8, 40, 10, 20]
<span class="CodeEditor-promptComment">// 8 is equal to 1 x 4 x 2</span>
<span class="CodeEditor-promptComment">// 40 is equal to 5 x 4 x 2</span>
<span class="CodeEditor-promptComment">// 10 is equal to 5 x 1 x 2</span>
<span class="CodeEditor-promptComment">// 20 is equal to 5 x 1 x 4</span>
</pre>
</div>

<h2>Hints</h2>

<p>
Think about the most naive approach to solving this problem. How can we do exactly what the problem wants us to do without focusing at all on time and space complexity?
</p>
<p>
Understand how output[i] is being calculated. How can we calculate the product of every element other than the one at the current index? Can we do this with just one loop through the input array, or do we have to do multiple loops?
</p>
<p>
For each index in the input array, try calculating the product of every element to the left and the product of every element to the right. You can do this with two loops through the array: one from left to right and one from right to left. How can these products help us?
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(n) space - where n is the length of the input array

```javascript
function arrayOfProducts(array) {
  const products = new Array(array.length).fill(1)

  let leftRunningProduct = 1;
  for (let i = 0; i < array.length; i++) {
    products[i] = leftRunningProduct
    leftRunningProduct *= array[i]
  }
  
  let rightRunningProduct = 1;
  for (let i = array.length - 1; i > -1; i--) {
    products[i] *= rightRunningProduct
    rightRunningProduct *= array[i]
  }

  return products
}

// Do not edit the line below.
exports.arrayOfProducts = arrayOfProducts;

```