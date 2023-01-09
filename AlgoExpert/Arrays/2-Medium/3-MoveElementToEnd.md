# Move Element To End

<div class="html">
<p>
  You're given an array of integers and an integer. Write a function that moves
  all instances of that integer in the array to the end of the array and returns
  the array.
</p>
<p>
  The function should perform this in place (i.e., it should mutate the input
  array) and doesn't need to maintain the order of the other integers.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [2, 1, 2, 2, 2, 3, 4, 2]
<span class="CodeEditor-promptParameter">toMove</span> = 2
</pre>
<h3>Sample Output</h3>
<pre>[1, 3, 4, 2, 2, 2, 2, 2] <span class="CodeEditor-promptComment">// the numbers 1, 3, and 4 could be ordered differently</span>
</pre>
</div>

<h2>Hints</h2>

<p>
You can solve this problem in linear time.
</p>
<p>
In view of Hint #1, you can solve this problem without sorting the input array. Try setting two pointers at the start and end of the array, respectively, and progressively moving them inwards.
</p>
<p>
Following Hint #2, set two pointers at the start and end of the array, respectively. Move the right pointer inwards so long as it points to the integer to move, and move the left pointer inwards so long as it doesn't point to the integer to move. When both pointers aren't moving, swap their values in place. Repeat this process until the pointers pass each other.
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(1) space - where n is the length of the array

```javascript
function moveElementToEnd(array, toMove) {

  let startPointer = 0;
  let endPointer = array.length - 1

  while(startPointer < endPointer) {
    if (array[endPointer] === toMove) {
        endPointer--
    } 
    else if (array[startPointer] === toMove) {
      array[startPointer] = array[endPointer]
      array[endPointer] = toMove
      startPointer++
      endPointer--
    } else {
        startPointer++
    }
  }
  return array
}


```