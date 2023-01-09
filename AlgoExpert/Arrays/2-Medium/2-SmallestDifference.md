# Smallest Difference

<div class="html">
<p>
  Write a function that takes in two non-empty arrays of integers, finds the
  pair of numbers (one from each array) whose absolute difference is closest to
  zero, and returns an array containing these two numbers, with the number from
  the first array in the first position.
</p>
<p>
  Note that the absolute difference of two integers is the distance between
  them on the real number line. For example, the absolute difference of -5 and 5
  is 10, and the absolute difference of -5 and -4 is 1.
</p>
<p>
  You can assume that there will only be one pair of numbers with the smallest
  difference.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">arrayOne</span> = [-1, 5, 10, 20, 28, 3]
<span class="CodeEditor-promptParameter">arrayTwo</span> = [26, 134, 135, 15, 17]
</pre>
<h3>Sample Output</h3>
<pre>[28, 26]</pre>
</div>

<h2>Hints</h2>

<p>
Instead of generating all possible pairs of numbers, try somehow only looking at pairs that you know could actually have the smallest difference. How can you accomplish this?
</p>
<p>
Would it help if the two arrays were sorted? If the arrays were sorted and you were looking at a given pair of numbers, could you efficiently find the next pair of numbers to look at? What are the runtime implications of sorting the arrays?
</p>
<p>
Start by sorting both arrays, as per Hint #2. Put a pointer at the beginning of both arrays and evaluate the absolute difference of the pointer-numbers. If the difference is equal to zero, then you've found the closest pair; otherwise, increment the pointer of the smaller of the two numbers to find a potentially better pair. Continue until you get a pair with a difference of zero or until one of the pointers gets out of range of its array.
</p>
<h2>Optimal Space & Time Complexity</h2>

O(nlog(n) + mlog(m)) time | O(1) space - where n is the length of the first input array and m is the length of the second input array

```javascript
function smallestDifference(arrayOne, arrayTwo) {
  arrayOne.sort((a,b) => a - b)
  arrayTwo.sort((a,b) => a - b)

  let idxOne = 0;
  let idxTwo = 0;
  let smallest = Infinity;
  let current = Infinity;
  let smallestPair = [];

  while (idxOne < arrayOne.length && idxTwo < arrayTwo.length) {
    let firstNum = arrayOne[idxOne]
    let secondNum = arrayTwo[idxTwo]

    if (firstNum < secondNum) {
      current = secondNum - firstNum
      idxOne++
    } else if (secondNum < firstNum) {
      current = firstNum - secondNum
      idxTwo++
    } else {
      return [firstNum, secondNum]
    }
    if (smallest > current) {
      smallest = current
      smallestPair = [firstNum, secondNum]
    }
  }
  return smallestPair
  
}

```