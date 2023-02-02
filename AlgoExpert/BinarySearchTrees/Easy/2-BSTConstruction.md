# BST Construction

<div class="html">
<p>
  Write a <span>BST</span> class for a Binary Search Tree. The class should
  support:
</p>
<ul>
  <li>Inserting values with the <span>insert</span> method.</li>
  <li>
    Removing values with the <span>remove</span> method; this method should
    only remove the first instance of a given value.
  </li>
  <li>Searching for values with the <span>contains</span> method.</li>
</ul>
<p>
  Note that you can't remove values from a single-node tree. In other words,
  calling the <span>remove</span> method on a single-node tree should simply not
  do anything.
</p>
<p>
  Each <span>BST</span> node has an integer <span>value</span>, a
  <span>left</span> child node, and a <span>right</span> child node. A node is
  said to be a valid <span>BST</span> node if and only if it satisfies the BST
  property: its <span>value</span> is strictly greater than the values of every
  node to its left; its <span>value</span> is less than or equal to the values
  of every node to its right; and its children nodes are either valid
  <span>BST</span> nodes themselves or <span>None</span> / <span>null</span>.
</p>
<h3>Sample Usage</h3>
<pre><span class="CodeEditor-promptComment">// Assume the following BST has already been created:</span>
         10
       /     \
      5      15
    /   \   /   \
   2     5 13   22
 /           \
1            14

<span class="CodeEditor-promptComment">// All operations below are performed sequentially.</span>
<span class="CodeEditor-promptParameter">insert</span>(12):   10
            /     \
           5      15
         /   \   /   \
        2     5 13   22
      /        /  \
     1        12  14

<span class="CodeEditor-promptParameter">remove</span>(10):   12
            /     \
           5      15
         /   \   /   \
        2     5 13   22
      /           \
     1            14

<span class="CodeEditor-promptParameter">contains</span>(15): true
</pre>
</div>

<h2>Hints</h2>

<p>
As you try to insert, find, or a remove a value into, in, or from a BST, you will have to traverse the tree's nodes. The BST property allows you to eliminate half of the remaining tree at each node that you traverse: if the target value is strictly smaller than a node's value, then it must be (or can only be) located to the left of the node, otherwise it must be (or can only be) to the right of that node.
</p>
<p>
Traverse the BST all the while applying the logic described in Hint #1. For insertion, add the target value to the BST once you reach a leaf (None / null) node. For searching, if you reach a leaf node without having found the target value that means the value isn't in the BST. For removal, consider the various cases that you might encounter: the node you need to remove might have two children nodes, one, or none; it might also be the root node; make sure to account for all of these cases.
</p>
<p>
What are the advantages and disadvantages of implementing these methods iteratively as opposed to recursively?
</p>
<h2>Optimal Space & Time Complexity</h2>

<div class="U1quNvMraAr3Hbq2JfVQ">Average (all 3 methods): O(log(n)) time | O(1) space - where n is the number of nodes in the BST
Worst (all 3 methods): O(n) time | O(1) space - where n is the number of nodes in the BST</div>

```javascript
// Do not edit the class below except for
// the insert, contains, and remove methods.
// Feel free to add new properties and methods
// to the class.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }

  insert(value) {
    if (value < this.value) {
      if (this.left === null) {
        this.left = new BST(value);
      } else {
        this.left.insert(value);
      }
    } else {
      if (this.right === null) {
        this.right = new BST(value);
      } else {
        this.right.insert(value);
      }
    }
    
    return this;
  }

  contains(value) {
    if (value < this.value) {
      if (this.left === null) {
        return false; 
      } else {
        return this.left.contains(value);
      }
    } else if (value > this.value) {
       if (this.right === null) {
        return false; 
      } else {
        return this.right.contains(value);
      }
    } else {
      return true;
    }
  }

  remove(value, parent = null) {
   if (value < this.value) {
     if (this.left !== null) {
       this.left.remove(value, this)
     }
   } else if (value > this.value) {
     if (this.right !== null) {
       this.right.remove(value, this)
     }
   } else {
     if (this.left !== null && this.right !== null) {
       this.value = this.right.getMinValue();
       this.right.remove(this.value, this)
     } 
     else if (parent === null) {
       if (this.left !== null) {
         this.value = this.left.value;
         this.right = this.left.right;
         this.left = this.left.left;
       } else if (this.right !== null) {
         this.value = this.right.value;
         this.left = this.right.left;
         this.right = this.right.right;
       }
     } 
     else if (parent.left === this) {
       parent.left = this.left !== null ? this.left : this.right;
     } else if (parent.right === this) {
       parent.right = this.left !== null ? this.left : this.right;
     }
   }
    return this;
  }

  getMinValue() {
    if (this.left === null) {
      return this.value;
    } else {
      return this.left.getMinValue();
    }
  }
}

// Do not edit the line below.
exports.BST = BST;
```
```javascript

// Do not edit the class below except for
// the insert, contains, and remove methods.
// Feel free to add new properties and methods
// to the class.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }

  insert(value) {
    let currentNode = this;
    while (true) {
      if (value < currentNode.value) {
        if (currentNode.left === null) {
          currentNode.left = new BST(value);
          break;
        } else {
          currentNode =  currentNode.left
        }
      } else {
        if (currentNode.right === null) {
          currentNode.right = new BST(value);
          break;
        } else {
          currentNode =  currentNode.right
        }
      }
    }
    return this;
  }

  contains(value) {
    let currentNode = this;
    while (currentNode !== null) {
      if (value < currentNode.value) {
        currentNode = currentNode.left
      } else if (value > currentNode.value) {
        currentNode = currentNode.right
      } else {
        return true
      }
    }
    return false;
  }

  remove(value, parentNode = null) {
    let currentNode = this;
    while (currentNode !== null) {
      if (value < currentNode.value) {
        parentNode = currentNode;
        currentNode = currentNode.left;
      } else if (value > currentNode.value) {
        parentNode = currentNode;
        currentNode = currentNode.right;
      } else {
        if (currentNode.left !== null && currentNode.right !== null) {
          currentNode.value = currentNode.right.getMinValue();
          currentNode.right.remove(currentNode.value, currentNode)
        } else if (parentNode === null) {
          if (currentNode.left !== null) {
            currentNode.value = currentNode.left.value;
            currentNode.right = currentNode.left.right;
            currentNode.left = currentNode.left.left;
          } else if (currentNode.right !== null) {
            currentNode.value = currentNode.right.value;
            currentNode.left = currentNode.right.left;
            currentNode.right = currentNode.right.right;
          } else {
            
          }
        } else if (parentNode.left === currentNode) {
          parentNode.left = currentNode.left !== null ? currentNode.left : currentNode.right;
        } else if (parentNode.right === currentNode) {
          parentNode.right = currentNode.left !== null ? currentNode.left : currentNode.right
        }
        break;
        
      }
    }
    
    return this;
  }

  getMinValue() {
    let currentNode = this;
    while (currentNode.left !== null) {
      currentNode = currentNode.left
    }
    return currentNode.value
  }
}

// Do not edit the line below.
exports.BST = BST;


```

