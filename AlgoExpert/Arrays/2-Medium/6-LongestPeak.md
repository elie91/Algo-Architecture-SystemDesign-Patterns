# Longest Peak

<div class="html">
<p>
  Write a function that takes in an array of integers and returns the length of
  the longest peak in the array.
</p>
<p>
  A peak is defined as adjacent integers in the array that are <b>strictly</b>
  increasing until they reach a tip (the highest value in the peak), at which
  point they become <b>strictly</b> decreasing. At least three integers are required to
  form a peak.
</p>
<p>
  For example, the integers <span>1, 4, 10, 2</span> form a peak, but the
  integers <span>4, 0, 10</span> don't and neither do the integers
  <span>1, 2, 2, 0</span>. Similarly, the integers <span>1, 2, 3</span> don't
  form a peak because there aren't any strictly decreasing integers after the
  <span>3</span>.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [1, 2, 3, 3, 4, 0, 10, 6, 5, -1, -3, 2, 3]
</pre>
<h3>Sample Output</h3>
<pre>6 <span class="CodeEditor-promptComment">// 0, 10, 6, 5, -1, -3</span>
</pre>
</div>

<h2>Hints</h2>

<p>
You can solve this question by iterating through the array from left to right once.
</p>
<p>
Iterate through the array from left to right, and treat every integer as the potential tip of a peak. To be the tip of a peak, an integer has to be strictly greater than its adjacent integers. What can you do when you find an actual tip?
</p>
<p>
As you iterate through the array from left to right, whenever you find a tip of a peak, expand outwards from the tip until you no longer have a peak. Given what peaks look like and how many peaks can therefore fit in an array, realize that this process results in a linear-time algorithm. Make sure to keep track of the longest peak you find as you iterate through the array.
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(1) space - where n is the length of the input array

```javascript
function longestPeak(array) {

  let longestPeakLength = 0;
  let i = 1;

  while (i < array.length - 1) {
    const isPeak = array[i - 1] < array[i] && array[i + 1] < array[i]
    if (!isPeak) {
      i++
      continue
    }

    let leftIdx = i - 2
    while (leftIdx >= 0 && array[leftIdx] < array[leftIdx + 1]) {
      leftIdx--
    }
    let rightIdx = i + 2;
    while (rightIdx < array.length && array[rightIdx] < array[rightIdx - 1]) {
      rightIdx++
    }
    const currentPeakLength = rightIdx - leftIdx - 1;
    longestPeakLength = Math.max(longestPeakLength, currentPeakLength)
    i = rightIdx
  }
  return longestPeakLength
}

// Do not edit the line below.
exports.longestPeak = longestPeak;



```