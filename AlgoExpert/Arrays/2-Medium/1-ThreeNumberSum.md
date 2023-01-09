# Three Number Sum

<div class="html">
<p>
  Write a function that takes in a non-empty array of distinct integers and an
  integer representing a target sum. The function should find all triplets in
  the array that sum up to the target sum and return a two-dimensional array of
  all these triplets. The numbers in each triplet should be ordered in ascending
  order, and the triplets themselves should be ordered in ascending order with
  respect to the numbers they hold.
</p>
<p>
  If no three numbers sum up to the target sum, the function should return an
  empty array.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [12, 3, 1, 2, -6, 5, -8, 6]
<span class="CodeEditor-promptParameter">targetSum</span> = 0
</pre>
<h3>Sample Output</h3>
<pre>[[-8, 2, 6], [-8, 3, 5], [-6, 1, 5]]
</pre>
</div>

<h2>Hints</h2>

<p>
Using three for loops to calculate the sums of all possible triplets in the array would generate an algorithm that runs in O(n^3) time, where n is the length of the input array. Can you come up with something faster using only two for loops?
</p>
<p>
Try sorting the array and traversing it once. At each number, place a left pointer on the number immediately to the right of your current number and a right pointer on the final number in the array. Check if the current number, the left number, and the right number sum up to the target sum. How can you proceed from there, remembering the fact that you sorted the array?
</p>
<p>
Since the array is now sorted (see Hint #2), you know that moving the left pointer mentioned in Hint #2 one place to the right will lead to a greater left number and thus a greater sum. Similarly, you know that moving the right pointer one place to the left will lead to a smaller right number and thus a smaller sum. This means that, depending on the size of each triplet's (current number, left number, right number) sum relative to the target sum, you should either move the left pointer, the right pointer, or both to obtain a potentially valid triplet.
</p>

<h2>Optimal Space & Time Complexity</h2>

O(n^2) time | O(n) space - where n is the length of the input array

```javascript
function threeNumberSum(array, targetSum) {

  const triplets = []
  array.sort((a, b) => a - b);
  
  for (let i = 0; i < array.length -2; i++) {
    const currentNum = array[i];
    let leftPointer = i + 1;
    let rightPointer = array[array.length - 1]
    while(leftPointer < rightPointer) {
      const sum = currentNum + array[leftPointer] + array[rightPointer]
      if(sum === targetSum) {
        triplets.push([currentNum, array[leftPointer], array[rightPointer]])
      }
      if (sum < targetSum) {
        leftPointer += 1
      } else {
        rightPointer -= 1
      }
    }
  }

  return triplets
}

```