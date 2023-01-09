# Powerset

<div class="html">
<p>
  Write a function that takes in an array of unique integers and returns its
  powerset.
</p>
<p>
  The powerset <span>P(X)</span> of a set <span>X</span> is the set of all
  subsets of <span>X</span>. For example, the powerset of <span>[1,2]</span> is
  <span>[[], [1], [2], [1,2]]</span>.
</p>
<p>
  Note that the sets in the powerset do not need to be in any particular order.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [1, 2, 3]
</pre>
<h3>Sample Output</h3>
<pre>[[], [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3]]
</pre>
</div>

<h2>Hints</h2>

<p>
Try thinking about the base cases. What is the powerset of the empty set? What is the powerset of sets of length 1?
</p>
<p>
If you were to take the input set X and add an element to it, how would the resulting powerset change?
</p>
<p>
Can you solve this problem recursively? Can you solve it iteratively? What are the advantages and disadvantages of using either approach?
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n*2^n) time | O(n*2^n) space - where n is the length of the input array

```javascript
// My solution

function powersetHelper (array, output, powersetPushed) {
  if (!array.length) {
    return
  } else {
    if(!(array.join('') in powersetPushed)) {
      powersetPushed[array.join('')] = true
      output.push(array)
    }
    for (let index = 0; index < array.length; index++) {
      const updatedArray = array.slice(0, index).concat(array.slice(index + 1))
      powersetHelper(updatedArray, output, powersetPushed) 
    }
  }
}

function powerset(array) {
  const output = [];
  const powersetPushed = {}
  powersetHelper(array, output, powersetPushed)
  output.push([])
  return output
  
}

// Do not edit the line below.
exports.powerset = powerset;


```

```javascript
// O (n*2^n) time | O(n*2^n) space
function powerset(array, idx = null) {
  if (idx === null) {
    idx = array.length -1
  }
  if (idx < 0) {
    return [[]]
  }
  const element = array[idx]
  const subsets = powerset(array, idx - 1)
  const length = subsets.length;
  for (let i = 0; i < length; i++) {
    const currentSubset = subsets[i]
    subsets.push(currentSubset.concat(element))
  }
  return subsets
}

// Do not edit the line below.
exports.powerset = powerset;

```

```javascript
// O (n*2^n) time | O(n*2^n) space
function powerset(array) {
  const subsets = [[]]
  for (const element of array) {
    const length = subsets.length
    for (let i = 0; i < length; i++) {
      const currentSubset = subsets[i]
      subsets.push(currentSubset.concat(element))
    }
  }
  return subsets
}

// Do not edit the line below.
exports.powerset = powerset;

```