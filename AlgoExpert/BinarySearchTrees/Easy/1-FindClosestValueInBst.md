# Find Closest value in BST

<div class="html">
<p>
  Write a function that takes in a Binary Search Tree (BST) and a target integer
  value and returns the closest value to that target value contained in the BST.
</p>
<p>You can assume that there will only be one closest value.</p>
<p>
  Each <span>BST</span> node has an integer <span>value</span>, a
  <span>left</span> child node, and a <span>right</span> child node. A node is
  said to be a valid <span>BST</span> node if and only if it satisfies the BST
  property: its <span>value</span> is strictly greater than the values of every
  node to its left; its <span>value</span> is less than or equal to the values
  of every node to its right; and its children nodes are either valid
  <span>BST</span> nodes themselves or <span>None</span> / <span>null</span>.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">tree</span> =   10
       /     \
      5      15
    /   \   /   \
   2     5 13   22
 /           \
1            14
<span class="CodeEditor-promptParameter">target</span> = 12
</pre>
<h3>Sample Output</h3>
<pre>13</pre>
</div>

<h2>Hints</h2>

<p>
Try traversing the BST node by node, all the while keeping track of the node with the value closest to the target value. Calculating the absolute value of the difference between a node's value and the target value should allow you to check if that node is closer than the current closest one.
</p>
<p>
Make use of the BST property to determine what side of any given node has values close to the target value and is therefore worth exploring.
</p>
<p>
What are the advantages and disadvantages of solving this problem iteratively as opposed to recursively?
</p>
<h2>Optimal Space & Time Complexity</h2>

<div class="U1quNvMraAr3Hbq2JfVQ">Average: O(log(n)) time | O(1) space - where n is the number of nodes in the BST

Worst: O(n) time | O(1) space - where n is the number of nodes in the BST</div>

```javascript
function findClosestValueInBst(tree, target) {
  // Write your code here.
  let currentNode = tree;
  let closest = tree.value;
  while (currentNode !== null) {
    if (Math.abs(target - closest) > Math.abs(target - currentNode.value)) {
      closest = currentNode.value;
    }
    if (target < currentNode.value) {
      currentNode = currentNode.left
    } else if (target > currentNode.value) {
      currentNode = currentNode.right;
    } else {
      break;
    }
  }
  return closest;
}

// This is the class of the input tree. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}
```
```javascript

function findClosestValueInBst(tree, target) {
  return findClosestValueInBstHelper(tree, target, tree.value);
}

function findClosestValueInBstHelper(tree, target, closest) {
  if (tree === null) {
    return closest;
  }
  if (Math.abs(target - closest) > Math.abs(target - tree.value)) {
    closest = tree.value;
  }
  if (target < tree.value) {
    return findClosestValueInBstHelper(tree.left, target, closest)
  } else if (target > tree.value) {
    return findClosestValueInBstHelper(tree.right, target, closest)
  } else {
    return closest
  }
}
// This is the class of the input tree. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

```

