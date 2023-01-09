# Merge Overlapping Intervals

<div class="html">
<p>
  Write a function that takes in a non-empty array of arbitrary intervals,
  merges any overlapping intervals, and returns the new intervals in no
  particular order.
</p>
<p>
  Each interval <span>interval</span> is an array of two integers, with
  <span>interval[0]</span> as the start of the interval and
  <span>interval[1]</span> as the end of the interval.
</p>
<p>
  Note that back-to-back intervals aren't considered to be overlapping. For
  example, <span>[1, 5]</span> and <span>[6, 7]</span> aren't overlapping;
  however, <span>[1, 6]</span> and <span>[6, 7]</span> <i>are</i> indeed
  overlapping.
</p>
<p>
  Also note that the start of any particular interval will always be less than
  or equal to the end of that interval.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">intervals</span> = [[1, 2], [3, 5], [4, 7], [6, 8], [9, 10]]
</pre>
<h3>Sample Output</h3>
<pre>[[1, 2], [3, 8], [9, 10]]
<span class="CodeEditor-promptComment">// Merge the intervals [3, 5], [4, 7], and [6, 8].</span>
<span class="CodeEditor-promptComment">// The intervals could be ordered differently.</span>
</pre>
</div>

<h2>Hints</h2>

<p>
  The problem asks you to merge overlapping intervals. How can you determine if
  two intervals are overlapping?
</p>
<p>
  Sort the intervals with respect to their starting values. This will allow you
  to merge all overlapping intervals in a single traversal through the sorted
  intervals.
</p>
<p>
  After sorting the intervals with respect to their starting values, traverse
  them, and at each iteration, compare the start of the next interval to the end
  of the current interval to look for an overlap. If you find an overlap, mutate
  the current interval so as to merge the next interval into it.
</p>
<h2>Optimal Space & Time Complexity</h2>

O(nlog(n)) time | O(n) space - where n is the length of the input array

```javascript
function mergeOverlappingIntervals(array) {

  const sortedIntervals = array.sort((a,b) => a[0] - b[0])
  const mergedIntervals = []
  let currentInterval = sortedIntervals[0]
  mergedIntervals.push(currentInterval)

  for (const nextInterval of sortedIntervals) {
    const [_, currentIntervalEnd] = currentInterval
    const [nextIntervalStart, nextIntervalEnd] = nextInterval

    if (currentIntervalEnd >= nextIntervalStart) {
      currentInterval[1] = Math.max(currentIntervalEnd, nextIntervalEnd)
    } else {
      currentInterval = nextInterval
      mergedIntervals.push(currentInterval)
    }
  }

  return mergedIntervals
}

// Do not edit the line below.
exports.mergeOverlappingIntervals = mergeOverlappingIntervals;


```